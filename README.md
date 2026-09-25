# Shrey Singala | Portfolio

A portfolio site showcasing my engineering projects. The home page lists every project;
each project links to its own detail page with the full story: how it works, how I built
it, and what I learned. Plain HTML, CSS, and JavaScript, with no build step and no dependencies.

## Structure

```
portfolio-site/
├── index.html            # home page (hero, project cards, skills, experience, contact)
├── css/styles.css        # dark technical theme (shared by every page)
├── js/main.js            # nav, active-link, reveal-on-scroll (shared)
├── .nojekyll             # tells GitHub Pages to serve files as-is
├── projects/             # one detail page per project
│   ├── chat-application.html
│   ├── analog-audio.html
│   ├── pipelined-cpu.html
│   └── object-tracking.html
└── assets/
    ├── resume/Shrey_Singala.pdf   # linked from the "Résumé" button
    ├── reports/                   # per-project PDF reports (linked from project pages)
    └── img/                       # project photos/screenshots
```

## Run locally

Just open `index.html` in a browser. For correct relative paths (so the PDF links
resolve exactly as they will when deployed), serve the folder:

```bash
cd portfolio-site
python -m http.server 8000
# then open http://localhost:8000
```

## Deploy to GitHub Pages

1. Create a new GitHub repo (e.g. `portfolio`).
2. From inside `portfolio-site/`:
   ```bash
   git init
   git add .
   git commit -m "Portfolio site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/portfolio.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   pick `main` / `root`, and save.
4. Your site goes live at `https://<your-username>.github.io/portfolio/` within a minute or two.

> The included `.nojekyll` file ensures the `assets/` folder and its PDFs are served
> without GitHub's Jekyll processing interfering.

Netlify or Vercel work too; just point them at this folder, no build command needed.

## Adding media later

Everywhere you see a "coming soon" box is a placeholder waiting for an image or clip.

- On the **home page**, each card has a `<div class="media-placeholder">…</div>`.
- On each **project page** (`projects/*.html`), the gallery has one large
  `<div class="shot shot--main">…</div>` plus three smaller `<div class="shot">…</div>`
  thumbnails. The label inside each one describes the photo it's expecting.

To add real media:

1. Drop the file into `assets/img/`.
2. Replace the placeholder `<div>` with an image or video. From the **home page** use a
   path like `assets/img/chat-demo.jpg`; from a **project page** (inside `projects/`) prefix
   it with `../`, e.g.:
   ```html
   <img src="../assets/img/chat-demo.jpg" alt="Chat application demo" style="width:100%;border-radius:12px;" />
   ```
   (or a `<video controls>` for a clip).

## Editing content

- Home page text lives in `index.html` under commented sections
  (`NAV`, `HERO`, `ABOUT`, `PROJECTS`, `SKILLS`, `EXPERIENCE`, `CONTACT`).
- Each project's full write-up lives in its own file under `projects/`.
- Colors, fonts, and spacing are CSS variables at the top of `css/styles.css` and apply
  to every page.
