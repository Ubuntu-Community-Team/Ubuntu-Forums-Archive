---
title: "Directory refuses to be deleted"
date: 2012-05-06
forum: General Help
---

### Post by davy jones on 2012-05-06
A particular folder on my Western Digital 2 TB external hard disk is refusing to get deleted. The error shown is "Input/Output error". I have faced this problem before with this hard disk but it was a very long time ago and the only solution I found then was to format it. It is a strange problem because the folder has suddenly gotten corrupted for no visible reason. One of the files now has a weird character in its name (this has also happened before). Formatting the drive is simply not an option anymore because it has too much data and I have no place to back it up. Any help would be much appreciated. Thank you.

---

### Post by CharlesA on 2012-05-06
That part of the drive is bad.

Have you tried running fsck or badblocks on the drive?

---

### Post by davy jones on 2012-05-07
No. Can you please tell me how to do that? (I'm not really tech savvy)

---

### Post by carl4926 on 2012-05-07
If you install gparted you can use that to check the drive, assuming it's a Linux format?

---

### Post by davy jones on 2012-05-07
It's NTFS

---

### Post by k999 on 2012-05-07
Try connecting it to a Windows computer, and then run a disk check on it.

---

### Post by davy jones on 2012-05-07
Also, when I clicked on the check option in gparted, there was an alert saying that doing that can cause loss of data, which as I said, I just can't afford.

---

### Post by carl4926 on 2012-05-07
Use windows to check it
It could be a dirty problem

---

### Post by CharlesA on 2012-05-07
> **carl4926 said:**
> Use windows to check it
It could be a dirty problem
Yep. That is more than likely the problem.

---

### Post by davy jones on 2013-01-04
OK I have still not been able to solve this problem. I have not checked it using windows yet but I don't want to take any steps that may result in loss of data. A similar thing has actually happened to another folder as well and my hard drive has been acting up more than unusual. My computer just shuts down automatically for no reason during the middle of file transfers to the drive sometimes. 
Please, I need to find a way to fix this problem WITHOUT losing any data. Help.

---

### Post by fdrake on 2013-01-04
> **davy jones said:**
> OK I have still not been able to solve this problem. I have not checked it using windows yet but I don't want to take any steps that may result in loss of data. A similar thing has actually happened to another folder as well and my hard drive has been acting up more than unusual. My computer just shuts down automatically for no reason during the middle of file transfers to the drive sometimes. 
Please, I need to find a way to fix this problem WITHOUT losing any data. Help.try not to use any further the drive. Make room. find another disk and start backing up. How big is the drive?

---

### Post by davy jones on 2013-01-04
It is a 2 TB drive and there is around a 1000 GB free. The problem was happening even when there was 1.3 to 1.4 TB free space on it. Plus it's a drive which I need to use regularly as my laptop only has a 250 GB internal drive and I do a lot of downloads.

---

### Post by CharlesA on 2013-01-04
> **davy jones said:**
> OK I have still not been able to solve this problem. I have not checked it using windows yet but I don't want to take any steps that may result in loss of data. A similar thing has actually happened to another folder as well and my hard drive has been acting up more than unusual. My computer just shuts down automatically for no reason during the middle of file transfers to the drive sometimes. 
Please, I need to find a way to fix this problem WITHOUT losing any data. Help.

That points to a drive going bad. Either clone it to another drive, or try to copying it and hope it doesn't fail in the middle of a copy.

---

### Post by davy jones on 2013-01-05
So I take it that buying a new hard drive is the only solution? I just want to check something to be sure - my laptop has shut down/restarted sometimes during file transfers to the drive. Is this solely because of the drive or my laptop could have something to do with it as well? And if it is only because of the drive, is that also harming my laptop? If I'm transferring data from this external drive to another one, and the computer shuts down in the middle again, will that harm the new drive as well?
Also, please recommend which external drive would be best suited with Ubuntu. Both in the portable and non-portable category. And yet another thing that I want to double check is - most of these drives (like Seagate, WD) say that they're compatible with only Windows and Mac and don't mention Linux at all. Is that just because they don't mention Linux or are some of them actually incompatible with Linux?

---

### Post by t0p on 2013-01-05
I would suggest you start backing up your data now.  If you can't get a big disk right away, start with USB sticks, cards, DVDs.  Get stuff backed up so when your external drive dies you will still have as much data as possible.

I have a 1TB external drive, and it works fine.  But that won't always be the case, so I try to periodically copy stuff to DVDs.  Most of my photos, music and video files are on DVD so if the drive suddenly dies I'll still have most of my stuff.  Your drive seems to be on its way out, so get backing up.

---

### Post by t0p on 2013-01-05
> **davy jones said:**
> Also, please recommend which external drive would be best suited with Ubuntu. Both in the portable and non-portable category. And yet another thing that I want to double check is - most of these drives (like Seagate, WD) say that they're compatible with only Windows and Mac and don't mention Linux at all. Is that just because they don't mention Linux or are some of them actually incompatible with Linux?

My 1TB drive is a Seagate.  Manufacturers and retailers rarely say if their kit is Linux-compatible because most customers don't care, plus the manufacturers probably don't know.  But I have yet to buy a drive that doesn't work with Ubuntu.

Sometimes external drives come with special protection/encryption software already installed.  That software won't work with Linux, and I guess you might have to format the drive before you can use it.  Maybe someone else knows more about that?

---

### Post by CharlesA on 2013-01-05
> **davy jones said:**
> So I take it that buying a new hard drive is the only solution? I just want to check something to be sure - my laptop has shut down/restarted sometimes during file transfers to the drive. Is this solely because of the drive or my laptop could have something to do with it as well? And if it is only because of the drive, is that also harming my laptop? If I'm transferring data from this external drive to another one, and the computer shuts down in the middle again, will that harm the new drive as well?
Also, please recommend which external drive would be best suited with Ubuntu. Both in the portable and non-portable category. And yet another thing that I want to double check is - most of these drives (like Seagate, WD) say that they're compatible with only Windows and Mac and don't mention Linux at all. Is that just because they don't mention Linux or are some of them actually incompatible with Linux?

The only thing a hard shutdown could do is corrupt data in transit, or cause the file system to have errors - fsck fixes the file system, but you'd have to check each file to make sure they aren't corrupted.

I would really check dmesg when you are transferring files and see if it throws any errors before the reboot. It's likely it freaks out if the machine is unable to read from the drive.

> **t0p said:**
> I would suggest you start backing up your data now.  If you can't get a big disk right away, start with USB sticks, cards, DVDs.  Get stuff backed up so when your external drive dies you will still have as much data as possible.

I have a 1TB external drive, and it works fine.  But that won't always be the case, so I try to periodically copy stuff to DVDs.  Most of my photos, music and video files are on DVD so if the drive suddenly dies I'll still have most of my stuff.  Your drive seems to be on its way out, so get backing up.

This. I've been using Seagate drives for a long while and haven't run into any problems (yet), I get them because they are cheap and have a smaller (sorta) form factor than some of the Western Digitals I have seen.

> **t0p said:**
> My 1TB drive is a Seagate.  Manufacturers and retailers rarely say if their kit is Linux-compatible because most customers don't care, plus the manufacturers probably don't know.  But I have yet to buy a drive that doesn't work with Ubuntu.

Sometimes external drives come with special protection/encryption software already installed.  That software won't work with Linux, and I guess you might have to format the drive before you can use it.  Maybe someone else knows more about that?

Indeed. All the drives I have tried - internal, external, thumb drives, etc have works fine with *nix.

Some of the externals came with "drive software" for the "capacity indicator" on the base of the drive, but it was Windows/Mac only and I just formatted the drive to EXT4 and left it at that. The indicator doesn't work, but a quick check of the drive after mounting it can show you the free space.

---

### Post by vanadium on 2013-01-05
This is an ntfs file system. I do not know why you refrained from the advise already given, i.e., have the drive connected to a Windows system and check/repair the file system. Any file system needs to be checked and made consistent from time to time. For an ntfs file system, only Windows has the tools for that.

I have had the issue myself, and I have looked for a linux way of solving the problem, but there is no solution. The linux ntfsfix tool was not able to resolve the issue. A check on Windows did.

---

### Post by Rebelli0us on 2013-01-05
Linux cannot repair NTFS partitions. Use Windows check-disk before concluding that the hardware is faulty.

---

### Post by davy jones on 2013-02-10
I haven't checked the disk in Windows yet because checking it could lead to loss of data and as I said, I can't afford that. I'm still looking to buy a new drive but I haven't been able to decide as almost all 2 TB drives, whether Seagate or WD or otherwise, have got mixed reviews. 
I'm obviously not going to buy another WD disk so I guess Seagate is the only option right now. I'm looking at Seagate Expansion and Seagate Backup Plus. Any suggestions?

---

### Post by CharlesA on 2013-02-10
> **davy jones said:**
> I haven't checked the disk in Windows yet because checking it could lead to loss of data and as I said, I can't afford that. I'm still looking to buy a new drive but I haven't been able to decide as almost all 2 TB drives, whether Seagate or WD or otherwise, have got mixed reviews.

Everything is like that because some people have great experiences with a product and some people have a rotten experience with the same product.

Unless you don't want to use that drive until you run chkdisk on it, it would be a good idea to run chkdisk to rule out a file system error, or to see if it is indeed a hardware error. My bet is a hardware error, which means it would be a good idea to copy any data on that external drive to different media ASAP.
 
> I'm obviously not going to buy another WD disk so I guess Seagate is the only option right now. I'm looking at Seagate Expansion and Seagate Backup Plus. Any suggestions?

The only difference I can see between the two is the [Expansion]("http://www.seagate.com/external-hard-drives/desktop-hard-drives/expansion-hard-drive/") is a desktop drive (which requires a power pack) and the [Backup Plus]("http://www.seagate.com/external-hard-drives/portable-hard-drives/standard/backup-plus/") is a "portable" drive and only requires power via USB. [There is also a "portable" version of the Expansion too]("http://www.seagate.com/external-hard-drives/portable-hard-drives/standard/expansion-portable/").

If you are intending to use either of these drives in Linux, the included software will likely not work.

---

### Post by davy jones on 2013-02-10
Can chkdisk cause data loss? If so, I would prefer to not do it until I've backed up my data.
I was looking at the 2 TB version of these drives and they both need external power. Anyway, if it's all the same then I guess I would prefer to go with Expansion since I don't need any of the software that's installed on Backup Plus.

---

### Post by Bufeu on 2013-02-10
> **davy jones said:**
> **Can chkdisk cause data loss?** If so, I would prefer to not do it until I've backed up my data.
I was looking at the 2 TB version of these drives and they both need external power. Anyway, if it's all the same then I guess I would prefer to go with Expansion since I don't need any of the software that's installed on Backup Plus.
No, as far as I know. chkdsk only checks the disk for errors. Maybe, if chkdsk tries to repair damaged, you can loose data.

---

### Post by davy jones on 2013-02-11
So this is the message that I got when I ran chkdsk on Windows -

chkdsk f: 
The type of the file system is NTFS. 
Volume label is Elements. 
 
WARNING!  F parameter not specified. 
Running CHKDSK in read-only mode. 
 
CHKDSK is verifying files (stage 1 of 3)... 
Deleting corrupt attribute record (128, "") 
from file record segment 1622. 
Deleting corrupt attribute record (128, "") 
from file record segment 1627. 
Deleting corrupt attribute record (128, "") 
from file record segment 1628. 
Deleting corrupt attribute record (128, "") 
from file record segment 1629. 
Deleting corrupt attribute record (128, "") 
from file record segment 1630. 
Deleting corrupt attribute record (128, "") 
from file record segment 1631. 
Deleting corrupt attribute record (128, "") 
from file record segment 1642. 
Deleting corrupt attribute record (128, "") 
from file record segment 2458. 
File verification completed. 
 
Errors found.  CHKDSK cannot continue in read-only mode.

Please tell me how to proceed from here

---

### Post by CharlesA on 2013-02-11
You would have to run it like this:

```
chkdsk /f f:
```

That will fix any file system errors it finds.

---

### Post by davy jones on 2013-02-12
But since this will try to repair damage, like you said, it could lead to data loss? There are only 2 folders on this drive that seem to be corrupt as far as I know because only these 2 refuse to be deleted. So what are the odds that any data outside these folders will get lost?
P.S I'm sorry for being such a stickler about this but I'm not very good at tech related stuff and I just have to know this before I can risk running that command.

---

### Post by bantuvez on 2013-02-12
CHKDSK will try to repair corrupted data. If it can't, it will remove the corrupted data. So you will only loose corrupted data, which is most likely already lost. 

The only reason not to run CHKDSK is if you have very-very important data on your drive AND you are willing to pay a lot of money to a professional data rescue company to save your data. Professional data rescue companies possibly can recover more corrupted data than CHKDSK.

---

### Post by davy jones on 2013-02-12
So good news. I ran chkdsk /f and it has apparently fixed all errors with no data loss. I thank you all for your advice and want to ask for some more. Should I still buy another drive or will this one stay good for a while?

---

### Post by CharlesA on 2013-02-12
> **davy jones said:**
> So good news. I ran chkdsk /f and it has apparently fixed all errors with no data loss. I thank you all for your advice and want to ask for some more. Should I still buy another drive or will this one stay good for a while?

If you want to be safe, get another drive and backup all your important data to it. That way if the original drive goes out, you still have the backup. :)

The only data you do not have a backup of is data you do not care about.

---

