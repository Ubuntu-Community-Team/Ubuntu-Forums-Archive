---
title: "VMware installation won't complete"
date: 2009-11-03
forum: General Help
---

### Post by chr3681 on 2009-11-03
Hey, I am getting the following errors when trying to install vmware-workstation 5.5.9-126128 (I know this is an older version, but this is the license that I own.):
-----------------------------------------------------------------------
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.28-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-generic'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:48:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_types.h:160: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config2/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config2/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-16-generic/arch/x86/include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:49:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config2/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:71:
/tmp/vmware-config2/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:80:
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config2/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
/tmp/vmware-config2/vmmon-only/linux/driver.c:144: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:145: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c:148: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config2/vmmon-only/linux/driver.c:149: warning: initialization from incompatible pointer type
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1661: error: ‘struct mm_struct’ has no member named ‘dumpable’
/tmp/vmware-config2/vmmon-only/linux/driver.c:1672: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

chris@chris-ubuntu:~/downloads/vmware-distrib$ 
-----------------------------------------------------------------------

******************************************************
Any help with this issue would be greatly appreciated!
******************************************************

---

