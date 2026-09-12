# habbo-jp-translation

Japanese localization data for a modified Habbo client (built on
[HabboAirPlus](https://github.com/LilithRainbows/HabboAirPlus)) that adds
full Japanese language support (interface, catalog, help pages, and
in-chat Japanese text) to the official Habbo client.

This is **not** a private server or an emulator. It's a set of data files
loaded at runtime by a modified launcher to translate the official,
currently-running Habbo client into Japanese, in tribute to the original
Japanese hotel (habbo.jp), which closed in 2009.

## Files

| File | Purpose |
|---|---|
| `texts_jp.txt` | Interface strings (menus, buttons, notifications, tutorials, achievements, etc.), keyed the same way as Habbo's official `external_texts.txt`. |
| `catalog_jp.txt` | Catalog page names and descriptions, keyed by page name (not page ID, which is hotel-specific and unstable). |
| `habbopages_jp.txt` | Content for the in-client FAQ pages, keyed by page path. |
| `jpcharset.txt` | The ordered list of Japanese characters (and a few extra symbols) supported by the client's modified font, used to encode/decode chat messages. |

## How it works

The modified client loads these files at boot and overlays their values on
top of the hotel's native language, keyed by Habbo's own localization keys.
Because localization keys are shared across every Habbo hotel, this
translation works on any server, not just one specific hotel.

Chat messages are encoded client-side into plain ASCII before being sent,
since the server only relays Latin-1 text. Any client running the same
modified launcher decodes them back into Japanese; anyone else sees the
raw encoded text.

## `jpcharset.txt` (important note)

The order of characters in this file is **positional**: each character's
index is used to encode chat messages. Characters must only ever be
**appended at the end** of the block, never inserted or reordered in the
middle (!!!), or previously encoded messages will decode incorrectly. See the
comments at the top of the file for details.

## Related Tools

Catalog data (page IDs, page names, collection descriptions) and external
text files used throughout this project are captured with
[Habbo-Data-Extraction](https://github.com/maxph3/Habbo-Data-Extraction),
a set of scripts developed by Max for dumping catalog structure via G-Earth
and downloading game data files across Habbo hotel domains.

## Credits

Built on [HabboAirPlus](https://github.com/LilithRainbows/HabboAirPlus)
by Lilith. Japanese terminology follows official habbo.jp usage wherever a
historical reference was available.

Maintained by [Yohaku](https://github.com/yohaku404). Font-rendering help
and the HTML archives used as the basis for the catalog and FAQ page
translations were contributed by [Max](https://github.com/maxph3).
