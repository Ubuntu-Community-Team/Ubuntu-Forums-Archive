---
title: "NEED HELP!!!! Netbook error 22 Grub"
date: 2009-11-02
forum: General Help
---

### Post by bigladluke on 2009-11-02
I recently like an idiot deleted my ubuntu partitions on my netbook leaving me with Grub error 22 which i have read up on. all of them say the solution is to use the live CD but iv got a netbook so i cant use a cd.
 
Im a bit of a newbie on ubuntu and just dont know what to do, any help would be nice.
 
thanks in advance,
Bigladluke

---

### Post by bigladluke on 2009-11-03
I think im not going to be able to fix this :(

---

### Post by eholly on 2009-11-03
Bigladluke

I use a external CD drive, You can download a .img file and put it on a usb drive. 
You need to re-partition and re-install linux. It will put in a new grub that works.

                E Holly

---

### Post by bigladluke on 2009-11-04
> **eholly said:**
> Bigladluke
 
I use a external CD drive, You can download a .img file and put it on a usb drive. 
You need to re-partition and re-install linux. It will put in a new grub that works.
 
E Holly
 
Thanks Eholly,
are you saying i should buy an external CD Drive?, cause i Have put an image file on a usb but when i try to load it GRUB comes straight up.
 
Thanks for the help i thought i was stuffed :D,
Bigladluke

---

### Post by Dooms_day on 2009-11-04
use the utility called unetbootin-windows  its for windows, but it lets you make a bootable USB drive really esialy, from there you can "sudo grub-install hd0" and then "sudo grub" - from there set the root partition and the rest is with menu.lst

---

### Post by RJ12 on 2009-11-04
Also make sure the BIOS is set to boot from the USB drive

---

### Post by dhughes on 2009-11-04
> **bigladluke said:**
> Thanks Eholly,
are you saying i should buy an external CD Drive?, cause i Have put an image file on a usb but when i try to load it GRUB comes straight up.
 
Thanks for the help i thought i was stuffed :D,
Bigladluke

 Using Ubuntu imagewriter you can put the Ubuntu image on a USB key (probably how you installed it) and select "try without installing" option, then install and use Gparted to wipe the drive and start over by putting a different OS or different distribution of OS on it.

---

### Post by bigladluke on 2009-11-05
> **Dooms_day said:**
> use the utility called unetbootin-windows its for windows, but it lets you make a bootable USB drive really esialy, from there you can "sudo grub-install hd0" and then "sudo grub" - from there set the root partition and the rest is with menu.lst
 
Thanks Dooms_Day but i have downloaded this application but i do not understand what you would like me to do know, if you want me to make USB boot to reinstall linux it doesnt work as GRUB loads when you select the USB
 
Thanks for te help,
bigladluke

---

### Post by bigladluke on 2009-11-05
> **dhughes said:**
> Using Ubuntu imagewriter you can put the Ubuntu image on a USB key (probably how you installed it) and select "try without installing" option, then install and use Gparted to wipe the drive and start over by putting a different OS or different distribution of OS on it.
 
Thanks but this does not work as GRUB loads straight after you select your usb stick, thanks for trying,
Bigladluke

---

### Post by bigladluke on 2009-11-06
Is there no solution :(

---

### Post by bigladluke on 2009-11-10
NO solution then :(

---

