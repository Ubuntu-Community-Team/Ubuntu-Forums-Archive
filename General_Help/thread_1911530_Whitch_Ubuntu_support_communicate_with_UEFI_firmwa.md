---
title: "Whitch Ubuntu support communicate with UEFI firmware variables?"
date: 2012-01-19
forum: General Help
---

### Post by jink2005 on 2012-01-19
Dear Friends:
In order to edit the boot option in a UEFI firmware, i need to use efibootmgr to do some thing. But "efibootmgr requires that the kernel support access to EFI non-volatile variables (through _/proc/efi/vars_ on 2.4 kernels, _/sys/firmware/efi/vars_ on 2.6 kernels)."
 
Do ubuntu support to use efibootmgr? And which Ubuntu support communicate with UEFI firmware variables?
 
looking forward to your help. Thanks.

---

### Post by jink2005 on 2012-01-20
Do somebody can help me? I'm still waitting for your reply. Thanks.

---

### Post by mastablasta on 2012-01-20
I think GRUB supports UEFI for a while now.

---

### Post by jink2005 on 2012-01-20
> **mastablasta said:**
> I think GRUB supports UEFI for a while now.
 
Thanks for your reply. I know that Grub2 can boot ubuntu in UEFI mode. But, when it booted, you can't use efibootmgr. There will be no /proc/firmware/efi directory. May ubuntu don't have the function to communicate with those variables.
 
I've tried Fedora 16. It's OK. May i've to turn to it for help. Thanks a lot, again.

---

### Post by oldfred on 2012-01-20
I do not have UEFI, but hope to soon, so I am following a lot of the threads. I have not seen the requirements you have posted.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

