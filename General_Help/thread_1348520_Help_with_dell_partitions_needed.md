---
title: "Help with dell partitions needed"
date: 2009-12-07
forum: General Help
---

### Post by McGuffin on 2009-12-07
Okay, so I've just got a new Dell inspiron with Windows 7, and I want to set up a dual-boot Ubuntu by partitioning the HDD (which seems to be a fairly standard way of achieving the dual boot).

But, I've hit on a small problem.  My Windows disk manager shows 3 partitions.  One of them is un-labelled (but is apparently an OEM Partition - though I have no idea what this means).  The others are: OS (C: ) and RECOVERY.  All three are primary partitions.  I seem to remember reading somewhere that I can only have a limited number of primary partitions on the drive, but I can't remember where I read this and how many partitions that might be.  Can anyone explain all this?

Further, I can't seem to be able to do anything with the RECOVERY partition, and I don't know what it's for.  Also, only about a third of the space in it is in use.  I'm wondering if I can safely get rid of it?  If so, how? (The "delete partition" option in disk manager is 'greyed-out', so I can't select it).  I've got a Windows re-installation disk that shipped with the laptop, and the pre-installed dell software wants me to create a recovery disk as well.  I don't know if that makes any difference.

I appreciate this may be a question better suited to a Windows forum, but I intend to follow this up with some queries about getting the Ubuntu installation right (once I've sorted out the partitions) which is why I've posted it here.

Thanks.

McG.

---

### Post by snowpine on 2009-12-07
> **McGuffin said:**
> Okay, so I've just got a new Dell inspiron with Windows 7, and I want to set up a dual-boot Ubuntu by partitioning the HDD (which seems to be a fairly standard way of achieving the dual boot).

But, I've hit on a small problem.  My Windows disk manager shows 3 partitions.  One of them is un-labelled (but is apparently an OEM Partition - though I have no idea what this means).  The others are: OS (C: ) and RECOVERY.  All three are primary partitions.  I seem to remember reading somewhere that I can only have a limited number of primary partitions on the drive, but I can't remember where I read this and how many partitions that might be.  Can anyone explain all this?

Further, I can't seem to be able to do anything with the RECOVERY partition, and I don't know what it's for.  Also, only about a third of the space in it is in use.  I'm wondering if I can safely get rid of it?  If so, how? (The "delete partition" option in disk manager is 'greyed-out', so I can't select it).  I've got a Windows re-installation disk that shipped with the laptop, and the pre-installed dell software wants me to create a recovery disk as well.  I don't know if that makes any difference.

I appreciate this may be a question better suited to a Windows forum, but I intend to follow this up with some queries about getting the Ubuntu installation right (once I've sorted out the partitions) which is why I've posted it here.

Thanks.

McG.

Hi McG, you can have up to 4 primary partitions.

The solution in this case is to create a 4th primary partition of the "extended" type. You can then subdivide the extended partition into several "logical" partitions, as needed.

The easiest option is to just let the Ubuntu installer do the work for you. It should give you the option to resize Windows and install Ubuntu in the empty space. Make sure you use the slider to give yourself *at least* 10gb for Ubuntu. 

There is no real advantage to deleting the recovery partition (aside from freeing up a small amount of space) so might as well keep it in case you need it someday.

---

### Post by McGuffin on 2009-12-07
I'd heard that windows will "object" to drive partitions that it doesn't create itself, which is why I'm planning on doing the partitioning ins windows.

What I had originally planned on was to create a "shared" partition for file storage and then have a partition for the windows and a third for ubuntu (the idea then being that both OSs can see the file-store but neither can see each other).  Can I achieve this with logical partitions, or would they all have to be primaries for me to do it?

McG.

---

### Post by audiomick on 2009-12-07
Hi.
I have seen advice from several people here suggesting to resize windows partitions with windows tools. What you should do in any case is defrag the windows partition before you try to resize it.

Having a data partition is a fairly common and good idea. Yes, it can be in a logical partition.

For Ubuntu, you should think about:
About 10GB for the system partition mounted at /  (this is generous, but I had to operate on a computer a few weeks ago on which the / had 5GB and was 100% full.

A swap partition a bit bigger than your RAM. If swap is smaller than RAM, suspend / hibernate can not work.

The rest for a partition for /home. The advantage is that should you have to do a fresh install, you can simply re-mount the /home partition, which contains all your data and all your user preferences and configs.

---

### Post by StuartN on 2009-12-07
> **McGuffin said:**
> My Windows disk manager shows 3 partitions.  One of them is un-labelled (but is apparently an OEM Partition - though I have no idea what this means).  The others are: OS (C: ) and RECOVERY.

One partition contains Dell Diagnostics, which are identical to those on the Dell Utilities CD. The other reinstalls the operating system to the state in which you bought the machine, i.e. minus your data but plus all the crapware.

If you are happy reinstalling from DVD and running diagnostics from the CD then you can erase these partitions (I do not know anyone who ever used either). There used to be a utility in C:/Dell/Utilities to do exactly this, rewriting the boot list to match, but they seem to have removed it. Running BCDEDIT.EXE from a (Windows) command line bootup will restore the boot list.

[http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&l=en&s=gen&docid=298A2E89689E13C2E040A68F5B280AA4](http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&l=en&s=gen&docid=298A2E89689E13C2E040A68F5B280AA4)

---

### Post by McGuffin on 2009-12-08
Okay, so I've got my partitions set up now as follows:

OEM (few MB); Recovery (few GB); C: (180GB); Z: (100GB)

The windows disk manager created the Z: as a logical drive, because according to [this]("http://www.sevenforums.com/tutorials/2674-partition-volume-create-new.html") I can only have three primaries.  Next, I was given a choice between NTFS and "exFAT".  I was expecting to be able to format it as FAT32 - is exFAT the same thing?

What will happen when I try to install Ubuntu on the Z? Can I divide it up again to make a FAT32 chunk that windows will recognise and some other bits just for linux?

Apologies if these seem like fairly amateurish questions, it's just that I've never done this before so I want to make sure I don't muck it up.

Thanks.

McG.

---

### Post by StuartN on 2009-12-08
> **McGuffin said:**
> What will happen when I try to install Ubuntu on the Z? Can I divide it up again to make a FAT32 chunk that windows will recognise and some other bits just for linux?

I do not know why you want any space formatted FAT in their because you already have the Windows partition, so ignoring that:

It does not matter how you format the partition in Windows, so do whatever is quickest. Give the partition a highly recognizeable name - this is probably going to be overwritten, but it makes sure that you are overwriting the correct partition and not one you want to keep.

Linux will let you assign any combination of partitions you want inside this space - you must have a / and a swap partition, but you have plenty of space for /home too. Linux will happily overwrite the existing format to something suitable. If you need to, then you can make Linux partitions (apart from swap) readable in Windows.

---

