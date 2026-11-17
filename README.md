# RSS-Bridge Filter Editor

**Live version: https://thescrabi.github.io/rss_bridge_filter_managment_ui/**

A small static web page for editing existing [RSS-Bridge](https://github.com/RSS-Bridge/rss-bridge)
[Filter bridge](https://rss-bridge.org/bridge01/#bridge-FilterBridge) URLs.

RSS-Bridge's own UI lets you *create* a filtered feed URL, but you can't paste an
existing URL back in to change it. This tool fills that gap:

1. Paste an existing Filter bridge URL (`...?action=display&bridge=FilterBridge&url=...&filter=...`).
2. The form is filled with all its parameters: feed URL, name, filter regex, keep/hide,
   filter targets (title, content, author, URI), options, length limit and output format.
3. Edit anything and copy the newly generated URL.

## Features

- Works with any RSS-Bridge instance (the base URL is taken from the pasted link).
- Filters like `foo|bar|baz` are shown as separate terms that can be removed or added
  one by one (with optional regex escaping).
- Warnings for common mistakes: using both `/` and `#` in the filter (rejected by
  RSS-Bridge), empty alternatives that match everything, invalid regexes, no filter
  target selected.
- A local test box to check whether a sample title would be kept or hidden
  (uses JavaScript regex, which is close to but not identical with PHP's PCRE).
- Unknown query parameters (e.g. `_cache_timeout`) are passed through unchanged.
- The editor state is kept in the page URL after `#`, so you can bookmark or share a
  pre-filled editor.

## Hosting

It's a single `index.html` with no dependencies or build step. Everything runs in the
browser; nothing is sent anywhere. To host it yourself, serve the file from any static
host, e.g. GitHub Pages (Settings → Pages → deploy from branch `master`, folder `/`).
