---
title: "Vmware not start?"
date: 2010-03-16
forum: General Help
---

### Post by mech7 on 2010-03-16
After long while Vmware is not working anymore.. I think because some upgrade a while ago.. but when I try to run the configure.pl then I get this error.. does anybody know what is wrong?

> root@ns:~# sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   VM communication interface socket family:                           done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-17-generic-pae/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.31-17-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. module
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic-pae'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:31:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:78: error: conflicting types for âpoll_
include/linux/poll.h:70: note: previous declaration of âpoll_initwaitâ was here
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:99:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not
In file included from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:31,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/x86apic.h:97:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.31-17-generic-pae/arch/x86/include/asm/apic.h
                 from /usr/src/linux-headers-2.6.31-17-generic-pae/arch/x86/include/asm/smp.h:
                 from include/linux/smp.h:36,
                 from include/linux/topology.h:33,
                 from include/linux/gfp.h:7,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config2/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.31-17-generic-pae/arch/x86/include/asm/apicdef.h:133:1: warning: thcation of the previous definition
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
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not define
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not define
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not define
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not define
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not define
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not define
In file included from /tmp/vmware-config2/vmmon-only/./include/vm_basic_asm.h:46,
                 from /tmp/vmware-config2/vmmon-only/./include/rateconv.h:45,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:40,
                 from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not d
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not
/tmp/vmware-config2/vmmon-only/./include/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not
In file included from /tmp/vmware-config2/vmmon-only/./include/vm_asm.h:43,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:103:
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not define
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not define
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not define
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not define
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:119:
/tmp/vmware-config2/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function âLinuxDriverSyncCallOnEachCPUâ:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1423: error: too many arguments to function âsmponâ
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function âLinuxDriver_Ioctlâ:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member
/tmp/vmware-config2/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member
/tmp/vmware-config2/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member â
/tmp/vmware-config2/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member
/tmp/vmware-config2/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member
/tmp/vmware-config2/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member
/tmp/vmware-config2/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member â
/tmp/vmware-config2/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member
/tmp/vmware-config2/vmmon-only/linux/driver.c:2007: error: too many arguments to function âsmponâ
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic-pae'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.


---

### Post by amrasurion on 2010-03-16
the problem im having is after using easy install using an ubunto 9.10 .ISO it says vmware tools isnt installed but i installed it via terminal. it says click vm > install vmware tools but will not completely boot the machine either it just comes to the black screen with the Grey(silver?) Ubuntu logo in the middle and does nothing else.
any ideas?
maybe a link to a proper install of vmware workstation for ubuntu 9.10 with the vmware tools package? i dunno. i just reall cant get it working.

---

### Post by mech7 on 2010-03-24
There is a link for a patch to compile somewhere on the internets... but i tried it and it crashes all the time in the web interface so I would not recommend it... need to wait for new version from vmware

---

