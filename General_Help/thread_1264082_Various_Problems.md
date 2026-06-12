---
title: "Various Problems"
date: 2009-09-11
forum: General Help
---

### Post by Nate8nate on 2009-09-11
After logging into my computer yesterday, Compiz was giving me a black screen.

I tried to do alt-F2 "metacity --replace", but after Compiz somehow crashed I learned that alt-F2 doesn't bring up the run window anymore.  After some research, I found Compiz was causing the black screen because of driver issues, so I tried reinstalling the driver through Jockey.  After a restart it a blank console with a white _ flashing in the upper left.  So, I rebooted again, went into Recovery Mode, and found that the driver failed to install.

I booted into Windows and downloaded the newest Linux driver from Nvidia.  When I try to install it through the root console in Recovery Mode, it says I need gcc 4.3.  I would have this, except I downloaded gcc 4.4 a while ago to run a Blender build built on Fedora 11, which comes with gcc 4.4.

I guess to get started, I would like to know how to down-grade to gcc 4.3.  I tried to do a "apt-get remove gcc-4.4".

---

### Post by Nate8nate on 2009-09-11
Does anyone in this forum know if it's possible to downgrade to gcc 4.3, or would a different section be more appropriate?

---

### Post by Nate8nate on 2009-09-12
I was able to get gcc 4.3 to work after following [THIS]("http://ubuntuforums.org/showthread.php?t=29449").  Now the Nvidia installer says I need the kernel source.  Would anyone know what the package is called or if I can do this without the source?

---

### Post by Nate8nate on 2009-09-12
O.K. Now I figured out how to get the installed to find the source.  It shows the progress bar but tells me it's having trouble with nvidia.ko.  Would anyone know how to fix this?

---

### Post by Nate8nate on 2009-09-12
Here's the log file from the installer.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Sep 12 18:09:22 2009
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
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-headers-2.6.31-10-generic
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 185.18.36.
-> There appears to already be a driver installed on your system (version: 180.
   44).  As part of installing this driver (version: 185.18.36), the existing d
   river will be uninstalled.  Are you sure you want to continue? ('no' will ab
   ort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-2.6.31-10-generic' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.31-10-generic'
-> Kernel output path: '/usr/src/linux-headers-2.6.31-10-generic'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux-headers-2.6.3
   1-10-generic SYSOUT=/usr/src/linux-headers-2.6.31-10-generic'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux-headers-2.6.31-10-generic SUB
   DIRS=/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.3
   6-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.4/include  -Iinclude
    -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include includ
   e/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -
   m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=
   2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-pro
   tector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwin
   d-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-omit-frame-pointer -fno
   -optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno
   -strict-overflow -I/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-comp
   are -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRI
   NG=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D
   "KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD
   _STR(nvidia)"  -c -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src
   /nv/.tmp_nv.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv.
   c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.4/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -Wno-format-security -fno-delete-null-pointer-checks -
   O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-bound
   ary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack
   -protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-u
   nwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-omit-frame-pointer 
   -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign 
   -fno-strict-overflow -I/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/s
   rc/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wp
   arentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -
   MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DN
   V_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_
   STR(nvidia)"  -c -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/
   nv/.tmp_nv-vm.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/n
   v-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.4/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstac
   k-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-omit-frame-pointer
   -fno-optimize-sibling-calls -Wdeclarati
   on-after-statement -Wno-pointer-sign -fno-strict-overflow -I/tmp/selfgz2989/
   NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -W
   switch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multich
   ar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__K
   ERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -
   DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2989/NVIDIA-Linux
   -x86-185.18.36-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz2989/NVIDIA-Linux-x8
   6-185.18.36-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.4/include 
   -Iinclude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack
   -b
   oundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fs
   tack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchrono
   us-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-omit-frame-poin
   ter -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-s
   ign -fno-strict-overflow -I/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/u
   sr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSI
   ON_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)
   =#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_
   STR(nvidia)"  -c -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/
   nv/.tmp_os-interface.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/s
   rc/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.4/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack
   -boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -
   fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchro
   nous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-omit-frame-po
   inter -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer
   -sign -fno-strict-overflow -I/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1
   /usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscrip
   ts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -
   Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VE
   RSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR
   (s)=#s" -D"K
   BUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia
   )"  -c -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_os
   -registry.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-re
   gistry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.4/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstac
   k-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-omit-frame-pointer
   -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign 
   -fno-strict-overflow -I/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/
   usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -W
   sign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VER
   SION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(
   s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(
   nvidia)"  -c -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.
   tmp_nv-i2c.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv-i
   2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.4/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstac
   k-protector -fstack-protector-all -pipe -W
   no-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 
   -mno-3dnow -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration
   -after-statement -Wno-pointer-sign -fno-strict-overflow -I/tmp/selfgz2989/NV
   IDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wsw
   itch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar
   -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERN
   EL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DND
   EBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvacpi)"  
   -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz2989/NVIDIA-Linux-x8
   6-185.18.36-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz2989/NVIDIA-Linux-x86-1
   85.18.36-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -m elf_i386   -r -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr
   /src/nv/nvidia.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/
   nv-kernel.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv.o 
   /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-agp.o /tmp/selfgz2989/N
   VIDIA
   -Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.o /tmp/selfgz2989/NVIDIA-L
   inux-x86-185.18.36-pkg1/usr/src/nv/os-registry.o /tmp/selfgz2989/NVIDIA-Linu
   x-x86-185.18.36-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz2989/NVIDIA-Linux-x86-18
   5.18.36-pkg1/usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg
   1/usr/src/nv/nvidia.ko;) > /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/u
   sr/src/nv/modules.order
   make -f /usr/src/linux-headers-2.6.31-10-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.31-10-generic/Modu
   le.symvers -I /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/M
   odule.symvers -S -K /usr/src/linux-headers-2.6.31-10-generic/Module.markers 
   -M /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/Module.markers
   -w  -s
   WARNING: could not find /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.4/include  -
   Iinclude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -inclu
   de include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -Wno-format-security -fno-delete-null-pointer-che
   cks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-
   boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -f
   stack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchron
   ous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -fno-omit-frame-poi
   nter -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-
   sign -fno-strict-overflow -I/tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/
   usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -
   Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-d
   efer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE 
   -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUIL
   D_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=K
   BUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.3
   6-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pk
   g1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -r -m elf_i386  --build-id -o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.3
   6-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/
   usr/src/nv/nvidia.o /tmp/selfgz2989/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/
   nv/nvidia.mod.o
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
   -1 Invalid module format
