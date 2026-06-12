---
title: "Shrink Raid5"
date: 2012-02-11
forum: General Help
---

### Post by ptmuldoon on 2012-02-11
I believe it can be done, but I'm sure of the exact commands and afraid of screwing it up and losing any data.

I have 5 x 1TB drives setup right now in a Raid5 array.  Thus, that give me about 4TB of disk space.

Now, I'm only using about 1.5TB of storage on the raid, and would like to shrink it down to 4 drives, leaving me about 3TB of space.

So I have enough file space to shrink it, just unsure of the proper steps.

Can anyone give some pointers?  FYI.  I'm doing this on Ubuntu Server edition, thus its all command line, with no GUI on the machine.

Thanks

---

### Post by dcstar on 2012-02-12
> **ptmuldoon said:**
> I believe it can be done, but I'm sure of the exact commands and afraid of screwing it up and losing any data.

I have 5 x 1TB drives setup right now in a Raid5 array.  Thus, that give me about 4TB of disk space.

Now, I'm only using about 1.5TB of storage on the raid, and would like to shrink it down to 4 drives, leaving me about 3TB of space.

So I have enough file space to shrink it, just unsure of the proper steps.

Can anyone give some pointers?  FYI.  I'm doing this on Ubuntu Server edition, thus its all command line, with no GUI on the machine.

Thanks

AFAIK you cannot "shrink" a RAID-5 array to reduce the quantity of disks, you will have to back up all the data and create a fresh array using the new quantity of disks.

---

### Post by ptmuldoon on 2012-02-12
But I've been reading that it should be possible.  I came across this article here:

[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)

And also this one here on the forums.  

[http://ubuntuforums.org/showthread.php?t=1794121&highlight=mdadm+reduce](http://ubuntuforums.org/showthread.php?t=1794121&highlight=mdadm+reduce)

---

