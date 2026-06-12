---
title: "Problem configuring VMware on Karmin Koala amd64"
date: 2010-01-01
forum: General Help
---

### Post by d3k0 on 2010-01-01
Hey again! I need a couple of things from a windows machine, without booting out of linux and I got myself VMWare! I can't manage to configure it. Installation worked great though... here is the error(s) I get after trying to configure it:

```
desislav@BSG:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-workstation.desktop: warning: value "vmware-workstation.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-player.desktop: warning: value "vmware-player.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.31-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:104:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:168: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/apic.h:11,
                 from /usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/smp.h:13,
                 from /usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/mmzone_64.h:12,
                 from /usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/mmzone.h:4,
                 from include/linux/mmzone.h:773,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/apicdef.h:133:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86cpuid.h:381:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/irqflags.h:61,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.31-16-generic/arch/x86/include/asm/pgtable_types.h:182:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/vcpuset.h:89,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config1/vmmon-only/./common/vmx86.h:18,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:16,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:272:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:276:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:344:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:350:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:403:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:449:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:494:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:538:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:583:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:627:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:672:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:716:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:718:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:759:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:803:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:805:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:846:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:888:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:890:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:929:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:971:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:973:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1012:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1166:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1170:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1256:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1454:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1581:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1714:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config1/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config1/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_asm_x86_64.h:25,
                 from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:28,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:52:
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:471:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:764:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:804:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:28,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:52:
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86_64.h:42:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:79:
/tmp/vmware-config1/vmmon-only/./common/hostif.h:39:7: warning: "WINNT_DDK" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config1/vmmon-only/linux/driver.c:149: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:150: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1710: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1710: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1711: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1711: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1712: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1712: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1713: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1713: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1715: error: ‘struct mm_struct’ has no member named ‘dumpable’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1726: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I tried searching the forums for something similar to my problem, but I found nothing! Hope someone can help me. Thanks in advance !

Cheers,
Desislav

---

