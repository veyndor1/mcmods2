![mc-mods2](banner.svg)

# mcmods2

## Current pack: Mirza gaga denemesi

The 2026-10-15 publication contains **142 mod JARs** and **9 changed optimization
config files**, grouped into 8 manifest entries. Mod binaries and selected config
files are copied without editing their contents. Other mod settings are generated
by the mods or kept by the player.

Published config files:

- `asyncparticles/asyncparticles.json`
- `asyncparticles/asyncparticles-mixin.properties`
- `bons_and_furious.properties`
- `c2me.toml`
- `embeddium-options.json`
- `flerovium.json`
- `flywheel-client.toml`
- `modernfix-mixins.properties`
- `saturn-optimizations.toml`

The selection includes the final seven engine/optimization config files and the
retained Embeddium/Flywheel worker settings. Restored graphics configs, vanilla
`options.txt`, worlds, launcher settings, account data and test tools are excluded.
The selected files are complete files; graphics fields already present in
`embeddium-options.json` are part of that file. This publication does not promise
a particular FPS or reproduce machine-specific GPU, memory or launcher settings.

`mods-to-host/` and `config-to-host/` contain the current publishing inputs.
`mods/` and `configs/` contain immutable download artifacts. Older hashed artifacts
remain available so an existing download can finish safely. `server-mods.json`
selects the active pack.

The distribution repository for Minecraft **1.20.1 / Forge 47.4.10 / Java 17**.
Players download the complete `AutoModUpdater-1.jar` from the
[latest updater release](https://github.com/veyndor1/mcmods2/releases/latest)
and place it in their Forge 1.20.1 profile's `mods` directory. The regular JAR filename has the same contents. No account,
token or additional service is required.

## Publishing

In the updater source project, put compatible mod JARs directly in
`mods-to-host`. Put the **contents** of the desired config directory in
`config-to-host`; do not wrap them in another `config` directory.
Run `make-manifest.bat`, then upload the contents of `publish-mc-mods2` to this
repository's `main` branch. Upload content-addressed artifacts first and
`server-mods.json` last. Keep old artifact URLs available for clients already downloading.
Attach the updater release JAR to a GitHub Release when distributing the updater itself.

Each published config root is authoritative. On every startup, a changed root is
backed up in the game's `.automodupdater/packs/mc-mods2-1.20.1/config-backups` and
replaced completely. Roots absent from the publication remain untouched.
The updater's own `config/automodupdater.json` is protected and excluded.
Config directories absent from the publication are left alone and can be created by
their mods on normal startup.
Config-only changes do not require a restart. Configs accompanying changed mods
are activated with those mods after the current game exits.

Repository visibility is public so the updater can download without credentials.
Only the repository owner should have write access. Third-party mod binaries and
config content retain their own licensing terms.

## Related projects

- [AutoModUpdater](https://github.com/veyndor1/AutoModUpdater): private updater source,
  build tools and owner releases; its default branch is `1.20.1`. Access requires
  the owner's permission.
- [Public updater releases](https://github.com/veyndor1/mcmods2/releases): complete
  obfuscated JARs, license notices and SHA-256 checksums for players.
- [mc-mods](https://github.com/veyndor1/mc-mods): related private pack assets,
  maintained separately. It is not this updater's fallback download source.

The updater uses a proprietary binary-use license. The repository metadata
license does not relicense the updater or third-party mod binaries.
