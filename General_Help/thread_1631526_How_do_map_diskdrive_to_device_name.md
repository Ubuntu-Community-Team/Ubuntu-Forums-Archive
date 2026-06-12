---
title: "How do map diskdrive to device name"
date: 2010-11-26
forum: General Help
---

### Post by rbm0307 on 2010-11-26
A drive on my RAID array has failed and I need to replace it.  I can identify the UNIX device in error.  How do I identify the physical disk drive associated with this device?  The array consists of 6 drives so I'd like to get it right.

/dev/sde is the failing drive in the console log below:

```
root@mythbe:~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid6 sdg1[4] sdf1[5] sdc1[1] sdb1[0] sdd1[2] sde1[3]
      1953535744 blocks level 6, 64k chunk, algorithm 2 [6/6] [UUUUUU]
      
unused devices: <none>
root@mythbe:~# parted -l
Model: ATA IC35L040AVVA07-0 (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  38.3GB  38.3GB  primary   ext3            boot
 2      38.3GB  40.0GB  1686MB  extended
 5      38.3GB  40.0GB  1686MB  logical   linux-swap(v1)


Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary               raid


Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary               raid


Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary               raid


Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary               raid


Model: ATA ST3500630AS (scsi)
Disk /dev/sdf: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary               raid


Model: ATA WDC WD5000KS-00M (scsi)
Disk /dev/sdg: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary               raid


Model: Unknown (unknown)
Disk /dev/md0: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext3

root@mythbe:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Sep 15 23:51:21 2008
     Raid Level : raid6
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Oct 24 06:33:52 2010
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 614a41ae:61369299:f04c99b8:3fd94616 (local to host mythbe)
         Events : 0.7430

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       97        4      active sync   /dev/sdg1
       5       8       81        5      active sync   /dev/sdf1
root@mythbe:~# udisks --dump
========================================================================
Showing information for /org/freedesktop/UDisks/devices/sde
  native-path:                 /sys/devices/pci0000:00/0000:00:05.1/host9/target9:0:0/9:0:0:0/block/sde
  device:                      8:64
  device-file:                 /dev/sde
    presentation:              /dev/sde
    by-path:                   /dev/disk/by-path/pci-0000:00:05.1-scsi-1:0:0:0
  detected at:                 Thu 25 Nov 2010 05:54:44 PM EST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Thu 25 Nov 2010 05:54:44 PM EST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        500107862016
  block size:                  512
  job underway:                no
  usage:                       
  type:                        
  version:                     
  uuid:                        
  label:                       
  partition table:
    scheme:                    
    count:                     1
  drive:
    vendor:                    ATA
    model:                     Hitachi HDP725050GLA360
    revision:                  GM4OA5A2
    serial:                    GEA530RE20JZSE
    WWN:                       5000cca32cdc6ecb
    detachable:                0
    can spindown:              1
    rotational media:          Yes, at 7200 RPM
    write-cache:               enabled
    ejectable:                 0
    adapter:                   /org/freedesktop/UDisks/adapters/0000_3a00_3a05_2e1
    ports:
      /org/freedesktop/UDisks/adapters/0000_3a00_3a05_2e1/host9
    similar devices:
    media:                     
      compat:                 
    interface:                 ata
    if speed:                  (unknown)
    ATA SMART:                 not available

========================================================================
Showing information for /org/freedesktop/UDisks/devices/sde1
  native-path:                 /sys/devices/pci0000:00/0000:00:05.1/host9/target9:0:0/9:0:0:0/block/sde/sde1
  device:                      8:65
  device-file:                 /dev/sde1
    presentation:              /dev/sde1
    by-id:                     /dev/disk/by-id/ata-Hitachi_HDP725050GLA360_GEA530RE20JZSE-part1
    by-id:                     /dev/disk/by-id/scsi-SATA_Hitachi_HDP7250_GEA530RE20JZSE-part1
    by-id:                     /dev/disk/by-id/wwn-0x5000cca32cdc6ecb-part1
    by-id:                     /dev/disk/by-uuid/c1f3bc50-936a-4a05-9c24-263ee54eee37
    by-path:                   /dev/disk/by-path/pci-0000:00:05.1-scsi-1:0:0:0-part1
  detected at:                 Fri 26 Nov 2010 01:47:10 PM EST
  system internal:             1
  removable:                   0
  has media:                   1 (detected at Fri 26 Nov 2010 01:47:10 PM EST)
    detects change:            0
    detection by polling:      0
    detection inhibitable:     0
    detection inhibited:       0
  is read only:                0
  is mounted:                  0
  mount paths:             
  mounted by uid:              0
  presentation hide:           0
  presentation nopolicy:       0
  presentation name:           
  presentation icon:           
  size:                        500105217024
  block size:                  512
  job underway:                no
  usage:                       filesystem
  type:                        ext2
  version:                     1.0
  uuid:                        c1f3bc50-936a-4a05-9c24-263ee54eee37
  label:                       
  partition:
    part of:                   /org/freedesktop/UDisks/devices/sde
    scheme:                    mbr
    number:                    1
    type:                      0x83
    flags:                    
    offset:                    32256
    alignment offset:          0
    size:                      500105217024
    label:                     
    uuid:                      

```

Thanks.

---

