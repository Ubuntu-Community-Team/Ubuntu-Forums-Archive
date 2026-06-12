---
title: "Corrupted Drive After Restart"
date: 2011-06-18
forum: General Help
---

### Post by sufjanfan on 2011-06-18
Hello all,
I've been running Ubuntu 10.04 for a while now on my 500 gb external hard drive, and for the most part I've had little to no problems I couldn't fix with a little common sense. However, recently my computer was taking an unusually long time to boot up, so I restarted, which normally works just fine, but just as I restarted the system had begun to boot. Now when I boot I get the following:

```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)
```I did a bit of searching around, but nobody seems to have the exact same problem as me. I plugged the external hard drive into another Ubuntu computer (also 10.04), but when I attempt to mount it it appears to do nothing, although I can see it in Disk Utility and in the 'Places' menu. I tried sudo fsck -ln /dev/sdc and got:

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Device or resource busy while trying to open /dev/sdc
Filesystem mounted or opened exclusively by another program?
```I haven't tried an Ubuntu LiveCD, because I lost mine (making a new one is difficult with our current internet connection) and I feel I would get the same results. At the very least, I would like to be able to get all my music, videos, etc. off the drive, but I would prefer being able to fix it completely so as not to have to buy a new one.

Any ideas? Thanks in advance.

---

### Post by DirtyPC on 2011-06-18
Install ubuntu into your internal drive, and copy your data to it, then reinstall ubuntu on your external drive. (After Flashing) You may have broken sectors.

---

### Post by sufjanfan on 2011-06-18
The computer with which I used the external drive has no internal drive; I was booting from the external. I have another computer with an internal Ubuntu drive, but I can't properly mount it or see anything.

---

### Post by sufjanfan on 2011-06-21
It appears to be working now, at least to the extent where I can mount it and back up my files from the other computer.

To others with similar problems, I'm not entirely sure what I changed. I ran e2fsck for a few days, but it was taking too long so I canceled. When I ran it again, it took a few seconds and my drive was fixed. Idk exactly what happened.

---

