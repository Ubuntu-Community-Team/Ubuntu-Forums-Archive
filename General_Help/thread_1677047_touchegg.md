---
title: "touchegg"
date: 2011-01-28
forum: General Help
---

### Post by abrahamthegrey on 2011-01-28
Hey guys, I read [this article]("http://www.omgubuntu.co.uk/2011/01/touchgg-allows-you-to-assign-actions-to-multitouch-gestures-in-linux/") on omgubuntu, and I think this program seems great, especially since my multitouch has been touch and go on my eeepc 1005ha.  anyone figure out how to install and configure it?

---

### Post by Zookalicious on 2011-02-08
There's a .deb for 32 bit. If you're on 64bit you'll have to compile it from source. There's also a video on how to configure it in that same article (or there was last time I checked.)

If you're stuck on installing from source so am I. Can't figure out how to get qmake to work..

---

### Post by jnfurst on 2011-02-15
> **Zookalicious said:**
> There's a .deb for 32 bit. If you're on 64bit you'll have to compile it from source. There's also a video on how to configure it in that same article (or there was last time I checked.)

If you're stuck on installing from source so am I. Can't figure out how to get qmake to work..

Make sure you have qt4 installed. Then run qmake-qt4 that will make sure you aren't running the old qt3 qmake program. After that you should be able to make with just 'make'

---

