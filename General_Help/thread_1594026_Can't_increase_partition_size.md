---
title: "Can't increase partition size"
date: 2010-10-11
forum: General Help
---

### Post by JohnElway on 2010-10-11
I have 4 primary partitions on my hard drive. One of these partitions has been divided into 3 logical partitions with some free space left over. The order is this: "swap", "/", "/home", and about 80GB of unallocated space. I want to incorporate that unallocated space into the home partition. I tried this by booting a live CD and starting GParted but it didn't give me the option to increase the size of my home partition or the primary partition as a whole. The only thing it would let me do is decrease the size of my home partition. 

Can anyone help me with this?

---

### Post by oldfred on 2010-10-12
It depends on where it is. You often have to resize the extended partition first as it is just a container for the logical partitions, then you can expand the logical partition in the extended.

But if the space is not adjacent to the /home where you want to add it, you may have to move everything else. I do not like moving partitions left as it is slightly higher risk as all data has to be copied & verified (and it is slow). Of course all partition changes have some risk, so you must have good backups.

If not near /home you can just make it a /data partition and mount that into /home. All data does not have to be in one partition. 

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I have all data in a data partition and only the hidden files & folders that are user settings in /home.

---

### Post by JohnElway on 2010-10-12
I figured that I needed to resize the extended partition first but couldn't figure out why GParted wasn't letting me do this. For some reason, even though my root and home partitions were unmounted, the swap partition was still mounted even when I was on the live CD (when I first tried this I just assumed they'd all be unmounted). By right-clicking it and selecting "Swapoff", I was able to resize the extended partition and then the home partition.

Thanks for the suggestions!

---

