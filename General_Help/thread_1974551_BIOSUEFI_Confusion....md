---
title: "BIOS/UEFI Confusion..."
date: 2012-05-06
forum: General Help
---

### Post by Uncle Spellbinder on 2012-05-06
Here are my computer's specs: [I]HP Pavilion - Intel Core i5 - 3.10GHz - 8 GB memory - nVidia GeForce GT 520 (1 GB)
[/I]

So, I wanted to dual-boot 12.04 on this computer with Windows 8 Customer Preview. I needed to get the CD/DVD to boot. Went into computer start-up by pressing Esc during restart.

Here is what I am presented with:

[IMG]http://i48.tinypic.com/24ywwwp.jpg[/IMG]


Clicking F9 for *boot menu* I get this:

[IMG]http://i45.tinypic.com/2dh8m89.jpg[/IMG]


But clicking F10 for *computer set-up*, then *storage > boot order* I get this:

[IMG]http://i48.tinypic.com/ej33m.jpg[/IMG]



Between the seemingly different boot order screens, I have several choices. Which boot order screen do I use? Then, what to change???

This whole BIOS/UEFI thing has me confused. And after searching the net, it seems I'm not alone.



:-?

---

### Post by L3ct3rIII on 2012-05-06
Hello there.

Go simple. Use the Computer Setup (F10). Then put *ATAPI CD/DVD Drive* on *Windows Boot Manager*'s place. Save and reboot with the CD/DVD on your drive. I believe this will do.

Any problems, please tell us here.

See ya.

---

### Post by oldfred on 2012-05-06
Some info:

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

To get Ubuntu to install in UEFI mode you have to boot CD or USB flash drive in UEFI mode.

Most that have installed Ubuntu successfully with UEFI have partitioned in advance. If you have installed Windows first backup efi partition before installing. There was a bug where grub overwrote the efi partition, not sure if fixed yet or not, so best to have backup.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

PC's boot menu, the DVD drive showed up twice: once prefixed with UEFI, once with BIOS.
grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot entry for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

---

### Post by Uncle Spellbinder on 2012-05-06
Thanks for the links, *oldfred*. Seems the days of just a simple dual-boot are gone.

I'll check out the links and attempt this when time permits.

---

### Post by Uncle Spellbinder on 2012-05-06
Or I could just forget the whole dual-boot scenario and install 12.04 cleanly, wiping Windows 8 in the process.

---

### Post by Bandit on 2012-05-06
> **Uncle Spellbinder said:**
> Or I could just forget the whole dual-boot scenario and install 12.04 cleanly, wiping Windows 8 in the process.

Win8 works goo... well ehh it works anyway in VirtualBox. :lolflag:

---

