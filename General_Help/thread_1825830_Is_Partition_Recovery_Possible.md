---
title: "Is Partition Recovery Possible?"
date: 2011-08-15
forum: General Help
---

### Post by ManMythLegend on 2011-08-15
I was trying to install Pinguy Linux on a partition of 1 of my 2 hard drives and instead of installing it on the partition that I boot from, I installed it over the partition that I keep my Data on.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000982ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1945139199   972568576   83  Linux
/dev/sda2      1945141246  1953523711     4191233    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1945141248  1953523711     4191232   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf98d6e74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   298616220   597232439   149308110   83  Linux
/dev/sdb2       271386045   298616219    13615087+  83  Linux
/dev/sdb3              63   271386044   135692991    7  HPFS/NTFS
/dev/sdb4       597232440   625137344    13952452+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 2055 MB, 2055021056 bytes
189 heads, 3 sectors/track, 7078 cylinders, total 4013713 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00077c7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048     4012031     2004992    b  W95 FAT32

```

sdb is the drive that I intended to boot from and sda is the drive where I store all my data.

Is there anyone way to basically undo the created partitions?

---

### Post by JC Cheloven on 2011-08-15
If you only deleted/created the partition, [there is hope]("https://help.ubuntu.com/community/DataRecovery").

If you actually installed the new system, physically overwritting your data, I'm affraid they're lost (at least the "overwritten" part). 

note: People say governmental agencies and such can recover even that, dunno if the applicable technology is of wider use. This is a bit out of reach for us anyway, I guess :D

---

### Post by ManMythLegend on 2011-08-15
As far as I can tell the original drive and possibly some files may have been overwritten to write the system files and the swap space. The installer failed however, shortly after which I realized my partitioning mistake.

I am 90% sure the original drive was ext4, but I could have been lazy and left it NTFS after purchase, in which case the file system may have been changed as well. 

Gparted shows that 17.43GB are used on the drive now after the botched install (which seems kind of large for a brand new install, imo).

Should I unallocate all the drive space and THEN try partition recovery tools like testdisk?

---

### Post by ottosykora on 2011-08-15
>they're lost (at least the "overwritten" part). <

right in this

it does not need to be all overwritten.
If the data were for example written in some fat or ntfs partition and now this was changed to some ext? and linux installed on it, chances are pretty good that most can be recovered by using test disk or similar.

---

### Post by ManMythLegend on 2011-08-15
I figured the overwritten part was gone.

Should I delete the new partition and then testdisk or will it work as is? I don't want to have to do anything to it if at all avoidable.

EDIT: I tried running testdisk without changing any of the new partitions and it found what looks to be the original partition setup but said it could not be restored. Could this be because the drive is still currently partitioned?

---

