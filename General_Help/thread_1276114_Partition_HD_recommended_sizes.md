---
title: "Partition HD recommended sizes?"
date: 2009-09-26
forum: General Help
---

### Post by iiinycboi on 2009-09-26
Hello everyone, I am new to the forum and i am new to linux. I just bought an ACER Timeline and i would like to use linux for the first time. 

I am trying to dual boot XP and Ubuntu. I will be doing a fresh install of windows XP but i have a question on how big the partitions i should be making. (I have a 250GB HD)

Should i make 40gb for xp, 40gb for ubuntu and the remaining 170gb for storage and installing programs?

or

Should i just chop the 250gv in half and make 125gb for linux and 125gb for windows.

I will be using linux mainly, but i want to keep xp just in case i need to use xp for certain programs for school that only support windows. 

Thank You!

Also, i read that i should leave room for /root /home and /swap... What are all these? Are these automatic when i install ubuntu or i would need to make 6 partitions on my harddrive!

---

### Post by louieb on 2009-09-26
my vote
> Should i make 40gb for xp, 40gb for ubuntu and the remaining 170gb for storage

I like my data separate from  the  OS.  Have found at least for me 20GB is plenty for Ubuntu.  But I have my data on another partition.

---

### Post by StuartN on 2009-09-26
> **iiinycboi said:**
> Should i just chop the 250gv in half and make 125gb for linux and 125gb for windows.

Most of your disk should go to data, shared between the OSs. You can read EXT filesystems in Windows, and any filesystem in Linux.

Linux needs 4 GB [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) and Windows 16 GB [http://windows.microsoft.com/en-US/windows7/products/system-requirements](http://windows.microsoft.com/en-US/windows7/products/system-requirements) but you should probably give them 50-100% extra if it is spare.

---

### Post by bodhi.zazen on 2009-09-26
Understand it is not critical as you can change later.

Personally I make my root / partition 10 Gb for Linux. 

Windows it will depend on how much software you need to install as mos tof it wants to go onto C:/ , 20 Gb is typically sufficient.

---

### Post by oldfred on 2009-09-26
Basic install is / or root and swap. With large amounts of memory swap is not used unless you load large applications or want to hibernate. Then swap needs to be at least as large as your memory. Old rule when memory was less than 1GB was swap 2x memory.
Many suggest a separate /home for your data and configuration settings of software as it makes it easy to do a full upgrade by replacing and not losing configurations.
Next is having a /data for all your data, then /home does not have to be as large as it is primarily configuration settings and some small amounts of data. If primarily linux the data partition can be ext3 or ext4, but if you want to share data with windows data can be ntfs or still another partition that is ntfs just for shared data.

---

### Post by Bigneil on 2009-09-26
i dual boot too and use 40 ubuntu and 40 xp and use the rest as a storage volume that is in ntfs

---

