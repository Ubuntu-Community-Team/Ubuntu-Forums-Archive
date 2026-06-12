---
title: "Error creating partition Using Disk Utility  (ubuntu 11.10 live CD)"
date: 2012-03-23
forum: General Help
---

### Post by XxUseRxX on 2012-03-23
Hi ,
while iam trying to create a new partition it says :
```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=152035131392, size=49533612544, type=0x83
Entering MS-DOS parser (offset=0, size=250999111168)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 26213935104, type 0x07)
new part entry
looking at part 1 (offset 26214398976, size 224771703808, type 0x0f)
Entering MS-DOS extended parser (offset=26214398976, size=224771703808)
readfrom = 26214398976
MSDOS_MAGIC found
readfrom = 57667438080
MSDOS_MAGIC found
readfrom = 125971092992
MSDOS_MAGIC found
readfrom = 151516086272
MSDOS_MAGIC found
readfrom = 201568711680
MSDOS_MAGIC found
readfrom = 230011729920
MSDOS_MAGIC found
readfrom = 152036075520
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failed

```
????

---

### Post by XxUseRxX on 2012-03-23
```
root@ubuntu:~# sudo fdisk -l omitting empty partition (11)  Disk /dev/sda: 251.0 GB, 250999111168 bytes 255 heads, 63 sectors/track, 30515 cylinders, total 490232639 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x278965d8     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          63    51199154    25599546    7  HPFS/NTFS/exFAT /dev/sda2        51199998   490207231   219503617    f  W95 Ext'd (LBA) /dev/sda5        51200000   112627711    30713856    7  HPFS/NTFS/exFAT /dev/sda6       112631778   246037290    66702756+   7  HPFS/NTFS/exFAT /dev/sda7       246038528   295929855    24945664   83  Linux /dev/sda8       295931904   296943615      505856   82  Linux swap / Solaris /dev/sda9       393688953   429722684    18016866    7  HPFS/NTFS/exFAT /dev/sda10      449249280   490207231    20478976    7  HPFS/NTFS/exFAT  Disk /dev/sdb: 2063 MB, 2063597568 bytes 255 heads, 63 sectors/track, 250 cylinders, total 4030464 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x01a53e32     Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *          63     4030463     2015200+   c  W95 FAT32 (LBA)
```

---

