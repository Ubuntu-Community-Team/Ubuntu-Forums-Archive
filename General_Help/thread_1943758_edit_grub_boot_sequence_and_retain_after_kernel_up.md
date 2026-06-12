---
title: "edit grub boot sequence and retain after kernel update"
date: 2012-03-20
forum: General Help
---

### Post by daehenoc on 2012-03-20
Hi all,

I have a 2008 Macbook Pro and I have installed an OCZ SSD into it.  I have read and followed the instructions on the ArchLinux wiki about enabling the AHCI mode on the SATA controller: [https://wiki.archlinux.org/index.php/Solid_State_Drives#Special_considerations_for_Mac_computers](https://wiki.archlinux.org/index.php/Solid_State_Drives#Special_considerations_for_Mac_computers)

I have gotten the grub menu to be displayed for 10 seconds and can manually edit the grub boot entry to add in the 'setpci -d 8086:2828 90.b=40' line just above the 'set root' line, and this DOES get the SATA controller to run in AHCI mode and makes a significant difference to the speed of SDD access :)

But I don't know how to make this change permanently, if I do manually edit the /boot/grub/grub.cfg file, and make the above change, that change will be lost when the grub.cfg file is next updated with a kernel update, right?

I am pretty sure that adding in the setpci command into the /etc/grub.d/10_linux is the correct approach to have this change retained in the grub.cfg file on kernel update, but I don't know where in this file to add this change - can anyone give me a tip on where to add it?

Thanks,!

---

### Post by Bucky Ball on 2012-03-20
Are you using 'sudo' to open the file and edit?

```
sudo nano /boot/grub/grub.cfg
```

Might be a silly question but you never know ...

---

### Post by daehenoc on 2012-03-20
Yes, I am using 'sudo' :)  So the file is saved and that option is executed on reboots.

But next time 'update-grub' is run (kernel update, grub update, something else), that change will go away as grub.cfg is overwritten with the configuration from /etc/grub.d/xx_blah

So I'm trying to find out where to put the 'setpci' line in the files in the /etc/grub/ directory (or /etc/default/grub file) so that this 'setpci' line is written to the grub.cfg file after a kernel or grub update.

---

### Post by oldfred on 2012-03-20
gksudo gedit /etc/default/grub
Then 
sudo update-grub

[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)

> GRUB_CMDLINE_LINUX
    * Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   * This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
       o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 


---

