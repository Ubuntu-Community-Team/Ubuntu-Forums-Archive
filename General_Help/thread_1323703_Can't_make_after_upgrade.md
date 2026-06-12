---
title: "Can't make after upgrade"
date: 2009-11-11
forum: General Help
---

### Post by izackrp on 2009-11-11
Here's my problem
```
izack@nes:~/Desktop/via-xserver-86a-50283_src/DRM/H5DRM_Independent_2.6.27_28$ make
make -C /lib/modules/2.6.31-14-generic/build M=/home/izack/Desktop/via-xserver-86a-50283_src/DRM/H5DRM_Independent_2.6.27_28 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/izack/Desktop/via-xserver-86a-50283_src/DRM/H5DRM_Independent_2.6.27_28/via_chrome9_drv.o
/home/izack/Desktop/via-xserver-86a-50283_src/DRM/H5DRM_Independent_2.6.27_28/via_chrome9_drv.c:220: error: unknown field ‘dri_library_name’ specified in initializer
/home/izack/Desktop/via-xserver-86a-50283_src/DRM/H5DRM_Independent_2.6.27_28/via_chrome9_drv.c:220: warning: initialization from incompatible pointer type
make[2]: *** [/home/izack/Desktop/via-xserver-86a-50283_src/DRM/H5DRM_Independent_2.6.27_28/via_chrome9_drv.o] Error 1
make[1]: *** [_module_/home/izack/Desktop/via-xserver-86a-50283_src/DRM/H5DRM_Independent_2.6.27_28] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'

make: *** [default] Error 2
```So what do dev pack do I need to install?

btw this worked before I updated.

---

### Post by bashphoenux on 2009-11-11
what are you trying to make ?

---

### Post by izackrp on 2009-11-12
I'm not entirely sure... I'm just trying to follow this tutorial to install my via driver.
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

I think I'm installing the libGL library which would explain some of the problems I'm having...

I'm hoping reinstalling the driver would fix my 

X11 error: BadAlloc (insufficient resources for operation)

problem when I try to run games or glxgears.

---

