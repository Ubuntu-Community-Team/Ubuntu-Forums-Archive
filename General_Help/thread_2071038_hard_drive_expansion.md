---
title: "hard drive expansion"
date: 2012-10-14
forum: General Help
---

### Post by unibroker on 2012-10-14
I just received a lack of storage warning.  The lack of storage warning came with trying to build Jelly Bean (Android) from source.  I am currently dual boot XP/Ubuntu 12.04 (I need to retain XP for access to a Windows based program's database (Wine doesn't work)).   

Can I easily upgrade (replace) the current hard drive keeping in mind the dual boot situation?  It seems the dual boot makes the transfer from one hard drive to another more complex.

Thanks in advance.

---

### Post by conradin on 2012-10-14
Clone to a larger harddrive then expand your partitions to the free space with a livecd.

---

### Post by unibroker on 2012-10-14
> **conradin said:**
> Clone to a larger harddrive then expand your partitions to the free space with a livecd.

Another thing ("Clone") I need to research!

I used gparted when I originally did the dual boot with XP.  I defragmented before gparted but was very conservative in allocating hard drive space to Ubuntu so as not to lose any XP files (even with defragmenting I read that this was a possibility). Any problems using gparted again to recapture more space for Ubuntu?  If not I may go into XP and delete everything but the few resources/data I need that can't be satisfied with Ubuntu.  Then I can recapture a lot of space for Ubuntu.  BTW, my hard drive is 250GB which should be more than enough for my needs.

Thanks for the response.

---

### Post by Bashing-om on 2012-10-14
unibroker; Hi !

I see two options for you.
1. the simplest to gain disk space is housecleaning in ubuntu by deleting old kernels, caches, and old log files.
2. Remember -> Windows tools for window's problems, linux tools for ubuntu situations.[INDENT]  use windows disk management tools to resize windows partitions (defrag first), then use ubuntu's GParted to enlarge the partition into the newly created free space. Depending on how large the partitions are, will take some time to move the data about.
I can foresee moving a partition with boot files requiring re-installing grub, which is not a big deal.
As always, in manipulating partitions, there is the chance of data loss/corruption, backing up important files/data is recommended.
[INDENT]I do hope this helps <==BDQ

[/INDENT][/INDENT]

---

### Post by unibroker on 2012-10-14
> **Bashing-om said:**
> unibroker; Hi !

I see two options for you.
1. the simplest to gain disk space is housecleaning in ubuntu by deleting old kernels, caches, and old log files.
2. Remember -> Windows tools for window's problems, linux tools for ubuntu situations.[INDENT]  use windows disk management tools to resize windows partitions (defrag first), then use ubuntu's GParted to enlarge the partition into the newly created free space. Depending on how large the partitions are, will take some time to move the data about.
I can foresee moving a partition with boot files requiring re-installing grub, which is not a big deal.
As always, in manipulating partitions, there is the chance of data loss/corruption, backing up important files/data is recommended.
[INDENT]I do hope this helps <==BDQ

[/INDENT][/INDENT]

Thanks for the response.  I just fired up gparted to look at the drive statistics.  SDA1 (ntfs) which is where XP is has 170GB of which 35G are being used.  SDA3 (extended) has 54GB of which 0 are being used. SDA5 (ext4) has 52G of which 49G have been used.  For what it's worth SDA6 (linux-swap) has 2G of which 0 are being used.

This is the first time I've looked at this in this way but what I see is a very inefficient setup.  Not only is there likely additional space to be gained from SDA1, it looks like I could use all of SDA3 by resizing SDA5?  That looks to be the safest route without going after space in the Windows partition.  I can hardly wait to be at a point where I can reformat the drive and make it a linux pc.

---

### Post by oldfred on 2012-10-14
The extended partition is just a container for all the logicals. So its total should be the sum of all the logicals you have. You have two logicals 52 & 2 which equals the 54GB so it is correct.

You can shrink the NTFS, but NTFS needs 30% free to work well. So just do not shrink too much. But even with that you have a lot of unused space in your NTFS partition.

Some of us use data partitions and keep / (root) smaller. Others may use separate /home partitions and keep / (root) smaller. But having a smaller / is a bit more efficient.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)

---

### Post by unibroker on 2012-10-14
> **oldfred said:**
> The extended partition is just a container for all the logicals. So its total should be the sum of all the logicals you have. You have two logicals 52 & 2 which equals the 54GB so it is correct.

And all this time I thought I picked up an extra 50GB of storage just for switching to linux!  Should have known the math didn't add up.

> You can shrink the NTFS, but NTFS needs 30% free to work well. So I just need to take the present, used ntfs (35GB) and give it 30% headroom?  It is not going to grow as I'm phasing it out.

Thanks for all of the links.

---

### Post by oldfred on 2012-10-14
If you use it, it will grow, but then you can houseclean to remove most of the growth. AT 20% free it should be functional but not as snappy, but at 10% free it becomes noticeable slower.

---

### Post by unibroker on 2012-10-16
> **Bashing-om said:**
> unibroker; Hi !

I see two options for you.
1. the simplest to gain disk space is housecleaning in ubuntu by deleting old kernels, caches, and old log files.
2. Remember -> Windows tools for window's problems, linux tools for ubuntu situations.[INDENT]  use windows disk management tools to resize windows partitions (defrag first), then use ubuntu's GParted to enlarge the partition into the newly created free space. Depending on how large the partitions are, will take some time to move the data about.
I can foresee moving a partition with boot files requiring re-installing grub, which is not a big deal.
As always, in manipulating partitions, there is the chance of data loss/corruption, backing up important files/data is recommended.
[INDENT]I do hope this helps <==BDQ

[/INDENT][/INDENT]

I did want to give you an update on my success with your suggestions.  I went into WinXP and did a Disk Cleanup followed by a defrag which freed up 6+GB of space.  I then booted into a live disk of gparted and was able to reclaim 110GB of space from WinXP.  Following this I booted into WinXP and after an automatic CHKDSK it rebooted into XP and I was able to access my database.

I hope this update helps others.

---

### Post by Bashing-om on 2012-10-16
You are indeed looking and doing good ! 

best to ya <==BDQ

---

