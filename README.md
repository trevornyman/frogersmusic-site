# frogersmusic.com

One static page that every social bio links to. No framework, no build step.

## Edit
Everything lives in the `window.SITE` block at the top of `index.html`.

- **Release day:** set `RELEASED: true`. The main button switches to Bandcamp, the headline says "Out now", and the email form stays below it.
- Fill in `releaseDate`, `aboutLine`, the Spotify/YouTube/Instagram/TikTok URLs, and `reverserSpotify` (the Spotify embed shows once that's a real track link).
- `bandcampPreorder`: add the pre-order URL if one exists. It shows as a second button before release.
- `bandcampEmbedId`: the album ID from Bandcamp's Share/Embed dialog. It shows a player in the released state.
- Cover: drop a square `cover.jpg` (1500 px or larger, compressed to under ~300 KB) in this folder. Until then a placeholder shows.

## Services
- **Email: Buttondown.** Set `buttondownUser` to your Buttondown username. Each subscriber gets a tag for where they came from (`src-ig`, `src-yt`, `src-direct`, …). Nothing is stored on this site.
- **Analytics: Plausible.** It reads `?ref=` as the traffic source on its own. It also logs `Signup`, `Main Click`, `Bandcamp Click` and `Link Click` events with a `ref` property. To see them, add those goals and the `ref` custom property in Plausible. If you'd rather use something else, delete the Plausible script tags.
- **Bandcamp:** turn on "require email address for free downloads" in the album settings.

## Bio links
| Platform | URL |
|---|---|
| Instagram | https://frogersmusic.com/?ref=ig |
| YouTube | https://frogersmusic.com/?ref=yt |
| TikTok | https://frogersmusic.com/?ref=tt |
| Spotify | https://frogersmusic.com/?ref=sp |

## Deploy (GitHub Pages)
1. Create an empty GitHub repo, then add it as the remote and push.
2. In the repo, go to Settings → Pages, set Source to `main` / root, and enter `frogersmusic.com` as the custom domain (the `CNAME` file is already here).
3. At your registrar, add A records for `@` pointing to 185.199.108.153, .109.153, .110.153 and .111.153. Add a CNAME record for `www` pointing to `<user>.github.io`.
4. Once the certificate is issued, tick "Enforce HTTPS".

Netlify or Cloudflare Pages work too: point them at the repo, leave the build command empty, and set the publish directory to `/`.
