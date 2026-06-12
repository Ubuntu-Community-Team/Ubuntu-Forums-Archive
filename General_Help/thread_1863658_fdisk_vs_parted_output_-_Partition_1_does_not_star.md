---
title: "fdisk vs parted output - Partition 1 does not start on physical sector boundary."
date: 2011-10-18
forum: General Help
---

### Post by alfonso78 on 2011-10-18
Hello, I have a big RAID with GPT and fdisk output is not really reassuring:

```
ubuntu@ubuntu:/mnt/big_raid$ sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x22cf0cdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbbca1224

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044377

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    78163967    39080960   83  Linux

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06b8c42b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdf: 2055 MB, 2055208960 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002a50b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          62     4011647     2005793    c  W95 FAT32 (LBA)

WARNING: GPT (GUID Partition Table) detected on '/dev/md0'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/md0: 4000.8 GB, 4000792444928 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814047744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1  4294967295  2147483647+  ee  GPT
**Partition 1 does not start on physical sector boundary.**

Disk /dev/mapper/big_raid: 4000.8 GB, 4000789168128 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814041344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

**Disk /dev/mapper/big_raid doesn't contain a valid partition table**

```

On the other hand, parted shows no errors. Anything to worry about?

```
ubuntu@ubuntu:/mnt/big_raid$ sudo parted -l
Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary               raid


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary               raid


Model: ATA INTEL SSDSA2M040 (scsi)
Disk /dev/sdc: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary  ext4         boot


Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary               raid


**Error: /dev/sde: unrecognised disk label **                                 

Model: G & T USB Flash Drive (scsi)
Disk /dev/sdf: 2055MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  2054MB  2054MB  primary  fat32        boot, lba


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/big_raid: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  4001GB  4001GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md0: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  4001GB  4001GB



```

Actually, there is one error in the parted output... I'll look into what it is... ( **Error: /dev/sde: unrecognised disk label **)

---

