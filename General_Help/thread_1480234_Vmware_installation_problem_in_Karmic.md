---
title: "Vmware installation problem in Karmic"
date: 2010-05-11
forum: General Help
---

### Post by damnated on 2010-05-11
Everything works fine until I read the user agreement, hit yes, right after that: ```
None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-21-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.31-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'
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
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_basic_asm.h:46,
                 from /tmp/vmware-config1/vmmon-only/./include/rateconv.h:45,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:40,
                 from /tmp/vmware-config1/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:101:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:43,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:103:
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.


```My headers are updated and I have g++ installed, any ideas why this happens?

---

### Post by cdenley on 2010-05-11
Did you try compiling with the make-vmpkg command provided by the vmware-package package?
[http://manpages.ubuntu.com/manpages/karmic/man1/make-vmpkg.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/make-vmpkg.1.html)

You're using karmic, right?

---

### Post by damnated on 2010-05-11
I just ran the installation script with ```
sudo ./vmware-install.pl
```

---

### Post by cdenley on 2010-05-11
> **damnated said:**
> I just ran the installation script with ```
sudo ./vmware-install.pl
```

So the answer is no? I suggest you try it. This will ensure it works properly in ubuntu.

---

### Post by damnated on 2010-05-11
```
The program 'make-vmpkg' is currently not installed.  You can install it by typing:
sudo apt-get install vmware-package
make-vmpkg: command not found
damnated@damnated-desktop:~/Downloads/vmware-server-distrib$ sudo apt-get install vmware-package
[sudo] password for damnated: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vmware-package: Depends: libstdc++5 but it is not installable
E: Broken packages

```

---

### Post by cdenley on 2010-05-11
Sorry, I guess the package is broken in karmic for 32-bit.

---

### Post by damnated on 2010-05-11
Nevertheless, running the vmware-install.pl should work.

It only requires, in theory, a C compiler and an up to date header, both of which I have. There's very little documentation about this apparently. 
The latest installation tutorial I could find was for 8.04 and the instructions there are exactly what I did in the first place. 

[http://www.lucidtips.com/2009/01/20/installing-vmware-server-and-windows-xp-on-ubuntu/](http://www.lucidtips.com/2009/01/20/installing-vmware-server-and-windows-xp-on-ubuntu/)

---

### Post by cdenley on 2010-05-11
What version of vmware-server?
[http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html)

---

### Post by damnated on 2010-05-11
VMware Server 2 for Linux Operating Systems. Version 2.0.1 | 156745 - 03/31/09

---

### Post by cdenley on 2010-05-11
> **damnated said:**
> VMware Server 2 for Linux Operating Systems. Version 2.0.1 | 156745 - 03/31/09

[http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-install-vmware-server-2-0-x-in-ubuntu-9-10-karmic.html)
> 
Now you might receive compilation error messages so now you need to download required patch files from here in vmware-server-distrib directory these patches from  vmware forum


---

### Post by damnated on 2010-05-11
```
The configuration of VMware Server 2.0.1 build-156745 for Linux for this running kernel completed successfully.
```

Thank you!

---

