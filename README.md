# Tender Analysis

A browser-based tender-estimating and project-review workspace. It is a static single-page application: open it through GitHub Pages or a local web server and use it directly in a modern desktop browser.

**Live site:** https://outline-systems.github.io/TW-Tender-analysis/

## Features

- Tender setup, sections, work packages and bid comparison
- Preliminary and General (P&G) build-up, provisional sums and options
- Rate, quantity, margin, contingency and contract-total calculations
- Clarifications, exclusions, team review and risk/letting forecast
- Drawing and scope viewer for PDFs and images
- Spreadsheet export, backup/restore and downloadable print pack
- Editable admin libraries for sections, packages, consultants, rates and clarifications

## Repository structure

```text
.
├── index.html          # Main application; includes application CSS, JavaScript and embedded PDF.js
├── baywide-theme.css   # Baywide Dingos / TradeOS visual-theme overrides
└── README.md           # Project documentation
```

`index.html` is deliberately large because it includes the application code and an embedded PDF.js library/worker. Do not replace it with a partial snippet when editing it.

## Run locally

### Easiest option

Open `index.html` in a current browser. Most functions will work directly from the file.

### Recommended option

Run a lightweight local server from the repository folder:

```bash
python3 -m http.server 8000
```

Then browse to:

```text
http://localhost:8000/
```

A local server is recommended when testing file handling, PDF viewing, browser storage or exports.

## Deploy with GitHub Pages

This repository is intended to be published from the `main` branch using GitHub Pages.

1. Commit `index.html`, `baywide-theme.css` and `README.md` to `main`.
2. In GitHub, open **Settings → Pages**.
3. Set the source to **Deploy from a branch**.
4. Choose the `main` branch and the repository root (`/`).
5. Save and allow GitHub Pages time to publish.
6. Open the published site URL.

For this repository, the published address is expected to be:

```text
https://outline-systems.github.io/TW-Tender-analysis/
```

## Theme setup

The application loads the theme from this line in `index.html`, placed immediately before `</head>`:

```html
<link rel="stylesheet" href="baywide-theme.css">
```

Keep `baywide-theme.css` in the **same repository folder** as `index.html`. Because the stylesheet is linked after the application’s embedded `<style>` block, its rules override the base visual theme without changing the application logic.

To confirm the deployed stylesheet is loading, open:

```text
https://outline-systems.github.io/TW-Tender-analysis/baywide-theme.css
```

If a theme update does not appear immediately:

- Wait for the GitHub Pages deployment to finish.
- Use a hard refresh: `Cmd + Shift + R` on macOS or `Ctrl + F5` on Windows.
- Test in an incognito/private window.
- Use **View Page Source** and confirm `baywide-theme.css` appears in the HTML `<head>`.

## Data and backups

Tender information is stored in the browser’s local storage. That means it is specific to the browser profile and device used.

- Use **Backup** regularly to export your work.
- Keep exported backup files in your project document-control location.
- Use the app’s restore function to move or recover tender data.
- Do not rely on browser storage as the only copy of commercial tender information.

## Updating safely

### Change only the visual theme

Edit `baywide-theme.css`. This is the preferred location for colours, spacing, typography, buttons, cards, tables and responsive visual changes.

### Change functionality or application content

Edit the full `index.html` in a code editor such as VS Code. Make a backup before altering it, particularly because it includes a large embedded PDF.js payload.

### Avoid GitHub’s browser editor for `index.html`

The file can be too large for GitHub’s browser editor to load reliably. Download/edit/upload the complete `index.html` instead. When replacing it, verify the target filename remains exactly `index.html`.

## Suggested additions

The current static build does not require a package manager, build system or environment file. The following repository files are useful additions:

### `.gitignore`

```gitignore
.DS_Store
Thumbs.db
*.bak
*.tmp
*.zip
```

### `LICENSE`

Add a licence appropriate to the owner and intended use. If the tool is proprietary/internal, a short all-rights-reserved notice is more suitable than an open-source licence.

### `CHANGELOG.md`

Record production updates, particularly changes to calculations, exports, tender data structures or theme revisions. Example:

```markdown
# Changelog

## Unreleased
- Added Baywide Dingos / TradeOS visual theme.
- Added external `baywide-theme.css` stylesheet reference.
```

### `docs/`

Use a `docs` folder for user guides, tender-process notes, screenshots and example backup files that do not contain live commercial data.

## Browser support

Use a current version of Chrome, Edge, Safari or Firefox. Desktop Chrome/Edge is recommended for the best experience with spreadsheets, print/PDF output, local data and drawing viewing.

## Security and commercial data

This is a client-side application. Treat backups, browser-stored data, exported spreadsheets and downloaded packs as commercially sensitive tender information. Do not commit live client data, supplier pricing, credentials, or confidential project documents to a public GitHub repository.

## Maintenance checklist

Before publishing a release:

- Confirm `index.html` loads without console errors.
- Confirm `baywide-theme.css` loads with HTTP status 200 on GitHub Pages.
- Hard-refresh and check the visible theme changes.
- Test backup and restore with a non-production sample.
- Test Excel export and the print/PDF pack.
- Test a PDF and an image in the drawings viewer.
- Check the mobile layout at widths below 900px.
- Create and retain a backup before structural changes.
