---
title: "Using UNetbootin &amp; Target SD card"
date: 2011-03-11
forum: General Help
---

### Post by Shiseiji on 2011-03-11
Tried a forum search, if I missed a previous thread my apologies. I need to create a bootable SD card for my OLPC XO and am trying to use UNetbootin on my Ubunto system. I have the img on a USB thumb drive and need to now create the bootable SD card. 

I am trying to use Unetbootin and there I can see my USB drive:

/media/PENDRIVE/XtraOrdinary_2010_for_XO-1_Download_Edition.img

So far so good. 

"But" the target only lists devices: 
/dev/sda1
/dev/shm
/dev/sdf1
/dev/sdd1
/dev/sda
/dev/sda2
/dev/sda5
/dev/sdd
/dev/sdf

and I have no idea which one is the SD card.

Ideas? Options on other software?

TIA,

Ron

---

### Post by wilee-nilee on 2011-03-11
Generally I use gparted in the admin part of the menu there is a drop down in the top right corner to see each drive. You can identify the sdX of the SD card and maybe even format it there if needed.

---

### Post by Shiseiji on 2011-03-11
Took care of it figuring out the device! SDD1 was the correct target. Hardest part was figuring out where GParted ended up in my menus. Now Ubootin is hanging, but that's another issue.

Thanks much!

EDIT: Ubootin came back alive and I "think" completed the task. 

Ron

---

