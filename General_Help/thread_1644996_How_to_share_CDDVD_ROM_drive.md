---
title: "How to share CD/DVD ROM drive?"
date: 2010-12-14
forum: General Help
---

### Post by arnab_das on 2010-12-14
How can i share a dvd rom drive on a network? which folder will i share? as i cant see anything in the "media" or "cdrom" folder.

---

### Post by arnab_das on 2010-12-14
this is the content of the /etc/fstab file:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1e75728e-51c0-49f1-bde9-daae5ed5f125 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=516ce0b4-abc5-4c97-aa4e-75eff2919be2 none            swap    sw              0       0


let me rephrase the question, how do i mount the cd/dvdrom drive permanently?

---

