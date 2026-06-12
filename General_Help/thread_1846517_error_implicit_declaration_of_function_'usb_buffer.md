---
title: "error: implicit declaration of function 'usb_buffer_free'"
date: 2011-09-19
forum: General Help
---

### Post by mswamy78 on 2011-09-19
I am finding following implicit declaration issue(below) when I use linux-
  2.6.35.3 header files. Please let me know how to resolve this issue.
   
  Regards,
  Swamy
  

$ CROSS_COMPILE=/opt/freescale/usr/local/gcc-4.4.4-glibc-
  2.11.1-multilib-1.0/arm-fsl-linux-gnueabi/bin/arm-none-linux-
  gnueabi- ARCH=arm make
   
  make -C /home/lucid/ltib/rpm/BUILD/linux-2.6.35.3
  SUBDIRS=/home/Research/Tomtom/ttviewer/uvcvideo-2.6.32
  modules
  make[1]: Entering directory `/home/lucid/ltib/rpm/BUILD/linux-
  2.6.35.3'
  CC [M] /home/Research/Tomtom/ttviewer/uvcvideo-
  2.6.32/uvc_video.o
  /home/Research/Tomtom/ttviewer/uvcvideo-2.6.32/uvc_video.c:
  In function 'uvc_free_urb_buffers':
  /home/Research/Tomtom/ttviewer/uvcvideo-
  2.6.32/uvc_video.c:737: error: implicit declaration of function 'usb_buffer_free'
  /home/Research/Tomtom/ttviewer/uvcvideo-2.6.32/uvc_video.c:
  In function 'uvc_alloc_urb_buffers':
  /home/Research/Tomtom/ttviewer/uvcvideo-
  2.6.32/uvc_video.c:777: error: implicit declaration of function 'usb_buffer_alloc'
  /home/Research/Tomtom/ttviewer/uvcvideo-
  2.6.32/uvc_video.c:779: warning: assignment makes pointer from integer without a cast
  make[2]: *** [/home/Research/Tomtom/ttviewer/uvcvideo-
  2.6.32/uvc_video.o] Error 1
  make[1]: ***
  [_module_/home/Research/Tomtom/ttviewer/uvcvideo-2.6.32]
  Error 2
  make[1]: Leaving directory `/home/lucid/ltib/rpm/BUILD/linux-
  2.6.35.3'
  make: *** [default] Error 2

---

### Post by raja.genupula on 2011-09-19
[http://ubuntuforums.org/showthread.php?t=1444746&page=8](http://ubuntuforums.org/showthread.php?t=1444746&page=8)

hey go with this

---

