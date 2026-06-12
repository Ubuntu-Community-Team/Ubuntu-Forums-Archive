---
title: "dd command problem"
date: 2011-05-21
forum: General Help
---

### Post by Ganesh Dhawale on 2011-05-21
Hi,

I have 2 IDE HDDs, 80Gb and 160Gb. I am trying to copy active partition from 80G to 160G by using dd command as
```
dd if=/dev/sda1 of=/dev/sdb1
```
To make sure about sizes, sda1 equals 37Gb while sdb1 is 52Gb. But the command fails after some time with output
```
dd: writing to `/dev/sdb1': Input/output error
6177169+0 records in
6177168+0 records out
3162710016 bytes (3.2 GB) copied, 312.115 s, 10.1 MB/s
```
Any idea why it is failing?

---

### Post by dcstar on 2011-05-21
> **Ganesh Dhawale said:**
> Hi,

I have 2 IDE HDDs, 80Gb and 160Gb. I am trying to copy active partition from 80G to 160G by using dd command as
```
dd if=/dev/sda1 of=/dev/sdb1
```
To make sure about sizes, sda1 equals 37Gb while sdb1 is 52Gb. But the command fails after some time with output
```
dd: writing to `/dev/sdb1': Input/output error
6177169+0 records in
6177168+0 records out
3162710016 bytes (3.2 GB) copied, 312.115 s, 10.1 MB/s
```
Any idea why it is failing?

You may have bad blocks on the small drive.

Install and use the **ddrescue** package.

You should also **never** use it on an "active partition", you should boot off a Live CD and use it on **unmounted** partitions only.

---

### Post by Ganesh Dhawale on 2011-05-21
> **dcstar said:**
> You may have bad blocks on the small drive.

Install and use the **ddrescue** package.

You should also **never** use it on an "active partition", you should boot off a Live CD and use it on **unmounted** partitions only.

I forgot to mention, I am not running ubuntu from the active partition to be copied. 

I believe the partitions have no bad sectors. I'll try with the ddrescue, if dd fails again as I am not sure about partitions being unmounted at last attempts.  


Thanks David

---

### Post by prshah on 2011-05-21
> **Ganesh Dhawale said:**
> 
```
dd if=/dev/sda1 of=/dev/sdb1
```

