# LOOMTRIC Agent Instructions

## Project Shape

- This is a hand-authored static HTML/CSS website; it has no framework, bundler, backend, package manifest, or automated test suite.
- Root pages are `index.html`, `services.html`, `about.html`, `projects.html`, and `contact.html`.
- Store pages live under `products/`; shared styles are in `css/style.css`; `js/` is currently empty.
- Navigation, footer markup, and some styling are duplicated across pages. Preserve the existing page structure unless the task requires a coordinated update.

## Working Rules

- Before editing, inspect the relevant HTML page, its linked stylesheet, local assets, and any nearby page with the same pattern.
- Keep changes focused and use existing HTML/CSS conventions. Use relative paths appropriate to the file depth: product pages need `../` when referring to root assets or pages.
- Prefer shared rules in `css/style.css` over new inline styles when changing reusable behavior. Do not introduce a framework or build system for a static-site change.
- Preserve external dependency usage unless the task explicitly changes it. Google Fonts, Font Awesome, Unsplash, and WhatsApp links require network access.
- Do not assume a form has a server-side handler: the contact form currently uses `mailto:` behavior.

## Autonomous Validation

1. After each substantive edit, run the narrowest relevant check immediately.
2. For static pages, start a local server from the workspace root with `python -m http.server 8000` and inspect the affected URL when browser tooling is available. Direct file opening is a fallback, but a server catches relative-path mistakes.
3. Check the browser console, failed network requests, page layout at desktop and mobile widths, navigation targets, and visible fallback/error states.
4. If a command, browser check, or validation reports an error, read the complete output, identify the owning file, patch the root cause, and rerun the same check. Continue until the affected workflow is clean.
5. If no executable check exists, inspect all changed links and asset paths and report the limitation clearly.
6. Do not ask for user intervention during ordinary debugging. Ask only when an external secret, unavailable tool, or genuinely ambiguous product requirement blocks progress.

## Known Constraints

- There is no defined build or test command; do not invent one. Use static serving plus focused browser/manual checks.
- Asset availability and relative paths are common failure points, especially under `products/`.
- Some pages intentionally rely on external images and CDN resources, so distinguish network failures from local markup/CSS defects.