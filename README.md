# INVA — Inventory Vault

A framework-free, offline-first inventory/product transaction manager using HTML5, CSS3, Vanilla JavaScript and IndexedDB.

## Files

- `index.html` — application shell
- `styles.css` — responsive UI
- `app.js` — IndexedDB CRUD, reports, backup/restore, PWA registration and XLSX export
- `manifest.json` — PWA manifest
- `service-worker.js` — offline application-shell cache
- `icon.svg` — application icon

## Run locally

For PWA/service-worker behavior, serve the folder over `localhost` rather than opening `index.html` directly. Any static server works. Example with Python's simple server:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080/`.

No build step or Node.js runtime is required.

## Static deployment

Upload all files to a static host such as GitHub Pages. HTTPS is recommended for service-worker/PWA behavior.

## Offline behavior

IndexedDB stores products and transactions. The service worker caches the application shell. No inventory data is transmitted to a server.

## XLSX export

The application includes a dependency-free local XLSX writer fallback implemented in `app.js`, so XLSX export works without a network connection or external CDN. The UI is also prepared to use a locally vendored SheetJS browser build if `xlsx.full.min.js` is added beside `index.html`: load it before `app.js` and the export adapter will use `window.XLSX` automatically.

The official SheetJS documentation recommends vendoring `xlsx.full.min.js` for offline stability. If you want the official SheetJS build, download version 0.20.3 from the SheetJS CDN and save it as `xlsx.full.min.js`, then add `<script src="xlsx.full.min.js"></script>` immediately before `app.js` in `index.html`.

## Android/iOS wrapper later

The static web app can later be wrapped with Capacitor or another WebView wrapper without changing the core application. Android APK packaging can use the normal Android signing workflow. iOS IPA/App Store/TestFlight distribution requires Apple's signing and provisioning process.

## Data safety

Use **Backup Data** regularly. Clearing browser/app storage can permanently remove the local IndexedDB database.


## Creator & Social Links
INVA is branded for **MD. Ikramul Islam Siddique Porosh**. The footer contains clickable links to the portfolio, LinkedIn, Facebook and YouTube. The links are simple outbound navigation; they do not collect analytics or inventory data, and they require internet access only when the user chooses to open a social platform.

Portfolio: https://rjporosh.github.io/
Phone: +880 1672-896992
LinkedIn: https://www.linkedin.com/in/md-ikramul-islam-siddique-porosh-4393b333a
Facebook: https://www.facebook.com/iamrjporosh
YouTube: https://www.youtube.com/@mdikramulislamsiddiqueporosh
