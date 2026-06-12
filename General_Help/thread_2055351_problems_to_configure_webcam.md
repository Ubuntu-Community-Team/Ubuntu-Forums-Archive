---
title: "problems to configure webcam"
date: 2012-09-09
forum: General Help
---

### Post by esbrinartot on 2012-09-09
I have ubuntu 11.04. My webcam works but the image that I get is so dark. So the webcam is not functional and each time i need to use the webcam I have to boot with windows.

I guess the problem is with the drivers. So I tried next:

OS: Ubuntu 11.04 64 bits
Webcam:  ID 0c45:627b Microdia PC Camera (SN9C201 + OV7660)
I download the drivers:
git clone [http://repo.or.cz/r/microdia.git](http://repo.or.cz/r/microdia.git)
cd microdia
make
After make I obtain next error:

joan@joan-P4M900T-M2:~/microdia$ make
make -C /lib/modules/2.6.38-15-generic/build SUBDIRS=/home/joan/microdia modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.38-15-generic'
  CC [M]  /home/joan/microdia/sn9c20x-usb.o
  CC [M]  /home/joan/microdia/sn9c20x-v4l2.o
  CC [M]  /home/joan/microdia/sn9c20x-sysfs.o
  CC [M]  /home/joan/microdia/sn9c20x-dev.o
  CC [M]  /home/joan/microdia/sn9c20x-queue.o
/home/joan/microdia/sn9c20x-queue.c:77:28: fatal error: linux/videodev.h: No existe el fichero o el directorio
compilation terminated.
make[2]: *** [/home/joan/microdia/sn9c20x-queue.o] Error 1
make[1]: *** [_module_/home/joan/microdia] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.38-15-generic'
make: *** [driver] Error 2

What I should do to compile this driver? 
Is the the driver that I need already included in the kernel?
Do I install the correct driver?

I need help mates

---

