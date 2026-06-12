---
title: "GRUB2 reinstall"
date: 2010-08-27
forum: General Help
---

### Post by The_Shady_1 on 2010-08-27
I finished reinstalling W7 and am trying to reinstall GRUB2 from Live USB.I used this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to help me reinstall but with no success. I went through the commands and I got a successful message that it had been reinstalled but I don't see the GRUB menu. Right now all I see is the grub rescue prompt. What am I doing wrong?

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059227

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32f932f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79907b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       42804   343823098+   7  HPFS/NTFS
/dev/sdc2           42805       60802   144563201    5  Extended
/dev/sdc5           42805       60066   138650624   83  Linux
/dev/sdc6           60066       60802     5911552   82  Linux swap / Solaris

Disk /dev/sdd: 2030 MB, 2030043136 bytes
129 heads, 32 sectors/track, 960 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f5db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         961     1982448    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(968, 128, 32) logical=(960, 63, 32)

Thank you for your help.

---

### Post by The_Shady_1 on 2010-08-27
> **The_Shady_1 said:**
> I finished reinstalling W7 and am trying to reinstall GRUB2 from Live USB.I used this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to help me reinstall but with no success. I went through the commands and I got a successful message that it had been reinstalled but I don't see the GRUB menu. Right now all I see is the grub rescue prompt. What am I doing wrong?

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059227

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32f932f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79907b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       42804   343823098+   7  HPFS/NTFS
/dev/sdc2           42805       60802   144563201    5  Extended
/dev/sdc5           42805       60066   138650624   83  Linux
/dev/sdc6           60066       60802     5911552   82  Linux swap / Solaris

Disk /dev/sdd: 2030 MB, 2030043136 bytes
129 heads, 32 sectors/track, 960 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f5db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         961     1982448    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(968, 128, 32) logical=(960, 63, 32)

Thank you for your help.

*UPDATE*
I got GRUB back but now I cant boot into Windows. How do I make changes to GRUB to show it that Windows is now on sdb? (sda is just storage space)

---

### Post by wilee-nilee on 2010-08-27
In Ubuntu I would try
```
sudo update-grub
```

I also notice that the boot flag from your information should be on sdb rather then sda, to make sdb active, you can change this with gparted in Ubuntu.

If that doesn't do it post the bootscript in my sig in code tags as described.

---

### Post by The_Shady_1 on 2010-08-27
I did sudo update-grub when I was in live session before.Forgot that I should do it when I boot into Ubuntu, doh! Thank you for your support!

---

