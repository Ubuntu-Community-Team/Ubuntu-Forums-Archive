---
title: "Windows can't start after deleting Ubuntu and restoring MBR"
date: 2010-08-30
forum: General Help
---

### Post by zweebna on 2010-08-30
I used to dualboot Ubuntu 9.04 and Windows XP Home Edition. A little while ago, I wanted to delete ubuntu, and without really thinking I backed up my files onto my windows partition and deleted all my Ubuntu partitions using GParted off a Live CD. I then tried to resize my windows partition to take up all the leftover space. This operation failed. I realized that there was a warning sign next to my windows partition. Upon looking at the information, it said: 
```
Warning:
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name     : /dev/hda1
NTFS volume version: 3.1
Cluster size     : 4096 bytes 
Current volume size: 74402976256 bytes (74403 MB)
Current device size: 74404431360 bytes (74405 MB)
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 1792675 (0x1b5aa3): missing cluster in $Bitmap
Cluster accounting failed at 1792676 (0x1b5aa4): missing cluster in $Bitmap
Filesystem check failed! Totally 2 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was and will be made to NTFS by this software until it gets repaired.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
```

At this point I tried to boot into windows to find myself with an error with GRUB. Looking around, I find [this](http://ubuntuforums.org/showthread.php?t=1359802) thread and follow the advice of drs305. Now when I try to boot into windows, I get a message saying:
```
Windows could not start because of a computer disk hardware configuration problem.

Could not read from the selected boot disk. Check boot path and disk hardware.

Please check the Windows documentation about hardware disk configuration and your hardware reference manuals for additional information. 
```

Searching some more, I find [this](http://support.microsoft.com/kb/314477).

Method 1: I don't know how I can do this without booting windows.
Method 2: Step 3 doesn't happen at all, it just goes straight to a command prompt. I don't think the XP CD I have is the original one. When I enter bootcfg /rebuild I get an error:
```
Error: Failed to successfully scan disks for Windows installations. This error may be caused by a corrupt file system, which would prevent Bootcfg from successfully scanning. Use chkdsk to detect any disk errors.

Note: This operation must complete successfully in order for the /add or /rebuild commands to be utilized.
```
Using chkdsk and chkdsk /p yields no results.

Method 3: Upon entering the command, I get "Access Denied"

Method 4: When I try to start the Recovery Console, I get:
```
A disk read error occurred
Press Ctrl+Alt+Del to restart
```
and cannot enter and commands.

I'm almost ready to just take my dad's old work computer and give up. Any help would be greatly appreciated.

---

### Post by cgroza on 2010-08-30
Corrupted File System? What do you say?

---

### Post by metalf8801 on 2010-08-30
you need a windows disc and you need to do a system rescue or repair broken system (something like that) then you need to use the command fix mbr or at least thats one of the first things you should try 

good luck oh and try reinstalling Ubuntu if fix mbr doesn't work 
Dan

---

### Post by drdanielfc on 2010-08-30
One link I will never lose - [http://www.pcstats.com/articleview.cfm?articleid=2264&page=8](http://www.pcstats.com/articleview.cfm?articleid=2264&page=8)

---

