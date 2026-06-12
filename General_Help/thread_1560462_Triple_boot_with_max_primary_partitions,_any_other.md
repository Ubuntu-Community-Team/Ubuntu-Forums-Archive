---
title: "Triple boot with max primary partitions, any other way to do this?"
date: 2010-08-24
forum: General Help
---

### Post by cAlpha on 2010-08-24
I've currently got the max number of primary partitions (4), one of which is an extended partitions comprised of four logical partitions.  I'm trying to install Windows 7 on a machine which is currently running Vista and Ubuntu.

My drive is currently laid out like this:

```
   Device Boot  System
Disk Device       Size
Dell Utility      70MB
Recovery          10GB 
Vista Boot        27GB
[unallocated]     24GB
Extended Partition   
  File Share      6GB 
  Ubuntu          7GB
  Swap            350MB

```



Ideally, I'd install Windows 7 in the 24GB [unallocated] partition, but can't because I already have four primary partitions.  

Is there a way either to:
(1)  Incorporate the unallocated 24GB into the Vista partition as a logical drive?
(2)  Somehow roll the unallocated 24GB into the extended partition WITHOUT a first wiping the current contents of the extended partition?

---

### Post by oldfred on 2010-08-25
If the 24GB is next to the extended you can move the extended to include it and create another partition.

Windows will let you install a second copy of windows in an extended partition, but its boot is moved to the windows install in the primary partition. If you ever delete Vista, you will not be able to boot Win7.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by PRC09 on 2010-08-25
Not sure on the partitioning but the 24gb might be a bit tight as win 7 minimum requirements is 16gb for 32bit and 24gb for 64bit......

---

### Post by cAlpha on 2010-08-25
> **oldfred said:**
> If the 24GB is next to the extended you can move the extended to include it and create another partition.

It is adjacent to the extended partition but just now attempting to resize/move the extended to incorporate the 24GB partition failed--the option to move/resize the WHOLE extended partition was greyed out and the move/resize option for each of the logical drives considered only those adjacent to it WITHIN the extended partition.

> **oldfred said:**
> 
Windows will let you install a second copy of windows in an extended partition, but its boot is moved to the windows install in the primary partition. If you ever delete Vista, you will not be able to boot Win7.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I'm mostly fine with that.  Worst case, I can always reinstall Win7 should I ever need to delete Vista.  

Given not being able to move/resize to incorporate the unallocated portion thus far, does anyone have any other ideas for ways to avoid having to wipe out my Ubuntu partition?


And a subsequent Q:  assuming I WILL have to wipe the extended partition to make use of the extra 24GB, would there be a preferable way to set up the triple-boot than to leave Vista on its current partition, create an extended partition and then create two (at least) logical partitions within it for each of Ubuntu and Win7?

---

### Post by plucky on 2010-08-25
> It is adjacent to the extended partition but just now attempting to resize/move the extended to incorporate the 24GB partition failed--the option to move/resize the WHOLE extended partition was greyed out and the move/resize option for each of the logical drives considered only those adjacent to it WITHIN the extended partition.


All the partitions within the extended partition has to be un-mounted and you have to do this from the Live CD or a Gparted Live CD.

The Live CDs will always mount the swap partition.

Once all the partitions are un-mounted,the resize/create button will no longer be greyed out.

You can then extend the extended partition wrapper to include the un-allocated space.

Good Luck

---

