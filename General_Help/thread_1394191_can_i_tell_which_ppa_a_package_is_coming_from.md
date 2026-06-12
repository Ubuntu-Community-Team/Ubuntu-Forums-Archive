---
title: "can i tell which ppa a package is coming from?"
date: 2010-01-30
forum: General Help
---

### Post by inphektion on 2010-01-30
from my thread here: [http://ubuntuforums.org/showthread.php?t=1393931](http://ubuntuforums.org/showthread.php?t=1393931)

It looks like i'm getting libglib from one of the PPA's I've added.  How can i tell which PPA its coming from and get it from official instead?

---

### Post by inphektion on 2010-01-30
turns out it was the ubuntuone beta ppa.
[https://launchpad.net/~ubuntuone/+archive/beta?field.series_filter=jaunty](https://launchpad.net/~ubuntuone/+archive/beta?field.series_filter=jaunty)

I ran this:
ppa-purge -p beta ubuntuone


then an aptitude update and upgrade and got the normal glib back and my nautilus now works again.

---

### Post by stoneage on 2010-01-30
That happened to me too. It took me a while to figure out why I was being asked to install Jaunty packages as part of an update for Karmic. 

;)

---

