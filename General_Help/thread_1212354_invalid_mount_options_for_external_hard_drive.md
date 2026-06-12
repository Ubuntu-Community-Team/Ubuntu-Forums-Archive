---
title: "invalid mount options for external hard drive"
date: 2009-07-13
forum: General Help
---

### Post by homerunner on 2009-07-13
Hello,

I have a new external hard drive. Jaunty auto-mounted it just fine when I got it, then I decided to partition it. Now I have two ext3 partitions and one fat32 partition on the disk and it does not auto-mount any more. Instead, I get three error messages (one for each partition) saying something like: could not mount volume, invalid mount options. Unfortunately no info what option it is trying to use or where the system is told to use that option.

I can mount the hard drive without problems on the hardy system on another laptop and also on my laptop under win xp. Furthermore, I have no problems with auto-mounting my usb stick or any other device on my laptop, except that hard drive.

Furthermore, mounting the hard drive manually is also no problem, however, for some reason it is mounted read-only and I can only write as an admin on it.

I have googled the problem, but I couldn't find anything to help me out. For many people, that error message seemed to come from a problem with the fstab, but that doesn't seem to be the case here.

My fstab:
```
# /etc/fstab: static file system information.
  2 #
  3 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  4 proc            /proc           proc    defaults        0       0
  5 /dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
  6 /dev/sda2       none            swap    sw              0       0
  7 /dev/sda1       /mnt/windows    ntfs    ro,uid=us,auto  0       0
  8 /dev/sda5       /mnt/sda5       vfat    rw,uid=us,auto  0       0
  9 #/dev/sdb1      /media/disk-1   ext3    rw,users,uid=us,auto    0       0

```

Also removing all mount options with gconf from /system/storage/default_options/vfat didn't help. Any other ideas?

---

