---
title: "Grub2 is not showing my windows xp partition on the main menu."
date: 2012-02-22
forum: General Help
---

### Post by winxpuser on 2012-02-22
Hello,

I recently installed Windows 7 on my system ( which already had windows xp and ubuntu 10.10 installed on it) and after the win 7 install the grub2 menu was no longer available so I used the boot-repair application from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
to restore the grub2 bootloader which did work, but now my grub2 menu looks something like this.

[IMG]http://i40.tinypic.com/ek3jig.jpg[/IMG]

If I select the Windows 7 (loader) option I am then taken to the windows 7 boot menu which does show both my Win 7 and Win XP installs, but I would like for the XP item to be on the main grub2 menu along with my Ubuntu and Win 7 items and to do away with the win 7 boot menu and have all 3 OS's showing on the grub2 menu.

Here is a screenshot of gparted to show you how my partitions are divided and how they are setup.

[IMG]http://i41.tinypic.com/10iawiq.png[/IMG] 

And finally, here is the pastebin link to my bootinfo summary page so you can see how everything is tied together.

[http://paste.ubuntu.com/853278/]("http://paste.ubuntu.com/853278/")

If you have any questions please do not hesitate to ask and thanks in advance for any and all replies.

Dave.

---

### Post by oldfred on 2012-02-22
Grub only finds one Windows bootable partition because that is how Windows configures itself. It can only boot from the active partition (boot flag) and litterally moves all the boot files from a second install to the first install.

In your case Windows 7 was second, but it moved the Windows 7 boot files into the XP partition and modified the BCD to boot either system.

More detail here.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You may be able to create a Windows 7 repairCD, move the 7 boot files back to the 7 partition, move boot flag and run repairs to fix & edit BCD to just boot 7.  You also may have to repair the XP partition boot sector PBR as it has been modified to boot 7. But it may work. I ran chkdsk from a Windows 7 repairUSB and it put a Windows 7 PBR or BS into my XP but it still booted XP (not sure how as it did say bootmgr in the partition?). Testdisk shows details of BS or PBR and I could see the difference.

Boot flag needs to be on partition you are repairing so you may have to move it back and forth. Grub does not use boot flag but Windows needs it to boot or run repairs to boot partition.

Make a Windows repairCd or USB before doing anything.
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by winxpuser on 2012-02-22
Thanks for the quick reply oldfred. It seems like alot of work just to move the xp entry to the main grub manu and from the sounds of your reply it may or may not even work after doing all of those things so my new question is since everything seems to be working (ie all the correct os's are booting up normally when selected) would it be ok to just leave things as they are now or does the current setup NEED to be fixed in some way ?

I am only asking because I eventually plan on removing XP from my system anyway and just dual booting the Win 7 and Ubuntu 10.10 OS (splitting up the newly freed HD space between them) so not sure I should even go thru all the hassle if nothing seems to be "broken" and I plan on removing xp soon anyway.  Thanks again for your quick reply.

Dave

---

### Post by oldfred on 2012-02-22
You do not have to do anything now. But at least make a Windows 7 repairCD or USB.

But, do not delete XP without making the fixes. The Windows 7 boot is thru XP and two main boot files (not sure what else but recovery also) is in the XP partition. IF you just delete XP, then 7 will not work and then you do not have a recovery partition.

And of course you cannot backup too much, so Windows 7 backup is a good idea.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by winxpuser on 2012-02-22
got it thx. I will mar this as solved.

Dave

---

