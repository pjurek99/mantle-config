# Mantle config

Settings the Mantle app (St. Elizabeth of Hungary, Wyckoff) reads every time it refreshes.
Everything here is public. Never put private information in it.

The app reads `config.json` from this site's GitHub Pages address. Changes reach phones the next
time Mantle refreshes: when someone opens the app, or in the background a few times a day.
GitHub can take up to about 10 minutes to publish an edit.

## How to edit

1. Open `config.json` and click the pencil (Edit).
2. Make the change (examples below). Keep the quotes, commas and brackets exactly as shown.
3. Click **Commit changes**.

If the file has a typing mistake, the app ignores it and keeps the last good version,
so nothing breaks. Check your edit by pasting the file into https://jsonlint.com.

## Send an alert

Add an entry to `"alerts"`. Each `id` must be new; each one is delivered once.
`level` is `urgent` (pop-up), `normal` (banner) or `easy` (badge only).
`expires` is the last day it shows (YYYY-MM-DD).

```json
"alerts": [
  { "id": "snow-2026-12-14", "level": "urgent", "title": "Church closed today",
    "body": "All Masses are cancelled because of snow.", "expires": "2026-12-14" }
]
```

To withdraw an alert, delete its entry.

## Cancel or add a Mass

The Mass schedule comes from the parish calendar on saintelizabeths.org. Removing one date from a
Mass in that calendar already shows it as cancelled. Use these only for changes that aren't there.

Times are minutes after midnight: 7:00 a.m. = 420, 9:00 a.m. = 540, 12:00 p.m. = 720,
5:00 p.m. = 1020, 7:00 p.m. = 1140.

```json
"cancel": [ { "d": "2026-11-26", "m": 540, "t": "Thanksgiving: one Mass at 10:00" } ],
"add":    [ { "d": "2026-11-26", "m": 600, "t": "Thanksgiving Day Mass", "p": "Church" } ]
```

Leave `"m"` out of a cancellation to cancel every Mass that day.

## Notice banner

`"notice"` shows a line at the top of the app, for example `"Parish office closed Friday"`.
`"noticeURL"` is an optional link for it. Set both back to `""` to remove it.

## Other settings

- `baseURL`: the parish website. Leave as is.
- `minAppVersion`: asks people on older versions of Mantle to update.
- `parish` (optional): a full replacement for the parish facts built into the app (office hours,
  holiday closures in `office.closedDates`, staff, links). Ask before using it.
