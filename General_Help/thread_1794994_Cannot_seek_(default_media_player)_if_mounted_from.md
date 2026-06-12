---
title: "Cannot seek (default media player) if mounted from ISO"
date: 2011-07-01
forum: General Help
---

### Post by twipley on 2011-07-01
Using Ubuntu 11.04, Totem (the default media player) is not able to seek (read: to forward or go back in time) whenever the file is read from a mounted ISO archive.

Whenever I extract individual media files from such an archive, the seek bar at the bottom works as it should. Thus, it can be ascertained that it is not the media files that are the source of the problem, here.

Any ideas on the reason why that is doing so? Sounds like a bug, or what?

---

### Post by mc4man on 2011-07-01
What happens if you just open the .iso, not mounted (there is no reason to mount an iso, it's just a file
The only .iso's I have here are of the DVD_VIDEO type, Movie Player (totem) can seek in them  fine.

---

### Post by twipley on 2011-07-01
By default, double-clicking on one of those ISOs open them using the "archive mounter," which makes them playable without extraction.

Opening them, on the other hand, through the "archive manager" forces the files to be extracted upon them being opened -- which, to my mind, may be quite unnecessary a step, as none of those files are compressed to start with.

---

### Post by haqking on 2011-07-01
> **twipley said:**
> By default, double-clicking on one of those ISOs open them using the "archive mounter," which makes them playable without extraction.

Opening them, on the other hand, through the "archive manager" forces the files to be extracted upon them being opened -- which, to my mind, may be quite unnecessary a step, as none of those files are compressed to start with.

why dont you just use your player of choice to point to the iso as its media ?

no need to use archive manager or mounter to play its contents ?

---

### Post by twipley on 2011-07-02
I am quite new to Linux. Those files do not contain unmodified MPEG-2 streams, but miscellaneous .wmv, .avi, and .flv files.

I think because of that those ISO files have to either be mounted or extracted.

---

### Post by mc4man on 2011-07-02
> **twipley said:**
> I am quite new to Linux. Those files do not contain unmodified MPEG-2 streams, but miscellaneous .wmv, .avi, and .flv files.

I think because of that those ISO files have to either be mounted or extracted.

You can try r. clicking > **open** with archive manager on these type of .iso's
Then just r. click on a single or group of files listed (shift click for group) > open with and pick 'movie player' (or just a d. left click on a single file if totem is default for mimetype
The file(s) will be loaded into totem and should be seek-able

(when doing a group and or large files it will say "extracting" but it's not really

Tested as so, (playable, seekable without 'extracting') on an iso of .wav's, .flac's, .mov's, .mp4's and .mkv

(fileroller has a longstanding bug about adding ;1 to displayed filenames, shouldn't matter - see screen

---

### Post by twipley on 2011-07-02
Thanks for the effort, but it says "extracting," and takes about 20 seconds to do so for 500 MB files, so I think *it really is extracting*.

Mounting the ISO permits one to watch any such media file on-the-fly, without needing the file to be extracted and copied over to some temporary-files repository (or wherever it is copied).

A bug report should be opened concerning that if non-seeking is a bug.

---

