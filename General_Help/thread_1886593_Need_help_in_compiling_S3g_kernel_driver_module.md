---
title: "Need help in compiling S3g kernel driver module"
date: 2011-11-25
forum: General Help
---

### Post by jonatutu on 2011-11-25
Because the pre-compile kernel module is not included with the installation package. 
We can compile our own kernel module 
Installation guide from s3chrome graphics.
[http://drivers.s3graphics.com/en/download/drivers/chrome4x-Linux/Readme.txt](http://drivers.s3graphics.com/en/download/drivers/chrome4x-Linux/Readme.txt)

I tried compiling but I have a error. I read alot of guide on how to compile but still dont work.
This was the error 
waikit@ubuntu:~$ cd /home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g waikit@ubuntu:~/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g$ make
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.38-12-generic/build  SUBDIRS=`pwd` S3GSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-12-generic'
  CC [M]  /home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_bufs.o
  CC [M]  /home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_context.o
  CC [M]  /home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.o
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.c: In function ‘s3g_get_busid’:
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.c:196:14: warning: statement with no effect
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.c: In function ‘s3g_ioctl_get_display_info’:
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.c:233:10: warning: unused variable ‘found’
  CC [M]  /home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_lock.o
  CC [M]  /home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.o
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:37:1: warning: missing braces around initializer
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:37:1: warning: (near initialization for ‘s3g_servers[0]’)
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c: In function ‘fill_in_dev’:
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:45:11: warning: unused variable ‘romaddr’
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:44:18: warning: unused variable ‘romsave2’
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:43:18: warning: unused variable ‘romsave’
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c: At top level:
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:315:5: error: unknown field ‘ioctl’ specified in initializer
/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:315:5: warning: initialization from incompatible pointer type
make[2]: *** [/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.o] Error 1
make[1]: *** [_module_/home/waikit/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-12-generic'
make: *** [modules] Error 2

---

