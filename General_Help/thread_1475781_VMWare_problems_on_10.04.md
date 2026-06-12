---
title: "VMWare problems on 10.04"
date: 2010-05-07
forum: General Help
---

### Post by Sammaye on 2010-05-07
Hey all,

I just upgraded to 10.04 and my vmware workstation 7 needed to update with the new kernel headers so I placed the update but it won't update.

With some digging I found this link:[http://communities.vmware.com/message/1401588#1401588](http://communities.vmware.com/message/1401588#1401588)

But either I don't understand it's instructions or it don't work since I get this output from running the sh file. I was hoping someone else has had to do this and could point me in the right direction.

```
mkdir: cannot create directory `original': File exists
patching file patched/vmci-only/linux/vmciKernelIf.c
Hunk #1 FAILED at 36.
1 out of 1 hunk FAILED -- saving rejects to file patched/vmci-only/linux/vmciKernelIf.c.rej
patching file patched/vmnet-only/vnetUserListener.c
Hunk #1 FAILED at 32.
1 out of 1 hunk FAILED -- saving rejects to file patched/vmnet-only/vnetUserListener.c.rej
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.32-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make -C $PWD SRCROOT=$PWD/. \
	  MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
Built vmmon module
make: Entering directory `/tmp/vmware-root/modules/vmnet-only'
make: *** No rule to make target `auto-build'. Stop.
make: Leaving directory `/tmp/vmware-root/modules/vmnet-only'
Unable to install vmnet

```


Thanks,

Sammaye

---

### Post by cisforcojo on 2010-05-12
Same problem here.

EDIT: See my post here re: how to solve this problem:
[http://ubuntuforums.org/showthread.php?p=9287124#post9287124](http://ubuntuforums.org/showthread.php?p=9287124#post9287124)

---

