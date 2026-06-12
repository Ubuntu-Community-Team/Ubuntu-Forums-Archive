---
title: "Mount of root filesystem failed, maitenance shell"
date: 2010-02-28
forum: General Help
---

### Post by Primefalcon on 2010-02-28
On boot its goes through it's steps, does a filesyetem scan and constantly drops back to a maintenance shell

funny thing is df -h shows the filesystem mounted and using cd I can navigate the files so.... what's going on?

What can I do short of a reinstall

---

### Post by Primefalcon on 2010-02-28
Since everything seems to be mounted ok I tried a startx and got the following

[IMG]http://i50.tinypic.com/v5c1at.jpg[/IMG]

---

### Post by cjhabs on 2010-02-28
I suspect it is mounted in read-only mode as it feels the file system is in an inconsistent state.

---

### Post by Primefalcon on 2010-02-28
So you think only option is a format :-( sigh

---

### Post by cjhabs on 2010-02-28
I would boot off live cd and run fsck manually on the root partition and see if you can clean it up then try booting again.

---

### Post by geirha on 2010-02-28
Boot the Ubuntu cd and do a filesystem check on your root partition. You can do it from System -> Administration -> Gparted ... right click the partition and choose «check». If you're not certain which is the root partition, just check all ext[2-4] partitions.

---

### Post by Primefalcon on 2010-02-28
Just posting to say that worked, just downlaoded the remix, used the startup disk creator to install Ubuntu to a usb stick....

ran the filesystem check from within gparted and its worked great. Thank you my great fellow community members :-).

---

