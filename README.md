# Takari Canal Tracker

Live open/closed status of the Takari canal network (Krishna Koyna LIS, Takari part) on a satellite map, with a days-open summary per distributary.

- `index.html` is the whole site.
- `canals.js` holds the 294 canal lines and attributes taken from the MAHACANALLI KMZ.
- `config.js` holds the Firebase settings for live data.
- `database.rules.json` holds the database rules: anyone can view, only signed-in staff can change status.

## One-time setup

### 1. Firebase (live data and staff sign-in)

1. Open https://console.firebase.google.com with a Google account and create a project (Analytics is not needed).
2. Build > Realtime Database > Create database. Choose a location and start in locked mode.
3. In the Realtime Database "Rules" tab, replace the rules with the contents of `database.rules.json` and publish.
4. Build > Authentication > Get started > Email/Password > Enable.
5. Authentication > Users > Add user. Add one email and password for each person who may open and close canals.
6. Project settings (gear icon) > Your apps > Web (`</>`) > register an app. Copy `apiKey`, `authDomain`, `databaseURL`, `projectId` and `appId` into `config.js`.
7. Authentication > Settings > Authorized domains > add `<your-github-username>.github.io`.

### 2. GitHub Pages (hosting)

1. Repository > Settings > Pages.
2. Source: "Deploy from a branch", branch `main`, folder `/ (root)`. Save.
3. After a minute the site is live at `https://<your-github-username>.github.io/<repository-name>/`.

## Using it

- Anyone with the link can see the map, the list and the summary. No account is needed.
- Staff tap "Staff sign in", then tap a canal and use "Open now" or "Close now". A past time can be entered under "Enter a different time".
- Summary shows days, hours and openings per canal for a chosen period, and downloads as CSV.

## Map credits

Satellite imagery: Esri, Maxar, Earthstar Geographics. Place names: OpenStreetMap contributors, CARTO. Map library: Leaflet.
