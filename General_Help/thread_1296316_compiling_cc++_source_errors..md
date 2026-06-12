---
title: "compiling c/c++ source errors."
date: 2009-10-20
forum: General Help
---

### Post by henkgeb on 2009-10-20
hi,
 
I'm trying to intall my new x-fi xtreme audio soundcard on my ubuntu studio 64 machine.
While compiling, I got some errors like error 1, error 2 and ´size of array ‘type name’ is negative¨. I've already installed all source files of gcc and g++, but it doesn't matter. I compile it exactly the way described in the readme file.
I get the following output:
 
henk@henk-desktop:~/Bureaublad/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for henk:
make -C /lib/modules/2.6.24-24-rt/build M=/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-rt'
  LD      /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/xfi.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctatc.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctpcm.o
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctmixer.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_src_rsc’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_srcimp_rsc’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_add’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_delete’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_mgr_destroy’:
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: error: size of array ‘type name’ is negative
/home/henk/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
make[2]: *** [/home/william/Bureaublad/XFiDrv_Linux_Public_US_1.00/ctsrc.o] Error 1
make[1]: *** [_module_/home/william/Bureaublad/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-rt'
make: *** [all] Error 2
henk@henk-desktop:~/Bureaublad/XFiDrv_Linux_Public_US_1.00$
 
Who can tell me what I'm doing wrong? help me, please...
thanks for reading.
 
my specs: amd athlon x2 4050e,
ubuntu studio 8.04, kernel 2.6.24-24-rt, GNOME 2.22.3

---

