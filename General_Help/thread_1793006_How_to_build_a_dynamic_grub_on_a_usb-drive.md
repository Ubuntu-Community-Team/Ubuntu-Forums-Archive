---
title: "How to build a dynamic grub on a usb-drive?"
date: 2011-06-28
forum: General Help
---

### Post by 13east on 2011-06-28
I would like to setup GRUB on a USB where it automatically detects the available OS installations on the machine that it is plugged into...

This could be useful if you messed up your default GRUB menu on a computer and would like to boot into the machine w/out booting Live-OS. Or if you have multiple Live-OS installations on a USB-Drive and would like to add/remove different installations w/out needing to update grub manually.

I know that Grub2 has a OS-prober feature that looks for other installations on the hard-drive, but will that work in either of the scenarios listed above?

---

### Post by andrewthomas on 2011-06-28
All you have to do is install ubuntu to the usb-drive and install grub to the MBR of the USB.

It is identical to installing to a HD.

---

### Post by 13east on 2011-06-29
> **andrewthomas said:**
> All you /have to do is install ubuntu to the usb-drive and install grub to the MBR of the USB.

It is identical to installing to a HD.

Will the OS-prober function work while booting into the USB-MBR?  Will plugging it into different machines update the GRUB dynamically on the spot w/out needing to update GRUB manually?

---

### Post by oldfred on 2011-06-29
A full install of Ubuntu on the USB will give you the full os-prober, but it will not give auto updates of live ISOs if you want those also. I have a full install and some ISOs on a 16GB flash drive. The only difference with a standard install to a second drive is changing a few settings to reduce writes which helps speed up the flash somewhat.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

