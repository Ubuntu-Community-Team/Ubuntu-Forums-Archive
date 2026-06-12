---
title: "MDADM issues with new raid"
date: 2010-09-08
forum: General Help
---

### Post by Onthax on 2010-09-08
Hey Guys

got an annoying one

running mythbuntu 10.04

have 7 drives 6 of which i want in a raid 6 array

so i partition the drives with sector starting at 128

```
sudo fdisk -u /dev/sda
```
Then new partition > primary > starting sector = 128 > ending = last sector
press t and set type to FD (Linux Raid autodetect)
i do this on /dev/sda,sdb,sdc,sdd,sde,sdf

then i create an mdadm array using 

```
sudo mdadm --create /dev/md0 --verbose --chunk=128 --auto=md --level=raid6 --raid-devices=6 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
```

kewl, all good and created successfully
run a dmadm --detail /dev/md0

 ```
sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Sep  9 00:45:10 2010
     Raid Level : raid6
     Array Size : 7814057472 (7452.07 GiB 8001.59 GB)
  Used Dev Size : 1953514368 (1863.02 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Sep  9 00:49:06 2010
          State : active, resyncing
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K

 Rebuild Status : 1% complete

           UUID : 356dba53:cc72b0a6:462a36bb:f8f383a4 (local to host media)
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda1
       1       8       16        1      active sync   /dev/sdb1
       2       8       32        2      active sync   /dev/sdc1
       3       8       48        3      active sync   /dev/sdd1
       4       8       64        4      active sync   /dev/sde1
       5       8       80        5      active sync   /dev/sdf1


```

All good and sweet

reboot the box, all of a sudden there is a 2tb partition made on /dev/md0 called /dev/md0p1
when i run ```
 Sudo Fdisk -u /dev/md0 i get 
sudo fdisk -u /dev/md0

WARNING: The size of this disk is 8.0 TB (8001594851328 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID
partition table format (GPT).


WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c').

Command (m for help): p

Disk /dev/md0: 8001.6 GB, 8001594851328 bytes
255 heads, 63 sectors/track, 972805 cylinders, total 15628114944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 524288 bytes
Disk identifier: 0x7cbb90c0

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1             128  3907029167  1953514520   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.
Command (m for help):
```

then when i run
```
sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Sep  9 00:45:10 2010
     Raid Level : raid6
     Array Size : 7814057472 (7452.07 GiB 8001.59 GB)
  Used Dev Size : 1953514368 (1863.02 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Sep  9 00:49:06 2010
          State : active, resyncing
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K

 Rebuild Status : 1% complete

           UUID : 356dba53:cc72b0a6:462a36bb:f8f383a4 (local to host media)
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       8       64        4      active sync   /dev/sde
       5       8       80        5      active sync   /dev/sdf 
```
so now it's not using partitions and i've lost 2tb to a random partition that's been created, anyone have any ideas?

---

### Post by Onthax on 2010-09-09
bump

---

### Post by srs5694 on 2010-09-09
First, although I gather it's possible to partition a RAID array, the way I've done it myself is to partition the individual disks and RAID together the individual partitions. In other words, I'd create, say, /dev/sda1, /dev/sda2, /dev/sda3, and equivalents on other drives, and then link together /dev/sda1, /dev/sdb1, and so on to create /dev/md0; and link /dev/sda2, /dev/sdb2, and so on to create /dev/md1, and so on. Done this way, there's no need to partition the RAID devices, so you wouldn't touch them with fdisk.

Second, if you have a reason for creating a big mongo RAID device (/dev/md0) and then partitioning it, fdisk is the wrong tool for the job. This is because your RAID device, as it exists now, is 8 TB in size. As fdisk warns, it can't handle disks that size. Instead, you should use GNU Parted, GParted, or gdisk. When using GNU Parted, GParted, or some other libparted-based tool, you must explicitly tell it to use GPT rather than MBR partitions. (If you use gdisk, it uses GPT automatically, since it's the GPT equivalent of fdisk.)

As to why you're seeing the inconsistent use of partitions vs. disks and the other issues, I can't say I have any ideas on that. My suggestion would be to disassemble the RAID array and start again. Perhaps you erred in typing a command somewhere along the line, or maybe old or random data on the disks is being misinterpreted. (You could try wiping at least the first couple megabytes of each drive with dd, and/or start your partitions at a different location, like sector 2048.)

---

### Post by Onthax on 2010-09-09
> **srs5694 said:**
> First, although I gather it's possible to partition a RAID array, the way I've done it myself is to partition the individual disks and RAID together the individual partitions. In other words, I'd create, say, /dev/sda1, /dev/sda2, /dev/sda3, and equivalents on other drives, and then link together /dev/sda1, /dev/sdb1, and so on to create /dev/md0; and link /dev/sda2, /dev/sdb2, and so on to create /dev/md1, and so on. Done this way, there's no need to partition the RAID devices, so you wouldn't touch them with fdisk.

Second, if you have a reason for creating a big mongo RAID device (/dev/md0) and then partitioning it, fdisk is the wrong tool for the job. This is because your RAID device, as it exists now, is 8 TB in size. As fdisk warns, it can't handle disks that size. Instead, you should use GNU Parted, GParted, or gdisk. When using GNU Parted, GParted, or some other libparted-based tool, you must explicitly tell it to use GPT rather than MBR partitions. (If you use gdisk, it uses GPT automatically, since it's the GPT equivalent of fdisk.)

As to why you're seeing the inconsistent use of partitions vs. disks and the other issues, I can't say I have any ideas on that. My suggestion would be to disassemble the RAID array and start again. Perhaps you erred in typing a command somewhere along the line, or maybe old or random data on the disks is being misinterpreted. (You could try wiping at least the first couple megabytes of each drive with dd, and/or start your partitions at a different location, like sector 2048.)

I'm only using fdisk to do the initial partitions on the disk which are 2tb, then creating the array on the 2tb partitions.

Then i'm hoping to plug the mdadm array into lvm and set it up that way, but it keeps making a 2tb array and killing partitions, annoying the crap out of me

just replicated it in VMware using 10gb drives

---

### Post by Onthax on 2010-09-10
used parted instead of fdisk and set label to gpt, all working great now : - )

---

