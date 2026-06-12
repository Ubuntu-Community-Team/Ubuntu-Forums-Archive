---
title: "can't mount partition"
date: 2006-02-13
forum: General Help
---

### Post by Alex99 on 2006-02-13
I reinstalled a system and mounted a new partition (hda7) as /home. An old partition that's still on my hard drive (hda5) doesn't show up however. With Knoppix I found out that it's still there with all the data, but I don't want to burn all this on CD. If I try to mount hda5, I'm told the mount point doesn't exist. I tried to establish the mount point in /etc/fstab though:

# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda5	/media/hda5		ext2	defaults	0	0
/dev/hda7       /home           ext2    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Ideas, anyone?

---

### Post by lha on 2006-02-13
How about
```
sudo mkdir /media/hda5
```?

---

### Post by wrtrdood on 2006-02-13
Yes, you must first create a "dummy" directory on your current available partition then the fstab entry should work as expected.

BTW - you didn't need to boot Knoppix to see the info on the drive.  Enter the following to see all existing partitions.

sudo fdisk -l /dev/hda

---

### Post by Alex99 on 2006-02-14
Thanks, now it works!

---

