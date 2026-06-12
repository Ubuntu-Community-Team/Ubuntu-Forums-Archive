---
title: "how to load ubuntu from hiren boot cd or grub4dos"
date: 2012-07-24
forum: General Help
---

### Post by nazar2nirvana on 2012-07-24
how can i load ubuntu 12.04 from grub4dos 0.4 ///or hiren boot cd which i have installed or kept in my 1st partition so as i boot my pc it shows hiren menu.. but there is no option to load ubuntu... only there is option for winodws 7...


previously it was like (i used to use this to modify menu.lst of hirenboot cd to load ubuntu which is installed in my 3rd partition)

fallback 5
find --set-root /sbin/init
savedefault --wait=2
configfile /boot/grub/menu.lst

now it is not working ///
what is the change ???

ps . i use hiren boot cd coz it provide other dos tools to use as well. so don;t suggest me to like install grub menu of ubuntu  and load ubuntu and windows 7 from it

---

### Post by oldfred on 2012-07-24
I do not know grub4dos settings. Is there some reason for grub4dos? Grub2 boots just about everything.

But menu.lst is from grub legacy or grub 0.97. Grub2 has been used by Ubuntu as the standard since 9.10 and is in Ubuntu at version 1.99. Grub2 was just released to version 2 recently.

Grub2 uses grub.cfg as the menu file.

someone posted this which is using the grub2 file core.img, where x is old style grub count of one less than partition or sda1 is 0:

title ubuntu
root (hd0,x)
rootnoverify
kernel  /boot/grub/core.img
boot

Also using kernel to boot iso:
[http://ubuntuforums.org/showthread.php?t=1946314](http://ubuntuforums.org/showthread.php?t=1946314)

where x is, per grub4dos, one less than the partition number of the ubu partition;

---

