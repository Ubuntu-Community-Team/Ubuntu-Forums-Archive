---
title: "Help needed relating to UEFI booting - Precise"
date: 2012-02-11
forum: General Help
---

### Post by Hekla on 2012-02-11
This morning, when trying to press F10 when changing the switchable graphics card settings in the bios on my Lenovo ThinkPad E320, I pressed F9 and reset to default settings. This appears to have got rid of the "Ubuntu" option in the boot menu, leaving me with no way to boot into Ubuntu on my SSD. I can only boot into windows or a live CD/USB (which I will only be able to access tomorrow).

From what I have read, this is related to the UEFI system that is being used, and I think should be fixable through a live CD, but last time I tried, I ended up re-installing Ubuntu in desperation.

Now that I have made the same mistake again, I would like to know how to fix it, I'd guess through a live CD.

It is perhaps a little to easy for me to make this mistake (as I did today a little too early in the morning) and I really need to know a fix.

Thanks.

---

### Post by Bobhuber on 2012-02-11
> **Hekla said:**
> This morning, when trying to press F10 when changing the switchable graphics card settings in the bios on my Lenovo ThinkPad E320, I pressed F9 and reset to default settings. This appears to have got rid of the "Ubuntu" option in the boot menu, leaving me with no way to boot into Ubuntu on my SSD. I can only boot into windows or a live CD/USB (which I will only be able to access tomorrow).

From what I have read, this is related to the UEFI system that is being used, and I think should be fixable through a live CD, but last time I tried, I ended up re-installing Ubuntu in desperation.

Now that I have made the same mistake again, I would like to know how to fix it, I'd guess through a live CD.

It is perhaps a little to easy for me to make this mistake (as I did today a little too early in the morning) and I really need to know a fix.

Thanks.
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by oldfred on 2012-02-11
I often post the link posted above by Bobhuber, but recompiling grub is not required any more.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

---

