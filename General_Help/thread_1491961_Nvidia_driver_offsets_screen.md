---
title: "Nvidia driver offsets screen"
date: 2010-05-24
forum: General Help
---

### Post by The Switch Blade on 2010-05-24
Sony vaio VPCF11NFX/B and Lucid 10.04.

Without use of the nvidia driver, my screen resolution is "too big" for the monitor.

When using the nvidia driver, the machine boots into low graphics mode and the screen is off center. Specifically, the top right corner is about 1/4 down and left of where it should be.

xvidtune doesn't work for my machine.

---

### Post by wojox on 2010-05-24
Can't you install the driver. then reboot and run in terminal:

```
nvidia-xconfig
```

---

### Post by The Switch Blade on 2010-05-24
And do what, exactly?

---

### Post by The Switch Blade on 2010-05-24
Here's what happens when I try to install the driver:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon May 24 08:18:24 2010
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 195.36.24.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.32-22-generic/build'
-> Kernel output path: '/lib/modules/2.6.32-22-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.32-22-gener
   ic/build SYSOUT=/lib/modules/2.6.32-22-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";    \
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";    \
       echo;                                \
       /bin/false)
   mkdir -p /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.tmp_
   versions ; rm -f /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/
   nv/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.3
   6.24-pkg2/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -Iin
   clude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -include 
   include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-functio
   n-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 
   -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-o
   utgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAM
   E=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mm
   x -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno
   -optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign 
   -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz4922/
   NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type
   -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multi
   char -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare
   -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\
   "195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBU
   ILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /
   tmp/selfgz4922/NVIDIA-Linux-x86_64
   -195.36.24-pkg2/usr/src/nv/.tmp_nv.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195
   .36.24-pkg2/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv.c:14:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/mtrr.h:173,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:161,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv.c:14:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nv.o";
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   nv_gvi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time 
   -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_C
   FI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -m
   no-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-fram
   e-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno
   -pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/t
   mp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv -Wall -Wimplicit
   -
   Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ari
   th -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -
   Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VE
   RSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR
   (s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR
   (nvidia)"  -c -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/
   nv/.tmp_nv_gvi.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/
   nv/nv_gvi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv_gvi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv_gvi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv_gvi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv_gvi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/mtrr.h:173,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:161,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nv_gvi.o";
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  -
   Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -inclu
   de include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -Wno-format-security -fno-delete-null-pointer-che
   cks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-a
   t-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCO
   NFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-
   tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-
   omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-state
   ment -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-s
   tack -I/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv -Wall -
   Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defe
   r-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DN
   VRM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D
   "KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=
   KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg
   2/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2
   /usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/mtrr.h:173,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:161,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nv-vm.o";
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   os-agp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time 
   -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_C
   FI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -m
   no-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-fram
   e-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno
   -pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/t
   mp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werr
   or -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast
   -qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195.36.2
   4\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASEN
   AME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/s
   elfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.tmp_os-agp.o /tmp/s
   elfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/mtrr.h:173,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:161,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/os-agp.o";
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/inc
   lude  -Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include
   -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wund
   ef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werr
   or-implicit-function-declaration -Wno-format-security -fno-delete-null-point
   er-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-
   time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG
   _AS_CFI_SIGN
   AL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse 
   -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-point
   er -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointe
   r-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/self
   gz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -W
   no-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign
   -compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION
   _STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#
   s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_ST
   R(nvidia)"  -c -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src
   /nv/.tmp_os-interface.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/u
   sr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/mtrr.h:173,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:161,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/os-interface.o";
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   os-registry.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/incl
   ude  -Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include 
   -include include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wund
   ef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werr
   or-implicit-function-declaration -Wno-format-security -fno-delete-null-point
   er-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-
   time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG
   _AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tabl
   es -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit
   -frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement
   -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack 
   -I/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv -Wall -Wimpl
   icit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoint
   er-arith -Wno-multichar -Werror -mcmodel=kerne
   l -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error 
   -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DE
   BUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os
   _registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4922/NV
   IDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.tmp_os-registry.o /tmp/selfgz49
   22/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-registry.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-registry.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/mtrr.h:173,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:161,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/os-registry.o";
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   nv-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time 
   -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS
   _CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchron
   ous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than
   =1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-
   after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -
   fconserve-stack -I/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src
   /nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpar
   entheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zon
   e -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -
   DMODULE -DNVRM -DNV_VERSION_STRING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBU
   ILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-1
   95.36.24-pkg2/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-1
   95.36.24-pkg2/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-i2c.c:8:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-i2c.c:8:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/mtrr.h:173,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:161,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nv-i2c.o";
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   nvacpi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time 
   -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_C
   FI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -m
   no-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-fram
   e-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno
   -pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack -I/t
   mp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD 
   -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_ST
   RING=\"195.36.24\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" 
   -D"KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)
   "  -c -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.tmp_
   nvacpi.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nvacp
   i.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:27,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2282: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/dma-mapping.h:42,
                    from include/linux/dma-mapping.h:103,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/pci.h:128,
                    from include/linux/pci.h:1126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:95,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nvacpi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:126,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nvacpi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/mtrr.h:173,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-linux.h:161,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     set -e ; perl /usr/src/linux-headers-2.6.32-22-generic/scripts/recordmcoun
   t.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/selfgz
   4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nvacpi.o";
     ld -m elf_x86_64   -r -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg
   2/usr/src/nv/nvidia.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nv-kernel.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/s
   rc/nv/nv.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nv_
   gvi.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nv-vm.o 
   /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/os-agp.o /tmp/
   selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/os-interface.o /tmp
   /selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/os-registry.o /tmp
   /selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nv-i2c.o /tmp/se
   lfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-
   pkg2/usr/src/nv/nvidia.ko;) > /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-
   pkg2/usr/src/nv/modules.order
   make -f /usr/src/linux-headers-2.6.32-22-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-22-generic/Modu
   le.symvers -I /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/
   Module.symvers  -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/sr
   c/nv/Module.symvers -S -w  -s
   WARNING: could not find /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/u
   sr/src/nv/.nv-kernel.o.cmd for /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24
   -pkg2/usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/src/nv/.
   nvidia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/inclu
   de  -Iinclude  -I/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include -
   include include/linux/autoconf.h -Iu
   buntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs
   -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-
   format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno
   -red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstac
   k-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign
   -compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3d
   now -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-c
   alls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflo
   w -fno-dwarf2-cfi-asm -fconserve-stack -I/tmp/selfgz4922/NVIDIA-Linux-x86_64
   -195.36.24-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat 
   -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -mcmo
   del=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -W
   no-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"195.36.24\" -UDE
   BUG -U_DEBUG -DNDEBUG  -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUIL
   D_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24
   -pkg2/usr/src/nv/nvidia.mod.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-
   pkg2/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr
   /src/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
     ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.32-22-generic/scripts/mo
   dule-common.lds --build-id -o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-
   pkg2/usr/src/nv/nvidia.ko /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2
   /usr/src/nv/nvidia.o /tmp/selfgz4922/NVIDIA-Linux-x86_64-195.36.24-pkg2/usr/
   src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [   28.485934]  domain 0: span 3,7 level SIBLING
   [   28.485936]   groups: 7 (cpu_power = 589) 3 (cpu_power = 589)
   [   28.485943]   domain 1: span 0-7 level MC
   [   28.485946]    groups: 3,7 (cpu_power = 1178) 0,4 (cpu_power = 1178) 1,5
   (cpu_power = 1178) 2,6 (cpu_power = 1178)
   [   34.937330] eth0: no IPv6 routers present
   [   85.466479] CE: hpet increasing min_delta_ns to 22500 nsec
   [  377.614268] CE: hpet increasing min_delta_ns to 33750 nsec
   [  378.613368] CE: hpet increasing min_delta_ns to 50624 nsec
   [  415.975165] __ratelimit: 9 callbacks suppressed
   [  415.975167] type=1505 audit(1274702953.933:15): 
   operation="profile_replace" pid=3786 name="/usr/lib/cups/backend/cups-pdf"
   [  415.975623] type=1505 audit(1274702953.933:16): 
   operation="profile_replace" pid=3786 name="/usr/sbin/cupsd"
   [  429.070539] type=1505 audit(1274702967.041:17): 
   operation="profile_replace" pid=3884 name="/usr/bin/evince"
   [  429.071086] type=1505 audit(1274702967.041:18): 
   operation="profile_replace" pid=3884 name="/usr/bin/evince-previewer"
   [  429.071469] type=1505 audit(1274702967.041:19): 
   operation="profile_replace" pid=3884 name="/usr/bin/evince-thumbnailer"
   [  939.290854] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 2
   [  983.935257] nvidia: module license 'NVIDIA' taints kernel.
   [  983.935260] Disabling lock debugging due to kernel taint
   [  984.450706] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  984.450713] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  984.450715] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  984.450718] NVRM: device(s).
   [  984.450722] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  984.450725] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  984.450727] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  984.450732] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by jerome1232 on 2010-05-24
What driver are you trying to install? Is that the one from nvidia's site? I wouldn't use it Unless they have a newer driver that you absolutely need. 

Otherwise use ubuntu's packages.

Use apt-get to install nvidia-current, reboot, if your in low graphics mode try running nvidia-xconfig and reboot.

---

### Post by The Switch Blade on 2010-05-24
[IMG]http://img227.imageshack.us/img227/8937/screenshothardwaredrive.png[/IMG]

---