But the command fails after some time with output
```
dd: writing to `/dev/sdb1': Input/output error
6177169+0 records in
6177168+0 records out
3162710016 bytes (3.2 GB) copied, 312.115 s, 10.1 MB/s
```
Any idea why it is failing?

You should use the bs (BlockSize) parameter for better performance, as well as the noerror flag to continue inspite of errors. 

Also, it's a good idea to copy the entire drive and not just the partition; you can then resize the target partition to achieve full size.

It's also a good idea to push the process in the background and get the process number stored in an environment variable to access stats.

Typically```
sudo dd if=/dev/sda of=/dev/sdb bs=64M conv=noerror & pid=$!
```

You can check copying performance by sending a USR1 signal to the running "dd" process```
sudo kill -USR1 $pid
``` This will respond with stats within a couple of seconds, and will not kill your dd process.

You can adjust your bs parameter if the stats don't satisfy you.

Edit: Very important forgot to mention: Please ensure that swap is turned off before starting your dd operation; ```
sudo swapoff -a
``` Even a live session activates swap if it detects a swap partition.

---

### Post by dandnsmith on 2011-05-21
> Also, it's a good idea to copy the entire drive and not just the partition; you can then resize the target partition to achieve full size.

Not the best idea, unless the source and receiving HDDs are exactly the same configuration. I once spent a couple of days recovering from doing just that without thinking - the damage was done in the first seconds, so wasn't entirely easy to fix.

---

### Post by prshah on 2011-05-21
> **dandnsmith said:**
> Not the best idea, unless the source and receiving HDDs are exactly the same configuration. 

No, both HDDs do NOT need to be the same. The only problems can possibly arise is if one HDD is sub-1TB, and the other a 1TB+ with 4k blocks (which is clearly not the case here). Even in this case, it just means that the new HDD will not work at it's fastest, and nothing else.

The smaller partition created on the new drive can subsequently be safely expanded with Palimpest or GParted.

There is ABSOLUTELY no need to ensure that both drives are the same capacity / type / etc. If you faced problems, it was probably due to some other issue.

---

### Post by Ganesh Dhawale on 2011-05-21
Done.

The good side is, unmounted partitions (source and destination) has worked fine with ```
dd if=/dev/sda1 of=/dev/sdb1
```

But I am facing another problem now. The target partition is not booting well. Halts in between on the logo screen. I am guessing now the target partition may have bad sector. Scan in progress now, if I find one I will simply keep old HDD as primary disk.

Thanks everyone.

Regards, Ganesh

---

### Post by prshah on 2011-05-21
> **Ganesh Dhawale said:**
> The good side is, unmounted partitions (source and destination) has worked fine with ```
dd if=/dev/sda1 of=/dev/sdb1
```

The target partition is not booting well. 

I don't believe you have any bad sectors. Even if you do, fsck will run automatically on the next reboot.

I think it is related to the partition to partition cloning that you have done; as against disk-to-disk cloning. As a matter of interest, how did you setup partition 1 (/dev/sdb1) on the target disk?

---

### Post by dandnsmith on 2011-05-21
> **prshah said:**
> No, both HDDs do NOT need to be the same. The only problems can possibly arise is if one HDD is sub-1TB, and the other a 1TB+ with 4k blocks (which is clearly not the case here). Even in this case, it just means that the new HDD will not work at it's fastest, and nothing else.

The smaller partition created on the new drive can subsequently be safely expanded with Palimpest or GParted.

There is ABSOLUTELY no need to ensure that both drives are the same capacity / type / etc. If you faced problems, it was probably due to some other issue.

The problem is that, specifying the entire disk, you're including the entire 1st block - which includes the partition table and sundry HDD information about HDD organisation. This doesn't matter if you're then going to recover the partition to the original HDD, but can considerably disrupt things for the use of the 2nd HDD - I know, and spent quite a while sorting such a situation out some while back.

---

### Post by gradinaruvasile on 2011-05-21
> **dandnsmith said:**
> The problem is that, specifying the entire disk, you're including the entire 1st block - which includes the partition table and sundry HDD information about HDD organisation. This doesn't matter if you're then going to recover the partition to the original HDD, but can considerably disrupt things for the use of the 2nd HDD - I know, and spent quite a while sorting such a situation out some while back.

But here is clearly about copying only a patition, not the whole device.

to the OP:

Copying a partition is not enough. You have to set it up correctly in grub afterwards. You should reinstall grub on the target drive after a copy like this and rebuild initramfs.

Also, partitions are defined in /etc/fstab by their UUID - make sure you change everything accordingly.

press ctrl-alt-f1 during the boot to actually see the error messages.

---

### Post by prshah on 2011-05-21
> **dandnsmith said:**
> The problem is that, specifying the entire disk, you're including the entire 1st block - which includes the partition table and sundry HDD information about HDD organisation. This doesn't matter if you're then going to recover the partition to the original HDD, but can considerably disrupt things for the use of the 2nd HDD - I know, and spent quite a while sorting such a situation out some while back.

> **gradinaruvasile said:**
> But here is clearly about copying only a patition, not the whole device.

Copying a partition is not enough. You have to set it up correctly in grub afterwards. You should reinstall grub on the target drive after a copy like this and rebuild initramfs.

Also, partitions are defined in /etc/fstab by their UUID - make sure you change everything accordingly.


When you use dd to copy the entire disk, you are including the "first block" (446 bytes for MBR+ 66 bytes for partition table). You are also copying the partitions and swap; the UUIDs are preserved, and you can immediately boot into the new drive, without the need for any "recovery", or reinstallation of GRUB.

To copy only a partition, one must use partition tools such as partimage, or even gparted's copy/paste. However, in this case, you will need to change swap information in the fstab, otherwise you will not be able to use the hibernate feature (since UUIDs have changed). Except for this hibernate problem, there is no other problem, since any swap found, irrelevant of it's UUID will be activated automatically.

As for "knowing through doing" I have moved from a 40GB to 80GB to 160 GB to 250GB to 320GB and currently a 1TB in exactly this manner, without needing any "recovery" or grub install, or anything else (except for expanding the partition to fill unused space everytime).

---

### Post by gradinaruvasile on 2011-05-21
> **prshah said:**
> When you use dd to copy the entire disk, you are including the "first block" (446 bytes for MBR+ 66 bytes for partition table). You are also copying the partitions and swap; the UUIDs are preserved, and you can immediately boot into the new drive, without the need for any "recovery", or reinstallation of GRUB.

To copy only a partition, one must use partition tools such as partimage, or even gparted's copy/paste. However, in this case, you will need to change swap information in the fstab, otherwise you will not be able to use the hibernate feature (since UUIDs have changed). Except for this hibernate problem, there is no other problem, since any swap found, irrelevant of it's UUID will be activated automatically.

As for "knowing through doing" I have moved from a 40GB to 80GB to 160 GB to 250GB to 320GB and currently a 1TB in exactly this manner, without needing any "recovery" or grub install, or anything else (except for expanding the partition to fill unused space everytime).


But this does not change the fact that the OP did 

```

