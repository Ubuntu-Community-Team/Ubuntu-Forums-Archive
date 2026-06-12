---
title: "KGuitar crashes when loading GP4 file. Also no midi."
date: 2006-03-14
forum: General Help
---

### Post by GarethMB on 2006-03-14
Here is the terminal error:

gareth@ubuntu:~$ kguitar
kbuildsycoca running...
kguitar: cannot create MIDI Scheduler
kguitar: ERROR opening MIDI device / Music can't be played
kguitar: SongView::playSong
kguitar: SongView::playSong: Scheduler not open from the beginning!
kguitar: cannot create MIDI Scheduler
kguitar: ERROR opening MIDI device / Music can't be played
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio_file: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kguitar: cannot create MIDI Scheduler
kguitar: ERROR opening MIDI device / Music can't be played
kguitar: GTP format: FICHIER GUITAR PRO v4.06
kguitar: Title:
kguitar: Title:
kguitar: Author:
kguitar: Author:
kguitar: Author:
kguitar: Bars: 220
kguitar: Tracks: 1
kguitar: PAD: 263235 (must be 263235)
kguitar: readBarProperties(): start
kguitar: BAR #138 - flags 1
kguitar: new time1 signature: 6:4
kguitar: BAR #139 - flags 1
kguitar: new time1 signature: 4:4
kguitar: BAR #179 - flags 1
kguitar: new time1 signature: 6:4
kguitar: BAR #180 - flags 1
kguitar: new time1 signature: 4:4
kguitar: readBarProperties(): end
kguitar: readTrackProperties(): start
kguitar: Track: \uffff\uffff\uffffy 1
kguitar: readTrackProperties(): end
kguitar: TRACK 0, BAR 0 (position: 1232)
QGArray::at: Absolute index 0 out of range
KCrash: Application 'kguitar' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
gareth@ubuntu:~$ ICE default IO error handler doing an exit(), pid = 8782, errno = 0

I have installed all dependencies, recommended and suggested.

---

