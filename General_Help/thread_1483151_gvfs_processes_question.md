---
title: "gvfs processes question"
date: 2010-05-14
forum: General Help
---

### Post by foobar66 on 2010-05-14
Hi, after booting, I have a number of gvfs processes running:

philip    3954     1  0 16:18 ?        00:00:00 /usr/lib/gvfs/gvfsd
philip    3959     1  0 16:18 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
philip    3968     1  0 16:18 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
philip    3971     1  0 16:18 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
philip    3974     1  0 16:18 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
philip    4006     1  0 16:18 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
philip    4027     1  0 16:18 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1

How are they started? Do I really need them? I've been googling a little bit, can find some general descriptions of what GVFS is, but is there a consise description of what these processes do?

---

### Post by dino99 on 2010-05-14
[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

set your prefs about apps at startup (system prefs startup apps)

---

### Post by foobar66 on 2010-05-14
> **dino99 said:**
> [http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

set your prefs about apps at startup (system prefs startup apps)

Thanks for your reply, but that wikipedia article does not explain much.
Also, I do not see anything about GVFS in the startup applications?

---

### Post by kulkarni.ankur on 2010-08-04
What purpose are these processes serving? On my computer (Lucid) they are getting launched at startup. Do I really need all of them at startup?

---

### Post by X9Tim on 2011-08-30
bump

My problem is more confusing...  I used to have all these processes running, but couldn't get Ubuntu to mount my iPhone.  So I searched and searched and could find nothing to help me.  So I have tried installing different versions of libimobiledevice, gtkpod, even rhythmbox!
No luck.

I now find that gvfs-afc-volume-monitor is no longer available at all.  What do I need to reinstall to revert this so it runs?

Also (and probably more useful) where oh where oh where is the HOW-TO for libimobiledevice and it's relatives?!?

I'm happy to write it myself, except no-one has yet posted enough for me to get the damn thing working :-x

-- 
Ubuntu 10.04.3 Lucid
Kernel 2.6.32-33
iPhone 4.2.1
libimobiledevice 1.0.6
gvfs 1.6.2
ifuse not currently installed

---

