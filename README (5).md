# Rx Ledger — Medicine Inventory

A private, single-page medicine inventory, billing and expiry tracker. It is a **static site** (one `index.html`, no build step, no backend). All data is stored in the browser's `localStorage` on the device that uses it — nothing is sent to any server.

## Features

- Inventory grouped by disease/category, with manufacturer, batch, mfg/expiry month, stock, purchase price, MRP and margin
- Expiry tracking: **Expired** / **Expiring soon** (15/30/60/90-day warning window) / **In date**
- Live billing with stock deducted as items are added, discounts (% or flat) and bill history
- Single sales, returns/unsold stock, and daily sales summary
- Expired batches are blocked from being sold or billed
- Export backup (`.json`) and CSVs for inventory, sales and bills; import a backup to move data between devices

## Run locally

Any static server works. With Node installed:

```bash
npm start
# open http://localhost:3000
```

Or just open `index.html` directly in a browser.

## Deploy to GitHub

```bash
git init
git add .
git commit -m "Initial commit: Rx Ledger"
git branch -M main
git remote add origin https://github.com/<your-username>/rx-ledger.git
git push -u origin main
```

## Deploy to Vercel

**Option A — from GitHub (recommended)**

1. Go to [vercel.com/new](https://vercel.com/new) and import the `rx-ledger` repository.
2. Framework Preset: **Other**. Leave Build Command and Output Directory **empty**. Root Directory: `./`.
3. Click **Deploy**. Every push to `main` redeploys automatically.

**Option B — Vercel CLI**

```bash
npm i -g vercel
vercel          # preview deployment
vercel --prod   # production deployment
```

## Important notes

- **Data lives per browser and per device.** A different browser, device or incognito window starts empty. Use **Export Backup** regularly and **Import Backup** to move data. Clearing site data erases it.
- Because data is local, the deployed URL itself holds no inventory — it is safe to host publicly. Do not commit exported backups/CSVs (they are in `.gitignore`).
- This tool is for record-keeping. Always verify expiry on the physical pack.

## Project structure

```
index.html     the whole app (HTML + CSS + JS)
vercel.json    clean URLs and security headers
package.json   metadata and a local `npm start` server
README.md
.gitignore
```

## License

MIT
