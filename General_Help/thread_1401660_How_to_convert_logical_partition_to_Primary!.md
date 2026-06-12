---
title: "How to convert logical partition to Primary!"
date: 2010-02-08
forum: General Help
---

### Post by chinmaya_n on 2010-02-08
Hi,
This is my partition table....(in the image)
Now I would like to install windows in the unpartitioned space [COLOR="Red"]**after a long time**[/COLOR]..... I tried but could not do that. I understood that Windows needs only primary partitions!

So I tried to convert this logical one into primary, but of no use...
Is it possible to convert that unpartitioned space which is under logical drive to a primary one!

---

### Post by r_s on 2010-02-08
you can shrink the extended volume . so that the space becomes unallocated and then install windows on it.

---

### Post by ajgreeny on 2010-02-08
First you could shrink one or all of the logical partitions in the extended sda2, then shrink the sda2 to leave a larger unallocated space at the end of the disk, or you could just install into the 18GB already available after shrinking sda2.   That 18GB is rather small for windows Vista, but you should be able to get XP or Win7 on that size.

---

### Post by oshunluvr on 2010-02-08
> **chinmaya_n said:**
> I understood that Windows needs only primary partitions!

If you mean needs a primary partition to boot to - thats correct (mostly). You can still use logical partitions for data. In fact I recommend "stealing" an idea from linux and having a separate partition for your home. Have you consider VirtualBox rather than a full dual boot setup?

> **chinmaya_n said:**
> 
Is it possible to convert that unpartitioned space which is under logical drive to a primary one!

Using gparted or a similar tool to remove or shrink a LOGICAL partition, then shrink the EXTENDED partition should result in available space for a new PRIMARY partition. When doing the shrinking - the EXTENDED partition needs to be at the END of the drive so the new PRIMARY partition is at the front for Windows to boot from.

Just in case anyone reading doesn't know this: Your drive will accept only FOUR partitions of the PRIMARY definition. One or more of these can be an EXTENDED partition. EXTENDED partitions can hold any number of LOGICAL partitions. There must be a limit, but I've never reached it!

Assuming your partition table isn't messed up (it happens sometimes during shrink and move or delete/create actions in the middle of the drive space), Linux will NUMBER your partitions from PRIMARY to LOGICAL in order of the partition table, except will number your EXTENDED as 4 regardless of how many other PRIMARY partitions you have. Thusly, all LOGICAL partitions start number at 5.

---

### Post by chinmaya_n on 2010-02-09
> Have you consider VirtualBox rather than a full dual boot setup?

I'm using it! But some applications dont do well with that!
for Example: See this [thread]("http://ubuntuforums.org/showthread.php?t=1387726") by this time there are 67 views for this but none replied!!
So I opted to reinstall it!
___________
I did nt find a way to shrink the partition in GParted!

Edit1: It didnt gave me the option because the partition is mounted ?? (see the picture in the post1)

---

### Post by Mark Phelps on 2010-02-09
In future, you would do better to use a GParted LiveCD to do partition work.  Not only is it generally a newer (and therefore, more bug-free) version, but it also does NOT mount any partitions by default.  You can get the ISO image from the distrowatch.com website.

---

### Post by oshunluvr on 2010-02-09
Yeah - sorry I should have been more specific about gparted.

Here's the latest stable bootable cd

[http://downloads.sourceforge.net/project/gparted/gparted-live-stable/0.5.1-1/gparted-live-0.5.1-1.iso?use_mirror=cdnetworks-us-2](http://downloads.sourceforge.net/project/gparted/gparted-live-stable/0.5.1-1/gparted-live-0.5.1-1.iso?use_mirror=cdnetworks-us-2)

---

### Post by ajgreeny on 2010-02-10
Using the ubuntu live CD you only need to right click on any partition that is mounted and choose "Unmount" and you can then work on it.  Remember that for the future.

---

