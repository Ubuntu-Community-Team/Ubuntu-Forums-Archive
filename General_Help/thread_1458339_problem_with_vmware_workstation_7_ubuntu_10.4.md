---
title: "problem with vmware workstation 7 ubuntu 10.4"
date: 2010-04-19
forum: General Help
---

### Post by tkblackbelt on 2010-04-19
Hi guys for some reason when I try to run vmware workstation 7 i get a errorsaying unable to start services.If anyone knows how to fix it it would be greatly appreciated.

heres a picture of the error


[ATTACH]153806[/ATTACH]




heres the output of sudo vmware

----------------------------------------------


chuck@chuck-laptop:~$ sudo vmware
Logging to /tmp/vmware-root/setup-8409.log
filename:       /lib/modules/2.6.32-21-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-21-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-21-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-21-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-21-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-21-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-21-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-21-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-21-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-21-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-21-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-21-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.32-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:100:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/driver.c:100:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/linux/hostif.c:67:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c: In function &#8216;HostIFReadUptimeWork&#8217;:
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c:1944: warning: &#8216;newUpBase&#8217; may be used uninitialized in this function
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/iommu.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/task.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/common/task.c:50:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/vmx86.o
In file included from /tmp/vmware-root/modules/vmmon-only/./include/vm_asm.h:42,
                 from /tmp/vmware-root/modules/vmmon-only/common/vmx86.c:43:
/tmp/vmware-root/modules/vmmon-only/./include/vm_asm_x86_64.h:50:7: warning: "_MSC_VER" is not defined
  CC [M]  /tmp/vmware-root/modules/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmnet-only'
make -C /lib/modules/2.6.32-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /tmp/vmware-root/modules/vmnet-only/driver.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/hub.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/userif.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/netif.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/filter.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/smac.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetUserListener.o
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function &#8216;VNetUserListenerEventHandler&#8217;:
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: (Each undeclared identifier is reported only once
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: for each function it appears in.)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function &#8216;VNetUserListenerRead&#8217;:
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function &#8216;signal_pending&#8217;
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function &#8216;schedule&#8217;
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/vnetUserListener.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmnet-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmblock-only'
make -C /lib/modules/2.6.32-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-root/modules/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-root/modules/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-root/modules/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmblock-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmblock-only'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-root/modules/vmblock-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmci-only'
make -C /lib/modules/2.6.32-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /tmp/vmware-root/modules/vmci-only/linux/driver.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.o
In file included from /tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:48:
/tmp/vmware-root/modules/vmci-only/./include/pgtbl.h: In function &#8216;PgtblVa2MPN&#8217;:
/tmp/vmware-root/modules/vmci-only/./include/pgtbl.h:301: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/./include/pgtbl.h: In function &#8216;PgtblVa2Page&#8217;:
/tmp/vmware-root/modules/vmci-only/./include/pgtbl.h:373: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCIHost_SignalCall&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:328: error: &#8216;TASK_NORMAL&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:328: error: (Each undeclared identifier is reported only once
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:328: error: for each function it appears in.)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCIHost_WaitForCallLocked&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:370: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:370: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:378: error: implicit declaration of function &#8216;schedule&#8217;
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:386: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:386: error: &#8216;TASK_RUNNING&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:390: error: implicit declaration of function &#8216;signal_pending&#8217;
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCI_SignalEvent&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:682: error: &#8216;TASK_NORMAL&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCI_WaitOnEventInterruptible&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:739: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:739: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:751: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:751: error: &#8216;TASK_RUNNING&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCIHost_GetUserMemory&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:1438: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:1440: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:1459: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:1487: error: dereferencing pointer to incomplete type
make[2]: *** [/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmci-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [vmci.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmci-only'
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmci-only'
make -C /lib/modules/2.6.32-21-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.o
In file included from /tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:48:
/tmp/vmware-root/modules/vmci-only/./include/pgtbl.h: In function &#8216;PgtblVa2MPN&#8217;:
/tmp/vmware-root/modules/vmci-only/./include/pgtbl.h:301: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/./include/pgtbl.h: In function &#8216;PgtblVa2Page&#8217;:
/tmp/vmware-root/modules/vmci-only/./include/pgtbl.h:373: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCIHost_SignalCall&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:328: error: &#8216;TASK_NORMAL&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:328: error: (Each undeclared identifier is reported only once
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:328: error: for each function it appears in.)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCIHost_WaitForCallLocked&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:370: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:370: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:378: error: implicit declaration of function &#8216;schedule&#8217;
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:386: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:386: error: &#8216;TASK_RUNNING&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:390: error: implicit declaration of function &#8216;signal_pending&#8217;
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCI_SignalEvent&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:682: error: &#8216;TASK_NORMAL&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCI_WaitOnEventInterruptible&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:739: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:739: error: &#8216;TASK_INTERRUPTIBLE&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:751: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:751: error: &#8216;TASK_RUNNING&#8217; undeclared (first use in this function)
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c: In function &#8216;VMCIHost_GetUserMemory&#8217;:
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:1438: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:1440: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:1459: error: dereferencing pointer to incomplete type
/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.c:1487: error: dereferencing pointer to incomplete type
make[2]: *** [/tmp/vmware-root/modules/vmci-only/linux/vmciKernelIf.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmci-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [vmci.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmci-only'
Starting VMware services:
   VMware USB Arbitrator                                               done
   Virtual machine monitor                                             done
   Virtual machine communication interface                            failed
   VM communication interface socket family                           failed
   Blocking file system                                                done
   Virtual ethernet                                                   failed

---

### Post by dcstar on 2010-04-20
All VM issues belong in the Virtualization forum.

---

