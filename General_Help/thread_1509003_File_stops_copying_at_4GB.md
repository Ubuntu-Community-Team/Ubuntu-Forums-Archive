---
title: "File stops copying at 4GB?"
date: 2010-06-13
forum: General Help
---

### Post by pandaconda on 2010-06-13
Just got my HTPC up and running with Ubuntu, and tried to copy a large video file to the HD.  It hung up at 4GB/7.5GB completed and gave an error message, but didn't say what's wrong. I tried it again, same thing.  I experienced something similar on my old Windows setup, where it wouldn't allow files larger than 4gb, but that was using FAT32 or NTFS, I'm not sure which.

I'm assuming I'm using the default ext4 file system, which I thought was supposed to support files up to at least 16GB, and I've never had a problem like this on my dual-boot setup with the other computer.  I'm using a new WD Green hard drive.

Any help would be greatly appreciated, thanks!

---

### Post by MooPi on 2010-06-13
Can you post the output to this command:
```
sudo fdisk -l
```

---

### Post by ibuclaw on 2010-06-13
The max file size is 16 TiB on ext4. And the 4GB cap is on FAT32 file systems.

Where are you copying the file to?

---

### Post by pandaconda on 2010-06-15
Here is the output of "sudo fdisk -l"

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035ca6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120944   971481088   83  Linux
/dev/sda2          120945      121602     5278721    5  Extended
/dev/sda5          120945      121602     5278720   82  Linux swap / Solaris

Disk /dev/sdf: 8019 MB, 8019509248 bytes
5 heads, 32 sectors/track, 97894 cylinders
Units = cylinders of 160 * 512 = 81920 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19e11eaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              51       97895     7827520    c  W95 FAT32 (LBA)


Thanks!

---

