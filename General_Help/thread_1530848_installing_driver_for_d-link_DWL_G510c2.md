---
title: "installing driver for d-link DWL G510c2"
date: 2010-07-14
forum: General Help
---

### Post by choooseen on 2010-07-14
hello, i have a prob to install d-link g510c2 driver with RaLink RT2561/RT61 chipset....
root@user:/home/user/Downloads/2010_0412_RT61_Linux_STA_v1.1.2.5/Module# make all
make -C /lib/modules/2.6.32-23-generic/build SUBDIRS=/home/user/Downloads/2010_0412_RT61_Linux_STA_v1.1.2.5/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/user/Downloads/2010_0412_RT61_Linux_STA_v1.1.2.5/Module/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/user/Downloads/2010_0412_RT61_Linux_STA_v1.1.2.5/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [all] Error 2
.. please help...thx

---

