---
title: "Boot from CDROM to HD root partition???"
date: 2009-12-13
forum: General Help
---

### Post by t2000kw on 2009-12-13
I had a dual boot setup on my laptop. When I installed Windows 7, I had to wipe out my boot manager (Easy BCD) and let Windows create a system partition as well as the Windows partition. The Linux partitions are untouched, but now I can't choose to boot to Ubuntu. 

Is there a way to create a bootable CDROM that will give me the option to boot from various partitions on my laptop's HD?

Thanks!!!

Donald

---

### Post by zvacet on 2009-12-13
You can reinstall grub from your ubuntu cd.Because you didn´t tell witch version you are running read both links

1. [this]("http://ubuntuforums.org/showthread.php?t=224351")    if you use version prior then karmic

2.[this]("https://help.ubuntu.com/community/Grub2") if you are using Karmic

---

### Post by t2000kw on 2009-12-13
I probably should have mentioned that I am trying to avoid using GRUB as my boot loader. I had plenty of issues upgrading Vista to 7 and it may have been because of the bootloader I was using. Some claim that using a 3rd party bootloader can cause problems with Windows Update. 

I do have GRUB installed on the Linux root partition, which is not the boot partition. My previous boot manager pointed to that partition to start GRUB and load Linux. 

I am running Jaunty, thinking of installing Karmic soon. 

I wish this laptop had the same boot options that my desktop PC has. I can boot to any drive I want to on it. 

Don

---

