# Publish your own clean, branding-free website (GitHub Pages)

This gives you a real website with your own URL, no Claude logo/branding bar, and live score updates for every visitor. It takes about 10–15 minutes and everything is free.

You need two things: a free Firebase project (stores the live data) and a free GitHub Pages site (hosts the page). Do them in order.

---

## PART 1 — Create the free database (Firebase)

1. Go to **https://console.firebase.google.com** and sign in with any Google account.
2. Click **"Add project"**.
   - Give it any name, e.g. `cs-champions-league`.
   - Click Continue.
   - You can turn OFF Google Analytics (not needed) — click Continue / Create project.
   - Click **"Continue"** once it's done.
3. In the left sidebar, click **Build → Realtime Database**.
4. Click **"Create Database"**.
   - Pick any location (closest to you is fine).
   - Choose **"Start in test mode"**. Click **Enable**.
5. In the left sidebar, click the **gear icon (⚙) → Project settings**.
6. Scroll down to **"Your apps"**. Click the **`</>`** (web) icon.
   - Give the app any nickname, e.g. `scoreboard`.
   - Click **"Register app"**.
7. Firebase now shows you a code block containing a `firebaseConfig` object, like:
   ```js
   const firebaseConfig = {
     apiKey: "AIzaSy...",
     authDomain: "cs-champions-league.firebaseapp.com",
     databaseURL: "https://cs-champions-league-default-rtdb.firebaseio.com",
     projectId: "cs-champions-league",
     storageBucket: "cs-champions-league.appspot.com",
     messagingSenderId: "123456789",
     appId: "1:123456789:web:abcdef123456"
   };
   ```
   **Copy this entire block** — you'll need it in Part 2. Then click **"Continue to console"**.

---

## PART 2 — Add your config to the website file

1. Open **`index.html`** (the file I've given you) in any text editor (Notepad, TextEdit, VS Code, etc.).
2. Press **Ctrl+F** (or Cmd+F on Mac) and search for: `YOUR_API_KEY`
3. You'll land on a block that looks like this:
   ```js
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT.firebaseapp.com",
     databaseURL: "https://YOUR_PROJECT-default-rtdb.firebaseio.com",
     projectId: "YOUR_PROJECT",
     storageBucket: "YOUR_PROJECT.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```
4. **Delete this whole block** and paste in the real one you copied from Firebase in Part 1, step 7.
5. Save the file.

---

## PART 3 — Publish it for free (GitHub Pages)

1. Go to **https://github.com** and sign up for a free account if you don't have one.
2. Click the **"+"** icon (top right) → **"New repository"**.
   - Name it anything, e.g. `cs-champions-league`.
   - Set it to **Public**.
   - Click **"Create repository"**.
3. On the new repo's page, click **"uploading an existing file"** (or drag files onto the page).
4. Upload:
   - `index.html`
   - the whole `assets` folder (containing `background.jpg`)
5. Click **"Commit changes"**.
6. Go to the repo's **Settings** tab → **Pages** (left sidebar).
7. Under **"Branch"**, choose `main` and folder `/ (root)`, then click **Save**.
8. Wait about a minute, then refresh the page — GitHub will show you your live URL, something like:
   `https://yourusername.github.io/cs-champions-league/`

That's your website — a plain URL, no Claude branding, no logo bar, works for anyone.

---

## Admin access & password (unchanged)

- Viewer link: `https://yourusername.github.io/cs-champions-league/`
- Admin link: same URL + `?admin=1`, e.g.
  `https://yourusername.github.io/cs-champions-league/?admin=1`
- Admin password: `CSAcademy#2026!Turf`

Only the `?admin=1` link ever shows the gear icon / Admin tab — the normal link never does.

---

## Optional — lock down the database once it's working

Test mode (Part 1, step 4) leaves the database open to anyone with its address. Once everything looks right:

1. Firebase console → **Realtime Database → Rules**.
2. Set:
   ```json
   {
     "rules": {
       ".read": true,
       ".write": true
     }
   }
   ```
   This keeps the same open behavior (matches how the page works today — no login, just the in-page password), but confirms the rule explicitly rather than relying on test mode's temporary default. Click **Publish**.

---

## Once it's live

Send me the final GitHub Pages URL and I'll generate QR codes for both the viewer link and the admin link.
