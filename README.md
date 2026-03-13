# Japanese Adverbs - Complete Guide (副詞完全ガイド)

A visually rich, single-page reference site for Japanese adverbs, focused on JLPT learners (N5-N3).

Live site: https://sheikhsulaiman.github.io/adverb/

## Overview

This project is a static website that explains the three major categories of Japanese adverbs:

- 情態の副詞 (Manner adverbs)
- 程度の副詞 (Degree adverbs)
- 呼応の副詞 (Correlative adverbs)

The page includes searchable data tables, type-based filters, quick comparison sections, and exam-oriented notes.

## Features

- Single-page educational reference with no framework dependencies
- Search and filter interactions for each adverb category
- Bilingual content (Japanese + English glosses)
- Mobile-friendly responsive layout
- SEO-ready metadata for social sharing
- Progressive Web App (PWA) support
- Offline support with a service worker

## Tech Stack

- HTML5
- CSS3
- Vanilla JavaScript
- Web App Manifest (`site.webmanifest`)
- Service Worker (`sw.js`)

No build tools, bundlers, or package manager are required.

## Project Structure

```text
.
|- index.html
|- site.webmanifest
|- sw.js
|- images/
|  |- android-chrome-192x192.png
|  |- android-chrome-512x512.png
|  |- apple-touch-icon.png
|  |- favicon-16x16.png
|  |- favicon-32x32.png
|  |- favicon.ico
|  |- maskable-icon-512x512.png
```

## Local Development

Because this project uses a service worker, test with a local web server (not by opening `index.html` directly).

### Option 1: Python

```bash
python -m http.server 8080
```

Open: `http://localhost:8080`

### Option 2: Node (npx)

```bash
npx serve .
```

## GitHub Pages Deployment

This repository is configured for GitHub Pages project-site deployment under:

- Base URL: `/adverb/`
- Canonical URL: `https://sheikhsulaiman.github.io/adverb/`

The manifest is already configured with:

- `id: /adverb/`
- `start_url: /adverb/`
- `scope: /adverb/`

If you ever rename the repository, update:

- `site.webmanifest` (`id`, `start_url`, `scope`)
- Canonical and Open Graph URLs in `index.html`

## SEO Setup

The page includes:

- `meta description`
- Canonical URL
- Open Graph tags (`og:title`, `og:description`, `og:url`, `og:image`)
- Twitter card tags (`summary_large_image`)
- Standard favicon and Apple touch icon links

SEO image source is currently the 512x512 app icon in `images/android-chrome-512x512.png`.

## PWA and Offline Support

### Manifest (`site.webmanifest`)

Configured for installability on mobile/desktop with:

- `display: standalone`
- `orientation: portrait-primary`
- Theme and background colors
- Any + maskable icon support

### Service Worker (`sw.js`)

Current behavior:

- Pre-caches app shell files on install
- Deletes old caches during activate
- Uses network-first for navigation requests, with offline fallback to cached `index.html`
- Uses cache-first with network fallback for same-origin static assets

To force clients to refresh caches after a major update, bump:

- `CACHE_NAME` in `sw.js` (example: `adverb-pwa-v2`)

## Customization Guide

### Add or Edit Adverbs

All table data is stored in JavaScript arrays in `index.html`:

- `jotaiData`
- `teidoData`
- `koouData`

Each entry includes fields like:

- `word`, `reading`
- `subtype`, `subtypeName`
- `patterns`, `meanings`
- `examples`
- `note`

### Update Theme/Visuals

Edit CSS variables in `:root` inside `index.html`.

### Replace Icons

Replace files in `images/` while keeping filenames the same, or update paths in:

- `site.webmanifest`
- icon links in `index.html`
- app shell cache list in `sw.js`

## Validation Checklist

Before release:

1. Open site in Chrome/Edge and verify no console errors.
2. Check install prompt/Install app option appears.
3. In DevTools, confirm service worker is active.
4. Test offline mode (DevTools -> Network -> Offline).
5. Run Lighthouse (PWA + SEO categories).
6. Verify Open Graph preview using a social debugger.

## Known Notes

- Service workers can serve stale cached content if `CACHE_NAME` is not updated after major changes.
- Browser cache may need hard refresh after icon updates.
- Some linters may flag empty CSS rule blocks in `index.html`; this does not break runtime behavior.

## Contributing

1. Fork the repo
2. Create a feature branch
3. Make and test your changes
4. Open a pull request

## Author

- GitHub: [@sheikhsulaiman](https://github.com/sheikhsulaiman)
