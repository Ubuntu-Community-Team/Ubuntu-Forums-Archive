---
title: "Ubuntu 9.10 Beta not detecting Win 7 drive in GRUB"
date: 2009-10-08
forum: General Help
---

### Post by mab1376 on 2009-10-08
I don't know how to change the new grub v2 entries for this drive

Below is my fdisk entry for the drive not being detected.

```
  
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38914   312567808    7  HPFS/NTFS

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03a903a9

```

---

### Post by marcopolo1981 on 2009-11-01
See tommcd's post in [http://ubuntuforums.org/showthread.php?t=1290851&highlight=grub+-detecting+xp](http://ubuntuforums.org/showthread.php?t=1290851&highlight=grub+-detecting+xp)

He says:
Grub2 no longer uses /boot/grub/menu.lst. Grub2 uses /boot/grub/grub.cfg, which you are not supposed to edit.
Anyway, it looks like you did not completely update to grub2, you may be chainloading grub2 from grub legacy. Follow this tutorial in the wiki about upgrading from grub legacy to grub2:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
Here is another good tutorial on grub2:
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
I'm still trying to get up to speed with grub2 myself.

---

