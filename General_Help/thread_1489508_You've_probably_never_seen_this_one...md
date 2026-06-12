---
title: "You've probably never seen this one.."
date: 2010-05-21
forum: General Help
---

### Post by R3VAMP3D on 2010-05-21
I've been using Ubuntu for awhile now on my laptop, using the same original installation from CD. I've noticed that kernel images are piling up in /boot, and will eventually run out of space, is there a tool to safely delete the right images?

---

### Post by dragonboss on 2010-05-21
You could use [ubuntu tweak]("http://ubuntu-tweak.com/") to get rid of older kernels but it is best to keep one of the older kernels in case one goes bonkers.

---

### Post by WorMzy on 2010-05-21
Open synaptic and do a search for the kernels version (e.g. 2.6.32-21) then remove the linux-headers and image for that version. Keep the most recent previous version as a backup in case you ever need it.

---

