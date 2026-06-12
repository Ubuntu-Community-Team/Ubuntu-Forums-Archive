---
title: "vmware server 2.0.2 will not install on Ubuntu 10.04"
date: 2010-08-16
forum: General Help
---

### Post by TimsterC on 2010-08-16
Hi Folks,

I've tried all of the patches and everything but I still can't make this install.
**Ubuntu 10.04** (*Linux XXXXXXXX 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux*)

**vmware server 2.0.2** (*VMware-server-2.0.2-203138.i386.tar.gz*)

**Patch** from **Rise Security** as suggested in this [post ]("http://ubuntuforums.org/showthread.php?t=1466772")*[http://ubuntuforums.org/showthread.php?t=1466772](http://ubuntuforums.org/showthread.php?t=1466772)*
*[http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/](http://risesecurity.org/2010/04/02/vmware-server-2-0-2-update-patch-2/)*

All applied with no problems and I still get this bunch of errors

Can someone tell me what it all means and how I can fix it?

Thanks in advance for your help.

```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-24-generic-pae/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.32-24-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:31:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:99:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config2/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./include/vm_basic_asm.h:46,
                 from /tmp/vmware-config2/vmmon-only/./include/rateconv.h:45,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:40,
                 from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./include/vm_asm.h:43,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:103:
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:119:
/tmp/vmware-config2/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config2/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config2/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config2/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config2/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config2/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config2/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config2/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config2/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.
```

---

### Post by bict on 2010-08-17
Had the same problem, the tutorial below resolved it!

I recommend you, installing vmware server 2.0.2 with this tutorial:
[http://hmontoliu.blogspot.com/2010/04/installing-vmware-server-202-in-ubuntu.html](http://hmontoliu.blogspot.com/2010/04/installing-vmware-server-202-in-ubuntu.html)

good luck

---

### Post by TimsterC on 2010-08-17
> **bict said:**
> Had the same problem, the tutorial below resolved it!

I recommend you, installing vmware server 2.0.2 with this tutorial:
[http://hmontoliu.blogspot.com/2010/04/installing-vmware-server-202-in-ubuntu.html](http://hmontoliu.blogspot.com/2010/04/installing-vmware-server-202-in-ubuntu.html)

good luck

Thanks I'll give that a try and post back how it goes.

---

### Post by aznnico on 2011-06-15
Did it work? I'm having trouble also.

---

