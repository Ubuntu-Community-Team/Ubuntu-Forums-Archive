---
title: "problems burning a ripped dvd"
date: 2006-06-10
forum: General Help
---

### Post by Melciah on 2006-06-10
i have a dvd filestructure ripped with dvdshrink from my windows machine on my ubuntu. ive tried to burn the structure (ie, the videots and audiots folder) to a backup dvd. it works fine in a standalone dvd player, but totem (and any other player for that matter) refuses to play it. it spits out something like, "are you trying to play this encryped dvd without dvdlibcss". but this is only when it's burned within ubuntu. ive tried it with both k3b and gnomebaker.

when burned in windows using nero with the "dvd video files" option it works fine in both windows and ubuntu. As far as i can tell, nero just sets up the two folders automatically. 

what am i doing wrong? is there some burning software that can specifically, burn a dvd structure in ubuntu?

---

### Post by Evil Dragon King on 2007-07-16
Are you absolutely sure that libdvdcss2 is installed? As I recall in Windows DVDShrink's autoburn through Nero decrypts the DVD, but with the wrong settings (or through not using DVD Decrypter or RipIt4Me beforehand, and thus working from a folder not from the disc) the backup folder option can sometimes be scrambled.

Without any more information, or a great legend-in-the-sky (Forum Veteran :P), I couldn't possibly give a conclusive answer. All of my RipIt4Me'd DVDs worked fine just by burning the VIDEO_TS folder (yes people who may be more knowledgeful about such things; I used RipIt4Me in WINE with no problems).

A little more information about the history and procedure of the rip and burn might clear the way forward, otherwise...

---

