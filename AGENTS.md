# Repository Guidelines

## Project Structure & Module Organization
- `assets/`: JavaScript, CSS, images (ES modules like `product-price.js`, styles like `base.css`).
- `layout/`: Global Liquid layouts.
- `sections/` and `blocks/`: Theme sections and reusable blocks. Prefix internal/private blocks with `_` (e.g., `blocks/_image.liquid`).
- `snippets/`: Small Liquid partials rendered via `{% render %}`.
- `templates/`: Page templates (`.json` or `.liquid`). Files marked “may be updated by the theme editor” should be edited cautiously.
- `locales/`: Translations and schema copy.
- `config/`: Theme settings.

## Build, Test, and Development Commands
- `shopify login --store <store-domain>`: Authenticate to a store.
- `shopify theme dev`: Run locally with live reload and editor previews.
- `shopify theme push`: Upload theme changes (use flags `--unpublished` for drafts).
- `shopify theme pull`: Pull remote changes to stay in sync.
- `shopify theme check`: Lint Liquid/JSON against Shopify rules.

## Coding Style & Naming Conventions
- Indentation: 2 spaces across Liquid/JSON/JS/CSS.
- Files: kebab-case for sections/snippets/assets (e.g., `predictive-search.js`). Use leading `_` for internal blocks/snippets.
- Liquid: Prefer `{% render %}` over `include`. Keep selectors/classes consistent with existing patterns; scope styles within `.shopify-section` roots where possible.
- JavaScript: ES modules in `assets/`. Avoid globals; target via data attributes/selectors. Keep filenames aligned with component/section names.
- CSS: Reuse existing custom properties and tokens; avoid inline styles.

## Testing Guidelines
- Run `shopify theme check` and address all warnings.
- Validate section/block `schema` JSON. Sanity-check key templates (home, product, collection, cart, search) in `shopify theme dev`.
- For UI changes, add before/after screenshots and test in both storefront and theme editor (design mode).

## Commit & Pull Request Guidelines
- Commits: imperative, concise, scoped (e.g., "Add variant image to picker"). Reference issues when applicable.
- PRs: include summary, affected files/sections, screenshots, reproduction steps/URLs, and any localization updates in `locales/`.

## Security & Assets
- Do not commit secrets or store-specific data. Prefer uploading media via Admin and reference with `shopify://` URLs. Keep binary assets small.

## Agent-Specific Instructions
- Keep changes minimal and localized; do not reformat unrelated files. Follow the structure and naming above when adding new sections, blocks, snippets, or assets.
