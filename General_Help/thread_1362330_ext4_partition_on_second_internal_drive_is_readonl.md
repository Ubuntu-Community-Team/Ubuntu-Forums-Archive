---
title: "ext4 partition on second internal drive is readonly"
date: 2009-12-23
forum: General Help
---

### Post by vdr60 on 2009-12-23
On my ubuntu 9.10 I want to use the second internal hard drive to store my files and my VMWare machines.
Using gparted i created a new ext4 partition, but when I mount it results read only!
From ls -l i have:

drwxr-xr-x 3 root root 4096 2009-12-23 06:36 VMStore

I tried to define /media/VMStore with rw permission and owned by my user, but when I mount my /dev/sdb1 on it it become ro and owned by root! It seems that the partition acquired its own privileges when it was created with gparted with root privilege.

Anyone has some idea to get this partition rw?

---

### Post by dcstar on 2009-12-23
> **vdr60 said:**
> On my ubuntu 9.10 I want to use the second internal hard drive to store my files and my VMWare machines.
Using gparted i created a new ext4 partition, but when I mount it results read only!
From ls -l i have:

drwxr-xr-x 3 root root 4096 2009-12-23 06:36 VMStore

I tried to define /media/VMStore with rw permission and owned by my user, but when I mount my /dev/sdb1 on it it become ro and owned by root! It seems that the partition acquired its own privileges when it was created with gparted with root privilege.

Anyone has some idea to get this partition rw?

[LIST=1]
[*]Never (ever) manually mount drives under /media, that folder is for **the system** to mount removable drives. Create a mount point somewhere else - outside of any system folders.
[*]Use the **pysdm** package to mount additional drives.
[/LIST]

---

### Post by vdr60 on 2009-12-23
OK, but the creation of folder under media directory was only a tentative.

Really I defined the ext4 partition with gparted (as primary partition) then with the Storage Manager (psdym) I added the definition to mount it, 
psdym added this line in my fstab:
/dev/sdb1     /media/VMStore   ext4         user           0  0

then I rebooted but is always readonly!

I found this topic [http://ubuntuforums.org/showthread.php?t=1313198](http://ubuntuforums.org/showthread.php?t=1313198)
but it sounds strange: how it is possible to define a partition without being root?

Any suggestions? (but it is so strange to have a second hard drive with an ext4 partition?)

---

