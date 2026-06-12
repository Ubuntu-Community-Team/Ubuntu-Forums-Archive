---
title: "Change filesystem from RAW to NTFS?"
date: 2011-06-26
forum: General Help
---

### Post by jeld on 2011-06-26
Hello all!

First of all, I do really like Ubuntu. Still working on getting my way around and finding things but overall I think its great!

But I have a problem. I used my friends removable drive to watch a movie on my laptop, and when he put it back in his it doesn't work.
He uses Windows 7. He has alot of stuff on his drive that we would rather not reformat, so Im here asking you fantastic people for help.

So he had it formatted to NTFS and now its RAW..I have no idea how. It won't work on either my desktop (XP) or his laptop (7) but it works fine on my UBUNTU :)

What gives?

---

### Post by slooksterpsv on 2011-06-26
I'm not sure why it changed to raw, but you may want to get a program called testdisk to repair it. I believe it's in the repos. Just search software center or install it via apt-get like so:

sudo apt-get install testdisk

You can use that program and it'll look for the MFT, partition table, etc. and repair it, if it can.

EDIT: Question did you have it hooked up like an external? If so did you unmount it properly (not just unplug it as that can cause issues like this) or shutdown then remove it?

---

### Post by jeld on 2011-06-26
I checked with my husband he says he unmounted before turning it off and going to sleep.

If I have to get a program to fix this, I'll have to wait to tell you if it worked. I don't have wireless.

I used my own little tiny drive to put a movie on before and all is fine. (But I have that one formatted to FAT32.) 

Is that why it corrupted?

---

### Post by sanderj on 2011-06-26
> **jeld said:**
> Hello all!

But I have a problem. I used my friends removable drive to watch a movie on my laptop, and when he put it back in his it doesn't work.
He uses Windows 7. He has alot of stuff on his drive that we would rather not reformat, so Im here asking you fantastic people for help.

So he had it formatted to NTFS and now its RAW..I have no idea how. It won't work on either my desktop (XP) or his laptop (7) but it works fine on my UBUNTU :)

What gives?

I've never heard of a filesystem called "RAW". So, what do you mean with RAW.

Or, better:
if you connect your friend's removable drive to your Ubuntu computer, can you see the content? If so, type 'mount' on the command line and post the output here.

And what's the goal: see the old contents, or let your friend use the drive again?

---

### Post by WorMzy on 2011-06-26
> **sanderj said:**
> I've never heard of a filesystem called "RAW". So, what do you mean with RAW.

Or, better:
if you connect your friend's removable drive to your Ubuntu computer, can you see the content? If so, type 'mount' on the command line and post the output here.

And what's the goal: see the old contents, or let your friend use the drive again?

RAW isn't a filesystem, it's just used to describe an empty (or in this case, somewhat damaged) partition.

I second the testdisk suggestion.

---

### Post by srs5694 on 2011-06-27
Testdisk is used to recover filesystems that have been lost, but the fact that Linux recognizes it suggests that the problem is something else. I recommend getting more information by issuing the following commands from Linux with the drive plugged in and mounted:

```

sudo fdisk -lu /dev/sdb
sudo blkid /dev/sdb*
df -h

```

This assumes the disk is the second one (/dev/sdb); it could be /dev/sdc, /dev/sdd, or even higher if the computer has more than one internal disk or if other external disks are plugged in.

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to preserve legibility.

It's possible that the partition table is damaged, in which case the fdisk output may provide clues. The blkid output will provide minimal information on filesystem(s) on the disk, and the df output will report what partition(s) have been mounted. My suspicion, though, is that there's been some subtle filesystem damage, not partition table damage. In that case, Windows tools will be the ultimate key to recovery. Getting the basic information from these initial diagnostic commands is the start of finding a solution, though.

---