-> Kernel messages:
   [   12.931979] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112,
   RF2413, RF5413)
   [   12.977164] wlan: 0.9.4
   [   13.016841] ath_pci: 0.9.4
   [   13.556501] EXT3 FS on sda3, internal journal
   [   22.780965] type=1505 audit(1252796799.126:2):
   operation="profile_replace" info="failed to unpack profile"
   name="/usr/bin/evince" pid=1154
   [   22.874083] type=1505 audit(1252796799.218:3):
   operation="profile_replace" info="failed to unpack profile"
   name="/usr/sbin/tcpdump" pid=1156
   [   22.980630] type=1505 audit(1252796799.323:4):
   operation="profile_replace" info="failed to unpack profile"
   name="/usr/share/gdm/guest-session/Xsession" pid=1157
   [   23.150419] type=1505 audit(1252796799.494:5):
   operation="profile_replace" info="failed to unpack profile"
   name="/sbin/dhclient3" pid=1158
   [   23.512740] type=1505 audit(1252796799.855:6):
   operation="profile_replace" info="failed to unpack profile"
   name="/usr/lib/cups/backend/cups-pdf" pid=1159
   [   46.085420] vboxdrv: Trying to deactivate the NMI watchdog permanently...
   [   46.085423] vboxdrv: Successfully done.
   [   46.085425] vboxdrv: Found 2 processor cores.
   [   46.085492] vboxdrv: fAsync=1 offMin=0xe346b offMax=0xe346b
   [   46.085540] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is
   'normal'.
   [   46.085542] vboxdrv: Successfully loaded version 3.0.6 (interface
   0x000e0000).
   [   48.895642] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
   [   48.895646] Bluetooth: BNEP filters: protocol multicast
   [   49.004132] Bridge firewalling registered
   [   49.985560] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
   [   49.985780] eth0: no link during initialization.
   [   49.986270] ADDRCONF(NETDEV_UP): eth0: link is not ready
   [   50.168469] ADDRCONF(NETDEV_UP): wlan0: link is not ready
   [   50.335864] ppdev: user-space parallel port driver
   [  118.000021] Clocksource tsc unstable (delta = -300115577 ns)
   [  219.769388] nvidia: no symbol version for struct_module
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by Nate8nate on 2009-09-12
I still haven't found anything on this error, insight would be appreciated.

