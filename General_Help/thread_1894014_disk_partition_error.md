---
title: "disk partition error"
date: 2011-12-11
forum: General Help
---

### Post by spulkit on 2011-12-11
i have a very weird problem i guess!!!i have the latest ubuntu installed and while installing i selected to install ubuntu side by side to windows 7 and do dual boot.

My windows that time had only one partition that is c. The ubuntu install made three new primary partitions alongside c of 3.86 gb 3.85 gb and 115.25 gb. Also there is system reserve of 100 mb and recovery of 13 gb. 
Now i wanted to split C and create a another drive so i shrank volume of c by a 100 gb but when i tried to create another drive it gae an error "cannot create a new volume in this unallocated space because disc already contains maximum number of partitions. "
when i deleted all the ubuntu drives i deleted grub bootloader also so couldnt boot windows . as a result i had to reinstall ubuntu again and install windows using recovery and i was back to where i was before. 

Now i have no idea what to do . Please help !!

---

### Post by lechien73 on 2011-12-11
You can only have 4 x primary partitions on the disk - or 3 x primary and 1 x extended partition. The extended partition can contain multiple sub-partitions (or logical partitions).

This link: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) might help you with understanding partitioning on your hard disk :)

---

### Post by dabl on 2011-12-11
> **spulkit said:**
> 

My windows that time had only one partition that is c.

No -- Windows may not have advertised it, but you already had 3 primary partitions before you launched the Ubuntu installer.  And you can only have 4 primary partitions on a hard disk drive.

First, (if you can still boot Windows) you need to use the Windows 7 disk management tool, found under System Administration, to shrink the Win 7 partition, freeing up however much space you want for Ubuntu and its data.  This space will be "unallocated".

Then, you will use GParted (from the Ubuntu Live CD, a Parted Magic Live CD, or wherever you wish) to make a new partition in the unallocated space.  This fourth primary partition will be an "Extended" type, using all the unallocated space.

Once you have made the extended partition, go ahead and make the needed partitions for Ubuntu.  For example, you could make a 15GB partition for the root filesystem, excluding /home, then you could make a 2GB swap partition, and then you could use the rest of the space for a /home partition, for your data.  These partitions will be "Logical" partitions, within the Extended partition. Linux doesn't mind running from logical partitions, but Windows won't.

When these preparations are done, you are ready to go with the Ubuntu installation, choosing the mount points as described above.

---

