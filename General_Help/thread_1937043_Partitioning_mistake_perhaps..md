---
title: "Partitioning mistake perhaps."
date: 2012-03-07
forum: General Help
---

### Post by pranjal_dude007 on 2012-03-07
Please help me! 

I'm trying to understand Linux and have ubuntu 11.04 Natty, although sometimes it gets a little impatient I manage to figure out what to do. 

Recently, I realized that I could not access about 100gb of storage due to certain partitioning. I could not place videos or music in those folders. Now I went over to the partitions and tried to unmount or delete that partition. Firstly, I have no idea what the difference is between unmounting and formatting. 

Now, when I switch my computer on, I get this 

Unknown Filesystem 
Grub rescue 

Please help me! I dont wanna lose any files and certainly want to understand linux more.

---

### Post by sikander3786 on 2012-03-07
There can be multiple different things that are causing the problem for you. For letting us take a better look at your partition setup, please boot an Ubuntu Live CD/USB and run and post the output of bootinfoscript as per instructions here:

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by pranjal_dude007 on 2012-03-07
okay downloading bootinfo

---

### Post by Mark Phelps on 2012-03-07
To address the question you posed, mounting makes the contents of a filesystem present on a partition accessible to applications.  Formatting, in contrast, erases the contents of the partition table, effectively removing easy access to the files and directories there.  Formatting does not actually "erase" the contents of the files.

If you merely unmounted a partition, while that might cause problems in accessing files, when you rebooted into Ubuntu, your filesystems would have been automatically remounted -- at least, the part of the filesystem needed to run Ubuntu.

The error message you're getting implies that you formatted the filesystem -- and if that is true, it could be quite difficult to get the files back.

The script you were told to run will tell us a lot more about the current state of your filesystems and partitions.

---

