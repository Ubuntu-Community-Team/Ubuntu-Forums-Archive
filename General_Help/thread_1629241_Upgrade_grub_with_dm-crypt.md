---
title: "Upgrade grub with dm-crypt"
date: 2010-11-23
forum: General Help
---

### Post by Phoenix_Swelter on 2010-11-23
I am still using Lucid with a Luks/dm-crypt setup. I picked up an upgrade today that included grub. It gave me a box that had me choose my location to install the upgrade. I chose /boot. When apt did its upgrade thing, I got the following message: 

[INDENT]Setting up grub-pc (1.98-1ubuntu8) ...
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
Installation finished. No error reported.

[/INDENT]I looked in /boot/grub and found no menu.lst file. I'm scared to reboot until I'm sure everything is going to be okay. Suggestions?

---

### Post by oldfred on 2010-11-23
The choice was where to install the grub boot loader which should be the MBR usually sda. Grub2 does not like to be installed to partitions like sda2 or sda3 as then it has to use blocklist.

You should install grub2 to the MBR of sda to make sure it is installed correctly. If you have multiple hard drives, then you may want to install to sdb or sdc etc.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Phoenix_Swelter on 2010-11-23
> reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

I don't know if I would have had a problem or not, but I followed your directions and had no problem with my reboot. Thank-you! :grin:

---

### Post by Dave_L on 2010-11-23
Ubuntu 10.04

I got the same, or similar, message when I upgraded grub yesterday.  I was given the choices sda and sda1. (I have a single hard drive.) I thought I chose sda, but I may be mistaken.

I'm not sure what a blocklist is, or how that's related to grub.

I can reboot ok, but how can I tell whether grub was updated properly (without blocklists)?

---

### Post by oldfred on 2010-11-23
If you can boot, grub has to be in the MBR. Computers boot from BIOS, to the MBR, to whatever the MBR then says. Grub2 needs the bit more room that the MBR and some space after it make available to work. 

You only end up with blocklists if you install grub2 to the PBR or partition boot sector which does not have much room. To boot you have to have another boot loader chainloading to the grub2 in the PBR. If you have blocklists it will work. But if a grub boot file gets moved on the hard drive, then you have to reinstall grub in the PBR to update the address to jump to or blocklist.

---

