---
title: "please help me recover a partition"
date: 2011-07-10
forum: General Help
---

### Post by dziring on 2011-07-10
[LEFT][COLOR=#000000]I'm having what feels like a major disk drive issue, but I'm hoping can be fixed easily:[/COLOR]
[COLOR=#000000]I have a hard drive that seems to have been corrupted. fdisk still shows that partition I need is in place, but says that[/COLOR]
[COLOR=#000000]"WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted."[/COLOR]
[COLOR=#000000]I did not intentionally set up GPT on this drive. Any ideas how I can recover the partition? (rebuild MBR?)[/COLOR]

[COLOR=#000000]---[/COLOR][/LEFT]

[COLOR=#000000][LEFT][COLOR=#333333][COLOR=black]parted tells me the following:[/COLOR][/COLOR][COLOR=#333333]
 
[LEFT][COLOR=black]Warning: /dev/sdc contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables. Or perhaps you deleted the GPT table, and are now using an msdos partition table. Is this a GPT partition table?[/COLOR][/COLOR][/COLOR][/LEFT]
[/LEFT]

---

### Post by dziring on 2011-07-10
Question:  Can I just run fdisk, 'w'rite the table, and quit?
 
I don't want to experiment.  I would really like to keep the data on the partition if at all possible.

---

### Post by srs5694 on 2011-07-10
The GUID Partition Table (GPT) consumes more space on the disk than does a typical Master Boot Record (MBR) partition table. Thus, if you take a GPT disk and use a GPT-unaware utility to create a new MBR partition table, the result is that the GPT data aren't completely overwritten. Technically, the result is a valid MBR partition table; however, some tools get confused by this and won't work on the disk, or will even work on the old GPT data rather than the new MBR data. (In some cases, that might even be appropriate -- say, if something improperly wrote MBR data to the disk.)

If you're certain that the disk should be using MBR data, you can fix the problem with my [FixParts](http://www.rodsbooks.com/fixparts/) program. (The Web page provides instructions for what to do in this case.) If, OTOH, the disk is a GPT disk and the MBR data are in error, you can use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to read the GPT data and write out a fresh protective MBR (the part of the GPT that's been damaged, if this is what's happened).

Chances are the problem is old GPT data, but I can't really be 100% positive of that without further information, such as the complete output of "sudo fdisk -lu /dev/sdc" (since what you did provide suggests it's /dev/sdc), a description of what should be on the disk, and possibly the GPT data as revealed by gdisk when you tell it to use the GPT data.

FWIW, this problem frequently occurs when a disk is moved from a Mac to a PC or after the user has experimented with a Hackintosh installation. This is because Mac OS X uses GPT by default. Although Windows Vista and 7 are both GPT-aware, their installation tools do an incomplete job of wiping the GPT data when installing the OS, so GPT disks often slip through this transition with enough GPT data intact to cause problems.

---

### Post by dziring on 2011-07-10
Thank you for the information.  In this case, I am fairly sure that it was an MBR drive yesterday, before I (best guess here as to what happened) accidentally typed '/dev/sdc' instead of '/dev/sdd' while I was trying to work on an external drive.  (OOPS!)

I will absolutely take a look at FixParts this evening.  

Thank you,
DZ

---

### Post by srs5694 on 2011-07-10
Accidentally working on the wrong drive would not have modified the one you were trying to work on, at least not with any tool with which I'm familiar. Chances are you had leftover GPT data on the disk and just didn't realize it.

---

