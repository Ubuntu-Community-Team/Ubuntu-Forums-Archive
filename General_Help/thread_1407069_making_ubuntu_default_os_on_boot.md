---
title: "making ubuntu default os on boot"
date: 2010-02-14
forum: General Help
---

### Post by northwestuntu on 2010-02-14
i recently installed crunchbang to try it out, but it made it the default os on boot.  how do i make ubuntu the default again?

---

### Post by Satoru-san on 2010-02-14
```
sudo nano /etc/defaults/grub
sudo update-grub
```

put ubuntu at the top.

---

### Post by northwestuntu on 2010-02-14
should i do this from ubuntu or crunchbang or does it matter?

---

### Post by Satoru-san on 2010-02-14
I would do it from the operating system that installed grub ;)

So if that is ubuntu, then yes, do that, if it is not ubuntu, then You are asking in the wrong forum as even something like grub is VERY different on different platforms.

---

### Post by lidex on 2010-02-14
If crunchbang is default that means it's bootloader overwrote ubuntu's. That means you either edit from there - crunchbang - or re-install grub from ubuntu liveCD.

---

### Post by Julita on 2010-02-14
In crunchbang, type the following command in the terminal
```
 sudo gedit /boot/grub/menu.lst
``` instead of gedit use any other app, nano, for example. You can change the boot sequence by changing installed OSs order.

---

### Post by Satoru-san on 2010-02-14
.

---

### Post by northwestuntu on 2010-02-15
> **Julita said:**
> In crunchbang, type the following command in the terminal
```
 sudo gedit /boot/grub/menu.lst
``` instead of gedit use any other app, nano, for example. You can change the boot sequence by changing installed OSs order.

i couldnt figure out how to change the boot order.  nothing really clear on what to do in there?  is there something i should be looking for?

---

### Post by oldfred on 2010-02-15
If you want ubuntu as the default you should just reinstall grub. Was your ubuntu 9.10 clean install with grub2 or an upgrade or older system with grub legacy (0.97).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you want help on old grub's menu.lst

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by northwestuntu on 2010-02-15
thanks

---

