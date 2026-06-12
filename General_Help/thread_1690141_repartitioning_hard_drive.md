---
title: "repartitioning hard drive"
date: 2011-02-17
forum: General Help
---

### Post by mattman85 on 2011-02-17
I initially was dual booting Windows 7 and Ubuntu. I ditched 7 completely, and am pure Ubuntu. However, I am left with some partition space, and want to rework it. I have attached a screenshot of what Disk Utility shows..

I have a 7.3GB partition free at the "beginning" of the drive. This was a recovery partition which was on my laptop by default thanks to Gateway.. Then I have an extended partition totaling 91GB, which contains my Ubuntu ext4 partition and its swap space. Whats not labeled at the end is my 25 or so GB ntfs partition which just houses files that I could access from either Windows or Ubuntu, which I used fsarchiver to compress onto an external drive.

My idea is to take SystemRescueCD 2.0.1 and use fsarchiver to compress Ubuntu onto an external drive, then format the hard drive, then using fsarchiver, restore Ubuntu onto the "new" partition.

My questions (I know, get to it already, right?!) are, will I have to recreate /etc/fstab? Ubuntu currently sits on /dev/sda5, and the partition will no longer be sda5. Also, should I create a new swap space partition, or also compress that too?

---

### Post by psusi on 2011-02-17
You can just boot the livecd and fire up gparted and expand the existing partition.  Actually since the free space is in the front, I think you have to move the partition to the left first, then expand it to the right.

---

### Post by mattman85 on 2011-02-17
Can I do that, even if the partition space that Ubuntu is in is an extended partition? Don't I need a logical partition (which is what type of partition that the free space resides on)?

---

### Post by plucky on 2011-02-18
> **mattman85 said:**
> Can I do that, even if the partition space that Ubuntu is in is an extended partition? Don't I need a logical partition (which is what type of partition that the free space resides on)?

The 7.3Gb partition is a primary partition.

Back up your data.

Then use Gparted on the Live CD

1) Delete 7.3Gb partition
2) Turn swap off
3) Move the start of the extended partition into the unallocated space.
4) Move the start of the Ubuntu partition to the left.
5) Resize the Ubuntu partition to the right.

Step 2 is necessary as all partitions have to be un-mounted.
Step 4 could take a long time as it has to move all your data.

You can only resize the rear of a partition,but you can move the start of a partition.

Good Luck

---

### Post by mattman85 on 2011-02-18
Thanks for the step-by-step. I'll try it once I'm home from work tonight.

I really did mean primary partition. I knew what I wanted to say :-D Just didn't come out that way..

---

