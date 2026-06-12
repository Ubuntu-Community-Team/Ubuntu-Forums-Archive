---
title: "Grub2 not updated with sudo update-grub"
date: 2010-01-13
forum: General Help
---

### Post by johnrine on 2010-01-13
I am using ubuntu 9.10. Grub 2 is not being updated with the general updates for ubuntu. I currently have four kernels in the boot directory 2.6.31-14, -15, -16, -17.
All the kernels are referenced in menu.1st but grub.cfg has stopped updating with the -14 and -15 kernel. Running sudo update-grub finds the kernels, updates menu.1st, but grub.cfg is not updated and the boot menu I am presented with at boot only list -14 and -15 kernel options to boot. I tried inserting the information on -17 taken from menu.1st into /etc/grub.d/*40_custom and then run sudo update-grub and still only kernels -14 and -15 are available in the boot menu.
If it is of any help, all of the files in the /boot/grub directory have the date Nov 29 and time stamp 13:45 which is the same as the -15 kernel Nov 29 13:46, the last time that grub2 was correctly updated with latest kernel and the updated files from the routine update.

I am at a loss as to why grub2 will not update with the new kernels?

---

### Post by john newbuntu on 2010-01-13
Do you use startup manager? It might have options to restrict the number of kernels displayed.

---

### Post by johnrine on 2010-01-13
There is not a startup manager available yet for grub2

---

### Post by Leppie on 2010-01-13
try the following command:
```
sudo grub-mkconfig
```

---

### Post by johnrine on 2010-01-13
I tried sudo grub-mkconfig to rewrite the grub.cfg file. It went through the script. When I rebooted the boot menu only showed the old -14 and -15 kernels to boot.
I looked at the /boot/grub folder and nothing was updated in the folder except the file grubenv.
grub.cfg is still the old version with the kernels -15 and -14 even through sudo grub-mkconfig generated a new file it was not written to the /boot/grub folder

---

### Post by Leppie on 2010-01-13
seems like you're using grub legacy and not grub2.
if you want to use grub2, follow these steps:
```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc grub-common
```
you will be presented with some dpkg configuration screens to set up grub2.

---

### Post by johnrine on 2010-01-13
I am using grub2
I tried grub-mkconfig -o /boot/grub/grub.cfg to rewrite this file then
grub-install
grub2 was updated but for some reason did not pick up the windows xp partition
So I was not able to boot into Windows - I need to use Windows for my work
So I was force to fdisk /mbr to restore my boot to Windows
So now  I am on hold with ubuntu to reinstall or repair grub2 for a new dual boot

Just my own thought - grub sure worked well and was easy to use - It would have been good for the ubuntu team to give us a choice of a boot loader not ready for prime time aka grub2 or to use a stable release grub. Grub was always easy to work with. Grub2 seems to be needlessly complicated especially for a simple dual boot installation.:(

John

---

