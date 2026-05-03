# Sri Sai Durga Caterers — Invoice Generator Web App

A static web app hosted on **GitHub Pages** that generates GST tax invoices as downloadable PDFs directly in the browser.

## Live App

Once deployed: `https://<your-username>.github.io/<repo-name>/`

---

## Features

- Select client company from dropdown (Srini Pharmaceuticals / Veena Life Sciences)
- Enter taxable amount → CGST & SGST auto-calculated at 9% (floored to nearest ₹)
- Total amount shown in Indian words (lakhs/crores format)
- Live invoice preview before downloading
- One-click PDF download — no server needed, runs entirely in browser

---

## Deploy to GitHub Pages (5 minutes)

### Step 1 — Create a new repository
Go to github.com → New repository → name it (e.g. `invoice-generator`) → Create

### Step 2 — Push these files
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/<your-username>/invoice-generator.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages
1. Go to your repo → **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. The workflow (`.github/workflows/deploy.yml`) will auto-run on every push

### Step 4 — Visit your app
After the workflow completes (~1 min), your app is live at:
`https://<your-username>.github.io/invoice-generator/`

---

## Adding More Companies

Open `index.html` and find the `<select id="company">` block. Add a new `<option>`:

```html
<option value="New Company Pvt Ltd" data-gstin="36XXXXX0000X1ZX">New Company Pvt Ltd</option>
```

Then add the company details to the `COMPANIES` object in the `<script>` section:

```javascript
"New Company Pvt Ltd": {
  gstin: "36XXXXX0000X1ZX",
  address: "Full address here",
  state: "TELANGANA",
  code: "36"
}
```

---

## Tech Stack

- Pure HTML + CSS + JavaScript (no framework)
- [jsPDF](https://github.com/parallax/jsPDF) for PDF generation (loaded from CDN)
- GitHub Pages for hosting (free, no server needed)
- GitHub Actions for automatic deployment on push
