---
title: "Troubleshooting Corrupted Windows Boot"
date: 2011-11-26
forum: General Help
---

### Post by AlexanderF on 2011-11-26
Yes another one of those threads. I am the end of my wits here. I wanted to dual boot Ubuntu and Windows 7. I installed Ubuntu, but apparently overwrote the MBR with GRUB. I can no longer boot into Windows 7. When I select Windows 7, it just displays a blank cursor. I tried inserting the Windows 7 Install DVDs (SP1 and original), but they could not detect my install. In fact, when I chose to re-install they could not find a suitable partition/drive to install Windows 7 to. This is probably, because I am using a GUID Partition Table layout. What I can not understand is that, all my Windows 7 files are there. Even the hibernate file, created right before installing Ubuntu. Does anybody know how to troubleshoot this (eg Gparted flags or Disk Utility). A warning sign for me is that the Windows Partition is listed as a Linux Basic Data Partition, even though it is not really a data partition.

---

### Post by hansdown on 2011-11-26
Welcome to the forum, AlexanderF.

Just a couple of quick questions, to help the helpers;

1- Can you boot into ubuntu?

2- Are your windows DVDs restore discs?

Thanks.

---

### Post by AlexanderF on 2011-11-26
1. I can login perfectly into Ubuntu. I can access all my Windows partition files through Ubuntu by mounting it.

2. No my Windows DVDs are my install discs. When I insert them, I have a Install option and a repair option. Neither work

---

### Post by Mark Phelps on 2011-11-26
I don't know that this will work, but I suggest you read through the info below on boot-repair -- it may be able to repair the boot files: 

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by AlexanderF on 2011-11-27
Thanks for the Link. I'll work through it

---

### Post by AlexanderF on 2011-11-28
I am having trouble selecting the right settings for boot-repair. My system is like this
SDA 1 - EFI (FAT)
SDA 2 - Windows 7 (NTFS)
SDA 3 - Ubuntu

Now some questions:
1. Do I select the GRUB reinstall or the MBR repair?
If Grub reinstall:
a) should I purge and reinstall?
b) should I seperate the /boot/efi ?
If MBR repair:
a) which restore of the MBR do I select. (gptmbr, gptmbr_c, gptmbr_f)
b) partition boot to mbr. Should I keep it at Ubuntu or switch to Windows?

---

### Post by oldfred on 2011-11-29
Is this a new system. If the first partition is efi, that may mean you are booting with UEFI not BIOS and have gpt(GUID) partitioning not MBR(msdos).

gpt partitioning only has a MBR so it can write info to tell old system tools that is really is not MBR and not to mess with it.

[http://en.wikipedia.org/wiki/UEFI](http://en.wikipedia.org/wiki/UEFI)
Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Post this from liveCD:
If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell

Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
Has chainload window efi grub entry:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Some have had success with getting Ubuntu to work & grub to install but there are a few bugs.

[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by AlexanderF on 2011-11-29
Thank you. I will work through those links and post back

---

