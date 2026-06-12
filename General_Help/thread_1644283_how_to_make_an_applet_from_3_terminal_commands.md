---
title: "how to make an applet from 3 terminal commands ?"
date: 2010-12-13
forum: General Help
---

### Post by doron387 on 2010-12-13
[SOLVED]  
i have just managed to establish wireless connection on my asus 1201n w/ubuntu 10.10/wubi.
every time when i reboot i have to open terminal and type :
sudo su
[password]
modprobe r8192se_pci

and then my wireless works.

is there a way i can create an applet in the top bar of the desktop that will launch it automatically in one click ?

thanks
doron387

---

### Post by lykeion on 2010-12-13
You can add modules to load at bootup by adding them to /etc/modules. To add r8192se_pci do this (once):
```
sudo su
echo r8192se_pci >> /etc/modules
exit
```
Hope it helps.

---

### Post by doron387 on 2010-12-13
works great.
thanks
i wish i would be like you guys..... those who really understand what the code says....
maybe in the next reincarnation....lol

doron387

---

