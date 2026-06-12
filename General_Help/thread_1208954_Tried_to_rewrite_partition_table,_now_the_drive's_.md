---
title: "Tried to rewrite partition table, now the drive's &quot;empty&quot;"
date: 2009-07-09
forum: General Help
---

### Post by Fleshtone on 2009-07-09
Hello, 

The original problem was that Windows XP, on /dev/sda1, could not boot from the grub menu.  I tried all manner of edits to menu.lst, I tried using Super Grub Disk, which only did more damage, and I tried reinstalling GRUB.  At some point I figured that the problem may have been a dodgy Windows Master Boot Record, which I read is a delicate thing.  

So I did some reading and ran an app called "ms-sys" which is supposed to write ms-dos boot records.  After running ms-sys, I began to get an error that said "invalid partition table" if I selected Windows XP from the GRUB menu.  Then I burned a GParted LiveCD and rewrote the partition table for the Windows drive.  When I did this, that sda drive lost its partition, and now it is "unallocated".

Now things seem to have gone very awry.  The output of *sudo fdisk -l* is:
> Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003ce98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf77ba720

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1459    11719386    7  HPFS/NTFS
/dev/sdb2            1460        4998    28427017+   f  W95 Ext'd (LBA)
/dev/sdb5            1460        4998    28426986   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b5566e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS
/dev/sdc4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.


As I mentioned, /dev/sda now has only one partition; it is /dev/sda4, and I have no idea why.  The file system went from NTFS to "empty", which strikes me as a bad thing.  It also contains 0 blocks.  I understand there is a chance that I've destroyed my Windows installation, but I thought that changing the partition table doesn't actually change any data on the drive.

Additionally, /dev/sdc4 now has a boot flag, and an empty file system in a 0 block partition, and that's a drive that has nothing to do with any of this.

If it helps, here is the relevant output of *sudo lshw*:

> *-disk:0

                description: ATA Disk
                product: ST340014A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.10
                serial: 5JXFJJAW
                size: 37GiB (40GB)
                configuration: ansiversion=5 signature=0003ce98

           *-disk:1
                description: ATA Disk
                product: Maxtor 6E040L0
                vendor: Maxtor
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: NAR6
                serial: E1S0G5RE
                size: 38GiB (41GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=f77ba720

              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 3.1
                   serial: f4553409-fd0a-d54d-b732-e0a5c90bee71
                   size: 11GiB
                   capacity: 11GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2007-04-02 20:31:38 filesystem=ntfs label=MAXTOR 02 state=clean

              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.1.0,2
                   logical name: /dev/sdb2
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary extended partitioned partitioned:extended

                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 27GiB

   *-cdrom
                description: CD-R/CD-RW writer
                product: LTR-48327S
                vendor: LITE-ON
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: PUS6
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready

              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted

           *-disk:2
                description: ATA Disk
                product: MAXTOR STM332062
                vendor: Maxtor
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/sdc
                version: 3.AA
                serial: 3QF0E9HK
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0b5566e0

              *-volume
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.1.0,1
                   logical name: /dev/sdc1
                   version: 3.1
                   serial: c435ca5f-91f2-5846-a6f4-fd4b32a89927
                   size: 298GiB
                   capacity: 298GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-04-07 20:48:02 filesystem=ntfs label=MAXTOR 01 state=clean


Is there a way to unscramble this and get this machine dual-booting again?  By the way, I do not have the windows disk.  If it was absolutely necessary, I could take a long drive and get it.

Thanks for reading this!

---

### Post by Fleshtone on 2009-07-14
bumpity.

---

