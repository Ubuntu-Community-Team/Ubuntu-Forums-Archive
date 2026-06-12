---
title: "WPC11 Packet Injection wlan-ng"
date: 2006-04-29
forum: General Help
---

### Post by LBCLinux on 2006-04-29
Hi, I have a WPC11 working using wlan-ng and the prism2 driver. The card works in monitor mode but will not inject packets. I downloaded the source and patched the drivers but can't compile.
Thanks-

---

### Post by Jason_25 on 2006-04-29
Have you installed build-essential and your kernel headers?

---

### Post by LBCLinux on 2006-04-29
Yes they are both installed. Also, I removed all of the unpatched wlan-ng information which I had previously installed.

---

### Post by LBCLinux on 2006-04-29
sbs@ubuntu:~/Desktop/linux-wlan-ng-0.2.1-pre26$ make all
set -e; for d in src doc man etc; do make -C $d ; done
make[1]: Entering directory `/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src'
set -e; for d in mkmeta p80211 prism2 shared wlanctl wland nwepgen wlancfg; do make WLAN_SRC=/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/ -C $d ; done
make[2]: Entering directory `/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/mkmeta'
gcc -E -M -I../include -I/lib/modules/2.6.15-21-386/build/include -D__LINUX_WLAN__ ../shared/p80211types.c ../shared/p80211metamsg.c ../shared/p80211metamib.c ../shared/p80211meta.c  mkmetadef.c ../shared/p80211types.c ../shared/p80211metamsg.c ../shared/p80211metamib.c ../shared/p80211meta.c  mkmetastruct.c > .depend
make[2]: Leaving directory `/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/mkmeta'
make[2]: Entering directory `/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/mkmeta'
mkdir -p obj
make[2]: Leaving directory `/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/mkmeta'
make[2]: Entering directory `/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211'
if test ! -d /home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src//.tmp_versions; then \
                if test -d /lib/modules/2.6.15-21-386/build/.tmp_versions; then \
                        cp -rf /lib/modules/2.6.15-21-386/build/.tmp_versions /home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211/../ ; \
                fi ; \
        fi
if test ! -e /home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211/Module.symvers ; then \
                cp /lib/modules/2.6.15-21-386/build/Module.symvers /home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211/../ ; \
        fi
make -C /lib/modules/2.6.15-21-386/build M=/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211 WLAN_SRC=/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/ MODVERDIR=/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src//.tmp_versions modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.15-21-386'
  CC [M]  /home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211mod.o
In file included from /home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211mod.c:73:
include/wlan/wlan_compat.h:146:7: warning: "WLAN_HOSTIF" is not defined
include/wlan/wlan_compat.h:146:22: warning: "WLAN_PCI" is not defined
/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211mod.c:211: error: &#8216;p802addr_to_str&#8217; undeclared here (not in a function)
make[4]: *** [/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211mod.o] Error 1
make[3]: *** [_module_/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.15-21-386'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src/p80211'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/sbs/Desktop/linux-wlan-ng-0.2.1-pre26/src'
make: *** [all] Error 2

---

