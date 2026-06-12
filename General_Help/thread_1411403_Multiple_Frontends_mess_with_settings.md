---
title: "Multiple Frontends mess with settings?"
date: 2010-02-19
forum: General Help
---

### Post by Ramrunner on 2010-02-19
Hi guys, for the first time I've gotten my hands on a ASRock ION 330HT and set it up as a front end to my existing front/backend which sits in the living room. I have EVERYTHING working but I've found an annoyance which is probably as a result of one of my screw-ups.

Basically - the backend (/frontend) stores it's videos in the default /var/lib/mythtv/ blah blah blah. This has always worked. I copy my video files there, rescan and bob's your uncle.

With the ASRock, I'd like to store some files locally, so currently the videos folder is set to /var/jan/Videos. I'll work on smb mounting later.

When I scan that, the videos also show and bob's my second uncle.

HOWEVER. After the scan from the ASRock, my MAIN box also is looking for files in /home/jan/Videos (which doesn't exist there) and finds nothing. If I rescan - all is good again. Then going back the the ASRock, IT is then looking for the files in /var/lib/mythtv etc. and finds nothing.

Why should setting in EITHER frontend mess with the setting in the other? That kind of defeats the purpose of having multiple front ends with multiple hardware/software configurations right?

Or am I doing something wrong?

Regards,
Ed.

---

### Post by Ramrunner on 2010-02-19
The kids were complaining this morning about not being able to watch some Hi-5 I'd converted. The files that weren't working were MKV files. The reason I found is because in the ION 330HT, I'd set the default for MKV files to be mplayer with switches for VDPAU. Reason I'd done this is because the internal player does not like my 1080p MKVs and stutters like mad. Using mplayer fixes that. HOWEVER, it's now changed the MKV file type on my main box to vpdau as well (which my main box does not support), causing mplayer to crash.

This is sorely annoying!

Why does changing setting on one front end affect the other? It shouldn't!

---

