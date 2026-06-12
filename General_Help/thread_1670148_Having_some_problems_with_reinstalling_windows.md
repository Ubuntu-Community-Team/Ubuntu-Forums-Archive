---
title: "Having some problems with reinstalling windows"
date: 2011-01-18
forum: General Help
---

### Post by rbailey83 on 2011-01-18
I followed the steps i was given to re install windows but when i get to the partition screen i cannot select a partition to delete, it tells me that windows cannot be installed because the partition needs to be NTFS. How do i re format this drive to NTFS so that i can remove ubuntu and put vista back on?

Thanks

---

### Post by ajgreeny on 2011-01-18
You should probably use the Ubuntu live CD/USB and use gparted to delete the partition where you want Windows installed, then format the space to NTFS and add a boot flag to the partition.

Now you should be able to pick that partition in the windows installer and carry on without problem.  When you have installed Windows you will have to restore grub to the MBR.  Come back again if you need to know how to do that, or look at [Grub 2 Basics.]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by coffeecat on 2011-01-18
> **rbailey83 said:**
> How do i re format this drive to NTFS so that i can remove ubuntu and put vista back on?

Do you want to remove Ubuntu completely and just have Vista alone? If so, boot up with a live Ubuntu CD and open System > Administration > Gparted. Right-click on the swap partition and choose 'swapoff'. You should now be able to delete all the partitions leaving the whole drive unallocated. Remember to click on the 'Apply' button (green tick) otherwise nothing is actually done.

With an entirely unallocated drive the Vista installer should be able to set up NTFS partitions for you. If it doesn't (it will), simply use Gparted on the live Ubuntu CD to make whatever NTFS partitions you need.

---

