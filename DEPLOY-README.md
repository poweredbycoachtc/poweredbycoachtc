# Deploy poweredbycoachtc.com — step by step

Everything in this folder is ready to publish. You do two logins (GitHub + GoDaddy) and copy-paste. ~15 minutes. No coding.

The `CNAME` file is already included — do not delete it. It tells GitHub your domain is poweredbycoachtc.com.

---

## PART 1 — Put the site on GitHub Pages (free hosting)

1. Go to https://github.com and create a free account (skip if you have one).
2. Click the **+** (top right) → **New repository**.
3. Repository name: `poweredbycoachtc` — set to **Public** — click **Create repository**.
4. On the new repo page, click **uploading an existing file** (the link in the middle).
5. Open this folder on your computer. Select **everything inside it**:
   - `index.html`
   - the `assets` folder
   - the `CNAME` file
   (Do NOT upload the outer folder itself — upload its *contents*. If you can't see CNAME, enable "show hidden files".)
6. Drag them into the GitHub upload box → click **Commit changes**.
7. Go to **Settings** (top of repo) → **Pages** (left sidebar).
8. Under "Build and deployment" → Source: **Deploy from a branch**. Branch: **main** → folder **/ (root)** → **Save**.
9. Wait 1–2 minutes. GitHub shows a live link like `https://YOURNAME.github.io/poweredbycoachtc/`. Open it — the site should load.

---

## PART 2 — Point your GoDaddy domain at it

1. Log in at https://godaddy.com → **My Products** → find **poweredbycoachtc.com** → **DNS** (or "Manage DNS").
2. Delete any existing **A record** with name `@` that points to a "Parked" or forwarding address (GoDaddy adds these by default). Leave everything else alone.
3. Add these **five records** (Add → pick type → fill Name + Value → Save each):

   **Four A records** (Name is `@` for all four):

   | Type | Name | Value |
   |------|------|-------------------|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |

   **One CNAME record:**

   | Type | Name | Value |
   |------|------|----------------------|
   | CNAME | www | YOURNAME.github.io |

   (Replace `YOURNAME` with your actual GitHub username — same one from the github.io link in Part 1. Keep the trailing part `.github.io`.)

4. Save.

---

## PART 3 — Connect the domain in GitHub + turn on HTTPS

1. Back in GitHub → repo **Settings** → **Pages**.
2. Under "Custom domain" it should already show `poweredbycoachtc.com` (from the CNAME file). If not, type it and click **Save**.
3. GitHub runs a DNS check. This can take anywhere from a few minutes to a few hours while DNS propagates — that's normal.
4. Once the check passes, tick **Enforce HTTPS**. (If the tickbox is greyed out, wait — it appears after the domain verifies.)

Done. `https://poweredbycoachtc.com` and `https://www.poweredbycoachtc.com` both serve your site.

---

## If something looks off

- **Site loads on github.io but not on your domain yet** → DNS still propagating. Wait and recheck. Use https://dnschecker.org and search `poweredbycoachtc.com` (type A) — you want to see the four 185.199.x.x addresses.
- **"Enforce HTTPS" greyed out** → domain not fully verified yet; give it more time.
- **Images missing** → make sure the whole `assets` folder uploaded (all files inside it), not just some.
- **404 page** → confirm `index.html` is at the top level of the repo, not inside a subfolder.

---

## To update the site later

Edit or re-upload files in the GitHub repo → Commit. Changes go live in a minute or two. No need to touch DNS again.
