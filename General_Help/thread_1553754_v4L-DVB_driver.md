---
title: "v4L-DVB driver"
date: 2010-08-15
forum: General Help
---

### Post by papershoes on 2010-08-15
I am trying to get my wintv-hvr-1600 working with mythtv on my recently installed Ubuntu 10.04 64 bit. I was using this [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers) guide to get the drivers installed, but get errors after running 'make'

```
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/papershoes/v4l-dvb/v4l/mceusb.o
  LD [M]  /home/papershoes/v4l-dvb/v4l/videodev.o
  CC [M]  /home/papershoes/v4l-dvb/v4l/v4l2-int-device.o
  CC [M]  /home/papershoes/v4l-dvb/v4l/v4l2-compat-ioctl32.o
/home/papershoes/v4l-dvb/v4l/mceusb.c: In function 'mceusb_dev_probe':
/home/papershoes/v4l-dvb/v4l/mceusb.c:923: error: implicit declaration of function 'usb_alloc_coherent'
/home/papershoes/v4l-dvb/v4l/mceusb.c:923: warning: assignment makes pointer from integer without a cast
/home/papershoes/v4l-dvb/v4l/mceusb.c:1003: error: implicit declaration of function 'usb_free_coherent'
make[3]: *** [/home/papershoes/v4l-dvb/v4l/mceusb.o] Error 1
make[3]: *** Waiting for unfinished jobs....
make[2]: *** [_module_/home/papershoes/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/papershoes/v4l-dvb/v4l'
make: *** [all] Error 2
```

Edit: I did modify the .config file to change firedtv=m to firedtv=n

---

### Post by papershoes on 2010-08-16
bump!

Anyone?

---

