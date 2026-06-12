---
title: "Vmware Server?"
date: 2009-11-14
forum: General Help
---

### Post by gletob on 2009-11-14
I'm trying to get Vmware server running on my machine, and when I run ```
sudo /usr/bin/vmware-config.pl
``` I get this error
```
glenn@glenn-laptop:~$ sudo /usr/bin/vmware-config.pl 
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.31-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:31:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:78: error: conflicting types for &#8216;poll_initwait&#8217;
include/linux/poll.h:70: note: previous declaration of &#8216;poll_initwait&#8217; was here
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:99:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config1/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:101:
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:103:
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:103:
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:119:
/tmp/vmware-config1/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function &#8216;LinuxDriverSyncCallOnEachCPU&#8217;:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1423: error: too many arguments to function &#8216;smp_call_function&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function &#8216;LinuxDriver_Ioctl&#8217;:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1987: error: &#8216;struct task_struct&#8217; has no member named &#8216;euid&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c:1987: error: &#8216;struct task_struct&#8217; has no member named &#8216;uid&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c:1988: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c:1988: error: &#8216;struct task_struct&#8217; has no member named &#8216;uid&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c:1989: error: &#8216;struct task_struct&#8217; has no member named &#8216;egid&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c:1989: error: &#8216;struct task_struct&#8217; has no member named &#8216;gid&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c:1990: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c:1990: error: &#8216;struct task_struct&#8217; has no member named &#8216;gid&#8217;
/tmp/vmware-config1/vmmon-only/linux/driver.c:2007: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

```

Can anyone here help?

---

### Post by gletob on 2009-11-14
Finally found the right terms to put in google and found this.
[http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html)

That's got me up and running but thanks.

---

