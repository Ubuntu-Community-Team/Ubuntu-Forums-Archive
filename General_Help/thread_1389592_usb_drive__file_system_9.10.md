---
title: "usb drive  file system 9.10"
date: 2010-01-24
forum: General Help
---

### Post by dln9 on 2010-01-24
I am confused about USB drives and file systems.  

At work I use a laptop running Windows XP Pro.  I believe it is using the NTFS.  

There are times that I need to bring large files home to work on them.  At home I am running Ubuntu 9.10 on the ext4 file system.  Then, when I'm done working on the file, I will need to bring the file back to work.  

I want to use a USB drive.  The drive I have is currently formatted with the vfat file system.  

Will this USB drive work for me on both systems?  Should I reformat the USB drive with a new file format?  Which format?  And, how do I reformat it?  Anything else I should be thinking of regarding this?  

Thanks in advance for any help.

---

### Post by marin123 on 2010-01-24
> When Microsoft introduced Windows 95 in, well, 1995, they made several improvements to the operating system when compared to its predecessors. One of the changes made was an enhancement to the classical FAT16 file system that had been in use up until that point. The new variation of FAT was called Virtual FAT or VFAT for short. (Note that many people use the terms "FAT" and "VFAT" interchangeably, even though they are technically not the same. All "FAT" partitions created under Windows 95 or later operating systems are really VFAT partitions.)

i think vfat is actually fat32, and therefore must work with windows... i have usb flash drive formatted in ubuntu and i use it everywhere...

---

### Post by rogue_0111 on 2010-01-24
reformat flash with "fat32" and off you go.

---

### Post by dln9 on 2010-01-24
Thanks to both of you.  

I think you each gave me different answers.  

Should I expect vfat to work just fine on both the XP and Ubuntu machines?  Or, do I need to change the format on the USB drive to fat32?  

(If XP uses NTFS, why wouldn't I want the USB drive formatted as NTFS?)  

Thanks again.

---

### Post by blueridgedog on 2010-01-24
> **dln9 said:**
> 
Will this USB drive work for me on both systems?

It should work with each system as it is currently formatted.

---

### Post by ppirilla on 2010-01-24
> **dln9 said:**
> Should I expect vfat to work just fine on both the XP and Ubuntu machines?  Or, do I need to change the format on the USB drive to fat32?

vfat **is** fat32.  Different systems switch the names, but they mean the same thing.

> **dln9 said:**
> (If XP uses NTFS, why wouldn't I want the USB drive formatted as NTFS?)

First, Linux support of NTFS is at times questionable, so I suggest against it on those grounds.  Secondly, the way NTFS writes data to a disk is thought to shorten the lifetime of flash memory, such as that found in most USB drives.

---

