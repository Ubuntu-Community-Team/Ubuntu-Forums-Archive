---
title: "can't compile zd1211 driver"
date: 2009-10-11
forum: General Help
---

### Post by l3git.h4cker on 2009-10-11
Ok, so I googled this problem for nearly 2 days and found nothing that will fix this problem.

I am trying to compile the zd1211 wireless driver, and I keep getting this error:
```

...

make -C /lib/modules/2.6.24-24-generic/build SUBDIRS=/usr/src/zd1211/branches/vendor modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /usr/src/zd1211/branches/vendor/src/zd1205.o
cc1: error: unrecognized command line option "-fno-stack-protector"
cc1: error: unrecognized command line option "-Wno-pointer-sign"
/usr/src/zd1211/branches/vendor/src/zd1205.c:1: error: bad value (generic) for -mtune= switch
make[4]: *** [/usr/src/zd1211/branches/vendor/src/zd1205.o] Error 1
make[3]: *** [_module_/usr/src/zd1211/branches/vendor] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/zd1211/branches/vendor'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/usr/src/zd1211/branches/vendor'
make: *** [all] Error 2

```or
```

...

/usr/src/zd1211/branches/vendor/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
/usr/src/zd1211/branches/vendor/src/zd1205.c:454: warning: initialization from incompatible pointer type
/usr/src/zd1211/branches/vendor/src/zd1205.c:481: error: expected declaration specifiers or ‘...’ before ‘write’
/usr/src/zd1211/branches/vendor/src/zd1205.c:481: error: expected declaration specifiers or ‘...’ before ‘fd’
/usr/src/zd1211/branches/vendor/src/zd1205.c:481: error: expected declaration specifiers or ‘...’ before ‘buf’
/usr/src/zd1211/branches/vendor/src/zd1205.c:481: error: expected declaration specifiers or ‘...’ before ‘count’
/usr/src/zd1211/branches/vendor/src/zd1205.c:482: warning: type defaults to ‘int’ in declaration of ‘_syscall3’
/usr/src/zd1211/branches/vendor/src/zd1205.c:482: error: expected ‘,’ or ‘;’ before ‘_syscall3’
/usr/src/zd1211/branches/vendor/src/zd1205.c:490: error: ‘dot11A_Channel’ undeclared here (not in a function)
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zd1205_rx_isr’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:4239: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zd1205_ioctl_setmode’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:6754: warning: passing argument 2 of ‘test_and_set_bit’ from incompatible pointer type
/usr/src/zd1211/branches/vendor/src/zd1205.c:6830: warning: passi/usr/src/zd1211/branches/vendor/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
/usr/src/zd1211/branches/vendor/src/zd1205.c:454: warning: initialization from incompatible pointer type
/usr/src/zd1211/branches/vendor/src/zd1205.c:481: error: expected declaration specifiers or ‘...’ before ‘write’
/usr/src/zd1211/branches/vendor/src/zd1205.c:481: error: expected declaration specifiers or ‘...’ before ‘fd’
/usr/src/zd1211/branches/vendor/src/zd1205.c:481: error: expected declaration specifiers or ‘...’ before ‘buf’
/usr/src/zd1211/branches/vendor/src/zd1205.c:481: error: expected declaration specifiers or ‘...’ before ‘count’
/usr/src/zd1211/branches/vendor/src/zd1205.c:482: warning: type defaults to ‘int’ in declaration of ‘_syscall3’
/usr/src/zd1211/branches/vendor/src/zd1205.c:482: error: expected ‘,’ or ‘;’ before ‘_syscall3’
/usr/src/zd1211/branches/vendor/src/zd1205.c:490: error: ‘dot11A_Channel’ undeclared here (not in a function)
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zd1205_rx_isr’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:4239: error: ‘struct sk_buff’ has no member named ‘mac’
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zd1205_ioctl_setmode’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:6754: warning: passing argument 2 of ‘test_and_set_bit’ from incompatible pointer type
/usr/src/zd1211/branches/vendor/src/zd1205.c:6830: warning: passing argument 2 of ‘clear_bit’ from incompatible pointer type
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zd1205_load_card_setting’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:8682: error: implicit declaration of function ‘open’
/usr/src/zd1211/branches/vendor/src/zd1205.c:8700: error: implicit declaration of function ‘read’
/usr/src/zd1211/branches/vendor/src/zd1205.c:8704: error: implicit declaration of function ‘close’
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zd1205_save_card_setting’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:8857: error: implicit declaration of function ‘write’
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zdcb_rx_ind’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:9882: error: implicit declaration of function ‘eth_copy_and_sum’
make[4]: *** [/usr/src/zd1211/branches/vendor/src/zd1205.o] Error 1
make[3]: *** [_module_/usr/src/zd1211/branches/vendor] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/zd1211/branches/vendor'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/usr/src/zd1211/branches/vendor'
make: *** [all] Error 2
ng argument 2 of ‘clear_bit’ from incompatible pointer type
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zd1205_load_card_setting’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:8682: error: implicit declaration of function ‘open’
/usr/src/zd1211/branches/vendor/src/zd1205.c:8700: error: implicit declaration of function ‘read’
/usr/src/zd1211/branches/vendor/src/zd1205.c:8704: error: implicit declaration of function ‘close’
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zd1205_save_card_setting’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:8857: error: implicit declaration of function ‘write’
/usr/src/zd1211/branches/vendor/src/zd1205.c: In function ‘zdcb_rx_ind’:
/usr/src/zd1211/branches/vendor/src/zd1205.c:9882: error: implicit declaration of function ‘eth_copy_and_sum’
make[4]: *** [/usr/src/zd1211/branches/vendor/src/zd1205.o] Error 1
make[3]: *** [_module_/usr/src/zd1211/branches/vendor] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/zd1211/branches/vendor'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/usr/src/zd1211/branches/vendor'
make: *** [all] Error 2

```According to some research I did, the current kernel I have does not have the 'config.h' that zd1211 needs.

