---
title: "Triple Boot: Can't install Grub to /boot during Installation."
date: 2011-12-03
forum: General Help
---

### Post by Wiking on 2011-12-03
Hi, I'm trying to set up a triple boot with Windows 7, Kubuntu 11.10, and Backtrack 5. 

My first primary is the W7 installation, I was also able to set up Kubuntu 11.10. During the installation of Kubuntu I was able to install Grub bootloader to Kubuntu's /boot partition (sdb3) as directed in many tutorials. Then I used a program in Windows to point to the Linux partition so W7 doesn't overwrite Grub on updates.

Trying to install the third OS I was able to set up the partitions, although the second /boot for BT5 was not a primary but a logical partition. When I tried to install Grub bootloader onto the BT5 /boot (sdb8) it would not let me. The OK button was not clickable, not highlighted, forcing me to abort the installation.

Could I perhaps install the BT5 Grub bootloader to the Kubuntu /boot (sdb3) folder? I made it 1gb just incase, that should be enough. Could I install two separate bootloaders to the same /boot partition?

Or could I perhaps delete the Kubuntu partition and try installing BT5 first, and then Kubuntu after? But then the Kubuntu /boot would still be a logical and not a primary.

---

