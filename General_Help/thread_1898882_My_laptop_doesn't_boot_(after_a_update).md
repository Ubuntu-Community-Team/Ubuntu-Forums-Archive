---
title: "My laptop doesn't boot (after a update)"
date: 2011-12-22
forum: General Help
---

### Post by sridharpandu on 2011-12-22
I updated ubuntu (using the update manager) and when I restarted my laptop  I get the following message
 mount: mounting /dev/mapper/Monsoon-root on /root failed: Invalid argument
 mount: mounting /dev on /root/dev failed: No such file or directory
 mount: mounting /sys on /root/sys failed: No such file or directory
 mount: mounting /proc on /root/proc failed: No such file or directory
 Target file system doesn't have requested /sbin/init
 No init found. Try passing init= bootarg.
 
 BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash) 
 Enter 'help' for a list of built-in commands
 
 (initramfs)

So I copied an ISO image on a USB disk and booted from it, I get the same shell environment
 BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
 Enter 'help' for a list of built-in commands
 
I ran fdisk -l and it gave me the following
 (pipe symbols added by me to make the readout tabular)
 
 Disk /dev/sda: 320.1GB, 320072933376 bytes
 255 heads, 63 sectors/track, 38913 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x0008157d
 
 Device      |Boot | Start |    End |      Blocks   |  Id  | System
 /dev/sda1 |      * |       1 |      32 |       248832  | 83  | Linux
 Partition 1 does not end on cylinder boundary
 /dev/sda2 |        |      32| 38914 | 312320001 |    5 | Extended  
 /dev/sda5 |        |      32| 38914 | 312320000 |   8e| Linux LVM
 
 Disk /dev/sdb: 8004 MB, 8004304896 bytes
 35 heads, 21 sectors/track, 21269 cylinders
 Units = cylinders of 735 * 512 = 376320 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum / optimal): 512 bytes / 512 bytes
 Disk identifier: 0x0008157d
 
 Device      |Boot | Start |    End |      Blocks   |  Id  | System
 /dev/sdb1 |      * |       1 | 21270 |   7816688  |    b  | W95 FAT32
 
 Disk /dev/dm-0:  310.4 GB, 310361718784 bytes
 255 heads, 63 sectors/track, 37732 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum / optimal): 512 bytes / 512 bytes
 Disk identifier: 0x00000000
 
 Disk /dev/dm-1:  9432 MB, 9432989696 bytes
 255 heads, 63 sectors/track, 1146 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum / optimal): 512 bytes / 512 bytes
 Disk identifier: 0x00000000 

Is there any way to make the drive bootable? I would like to recover my data and my emails. Any help would be appreciated.

---

