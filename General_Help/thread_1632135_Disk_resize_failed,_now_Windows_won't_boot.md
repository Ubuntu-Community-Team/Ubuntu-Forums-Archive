---
title: "Disk resize failed, now Windows won't boot"
date: 2010-11-27
forum: General Help
---

### Post by AndrewX192 on 2010-11-27
Hello,

I am running out of disk space, so I decided to resize Windows 7 on my first hard drive, so I could add another ext4 partition to put data on.

However, gparted threw an error during the resize, and left with me a un-bootable Windows 7 partition.

Windows 7 gets up to about where the login screen appears, but then BSODs and reboots.
Unfortunately, the bsod is so fast, that I cannot see any details.

Windows 7 recovery mode cannot fix the issue.

When I try to repair the disk in gparted I get this error:
ERROR: Current NTFS volume size is bigger than the device size!
Corrupt partition table or incorrect device partitioning?

I have attached my gparted_details log files, in a zipped folder.

Thanks,
Andrew

---

### Post by Sharpie1 on 2010-11-27
I did a similar thing when resizing you will probably need to reboot with your Windows startup disk and enter some commands in the repair console.. at least run chkdsk /r and possibly fix the master boot record ?  do a search on here for "fixmbr" ... you may have to reinstall grub after fixing..

Sharpie1

---

### Post by mikewhatever on 2010-11-27
I've heard W7 doesn't like its partitions resized by non-Windows tools. It is usually advised to use the built in tool to resize the W7 partition. O:) Hope you have a backup.

---

### Post by AndrewX192 on 2010-11-27
> **Sharpie1 said:**
> I did a similar thing when resizing you will probably need to reboot with your Windows startup disk and enter some commands in the repair console.. at least run chkdsk /r and possibly fix the master boot record ?  do a search on here for "fixmbr" ... you may have to reinstall grub after fixing..

Sharpie1
Windows identifies the disk type as RAW.
testdisk shows all the data on the drive, so I haven't lost any work.
There has to be a way to get this back and running.

---

### Post by wet-willy on 2010-11-27
Bootitng is a shareware boot manager/hard drive tools software bundle, very small. If you try it, hit cancel at the first screen and go into maintenance. If it sees the partition, you can try to resize again, it will do error checks first and possibly straighten out the partition information. But first, if your partitions appear in the window, try repairing the MBR first. 
When you hit the radio button for the appropriate drive, hit "view mbr" button, if all four lines are empty, you have a corrupt MBR. Highlight the top row, click fill, if your partitions appear, select the one you want as #1, continue filling in the rest till all partitions are there, click "std mbr" button, click "apply" to write the info to MBR, close and reboot to see if it works. If you were able to rewrite the MBR, it should be good to go.
If testdisk sees the partitions also, you should be able to accomplish the same with it, not sure how it handles errors though.

The Windows 7 recovery disk which can be created on Ultimate and possibly other versions is also available for download on-line, you need the right architecture disk. It works automatically, you boot it, it will suggest automatic first which you should try. But I'm not sure it will be able to re-write partition information to the MBR.

---

### Post by AndrewX192 on 2010-11-27
I got my system back to a working state by reverting to my backups.
I will have to take another go at resizing disks at a latter time.

---

### Post by oldfred on 2010-11-27
If you were resizing it the backup may also be wrong, so testdisk may not work. RAW indicates it needs the boot sector fixed. The boot sector is missing or damaged in the NTFS partition.

download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Restore PBR boot sector for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Testdisk also has a way to rebuild the boot sector.

Or from a windows repair cd you want fixboot.

BootRec.exe /FixBoot
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by AndrewX192 on 2010-11-27
> **oldfred said:**
> If you were resizing it the backup may also be wrong, so testdisk may not work. RAW indicates it needs the boot sector fixed. The boot sector is missing or damaged in the NTFS partition.

download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
Restore PBR boot sector for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Testdisk also has a way to rebuild the boot sector.

Or from a windows repair cd you want fixboot.

BootRec.exe /FixBoot
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I have used testdisk in the past for situations similar to this, and it has been very helpful.
I already checked the results of my restore from backup, and everything is fine!

Thanks for your suggestion, at any rate.

---

### Post by wet-willy on 2010-11-27
Well, here's a little something to think about:

Ultimately you should use Windows 7 disk management first, but it has limitations. The NTFS file system has a backup master file table in the middle of the partition, Windows disk management will not resize below it. If you have a 300GB partition, you will still have to stay with 150GB+.
 
Bootitng's claim to fame is "non-destructive NTFS FAT partition resize", unlike any other partition resize tools, such as the one you resorted to. It will do an error check, report back the maximum/minimum size based on available free space etc., and it will resize your 300GB partition down to 50GB if you like, moving the backup MFT accordingly. It has never failed me on a Windows partition, done it a million times.

---

### Post by Herman on 2010-11-27
:p Does Bootitng fix disk I/O errors too?

---

