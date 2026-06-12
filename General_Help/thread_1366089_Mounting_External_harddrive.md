---
title: "Mounting External harddrive"
date: 2009-12-28
forum: General Help
---

### Post by Keikowned on 2009-12-28
I know it has been mentioned before and I did search but the instructions I tried didn't work.

Type of HD = ntfs

---

### Post by spigy11 on 2009-12-28
Hi

first check for packeges ntfs-3g, bit should be installed by default

if that is present

find your external (USB) disk 

ls /dev/disk/by-label -l

Create mounting folder
mkdir /exter_hdd

mount -t ntfs-3g /dev/disk/{NAME_OF_YOUR_HDD} /exter_hdd

If you want to add your exter_hdd perm into fstab create a new entry
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0

For closer information

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

HaveFunn

---

### Post by Keikowned on 2009-12-28
> **spigy11 said:**
> Hi

first check for packeges ntfs-3g, bit should be installed by default

if that is present

find your external (USB) disk 

ls /dev/disk/by-label -l

Create mounting folder
mkdir /exter_hdd

mount -t ntfs-3g /dev/disk/{NAME_OF_YOUR_HDD} /exter_hdd

If you want to add your exter_hdd perm into fstab create a new entry
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0

For closer information

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

HaveFunn

tried your instructions and at this part ```
mount -t ntfs-3g /dev/disk/External /exter_hdd
```

it said mount: invalid option -- 3

---

### Post by spigy11 on 2009-12-28
Try

ok I need to know under which user are U running the mount command root or normal user

if root

try the command just 

mount -t ntfs /dev/disk/External /exter_hdd

check if the FS was mounted if not, try the following

apt-get install ntfs-3g --> install ntfs-3g drivers for mounting ntfs under linux

btw which distro version are U using?

---

