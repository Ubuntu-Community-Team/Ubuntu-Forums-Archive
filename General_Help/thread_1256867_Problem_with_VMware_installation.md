---
title: "Problem with VMware installation"
date: 2009-09-03
forum: General Help
---

### Post by balumankala on 2009-09-03
Hi Frnds

I have Ubuntu 9.04( Desktop Edition) installed on my workstation
I have downloaded VMware-workstation-6.0.0-45731.i386.tar.gz   for ubuntu and tried to install. But im getting an error saying that "Execution Aborted"

Here are the detailed steps that I've followed. Can you please help me where im stuck ??

> 

balu@ubuntu:~/Desktop/VMware Linux/Linux_workstation6.part1/vmware-distrib$ sudo ./vmware-install.pl
A previous installation of VMware Workstation has been detected.

The previous installation was made by the tar installer (version 4).

Keeping the tar4 installer database format.

Uninstalling the tar installation of VMware Workstation.

Stopping VMware services:
   Virtual machine monitor                                             done

The removal of VMware Workstation 6.0.0 build-45731 for Linux completed 
successfully. Thank you for having tried this software.

Installing VMware Workstation.  This may take from several minutes to over an 
hour depending upon its size.

In which directory do you want to install the binary files? 
[/usr/bin/vmware] /usr/bin/vmware

The path "/usr/bin/vmware" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] y

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] /etc

What is the directory that contains the init scripts? 
[/etc/init.d] /etc/init.d

In which directory do you want to install the daemon files? 
[/usr/bin/sbin] /usr/bin/sbin

The path "/usr/bin/sbin" does not exist currently. This program is going to 
create it, including needed parent directories. Is this what you want? 
[yes] y

In which directory do you want to install the library files? 
[/usr/bin/lib/vmware] /usr/bin/lib/vmware

The path "/usr/bin/lib/vmware" does not exist currently. This program is going 
to create it, including needed parent directories. Is this what you want? 
[yes] y

In which directory do you want to install the manual files? 
[/usr/bin/man] /usr/bin/manual

In which directory do you want to install the documentation files? 
[/usr/bin/doc/vmware] /usr/bin/doc/vmware

The path "/usr/bin/doc/vmware" does not exist currently. This program is going 
to create it, including needed parent directories. Is this what you want? 
[yes] y

The installation of VMware Workstation 6.0.0 build-45731 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware/vmware-uninstall.pl".

Before running VMware Workstation for the first time, you need to configure it 
by invoking the following command: "/usr/bin/vmware/vmware-config.pl". Do you 
want this program to invoke the command for you now? [yes] y

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] /usr/share/icons

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] /usr/share/applications

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] /usr/share/pixmaps

/usr/share/applications/vmware-workstation.desktop: warning: value "vmware-workstation.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-player.desktop: warning: value "vmware-player.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-14-generic/build/include] /lib/modules/2.6.28-14-generic/build/include

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.28-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-14-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:48:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:170: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/fixmap_32.h:29,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/fixmap.h:5,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apic.h:8,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:30,
                 from include/linux/topology.h:33,
                 from include/linux/mmzone.h:763,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/apicdef.h:132:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86cpuid.h:381:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.28-14-generic/arch/x86/include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config0/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config0/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:149: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:150: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1715: error: ‘struct mm_struct’ has no member named ‘dumpable’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1726: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
**Unable to build the vmmon module.**

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

**Execution aborted.**





---

### Post by stefangr1 on 2009-09-03
Can't you upgrade to the newest version of vmware-server-2, or otherwise vmware-workstation (paid, but offers almost no extras in functionality) ?

---

