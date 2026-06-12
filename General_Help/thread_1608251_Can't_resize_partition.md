---
title: "Can't resize partition"
date: 2010-10-28
forum: General Help
---

### Post by sofasurfer on 2010-10-28
I never had trouble with gparted before. But now I do.
When I load the disk I can view my backup drive properly but when I try to view my working drive it shows it as being empty. I also noticed that I had a 1 mg unallocated partition at the beginning followed by my ubuntu partition.

I then ran gparted in terminal and it did show the partition as having my system on it but I am not able to perform any tasks. No moving or resizing.

Any obvious reason for this?

---

### Post by RJ12 on 2010-10-28
If you are trying to resize / move the partition you are currently using, it won't work. The partition is in use if you are using it. What you need to do is use a Live CD / Live USB with either Ubuntu (and run GParted from their) or GParted on it.:)


I hope I understand you right, and I am answering correctly!

---

### Post by GoldenSun on 2010-10-28
you could also try fdisk if gparted isn't cooperating.

---

### Post by crackpotfox on 2010-10-28
ok, this is an easy one, (not to be condescending or anything ;)) well, boot into your trusty live cd of ubuntu, NEVER THROW IT AWAY, it is always useful... then, run the command 

sudo gparted

in the live cd terminal

next, go to your linux swap and rightclick and click swapoff

Problem Solved!

---

### Post by sofasurfer on 2010-10-28
Sounds like good answers to me. I hadn't thought of the live cd. Thanks.
EXCEPT...What are you talking about, "go to your linux swap and rightclick and click swapoff".
Whats that for???

---

### Post by Mark Phelps on 2010-10-28
When you boot into an Ubuntu LiveCD, it needs swap space.  So, if it finds a linux-swap partition already present on a local hard drive, it mounts it and uses it.

Ubuntu will run without swap, just not as fast.

So, to work on the partitions using the Ubuntu LiveCD, you must first umount the used swap space.  That's what the directions were about.

A more foolproof method of doing the same is to download and burn a GParted LiveCD from distrowatch.com, burn it, and boot from it.  That does NOT mount anything by default, so you don't have to deal with unmounting partitions.

---

### Post by sofasurfer on 2010-10-28
I understand now. Thanks. But as for gparted...I have the disk and that is why I started this thread. Gparted does not seem to be working. It shows my partition as empty. That is why I am going to try the live cd.

---

### Post by sofasurfer on 2010-10-28
Ok. Live cd, turn off swap, it worked. I resized my partition.
I still did not have the ability to move my partition to the left where there is an unallocation, 1 mg space.
Any thoughts on that?

---

### Post by Quackers on 2010-10-28
That seems to be a regular occurrence nowadays. I seem to remember it's something to do with ensuring cylinder boundaries between partitions or that partitions end on cylinder boundaries (but I may have dreamed that) :-)

---

### Post by srs5694 on 2010-10-28
> **Quackers said:**
> That seems to be a regular occurrence nowadays. I seem to remember it's something to do with ensuring cylinder boundaries between partitions or that partitions end on cylinder boundaries (but I may have dreamed that) :-)

The ~1 MiB of free space is because most partitioning software today now aligns the starts of partitions on 1 MiB boundaries in order to improve performance on certain types of RAID arrays and on the new Advanced Format disks. (See [this article I wrote](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) for details, particularly with respect to Advanced Format disks.) This alignment policy supercedes the older cylinder alignment practice, which would usually put the start of the first partition at sector 63, although that varied from disk to disk and sometimes even varied with the disk controller or BIOS. Some partitioning tools enable you to change the alignment policy and therefore create partitions that start earlier than 1 MiB; however, as a general rule it's probably best not to do this unless you know what you're doing, simply because you might have an Advanced Format disk and not realize it. (Check the graphs in the article to which I linked.)

As to the original problem, there are several possible causes. One is described on [this Web page](http://www.rodsbooks.com/missing-parts/) of mine; however, AFAIK all versions of libparted (upon which GParted, the Ubuntu partitioner, and several other tools are based) suffer from the same problem, so I suspect there's another cause in sofasurfer's case. Another common cause of this symptom, but one with which I'm less familiar, is leftover RAID data from a previous use of the disk in a RAID array. IIRC, this source of the problem can usually be overcome by uninstalling the mdadm package (assuming you're not currently using RAID on the affected system). Yet another cause of these symptoms is leftover GUID Partition Table (GPT) data; if a GPT disk is re-used as a Master Boot Record (MBR) disk without first wiping the GPT data, GParted gets confused. I don't know if some versions of libparted are more susceptible to confusion on this score than are others; however, if this is the cause, it should be corrected, as I described in [this post](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34) in another thread.

---

### Post by Quackers on 2010-10-28
That's what I meant to say, honest :-)
A full and proper explanation is much appreciated.

---

### Post by sofasurfer on 2010-10-28
Thank you all. 
This case is closed.

---

