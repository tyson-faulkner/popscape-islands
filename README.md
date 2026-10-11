# popscape-islands

A genre-neutral starting point for a link-shareable three-player browser game. The rules, visuals, and save format will be chosen before game behavior is added.

## Release flow

- `main` is the production branch.
- Make changes on a feature branch and open a pull request.
- Cloudflare Pages builds a preview for the branch or pull request. Check the preview link before merging.
- Merging to `main` updates the public game link. Visitors only need a browser; there is nothing to install.
- Static HTML is hosted from the repository root, with no build command.

## Saves and multiplayer

Supabase will provide the database and realtime service after the lobby, player identity, and save behavior are decided. Turn on Row Level Security (RLS) for game tables and permit only the intended room members to read or write data. Do not guess policies before the room flow is defined.

## Protecting keys

The project URL and publishable/anon key are designed to be visible in browser code. RLS must protect the data. Never put a Supabase `service_role` or secret key in browser code, GitHub, or public build settings. Keep server-only secrets in a server-side secret store. `.gitignore` excludes local environment files and generated configuration.

## Current state

`index.html` is a hosting placeholder; it is not a playable game. The next infrastructure step is to connect Cloudflare Pages with `main` as production and feature branches as previews. Supabase should be connected after we decide how rooms and persistent saves should work.
