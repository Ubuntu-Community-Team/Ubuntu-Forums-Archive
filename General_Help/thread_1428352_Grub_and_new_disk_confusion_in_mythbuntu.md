---
title: "Grub and new disk confusion in mythbuntu"
date: 2010-03-12
forum: General Help
---

### Post by rramesh on 2010-03-12
When I add new disk to my mythbuntu box, the disk device numbers/names seem to change. This seem to confuse grub. How do I help grub to see root partition (and windows partition) correctly?

Ramesh

---

### Post by srs5694 on 2010-03-12
The simplest solution may be to change how you add the disks. What types of disks are these? If they're SATA, try swapping the motherboard connectors to which each disk is connected. If they're PATA on one cable, try swapping their positions on the cable. If they're PATA on different cables, try swapping which motherboard connectors they plug into. (This may change the way Ubuntu recognizes other devices on each PATA cable, though.)

Another option may be to set the disk order in your BIOS setup utility. Details vary from one BIOS to another, but you should look for a page with advanced disk setup options. Modern BIOSes usually enable you to set the drive order there; use it to reverse the order of the two drives. This solution, however, may require you to re-install GRUB using an emergency disc.

The /boot/grub/device.map file contains mappings of GRUB to Linux device filenames, as in:

```

(hd0)   /dev/sda
(hd1)   /dev/sdb

```

Swapping those around (to associate (hd0) with /dev/sdb and (hd1) with /dev/sda in this example) and then re-installing GRUB (via the grub-install command) may fix the problem. There does seem to be a little bit of voodoo going on with this, though; on one of my systems, the mappings are just plain wacky.

Yet another option is to accept everything as it is and edit /boot/grub/menu.lst (GRUB Legacy) or /boot/grub/grub.cfg. You may need to change "hd0" to "hd1" and vice-versa (or adjust higher numbers if you've got more than one disk). You may also need to edit the "root=" option on the "kernel" line for your system, if it uses a Linux device name and if it's incorrect.

---

### Post by rramesh on 2010-03-12
In saw in another thread for that I could simple execute "sudo update-grub"  What does this command do?
(I usually edit menu.lst as use to be debian proper that used GRUB legacy) Now there is too much complication in everything. The distros are becoming more like windows. Everything is abstracted with menus and buttons that you no longer can fix things unless you are already a guru.

---

### Post by srs5694 on 2010-03-12
GRUB2, at least as delivered with Ubuntu, includes a number of scripts in /etc/grub.d that are supposed to detect your kernels and non-Linux OSes and create GRUB2 configurations for them. The update-grub command runs these scripts to update the GRUB2 settings, and it may in fact fix the problem -- or it might not.

Personally, I tend to agree with you about some of these advanced "the computer knows better than the user" features. You might look into Debian, Slackware, or Gentoo, which tend to assume more Linux-knowledgeable users.

---

