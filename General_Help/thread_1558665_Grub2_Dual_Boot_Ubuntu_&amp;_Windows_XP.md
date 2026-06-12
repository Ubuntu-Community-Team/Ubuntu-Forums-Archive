---
title: "Grub2 Dual Boot Ubuntu &amp; Windows XP"
date: 2010-08-22
forum: General Help
---

### Post by Limpaa on 2010-08-22
Hi all 

I'm trying to use grub2 as a bootloader. After tweaking my bootloader I'm still able to run Ubuntu but I'm still not able to run my Windows XP. I suspect a wrong entry in my Grub.cfg. As suggested on one of the thread on this forum I've downloaded the Boot info script:

[http://ubuntuforums.org/showthread.php?t=1495816](http://ubuntuforums.org/showthread.php?t=1495816)

Here is the result of it:
[ATTACH]167220[/ATTACH]

Moreover before this issue, I had a similar issue with the Grub2 dual boot, where I got Windows to work untill I got the message: NTLDR is missing. When running the repair mode of Windows XP I made a huge mistake by running FIXBOOT, where I pretty much erased my Ubuntu boot disk, because FIXBOOT by default takes the first drive. Anyway after reinstalling Ubuntu again I got now up to this point again. After I sorted out my Grub entries in Grub.cfg I still have to fix my boot of Windows.

Any suggestion on how to attack this issue?

---

### Post by dougalkerr on 2010-08-22
You could download and burn the SuperGrub boot disk and have a go at one of the options. It should fix the Windows boot problem even if you have to yet again install Linux.

---

### Post by oldfred on 2010-08-22
This is a more typical windows entry. You would have to add your UUID.

menuentry "Windows XP" {
       insmod ntfs
       set root=(hd1,1)
       search --no-floppy --fs-uuid --set EC0CEE940CEE595A
       drivemap -s (hd1) (hd0)
       chainloader +1
}

But you do not have any windows boot files in any windows partitions. Did you have another windows install that you eliminated? Windows combines boot into the first and moves all the boot files into that partition. You will have to repair the windows boot partition.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by Limpaa on 2010-08-22
Wow! Thanks a lot I'll give it a go.

I've solved the Grub.cfg issue by changing my entry to:

        insmod ntfs
        search --no-floppy --fs-uuid --set D6940D7012345678
        set root=(hd1,3)
        drivemap -s (hd0) (hd1)
        chainloader +1

This resolved my issue of the grub.cfg. Anyway as discussed before I'm now facing the NTLDR is Missing error.
I've already started with the FIXMBR, but thought the syntax was FIXMBR \device\harddisk1,

At last I've tried to copy the ntldr & ntdetect.com from the XP Recovery Disk unto the my Windows Partition which worked but still no luck. Keep in mind that my XP recovery CD is rather old with SP2 and my installed XP Version is SP3. Maybe this can be asking for trouble?
After reading your reply again I remembered that before installing Ubuntu, the drive contained Windows 2K3 Server, which was my primary boot. This might be the reason why I was not able to boot anymore since the Boot.ini, ntdetect.com & NTLDR, where resided on that drive? When I was looking on my xp drive I couldn't find these files under my mounted XP Drive in Ubuntu.

At last I also tried the BootCFG /Rebuild and strangely enough it doesn't even detect my Windows XP version. But it does detect my legacy BARTPE CD on drive D:

Also I'm able to boot into Ubuntu without any problems.

Since Windows XP is on the second hard disk partition 3.

If none of the repair function work from the XP recovery CD I'll give it a try with the suggested of the TUX repair disk.

---

### Post by Limpaa on 2010-08-22
Hi Again

I seem to also have solved the boot loader issue, but I'm now facing the issue that my Hal.dll is corrupted or missing. I've already tried this without any luck:
[http://www.tech-pro.net/howto-fix-hal-dll-missing-corrupt.html](http://www.tech-pro.net/howto-fix-hal-dll-missing-corrupt.html) under the section:** Using the Windows Recovery Console**.

I've also noticed that my drive letter has changed from F: to E:, which I think might be the case of this issue.

---

### Post by oldfred on 2010-08-23
hal missing is almost alway not hal.dll missing but an issue with the boot.ini. Check that boot.ini refers to correct partition.

Fix WinXP hal.dll Post #8
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
From Recovery Console run bootcfg /rebuild (fixes boot.ini which often causes hal.dll errors) and CHKDSK /r (which checks the drive for errors and fixes any).

Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)

---

### Post by Limpaa on 2010-08-23
Thanks again. I'll have a look at your solutions on wednesday and otherwise on Friday and let you know any results. One of my google thoughts was also an incorrect Boot.ini. I'll keep you posted.

---

