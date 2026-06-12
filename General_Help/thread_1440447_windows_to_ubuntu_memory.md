---
title: "windows to ubuntu memory"
date: 2010-03-27
forum: General Help
---

### Post by xredan on 2010-03-27
I have a dual boot with windows vista and ubuntu 9.10 i would like to move some of the memory on my hard drive from my windows partition to my ubuntu partition. If i can i would like to do it from my ubuntu partition if possible.
My ubuntu partition is 15 GB my windows partition has 235 GB with 93 free.

---

### Post by Mark Phelps on 2010-03-27
You have your terms wrong.  Memory is NOT contained on drives; that is know as disk space.

OK, so you want to remove some space from your Vista partition and add that space to your Ubuntu partition. Right?

If that's true, you would do the following:
1) Boot into Vista and use the Disk Management utility to shrink the Vista partition.
2) Since you can't change the Ubuntu partition size while you're running Ubuntu, you would need to go to distrowatch.com and download and burn a GParted LiveCd
3) Boot from the GParted LiveCD and use the Partition Editor tool to resize the Ubuntu partition to fill the unallocated space freed up by shrinking the Vista OS partition.

However ... are you SURE they are on separate partitions?  If not, don't do what I said above; instead, open a terminal in Ubuntu, type the following "sudo fdisk -lu" (that's a lowercase L, not a one) and post the results back here -- before you do anything to your partitions.

---

### Post by dcstar on 2010-03-27
> **Mark Phelps said:**
> 
.........
2) Since you can't change the Ubuntu partition size while you're running Ubuntu, you would need to go to distrowatch.com and download and burn a GParted LiveCd
.........

There is no need whatsoever to burn any other CD if you have a Live Ubuntu CD (which virtually everyone has if they have installed Ubuntu), just boot off the Live CD and use the gparted program which it contains.

---

