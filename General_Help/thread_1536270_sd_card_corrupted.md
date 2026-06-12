---
title: "sd card corrupted?"
date: 2010-07-22
forum: General Help
---

### Post by lmm5247 on 2010-07-22
i normally don't need to ask for help around here, but i've searched very extensively and can't find an answer anywhere.

i have an SD card with pictures on it that i would really like to have. problem is, i can't get it to mount.  when i try in windows, it says it needs to be formatted before use.  i thought i might be able to get it to mount in linux, but to no avail.

using ```
ls /dev/sd*
``` gives me:
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4  /dev/sda5  /dev/sda6  /dev/sdb



using ```
sudo fdisk -l
``` gives me:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ee5d663

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4463    35737600    7  HPFS/NTFS
/dev/sda3            4463        7650    25598977    5  Extended
/dev/sda4            7650       19458    94848000    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5            4463        4827     2928640   82  Linux swap / Solaris
/dev/sda6            4827        7650    22669312   83  Linux


at this point, i'm thinking the card itself might be bad. any suggestions?

thanks =)

---

### Post by jbrown96 on 2010-07-22
> **lmm5247 said:**
> i normally don't need to ask for help around here, but i've searched very extensively and can't find an answer anywhere.

i have an SD card with pictures on it that i would really like to have. problem is, i can't get it to mount.  when i try in windows, it says it needs to be formatted before use.  i thought i might be able to get it to mount in linux, but to no avail.

using ```
ls /dev/sd*
``` gives me:
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sda4  /dev/sda5  /dev/sda6  /dev/sdb



using ```
sudo fdisk -l
``` gives me:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ee5d663

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        4463    35737600    7  HPFS/NTFS
/dev/sda3            4463        7650    25598977    5  Extended
/dev/sda4            7650       19458    94848000    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5            4463        4827     2928640   82  Linux swap / Solaris
/dev/sda6            4827        7650    22669312   83  Linux


at this point, i'm thinking the card itself might be bad. any suggestions?

thanks =)

I can't tell much from what you posted; however, I'm thinking that you only have one hard drive on your system (/dev/sda). If that is the case and/dev/sdb is your SD card, then you should immediately take a full backup with it. Don't use the card for anything else and only work from the backup 

```
Sudo dd if=/dev/sdb of=/home/$USER/SD
``` will you give a complete image of you SD card. From there you can try to mount it

---

### Post by thahir1986 on 2010-07-22
i'm too pretty sure /dev/sdb should be the SD card, follow the code given by jbrown

---

