---
title: "Partition Scheme (Ubuntu/LFS/home etc). Recommendation Please?"
date: 2010-04-10
forum: General Help
---

### Post by UbuNoob001 on 2010-04-10
Hi There All! Noob here so be gentle! 
   Currently, I have the following system: 

Dell Insp 1545 160GB HD /3GB RAM
OS: Vista
Partitions: 1. Dell Utility (.5GB) 
            2. Vista        (150ish GB)

So I would like to return to Ubuntu.

I would like to partition such that I can also experiment with LFS (Linux From Scratch) in addition to Ubuntu and Vista.  Also I wouldn't mind having a /home partition. 
   
Question 1: How would it be feasible to have 1. Ubuntu 2. Vista 3. LFS 4. /home and 5. Swap (home and swap shared by Ubuntu and LFS partitions (in case I move from LFS to something else)). Maybe using extended or logical partitions? Any suggestions would be appreciated. 

Questions 2: What is on the Dell Utility Partition? [HTML][/HTML]

---

### Post by srs5694 on 2010-04-10
The Master Boot Record (MBR) partitioning scheme supports three types of partitions:


[list]
[*]Primary partitions are limited in number to 4. They're defined by data structures in the first sector of the disk. Windows must boot from a primary partition, but Linux is not so limited. Linux numbers these from 1-4.
[*]Extended partitions are a special type of primary partition. Extended partitions serve as placeholders for logical partitions. Normally only one extended partition may exist on the disk. If you have an extended partition, you can have at most three regular primary partitions.
[*]Logical partitions reside within a single extended partition, so they must be contiguous (or be separated only by unpartitioned space); primary partitions can't exist between logical partitions. You can have an arbitrary number of logical partitions. They're numbered from 5 up, and are defined by data structures inside the extended partition.
[/list]


Thus, basically, you'll need to resize your Vista partition (or delete it and re-install Windows), create new partitions for Linux, and install Linux in the new partitions. Your new partitions can all be logical partitions, if you like, except of course for an extended partition to hold them. The extended/logical partitions can reside before both your primaries, after both your primaries, or between your two primaries, as is convenient. The consensus is that it's safest to resize Vista using Windows' tools.

---

### Post by UbuNoob001 on 2010-04-10
> **srs5694 said:**
> ...Thus, basically, you'll need to resize your Vista partition (or delete it and re-install Windows), create new partitions for Linux, and install Linux in the new partitions. Your new partitions can all be logical partitions, if you like, except of course for an extended partition to hold them. The extended/logical partitions can reside before both your primaries, after both your primaries, or between your two primaries, as is convenient. The consensus is that it's safest to resize Vista using Windows' tools.

Srs. Thanks! So, resizing my Vista partition shouldn't be a problem..thereby making free space. From there, I can create a new extended partition containing several logical partitions? 
Example: 
Primary 1. Dell Utility
Primary 2. Vista
Primary 3 (Extended)
           Log1. Ubuntu
           Log2. LFS
           Log3. Swap
           Log4. /Home

How does this seem?

---

### Post by srs5694 on 2010-04-11
> **UbuNoob001 said:**
> How does this seem?

That looks good to me; however, I might add another partition for data sharing between Linux and Windows. That way, you won't need to mount the sensitive Windows boot partition from Linux if you want to access files that were stored under Windows. (Either files you want to use regularly from both OSes, such as MP3s, or files that you download in Windows for use in Linux.) For best performance, put this filesystem in-between the Windows and Linux filesystems. (Putting swap space between the Linux installation and /home filesystems, as you did, may also slightly increase performance if the swap space sees much use.)

Also, Linux uses case-sensitive filenames, so it's the /home partition, not /Home. Chances are you'd get that right because the installer has some ready-made partition types that you select from a drop-down menu, but it's best if you understand this from the start.

---

