---
title: "installation partitioning questions!!!"
date: 2011-05-30
forum: General Help
---

### Post by evilheart on 2011-05-30
hi , i am new linux user , i installed ubuntu through wubi couple of weeks ago and it crashed , so i want to install lubuntu from live CD , but i am still confused at the partitioning step , as i want to be 100% sure of what i am doing , i already discussed this problem in another topic , but probably because of my bad explaining , i didn't get the answer i wanted.

i already read some of the ubuntu and Gparted partitioning tutorials , so i think i have some back ground , my questions is :

- can i delete the only primary partition on one of my HDD? does the size of the partition will be an unallocated memory or it will be added to the extended partition ? same question also for logical partitons.

- if i deleted one of my partitions , and assumed it will turn into unallocated memory , i can use it to make ubuntu partitions , right?

- then ,if i created ubuntu partitions from the unallocated memory , will that format my whole HDD?? i read something like changing the partition table will format the HDD.

- instead of making a swap partition , can i skip that in the installation and create a swap file later? in fact i want just format a primary partition for root , and skip making either swap or home partitions.

- can i assign a FAT32 drive as my home folder without formatting it ?

thanks in advance

---

### Post by JRV on 2011-05-30
If you are going to use the entire disk for Ubuntu you can just use the guided install option in the partitioner.

Your questions seem to apply to the manual partitioner, so I am assuming that is what you are doing.

> **evilheart said:**
> 

- can i delete the only primary partition on one of my HDD? does the size of the partition will be an unallocated memory or it will be added to the extended partition ? same question also for logical partitons.

Yes you can delete the primary partition and it will become unallocated space.

Yes you can delete the logical partitions and they will become unallocated space. Before you can delete the logical partitions you must delete the logical drives within the logical partitions.

> 

- if i deleted one of my partitions , and assumed it will turn into unallocated memory , i can use it to make ubuntu partitions , right?


Yes.

> 
- then ,if i created ubuntu partitions from the unallocated memory , will that format my whole HDD?? i read something like changing the partition table will format the HDD.


It will just format the partitions you tell it to.
If you use the option for a new partition table it will erase the entire disk.

> 

- instead of making a swap partition , can i skip that in the installation and create a swap file later? in fact i want just format a primary partition for root , and skip making either swap or home partitions.


Yes, but it is easier to do it now.

> 
- can i assign a FAT32 drive as my home folder without formatting it ?


I don't know, I have never heard of anyone using a FAT32 partition as /home.  If it is possible I would not recommend it.


Hope this helps.

---

### Post by sanderd17 on 2011-05-30
> **evilheart said:**
> 
- can i assign a FAT32 drive as my home folder without formatting it ?


Yes, you can, but it's not advisable. FAT32 is not good in storing things like user rights and time stamps. So you'll almost surely end with weird problems.

Just to be sure: you want Ubuntu to be your only OS? Or not?

If you use the install wizard, you can simply choose to use Ubuntu as your only OS or to install it next to windows, without having to do the partition manually.

---

### Post by oldfred on 2011-05-30
Windows files systems FAT or NTFS do not support Linux file permissions and ownership which is part of the reason Linux is more secure than widnows. So no you cannot use FAT for /home. 

But /home only has to have the mostly hidden user settings. You can create  another partition for shared data with windows. I use NTFS as it is a newer better system than FAT and Ubuntu's NTFS driver works. I still would not directly write into a windows system partition with anything other than windows though (reading is fine).

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by evilheart on 2011-05-30
thanks guys for you helpful reply!!!!

---

