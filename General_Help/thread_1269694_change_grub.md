---
title: "change grub"
date: 2009-09-18
forum: General Help
---

### Post by AmerNewbieInDE on 2009-09-18
i have a little problem, i moved my ubuntu install to a new hd on my pc. it is now hd1,0 when i boot my pc, it wont boot windows or linux, i tried to repair grub and set it to hd0 but it doesnt work. in order for my pc to boot i have to tell the bios to boot from my second hard drive and it works for ubuntu, but not windows, even though it gives me windows options... how do i get grub back into the mbr on my first drive, so it boots to windows also...

---

### Post by Liolikas on 2009-09-18
Move (also just in case keep other copy of) /boot to old hdd to only ~200Mb size partition. This may make kernel update harder but Ubuntu will be more secure and windows will boot. More details:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Don1500 on 2009-09-18
How do you have Ubuntu set up (one partition for "/" and a separate "/home" partition? or all Ubuntu on one partition?)

You can try reinstalling Ubuntu where you want, but don't format the drive. This should give you a new grub in the correct place. (Careful, you may lose your data, so back it up)
I am set up with two partitions to hold Ubuntu so I can reinstall and reformat the "/" partition, not reformat my "/home" partition, and most of my stuff is still there. The grub is refreshed and everything works fine. Most of the Grub utilities that I have found can only go back one level, if you screwed up once and then didn't refresh right you can't use the utility to get you back. If you're useing Grub V.2 the utilities (Super Grub) are not applicable anyway. (Grub V.2 is only standard on the upcomming Karmic load, 9.10).

---

### Post by ajgreeny on 2009-09-18
Just post the output of ```
sudo fdisk -l
``` back here and also the menu part from the output (at the bottom) of ```
cat /boot/grub/menu.lst
``` and I should think we can get the system to boot again.

It's not absolutely needed but the output of ```
sudo blkid
``` would also be useful as the default of menu.lst is to use UUIDs.

---

