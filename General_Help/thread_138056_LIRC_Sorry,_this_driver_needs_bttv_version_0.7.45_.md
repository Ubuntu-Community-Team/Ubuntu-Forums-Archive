---
title: "LIRC: Sorry, this driver needs bttv version 0.7.45 or higher."
date: 2006-03-01
forum: General Help
---

### Post by i-mehl on 2006-03-01
I always get this error, when i compile LIRC

Sorry, this dri ver needs bttv version 0.7.45 or higher. If you are using the bttv package, copy it to the kernel

by lirc_gpio

I tried different versions of lirc, and also different kernels, and the tools module-assistant .... but always this error

---

### Post by ollie98 on 2006-03-21
I am getting the same error.

Any suggestions as to what I need to do?

---

### Post by d0d0 on 2006-05-24
anyone ?

---

### Post by d0d0 on 2006-05-25
I finally found out how to get through this problem. Hope it helps some people out there :) !

Anway, I followed this post : [http://www.ubuntuforums.org/showthread.php?t=30612](http://www.ubuntuforums.org/showthread.php?t=30612)

I'll just continue from step #10 (before compiling lirc with ./setup.sh, make.....)

1. Download the bttv driver  [here]("http://dl.bytesex.org/releases/video4linux/bttv-0.9.15.tar.gz") or at this address : [http://linux.bytesex.org/v4l2/bttv.html]("http://linux.bytesex.org/v4l2/bttv.html")

2. Decompress the files in your /usr/src/linux/drivers/video directory.

```
sudo tar xvjf bttv-0.9.15.tar.gz
```
```
cd bttv-0.9.15
```
```
sudo cp * /usr/src/linux/drivers/video
```

Then go back to your lirc directory and do the setup, make.... and all the rest.

Hope it helps some of you out there !

---

### Post by gosh on 2006-12-06
I keep getting this output of sudo make:

```
jos@mediacenter:/usr/src/lirc-0.8.0$ sudo make
make  all-recursive
make[1]: Entering directory `/usr/src/lirc-0.8.0'
Making all in drivers
make[2]: Entering directory `/usr/src/lirc-0.8.0/drivers'
Making all in lirc_dev
make[3]: Entering directory `/usr/src/lirc-0.8.0/drivers/lirc_dev'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/lirc-0.8.0/drivers/lirc_dev'
Making all in lirc_gpio
make[3]: Entering directory `/usr/src/lirc-0.8.0/drivers/lirc_gpio'
Makefile:8: **************************************************
Makefile:8: *** Makefile trick not undone, trying to recover *
Makefile:8: **************************************************
mv Makefile.automake Makefile
make all
make[4]: Entering directory `/usr/src/lirc-0.8.0/drivers/lirc_gpio'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.17-10-generic/build/ SUBDIRS=/usr/src/lirc-0.8.0/drivers/lirc_gpio modules \
                KBUILD_VERBOSE=1
make[5]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
mkdir -p /usr/src/lirc-0.8.0/drivers/lirc_gpio/.tmp_versions
rm -f /usr/src/lirc-0.8.0/drivers/lirc_gpio/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/src/lirc-0.8.0/drivers/lirc_gpio
  gcc -m32 -Wp,-MD,/usr/src/lirc-0.8.0/drivers/lirc_gpio/.lirc_gpio.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/src/lirc-0.8.0/drivers/lirc_gpio/../.. -I/lib/modules/2.6.17-10-generic/build//include/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_gpio)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_gpio)" -c -o /usr/src/lirc-0.8.0/drivers/lirc_gpio/.tmp_lirc_gpio.o /usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:52:41: error: ../drivers/media/video/bttv.h: No such file or directory
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:53:42: error: ../drivers/media/video/bttvp.h: No such file or directory
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:56:5: warning: "BTTV_VERSION_CODE" is not defined
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:57:2: error: #error "*******************************************************"
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:58:2: error: #error " Sorry, this driver needs bttv version 0.7.45 or       "
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:59:2: error: #error " higher. If you are using the bttv package, copy it to "
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:60:2: error: #error " the kernel                                            "
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:61:2: error: #error "*******************************************************"
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:71: error: ‘BTTV_BOARD_UNKNOWN’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:98: error: ‘BTTV_BOARD_PXELVWPLTVPAK’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:99: error: ‘BTTV_BOARD_PXELVWPLTVPRO’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:100: error: ‘BTTV_BOARD_PV_BT878P_9B’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:101: error: ‘BTTV_BOARD_PV_BT878P_PLUS’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:102: error: ‘BTTV_BOARD_AVERMEDIA’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:103: error: ‘BTTV_BOARD_AVPHONE98’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:104: error: ‘BTTV_BOARD_AVERMEDIA98’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:112: error: ‘BTTV_BOARD_CHRONOS_VS2’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:115: error: ‘BTTV_BOARD_MIRO’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:116: error: ‘BTTV_BOARD_DYNALINK’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:117: error: ‘BTTV_BOARD_WINVIEW_601’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:122: error: ‘BTTV_BOARD_MAGICTVIEW061’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:123: error: ‘BTTV_BOARD_MAGICTVIEW063’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:124: error: ‘BTTV_BOARD_PHOEBE_TVMAS’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:130: error: ‘BTTV_BOARD_FLYVIDEO’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:131: error: ‘BTTV_BOARD_FLYVIDEO_98’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:132: error: ‘BTTV_BOARD_TYPHOON_TVIEW’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:142: error: ‘BTTV_BOARD_WINFAST2000’ undeclared here (not in a function)
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c: In function ‘build_key’:
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:193: warning: implicit declaration of function ‘bttv_write_gpio’
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:197: warning: implicit declaration of function ‘bttv_read_gpio’
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c: In function ‘get_queue’:
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:355: warning: implicit declaration of function ‘bttv_get_gpio_queue’
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:355: warning: return makes pointer from integer without a cast
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c: In function ‘gpio_remote_init’:
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:405: warning: implicit declaration of function ‘bttv_gpio_enable’
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c: In function ‘init_module’:
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:467: warning: implicit declaration of function ‘bttv_get_cardinfo’
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:474: warning: comparison between pointer and integer
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:496: warning: comparison between pointer and integer
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:497: warning: assignment makes integer from pointer without a cast
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:499: warning: comparison between pointer and integer
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:500: warning: assignment makes integer from pointer without a cast
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:502: warning: comparison between pointer and integer
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:503: warning: assignment makes integer from pointer without a cast
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:505: warning: comparison between pointer and integer
/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.c:506: warning: assignment makes integer from pointer without a cast
make[6]: *** [/usr/src/lirc-0.8.0/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[5]: *** [_module_/usr/src/lirc-0.8.0/drivers/lirc_gpio] Error 2
make[5]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[4]: *** [lirc_gpio.o] Error 2
make[4]: Leaving directory `/usr/src/lirc-0.8.0/drivers/lirc_gpio'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.0/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.8.0/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.0'
make: *** [all] Error 2

```

---

