---
title: "Can't compile driver module with custom kernel"
date: 2010-06-16
forum: General Help
---

### Post by xefix on 2010-06-16
I was trying to compile my own kernel to make sure that all the USB drivers (uhci-hcd and ehci-hcd) were installed as modules and not compiled as part of the kernel because I would like to disable them temporarily. I used kernel version 2.6.35-rc3 from kernel.org

Then, I tried to compile ndiswrapper from source, but the compiler keeps failing with the following list of errors:


olga@oberon:~/Desktop/ndiswrapperstuff/ndiswrapper-1.54$ sudo make KBUILD=/home/olga/Desktop/linux-2.6.35-rc3
make -C driver
make[1]: Entering directory `/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver'
make -C /home/olga/Desktop/linux-2.6.35-rc3 M=/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver
make[2]: Entering directory `/home/olga/Desktop/linux-2.6.35-rc3'
  MKEXPORT /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/crt_exports.h
  CC [M]  /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/crt.o
  MKEXPORT /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/hal_exports.h
  CC [M]  /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/hal.o
  MKEXPORT /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/ndis_exports.h
  CC [M]  /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/ndis.o
  MKEXPORT /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/ntoskernel_exports.h
  CC [M]  /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/ntoskernel.o
  MKEXPORT /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/ntoskernel_io_exports.h
  CC [M]  /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/ntoskernel_io.o
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/ntoskernel_io.c: In function ‘IoConnectInterrupt’:
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/ntoskernel_io.c:566: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:130: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
  MKEXPORT /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/rtl_exports.h
  CC [M]  /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/rtl.o
  CC [M]  /home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.o
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c: In function ‘set_multicast_list’:
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:953: error: ‘struct net_device’ has no member named ‘mc_count’
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:956: error: ‘struct net_device’ has no member named ‘mc_count’
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:960: warning: type defaults to ‘int’ in declaration of ‘_min2’
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:967: error: ‘struct net_device’ has no member named ‘mc_list’
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:968: error: dereferencing pointer to incomplete type
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:969: error: dereferencing pointer to incomplete type
/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.c:971: error: dereferencing pointer to incomplete type
make[3]: *** [/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver] Error 2
make[2]: Leaving directory `/home/olga/Desktop/linux-2.6.35-rc3'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/olga/Desktop/ndiswrapperstuff/ndiswrapper-1.54/driver'
make: *** [all] Error 2


Any idea what is going wrong? Did I mess up compiling and installing the new kernel?

---

### Post by dino99 on 2010-06-16
trusted ppa with latest releases:

[https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=lucid](https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=lucid)

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by xefix on 2010-06-16
How is the kernel at that link different from the one I installed? Are you saying that I should try recompiling the kernel again?

---

### Post by xefix on 2010-06-16
I've tried to recompile the kernel again, now using source version 2.6.34. However, that didn't help - I was getting errors with the post-installation script update-grub and the kernel would only partially configure. I commented out the pre-installation and post-installation portions of the .config file (I don't need grub anyway, as I boot into Lucid using Fedora's grub) and the kernel seemed to finish installing fine. Ndiswrapper also installed fine, as did the WinXP driver I was trying to run with it. However, when I try to sudo modprobe ndiswrapper, I again get the error:

FATAL: Module ndiswrapper not found

This was happening before I tried to recompile ndiswrapper for my kernel. Running the module assistant also doesn't help. When I select prepare, it seems to check linux-headers and build-essential; everything goes through fine. However, when I select ndiswrapper and ask m-a to build it for the current kernel, I get the following errors:

1. 
Installation of the ndiswrapper-source source failed.                                                                           &#9646; 

 Ignoring this package. Maybe you need to add something to           
sources.list, maybe the contrib and non-free archives. 

2.  Bad luck, the kernel headers for the target kernel version could   
     not be found
     and you did not specify other valid kernel headers to use.

3. However, you can install the header files for your kernel which   
 are provided by the linux-headers-2.6.34 package. For most       
 modules packages, these files are perfectly sufficient without     
 having the original kernel source.                                 
                                                                   
 To install the package, run the PREPARE command from the main  
 menu, or on the command line:                                      
                                                                    
 module-assistant prepare

---

