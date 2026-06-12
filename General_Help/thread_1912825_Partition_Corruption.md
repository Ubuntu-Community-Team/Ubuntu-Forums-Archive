---
title: "Partition Corruption"
date: 2012-01-21
forum: General Help
---

### Post by Chudz on 2012-01-21
Setup:
 I did a fresh install when I went to 11.10, and decided I would encrypt my home directory since I've never tried it before. /home is mounted on its own disk, which I'll call disk2, and the system, including the swap partition, is on disk1.   
 

 Issue:
 The /home partition has become corrupted twice during the past month and a half. So I'm leaning toward the drive starting to fail. However, the swap partition, on a separate drive, has also become unusable each time as well. The partition shows in Gparted, but it's no longer recognized as swap.   
 

 Recovery:
 So far I've been able to recover /home each time by using a live cd and doing a file system check. As far as swap goes, I've had to blow away the partition each time, create a new one, and then edit fstab. Along with that, my data is backed up just in case.
 

 Question:
 Would a corrupted /home partition also tank a swap partition on another disk? If that's the case, then I'll start looking around for a replacement drive. And if that's not the case, then I'm open to suggestions.

---

### Post by dino99 on 2012-01-21
your logs might help a lot. Maybe you can force a fsck on the partition(s) if you boot on a livecd.

---

### Post by 2F4U on 2012-01-21
If this is one drive, bad sectors may show up everywhere. As far as I know, the drive keeps a list of bad sectors, so if you create a new partition, those sectors are excluded. But if new bad sectors show up, any partition may get corrupted.
Now I don't trust encryption technology much so my guess would be if you get the same problems if the partitions are not encrypted.

---

### Post by Chudz on 2012-01-21
Thanks for the replies. 

I'm not familiar with deciphering the log files, but this sounds like a good time to learn more. So I'll look into those and post if I have any questions. In the meantime, hopefully hard drive prices will get closer to where they were.

And for future rebuilds, maybe I'll keep the home drive unencrypted, and use Trucrypt for the stuff I really want encrypted.

---

