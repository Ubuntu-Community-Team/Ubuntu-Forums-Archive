---
title: "Unable to unmount LACIE external harddrive without an error."
date: 2006-05-18
forum: General Help
---

### Post by YourSurrogateGod on 2006-05-18
Ok, so I recently got [this](http://www.lacie.com/products/product.htm?pid=10468) hard-drive and decided to promptly fill it up with stuff that I'd like to see backed up forever. Now, whenever I right-click on it on the desktop and try to unmount it, I get [this](http://www.engr.uconn.edu/~ats01001/ErrorDesktop01.png) error. Anyone have this problem before? If so, how did you solve it?

---

### Post by kokiri on 2006-05-18
have you tried to umount it?

---

### Post by YourSurrogateGod on 2006-05-18
From the command line? No.

---

### Post by kokiri on 2006-05-18
that should "let go" of the drive so you can eject it...unlike windows I don't think that it really matters when you unplug the unit, just as long as the kernel isn't using it. to make it possible for the general users to unmount (umount) it, add users after defaults in fstab for the entry

eject is primarily used for cd/dvd drives by sending the "eject" atapi command to the drive

---

### Post by YourSurrogateGod on 2006-05-18
Dammit, I forget, how do I get at fstab?

---

### Post by kokiri on 2006-05-18
it's right here:
sudo nano /etc/fstab

---

### Post by YourSurrogateGod on 2006-05-18
This is how my fstab looks like right now.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

```
I don't see my external hard-drive anywhere, even if it's mounted right now.

---

### Post by aysiu on 2006-05-18
It's a known bug in Breezy, and it's been fixed for Dapper.

It doesn't happen in Kubuntu, incidentally--only in Gnome.

Read more [here](http://www.ubuntuforums.org/showthread.php?t=84262).

---

### Post by YourSurrogateGod on 2006-05-19
[QUOTE=aysiu]It's a known bug in Breezy, and it's been fixed for Dapper.

It doesn't happen in Kubuntu, incidentally--only in Gnome.

Read more [here](http://www.ubuntuforums.org/showthread.php?t=84262).[/QUOTE]
Thanks. I'll get dapper after it comes out in stable release.

---

