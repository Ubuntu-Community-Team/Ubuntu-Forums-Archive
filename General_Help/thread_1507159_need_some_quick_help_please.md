---
title: "need some quick help please"
date: 2010-06-11
forum: General Help
---

### Post by linuxnoob420 on 2010-06-11
hey folk jus messing with the plymouth themes in ubuntu 10.04 had to use this command 
to delay loading of the splash

echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash


just wondering how to undo it so startup can run at normal speed can someone please tell me what to do or type:-)
 
Thanks in advance

---

### Post by dino99 on 2010-06-11
remove splash (after quiet):

gksudo gedit /etc/default/grub

then 

sudo update-grub

[COLOR="Red"]or [/COLOR]

gksudo gedit /etc/initramfs-tools/conf.d/splash

and remove framebuffer=y or set it to n instead y

then

sudo update-grub

---

### Post by linuxnoob420 on 2010-06-11
okay well im not doing any thing with grub it has more to do with the startup after grub here is a link to the web page i was at so you have a better idea of what i was doing

if the link don't work copy and paste  [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

grub seems to be working fine :-)

---

### Post by dino99 on 2010-06-11
as you might know, plymouth and splash are very closed, and as splash is incerted into /etc/default/grub, so i guess you can see the relation :lolflag: or you have not understood why you have added framebuffer

---

### Post by linuxnoob420 on 2010-06-11
Okay fixed it very easy dam easy just change command  
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
to
echo FRAMEBUFFER=n >>/etc/initramfs-tools/conf.d/splash

back to normal startup
thanks i figured after having bigger problem before haveing to fix it on a limb should come here before going further so thanks everything is back to normal :-)

---

