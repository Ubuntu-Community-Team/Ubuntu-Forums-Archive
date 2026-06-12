---
title: "Resize root (logical) partition on Windows-7/Ubuntu-10.04 dual-boot?"
date: 2010-09-29
forum: General Help
---

### Post by silentstone on 2010-09-29
I want to resize my Ubuntu partition without junking either system install.   When I installed UbuntuNR-10.04 to my new Win-7 netbook, I opted to repartition in the installer, shrinking the Windows partition, creating a new extended partition right behind it, and filling that with one giant logical partition for Ubuntu.  Everything was fine until I tried to boot Windows from the Grub boot menu:  It didn't work, and my only recourse was to reinstall Windows from the recovery partition, lacking a Windows 7 installation disk or anything resembling a Windows Recovery Console. 

Currently, my partitions look like this:
```
root@mouse:~# fdisk -l /dev/sda

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x935d59dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5791    46508565+   7  HPFS/NTFS    =win7
/dev/sda2           10475       29093   149557117+   5  Extended    
/dev/sda3           29094       30400    10485760   1b  Hidden W95 FAT32   =win7 recovery
/dev/sda4           30400       30401       16064+   b  W95 FAT32    =eeepc boot booster
/dev/sda5           10475       29093   149557086   83  Linux    =ubuntulucid
root@mouse:~# 
root@mouse:~# parted --list
Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  47.6GB  47.6GB  primary   ntfs         boot
 2      86.2GB  239GB   153GB   extended
 5      86.2GB  239GB   153GB   logical   ext2
 3      239GB   250GB   10.7GB  primary   fat32        hidden
 4      250GB   250GB   16.5MB  primary

```Windows was already shrunk with its own partitioner, and boots fine.  Now, can the extended partition (sda4), with Ubuntu on its logical partition (sda5), be moved or grown to the left without destroying its logical partition?  And what will Grub2 do, or the initrd disk-image?

---

### Post by gzarkadas on 2010-09-29
You will first extend your extended partition (sda2) to the left. Then move your logical partition (sda5) to the left inside the grown extended partition. Then expand your logical partition to cover the entire extended partition. Do one thing at a time, not all three together, to minimise the possibility of leaving your linux partition in an inconsistent state. Then run `update-grub'. I don't think your initramfs will need to be updated, but if you are unsure run also `update-initramfs -u -k all' to update it for all your installed kernels.

---

### Post by silentstone on 2010-09-30
Thank you, gzarkadas!  I followed your steps carefully through the partitioning.  The data on the Ubuntu root partition seems intact (the partitioner shows it).  Unfortunately, the live-cd I'm using doesn't have Grub2, so I'll have to wait on updating that.

---

### Post by Mark Phelps on 2010-09-30
Glad to see you got it working ... but for future reference, and to prevent this same problem from happening again, do not repeat this: "I opted to repartition in the installer". That has a bad reputation for corrupting Win7 OS partitions as a side-effect.

---

### Post by silentstone on 2010-10-01
> **Mark Phelps said:**
> do not repeat this: "I opted to repartition in the installer". That has a bad reputation for corrupting Win7 OS partitions as a side-effect.
You got that right :/ What can I say...I was so impressed and excited with the Netbook Remix live-cd and its performance that I got impatient and made more trouble for myself. 

*Don't let it happen to you!*

---

