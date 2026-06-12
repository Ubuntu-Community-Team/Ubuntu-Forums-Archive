---
title: "Resize a physical volume, will lvm freak out?"
date: 2010-06-22
forum: General Help
---

### Post by jerome1232 on 2010-06-22
So I'm installing bsd in a virtual machine to play around with it, may install it to my machine if I have enough fun :D

This is my current partition layout.

```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e5e32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          36      289138+  83  Linux
/dev/sda2              37       30515   244822537    5  Extended
/dev/sda5              37       30515   244822536   8e  Linux LVM
```

/dev/sda5 is the only physical volume in my volume group, will lvm freak out if I go resizing it so I can carve out some space for bsd.
 
Here is a screen shot of system-config-lvm if that is relevant.

---

### Post by justleen on 2010-06-22
yea, it will.
If you shrink the parition on which the VG is residing, LVM will freak.
But, why would you want to do that? the whole idea of LVM is to let LVM handle resizes..

---

### Post by jerome1232 on 2010-06-22
Well will bsd recognize lvm? I thought it only worked on linux.

---

### Post by justleen on 2010-06-22
eeehm.. That's a good one. Probably not.

Okay, let assume it doesn't. You would then have to
- shrink locigal volumes
- shrink volume group
- shrink physical volume
- use freed space to create partition for bsd.

Note: quick search on BSD install in LVM told me "No,it doenst install to a lvm.."

---

### Post by jerome1232 on 2010-06-22
! was going through the man pages of the lvm tools and notice there's pvresize. I can use it to set the pvsize then use fdisk or another partitioning tool to bring it down to that size.

This ought to keep lvm from dieing on me, I already don't fill the volume group up completely (I keep room for snapshots and growth) so I think that will work for me.

I will setup a test system in a virtual machine before I go hacking up my real system, if I can get it working there I might be brave enough to make the attempt.

---

### Post by justleen on 2010-06-22
Testing on a different lvm would definitely  be the way go indeed!
I do think you should resize bottom up though. if you just do a pvresize, what happens to the lv's??

from lvreduce manpage
"lvreduce allows you to reduce the size of a logical volume.  Be careful when reducing a logical volume's size, because data in the reduced part is lost!!!"


So that means you need fdisk/parted/gparted to resize the volume on the LV, then lvreduce the lv and after that resize VG and PV

---

### Post by jerome1232 on 2010-06-22
After destroying my virtual machine 5 times in a row I made some progress on the resize. It's actually pretty easy unfortunately I don't think it will work on my real machine (I'll explain)

So a few things, pvresize isn't destructive (it will refuse to shrink if there are allocated extents that are going to be destroyed) In a future release it is planned that it will actually move extents around if possible to get them out of the way of a resize as well. Right now it just flat out refuses to shrink if there is a volume in the way though.

parted is destructive. :D


At first I had difficulty with parted because pvdisplay defaults to units of GiB and parted shows units in MB or sectors. I tried converting myself and destroyed the partition 5 times. Then I found this write up and it helped wonders. What I mostly got out of that was you can get pvdisplay and parted to both display in units of sectors. Do a little addition and bam.


[http://fedorasolved.org/Members/zcat/shrink-lvm-for-new-partition](http://fedorasolved.org/Members/zcat/shrink-lvm-for-new-partition)

I did this while the system was running to the physical volume on which the root partition resides. Rebooted and it's working with the resized physical volume.


The problem is on my real system one of the logical volumes is residing at the end of the physical volume, so without another physical volume to pvmove it to I can't resize the physical volume. I don't know of a way to move the logical volume more towards the beginning of the physical volume. It has 32 GB's free so I guess I can shrink it down and hope the shrinking occurs at the end of the physical volume, but there's no guarantee that that is where the unallocated extents are.

---

### Post by bodhi.zazen on 2010-06-22
That is the "problem" with downsizing a LVM.

It is easy to upsize them (LVM), but when you downsize them, you run into fragmentation.

In a nutshell, LVM may fragment the files and when you downsize you just move the physical boundaries of the LVM. The tools to downsize the LVM will not move the data.

You would need to physically move the data yourself and honestly it is often easier (IMO) to simply back up your data , re-partition you HD, and then restore your data.

This wiki page :

[https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview](https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview)

Will give you some pointers . It was written for LUKS, but it uses LVM as well.

You might also want to try the Fedora forums as LVM is default in Fedora and you may find someone there with more expertise in LVM.

---

### Post by jerome1232 on 2010-06-22
> **bodhi.zazen said:**
> 
You would need to physically move the data yourself and honestly it is often easier (IMO) to simply back up your data , re-partition you HD, and then restore your data.


If you read the how to I followed one of the listed pre-req's is a desire to do things the hard way ;)

Nevertheless I just so happen to keep backups of that particular volume, it also just so happens that the computer that holds the backups has a 10 mbs nic and it's a pain to restore 60 GB's of data over that connection :s

I took a peruse around the fedora forums and didn't find anything too useful, I think I have all the info I need (I really think there should be a tool to shuffle your volumes around on one PV)

I'll try resizing the LV, and cross my fingers the free'd space is in the right spots. If that doesn't work I guess I can lvremove do my resizing then recreate and restore from backup (12 hours later...)

Thanks for all the advice. I'll go ahead and mark this as solved.

---

### Post by bodhi.zazen on 2010-06-22
> **jerome1232 said:**
> If you read the how to I followed one of the listed pre-req's is a desire to do things the hard way ;)

Nevertheless I just so happen to keep backups of that particular volume, it also just so happens that the computer that holds the backups has a 10 mbs nic and it's a pain to restore 60 GB's of data over that connection :s

I took a peruse around the fedora forums and didn't find anything too useful, I think I have all the info I need (I really think there should be a tool to shuffle your volumes around on one PV)

I'll try resizing the LV, and cross my fingers the free'd space is in the right spots. If that doesn't work I guess I can lvremove do my resizing then recreate and restore from backup (12 hours later...)

Thanks for all the advice. I'll go ahead and mark this as solved.

Best of luck to you, if you run into problems post back and I will take a look.

---

