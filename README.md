# Asian Chess Federation website prototype

A mobile-first redesign prototype of asianchess.com. It is a static site with no build step and no dependencies to install.

## Run it

Serve the folder with any static web server and open it in a browser:

```
cd acf-site
python3 -m http.server 8000
# open http://localhost:8000
```

You need a server because the regulations viewer loads the PDF over HTTP; the pages also work when you open `index.html` directly, apart from that viewer. Any static host also works (Netlify, Vercel, GitHub Pages, cPanel or a WordPress theme folder).

## Files

| Path | What it is |
|---|---|
| `index.html` | The whole site: HTML, CSS and JavaScript in one file. Pages are rendered client-side and switched by the URL hash (`#news`, `#event-aacc26`, `#me-articles`). |
| `assets/` | ACF logo with the background removed (984px, 512px and 256px PNG). |
| `img/` | 20 illustrative chess photos from Unsplash, compressed to WebP. Credits are shown on the site and listed on the `#notes` page. |
| `flags/` | 47 country flags as SVG, from the open-source flag-icons package (MIT licence). |
| `asian-amateur-2026-regulations.pdf` | Regulations V3 for the 2026 Asian Amateur Chess Championships, opened in the built-in viewer at `#regulations`. |

## External resources

- Inter font from Google Fonts (falls back to the system font if blocked).
- PDF.js 2.16.105 from cdnjs, loaded only on the regulations page.

## Where to edit content

All content lives in data arrays near the top of the `<script>` in `index.html`:

- `NEWS`: news articles
- `EVENTS`: championships and programmes
- `FEDS`: member federations (FIDE code, country, region, map position, official name)
- `ISO`: FIDE code to flag file mapping
- `OFFICERS`: federation officers
- `DOCS`: documents in the library
- `SCHED`: Asian Amateur 2026 schedule
- `PLAYERS`: player list for member interviews
- `UNS` / `PALT`: photo credits and alt text

## Prototype only: what is simulated

Accounts, sign-up, email verification (code `246810`), member submissions, moderation and settings run entirely in the browser's memory and reset on reload. Nothing is sent to a server.

Demo accounts (password `demo1234`):

- Member: `member@demo.acf`
- ACF staff: `staff@demo.acf`

For production, connect these screens to the existing WordPress backend (or another CMS):

- Login, sign-up, password reset and email verification: WordPress authentication.
- Articles, interviews, gallery: custom post types, submitted with status `pending`.
- Moderation: staff approve, which changes the status to `publish`.
- Enforce every permission on the server. The hidden buttons in this prototype are not security.

The full audit, sitemap, design system and launch checklist are on the site at `#notes`.

Deployment refresh
