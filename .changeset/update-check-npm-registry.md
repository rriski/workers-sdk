---
"wrangler": patch
"@cloudflare/vite-plugin": patch
"@cloudflare/workers-utils": patch
---

Query the npm registry set in `npm_config_registry` when checking for updates

The update check behind the "update available" notice always queried `https://registry.npmjs.org/`, so environments that only allow traffic to an npm mirror made a blocked request on every run. It now uses the registry from the `npm_config_registry` environment variable, which npm, npx and `npm run` also set from `.npmrc`, and falls back to the public registry when it is unset.
