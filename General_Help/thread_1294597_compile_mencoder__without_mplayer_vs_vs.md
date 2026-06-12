---
title: "compile mencoder  without mplayer vs vs"
date: 2009-10-18
forum: General Help
---

### Post by rfrayer on 2009-10-18
I was wondering if someone could helpme i was wondering if there is a way to compile only mencoder  and only mplayer both sepearately that way stuff dont get screwed during upgrades offcourse id be using checkinstall to makethe packages

---

### Post by andrew.46 on 2009-10-18
Hi rfrayer,

> **rfrayer said:**
> I was wondering if someone could helpme i was wondering if there is a way to compile only mencoder  and only mplayer both sepearately that way stuff dont get screwed during upgrades offcourse id be using checkinstall to makethe packages

Ubuntu creates many individual packages from the MPlayer source code and I suspect the best way to accomplish your goal is to learn a bit about *formal* packaging and duplicate these efforts with your own packages. Having said that have a look at [this guide here ]("http://ubuntuforums.org/showthread.php?t=1280543")that builds an mplayer-nogui package without MEncoder and utilitising checkinstall. This might provide a start for your own efforts?

All the best,

Andrew

---

### Post by laceration on 2009-10-18
However, I believe MPlayer is a dependency of Mencoder, so it would not be possible to compile it on its own.

---

### Post by andrew.46 on 2009-10-18
Hi laceration,

> **laceration said:**
> However, I believe MPlayer is a dependency of Mencoder, so it would not be possible to compile it on its own.

I believe this is possible by using *./configure --disable-mplayer*, but I have been wrong before :).

Andrew

---

