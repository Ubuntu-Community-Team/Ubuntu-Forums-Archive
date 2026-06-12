---
title: "VMWare - hitting error during installation"
date: 2010-11-13
forum: General Help
---

### Post by grayfox444 on 2010-11-13
I'm running Ubuntu 10.04. I downloaded the package and am following this guide: [http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04)

While I'm running through the installation wizard via the terminal, i hit an error at this step:

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 


I hit yes then it says:

```

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-25-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.32-25-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:31:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config0/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:99:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:101:
/tmp/vmware-config0/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-25-generic/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-25-generic/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-25-generic/arch/x86/include/asm/msr-index.h:230:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config0/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config0/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:101:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:103:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:103:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:119:
/tmp/vmware-config0/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config0/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

```

---

### Post by dcstar on 2010-11-14
> **grayfox444 said:**
> I'm running Ubuntu 10.04. I downloaded the package and am following this guide: [http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04)

While I'm running through the installation wizard via the terminal, i hit an error at this step:
..........

Look in the Virtualization forum for VM issues like this.

---

### Post by grayfox444 on 2010-11-14
is it possible to have my topic move, being the case?

---

