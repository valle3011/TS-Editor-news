# TS Editor — news feed

`news.json` is the feed the TS Editor's **What's new** panel reads on the welcome
page. It lives here, apart from the editor's source, because that repository is
private and the panel fetches this file anonymously over HTTPS.

Editing it publishes news — the app picks the change up on its next start
(raw.githubusercontent caches for a few minutes).

## Format

```json
{
  "latest_version": "5.3.0",
  "url": "https://github.com/valle3011/TS-Editor/releases",
  "items": [
    {"title": "…", "date": "2026-07-17", "text": "…", "url": "https://…"}
  ]
}
```

- `latest_version` — set it **above** the running build's version to raise the
  green update banner with a download link. Leave it empty for no banner.
- `url` — where the banner's Download link points.
- `items` — newest first; the panel shows up to 25. `text` and `url` are
  optional.

Write `title` and `text` as **plain text**: the panel escapes them, so an HTML
entity here would show up literally.

The reader is `libs/ui/widgets/KisWhatsNewWidget.cpp` in the TS Editor repo.
