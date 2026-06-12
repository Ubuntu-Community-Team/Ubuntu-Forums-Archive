---
title: "Degraded RAID 5 with LVM"
date: 2010-08-11
forum: General Help
---

### Post by ee42426 on 2010-08-11
Hello,

I have a four-drive RAID5 with an LVM volume group on it. That is to say, I had it. My machine stopped booting properly, and mdadm --detail /dev/md0 said that this array had two faulty disks and was thus down permanently. I believed it about one of the disks - the BIOS didn't detect it, it was cool when the others were warm, and it made a funny noise when I held it up to my ear and shook it. But the other three seemed okay. They were detected by the BIOS and fdisk -l showed a single large partition, like I expected.

Question 1: Is this a good way of determining if the disk is OK?  Any other ways, without overwriting any data?

Since mdadm wasn't going to solve my problem without a shove, I followed the advice on this post: [http://www.issociate.de/board/post/443210/mdadm_create_to_existing_raid5.html](http://www.issociate.de/board/post/443210/mdadm_create_to_existing_raid5.html) and ran ```
mdadm --create /dev/md0 --level=5 --raid-devices=4 missing /dev/sdb1 /dev/sdc1 /dev/sdd1
```It told me that it looks like these drives are already part of an array, are you sure? And I said yes. After that, the mdadm --detail says that the array is up and in degraded mode (like I wanted). At this point, I ran a vgscan, and it found my volume group. lvmdisplay showed both of my physical volumes.

Question 2: Is this sufficient to show that I had the right ordering on my devices? Does this tell me that my array is, at some level, okay?

At this point, I tried 'mount /dev/my_vg/home_lv /mnt/md' (md is an empty directory). Mount tells me to specify the filesystem type. I think I made it ext3, but I can't quite remember.

Question 3: Is there a way to tell the filesystem type by looking at the logical volume somehow?

Finally, I tried to mount it ext3. There is a complaint about the superblock. I run 'fsck /dev/my_vg/home_lv', and it tells me "The superblock could not be read or does not describe a correct ext2 filesystem".

Question 4: Where do I go from here? My new hard drive has come, which I intended to use a small part of as the new fourth disk in the array. However, I notice that it's big enough to hold the entire old array. Is it a good idea to dd the current /dev/my_vg/home_lv, or even the current /dev/md0, to this new disk? It seems like I would want to be sure the raid was created correctly first. Also, this may take a while, and my worry is that another disk may suffer a mechanical failure in the meantime.

A little more information: /dev/sda was the failed drive. I put in the new drive, which now shows as /dev/sda. /dev/sdb1, /dev/sdc1, and /dev/sdd1 are the partitions that comprise the array (they take up the entirety of their disks). The root filesystem is on /dev/sde.

Thanks!

---

