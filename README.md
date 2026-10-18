# Flow Media Collective — theflowteam.com

The website for Flow Media Collective, a film and advertising studio in Austin, Texas.
It's a static site: one HTML page plus media files, with no build step, so it deploys to Vercel as is.

## What's in this folder

| Path | What it is |
| --- | --- |
| `index.html` | The whole site: home page, Work, Services, Studio, Journal, Contact, and the Privacy Policy, Terms of Use, Cookie Policy and Journal articles (shown as in-page views). |
| `media/` | Compressed videos (`.mp4`), video posters and photos (`.jpg`), and `og-image.jpg` for link previews. |
| `brand/` | Logo mark as SVG (white and black) and a 512px app icon. |
| `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png` | Browser and home-screen icons. |
| `404.html` | Page shown for broken links on Vercel. |
| `vercel.json` | Security headers, media caching, and short links such as `/privacy` and `/terms`. |
| `robots.txt`, `sitemap.xml` | For search engines. |

## Deploy: GitHub, then Vercel

### 1. Put the files on GitHub

**In the browser (no command line):**
1. Sign in at github.com and click **New repository**. Name it `flow-media-collective`, keep it **Private**, and don't add a README.
2. On the new repository's page, click **uploading an existing file**.
3. Drag in everything from this folder, including the `media` and `brand` folders, then click **Commit changes**.
   GitHub's web uploader takes up to 100 files at a time. This folder has fewer than that, so one upload works.

**Or with Git on your computer:**
```bash
cd flow-media-collective
git init -b main
git add -A
git commit -m "Flow Media Collective website"
git remote add origin https://github.com/YOUR-ACCOUNT/flow-media-collective.git
git push -u origin main
```

### 2. Deploy on Vercel
1. Sign in at vercel.com with your GitHub account.
2. Click **Add New → Project** and import `flow-media-collective`.
3. Leave the settings as they are: **Framework Preset: Other**, no build command, output directory = the project root.
4. Click **Deploy**. You'll get a preview address ending in `.vercel.app`.

Every later push to the `main` branch redeploys the site automatically.

### 3. Connect theflowteam.com
1. In the Vercel project, open **Settings → Domains** and add `theflowteam.com` and `www.theflowteam.com`.
2. Vercel shows the DNS records to add at your domain registrar (usually an `A` record for the bare domain and a `CNAME` for `www`). Add them there.
3. Set `www` to redirect to `theflowteam.com` so there's one address. HTTPS is set up automatically.

## Before you launch

- [ ] **Connect the contact form.** Create a form at a service such as [Formspree](https://formspree.io), copy its endpoint URL, and paste it into `index.html` here:
      `const FORM_ENDPOINT = "";`
      Until then the form tells visitors it isn't connected and sends nothing.
- [ ] **Fill in every highlighted `[CONFIRM: …]` item** in the Privacy Policy, Terms of Use and Cookie Policy, and the Contact section's email. Search `index.html` for `[CONFIRM` and `[DATE]`.
- [ ] **Add the form service and Vercel to the Privacy Policy's list of service providers.**
- [ ] **Have an attorney review the legal pages**, then add effective dates.
- [ ] **If you add analytics (for example Vercel Analytics or Google Analytics),** load it only inside `applyConsent()` in `index.html` so it runs after a visitor accepts, and add it to the Cookie Policy table.

## Updating content

- **Swap a video or photo:** replace the file in `media/` with one of the same name, or change the path in `index.html`. Video paths for the player are in the `FILMS` list near the bottom of the file.
- **Change copy:** edit the text directly in `index.html`.
- **Media sizes:** videos are compressed for the web (360–720px wide, about 1–12 MB each). For sharper video, export your originals at 720×1280 or 1080×1920 in H.264 MP4 and keep each file under about 15 MB.

## Links into the site

Sections and pages use addresses like `theflowteam.com/#work` or `#privacy`. The short links in `vercel.json` also work:
`/privacy`, `/terms`, `/cookies`, `/journal/six-courses-above-austin`, `/journal/red-drive`, `/journal/its-not-about-the-cars`.

© 2026 Flow Media Collective. All rights reserved. Photos and video © Flow Media Collective and used with the permission of the clients shown.
