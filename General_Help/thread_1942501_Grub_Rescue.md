---
title: "Grub Rescue"
date: 2012-03-17
forum: General Help
---

### Post by Rtlz on 2012-03-17
Hey guys,

I was trying to format my dual boot computer with a windows 7 cd. Unfortunatly, it kept avoiding the cd format menu, entering instead in the dual boot menu. So I had the most wonderful ideia: Let's delete the ubuntu partition and this menu won't show up! Well, the pc didn't found this idea so amazing has I did so now the grub rescue thing doesn't move out of my way. 
As I understood of other threads, I need a Ubuntu installation cd to fix it. Though, I don't want to fix it, I want to format it. Is there a way to format it ignoring this error, or there's no other way, and I'll have to get a Ubuntu cd to fix this, and then format the computer? If so, which steps I'll have to follow?

Thanks for your help!

---

### Post by JC Cheloven on 2012-03-17
As far as I understand from your post (I admit I didn't completely get the idea), you want to format the whole hard disk.

If so, either from the w7 install disk or from a live cd ubuntu disk, it should be pretty simple. In the case of ubuntu live cd, use the program called "gparted".

Perhaps if you explain what your goal is, we could be a bit more helpul (ie, do you want to end up with w7 only, Ub only, dual boot... ?)

---

### Post by Rtlz on 2012-03-17
Yes, my intention is to format the whole hard disk, but this grub rescue error, doesn't allow the w7 install disk to start the regular menu.

---

### Post by swright007 on 2012-03-18
you could always boot from an Ubuntu boot CD... open a terminal and type 

sudo update-grub

when it is done, your grub menu should be fixed.  You should be able to access both operating systems when you reboot without the live cd.

If you would still rather restore your hard drive in a manner that Windows can see, you would need to boot from an Ubuntu live cd.  Open the program 

Disk Utility

then you would need to unmount the hard drive.  delete it's partitions.  Then create a new partition the size of the whole hard drive.  Make sure the partition you create is NTFS. Make sure the partition is formatted (NTFS)   When done, just mount the hard drive.... then shut down.  When you start your computer insert your Windows CD this time.  From this point, Windows will be able to see the drive.

---

