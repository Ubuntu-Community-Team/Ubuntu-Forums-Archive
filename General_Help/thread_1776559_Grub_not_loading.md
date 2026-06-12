---
title: "Grub not loading"
date: 2011-06-06
forum: General Help
---

### Post by sauravshrestha on 2011-06-06
Hi, I deleted my Ubuntu partition from Windows vista and when my laptop boots up it goes to the grub-rescue> prompt. When I tried to do the root        (hd0,0) command, it says "command not found". And I tried to put the ubuntu installtion CD but it does not load either although my boot sequence has CD as the first choice. How can I get it to start windows?

---

### Post by seawolf167 on 2011-06-06
You'll have to reinstall your Windows MBR and boot records

Insert the Windows installation cd and boot into "Recovery Mode" (versus starting an installation)

Once there (it'll be a command prompt), type

```
fixmbr
fixboot C:
```reboot and you should be good to go

---

### Post by oldfred on 2011-06-06
seawolf167 commands are correct if XP. But with Vista or 7, it is bootrec.exe or just bootrec and then the command.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by sauravshrestha on 2011-06-07
Hi guys, I am not able to load anything from the CD drive. The CD is the first in my boot order list. But some why when I put the Windows recovery CD or UBUNTU live CD, it just says "Grub commands>" and does not load anything. And the only command that seems to work is ls which shows the partitions on the disk. Do i have to reset the BIOS or something?

---

### Post by seawolf167 on 2011-06-07
That means you are not booting from the cd yet. Look for a message during POST that says something similar to "Press [F12] to enter boot menu". Press that key and you'll get a one time boot menu where you can select to boot off your cd/dvd drive. If you don't see a message, the displaying of such messages is probably turned off in BIOS, you'll have to check that.

---

### Post by sauravshrestha on 2011-06-07
I hit the F12 that should show the Boot options but the same "grub command>" console shows up...I just took out the hard drive and formatted it but it still says "grub command>" at startup...how do i get rid of this and be able to setup ubuntu ?

---

### Post by linuxinstalledfromhdd on 2011-06-07
Did you change the boot order in BIOS?

---

### Post by sauravshrestha on 2011-06-08
My BOOT order was fine. I did however fix my laptop. I hooked my hard drive up to this device that let me see the files (dont know the name of this thing sorry :(....) it hooks up as a USB connection and let me see the files. So I installed Ubuntu on it via USB, so now that the Ubuntu is installed on the primary partition, grub works fine and shows me all the OS installed (even deleted ones). So I am able to load up Ubuntu. If I need, I will install Windows 7 in the future. 

Thanks guys!...it took some time but nailed it down. Phewww!!!!

---

