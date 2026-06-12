---
title: "Ubuntu Linux Mint Dual boot"
date: 2010-07-13
forum: General Help
---

### Post by su-37 on 2010-07-13
Hey I installed Ubuntu first and then decided to try linux mint. Now i want to go back to a single boot with Ubuntu without frying my hard drive.
Can i do this without reinstalling Ubuntu?

---

### Post by dtrot55 on 2010-07-13
Yeah...you should be able to remove that distro if you put it on a different partition in gparted...just get it through the software center and locate the partition in gparted and delete it...then again this is only if you put it on a different partition

---

### Post by oldfred on 2010-07-13
Which grub do you have in the MBR. Is the default Ubuntu then Ubuntu is in the MBR and you can just delete Mint. If the default boot is Mint then when you delete Mint, your system will not boot until you reinstall Uubntu's grub. If Mint is in the MBR install Ubuntu's grub before uninstalling Mint.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you are booted into Ubuntu you do not need the liveCD to install grub to the MBR.

reinstall from your working Ubuntu (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda

---

