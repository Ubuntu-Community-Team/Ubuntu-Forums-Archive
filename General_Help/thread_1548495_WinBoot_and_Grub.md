---
title: "WinBoot and Grub"
date: 2010-08-08
forum: General Help
---

### Post by tcopeland on 2010-08-08
So, I just got my tablet back from hp tech, and (<sarcastic>who could have guessed?</sarcastic>) they formatted me. So, I want to install Lucid again (not maverick yet- I want to just do a check on any bugs in lucid first) and use grub but have the option to switch back to Win BCD in the future. I used the command "sudo dd if=/dev/sda1 of=mbr.backup bs=512 count=1" and it was successful. Is that correct for backup of the bcd? How would I switch back to win bcd from grub in the future? Also, is it normal for wireless not to work in live env.? If so, I'll install maverick.

Thanks!

---

### Post by oldfred on 2010-08-08
You should not have to copy the partition boot sector for windows as grub should not overwrite it. Grub does overwrite the MBR, but it is not difficult to reinstall windows boot loader or lilo boot loader as all the MBR windows style boot loaders do is look at the partition table for the active partition (boot flag) and jump to that boot sector to continue booting. When grub boots windows it skips the MBR and just jumps to the partition boot sector to boot windows.

I was able to download the windows repair and copy it to a USB to be able to repair windows. I did not have win7 so I copied the repair CD to a CD and used it to copy itself to the USB.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by tcopeland on 2010-08-08
I don't want to have to repair Windows, I just want to be able to set Windows BCD as default (with an "Ubuntu" option that links to grub) using command lines-whether it be in terminal or cmd- AFTER install. I set Windows BCD as default on my desktop right after install, and the program EasyBCD allows you to add entries to the BCD. If grub is default, does the option "Windows Vista Loader" boot windows or bring up the boot loader? If I have grub as default, how would I switch back to BCD as default with a "Windows" option and an "Ubuntu" option (that actually brings up grub, not ubuntu)? Would I install grub to the ubuntu partition during install to prevent the overwriting of Windows BCD?

---

### Post by oldfred on 2010-08-08
Understand that with easybcd you have to install grub2 to the Ubuntu partition and make a copy of that to boot. But grub2 is not considered by grub to be reliable as it has to use blocklists. Block lists as I understand are hard coded addresses, so if a file is moved on the hard drive by partitioning, updates or even filechks you will have to reinstall grub to make it work. It will work in the beginning but who knows down the road what may change. Grub2 will reliably boot windows. It is not difficult to reinstall a windows boot loader to the MBR. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by tcopeland on 2010-08-08
So reinstalling Windows BL DOES NOT require reinstalling windows? It's not like restore?

---

### Post by oldfred on 2010-08-08
Many but not all windows repairs can be done from linux. That is why many repairCDs are linux based.

Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR
You also can use linux's testdisk to recover a corrupt boot sector from its backup in windows.

From windows repair CD:
In XP
fixMBR
fixBoot
in Vista or 7
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector

---

