---
title: "Error in mounting /Windows"
date: 2010-06-06
forum: General Help
---

### Post by devanson on 2010-06-06
Hi.. All.. Here my story.. I need hepl, pls...

First I installed windows Xp on C - drive. and then ubuntu on my last partition (5 partition)... Today I formatted c-drive only and installed Windows 7 (on C - drive)... And recovered my grub2 menu successfully. 

My problem is during installation of Ubuntu, I mounted (C-drive - windows xp (before)) and all my rest partion, during installation of ubuntu itself, for conveniences...

But, now the problems, after installing windows 7 and recovered my grub2 menu, its showing error while booting into my Ubuntu desktop...

The error is 

"Disk drive for /Windows is not ready yet or not present"
"Continue to wait, or press S to skip mounting or M for manual recovery"

Need your help please.....

---

### Post by Forged on 2010-06-06
can you post your /etc/fstab

---

### Post by octavius on 2010-07-02
Hi!

I have the exact same problem, although I have Windows 7. I wiped out my HD, installed Windows 7 Ultimate, then Partitioned for Ubuntu 10.04.

The firsts couple of times I successfully booted Ubuntu and Windows. Then, for no apparent reason, that message started to appear. Just pressing S continues the boot process but is so annoying...

Here's my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=d8539306-8756-4105-bc7a-ab91f2c19b2c /home           ext4    defaults        0       2
# /tmp was on /dev/sda7 during installation
UUID=cf4fb472-1032-4f73-9083-169cdf18c748 /tmp            ext4    defaults        0       2
# /usr was on /dev/sda6 during installation
UUID=6acd9656-416c-4dc5-b73c-28d020759fc1 /usr            ext4    defaults        0       2
# /var was on /dev/sda8 during installation
UUID=8ec1daba-2043-4975-a15c-eb7d3ace3990 /var            ext4    defaults        0       2
# /windows was on /dev/sda10 during installation
UUID=3CF9-1DB4  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
UUID=126942a9-a8bf-4264-9441-436d3fa093f1 none            swap    sw              0       0

```

Hope you can help us both...

Regards,
Octavius

---

