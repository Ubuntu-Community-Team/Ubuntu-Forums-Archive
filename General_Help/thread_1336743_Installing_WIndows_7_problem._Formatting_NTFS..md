---
title: "Installing WIndows 7 problem. Formatting NTFS."
date: 2009-11-24
forum: General Help
---

### Post by blinkblink on 2009-11-24
hey guys, I'm very new to Linux and this OS is pretty confusing to me now. Right now, I don't think it's a good time to pick up a new OS since I'm in the middle of the school year, so i think I'll try to understand ubuntu this summer. But right now I want to do a clean install of Windows 7.

So I changed my system bios to reboot from CD, I reboot, and I run the installation. But Win7 can't be intalled because the disk is not in NTFS format. How do I fix this? Anyone help me with switching back to Win7? 

Also, I head that after Windows is installed, a small part of ubuntu is still intact because Windows doesn't recognize the ubuntu format. How can I remove this vestige? 


p.s. I really like Linux, and I intend to learn it. but it I'm a little sad that I can't understand the OS (especially the downloading/unpackaging/compiling) because I'm a CompSci major. So much to learn haha.

---

### Post by blinkblink on 2009-11-24
bump

---

### Post by rbc on 2009-11-24
While I'm shocked that the install DVD doesn't do its own partitioning, here's what you do....you're going go need a linux distro's Live CD (any one that has GParted) or the GParted LiveCD. Boot up, delete ext3 partition and the swap partition. Then, use that space to create an NTFS partition. Here's a happy medium though. Why not dual boot, or do a Wubi install. That way you can get up to spped with linux at your leisure.
A helpful hint....I have always had better luck with GParted when Applying one change at a time

---

### Post by blinkblink on 2009-11-24
eh, i'm really a ubuntu noob and i didn't understand too much of what you said.  <_<

I appreciate any and all help, but if anyone could, can you give me a detailed step-by-step play of how to install win7? As in...Gparted live cd (w/e that is).  

thanks.

---

### Post by 3rdalbum on 2009-11-24
If you erase the hard disk, then no part of Ubuntu remains except for the first stage of GRUB in the Master Boot Record (this will be removed when you install Windows).

Boot up the Ubuntu live CD.
Go to System > Administration > Partition Editor.
Select each partition that's displayed, right-click and choose "Delete" (sorry I'm working from memory here).
Click Apply. This will delete all partitions on your hard disk, leaving the whole lot unallocated.

The Windows installer can take it from there.

---

### Post by rbc on 2009-11-24
When you installed Ubuntu, you were using a LiveCD. In other words, it's an operating system that is running solely in RAM. GParted=Gnone Partition Editor, and is also linux based. Unlike Ubuntu, though, it only has one application, that being the partition editor. The reason you need a LiveCD is because you cannot edit the partitions while they are mounted (being used, or at least while you have access to them). There are many partition editors out there. I happen to prefer GParted. Google it and find the download site, then burn the image to CD. Then pop it in the optical drive and boot up. You will then be able to delete the linux related partitions and create the necessary NTFS

Edit: 3rdalbum is obviously much more linux savvy than I, but I have always had better luck with the GParted LiveCD. GParted under Ubuntu would never let me turn off the swap partition

---

