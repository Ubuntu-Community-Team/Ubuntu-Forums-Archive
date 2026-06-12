---
title: "vmware 6.5 module updater failing"
date: 2010-02-02
forum: General Help
---

### Post by SpenceMakesSense on 2010-02-02
After I had installed vmware I went and loaded it from the applications dropdown box. When it started it showed a screen that said it had to run the module updater. When I ran that it fails almost immediately with an error that says  
```
Unable to build kernel module.

See log file /tmp/vmware-root/setup-15970.log for details.
```

heres the log ```
Feb 02 17:17:42.561: app| Log for VMware Workstation pid=17717 version=6.5.0 build=build-118166 option=Release
Feb 02 17:17:42.561: app| Host codepage=UTF-8 encoding=UTF-8
Feb 02 17:17:42.561: app| Logging to /tmp/vmware-root/setup-17717.log
Feb 02 17:17:43.788: app| Extracting the sources of the vmmon module.
Feb 02 17:17:43.804: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-17-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1
```

and heres the code when running it in a terminal

```
 spence@ubuntu:~$ vmware
Logging to /tmp/vmware-spence/setup-17132.log
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
ERROR: modinfo: could not find module vmmon
ERROR: modinfo: could not find module vmnet
ERROR: modinfo: could not find module vmblock
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
Stopping VMware services:
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.31-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:31:
/tmp/vmware-root/modules/vmmon-only/./include/compat_wait.h:78: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:70: note: previous declaration of &#8216;poll_initwait&#8217; was here
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:99:
/tmp/vmware-root/modules/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./common/vmx86.h:31,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:101:
/tmp/vmware-root/modules/vmmon-only/./include/x86apic.h:97:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/apic.h:11,
                 from /usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/smp.h:13,
                 from include/linux/smp.h:36,
                 from include/linux/topology.h:33,
                 from include/linux/gfp.h:7,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-root/modules/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.31-17-generic/arch/x86/include/asm/apicdef.h:133:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-root/modules/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-root/modules/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:101:
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_basic_asm.h:46,
                 from /tmp/vmware-root/modules/vmmon-only/./include/rateconv.h:45,
                 from /tmp/vmware-root/modules/vmmon-only/./include/modulecall.h:40,
                 from /tmp/vmware-root/modules/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:101:
/tmp/vmware-root/modules/vmmon-only/./include/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:43,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:103:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:119:
/tmp/vmware-root/modules/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-root/modules/vmmon-only/linux/driver.c: In function &#8216;LinuxDriverSyncCallOnEachCPU&#8217;:
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1423: error: too many arguments to function &#8216;smp_call_function&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1987: error: &#8216;struct task_struct&#8217; has no member named &#8216;euid&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1987: error: &#8216;struct task_struct&#8217; has no member named &#8216;uid&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1988: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1988: error: &#8216;struct task_struct&#8217; has no member named &#8216;uid&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1989: error: &#8216;struct task_struct&#8217; has no member named &#8216;egid&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1989: error: &#8216;struct task_struct&#8217; has no member named &#8216;gid&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1990: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:1990: error: &#8216;struct task_struct&#8217; has no member named &#8216;gid&#8217;
/tmp/vmware-root/modules/vmmon-only/linux/driver.c:2007: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vmware-root/modules/vmmon-only/linux/driver.o] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make[1]: *** [_module_/tmp/vmware-root/modules/vmmon-only] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
make: *** [vmmon.ko] Error 2
ERROR: modinfo: could not find module vmmon
```

Any help would be much appreciated. I would use virtualbox but It doesn't support everything I would like to do with my virtual machine

EDIT: Im using ubuntu 9.10.

---

### Post by SpenceMakesSense on 2010-02-04
bumpity

---

### Post by guneza on 2010-04-02
Maybe this thread helps?

[http://ubuntuforums.org/showthread.php?t=1287535](http://ubuntuforums.org/showthread.php?t=1287535)

---

