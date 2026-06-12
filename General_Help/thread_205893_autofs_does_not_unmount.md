---
title: "autofs does not unmount"
date: 2006-06-29
forum: General Help
---

### Post by MatBi on 2006-06-29
Hi, i installed and properly configured autofs to mount a USB drive, with a unmount timeout of 4 seconds.
On access the disk is properly mounted, but is never unmounted.
I checked with lsof if any process had open file handles under the mount path and got nothing.

Launching automount with verbose option, every 4 seconds i get:
automount[10577]: rm_unwanted: /media/auto/quirino
automount[10577]: expired /media/auto/quirino
automount[10447]: attempting to mount entry /media/auto/quirino

After killing processes one by one, i discovered that hald is the culprit. Is it safe to remove it, or there's some critical process hanging from it?

---