### Post by dcstar on 2010-11-26
> **rbm0307 said:**
> A drive on my RAID array has failed and I need to replace it.  I can identify the UNIX device in error.  How do I identify the physical disk drive associated with this device?  The array consists of 6 drives so I'd like to get it right.

/dev/sde is the failing drive in the console log below:
........

You may be able to use the **hdparm** command to put it to sleep, so then it will be the one with no LED blinking, or:
[http://deandra.homeip.net/node/14](http://deandra.homeip.net/node/14)

---

### Post by rbm0307 on 2010-11-27
> **dcstar said:**
> You may be able to use the **hdparm** command to put it to sleep, so then it will be the one with no LED blinking, or:
[http://deandra.homeip.net/node/14](http://deandra.homeip.net/node/14)

Thanks for responding.  Unfortunately, none of the drives have activity LEDs so hdparm won't work for me,  The recipe in the link referred to a RAID1 array with two drives. Tracing the failing drive in that configuration would be easier than in my 6 drive RAID6.

I have a feeling that the output from **udisks --dump** command will help me in conjunction with info from the BIOS.  I'm going to investigate further along this path.

---

### Post by rbm0307 on 2011-01-08
Back with the same request.

A disk interface is starting to fail and is reporting in /var/log/messages:
```
Jan  8 20:44:58 mythbe kernel: [106945.435529] ata5: nv: skipping hardreset on occupied port
Jan  8 20:44:59 mythbe kernel: [106945.990047] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  8 20:44:59 mythbe kernel: [106946.041662] ata5.00: configured for UDMA/33
Jan  8 20:44:59 mythbe kernel: [106946.041713] ata5: EH complete
Jan  8 20:54:28 mythbe kernel: [107515.475337] ata5: hard resetting link
Jan  8 20:54:28 mythbe kernel: [107515.475340] ata5: nv: skipping hardreset on occupied port
Jan  8 20:54:29 mythbe kernel: [107516.020057] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan  8 20:54:29 mythbe kernel: [107516.080426] ata5.00: configured for UDMA/33
Jan  8 20:54:29 mythbe kernel: [107516.080470] ata5: EH complete
```

The kernel has identified the failing interface/device as **ATA5.00**.  How do I map this to a physical drive in the system?  **udisks --dump** does not help with this mapping and I can't readily identify any information from /proc/  

Please help me to understand this.

TIA

---

### Post by Ocxic on 2011-01-08
generally in my experience, the device naming relies on your disk port number, ex:

SATA port 1 = /dev/sda
SATA port 2 = /dev/sdb
and so on.

secondly, removing/unpluging a good drive in a RAID 5 (when one has already failed) array will cause the whole array to fail, and most likely not boot, so you can try process of elimination maybe?

---

### Post by efflandt on 2011-01-08
Do you think something here might be a clue (like serial number)?
    
model:                     Hitachi HDP725050GLA360
revision:                  GM4OA5A2
serial:                    GEA530RE20JZSE
WWN:                       5000cca32cdc6ecb

You cannot necessarily go by how the SATA ports are marked on the board, because when I plug my DVD drive into what I think is SATA port 3, Linux shows it as ata4, and if I plug it into port 4, Linux shows it as ata3.

But my ata1 is /dev/sda and ata2 is /dev/sdb, so from that it would appear that ata5 would be /dev/sde.  You can also get the serial number with **sudo hdparm -i /dev/sde** (that is -i as in info)

---

### Post by rbm0307 on 2011-01-10
> **Ocxic said:**
> generally in my experience, the device naming relies on your disk port number, ex:

SATA port 1 = /dev/sda
SATA port 2 = /dev/sdb
and so on.

If it were only so easy.  I have an IDE system disk attached to IDE1:

IDE port 1 = /dev/sdc

This throws a wrench into the works because I can't assume that SATA port 3 = /dev/sdd because of this hardware annomoly.

> **Ocxic said:**
> 
secondly, removing/unpluging a good drive in a RAID 5 (when one has already failed) array will cause the whole array to fail, and most likely not boot, so you can try process of elimination maybe?
I have a RAID6 array so failing a disk will cause the array to restructure parity throughout the remaining drives.  I could try failing disk-by-disk and see if the entries in /var/log/message stop.  It would be a slow process but doable.

---

### Post by rbm0307 on 2011-01-10
> **efflandt said:**
> Do you think something here might be a clue (like serial number)?
    
model:                     Hitachi HDP725050GLA360
revision:                  GM4OA5A2
serial:                    GEA530RE20JZSE
WWN:                       5000cca32cdc6ecb

You cannot necessarily go by how the SATA ports are marked on the board, because when I plug my DVD drive into what I think is SATA port 3, Linux shows it as ata4, and if I plug it into port 4, Linux shows it as ata3.

But my ata1 is /dev/sda and ata2 is /dev/sdb, so from that it would appear that ata5 would be /dev/sde.  You can also get the serial number with **sudo hdparm -i /dev/sde** (that is -i as in info)

I do have the serials and model numbers to guide me, yes. I have some duplicate drives in the array which adds a bit of complexity to the problem.  Still the udisks output doen't help me to map to the "ata" identifier used by the kernel to record in /var/log/messages and you are right that I can't depend on Ubuntu sequentially mapping SATA ports to block device identifiers. I guess this will be a slow mapping process as I outlined above.

Thanks.

---

