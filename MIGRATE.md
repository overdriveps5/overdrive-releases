# Switch to the single-file install

Overdrive now ships as one file, `Overdrive-PPSA99058.exfat`: an exFAT image of the whole app that
ShadowMountPlus mounts as it is. One file to copy instead of thousands, and no permission fixes.
**The folder install (`/data/homebrew/PPSA99058`) will stop getting updates soon**, so switch once
by hand; after that, Overdrive keeps updating itself as before.

It takes a few minutes. Close Overdrive before you start.

## 1. Download the image

Download `Overdrive-PPSA99058.exfat.zip` from the
[latest release](https://github.com/overdriveps5/overdrive-releases/releases/latest) and unzip it on
your computer. You get a single file, `Overdrive-PPSA99058.exfat` (about 780 MB). Keep that name.

## 2. Delete the old folder

Delete the `PPSA99058` folder wherever you installed it: usually `/data/homebrew/PPSA99058`, but
it may also be under a USB drive (`/mnt/usb0/homebrew/PPSA99058`, `/mnt/usb1/...`) or another
folder ShadowMountPlus scans. Use your FTP client, PS5Upload's file browser or a file manager on the
console.

What you keep:

- **Your downloads and the download list.** Downloaded games stay where they are, and the list
  lives in `/data/ps5-react/PPSA99058`, outside the app folder.
- **Your favorites, recently viewed games and language should be kept too.** They live in the app's
  data folder on the console, which stays as long as Overdrive stays in the console's library. If
  they reset after the switch, this is why: the console treated it as a new install. To make that
  less likely, do step 3 right away (ShadowMountPlus's `auto_remove_missing_games`, off by default,
  removes a title whose source has been missing for 5 minutes), and do not delete Overdrive from the
  console's own settings or Storage screen.

## 3. Copy the image

Copy the single file `Overdrive-PPSA99058.exfat` to `/data/homebrew/`, so you end up with
`/data/homebrew/Overdrive-PPSA99058.exfat`. Do not change its permissions.

- **FTP:** connect to the console's FTP server and upload the file into
  `/data/homebrew/`. Upload it in binary mode, which every modern client uses by default.
- **PS5Upload:** send the file with `/data/homebrew/` as the destination folder.
- **USB:** copy the file to a `homebrew` folder at the root of an exFAT drive and plug it into the
  console. ShadowMountPlus mounts it from there (`/mnt/usb0/homebrew/`); there is no need to move it
  to the internal storage. Keep the drive plugged in to use Overdrive.

## 4. Open Overdrive

With ShadowMountPlus running, it picks the image up within a few seconds. If Overdrive does not
start, run ShadowMountPlus's scan again (or restart the console), then open Overdrive from the home
screen. The notice about folder installs on its home screen is gone.

## Troubleshooting

<details>
<summary><b>Overdrive does not show up, or does not open</b></summary>

- Check that the file is at `/data/homebrew/Overdrive-PPSA99058.exfat` (or `homebrew/` on the USB
  drive), not inside another folder, and that its size matches the unzipped file: a copy cut short
  does not mount.
- Check that `/data/homebrew/PPSA99058` is gone. With both the folder and the image there,
  ShadowMountPlus sees the same title twice; delete the folder.
- Check that ShadowMountPlus is running: it must be loaded after every reboot.
</details>

<details>
<summary><b>Overdrive shows up twice, or ShadowMountPlus reports a duplicate title ID</b></summary>

Two copies are installed: the old folder and the image, or the image on both the console and a USB
drive. Keep one: delete `/data/homebrew/PPSA99058` (or the extra image), then run ShadowMountPlus's
scan again.
</details>

<details>
<summary><b>I want to go back to the folder</b></summary>

Delete the image, then follow the folder install in the [README](README.md#install). Folder
installs keep working until they stop getting updates.
</details>
