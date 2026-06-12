---
title: "Computer will not load /sbin/init error"
date: 2010-11-27
forum: General Help
---

### Post by algebraicgeom on 2010-11-27
Hi:

After normal use the computer was turned on and would not load (10.04) and the error message on the screen was :

> /sbin/init: error while loading shared libraries: libnih.so.1: cannot open shared object file: Input/output error

[   26.369130] Kernel panic - not syncing: Attempted to kill init!

Anyways, I put the hard drive in an external unit, and I ran fsck. Many errors came up and they were all fixed. I was able to mount the drive on my other computer and back up files in the home directory. 

If I try to select recovery mode and the same error appears. 

What can I do in this case? Can I somehow get into a recovery-like mode off of the livecd to maybe fix the packages that might be "messed up"?

---

### Post by dcstar on 2010-11-28
> **algebraicgeom said:**
> Hi:

After normal use the computer was turned on and would not load (10.04) and the error message on the screen was :



Anyways, I put the hard drive in an external unit, and I ran fsck. Many errors came up and they were all fixed. I was able to mount the drive on my other computer and back up files in the home directory. 

If I try to select recovery mode and the same error appears. 

What can I do in this case? Can I somehow get into a recovery-like mode off of the livecd to maybe fix the packages that might be "messed up"?

If you can recover the whole /home folder then it may be simpler to just do a fresh install and use the old /home data. You can waste far more time trying to get a broken system working instead of just doing a new install.

---

