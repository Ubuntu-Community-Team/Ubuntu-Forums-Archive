---
title: "Nvidia-210-drivers and Kernelbuilds"
date: 2009-12-19
forum: General Help
---

### Post by coth on 2009-12-19
Hi folks!
Recently put together a fairly good desktop computer, mostly built for audio and producing. I got a gainward 210 graphics card fairly cheap, thought this would be good since I've runned with ati chips before and... well I got tired of all the don'ts so to speak .) . So after some configuration most things work, exept drivers for the card, not so surprising I found out as the drivers are not embeded within 180.-- but rather in 190.-- package. 

Spent the day fixing and stuff and using this(" [http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html) ") guide I managed to install propretary drivers for the card. However I'm still unable to activate the driver using "Hardware Drivers" (it activates but does not show as activated) and when I restart I get kicked into "non-X" mode. I run dpkg-reconfigure xserver-xorg and I fix this. I then tried tolocate the problem and noticed something from the instalation log for the 190.53 driver packages. It says that it can't compile the kernel. From this I found this(" [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/385515](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/385515) ") site after some googling and ran "sudo dkms build -m nvidia -v 96.43.10" 

It tells me this:
""
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
su nobody -c "make KERNELRELEASE=2.6.28-3-rt module KERNDIR=/lib/modules/2.6.28-3-rt IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/2.6.28-3-rt/build"......(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.28-3-rt (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/190.53/build/ for more information.
0
0
""

How do I fix this? I'm running an rt-kernel under Ubuntu Studio ftm. Figured this might have something to do with the problem.

//Paco

---

### Post by coth on 2009-12-19
...and this is my make.log file in "/var/lib/dkms/nvidia/190.53/build":
```
DKMS make.log for nvidia-190.53 for kernel 2.6.28-3-rt (i686)
Sat Dec 19 21:28:48 CET 2009
NVIDIA: calling KBUILD...
make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.28-3-rt/build SUBDIRS=/var/lib/dkms/nvidia/190.53/build modules
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /var/lib/dkms/nvidia/190.53/build/.tmp_versions ; rm -f /var/lib/dkms/nvidia/190.53/build/.tmp_versions/*
make -f scripts/Makefile.build obj=/var/lib/dkms/nvidia/190.53/build
  cc -Wp,-MD,/var/lib/dkms/nvidia/190.53/build/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv -I/var/lib/dkms/nvidia/190.53/build -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"190.53\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /var/lib/dkms/nvidia/190.53/build/.tmp_nv.o /var/lib/dkms/nvidia/190.53/build/nv.c
In file included from include/linux/bitops.h:17,
                 from include/linux/kernel.h:15,
                 from include/linux/sched.h:52,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/190.53/build/nv-linux.h:21,
                 from /var/lib/dkms/nvidia/190.53/build/nv.c:14:
/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In function ‘set_bit’:
/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arithmetic
/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h: In function ‘clear_bit’:
/usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/list.h:6,
                 from include/linux/preempt.h:11,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:29,
                 from include/linux/time.h:8,
                 from include/linux/timex.h:57,
                 from include/linux/sched.h:54,
                 from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/190.53/build/nv-linux.h:21,
                 from /var/lib/dkms/nvidia/190.53/build/nv.c:14:
include/linux/prefetch.h: In function ‘prefetch_range’:
include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/linux/utsname.h:35,
                 from /var/lib/dkms/nvidia/190.53/build/nv-linux.h:21,
                 from /var/lib/dkms/nvidia/190.53/build/nv.c:14:
include/linux/sched.h: In function ‘object_is_on_stack’:
include/linux/sched.h:2124: warning: pointer of type ‘void *’ used in arithmetic
In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/dma-mapping.h:9,
                 from include/linux/dma-mapping.h:57,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/pci.h:94,
                 from include/linux/pci.h:1002,
                 from /var/lib/dkms/nvidia/190.53/build/nv-linux.h:92,
                 from /var/lib/dkms/nvidia/190.53/build/nv.c:14:
include/linux/scatterlist.h: In function ‘sg_virt’:
include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used in arithmetic
In file included from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/hardirq_32.h:5,
                 from /usr/src/linux-headers-2.6.28-3-rt/arch/x86/include/asm/hardirq.h:2,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /var/lib/dkms/nvidia/190.53/build/nv-linux.h:93,
                 from /var/lib/dkms/nvidia/190.53/build/nv.c:14:
include/linux/irq.h: In function ‘irq_to_desc’:
include/linux/irq.h:203: warning: comparison between signed and unsigned
In file included from /var/lib/dkms/nvidia/190.53/build/nv-linux.h:119,
                 from /var/lib/dkms/nvidia/190.53/build/nv.c:14:
include/linux/highmem.h: In function ‘zero_user_segments’:
include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in arithmetic
include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in arithmetic
In file included from /var/lib/dkms/nvidia/190.53/build/nv.c:14:
/var/lib/dkms/nvidia/190.53/build/nv-linux.h: At top level:
/var/lib/dkms/nvidia/190.53/build/nv-linux.h:202: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘nv_spinlock_t’
/var/lib/dkms/nvidia/190.53/build/nv-linux.h:1282: error: expected specifier-qualifier-list before ‘nv_spinlock_t’
/var/lib/dkms/nvidia/190.53/build/nv-linux.h:1353: error: expected specifier-qualifier-list before ‘nv_spinlock_t’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘verify_pci_bars’:
/var/lib/dkms/nvidia/190.53/build/nv.c:212: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nvos_proc_create’:
/var/lib/dkms/nvidia/190.53/build/nv.c:659: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nvl_add_alloc’:
/var/lib/dkms/nvidia/190.53/build/nv.c:865: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:868: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nvidia_init_module’:
/var/lib/dkms/nvidia/190.53/build/nv.c:1508: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:1680: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:1714: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nvidia_exit_module’:
/var/lib/dkms/nvidia/190.53/build/nv.c:1757: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:1821: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_alloc_file_private’:
/var/lib/dkms/nvidia/190.53/build/nv.c:2012: error: implicit declaration of function ‘semaphore_init’
/var/lib/dkms/nvidia/190.53/build/nv.c:2013: error: ‘nv_file_private_t’ has no member named ‘waitqueue’
/var/lib/dkms/nvidia/190.53/build/nv.c:2014: error: implicit declaration of function ‘atomic_spin_lock_init’
/var/lib/dkms/nvidia/190.53/build/nv.c:2014: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2016: error: ‘nv_file_private_t’ has no member named ‘event_fifo’
/var/lib/dkms/nvidia/190.53/build/nv.c:2017: error: ‘nv_file_private_t’ has no member named ‘event_fifo’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_free_file_private’:
/var/lib/dkms/nvidia/190.53/build/nv.c:2032: error: ‘nv_file_private_t’ has no member named ‘event_fifo’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_kern_open’:
/var/lib/dkms/nvidia/190.53/build/nv.c:2093: error: ‘nv_linux_state_t’ has no member named ‘device_num’
/var/lib/dkms/nvidia/190.53/build/nv.c:2095: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:2107: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2188: error: request for member ‘entry’ in something not a structure or union
/var/lib/dkms/nvidia/190.53/build/nv.c:2188: error: request for member ‘entry’ in something not a structure or union
/var/lib/dkms/nvidia/190.53/build/nv.c:2188: error: request for member ‘entry’ in something not a structure or union
/var/lib/dkms/nvidia/190.53/build/nv.c:2188: error: request for member ‘entry’ in something not a structure or union
/var/lib/dkms/nvidia/190.53/build/nv.c:2188: warning: initialization from incompatible pointer type
/var/lib/dkms/nvidia/190.53/build/nv.c:2264: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_kern_close’:
/var/lib/dkms/nvidia/190.53/build/nv.c:2353: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2364: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2372: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2378: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2380: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2423: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_kern_mmap’:
/var/lib/dkms/nvidia/190.53/build/nv.c:2655: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2667: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2676: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2683: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2709: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2715: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2735: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2744: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2753: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2760: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_kern_poll’:
/var/lib/dkms/nvidia/190.53/build/nv.c:2815: error: ‘nv_file_private_t’ has no member named ‘waitqueue’
/var/lib/dkms/nvidia/190.53/build/nv.c:2818: error: implicit declaration of function ‘atomic_spin_lock_irqsave’
/var/lib/dkms/nvidia/190.53/build/nv.c:2818: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:2829: error: implicit declaration of function ‘atomic_spin_unlock_irqrestore’
/var/lib/dkms/nvidia/190.53/build/nv.c:2829: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_kern_ioctl’:
/var/lib/dkms/nvidia/190.53/build/nv.c:2979: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_kern_ctl_open’:
/var/lib/dkms/nvidia/190.53/build/nv.c:3198: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:3218: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_kern_ctl_close’:
/var/lib/dkms/nvidia/190.53/build/nv.c:3240: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:3252: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_alloc_kernel_mapping’:
/var/lib/dkms/nvidia/190.53/build/nv.c:3693: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:3712: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:3727: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:3733: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:3737: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_free_pages’:
/var/lib/dkms/nvidia/190.53/build/nv.c:4073: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4088: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4093: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_lock_init_locks’:
/var/lib/dkms/nvidia/190.53/build/nv.c:4148: error: ‘nv_linux_state_t’ has no member named ‘rm_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4150: error: ‘nv_linux_state_t’ has no member named ‘ldata_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4151: error: ‘nv_linux_state_t’ has no member named ‘at_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4158: error: ‘nv_linux_state_t’ has no member named ‘rm_lock_cpu’
/var/lib/dkms/nvidia/190.53/build/nv.c:4159: error: ‘nv_linux_state_t’ has no member named ‘rm_lock_count’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_lock_rm’:
/var/lib/dkms/nvidia/190.53/build/nv.c:4172: error: ‘nv_linux_state_t’ has no member named ‘rm_lock_cpu’
/var/lib/dkms/nvidia/190.53/build/nv.c:4174: error: ‘nv_linux_state_t’ has no member named ‘rm_lock_count’
/var/lib/dkms/nvidia/190.53/build/nv.c:4180: error: implicit declaration of function ‘atomic_spin_unlock_wait’
/var/lib/dkms/nvidia/190.53/build/nv.c:4180: error: ‘nv_linux_state_t’ has no member named ‘rm_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4181: error: implicit declaration of function ‘atomic_spin_lock_irq’
/var/lib/dkms/nvidia/190.53/build/nv.c:4181: error: ‘nv_linux_state_t’ has no member named ‘rm_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4183: error: ‘nv_linux_state_t’ has no member named ‘rm_lock_cpu’
/var/lib/dkms/nvidia/190.53/build/nv.c:4184: error: ‘nv_linux_state_t’ has no member named ‘rm_lock_count’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_unlock_rm’:
/var/lib/dkms/nvidia/190.53/build/nv.c:4194: error: ‘nv_linux_state_t’ has no member named ‘rm_lock_count’
/var/lib/dkms/nvidia/190.53/build/nv.c:4197: error: ‘nv_linux_state_t’ has no member named ‘rm_lock_cpu’
/var/lib/dkms/nvidia/190.53/build/nv.c:4198: error: implicit declaration of function ‘atomic_spin_unlock_irq’
/var/lib/dkms/nvidia/190.53/build/nv.c:4198: error: ‘nv_linux_state_t’ has no member named ‘rm_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_post_event’:
/var/lib/dkms/nvidia/190.53/build/nv.c:4219: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4223: error: ‘nv_file_private_t’ has no member named ‘waitqueue’
/var/lib/dkms/nvidia/190.53/build/nv.c:4224: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4229: error: ‘nv_file_private_t’ has no member named ‘event_fifo’
/var/lib/dkms/nvidia/190.53/build/nv.c:4232: error: ‘nv_file_private_t’ has no member named ‘event_fifo’
/var/lib/dkms/nvidia/190.53/build/nv.c:4233: error: ‘nv_file_private_t’ has no member named ‘event_fifo’
/var/lib/dkms/nvidia/190.53/build/nv.c:4240: error: ‘nv_file_private_t’ has no member named ‘waitqueue’
/var/lib/dkms/nvidia/190.53/build/nv.c:4241: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_get_event’:
/var/lib/dkms/nvidia/190.53/build/nv.c:4255: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4258: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c:4262: error: ‘nv_file_private_t’ has no member named ‘event_fifo’
/var/lib/dkms/nvidia/190.53/build/nv.c:4279: error: ‘nv_file_private_t’ has no member named ‘fp_lock’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_kern_probe’:
/var/lib/dkms/nvidia/190.53/build/nv.c:4707: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:4707: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:4708: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:4711: error: ‘nv_linux_state_t’ has no member named ‘device_num’
/var/lib/dkms/nvidia/190.53/build/nv.c:4823: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:4827: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:4827: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:4828: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c:4828: error: ‘nv_linux_state_t’ has no member named ‘next’
/var/lib/dkms/nvidia/190.53/build/nv.c: In function ‘nv_get_adapter_state’:
/var/lib/dkms/nvidia/190.53/build/nv.c:5160: error: ‘nv_linux_state_t’ has no member named ‘next’
make[3]: *** [/var/lib/dkms/nvidia/190.53/build/nv.o] Error 1
make[2]: *** [_module_/var/lib/dkms/nvidia/190.53/build] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
```

---

### Post by falconindy on 2009-12-19
What's the output of uname -r? Given that output, have you installed headers for that kernel?

---

### Post by cormano on 2009-12-19
ppa:nvidia-vdpau/ppa

This ppa has the 190.42 driver

---

### Post by coth on 2009-12-19
Output for uname -r: 2.6.28-3-rt, what do you mean by headers? I'm ok at tricking with settings and stuff but it's been a while since I last programed anything .) . 

What does ppa:nvidia-vdpau/ppa mean? I got the drivers installed and they show up in "Hardware Drivers".

---

### Post by cormano on 2009-12-19
vdpau is the new nvidia api for video acceleration in unix.
It helps decoding avc, vc-1, mpeg4 asp and others.
In the same repository theres an mplayer build with vdpau support.

---

### Post by falconindy on 2009-12-19
The 190 driver requires kernel 2.6.32. You won't be able to compile it on 2.6.28.

---

### Post by cormano on 2009-12-19
How come the one from the ppa works then?

---

### Post by coth on 2009-12-19
First of all I'm not using 190.42 but 190.53 and I'm guessing that it's not the same thing anyways since I've been diggin for propretary drivers.

Thx for the fast replies. Btw, since the rt-kernel doesn't seem to be out yet, you're supposed to be able to recompile it rather than reinstalling, right?

---

### Post by coth on 2009-12-20
So, I let go of the Studio-Install(for some reason I can't install the rt-kernel embedded within 9.10) and succesfully installed Ubuntu 9.10 and it worked like a charm from the start. Installed the audio-package and only problem is that jack keeps making xruns at very low latencylevels because of the non-rtkernel, but I can live with that for now. Thx again guys for the fast replies.
//Paco

---

### Post by AdrianVeidt on 2009-12-21
> The 190 driver requires kernel 2.6.32. You won't be able to compile it on 2.6.28.

Incorrect. It should compile on old kernels. It's new kernels, and rt kernels that present a problem.

coth, forget about using any nvidia blob with that piece of junk. You have three options.

1. Use the pathetic nv driver that gets loaded by default (no video playback at all).
2. Add the xorg-edgers ppa and use the Nouveau driver, if it works (no vdpau or 3d acceleration but good 2d, kms, and xv for video playback).
3. Buy a new graphics card making sure it's an Nvidia Geforce 8k or newer card.

For crikey's sake do the third and save yourself a lot of headaches.

---

### Post by DeMus on 2009-12-21
> **falconindy said:**
> The 190 driver requires kernel 2.6.32. You won't be able to compile it on 2.6.28.

It works wonders with 2.6.30 which is a rock stable kernel version. Higher numbers kernel have problems with hardware detection, like temp sensors. So better to stick to 2.6.30.
I also use 190.53 and it works great. I get them from:
[_nVidia_]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu") which I added to my repositories. Have a look around there and install the driver through Synaptic. You'll get updates automatically as soon as they exist.

---

### Post by coth on 2009-12-22
> **AdrianVeidt said:**
> Incorrect. It should compile on old kernels. It's new kernels, and rt kernels that present a problem.

coth, forget about using any nvidia blob with that piece of junk. You have three options.

1. Use the pathetic nv driver that gets loaded by default (no video playback at all).
2. Add the xorg-edgers ppa and use the Nouveau driver, if it works (no vdpau or 3d acceleration but good 2d, kms, and xv for video playback).
3. Buy a new graphics card making sure it's an Nvidia Geforce 8k or newer card.

For crikey's sake do the third and save yourself a lot of headaches.

Ey, nah?!

As I said; hardwaredrivers works like a charm with the new kernel. Even installed the Linux-rt package and haven't met any problems so far, now Jack keeps making NO Xruns at all, 9.10 kicks as. :) 

Btw it's not 190.-- that came up but but 185, this seem to work aswell.

---

