---
title: "Partition Problems, Extended Partion too long."
date: 2011-05-11
forum: General Help
---

### Post by 0akash0 on 2011-05-11
Dear geniuses,

Today, I was experiencing some lack of storage space on my computer, so I just wanted to find out what caused it. In the "Disk Utility" I found that I had following partitions:

Total 160GB SATA

Sda1 = 42GB NTFS (Windows Xp)
Sda2 = 118GB Extended (Master Boot Record) - Container for logical partitions
Sda5 = Swap 4.1 GB
Sda6 = 114GB EXT4 Mounted at /

I thought that 118GB was too much for MBR, how do I reduce it? Is there any harm if I do?

Please Help.

Thanking you in advance.

---

### Post by garvinrick4 on 2011-05-11
#mbr (master boot record) is in sda not a partition per say and where the boot manager is installed. (grub)
#The 114 gig partition of / is your linux install
#The swap is just part of hard disk used as scratch disk for ram when you get low in linux.
#You can resize anything you want to in a program called gparted:
#extended partition is a house for logical partitions where linux survives. Windows likes Primary partitions can only have 4 on a drive. (links will explain)
```
sudo apt-get install gparted
```# read up on gparted to understand what you are doing it is a partition manager
and you can make a mess of your drive.
Here are some links do not know how current but gparted been the same for a while:
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by vanadium on 2011-05-11
> **0akash0 said:**
> 
I thought that 118GB was too much for MBR, how do I reduce it? Is there any harm if I do?

Thanking you in advance.
Do you actually experience an issue? If not, do not bother.

---

