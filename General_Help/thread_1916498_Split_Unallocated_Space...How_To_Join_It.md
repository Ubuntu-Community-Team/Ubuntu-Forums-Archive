---
title: "Split Unallocated Space...How To Join It?"
date: 2012-01-28
forum: General Help
---

### Post by ryanmichaelmcclure on 2012-01-28
As a reference, here's a screenshot of my current partitioning:

[IMG]http://i41.tinypic.com/ev6xow.png[/IMG]

As you see, I have two bits of unallocated space. I tried under the LiveCD GParted to join the two spaces and the Ubuntu partition. However, this didn't work, yielding an error during the MOVING FILES TO LEFT stage.

So...here's my question: Can I join the two unallocated spaces, move them to the RIGHT of the Ubuntu partition, and then join them? My main goal is to have the Grub partiton, the Ubuntu partition, and the Swap partition in that order. 

Also, totally unrelated question: Is the size of my Swap partition acceptable? I have 3 GB of RAM.

Thanks all!!!

EDIT: I do remember why the error occurred when moving to the left. It had to do with bad sectors. I tried to run a SMART self-test, but it failed.

---

### Post by Double.J on 2012-01-28
Hi there!

You're quite right - the correct way to do this is to move the linux partition to the left, thus creating conjoined free space on the right (end) of the disk. You can't more free spae however as it *doesn't exit* in that you could move a ballon across a room, but you couldn't move all of the air from one ide of the balloon to another.

The good thing is that you know why you are having problems moving the partition. I'd recommend grabbing another HDD, copying your partitions from this drive to that (use clonezilla if you don't know how to do this) CHECK that copying your partitions hasn't caused any loss of data, then create one big ext4 partition across the drive you are setting up (not the one you copied to) and check the filesystem for errors  - use [this guide]("http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/") if you're not sure how

Once that's all done and any issues have been resolved, it's time to move your partitions back. If you are using MBR I'd be inclined to put your partitions back as logical inside an extended one - at the moment you are using 3 primaries of 4...if you're using gpt, don't worry :)

Hope it helps! as to the other HDD - if you haven't already backed up the data off the drive, think about whether you really want to move your root partition?

All the best!

---

### Post by ajgreeny on 2012-01-28
A few points to make:-

[LIST=1]
[*]Why a separate /boot partition?  It usually makes life more complicated and adds little to the system's ease of use, or anything else.  Also 200MB may be rather small for a grub 2 partition.  500MB is probably better.
[*]Presumably you have had many more partitions as your root partition is now sda7.
[*]**Backup** before you do anything to your partitions.  It should not go wrong, but you never know.
[*]You should be able to move the sda7 to the start of the disk, or at least next to the boot partition, if you want to keep that, but first you need to right click and "unmount" the partition.  This will possibly take several hours, so be patient and under no circumstances should you stop this once you have started.
[*]You can then make whatever partition you want in the unallocated space at the end of the disk.
[*]Your swap size is probably fine, though you could resize it slightly if you wish by dragging its left side to the left a bit.  To do that you will need to right click and choose "swapoff".
[/LIST]

---

### Post by ryanmichaelmcclure on 2012-01-28
> **ajgreeny said:**
> A few points to make:-

[LIST=1]
[*]Why a separate /boot partition?  It usually makes life more complicated and adds little to the system's ease of use, or anything else.  Also 200MB may be rather small for a grub 2 partition.  500MB is probably better.
[*]Presumably you have had many more partitions as your root partition is now sda7.
[*]**Backup** before you do anything to your partitions.  It should not go wrong, but you never know.
[*]You should be able to move the sda7 to the start of the disk, or at least next to the boot partition, if you want to keep that, but first you need to right click and "unmount" the partition.  This will possibly take several hours, so be patient and under no circumstances should you stop this once you have started.
[*]You can then make whatever partition you want in the unallocated space at the end of the disk.
[*]Your swap size is probably fine, though you could resize it slightly if you wish by dragging its left side to the left a bit.  To do that you will need to right click and choose "swapoff".
[/LIST]

I have a separate boot partition because I'm planning on having multiple distros on my system. And yes, I used to have mult. systems on my disk. Thanks for uour input :)

---

### Post by oldfred on 2012-01-28
You will need a separate /boot for every system. Or if just a grub only partition you will be ok, but have to manually update the grub menu each time you change something. With grub2 in Ubuntu you can easily run the os-prober and boot other installs and no separate /boot or /grub is required.

Screenshot does not make it clear on where the extended partition is. If moving sda7, you also have to move the extended partition start first. Moves can take a long time and any power outage or issue can cause problems, so have good backups.

---

### Post by ryanmichaelmcclure on 2012-01-28
UPDATE: After doing some deleting of unneeded partitions and other things, here is my current partition system:

[IMG]http://i40.tinypic.com/xm6agg.png[/IMG]

Ubuntu is my current install, New is a new partition.

Here's my plan:

Move everything from Ubuntu (total of 62.36 GB) to New (66.60 GB), then delete the Ubuntu partition and join its blank space with New. Moving to the left still didn't work.

How can I go about moving everything to that partition and still have it boot? 

-Ryan

PS: I'm still noobish to Linux, so I want to thank you all for being so understanding :) I was so tired of WIndows' cold grip on me.

---

### Post by oldfred on 2012-01-29
In the last couple of days I have posted in threads where users were copying from one drive to another. Issues on fstab, grub and a few others. Any place that uses UUID, or device like /dev/sda7 will have to be manually updated. It can be done but is not particularly easy.

I normally suggest a clean install. That also in effect does a houseclean of old log files and other cruft. You would have dual boot so you could go back into your install in sda7 if you miss something. But you can copy all of /home which has all your data and users settings. You can export a list of installed apps and reinstall. If slow Internet and installing exactly the same version only you could copy the debs from the old install to the new if you have not housecleaned them out.

I also suggest a separate /home and a smaller system partition of 10 to 25GB depending on available hard drive space.

I plan on a clean install if my system totally crashed and my backup plan is to have all the settings & configurations backed up.

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Your sda1 is small compared to the amount of used space in sda7. I think you may quickly have system issues with not enough free space.

---

