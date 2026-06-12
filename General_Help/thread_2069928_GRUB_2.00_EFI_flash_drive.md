---
title: "GRUB 2.00 EFI flash drive"
date: 2012-10-11
forum: General Help
---

### Post by greenyouse on 2012-10-11
I'm trying to build a flash drive that can boot using EFI and GRUB2.  GRUB 2.00-beta6 is able to do this but my Ubuntu host computer has GRUB 1.99-21ubuntu3.4, which lacks the newer grub-install commands.  From a downloaded GRUB 2.00 copy I've tried:

```

$ sudo ./grub-install --target=x86_64-efi --boot-directory=/media/sdb1/EFI/BOOT --efi-directory=/media/sdb1 --removable

```but an error pops up saying "source_dir doesn't exist. Please specify --target or --directory".  Does anyone know how to upgrade Ubuntu to GRUB 2.00-beta6 or install GRUB2 to an external disk from the untarred 2.00 files?

ps. here's where I got the new 2.00:    [ftp://alpha.gnu.org/gnu/grub/](ftp://alpha.gnu.org/gnu/grub/)

---

### Post by oldfred on 2012-10-11
I do not have UEFI, but have this in my notes:

[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)
Bootable UEFI USB Key 
[http://ubuntuforums.org/showthread.php?t=2015019](http://ubuntuforums.org/showthread.php?t=2015019)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)

---

