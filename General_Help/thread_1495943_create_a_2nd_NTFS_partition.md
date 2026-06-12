---
title: "create a 2nd NTFS partition ?"
date: 2010-05-28
forum: General Help
---

### Post by ieee488 on 2010-05-28
I have Ubuntu 10.04 dual booting with Windows XP.

I want to create another NTFS partition out of the partition that currently has Windows XP. In other words, I want to have C:\ for Windows XP operating system files but have the new D:\ for data.

How do I do this so that I don't break Grub?

---

### Post by drdos2006 on 2010-05-28
Boot up with your Live CD, run GParted. GParted will show how much of the Windows partition has been used, resize to a smaller size, make a new partition, format to NTFS.

regards

---

### Post by ieee488 on 2010-05-28
And this new partition becomes /dev/sda3 even though physically on the hard drive it will be between /dev/sda1 which has Windows XP and /dev/sda2 which has Ubuntu 10.04 ?

---

