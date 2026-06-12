---
title: "How to exit X"
date: 2010-05-21
forum: General Help
---

### Post by hblazeviczx6r on 2010-05-21
Just installed Ubuntu 10.04, and X11 does not really work well (on Sony VPCF115FM notebook with Nvidia GT330M GPU). Tried proprietary driver that is provided with Ubuntu, but that crashed X completely.
Reinstalled Ubuntu again and now I want to install the latest beta driver from Nvidia, but to do that I need to exit X11. Tried "init 3" as root (which would work on Fedora) but this does not work. How to do this???

---

### Post by 2hot6ft2 on 2010-05-21
Ctrl+Alt+F2
```
sudo service gdm stop
```
If you are running 64 bit install the driver to the 2.6.32-21 kernel not the -22 kernel.

---

### Post by hblazeviczx6r on 2010-05-23
Thanks.

---

### Post by ahso4271 on 2010-05-23
those keys are not working/cannot switch. would you suggest updating my nvidia drivers?

---

### Post by hblazeviczx6r on 2010-05-23
sudo service gdm stop

is not really working. That is, it stops X and drops me in a shell full screen, but this is absolutely unresponsive. Get a blinking cursor, but it does not let me type anything???

---

