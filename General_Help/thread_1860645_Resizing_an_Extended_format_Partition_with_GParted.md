---
title: "Resizing an Extended format Partition with GParted live"
date: 2011-10-15
forum: General Help
---

### Post by alphaamanitin on 2011-10-15
Hey guys,

Trying to help a friend get his dual boot on a larger HD.  HAve successfully cloned to from 80 gb to 320 gb hard drive.  Drive boots into Windows XP and Ubuntu 10.04.  Sorry, I will simply have to describe the HD partitioning.  


sda1: 59 GB Windows XP on left side of HD
sda3: 223 gb space in extended format with 123 gb unallo space on left side of partition
sda5: 100 gb ubuntu install inside sda3 on right side of sda3
swat: 2 gb at end of sda3
4 mb unallo space
sdaX: 2gb some lenovo partition at end of HD

Sorry, I cannot give more sda details, I just remember the ones I payed the most attention to.  Anyway, trying resize SDA3 down to just the SDA5 and swap.  I get 'cannot have overlapping partitions" error.  Goal is to shrink down sda3 to just the swap+sda5 size and expand his full to bursting XP partition.  I don't get why it won't let me shrink sda3.  Any thoughts?

Thanks,

AlphaA

---

### Post by plucky on 2011-10-15
> Sorry, I cannot give more sda details, I just remember the ones I payed the most attention to. Anyway, trying resize SDA3 down to just the SDA5 and swap. I get 'cannot have overlapping partitions" error. Goal is to shrink down sda3 to just the swap+sda5 size and expand his full to bursting XP partition. I don't get why it won't let me shrink sda3. Any thoughts?


If the swap partition is inside the extended partition you won't be able to do anything with the extended partition until you turn swap off.

Run Gparted off the Live CD and turn swap off,you should then be able to manipulate the partitions.

If not post a screenshot of the Gparted window.

Good Luck

---

### Post by alphaamanitin on 2011-10-15
> **plucky said:**
> If the swap partition is inside the extended partition you won't be able to do anything with the extended partition until you turn swap off.

Run Gparted off the Live CD and turn swap off,you should then be able to manipulate the partitions.

If not post a screenshot of the Gparted window.

Good Luck


THANKS!  The swap is most definitely inside the extended, I remember the layout, just not the partition numbers.  My friend is a colleague who will be flying back to Finland today, (Im in USA) and I have been working hard to get him a new, larger HD before he leaves.  Thanks a lot.

AlphaA

---

