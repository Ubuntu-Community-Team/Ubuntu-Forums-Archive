---
title: "Mounting from the command line"
date: 2010-09-14
forum: General Help
---

### Post by d5xtgr on 2010-09-14
So I was thinking about making a batch file that automatically mounts my Windows 7 partition when I start up.  While I can use the disk mounter to put the drive on my desktop, and then unmount it:```
sudo umount /media/C:
```trying to mount it using the same form I get an error:```
sudo mount /media/C:
mount: can't find /media/C: in /etc/fstab or /etc/mtab

```
How do I mount my partition from the command line?

---

### Post by Capt_Scribble on 2010-09-14
I think you can't mount it the same way because it does not yet exist by that name until it is mounted. Just do a google search for ways to auto mount it. Here is one of many involving a GUI program:
[http://www.hackourlives.com/auto-mount-windows-partitions-in-ubuntu-10-04-lucid/](http://www.hackourlives.com/auto-mount-windows-partitions-in-ubuntu-10-04-lucid/)

---

### Post by d5xtgr on 2010-09-15
Very good. thank you.

---

