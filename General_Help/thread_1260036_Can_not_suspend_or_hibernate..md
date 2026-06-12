---
title: "Can not suspend or hibernate."
date: 2009-09-07
forum: General Help
---

### Post by ToshibaLaptoplinux on 2009-09-07
If I try to suspend or hibernate from either the menu item, or by running the script directly, it fails and issues a warning saying that VLC is preventing it because it is running some media. Needless to say VLC is not running and no other media players are running. I even have checked the running processes.

Shutdown works without any problem.

This is recent behavior which leads me to believe something came down in one of the safe-upgrades that broke it? Any ideas/suggestions and should I report it as a bug?

Ubuntu 9.04 Jaunty
Kernel Linux 2.6.28-11-generic
GNOME 2.26.1

on a Toshiba Dynabook; TX/760LS

---

### Post by P4man on 2009-09-07
try this (assuming you have at least vlc installed): start vlc > tools > preferences > show setttings "all" > uncheck "inhibit power mngt deamon during playback "

Im not sure how it works, but perhaps it puts a lock somewhere and its not removing it for whatever reason?

---

### Post by ToshibaLaptoplinux on 2009-09-15
> **P4man said:**
> try this (assuming you have at least vlc installed): start vlc > tools > preferences > show setttings "all" > uncheck "inhibit power mngt deamon during playback "

Im not sure how it works, but perhaps it puts a lock somewhere and its not removing it for whatever reason?

That did the trick for me but opened up a whole other can of worms I will address in another thread.

Thanks.

---

