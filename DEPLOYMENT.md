# Deploying to Cloudflare Pages

This repository is configured as a static Cloudflare Pages site.

## Project settings

- Project name: `x-algorithm-explainer`
- Static output directory: `public`
- Wrangler config: `wrangler.toml`

## If your Cloudflare deploy command is `npx wrangler deploy`

The `wrangler.toml` file includes:

```toml
[assets]
directory = "./public"
```

That lets Cloudflare's Workers deploy command upload the static HTML assets
from `public`.

## Deploy to Pages with Wrangler

For local interactive deployment, authenticate once:

```shell
npx -y wrangler@latest login
```

Then deploy:

```shell
npx -y wrangler@latest pages deploy public --project-name x-algorithm-explainer
```

For non-interactive environments, create a Cloudflare API token with Pages
deployment access and export it before deploying:

```shell
export CLOUDFLARE_API_TOKEN="<your-token>"
npx -y wrangler@latest pages deploy public --project-name x-algorithm-explainer
```

Wrangler prints the deployment URL after a successful upload.
