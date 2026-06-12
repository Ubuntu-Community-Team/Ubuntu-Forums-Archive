---
title: "Attempted to re-install Ubuntu, now cannot alter partitions."
date: 2010-09-09
forum: General Help
---

### Post by silkworm2.5 on 2010-09-09
Hi,
Yesterday I tried to re-install Ubuntu. Long story behind that, I wont bore you with it.
I used Parted Magic to remove the partitions that Ubuntu was using. I then rebooted, and I get Grub come up saying that no such Partition exists. I guess it's looking for the Linux partition. I can use the Ultimate Boot CD's boot management tools to access and boot my Windows 7 though.
The problem is, that Gparted will not allow me to modify the partitions on my HDD any more. Attached is a graphic of the message and the layout of my hard drive.

[ATTACH]168967[/ATTACH]

Note: i use windows 7 which came with an emergency recovery tool built into a separate partition.

It says to use Windows 'chkdsk /f' tool to scan the drive. Hard in 7 with UAC not giving the primary admin clearance to allow it, but I got it to. Wrote 'chkdsk /f' in notepad, and saved it as a .bat file and ran with admin privileges. 
So, it scanned thoroughly, with 5 methods and 30 mins, and I booted it twice like it said to. I received no text regarding corruption or correction. Still I get the error message. Any help please?

---

### Post by ezsit on 2010-09-09
Why not use Windows to remove the partition if Windows can not find anything wrong with it? Remove the partition from within Windows and leave it as unallocated space. Gparted should be able to work with the unallocated space.

---

### Post by silkworm2.5 on 2010-09-09
I didn't know Windows 7 had a Partition Editor. How do I access it?

---

### Post by ezsit on 2010-09-09
Control Panels - Administrative Tools - Disk Management

Has it changed in Windows 7?

---

### Post by oldfred on 2010-09-09
If there are a lot of errors chkdsk does not fix them all. You have to keep running chkdsk until you get no errors.

You always should use the windows tools to resize the windows partition.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by silkworm2.5 on 2010-09-09
Thanks for the replies guys.
I used TestDisk to rebuild the MFT and MBR but now I cannot boot windows or the windows recovery partition. Help Please? I is stuck...

---

### Post by oldfred on 2010-09-09
You should use windows tools to repair windows, if at all possible:

Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by silkworm2.5 on 2010-09-09
Should I back up my data before attempting fixing with the rec' disc?

---

### Post by oldfred on 2010-09-09
If it is a recovery disk it probably is the type that just erases everything and restores the hard drive to the day you purchased it. Yes back everything up.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by silkworm2.5 on 2010-09-09
It came with no cd's, but has recovery tools by HP which allowed me to make my own spread over 3 CD's. Thanks. I'l report back soon with my findings.

---

### Post by silkworm2.5 on 2010-09-10
Yep, that fixed it right up! thanks!

---

### Post by perspectoff on 2010-09-10
Make sure you have a new version of whatever Partition Manager you are using.

I have used GParted (on a LiveCD) for years and have loved it. But my older version did not recognize the ext4 filesystem (used in Karmic and Lucid). I laughed when I could not manage the partitions, because all it indicated was an exclamation mark as an error!

But I updated to a new version. Now I'm well again!

---

### Post by silkworm2.5 on 2010-09-10
Thanks for the help! It fixed it!
(sorry if I said this twice, but my other response isn't appearing on my screen.)

---

### Post by perspectoff on 2010-09-10
Just as an aside, I like Perfect Disk (trial or purchased edition) for my Windows Partition Manager (including Windows 7) because you can manage the MFT with it.

You can't work with the Windows partition while Windows is running (except to shrink the partition a bit)! You can't move the MFT while Windows is running.

Further, if the MBR (Master Boot Record) has been altered, you can't boot into Windows anyway!

(A Windows LiveCD might be able to do that, though, I don't know).

Fixing the MBR is automatically done when installing Ubuntu, BTW, if that is your only problem.

There are a wealth of suggestions at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

or

[http://kubuntuguide.org/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://kubuntuguide.org/Multiple_OS_Installation#Changing_Windows_partition_sizes)

---

