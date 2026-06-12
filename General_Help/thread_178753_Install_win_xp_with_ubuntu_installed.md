---
title: "Install win xp with ubuntu installed"
date: 2006-05-18
forum: General Help
---

### Post by Gosta on 2006-05-18
I have a computer with ubuntu and Win2000, and with Grub I can choose which one to start. Now I need win xp on that mashine too. How do I do that, without destroying the other operating systems? Will win xp overwrite Grub?

---

### Post by infoburner on 2006-05-18
the first thing i would do is download gparted. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php).

gparted is a live cd image that will allow you to resize partitions on your hard drive. use gparted to make some space in a primary partition for winxp.

windows xp should ask you if you want it to write it's own master boot record at some point during the install. dont. after you have successfully installed windows xp, you can then boot into ubuntu and reconfigure grub. i think re-configuring grub is as easy as 

sudo dpkg-reconfigure grub

---

### Post by sciyoshi on 2006-05-18
Actually, when you install Windows XP it doesn't ask you, it automatically overwrites the MBR. You have two options: either you can use the Windows bootloader and set it up (using msconfig, see [http://jaeger.morpheus.net/linux/ntldr.php)](http://jaeger.morpheus.net/linux/ntldr.php)), or after installing you can boot into a live cd, add Windows to your /boot/grub/menu.lst and re-run grub-install from the Ubuntu partition. Infoburner, I think reconfiguring grub only detects other operating systems on install... But yea, good luck :-)

Samuel

---

