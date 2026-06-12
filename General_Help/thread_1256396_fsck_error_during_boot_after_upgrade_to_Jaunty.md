---
title: "fsck error during boot after upgrade to Jaunty"
date: 2009-09-02
forum: General Help
---

### Post by jfl on 2009-09-02
I just got an error during the boot sequence after upgrading to Jaunty.

The boot stops during "fsck" with an error (4 I believe) , tells me to run "fsck" manually and to enter <ctrl-D> to continue; the boot then proceeds normally.
Tried to run fsck from the console and got a scary warning about running fsck on a mounted partition, so I aborted.

Here is the /var/log/fsck/checkfs

> Log of fsck -C3 -R -A -a 
Wed Sep  2 10:57:25 2009

fsck 1.41.4 (27-Jan-2009)
dosfsck 3.0.1, 23 Nov 2008, FAT32, LFN
/dev/sdb7: 57633 files, 980568/2032361 clusters
/dev/sda5: clean, 16418/2469152 files, 1109579/4935963 blocks
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: Inode 2614409 has EXTENTS_FL flag set on filesystem without extents support.


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Wed Sep  2 10:58:08 2009
----------------

Since I upgraded on-line, I don't have a live CD ...

What do you suggest; file system error make me nervous :confused:

Thanks !!!

---

### Post by sisco311 on 2009-09-02
Reboot the computer and from the BusyBox run:
```
umount /dev/sda1
e2fsck -C**0** -f -p -v /dev/sda1
```

EDIT:
it's a zero in the command NOT a capital 'o'.

---

### Post by jfl on 2009-09-02
Thanks !!!

Actually I booted in "recovery" mode, ran fsck /dev/sda1, it found the error, asked me if I wanted to clear the EXTENTS_FL flag I hit <y> and everything looks good now !!!

---

