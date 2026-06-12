---
title: "Migrating from 7.10 to 9.04"
date: 2009-09-21
forum: General Help
---

### Post by knichel on 2009-09-21
I have a server that is running 7.10.  I wish to upgrade, but would like to start fresh.  I was thinking of installing a new HD and booting from a live CD and installing on new HD. 

The problem is I do not have enough time in any one sitting to do all the configuration (iptables, squid, dansguardian, samba, nfs etc...).

I am wondering, Can I install the OS and some parts, then reboot to the 7.10 OS and go back when I have more time to complete ... ?

Will the installer install grub on the new HD?  and will it add entries for the other installed OS (7.10)?  and can I remove the old HD with 7.10 after installing is complete? (/home is on separate drive)

Thanks in advance.

--
Mike

---

### Post by P4man on 2009-09-21
In most cases, you can just prepare a drive on a different machine. As long as you dont install proprietary drivers, you could do a complete install and configuration on whatever machine, then plug the drive in your server and boot from it. You'll probably have to make some adjustments (possibly grub and for sure fstab to mount your /home)  but other than that, I never had any issues "transplanting" an ubuntu install across vastly different hardware.

---

### Post by gali98 on 2009-09-21
I assume you are using the server install disk...
One way (I don't know my way around the alternative installer too well so there might be another way) would be to unplug the old hard drive (with 7.10 thus forcing the installer to add grub to the new disk.) Then after installation is complete, plug the old hard drive back in and run "update-grub" on the new server, adding entries for the old hard drive on the new hard drive.
Then you can boot off either one (making sure you set the bios to boot from the new hard drive.)

Kory

---

### Post by knichel on 2009-09-21
Thanks to both for posting.  My concern with doing the install on another box is that I am afraid that since the hardware is different, it will mess things up (load incorrect drivers etc...).

As for the server install, I am using a plain kubuntu desktop disc as I am dealing with a small classroom of 10-15 computers.  I was also under the impression that the way the installer works is it loads grub on the disk you are installing onto and changes the MBR to point to that install of grub.  ?

--
Mike

---

### Post by P4man on 2009-09-21
if you don't need any drivers that aren't already in the kernel, then its quite okay to install on a different machine. Windows will bluescreen when you do that, but linux handles it just fine ...

---

### Post by knichel on 2009-09-21
Cool, thanks for the tip.

---

### Post by gali98 on 2009-09-22
If you are using a desktop install disk, at the end of the installer (right before you click OK and it starts installing) There is a button that says advanced, and it lets you pick where grub is installed to.
Kory

---

### Post by knichel on 2009-09-23
OK.  So say I have the new disk installed and it is currently connected via /dev/sdc  and the current boot disk is /dev/sda.  If I  install the new OS and configure and install grub to it, then remove the original hd /dev/sda, will that cause problems?

---

### Post by gali98 on 2009-09-23
I wouldn't think so. Just run update-grub once you take it out on the new OS, and it should delete any bad entries.
Kory

---

