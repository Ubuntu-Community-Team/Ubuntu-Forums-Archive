---
title: "Extended Partition Editing"
date: 2010-06-07
forum: General Help
---

### Post by crazyamerican on 2010-06-07
Sys Specs:
60GB HD
1.6Ghz Intel Celeron
1.5GB RAM

I am Using the LiveCD and Gparted for this.

Here's the deal: I have my HD partitioned with one Extended Partition containing two Logical partitions (My Filesystem and my swap) and a FAT32 partition used for backup. Both are fairly equal in size.

I just bought a 500GB external HD, so my backup partition is no longer needed. I would like to:
1) Delete the Backup partition 
2) Grow the Extended Partition to cover all available space
3) Move swap logical partition to the far side
4) Grow Filesystem logical partition to cover remaining space

Everything went well until I tried to grow my filesystem logical partition. It would not let me grow it.

Is this operation possible? Am I doing something wrong? I am quickly running out of space on my comp. This operation needs to be performed ASAP.

---

### Post by dino99 on 2010-06-07
boot with partedmagic and validate each resizing step by step, resize the Extended first as others are embedded.

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by lavinog on 2010-06-07
You should be able to do everything with gparted.
Does the partition have a lock icon next to it?
Are any of the partitions mounted?

---

### Post by indytim on 2010-06-07
Boot to your LiveCD and run GParted from there.  Should be able to do everything in that environment.

-IndyTim  / DataMan

---

### Post by oldfred on 2010-06-07
Even the liveCD mounts the swap partition to speed things up. If swap is in the extended partition the entire extended is seen as mounted.

right Click on the swap partition and swapoff.

If you delete the swap and create a new one you will have to manually edit the fstab file with the new UUID. Moving may or may not change UUID so you will have to check it. To see UUIDs:

sudo blkid

---

