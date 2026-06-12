---
title: "GRUB overwritten by windows?"
date: 2006-04-19
forum: General Help
---

### Post by robek on 2006-04-19
Hi there,
I recently installed Ubuntu as a second system together with XP, it all worked fine -  first it showed GRUB menu and then windows one (I have win98 installed as well). after accidentaly booting computer from winXP's installation cd, GRUB menu has disappeared and it goes straight away to the windows booting menu.

Is there a way to get it working again without having to reinstall ubuntu?

---

### Post by kaamos on 2006-04-19
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

### Post by gogi on 2006-04-19
[QUOTE=robek]... Is there a way to get it working again without having to reinstall ubuntu?[/QUOTE]

Sure! It's easy... First you have to boot with a Linux-CD which contains an installed Grub program (e.g. Knoppix). I don't know if the Ubuntu-Install-CD provide the Grub program. If it does just boot the Ubuntu-Install-CD and change from the installation-menu to another console with:> Ctrl+Alt+F2

Mount your partition of your ubuntu-installation. E.g. mount /dev/hdaX /mnt . Be sure to replace X with your correct partition-number!

Change the root directory:```
sudo chroot /mnt
```

Start grub:```
sudo grub
```

Enter the following commands:```
root (hd0,1)
```

This means first disk second partition (hda2). For hdb3 use root (hd1,2).```
setup (hd0)
```Be sure to use the right disk. See above.```
quit
```

And then reboot!

---

### Post by njzillest on 2006-04-19
.. or you can just boot into the install disk.. and skip the whole installation.. and reinstall the grub (thats what i did with XP) 

i put mine in the MBR... its not that hard.. but you may expeirance problems getting to the grub installer before partitionaing your disks and reisntallling windows..


DO NOT FORMAT YOUR DISK OR REINSTALL EVERYTHING (hit back when you get up to the partition tables)

---

