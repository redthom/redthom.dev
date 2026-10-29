# redthom.dev

Source for [redthom.dev](https://redthom.dev), the personal site of Blake Smith.

Plain HTML and CSS, no framework and no build step. Served by Cloudflare Workers static assets.

## Layout

```
public/            everything that gets served
  index.html       the page
  404.html         served for unknown paths (not_found_handling: "404-page")
  styles.css       light theme by default, dark via prefers-color-scheme
  _headers         response headers (not served)
  assets/fonts/    Inter and JetBrains Mono, Latin subset, self-hosted (SIL OFL, licenses alongside)
  assets/img/      Triplo gameplay clip and poster frame
wrangler.jsonc     Cloudflare config
```

## Local preview

Any static server works:

```sh
python3 -m http.server -d public 8080
```

Or with Cloudflare's own runtime (also applies `_headers` and the 404 rule):

```sh
npx wrangler dev
```

## Deploy

Pushing to `main` deploys automatically through the Cloudflare Workers Git integration.
Manual deploy: `npx wrangler deploy`.

## Updating

- **Résumé:** put `resume.pdf` in `public/`, then uncomment the résumé link in `index.html` (search for `resume.pdf`).
- **New project:** copy the `<article class="project">` block in `index.html`. The card layout stacks automatically.
- **Cached assets:** files under `/assets/` are cached for a year. Give a changed file a new name (e.g. `triplo-turn-v2.mp4`) rather than overwriting it.

## Credits

Triplo is a board game designed by Viktor Bautista i Roca; the project shown here is an independent implementation of it in Odin.
Fonts: [Inter](https://github.com/rsms/inter) and [JetBrains Mono](https://github.com/JetBrains/JetBrainsMono), SIL Open Font License 1.1.
