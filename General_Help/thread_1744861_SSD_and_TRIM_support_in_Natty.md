---
title: "SSD and TRIM support in Natty?"
date: 2011-04-30
forum: General Help
---

### Post by donalgodon on 2011-04-30
Does the Natty kernel offer out of the box support for TRIM on a TRIM capable SSD drive?

I have not found an answer, so I thought maybe someone could shed some light on this.

If not out of the box, can TRIM be enabled?

---

### Post by ChrisWells on 2011-04-30
It didn't by default for me, you have to add discard to fstab for the ext4 drive. Might as well add noatime to it as well:  gksudo gedit /etc/fstab  make ext4 drive look like this:  discard,noatime,errors=remount-ro

---

### Post by donalgodon on 2011-04-30
Got it. Thanks.

I can't believe that this is not enabled by default when the installer finds the SSD.

Come on Canonical. How many new users are going to be able to do that? Granted, many of them might not use SSD, but there's no doubt that SSDs are here to stay and they are growing in market share even among average users.

---

### Post by oldfred on 2011-04-30
The last link to the archlinux has some good info on SSDs & trim.


It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

