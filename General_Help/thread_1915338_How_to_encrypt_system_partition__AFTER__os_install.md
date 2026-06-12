---
title: "How to encrypt system partition  AFTER  os installation?"
date: 2012-01-26
forum: General Help
---

### Post by iX9 on 2012-01-26
Hi ;)
With alternate LiveCD, it is relatively simple to encrypt / root partition while install. Some How-To can be found here.

I have Kubuntu Natty already installed with no encryption. How to add encryption?

My situation:
USB external hardisk with two partitions.
/dev/sdb1 (FAT32) /boot   for boot
/dev/sdb2 (EXT3)  /       system partition with /home and SwapFile inside
Grub2 installed on MBR /dev/sdb.

I need to fully encrypt /dev/sdb2. When booting, enter password.
Later, maybe I would like to add some scrip to check hashes of boot files on unencrypted partition to ensure they not compromised.

---

### Post by claracc on 2012-01-26
[https://help.ubuntu.com/community/DrivesAndPartitions#Removable_Storage](https://help.ubuntu.com/community/DrivesAndPartitions#Removable_Storage)

Go to removable storage section of the foementioned document.

---

