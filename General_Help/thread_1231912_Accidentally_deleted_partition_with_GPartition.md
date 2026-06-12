---
title: "Accidentally deleted partition with GPartition"
date: 2009-08-05
forum: General Help
---

### Post by theblang on 2009-08-05
I had my 500gb external (NTFS) as well as my USB drive plugged into my laptop running Ubuntu.  I meant to delete the partitions on the USB drive using GPartition;  however, I accidentally deleted the partitions on the 500gb external.  I know the data is still there, but what is the best way to get it, or better yet, just repair the partition table?  Thanks in advance.

---

### Post by amac777 on 2009-08-05
I just did a google search and found:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

That seems to be what you are looking for. However, I've never used it myself. Maybe somebody else has some other ideas.

EDIT: Here's a thread about it: [http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)

---

### Post by theblang on 2009-08-05
EDIT: The program is Gparted, not Gpartition, my apologies.

I already tried testdisk.  It did not find any partitions.  I also tried scanning from 0 to 15000 using Parted, also to no avail.  All I did was delete the partition in Gparted, I know the data is still there.  I seem to be having issues restoring the partition though.  Any help would be greatly appreciated, this drive has years worth of data all organized.  I know if worst comes to worst I can data carve it, but surely there is some way I can get the partition information back.  

One option I thought of was deleted the 'unknown' partition that is now listed in Gparted and creating a new NTFS partition.  Not sure if this would work or just screw it up worse.

---

### Post by Hobgoblin on 2009-08-05
> **theblang said:**
> 
One option I thought of was deleted the 'unknown' partition that is now listed in Gparted and creating a new NTFS partition.  Not sure if this would work or just screw it up worse.

Doing anything which writes to the disk will make things worse, unless it is software specifically designed to recover the deleted partition table (I'm not sure that is possible).

photorec (can be installed through the package manager) will get the files back, you'll need somewhere with enough space to put them and they will be completely disorganised.

Maybe someone can come up with a better idea. Until then do not do anything which writes to the drive.

---

### Post by theblang on 2009-08-05
I tried using testdisk.  At first it found nothing, but with a deeper search it found an NTFS partition.  I hit the restore option, it then had to rebuild a boot table I believe, and it asked me to restart.  No luck though.  Still says the drive is corrupted and unreadable.

I grabbed GPart (not to be confused with GParted) but it gives me a seek failure error when I try to run with the -f option.

Any more suggestions would be greatly appreciated.

---

### Post by amac777 on 2009-08-06
As Hobgoblin said above, the more stuff you do the drive, the worse your chances of being able to recover it is. If this is important data that you care about, you need to stop experimenting and be very careful not to further mess up the data. One thing you could try is to make a bit for bit copy onto another physical drive and attempt to recover from that copy. That way, if it does not work, you still have the original disk in its original form to give to a professional data recovery company. But for heaven's sake, don't make any more writes the original copy.

---

### Post by Johnny B on 2009-08-06
testdisk comes with a utility called photorec (or something like that)
probably your best bet

---

### Post by PeterAS on 2009-08-07
A utility that could help you if you can stretch to it is at [www.pcrecovery.com]("http://www.pcrecovery.com").
It's called Drive Restore Professional. Restoring deleted partitions is achieved by analysing the existing structure and rebuilding the Partition Table and/or the MBR. No formatting is required so no changes are made to the partition data. It won't overwrite any existing files and folders even though they are, to all intents and purposes invisible, since the partition currently doesn't exist.  Any changes made with DRP can be rolled back.  It can also handle more complex multi-partition (primary and logical combinations) disks.  
I do hope this can help.

---