My ultimate goal is to get my usb wireless stick to use master mode, via the zd1211b wireless drivers.

Any ideas on how I might compile this d*** driver??:confused::confused::confused:
My kernel version is linux-headers-2.6.24-24.

NOTE: I DO NOT want to use the zd1211rw, for this does NOT support master mode.

---

### Post by delcypher on 2009-10-11
Er.. you haven't shown us the command you ran (but I'll assume these are configure && make commands)

> error: linux/config.h: No such file or directory


do you have the kernel development headers installed?

linux-headers-2.6 (you need to find the right package for your kernel)

---

### Post by l3git.h4cker on 2009-10-11
> **delcypher said:**
> Er.. you haven't shown us the command you ran (but I'll assume these are configure && make commands)



do you have the kernel development headers installed?

linux-headers-2.6 (you need to find the right package for your kernel)

Yes I verified that I have the linux headers installed - including references in /lib/modules.

To be clear, the config.h is present in the OLD linux kernels (i.e. 2.6.12...) I have 2.6.24...
I verified this by downloading the 2.6.12 kernel, and found the config.h in the appropriate place.

The command I ran was:

sudo make

If nobody knows the answer to my problem, then I should ask - what driver should I get for my Intel PRO/Wireless 3945ABG Network adapter such that I can use Master Mode (Access Point mode)?

---

### Post by supi007 on 2009-10-11
I also cannot compile the driver into my kernel! :confused:
I don't have any idea.
Here is my result:

```
root@nb09ulx0321sb:/var/tmp/ieee80211-1.2.18# sudo make
Checking in /lib/modules/2.6.24-24-generic for ieee80211 components...
make -C /lib/modules/2.6.24-24-generic/build M=/var/tmp/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /var/tmp/ieee80211-1.2.18/ieee80211_module.o
/var/tmp/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/var/tmp/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/var/tmp/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/var/tmp/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/var/tmp/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/var/tmp/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/var/tmp/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/var/tmp/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make: *** [modules] Error 2

```

---

### Post by baenbaen on 2010-06-17
#include <linux/config.h>

It seems not to be used anymore

#include <linux/autoconf.h>

---

