---
title: "DVD drive not mounting"
date: 2011-04-14
forum: General Help
---

### Post by madshad on 2011-04-14
hi, I have a built in dvd drive that will not mount in ubuntu10.10. works fine in windows. i searched but can not find a solution

heres my fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=de017f42-b784-4ca5-9417-d95a71edc95a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=80338811-fcd3-4bd3-9e55-e028171a6281 none            swap    sw              0       0

trying to  access dvd data disks
info from sysinfo
SCSI device scsi1
vendor HP
model DVD Writer 400c

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

