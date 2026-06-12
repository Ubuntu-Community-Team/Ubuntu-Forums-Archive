---
title: "Cannot resize my Windows 7 Partition with Gparted"
date: 2010-05-13
forum: General Help
---

### Post by schwabdale on 2010-05-13
I have seen this on two PC's now. When I boot off a Ubuntu CD, I am unable to shrink the Windows Partition. I know there is enough space to shrink it. Maybe 100gb of space available.

---

### Post by howefield on 2010-05-13
What's the error ?

In any event, I'd always use Windows file system tools on windows systems, and linux tools on linux systems when doing something like this.

Windows 7 has an application included that will do this for you, if I recall correctly.

---

### Post by wojox on 2010-05-13
Why don't you boot into Windows 7 and use the built-in functionality in Disk Management to shrink it?

---

### Post by wilee-nilee on 2010-05-13
> **schwabdale said:**
> I have seen this on two PC's now. When I boot off a Ubuntu CD, I am unable to shrink the Windows Partition. I know there is enough space to shrink it. Maybe 100gb of space available.

Do not try to resize W7 with gparted, that is not a good idea it will break W7. Use the W7 disk manager virtual to shrink it after doing a optimizing defrag, leave a open space for Ubuntu and only install grub to the hard drive not to any partitions. So if it is a single HD your trying to install to grub goes to sda, nothing with a # like sda1...etc.

Sorry I as soon as I saw somebody trying to resize W7 with gparted I just quickly posted, without reading that this had already been addressed. ;)

---

### Post by schwabdale on 2010-05-13
Is there any Linux software that will resize a Windows 7 partition? Or Free windows software?

---

### Post by warfacegod on 2010-05-13
Gparted can do it. You'll need to get ntfsprogs from Synaptic. I think its that one anyway, there are several ntfs related packages in there.

Again, as others have said, this is an unwise thing to do at best and at worst you'll *never* get 7 (or Vista for that matter) running again.

---

### Post by WorMzy on 2010-05-13
[QUOTE="schwabdale"]Is there any Linux software that will resize a Windows 7 partition? Or Free windows software?[/QUOTE]

Did you try the disk manager that comes with Windows 7, like others have suggested? Here's a link to more info about it: [http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/](http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/)

---

### Post by wilee-nilee on 2010-05-13
> **schwabdale said:**
> Is there any Linux software that will resize a Windows 7 partition? Or Free windows software?

Maybe if you shared with us why your hesitant to use the on board W7 partitioner we could help.

---

### Post by Mark Phelps on 2010-05-13
> **schwabdale said:**
> Is there any Linux software that will resize a Windows 7 partition? Or Free windows software?


Free Windows software ...

EASUS Partition Master.  Will do the resizing of NTFS partitions you want to do.

---

### Post by schwabdale on 2010-05-13
Thanks All!

I want to resize a partition and install Ubuntu at the same time. I don't want to boot into Windows, resize, the boot off a Ubuntu disk and install. 
I just want to resize and install off the same disk. 

I wonder if I could get Easeus on Ubuntu? Anybody know?

---

### Post by wojox on 2010-05-14
> **schwabdale said:**
> Thanks All!

I want to resize a partition and install Ubuntu at the same time. I don't want to boot into Windows, resize, the boot off a Ubuntu disk and install. 
I just want to resize and install off the same disk. 

I wonder if I could get Easeus on Ubuntu? Anybody know?

Look here [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

The Live CD has Gparted installed on it.

---

### Post by Mark Phelps on 2010-05-14
> **schwabdale said:**
> Thanks All!

I want to resize a partition and install Ubuntu at the same time. I don't want to boot into Windows, resize, the boot off a Ubuntu disk and install. 
I just want to resize and install off the same disk. 

I wonder if I could get Easeus on Ubuntu? Anybody know?

What you want, and what SHOULD be done are two different things ...

If you want to trash your Win7 install, then go ahead insisting on doing things YOUR WAY.  But, if you want to do it such that when you're done, both OSs will work, then stop being so stubborn and listen to those of us who have done this and know how to do it right.

---

### Post by warfacegod on 2010-05-14
> **Mark Phelps said:**
> What you want, and what SHOULD be done are two different things ...

If you want to trash your Win7 install, then go ahead insisting on doing things YOUR WAY.  But, if you want to do it such that when you're done, both OSs will work, then stop being so stubborn and listen to those of us who have done this and know how to do it right.

Agreed! Wholeheartedly Agreed!

schwabdale,

What you are looking to do has, at best, a 1 in 10 shot at working. I dodged this bullet once with Vista because I had *no choice*. Vista's Disk Manager would only shrink the partition so small (76 GB). I shrank it again with Gparted (45 GB) without breaking Vista. I am convinced the *only* reason it worked was because I first shrank it in Vista and ran chdsk before and after each operation. I will not be trying this again, ever, and I absolutely do not recommend you try it either.

---

### Post by wilee-nilee on 2010-05-14
> **warfacegod said:**
> Agreed! Wholeheartedly Agreed!

schwabdale,

What you are looking to do has, at best, a 1 in 10 shot at working. I dodged this bullet once with Vista because I had *no choice*. Vista's Disk Manager would only shrink the partition so small (76 GB). I shrank it again with Gparted (45 GB) without breaking Vista. I am convinced the *only* reason it worked was because I first shrank it in Vista and ran chdsk before and after each operation. I will not be trying this again, ever, and I absolutely do not recommend you try it either.

Yes this is all correct, you should never repartition a windows setup then just install before you check to see if it boots and is not corrupted.

---

