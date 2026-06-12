---
title: "Unmount and hide windows partition"
date: 2011-01-09
forum: General Help
---

### Post by electronictim on 2011-01-09
Hi there.
When running linux (Lubuntu 10.04) my windows partition mounts automatically and can be opened and edited in file manager.  Is there any way I can prevent it mounting when linux launches, prevent it from being mounted in linux, and (ideally) prevent it from being displayed/opened/edited at all from linux?

(In case it's relevant: 
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe10f058e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         912     7325608+  12  Compaq diagnostics
/dev/sda2   *         913        4560    29302560    7  HPFS/NTFS
/dev/sda3            4561        6019    11717633    5  Extended
/dev/sda4            6019       30402   195851264    7  HPFS/NTFS
/dev/sda5            4561        4804     1952768   82  Linux swap / Solaris
/dev/sda6            4804        5411     4881408   83  Linux
/dev/sda7            5412        6019     4881408   83  Linux

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         976     7839698    b  W95 FAT32

Disk /dev/sdc: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02a8f889

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       43777   351638721    b  W95 FAT32

```

---

### Post by TeoBigusGeekus on 2011-01-09
```
sudo nano /etc/fstab
```
Comment out the lines referring to your windows partitions.

---

