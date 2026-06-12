---
title: "Creating RAID 1 array"
date: 2010-11-18
forum: General Help
---

### Post by UltraAnders on 2010-11-18
I'd like to create a software RAID 1 to backup my data. Is it possible to create the array with existing data on one of the HDDs? 

Below is my partition layout. It's HDD1, partition 3 that I'd like to RAID 1 with HDD2. HHD1 and HDD2 are same size, brand and model, although the last digit differs (revision number?), i.e. WDC WD5000AAKS-0 and WDC WD5000AAKS-7

SSD:
1 - 256mb (ext2), mount point: /boot
--then in the extend partition:
2 - 15gb (ext2), mount point: /
3 - the rest left spare

HDD1:
1 - 100gb (ntfs), Windows XP
--then in the extended partition:
2 - 2gb (linux-swap), mount point: /swap
3 - the rest (ext3), mount point: /home

HDD2:
Blank

---

### Post by dcstar on 2010-11-18
> **UltraAnders said:**
> I'd like to create a software RAID 1 to backup my data. Is it possible to create the array with existing data on one of the HDDs? 


[https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID)

---

