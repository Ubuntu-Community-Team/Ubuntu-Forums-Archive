---
title: "Partition manager isn't finding my Windows"
date: 2010-01-04
forum: General Help
---

### Post by randall550 on 2010-01-04
Can anyone tell me why A Linux partition manager can't find my Windows XP? I know it's there because if I reboot and remove the flash drive with my Ubuntu on it, it boots into XP.
I have an Acer Aspire One and I want to split the hard drive and install Ubuntu to dual boot, but the partition manager shows my hard drive is all unallocated space. Does anybody have a clue what's going on and what I can do about it?:confused:

---

### Post by switch10 on 2010-01-04
Because Ubuntu has mounted your hard drive.  you must first unmount the drive.  It should be on your desktop or under places.  right click on it and select unmount.

---

### Post by randall550 on 2010-01-05
Okay, I tried that, found that it wasn't mounted. Still wasn't showing the windows. I thought by chance if I mount it, it would reveal something. Still no windows or any clue why not. So I unmounted it again, and it still is not detecting the windows. Whatever the problem is, it isn't the mounting or lack thereof. Any other ideas? Thanks.

---

### Post by michy99 on 2010-01-05
Can you post a screenshot from Gparted?

---

### Post by cenzorrll on 2010-01-05
if you're using gparted, then you need to make sure you select the correct drive (sda, sdb, etc).  it'll be in the top right corner.  if it still doesn't show up then i have no idea.

if it doesn't, what does the partition manager show, just the usb drive? or only other partitions on the hard drive?

---

### Post by randall550 on 2010-01-05
[ATTACH]142628[/ATTACH]
Here's the screenshot. It shows an empty hard drive. As I said before, I know it isn't empty, but the XP isn't being detected.

---

### Post by michy99 on 2010-01-05
Open a terminal and enter this command and post the output.```
sudo fdisk -l
```

---

### Post by randall550 on 2010-01-05
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638       19457   151171650    7  HPFS/NTFS
/dev/sda3               1          14      108020+  de  Dell Utility
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by randall550 on 2010-01-06
bump

---

### Post by cenzorrll on 2010-01-06
i think everyone is at a loss here.  try reinstalling gparted?  i've never seen fdisk see the partitions but gparted not

---

### Post by randall550 on 2010-01-06
My gparted is part of an UbuntuLive installed on a flash drive. I don't think it's that, because I had the same issue with an Ubuntu UNR. 
Somebody has to have dealt with this before. This can't be an unprecedented issue.

---

### Post by warfacegod on 2010-01-06
> My gparted is part of an UbuntuLive installed on a flash drive. I don't think it's that, because I had the same issue with an Ubuntu UNR.
Somebody has to have dealt with this before. This can't be an unprecedented issue. 

It may very well be. I've never seen gparted do that especially when in a Live environment. Try searching here and the net for gparted broken/not seeing drive,help, etc.

---

### Post by Coco999 on 2010-01-06
I had the same trouble. The reason was that the partition table was corrupted, don't ask me how or why. When the partition table was corrected, then GParted saw the partitions and I could install Ubuntu to the HD.

---

### Post by warfacegod on 2010-01-06
> I had the same trouble. The reason was that the partition table was corrupted, don't ask me how or why. When the partition table was corrected, then GParted saw the partitions and I could install Ubuntu to the HD.

If that's the case then running chckdsk in Windows seems to be the logical next step.

---

### Post by randall550 on 2010-01-06
So if I run chkdsk, will I be able to use that to correct the problem?

---

### Post by warfacegod on 2010-01-06
Running chckdsk (remember, it's for windows) is supposed to repair if possible. Google chckdsk (I think that's how to spell it) because it's been 3 years since I used Windows and I can't for the life of me remember enough of it to walk you through starting chckdsk.

You should also google partition table repair.

To answer your question, if it will fix the problem, then it will do it for you, it's an automated process once you tell it to run after rebooting.

---

### Post by randall550 on 2010-01-07
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\showplace>chkdsk
The type of the file system is NTFS.
Volume label is ACER.

WARNING!  F parameter not specified.
Running CHKDSK in read-only mode.

CHKDSK is verifying files (stage 1 of 3)...
File verification completed.
CHKDSK is verifying indexes (stage 2 of 3)...
Index verification completed.
CHKDSK is verifying security descriptors (stage 3 of 3)...
Security descriptor verification completed.
Correcting errors in the Volume Bitmap.
Windows found problems with the file system.
Run CHKDSK with the /F (fix) option to correct these.

 151171649 KB total disk space.
  18143616 KB in 40179 files.
     13776 KB in 4211 indexes.
         0 KB in bad sectors.
    116889 KB in use by the system.
     65536 KB occupied by the log file.
 132897368 KB available on disk.

      4096 bytes in each allocation unit.
  37792912 total allocation units on disk.
  33224342 allocation units available on disk.

C:\Documents and Settings\showplace>

This is the output from running chkdsk in "read only" mode. I ran it with "-f" and "-c" twice, did disk cleanup and defrag, and then ran "chkdsk -f" one more time. Then I tried gparted again, and nothing has changed.

---

### Post by warfacegod on 2010-01-07
Chkdsk (that's how it's spelled!) has eliminated your hard drive being bad as the problem. Post your partition table if you don't mind.

```
sudo fdisk -l
```

You know what? Hold off on that for a bit. Use synaptic to completely remove gparted and then reinstall it. If that doesn't work, then do the above.

---

### Post by Coco999 on 2010-01-07
If you pay a look at my thread in
[http://ubuntuforums.org/showthread.php?t=1366233]("http://ubuntuforums.org/showthread.php?t=1366233")
you'll probably find the key to solve your problem. 
Warning: The corrected partition table PT.txt applied to my HD, yours is different.

---

### Post by warfacegod on 2010-01-07
I just found this:

[http://ubuntuforums.org/showthread.php?t=1366233&highlight=partition+table+repair]("http://ubuntuforums.org/showthread.php?t=1366233&highlight=partition+table+repair")

---

### Post by meierfra. on 2010-01-09
Please post the output of

```
sudo fdisk -lu
sudo sfdisk -d
sudo parted -l
```

(don't type the output, use copy and paste)

---

