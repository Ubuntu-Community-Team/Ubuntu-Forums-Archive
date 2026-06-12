---
title: "Help, PC with grub error"
date: 2010-09-10
forum: General Help
---

### Post by Chlorhydrikk on 2010-09-10
Hi, I just installed Ubuntu on a computer but it can't boot, it ends with a greb-rescue error.
What shall I do? Here's my fstab and my sudo blkid. I did an ubuntu side installation with xp.
Thank you !

Le FSTAB

# /etc/fstab: static file system information.
#
#  Use 'blkid -o value -s UUID' to print the universally unique identifier
#  for a device; this may be used with UUID= as a more robust way to name
#  devices that works even if disks are added and removed. See fstab(5).
#
#  <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc             /proc           proc    nodev,noexec,nosuid 0       0
# / was on  /dev/sda5 during installation
UUID=3a307ad3-99a9-4301-8ad0-f601ef9d157c  /               ext4    errors=remount-ro 0       1
# swap was on  /dev/sda6 during installation
UUID=5b3ff501-f07c-4c2e-ac2d-a238b599cbe2  none            swap    sw              0       0
/dev/fd0         /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

SUDO  BLKID:
/dev/sda1: LABEL="System" UUID="26AC3F75AC3F3E9D" TYPE="ntfs" 
/dev/sda6:  UUID="5b3ff501-f07c-4c2e-ac2d-a238b599cbe2" TYPE="swap" 
/dev/loop0:  TYPE="squashfs" 
/dev/sda5:  UUID="3a307ad3-99a9-4301-8ad0-f601ef9d157c" TYPE="ext4"

---

### Post by Rubi1200 on 2010-09-10
From a LiveCD, post the results of the bootscript linked to at the bottom of my post.

---

