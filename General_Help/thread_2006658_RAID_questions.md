---
title: "RAID questions"
date: 2012-06-19
forum: General Help
---

### Post by Fenlig on 2012-06-19
Hey Guys,

So heres the config.

2x 500gb Raid 1
2x 2000gb Raid 1
1x 500gb non-raid

Okay I have setup this raid from my onboard raid controller (Intel® ICH10R controller). From what I understand the OS should see the individual drives and should only see the on partition, but when i do fdisk -l I get a everything.

Am I just mistaken and the OS can see these or have I configured something wrong?

```
skay@Servertron:/etc/init.d$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3907007999  1953502976   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907007999  1953502976   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070a3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   976766975   488382464   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070a3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   976766975   488382464   83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
108 heads, 41 sectors/track, 220590 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ac13

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2046       38911       18433    5  Extended
/dev/sde5            2048       38911       18432   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_bcficbfcbc_Media'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_bcficbfcbc_Media: 2000.4 GB, 2000395833344 bytes
255 heads, 63 sectors/track, 243200 cylinders, total 3907023112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

                           Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bcficbfcbc_Media1            2048  3907007999  1953502976   83  Linux

Disk /dev/mapper/isw_fcdbbbhib_OS: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070a3b

                       Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_fcdbbbhib_OS1   *        2048   976766975   488382464   83  Linux

Disk /dev/mapper/isw_fcdbbbhib_OS1: 500.1 GB, 500103643136 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976764928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_fcdbbbhib_OS1 doesn't contain a valid partition table

Disk /dev/mapper/isw_bcficbfcbc_Media1: 2000.4 GB, 2000387047424 bytes
255 heads, 63 sectors/track, 243199 cylinders, total 3907005952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_bcficbfcbc_Media1 doesn't contain a valid partition table
```

---

