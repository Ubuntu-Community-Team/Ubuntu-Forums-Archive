---
title: "Can't use space on ext4 partition after upsizing"
date: 2010-01-31
forum: General Help
---

### Post by Eagleguy125 on 2010-01-31
I recently dropped Windows as my primary operating system in favor of Ubuntu, (I've used Ubuntu off and on for years, but Karmic really sold me on Linux once and for all.) but I only had about 20GB of free space to allocate to the OS when I was installing. I have two 186GB (usable) internal hard drives, with the first being NTFS for Windows and the second having a chunk for NTFS (shared media space, soon to be moved) with the remainder allocated as ext4 and swap.

Here's my issue: as I said, I originally allocated 20GB. After clearing some space on the NTFS partition that dominated the rest of the disc, I cleared 80GB up as free space from within the built-in Windows partitioning tool before booting up from an Ubuntu LiveCD, firing up gparted, unmounting the swap partition the LiveCD had grabbed onto, and combining the newly freed 80GB with my 20GB ext4 partition. This all sounds well and good, but I got an "input/output error" on the last step of the operation. Now booted back into Ubuntu through the ext4 partition, sure enough, my computer tells me that I have 100GB (roughly) total space available, but I have the same 1.2GB free that I had before starting this operation.

To summarize, I added 80GB of space to my ext4 partition, but it appears to the system as though the space is already used up. I can't find what it claims is using that space or any way of telling the system to just treat the new space as free space and ignore what it may think is there. I would like to get through this without reinstalling, as I've done some really heavy customizing to my installation. Is there any easy way of fixing this?

--Ethan

---

### Post by john newbuntu on 2010-01-31
Can you please post the outputs of:
sudo fdisk -l
df -Th

---

### Post by Eagleguy125 on 2010-01-31
> **john newbuntu said:**
> Can you please post the outputs of:
sudo fdisk -l
df -Th

Output of fdisk -l:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03390339

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24322   195358560+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007481e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11268    90505216    7  HPFS/NTFS
/dev/sdb2           11269       24321   104848222+   5  Extended
/dev/sdb5           11269       24207   103932486   83  Linux
/dev/sdb6           24208       24321      915673+  82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x904157f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

Output of df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb5     ext4     19G   17G  1.2G  94% /
udev         tmpfs   1007M  420K 1007M   1% /dev
none         tmpfs   1007M  440K 1006M   1% /dev/shm
none         tmpfs   1007M  192K 1007M   1% /var/run
none         tmpfs   1007M     0 1007M   0% /var/lock
none         tmpfs   1007M     0 1007M   0% /lib/init/rw


Hmmm... Gparted is claiming 100GB, while df is claiming 20GB. Intriguing.

---

### Post by Eagleguy125 on 2010-02-01
Fixed! After trying many variants on this plan, I finally got gparted on the Ubuntu LiveCD to recheck and fix the filesystem and correctly report free space. However, (and this may just be a quirk of ext4 or Ubuntu that I'm unfamiliar with), gparted on both the LiveCD and inside of my standard installation both report 81.07GB of free space while navigating to the root of my filesystem claims 76.01GB. Go figure.

---

### Post by mcduck on 2010-02-01
> **Eagleguy125 said:**
> Fixed! After trying many variants on this plan, I finally got gparted on the Ubuntu LiveCD to recheck and fix the filesystem and correctly report free space. However, (and this may just be a quirk of ext4 or Ubuntu that I'm unfamiliar with), gparted on both the LiveCD and inside of my standard installation both report 81.07GB of free space while navigating to the root of my filesystem claims 76.01GB. Go figure.

Gparted tells the free amount on the file system, while Nautilus shows the amount of free space available to current user. Ext filesystyems reserve 5% of the disk space for root user only, so that space doesn't count as available for any normal usrs.

---

