# CLAUDE.md

## Project purpose

Fork of [haakonnessjoen/MAC-Telnet](https://github.com/haakonnessjoen/MAC-Telnet) — Linux console tools for connecting to and serving devices using MikroTik RouterOS' MAC-Telnet protocol. The VyOS fork is stale (last upstream activity 2014) and is retained only for packaging into VyOS images.

## Tech stack

- C, with autotools (`configure.ac`/`Makefile.am`) plus a top-level `Makefile`. License GPL-2.
- Source files: `mactelnet.c`, `mndp.c`, `macping.c`, `mactelnetd.c`, `autologin.c`, `interfaces.c`, `console.c`, `users.c`, ...

## Build / test / run

```
./autogen.sh        # if present
./configure
make all
make install
```

Per upstream README: `make all install`. No automated test suite.

## Repository layout

Flat C source layout: per-binary `.c` files at top level (`mactelnet.c`, `mactelnetd.c`, `mndp.c`, `macping.c`), shared helpers (`config.c`, `interfaces.c`, `users.c`, `console.c`), `protocol.c/h`, `md5.c/h`, plus `Makefile`, `LICENSE` (GPL-2). Internationalisation under `po/`.

## Cross-repo context

Per-package C binary; one of the small native packages built into VyOS images via `VyOS-Networks/vyos-build-packages` and consumed at ISO assembly time by `vyos/vyos-build`. Not in the canonical 14-repo `repos.toml` build set; built manually when needed.

## Conventions

- Commit / PR title format: `component: T12345: description` (Phorge task ID mandatory). Enforced by `vyos/.github` reusable workflows where consumed.
- Branch model: `current` (rolling), `circinus` (1.5 LTS), `sagitta` (1.4 LTS), `equuleus` (1.3 LTS).
- Fork of upstream — keep VyOS-specific patches minimal; prefer upstreaming.

## Mirror relationship

Mirror twin: `VyOS-Networks/MAC-Telnet`. Canonical side is **here** (`vyos/MAC-Telnet`).

## Notes for future contributors

- Stale codebase — last meaningful upstream activity in 2014. Touch only when strictly necessary for VyOS packaging.
- Fork parent: `haakonnessjoen/MAC-Telnet`.
- License: GPL-2.

---

This file is mirrored on Confluence: [`vyos/MAC-Telnet`](https://internal.confluence.vyos.com/wiki/spaces/VYOS/pages/818184542). The Confluence page also carries the per-repo audit data (settings, workflows, secret counts, hygiene) that complements this CLAUDE.md. Edit either side; resync via the documentation pipeline.
