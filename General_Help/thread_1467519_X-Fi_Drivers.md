---
title: "X-Fi Drivers"
date: 2010-04-30
forum: General Help
---

### Post by Nostigex on 2010-04-30
Having problems installing the drivers for my x-fi xtrememusic on Ubuntu 10.04. I'm a first-time Linux user.

From the terminal:

> 
root@GECKO:/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00# make
make -C /lib/modules/2.6.32-21-generic/build M=/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  LD      /home/erik/Desktop/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/erik/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [all] Error 2
root@GECKO:/home/erik/Desktop/XFiDrv_Linux_Public_US_1.00# make install
Copy module files...
cp: cannot stat `ctxfi.ko': No such file or directory
make: *** [install] Error 1
Help?

---

### Post by The_true_power on 2010-05-01
Hello Erik.

First of all, i had the exact same problem as you 10 minutes ago.

I also use a Xtreme Music card, with Lucid Lynx x64.

You don't actually need to install the driver, because it's working natively. 
I was thinking it was needed for 5.1 sound, but it wasn't. 
It all works natively. 

So why would you want to install the driver ?

---

### Post by Nostigex on 2010-05-01
It's odd, because my audio works in VLC Media Player, but not in Amarok.

---

