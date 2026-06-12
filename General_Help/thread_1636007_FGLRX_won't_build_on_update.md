---
title: "FGLRX won't build on update"
date: 2010-12-02
forum: General Help
---

### Post by Irony on 2010-12-02
I am attempting to update the from 2.6.32-24 to 2.6.32-26 but this breaks the ATI proprietary driver.

I attempted reinstall of the drivers;

fglrx (2:8.723.1-0ubuntu3)
fglrx-amdcccle (2:8.723.1-0ubuntu3)
fglrx-modaliases (2:8.723.1-0ubuntu3)

but get the following error;

```
Error! Bad return status for module build on kernel: 2.6.32-26-generic (x86_64)
```

The make log shows;

```
DKMS make.log for fglrx-8.723.1 for kernel 2.6.32-26-generic (x86_64)
Thu Dec  2 20:18:58 GMT 2010
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.32-26-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.723.1/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-26-generic'
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.o
In file included from /var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:443:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/drm_proc.h: In function ‘FGLDRM__vma_info’:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/drm_proc.h:497: warning: format ‘%08lx’ expects type ‘long unsigned int’, but argument 5 has type ‘phys_addr_t’
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c: In function ‘KCL_SetPageCache_Array’:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.c:1316: warning: passing argument 1 of ‘KCL_ConvertPageToKernelAddress’ makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/firegl_public.h:325: note: expected ‘void *’ but argument is of type ‘long unsigned int’
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_acpi.o
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_agp.o
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_debug.o
  CC [M]  /var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.o
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.c: In function ‘KCL_IOCTL_AllocUserSpace32’:
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.c:196: error: implicit declaration of function ‘compat_alloc_user_space’
/var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.c:196: warning: return makes pointer from integer without a cast
make[2]: *** [/var/lib/dkms/fglrx/8.723.1/build/2.6.x/kcl_ioctl.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.723.1/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-26-generic'
make: *** [kmod_build] Error 2
build failed with return value 2
```

Tried purging fglrx but this made no difference.

Anyone have the same problem? Anyone with any solutions?

---

### Post by Irony on 2010-12-03
Solved the problem by looking here; [http://ubuntuforums.org/showthread.php?p=9870037](http://ubuntuforums.org/showthread.php?p=9870037)

I updated the kernel as normal then deleted the old kernel and rebooted purged fglrx files also manually deleted /usr/lib/fglrx and /usr/lib32/fglrx and rebooted then downloaded the latest ati drivers; [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Then made some debs; [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and installed them and rebooted and all is okay.

Not sure whether the latest driver is the solution or simply that I deleted the old kernel.

---

