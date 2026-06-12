---
title: "GRUB won't boot windows xp"
date: 2010-02-15
forum: General Help
---

### Post by bluestar14 on 2010-02-15
this all started when i tried to upgrade to lucid lynx(using update-manager -d). after that everything stopped working, when i booted into windows, it said "grub_"   ( _ was blinking) and wouldn't do anything, when i updated the bootloader from recovery menu, same thing happened,  so i reinstalled back to 9.10, but it is still saying same thing.... i searched online, and all they say was edit the  /boot/grub/menu.lst, but it says the file doesn't exist(when i use cat)

---

### Post by bluestar14 on 2010-02-15
also, the live cd did see the windows partition....

---

### Post by tom4everitt on 2010-02-15
There's no menu.lst on 9.10 and later (because its using grub2 instead of grub). 

Here's a grub2 tutorial:
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

The grub2 equivalent to menu.lst is /boot/grub/grub.cfg.

EDIT: You can run sudo update-grub, and see if it gives you any error messages.

---

### Post by bluestar14 on 2010-02-15
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done
avin@STUDYROOML:~$ 
```

this is the output, no errors....

---

### Post by bluestar14 on 2010-02-15
now how do i find out if windows is on hd0, 1, i am pretty sure it is, but why does that GRUB_ ( _ blinking) come, and why won't it boot windows?????( i need my songs, and my itunes, and all my school stuff, and word, and, you get the point)

---

### Post by jsriz on 2010-02-15
> 
now how do i find out if windows is on hd0


Run sudo fdisk -l
u can tell where the bootable ntfs disk is

> 
( i need my songs, and my itunes, and all my school stuff, and word, and, you get the point) 	  	


 U can access all those from linux rite
if upadte of the grub was the prb jus run the startup repair of windows 
an reinstall the grub with a live cd

---

### Post by bluestar14 on 2010-02-15
so, reinstalling the os didn't downgrade grub? or is here a option somewhere just to install grub....will i have to inst5all ubuntu again?

---

### Post by bluestar14 on 2010-02-15
i did sudo gparted /dev/dsa1, and when i looked at info, it said that there was no mount point, is that why, and if it is, how do i fix it....(i am just confused, cause i can mount it from ubuntu)

---

### Post by bluestar14 on 2010-02-15
but then i saw, it has no support for ntfs partitions, but does that matter(could someone look at these 3 post in a row and just give me one big answer?)

---

### Post by oldfred on 2010-02-15
If you want to see everything at once on how it is booting:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by tom4everitt on 2010-02-16
Reinstalling will probably not help. Your reinstallation upgraded grub, not downgraded. Sometimes there are issues with the new version of grub, i.e grub2.

Basically only partitions that are mounted during boot have an assigned mount point. This is nothing to worry about. 

That gparted doesn't support ntfs only means that it is unable to create/modify ntfs file systems. So this is nothing to worry about either (you can probably install a plugin to give it ntfs-capabilities).

EDIT: and if you follow oldfreds advice, to post the result of that command, it will help us helping you :)

---

### Post by m4tic on 2010-02-16
do ```
sudo update-grub2
```
It will find other os and configure them correctly

---

### Post by bluestar14 on 2010-02-16
i just did a repair on windows, now it works!

---

