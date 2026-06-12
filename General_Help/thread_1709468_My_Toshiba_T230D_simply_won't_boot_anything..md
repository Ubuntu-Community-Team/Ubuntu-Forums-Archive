---
title: "My Toshiba T230D simply won't boot anything."
date: 2011-03-18
forum: General Help
---

### Post by linx1398 on 2011-03-18
My Toshiba laptop is a nightmare for Linux. It came with Windows 7, has no optical drive, and won't boot from USB.  I got around this by using EasyBCD's BIOS extender and installed Ubuntu from a 32GB flash drive with no issues.  However, upon downloading the driver for the HD4200 (From within Ubuntu, a recommended driver) and restarting my computer, well... nothing boots. No GRUB, no whetever-the-heck-the-Windows-bootloader is,  I just get a flashing cursor for a few minutes and then "Please reboot the computer or insert the boot drive and press any key" and something about realtek...  I'm paraphrasing, because I can't reproduce this, as now I just get an ENDLESS flashing cursor!!!

Deep breaths...

My two boot options are HDD, and LAN acording to the BIOS, and no amount of BIOS fiddling has enabled me to boot from a USB.

---

### Post by pricetech on 2011-03-18
I know you said you don't have an ODD, but does your BIOS have an option to boot from one ??

It might see a USB ODD and let you boot from it even though it won't boot from other USB devices.

Worth a shot.

---

### Post by linx1398 on 2011-03-19
Hmmm... It seems it will boot from a USB FDD (not ODD, but... close enough), and changing the boot order (FDD first) allows me to boot from my USB.  Thanks!
I'll just put Win7 on my USB and repair the installation, and then try and install Ubuntu. Again. ;)

I must have reformatted this poor USB stick about 150 times now...

---

