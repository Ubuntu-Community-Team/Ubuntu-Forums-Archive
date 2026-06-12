---
title: "reinstalling windows, while keeping ubuntu"
date: 2010-10-17
forum: General Help
---

### Post by artoop on 2010-10-17
I need to reinstall windows, but it'll wipe GRUB2. I have Ubuntu 10.04 LTS. How can i revert MBR after installing win?

---

### Post by Rubi1200 on 2010-10-17
Welcome to the forums :-)

To reinstall GRUB after installing Windows:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by psycho5 on 2010-10-17
After Windows installation, put in your ubuntu cd, and boot into the live desktop

open up a terminal Applications>Accessories>Terminal

type 

sudo -i
fdisk -l


it will list your disks and partitions, identify your ubuntu partition from there, take note of it. if it's /dev/sda1 for example. 

mount /dev/sda1 /mnt (if your ubuntu is at sda1)
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
umount /mnt
exit

reboot, then you should be good.

---

### Post by ivarn on 2010-10-17
If that's too advanced, login to windows and download auto super grub from [http://download.cnet.com/Auto-Super-Grub-Disk/3000-2094_4-10829335.html?tag=mncol;1](http://download.cnet.com/Auto-Super-Grub-Disk/3000-2094_4-10829335.html?tag=mncol;1)

---

### Post by artoop on 2010-10-18
Thank all for your replies. I've reinstalled windows and have restored GRUB2 successfully.

---

