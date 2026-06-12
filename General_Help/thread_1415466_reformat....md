---
title: "reformat..."
date: 2010-02-24
forum: General Help
---

### Post by flyingsliverfin on 2010-02-24
somehow i accidentally changed my windows partition, so now everything i try to use to mount it thinks it is ext4... i dont think its because i  looked at it in gparted, my 32 gb of files are still there. also, fdisk seems to think that it is NTFS/HPFS, but keeps trying to mount it as ext4 and failing...

should i attempt to reformatt it back to NTFS or will that destry all my data on there? i have most of it on my ubuntu partition, but somethings are only on my windows.

otherwise, does anyone have any idea what could have caused the problem? here is the error from mount -t ntfs-3g /dev/sda1 /media/windows:

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by Pollox on 2010-02-25
Maybe the file system is damaged?  Have you tried running chkdsk from Windows?

---

