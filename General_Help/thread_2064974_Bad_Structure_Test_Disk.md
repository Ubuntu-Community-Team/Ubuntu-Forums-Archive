---
title: "Bad Structure Test Disk"
date: 2012-09-30
forum: General Help
---

### Post by nk1 on 2012-09-30
Can somebody help me figuring out why Teskdisk says in the following data that the structure is bad.

The end size of the sector is much larger than the fourth partition and none of the partition is overlapping but it does'nt let me choose the fourth partition ( Bazzinga )

Disk \\.\PhysicalDrive0 - 320 GB / 298 GiB - CHS 38914 255 63

 HPFS - NTFS              0  32 33    12 223 19     204800 [System Reserved]
 HPFS - NTFS             12 223 20  9138  11 25  146595840
 HPFS - NTFS           9138  11 26 18276  22 50  146802688 [Travaux]
 HPFS - NTFS          18276  22 51 25860 162 30  121845760 [Misceo]
 HPFS - NTFS          25860 162 31 35664 230 22  157505536 [Bazzinga]

---

### Post by oldfred on 2012-10-01
In Windows did you create more than the 4 primary partitions. It converts to dynamic which uses logical partitions that may overlap the physical partitions?

Or is an extended partition just beyond the end of the drive. I cannot easily convert the testdisk CHS output and prefer just the sector output from fdisk

sudo fdisk -lu

If just partition table issue not dynamic partitions.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

