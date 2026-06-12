---
title: "VLC Slow Start"
date: 2010-10-02
forum: General Help
---

### Post by mooreted on 2010-10-02
I have an Intel Celeron 2.80 Ghz processor, 1GB RAM, GeForce 8400 512MB video card running Ubuntu 10.04.

When I open VLC it takes 15 to 20 seconds to open. 

I just setup another computer: Pentium III 1.1Ghz with 256MB of RAM with Crunchbang Lite, and VLC opens in less than a second. 

No problem with VLC on my computer at home.

I have tried uninstalling and reinstalling VLC but no change.

No errors from the command line.

What could cause VLC to open slowly on only one computer?

---

### Post by stRunF on 2010-10-02
does it open slowly, or has delay when going in Fullscreen mode and back?
if you have delay while going in fullscreen, it's from the graphic driver, had this problem too, had to reinstall it some other way

---

### Post by mooreted on 2010-10-02
> **stRunF said:**
> does it open slowly, or has delay when going in Fullscreen mode and back?
if you have delay while going in fullscreen, it's from the graphic driver, had this problem too, had to reinstall it some other way

Well, I open a terminal (in case there's an error) and type "vlc" and press enter. It takes 15 or more seconds to actually launch.

Found a work-around:

Open Tools/Preferences/Show All/Advanced/Playlist

Uncheck "Use Media Library"

Now VLC opens normally.

I'll have to do some research on this before I can call this thread "Solved".

---

### Post by mooreted on 2010-10-02
> **samiparker said:**
> Try to use another version of the VLC, try and old one, i hope that will work, the new VLC include too many of the modules and codex... try an old one, I hope that will work properly and will be fast enough to do your work.

Well, it seems to be fine if I leave that option off. I don't even know what the "media library" function is, so obviously I don't need it.

Thanks for the help.

---

