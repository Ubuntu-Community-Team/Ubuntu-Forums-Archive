---
title: "Disabling GRUB boot and adding entry to boot.ini"
date: 2010-06-19
forum: General Help
---

### Post by nemiux on 2010-06-19
Hey everyone, I want to install ubuntu 9.10 into other partition, but I want the win xp boot.ini file to configure my boot settings, not the GRUB. First I want to ask is it possible to install ubuntu, but add a boot entry in boot.ini? If not, then I know how to remove it, i found a file called ms-sys, with it I can remove GRUB. So let's say grub is no more, what should be an entry to ubuntu. When it was installed into Windows it was ```
c:\wubildr
```, now what should I enter, my guess would be ```
m:\boot\grub\menu.lst
``` But I want to be sure, hope you understand my question. Thanks :)

---

### Post by TeoBigusGeekus on 2010-06-19
I don't think you can do that - windows can't read linux filesystems.
You could try of course, if you have ubuntu installed on a ntfs partitions, but don't hold your breath...

---

### Post by elliotn on 2010-06-19
When I first got ubuntu I too wanted to do that, but couldnt succeed, grub is better than windows boot.ini

---

### Post by oldfred on 2010-06-19
Windows had code in the partition boot sector and that is how it works. With grub legacy it was also easy to install to a partition boot sector and chainload to, but grub2 does not like to install to a partition, but can be force. If any of the files grub2 uses to boot get moved even by filechecks then you will have boot issues. You then have to copy the grub2 image in the partition boot sector and put that into the windows partiiton to boot to.

I suggest you use grub. If you ever want to revert to windows just use fixMBR or install a window style boot loader.

per meierfra. mbr.bin may cause problems in some cases better to use lilo
sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

per kansasnoob Note: If I use Lilo to restore a Windows MBR using my "installed" Ubuntu I always like to remove the package "lilo" when done just to prevent some later "conflict" with grub updates, this of course is as easy as "sudo apt-get remove lilo".

---

