# digirequests

Source for six Digitakt I mods by sumedho, for OS 1.53 and 1.54. Each mod is
an Elekloader format-2 module for Core 2.1, the core Modwerk's catalogue ships, and each folder is laid out
for Modwerk's source builder.

| Mod | Version | Requires | Folder |
| --- | --- | --- | --- |
| MIDI Retrig | 2.0.1 | Core 2.1 | [modules/midi-retrig](modules/midi-retrig) |
| CC Assignment Names | 2.1.1 | Core 2.1, DT Support | [modules/cc-names](modules/cc-names) |
| Euclidean Sequencing | 1.1.5 | Core 2.1, DT Support | [modules/euclidean](modules/euclidean) |
| RAM Record and Playback | 1.3.1 | Core 2.1, Machine Pages 1.2 | [modules/ram-machines](modules/ram-machines) |
| Per-step Note Accumulator | 1.1.1 | Core 2.1 | [modules/note-accumulator](modules/note-accumulator) |
| Sample Snap and Crossfade | 0.2.2 | Core 2.1 | [modules/sample-tools](modules/sample-tools) |

`dependencies/dt-support` is a small shared lifetime hook used by CC
Assignment Names and Euclidean Sequencing. `dependencies/machine-pages` is
irpina's Machine Pages 1.1 from Elekloader
[`3acac10e`](https://github.com/irpina/elekloader/tree/3acac10ea86882a2ea51c9377ac6bd58fc4fec57/mods/machine-pages),
adapted to run on Core 2.1 (version 1.2; see its `NOTICE`). Core 2.1 itself is
irpina's, as pinned in Modwerk's catalogue.

## Layout

Each folder holds:
- `src/`: one `release-153/` and one `release-154/` source tree, selected at
  compile time by `DT_OS154`. The top-level files only include the right one.
- `build.json`: what to compile and link, the events subscribed, and the
  patch sites for each OS.

A patch site gives its address, length and the SHA-256 of the stock bytes it
replaces. The builder checks those bytes in your own copy of the stock OS.

## Building

Use your own stock `Digitakt_OS1.53.syx` or `Digitakt_OS1.54.syx`. This
repository contains no Elektron firmware, firmware bytes or tables. Modwerk
builds these folders in its browser builder; see its
[source build guide](https://github.com/repeat98/modwerk/blob/main/docs/ELEMOD_SOURCE_BUILDS.md).
Do not install a 1.53 build on 1.54, or the reverse.

User documentation, screenshots, test reports and changelogs are kept with
each mod's Modwerk listing.

## Licence

GPL-2.0-or-later; see each folder's `LICENSE` and `NOTICE`. The
`core3.h` header copied into the sources is irpina's, under the same licence;
the mods use only its declarations that Core 2.1 provides, and `core21.h`
names the firmware locations Core 2.1 does not export.
