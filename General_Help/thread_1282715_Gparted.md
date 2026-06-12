---
title: "Gparted"
date: 2009-10-04
forum: General Help
---

### Post by topdog2009 on 2009-10-04
Need assistance with gparted to make room for Ubuntu

Have the following

Partition      File system      Size    Used    Flag
/dev/sda1       ntfs              169.61    66.97     boot   Note All sizes in GB
unallocated   unalloacted     50.09
/dev/sda3      extended          2.50
  /dev/sda5    ext3                  2.34      2.19
  /dec/sda6    linux=swap      164.70mb 
unallocated   unallocated         7.02mb
/dev/sda2      ntfs                 10.68     9.41

The second ntfs is the windows recovery.
I tried to reduce the ntfs by 50gb to make available for Ubuntu and now have the 50.09gb as unallocated. The second unallocated 7.02mb was presumably done at the Ubuntu install.

I now want to increase the /dev/sda5 (presumably) for Ubuntu but when I try to increase the size it will not allow me to go beyond the existing - at least the way in which I am trying to do it. I know I am doing something I am doing something incorrectly but not sure what.

Incidentally, the Help for Gparted appears to be written for an ealier version because the help does not tie in with the Screens.

Brian

---

### Post by stephana on 2009-10-04
you need to start gparted from LiveCD? Otherwise i think increasing the drive is not possible.

---

### Post by wilee-nilee on 2009-10-04
Gpatrted is a great tool, but will not expand into areas formally mounted with another OS even if the space is empty. When you install Ubuntu the partition GUI gives you a choice of side by side and a slider to adjust accordingly. So in other words you are limited by the original sized partition in moving it side to side or expanding, I suspect though that the ubergeeks have some tricks to bypass this limitation with terminal commands.

---

### Post by ajgreeny on 2009-10-04
Yes, use the ubuntu live CD for the gparted activities, or you will find problems.

Regarding your partition setup, and assuming there is nothing of any importance on sda3, sda5 and sda6, I would delete all of them with gparted, and then you will have one large single unallocated space which includes them and the two current unallocated spaces noted in your list.  This also assumes that the partition layout on disk is in numerical order, with the possible exception of sda2 (ntfs recovery), which may be at the end of the disk.  If that assumption is correct, now install ubuntu into the free space, either as default, or if you prefer using one partition for root (/), another for /home and a third for swap, though make that larger than the current 164Mb; I suggest about 1 - 2 GB.  You can do all this if you choose manual partitioning at that stage of the install.

It would help if you ran gparted from the live CD and posted a screenshot here of the gparted window to show partition layout.

---

### Post by topdog2009 on 2009-10-05
That worked - thanks

---

### Post by mudeye on 2009-10-05
If I may join in the middle of this thread -- I also have too little space allocated to U9.04.  Whenever I try to delete or change the size of a partition I am told "no root file system is defined".  

Q: How to define the root file system?  Thanks in advance.

---

