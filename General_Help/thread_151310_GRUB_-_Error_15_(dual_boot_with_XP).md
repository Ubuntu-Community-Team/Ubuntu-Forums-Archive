---
title: "GRUB - Error 15 (dual boot with XP)"
date: 2006-03-27
forum: General Help
---

### Post by chriszanf on 2006-03-27
Hello all,

I have spent pretty much most of my day trying to install ubuntu with no success at all.

I have my machine set up to dual boot with XP but Im trying to keep the OS's seperate by not installing GRUB to the MBR on my hda but I keep repeatedly getting an "Error 15".

I have run through the install procedure correctly (to teh best of my knowledge) and have repeatedly checked on threads here if I am installing GRUB correctly.

My HDD format is as follows:

hda 160Gb
#1    25Gb    XP Boot
#2    60Gb    NTFS partition [logical]
#3    66Gb    NTFS partition [logical]

hdb  80Gb
#1    23Gb    Primary  ext3  /
#4    250Mb  Primary  ext3  /boot
#5    1.1Gb   Logical  swap /swap
#2    55Gb    Primary  [empty - unformatted]

I have run through the install process and when it gets to installing GRUB, I choose to place it on hdb4 and yet it keeps returning the error 15.

I tried running through an install as "linux acpi=off" and GRUB installed and booted to the choice screen but failed to see ubuntu installation to finish the install process.

Ive been trying this since about 5pm (its now 11pm) and Ive pretty much lost all hope of getting ubuntu installed without GRUB being on the MBR. 

Can anyone offer any advice or tips to get this to work?

Many thanks

---

