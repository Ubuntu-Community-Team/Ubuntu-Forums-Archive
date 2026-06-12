---
title: "VMWare Workstation 7 Kernel Module Update Error"
date: 2010-07-12
forum: General Help
---

### Post by Sanllian on 2010-07-12
I freshly installed VMWare Wrokstation 7 x86_64. And I was compiling the Kernel Module and got an error, Heres the error log.. I can't find anything about it.

Jul 12 10:24:44.157: app-140276199524096| Log for VMware Workstation pid=23577 version=7.0.0 build=build-203739 option=Release
Jul 12 10:24:44.157: app-140276199524096| The process is 64-bit.
Jul 12 10:24:44.157: app-140276199524096| Host codepage=UTF-8 encoding=UTF-8
Jul 12 10:24:44.157: app-140276199524096| Logging to /tmp/vmware-root/setup-23577.log
Jul 12 10:24:44.323: app-140276199524096| modconf query interface initialized
Jul 12 10:24:44.324: app-140276199524096| modconf library initialized
Jul 12 10:24:44.381: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.392: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.412: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.440: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.460: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.525: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.529: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.532: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.534: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.537: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.572: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.576: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.580: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.583: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.585: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.595: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.614: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.688: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.693: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.698: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.701: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.704: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.714: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.734: app-140276199524096| Your GCC version: 4.4
Jul 12 10:24:44.841: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.846: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.851: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.854: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:44.859: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:46.193: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:46.194: app-140276199524096| Building module vmmon.
Jul 12 10:24:46.194: app-140276199524096| Extracting the sources of the vmmon module.
Jul 12 10:24:46.220: app-140276199524096| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 12 10:24:54.437: app-140276199524096| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Jul 12 10:24:54.439: app-140276199524096| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-23-generic/misc/vmmon.o
Jul 12 10:24:55.189: app-140276199524096| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-23-generic/misc/vmmon.ko
Jul 12 10:24:56.697: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:24:56.697: app-140276199524096| Building module vmnet.
Jul 12 10:24:56.698: app-140276199524096| Extracting the sources of the vmnet module.
Jul 12 10:24:56.720: app-140276199524096| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 12 10:25:04.900: app-140276199524096| Failed to compile module vmnet!
Jul 12 10:25:04.909: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:25:04.910: app-140276199524096| Building module vmblock.
Jul 12 10:25:04.910: app-140276199524096| Extracting the sources of the vmblock module.
Jul 12 10:25:04.933: app-140276199524096| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 12 10:25:10.989: app-140276199524096| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Jul 12 10:25:10.990: app-140276199524096| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-23-generic/misc/vmblock.o
Jul 12 10:25:11.760: app-140276199524096| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-23-generic/misc/vmblock.ko
Jul 12 10:25:13.220: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:25:13.221: app-140276199524096| Building module vmci.
Jul 12 10:25:13.221: app-140276199524096| Extracting the sources of the vmci module.
Jul 12 10:25:13.243: app-140276199524096| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 12 10:25:15.269: app-140276199524096| Failed to compile module vmci!
Jul 12 10:25:15.275: app-140276199524096| Trying to find a suitable PBM set for kernel 2.6.32-23-generic.
Jul 12 10:25:15.275: app-140276199524096| Building module vmci.
Jul 12 10:25:15.275: app-140276199524096| Extracting the sources of the vmci module.
Jul 12 10:25:15.300: app-140276199524096| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-23-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jul 12 10:25:16.307: app-140276199524096| Failed to compile module vmci!

---

### Post by dacookiemonn on 2010-07-22
I get the same thing.