---

### Post by Nate8nate on 2009-09-13
I seems the installer was trying to use an old kernel, so I unistalled that through Synaptic.  Now I am getting this:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Sep 13 17:51:42 2009
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
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
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
-> Installing NVIDIA driver version 185.18.36.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.31-10-generic/build'
-> Kernel output path: '/lib/modules/2.6.31-10-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.31-10-gener
   ic/build SYSOUT=/lib/modules/2.6.31-10-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-10-generic/build SUBDIRS
   =/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.3
   6-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinclude
    -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include includ
   e/linux/autoconf.h -Iubunt
   u/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-for
   mat-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm
   =3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=gener
   ic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack-protector-a
   ll -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx
   -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-o
   ptimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-s
   trict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz6761/NVIDIA-Linux-x86-185.18
   .36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-
   subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-p
   op -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM
   -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBU
   ILD_STR(s)=#s" -D"KBUILD_BASENAME=
   KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz676
   1/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6761/NVIDI
   A-Linux-x86-185.18.36-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iincl
   ude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include in
   clude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -Wno-format-security -fno-delete-null-pointer-checks -
   O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-bound
   ary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack
   -protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-u
   nwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024
   -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-stat
   ement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/self
   gz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-
   type -Wswitch -Wformat -
   Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-d
   efer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE 
   -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAM
   E=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1
   /usr/src/nv/.tmp_nv-vm.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr
   /src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstac
   k-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-
   unwind-tables -mno-sse -mno-mm
   x -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno
   -optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fno
   -strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz6761/NVIDIA-Linux-x86-185.
   18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wcha
   r-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer
   -pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNV
   RM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"
   KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=
   KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/u
   sr/src/nv/.tmp_os-agp.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/
   src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include 
   -Iinclude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declara
   tion -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-fl
   oat -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586
   -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-protector -fstack
   -protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-p
   ointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointe
   r-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz6761/NVIDIA-Lin
   ux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wf
   ormat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror
   -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -D
   MODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6761/NVIDIA-Linux-x86-
   185.18.36-pkg1/usr/src/nv/.tmp_os-
   interface.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-in
   terface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  
   -Iinclude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -Wno-format-security -fno-delete-null-pointer-ch
   ecks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack
   -boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -
   fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchro
   nous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-tha
   n=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-aft
   er-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/t
   mp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -W
   return-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-
   cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.
   18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c 
   -o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_os-regist
   ry.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-registry.
   c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -Wno-format-security -fno-delete-null-pointer-checks 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstac
   k-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-
   unw
   ind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -
   fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-state
   ment -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfg
   z6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-t
   ype -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-m
   ultichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error
   -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DE
   BUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv
   _i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6761/NVIDIA-
   Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz6761/NVIDIA-Lin
   ux-x86-185.18.36-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -Iinc
   lude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -include i
   nclude/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-fu
   nction-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 
   -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary
   =2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -fstack-pr
   otector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwi
   nd-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -f
   no-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statem
   ent -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz
   6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-ty
   pe -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mu
   ltichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error 
   -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DE
   BUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv
   acpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz6761/NVIDIA-
   Linux-x86-185.18.36-pkg1/usr/src/nv/
   .tmp_nvacpi.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nva
   cpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:56,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/io.h:22,
                    from include/linux/pci.h:54,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h: In funct
   ion ‘writeq’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/io.h:70: warni
   ng: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -m elf_i386   -r -o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr
   /src/nv/nvidia.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/
   nv-kernel.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv.o 
   /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-agp.o /tmp/selfgz6761/N
   VIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.o /tmp/selfgz6761/NVI
   DIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-registry.o /tmp/selfgz6761/NVIDIA
   -Linux-x86-185.18.36-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz6761/NVIDIA-Linux-x
   86-185.18.36-pkg1/usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg
   1/usr/src/nv/nvidia.ko;) > /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/u
   sr/src/nv/modules.order
   make -f /usr/src/linux-headers-2.6.31-10-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.31-10-generic/Modu
   le.symvers -I /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/M
   odule.symvers -S -K /usr/src/linux-headers-2.6.31-10-generic/Module.markers 
   -M /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/Module.markers
   -w  -s
   WARNING: could not find /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.4.1/include  -
   Iinclude  -I/usr/src/linux-headers-2.6.31-10-generic/arch/x86/include -inclu
   de include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -Wno-format-security -fno-delete-null-pointer-che
   cks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-
   boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -f
   stack-protector -fstack-protector-all -pipe -Wno-sign-
   compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dn
   ow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-ca
   lls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fn
   o-dwarf2-cfi-asm -I/tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-comp
   are -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRI
   NG=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMO
   DULE -c -o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nvidia
   .mod.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nvidia.mod
   .c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.31-10-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-10-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
     ld -r -m elf_i386  --build-id -o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.3
   6-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/
   usr/src/nv/nvidia.o /tmp/selfgz6761/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/
   nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [  127.032732] cfg80211: Regulatory domain: 98
   [  127.032734] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain,
   max_eirp)
   [  127.032737] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
   [  127.032742] cfg80211: Disabling channel 2467 MHz on phy0 due to Country
   IE
   [  127.032745] cfg80211: Disabling channel 2472 MHz on phy0 due to Country
   IE
   [  127.032747] cfg80211: Disabling channel 2484 MHz on phy0 due to Country
   IE
   [  127.032752] cfg80211: Current regulatory domain updated by AP to: US
   [  127.032754] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain,
   max_eirp)
   [  127.032757] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
   [  137.800024] wlan0: no IPv6 routers present
   [  145.000036] Clocksource tsc unstable (delta = -117785168 ns)
   [  699.037506] wlan0: disassociating by local choice (reason=3)
   [  775.748417] nvidia 0000:00:12.0: setting latency timer to 64
   [  775.748816] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri
   Aug 14 17:18:04 PDT 2009
   [  901.277906] glxinfo[6092]: segfault at 17cc ip 002cad09 sp bf82509c error
   6 in libc-2.10.1.so[25b000+155000]
   [  902.930878] wlan0: authenticate with AP 00:22:6b:63:4c:ae
   [  902.932321] wlan0: authenticated
   [  902.932325] wlan0: associate with AP 00:22:6b:63:4c:ae
   [  902.934365] wlan0: RX AssocResp from 00:22:6b:63:4c:ae (capab=0x401
   status=0 aid=1)
   [  902.934370] wlan0: associated
   [  903.241158] glxinfo[6180]: segfault at 4 ip 009d98b7 sp bfe400d0 error 4
   in libc-2.10.1.so[9a9000+155000]
   [  904.272631] compiz.real[6221]: segfault at 184d ip 00550d09 sp bff60dbc
   error 6 in libc-2.10.1.so[4e1000+155000]
   [ 1538.463997] wlan0: disassociating by local choice (reason=3)
   [ 1563.787962] nvidia 0000:00:12.0: setting latency timer to 64
   [ 1563.788883] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri
   Aug 14 17:18:04 PDT 2009
-> Installing both new and classic TLS OpenGL libraries.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (185.18.36):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
ERROR: The runtime configuration check failed for the library
       'libnvidia-tls.so.185.18.36' (expected:
       '/usr/lib/tls/libnvidia-tls.so.1', found:
       '/usr/lib/libnvidia-tls.so.1').  The most likely reason for this is that
       conflicting OpenGL libraries are installed in a location not inspected
       by `nvidia-installer`.  Please be sure you have uninstalled any
       third-party OpenGL and/or third-party graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by Nate8nate on 2009-09-15
It seems to be a problem with eglibc as seen in [https://bugs.launchpad.net/ubuntu/karmic/+source/eglibc/+bug/429003]("https://bugs.launchpad.net/ubuntu/karmic/+source/eglibc/+bug/429003").  The update I'm running should fix it.  I'll report back if it doesn't.

---