dd if=/dev/sda1 of=/dev/sdb1

```
= copying a partition to another partition and that is the case i was referring to.

BTW swap is not always activated automatically - it happened to me and i had to edit fstab for that.

---

### Post by prshah on 2011-05-22
> **gradinaruvasile said:**
> ```

dd if=/dev/sda1 of=/dev/sdb1

```
= copying a partition to another partition and that is the case i was referring to.

BTW swap is not always activated automatically - it happened to me and i had to edit fstab for that.

I'm getting tired of all the fallacies propounded in this thread. I'll try to clear them just this once, and then I hope to just ignore this thread.

a) All available swap partitions are automatically activated at boot time, whether or not it is defined in the /etc/fstab. Don't believe it? Check the man page on swapon > Calls  to  swapon  normally occur in the system boot scripts making **all**
       swap devices available Only swap-FILE devices will not be activated unless defined in the /etc/fstab. Swap partitions, when detected at boot time, are always activated. If multiple swap partitions are detected, then multiple swap partitions are activated. When you boot off a live CD (which definitely does not have a customised /etc/fstab), it will automatically activate swap partitions it detects.

b) using "dd" to copy just a partition is a bad idea. It may work at times, but it is not always so. In this case, the OP has tried to copy an "active" partition, but the information on whether the partition is active or not is not stored with the partition; it is stored in the partition table, which is not in the area that the OP has copied. Further, using "dd" to copy to a target partition (instead of a target disk) can allow for the copy to overrun other partition information, ie, if the target partition is too small. There is no check to allow or disallow this. To copy a partition, it is better to use partition management tools, rather than "dd". Use "dd" if you like, but a partition management tool is suggested instead.

c) Using "dd" to clone an HDD (any smaller size to any same or bigger size, with sector compatibility) will never be a problem. Since all information is lifted as-is from the old HDD, UUIDs etc remain unchanged. Another advantage is that since "dd" uses a sector-to-sector copying method, it doesn't care what the underlying information is; it can be ntfs, ext2/3/4, swap, whatever. Using "dd" to attempt to clone an ntfs partition will rarely cause corruption in the MFT, hence the utility ntfsclone to clone a NTFS PARTITION. 

d) I'm not suggesting that "dd" cannot be used to clone a partition; I'm just suggesting that it is better if "dd" is used to clone the entire HDD, and partition management tools used to clone partitions. 

e) When upgrading the harddisk, it is much better to use "dd" to clone the entire old HDD to the new HDD, rather than clone individual partitions one at a time.

In summary of it all: swap partitions always get activated automatically; it's better to use "dd" to clone an old HDD to a new HDD ; it's better to use a partition management tool (over "dd") to clone individual partitions.

---

