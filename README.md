# Chrome vs Firefox extensions

Start by collecting popular Chrome extensions:

```sh
node popular_chrome_extensions.mjs --limit 100 --output data/popular-chrome-extensions.json
```

Requires Node.js 18 or later. The script uses the public Chrome Web Store category and detail pages. It needs no API key. Output includes each extension's ID, name, store URL, displayed user count, rank, and the categories where it appeared. Failed detail-page lookups are recorded in `errors`.

Google's [documented Chrome Web Store API](https://developer.chrome.com/docs/webstore/api/reference/rest) does not offer a public store-wide popularity ranking. This script samples extension category pages, then sorts their union by the user count shown on each detail page. Consequently, it can miss an extension absent from those category pages. Store user counts are rounded, so ranks with equal counts are arbitrary. The store's HTML can change and require a parser update.

Firefox availability and equivalent matching are future steps; this script produces the Chrome candidate list for them.
# chrome-vs-firefox
