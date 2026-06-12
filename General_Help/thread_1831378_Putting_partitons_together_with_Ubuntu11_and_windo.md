---
title: "Putting partitons together with Ubuntu11 and windows 7 dual install"
date: 2011-08-23
forum: General Help
---

### Post by wingman1 on 2011-08-23
Okay so my friend has a laptop which originally came with Win7 but he wanted to install Ubuntu on there too so now he has a dual install but he wants to remove ubuntu because he's having some trouble with the wireless connection to the internet. So now i want to know how he can delete ubuntu and get the partition he had it on to be assigned back to win7?

---

### Post by dave01945 on 2011-08-23
yeah within windows he can just delete the ubuntu partition and the extend the windows one to use the whole disk again

---

### Post by grahammechanical on 2011-08-23
I do not have any experience with doing this but I suggest that he

1) Use Windows tools to first defrag the hard disk.

2) Become familiar with any Windows partitioning tools available to him and use them to delete the Ubuntu partitions and then expand and move or move and expand (whichever is necessary) the Windows partitions to take up the unallocated space that use to be the Ubuntu partitions.

3) He will need to run some utility to remove the Ubuntu boot loader (Grub) from the MBR.

Regards.

---

### Post by oldfred on 2011-08-23
Best to restore windows boot loader to MBR first or else once you delete Ubuntu you will not be able to boot. Then you need a repairCD. You also can fix from Ubuntu liveCD.

So create a repairCD which you always should have for every installed system or Ubuntu liveCD.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You should only need to run fixMBR but I post the standard fix windows commands.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
[COLOR=Red]BootRec.exe /fixMBR [/COLOR]  #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

