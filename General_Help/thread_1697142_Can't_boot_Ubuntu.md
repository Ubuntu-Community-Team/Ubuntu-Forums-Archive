---
title: "Can't boot Ubuntu"
date: 2011-02-28
forum: General Help
---

### Post by Therseo on 2011-02-28
When I select Ubuntu in my Grub menu it attempts to boot it and then it stops with the error:
```
Failed to mount /root/dev: no such directory
Failed to mount /root/sys: no such directory
Failed to mount /root/proc: no such directory
```
I do not understand why it has done it, It was working, then it stopped
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b8aac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30028   241190912   83  Linux
/dev/sda2           30028       30402     3005441    5  Extended
/dev/sda5           30028       30402     3005440   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbf2bbf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

```
Please help, thanks
Charles

---