[COLOR="Navy"]jason@hacker:/tmp$ sudo /usr/bin/vmware
Logging to /tmp/vmware-root/setup-12664.log
filename:       /lib/modules/2.6.32-23-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-23-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-23-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-23-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-23-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-23-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-23-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-23-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-23-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-23-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
parm:           root:The directory the file system redirects to. (charp)
ERROR: modinfo: could not find module vmci
ERROR: modinfo: could not find module vsock
filename:       /lib/modules/2.6.32-23-generic/misc/vmmon.ko
supported:      external
license:        GPL v2
description:    VMware Virtual Machine Monitor.
author:         VMware, Inc.
srcversion:     9FB063A3FC33465439B2834
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
ERROR: modinfo: could not find module vmnet
filename:       /lib/modules/2.6.32-23-generic/misc/vmblock.ko
supported:      external
version:        1.1.2.0
license:        GPL v2
description:    VMware Blocking File System
author:         VMware, Inc.
srcversion:     400149ED038D22A87322D56
depends:        
vermagic:       2.6.32-23-generic SMP mod_unload modversions 
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
make -C /lib/modules/2.6.32-23-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
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
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c: In function ‘HostIFReadUptimeWork’:
/tmp/vmware-root/modules/vmmon-only/linux/hostif.c:1944: warning: ‘newUpBase’ may be used uninitialized in this function
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
make: *** /tmp/vmware-root/modules/vmnet-only: No such file or directory.  Stop.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmblock-only'
make -C /lib/modules/2.6.32-23-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmblock-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmblock-only'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-root/modules/vmblock-only'
make: *** /tmp/vmware-root/modules/vmci-only: No such file or directory.  Stop.
make: *** /tmp/vmware-root/modules/vmci-only: No such file or directory.  Stop.
Starting VMware services:
   VMware USB Arbitrator                                               done
   Virtual machine monitor                                             done
   Virtual machine communication interface                            failed
   VM communication interface socket family                           failed
   Blocking file system                                                done
   Virtual ethernet                                                   failed
[/COLOR]

---

### Post by CTritz on 2010-10-10
I am getting the same thing

[COLOR="Blue"]
Oct 10 21:14:00.596: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.598: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.600: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.602: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.603: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.614: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.616: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.617: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.619: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.621: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.624: app-140206889821952| Your GCC version: 4.4
Oct 10 21:14:00.631: app-140206889821952| Your GCC version: 4.4
Oct 10 21:14:00.653: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.655: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.657: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.659: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.660: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.663: app-140206889821952| Your GCC version: 4.4
Oct 10 21:14:00.669: app-140206889821952| Your GCC version: 4.4
Oct 10 21:14:00.697: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.699: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.701: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.702: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.704: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.834: app-140206889821952| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 10 21:14:00.835: app-140206889821952| Building module vmmon.
Oct 10 21:14:00.835: app-140206889821952| Extracting the sources of the vmmon module.
Oct 10 21:14:00.843: app-140206889821952| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Oct 10 21:14:02.804: app-140206889821952| Failed to compile module vmmon![/COLOR]

---

### Post by szafa on 2010-10-11
The solutions is [here]("https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635")

---

### Post by CTritz on 2010-10-11
> **szafa said:**
> The solutions is [here]("https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635")

This patch is for workstation 7.1.1 I am getting the error on vmware player 3.1.2

---

### Post by CTritz on 2010-10-12
Here you go. This patch got it working for me.

[http://www.apleben.com/2010/10/vmware-workstation-7-1-patch-for-linux-kernel-2-6-35/](http://www.apleben.com/2010/10/vmware-workstation-7-1-patch-for-linux-kernel-2-6-35/)

---

### Post by CTritz on 2010-10-12
> **szafa said:**
> The solutions is [here]("https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635")

Correction, I just ran into the same problem on my desktop. I had to do moth patches to get it to run.


> 
Here you go. This patch got it working for me.


[http://www.apleben.com/2010/10/vmwar...kernel-2-6-35/](http://www.apleben.com/2010/10/vmwar...kernel-2-6-35/)


---

### Post by rhigmus on 2011-05-17
> **szafa said:**
> The solutions is [here]("https://sites.google.com/site/lightrush/random-1/vmwareplayeronubuntulucidormaverickrunningkernel2635")

thanks so much! that worked perfectly.

---

