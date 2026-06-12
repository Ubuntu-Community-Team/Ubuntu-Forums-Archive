---
title: "Driver installation issue"
date: 2009-11-15
forum: General Help
---

### Post by UltraFlynn on 2009-11-15
I've recently upgraded to 9.10 and my network drivers (both wired and wireless) seem to have been over-written. I've tracked down what I need to be able to install them again but on both I've got issues with my Ubuntu installation.

This is the log whilst trying to make the wireless driver:

```
ultraflynn@fizgig:~/Linux/rtl8187se_coffee$ ./makedrv 
make -C /lib/modules/2.6.31-14-generic/build M=/home/ultraflynn/Linux/rtl8187se_coffee/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ultraflynn/Linux/rtl8187se_coffee/ieee80211/ieee80211_module.o
/home/ultraflynn/Linux/rtl8187se_coffee/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/ultraflynn/Linux/rtl8187se_coffee/ieee80211/ieee80211_module.c:116: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/ultraflynn/Linux/rtl8187se_coffee/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/ultraflynn/Linux/rtl8187se_coffee/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2
cp: cannot stat `Module.symvers': No such file or directory
make -C /lib/modules/2.6.31-14-generic/build M=/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.o
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c: In function ‘rtl8180_shutdown’:
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c:203: error: ‘struct net_device’ has no member named ‘stop’
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c: In function ‘rtl8180_init’:
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c:4640: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c: In function ‘rtl8180_pci_probe’:
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c:6027: error: ‘struct net_device’ has no member named ‘open’
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c:6028: error: ‘struct net_device’ has no member named ‘stop’
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c:6030: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c:6032: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c:6033: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.c:6034: error: ‘struct net_device’ has no member named ‘set_mac_address’
make[2]: *** [/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/ultraflynn/Linux/rtl8187se_coffee/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [modules] Error 2
```

I'm convinced that my ubuntu installation has something set up wrong. i.e. I this it's looking in the wrong place for it's linux source files.

All suggestions gratefully accepted because I've spent hours on this and I'm at a loss as to how to get either of my network interfaces working.

Many thanks.

---

### Post by UltraFlynn on 2009-11-15
This is the log of trying to build the wired network driver:

```
ultraflynn@fizgig:~/Linux/r8101-1.013.00$ sudo make clean modules
[sudo] password for ultraflynn: 
make -C src/ clean
make[1]: Entering directory `/home/ultraflynn/Linux/r8101-1.013.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order
make[1]: Leaving directory `/home/ultraflynn/Linux/r8101-1.013.00/src'
make -C src/ modules
make[1]: Entering directory `/home/ultraflynn/Linux/r8101-1.013.00/src'
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC      kernel/bounds.s
  GEN     /src/include/linux/bounds.h
  CC      arch/x86/kernel/asm-offsets.s
  GEN     /src/include/asm/asm-offsets.h
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
strip --strip-debug r8101.ko
strip: 'r8101.ko': No such file
make[1]: *** [modules] Error 1
make[1]: Leaving directory `/home/ultraflynn/Linux/r8101-1.013.00/src'
make: *** [modules] Error 2
```

---

