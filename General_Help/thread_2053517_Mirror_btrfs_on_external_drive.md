---
title: "Mirror btrfs on external drive?"
date: 2012-09-05
forum: General Help
---

### Post by ratcheer on 2012-09-05
Yesterday, I started playing with btrfs for the first time. I created a new 100 GB disk partition and created a btrfs filesystem on it. I have played a little with snapshots and subvolumes. My main idea is to use it as a data repository that I can share among all my Linux installations.

My next idea is to make the filesystem act like a RAID-1 volume. Unfortunately, my PC has a single internal disk drive. However, I do have a 2 TB external USB-3 drive that is almost completely empty of data. The entire external drive is formatted as NTFS.

I know that btrfs can use dissimilar drives in a filesystem. I know performance would not be as good to do so, but for a data sharing use, it shouldn't make that much difference. Would it be really stupid to shrink the NTFS filesystem to carve out another 100 GB or so to add to my btrfs filesystem?

Tim

---

### Post by ratcheer on 2012-09-05
Never mind, I went ahead and did it. It is working great! If there is even a performance hit, I cannot tell it.

Tim

---

### Post by ratcheer on 2012-09-06
One small performance hit is that, after a while of inactivity, the USB drive has to "wake up" to get going again. This takes a couple of seconds. But, when it is running, things seem quite fast.

If I go to the root-level of the btrfs and run "du .", the output is almost instantaneous. The stuff I copied into it is about 33 GB and there are quite a few subdirectories. I attribute this quickness to the b-tree nature of the filesystem. That's just a guess, though.

Tim

---

