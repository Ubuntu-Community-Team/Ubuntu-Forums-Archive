---
title: "How to hide a partition?"
date: 2012-01-03
forum: General Help
---

### Post by ashkano on 2012-01-03
Is there a way to hide a partition in Ubuntu? 
 
I have a dualboot Windows 7 with Ubuntu. There is a system reserved partition of Windows 7. I want to hide this partition.

---

### Post by samigina on 2012-01-03
[B]The easy way
[/B]
Install Gparted "sudo apt-get install gparted", open it, select your disk, select you partition, right click, properties, flags, hidden.

**The hard way**

Here is a list of the commonly used partitions, hide and unhide

< bit position>-----ID------Partition type------------
0	0	0	0	0	1	1	1	---	7	----	ntfs	
0	0	0	1	0	1	1	1	---	17	---	ntfs	(hidden)
1	0	0	0	0	0	1	1	---	83	---	native Linux	
1	0	0	1	0	0	1	1	---	93	---	native Linux	(hidden)
0	0	0	0	0	1	1	0	---	6	----	fat16	
0	0	0	1	0	1	1	0	---	16	---	fat16	(hidden)
0	0	0	0	1	1	0	0	---	c	----	fat32 (LBA)	
0	0	0	1	1	1	0	0	---	1c	---	fat32 (LBA)	(hidden)
1	0	1	0	0	1	0	1	---	a5	---	BSD	
1	0	1	1	0	1	0	1	---	b5	---	BSD	(hidden)
1	0	1	1	1	1	1	1	---	bf	---	Solaris 
1	0	1	0	1	1	1	1	---	af	---	Solaris	(hidden)
0	0	0	0	0	1	0	1	---	5	----	Dos extended partition	
0	0	0	1	0	1	0	1	---	15	---	Dos extended partition	(hidden)
1	0	0	0	0	1	0	1	---	85	---	Linux extended partition	
1	0	0	1	0	1	0	1	---	95	---	Linux extended partition	(hidden)

The above hidden partitions, as far as I am aware, are supported by all the major PC operating systems and nobody uses another convention. You can find them listed in &#8220;fdisk&#8221;, &#8220;cfdisk&#8221; and &#8220;sfdisk&#8221;. With these programs a user hide the partition by altering the partition ID. Interestingly both the Linux boot loader Grub and Lilo also hides or unhides a partition simply by toggling the 5th bit of binary number of the partition ID.

---

### Post by ashkano on 2012-01-03
Thanx. It really helped.

---

### Post by pholden on 2012-01-06
> **samigina said:**
> Install Gparted "sudo apt-get install gparted", open it, select your disk, select you partition, right click, properties, flags, hidden.
I have a similar setup to the original poster (dual boot with Windows 7), and using the above method does indeed hide the Windows volume from Ubuntu, but also seems to prevent Windows actually booting... :-?

---

