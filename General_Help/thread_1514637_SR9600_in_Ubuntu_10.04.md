---
title: "SR9600 in Ubuntu 10.04"
date: 2010-06-21
forum: General Help
---

### Post by anandogc on 2010-06-21
Is it possible to make USB to LAN adapter model SR9600  work in Lynx. It is made in China. Only Windows driver is available with it.
There is a post [http://21500.net/?p=616](http://21500.net/?p=616) that describes how to teak DM9601 driver to make it work with SR9600 but it is made for old kernel. the latest Ununtu kernel has changed some structure API&#347;


anandogc@ubuntu:/media/Anando/9601$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0fe6:8101  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 017: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 002 Device 003: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


anandogc@ubuntu:/media/Anando/9601$ make
make -C /lib/modules/2.6.32-22-generic/build M=/media/Anando/9601 LDDINCDIR=/media/Anando/9601/../include modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /media/Anando/9601/dm9601.o
/media/Anando/9601/dm9601.c: In function ‘__check_reg5’:
/media/Anando/9601/dm9601.c:124: warning: return from incompatible pointer type
/media/Anando/9601/dm9601.c: In function ‘__check_reg8’:
/media/Anando/9601/dm9601.c:125: warning: return from incompatible pointer type
/media/Anando/9601/dm9601.c: In function ‘__check_reg9’:
/media/Anando/9601/dm9601.c:126: warning: return from incompatible pointer type
/media/Anando/9601/dm9601.c: In function ‘__check_rega’:
/media/Anando/9601/dm9601.c:127: warning: return from incompatible pointer type
/media/Anando/9601/dm9601.c: In function ‘__check_nfloor’:
/media/Anando/9601/dm9601.c:128: warning: return from incompatible pointer type
/media/Anando/9601/dm9601.c: In function ‘ctrl_callback’:
/media/Anando/9601/dm9601.c:160: error: implicit declaration of function ‘warn’
/media/Anando/9601/dm9601.c: In function ‘write_bulk_callback’:
/media/Anando/9601/dm9601.c:506: error: implicit declaration of function ‘info’
/media/Anando/9601/dm9601.c: In function ‘dm9601_tx_timeout’:
/media/Anando/9601/dm9601.c:570: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c: In function ‘dm9601_start_xmit’:
/media/Anando/9601/dm9601.c:586: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c: In function ‘dm9601_netdev_stats’:
/media/Anando/9601/dm9601.c:627: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c: In function ‘init_dm9601’:
/media/Anando/9601/dm9601.c:755: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c: In function ‘dm9601_open’:
/media/Anando/9601/dm9601.c:795: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c: In function ‘dm9601_close’:
/media/Anando/9601/dm9601.c:831: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c: In function ‘dm9601_ioctl’:
/media/Anando/9601/dm9601.c:864: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c: In function ‘dm9601_set_multicast’:
/media/Anando/9601/dm9601.c:900: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c: In function ‘dm9601_probe’:
/media/Anando/9601/dm9601.c:980: error: ‘struct net_device’ has no member named ‘priv’
/media/Anando/9601/dm9601.c:981: error: ‘struct net_device’ has no member named ‘open’
/media/Anando/9601/dm9601.c:982: error: ‘struct net_device’ has no member named ‘stop’
/media/Anando/9601/dm9601.c:984: error: ‘struct net_device’ has no member named ‘tx_timeout’
/media/Anando/9601/dm9601.c:985: error: ‘struct net_device’ has no member named ‘do_ioctl’
/media/Anando/9601/dm9601.c:986: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/media/Anando/9601/dm9601.c:987: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/media/Anando/9601/dm9601.c:988: error: ‘struct net_device’ has no member named ‘get_stats’
make[2]: *** [/media/Anando/9601/dm9601.o] Error 1
make[1]: *** [_module_/media/Anando/9601] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [default] Error 2

---

