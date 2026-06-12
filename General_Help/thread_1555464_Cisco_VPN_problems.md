---
title: "Cisco VPN problems"
date: 2010-08-18
forum: General Help
---

### Post by rpakalns on 2010-08-18
Hi!

I was trying to compile my Cisco VPN client and got the following error:

Directory containing linux kernel source code [/lib/modules/2.6.32-21-generic-pae/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.32-21-generic-pae/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.32-21-generic-pae/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.32-21-generic-pae/build SUBDIRS=/home/pakalns/Downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic-pae'
  CC [M]  /home/pakalns/Downloads/vpnclient/interceptor.o
/home/pakalns/Downloads/vpnclient/interceptor.c: In function ‘interceptor_init’:
/home/pakalns/Downloads/vpnclient/interceptor.c:132: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/pakalns/Downloads/vpnclient/interceptor.c:133: error: ‘struct net_device’ has no member named ‘get_stats’
/home/pakalns/Downloads/vpnclient/interceptor.c:134: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/pakalns/Downloads/vpnclient/interceptor.c: In function ‘add_netdev’:
/home/pakalns/Downloads/vpnclient/interceptor.c:271: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/pakalns/Downloads/vpnclient/interceptor.c:272: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/pakalns/Downloads/vpnclient/interceptor.c: In function ‘remove_netdev’:
/home/pakalns/Downloads/vpnclient/interceptor.c:294: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/pakalns/Downloads/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/pakalns/Downloads/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic-pae'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Have you any idea what might be wrong? 

Thank you!
Roberts

---

