---
title: "Compiling Sound Blaster X-fi driver"
date: 2011-07-06
forum: General Help
---

### Post by Packetbomb on 2011-07-06
* Ubuntu 10.04 LTS *

make

> make -C /lib/modules/2.6.32-32-generic/build M=/home/n/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-32-generic'
  CC [M]  /home/n/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/n/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/n/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/n/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/n/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/n/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/n/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
make: *** [all] Error 2

Why?

---

