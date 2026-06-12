---
title: "Error compiling linux-wlan-ng-0.2.1-pre26"
date: 2006-03-22
forum: General Help
---

### Post by emediquei on 2006-03-22
Hi there, I'm getting an error when compiling linux-wlan-ng-0.2.1-pre26. I get the same error when compiling linux-wlan-ng-0.2.1-pre25. I can compile linux-wlan-ng-0.2.3 fine, but I need 0.2.1-pre26 because of a patch.


The output of "make all" is included below. Please tell me if you know what can be causing this problem.

Thanks in advance,
Manuel Cabral

set -e; for d in src doc man etc; do make -C $d ; done
make[1]: Entering directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src'
set -e; for d in mkmeta p80211 prism2 shared wlanctl wland nwepgen wlancfg; do make WLAN_SRC=/usr/src/linux-wlan-ng-0.2.1-pre26/src/ -C $d ; done
make[2]: Entering directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src/mkmeta'
gcc -E -M -I../include -I/lib/modules/2.6.12-9-686/build/include -D__LINUX_WLAN__ ../shared/p80211types.c ../shared/p80211metamsg.c ../shared/p80211metamib.c ../shared/p80211meta.c  mkmetadef.c ../shared/p80211types.c ../shared/p80211metamsg.c ../shared/p80211metamib.c ../shared/p80211meta.c  mkmetastruct.c > .depend
mkdir -p obj
gcc -c -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -I../include -I/lib/modules/2.6.12-9-686/build/include -D__LINUX_WLAN__ ../shared/p80211types.c -o obj/p80211types.o
gcc -c -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -I../include -I/lib/modules/2.6.12-9-686/build/include -D__LINUX_WLAN__ ../shared/p80211metamsg.c -o obj/p80211metamsg.o
gcc -c -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -I../include -I/lib/modules/2.6.12-9-686/build/include -D__LINUX_WLAN__ ../shared/p80211metamib.c -o obj/p80211metamib.o
gcc -c -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -I../include -I/lib/modules/2.6.12-9-686/build/include -D__LINUX_WLAN__ ../shared/p80211meta.c -o obj/p80211meta.o
gcc -c -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -I../include -I/lib/modules/2.6.12-9-686/build/include -D__LINUX_WLAN__ mkmetadef.c -o obj/mkmetadef.o
gcc  -o mkmetadef obj/p80211types.o obj/p80211metamsg.o obj/p80211metamib.o obj/p80211meta.o  obj/mkmetadef.o
cat mkmetadefhead.txt > ../include/wlan/p80211metadef.h
./mkmetadef >> ../include/wlan/p80211metadef.h
echo "#endif" >> ../include/wlan/p80211metadef.h
gcc -c -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -I../include -I/lib/modules/2.6.12-9-686/build/include -D__LINUX_WLAN__ mkmetastruct.c -o obj/mkmetastruct.o
gcc  -o mkmetastruct obj/p80211types.o obj/p80211metamsg.o obj/p80211metamib.o obj/p80211meta.o  obj/mkmetastruct.o
cat mkmetastructhead.txt > ../include/wlan/p80211metastruct.h
./mkmetastruct >> ../include/wlan/p80211metastruct.h
echo "#endif" >> ../include/wlan/p80211metastruct.h
make[2]: Leaving directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src/mkmeta'
make[2]: Entering directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211'
if test ! -d /usr/src/linux-wlan-ng-0.2.1-pre26/src//.tmp_versions; then \
        if test -d /lib/modules/2.6.12-9-686/build/.tmp_versions; then \
                cp -rf /lib/modules/2.6.12-9-686/build/.tmp_versions /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/../ ; \
        fi ; \
fi
if test ! -e /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/Module.symvers ; then \
        cp /lib/modules/2.6.12-9-686/build/Module.symvers /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/../ ; \
fi
make -C /lib/modules/2.6.12-9-686/build M=/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211 WLAN_SRC=/usr/src/linux-wlan-ng-0.2.1-pre26/src/ MODVERDIR=/usr/src/linux-wlan-ng-0.2.1-pre26/src//.tmp_versions modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CC [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211mod.o
  CC [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211conv.o
  CC [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211req.o
/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211req.c: In function `p80211req_dorequest':
/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211req.c:160: warning: passing arg 2 of `test_and_set_bit' from incompatible pointer type
/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211req.c:173: warning: passing arg 2 of `clear_bit' from incompatible pointer type
  CC [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211frm.o
  CC [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211wep.o
  CC [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211wext.o
/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211wext.c:172:2: warning: #warning "make a smarter sharedkey/opensystem auth decision"
/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211wext.c:438:2: warning: #warning "get rid of p2mib here"
/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211wext.c:748:2: warning: #warning "Get rid of p2mib here!"
  CC [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211netdev.o
  LD [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211.o
  Building modules, stage 2.
  MODPOST
  CC      /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211.mod.o
  LD [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211/p80211.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
make[2]: Leaving directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src/p80211'
make[2]: Entering directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2'
set -e; for d in driver ridlist download; do make -C $d ; done
make[3]: Entering directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver'
make -C /lib/modules/2.6.12-9-686/build M=/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver WLAN_SRC=/usr/src/linux-wlan-ng-0.2.1-pre26/src/ \
        MODVERDIR=/usr/src/linux-wlan-ng-0.2.1-pre26/src//.tmp_versions modules
make[4]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CC [M]  /usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2_cs.o
In file included from /usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2_cs.c:2:
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:476: error: redefinition of 'hfa384x_drvr_getconfig16'
include/prism2/hfa384x.h:2750: error: previous definition of 'hfa384x_drvr_getconfig16' was here
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:511: error: redefinition of 'hfa384x_drvr_getconfig32'
include/prism2/hfa384x.h:2761: error: previous definition of 'hfa384x_drvr_getconfig32' was here
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c: In function `hfa384x_cmd_access':
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:1877: error: structure has no member named `resp0'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c: In function `hfa384x_drvr_mmi_read':
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2242: error: structure has no member named `resp0'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c: In function `hfa384x_docmd_wait':
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2848: error: structure has no member named `status'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2849: error: structure has no member named `resp0'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2850: error: structure has no member named `resp1'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2851: error: structure has no member named `resp2'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2854: error: structure has no member named `status'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c: In function `hfa384x_dl_docmd_wait':
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2945: error: structure has no member named `status'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2946: error: structure has no member named `resp0'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2947: error: structure has no member named `resp1'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2948: error: structure has no member named `resp2'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/hfa384x.c:2950: error: structure has no member named `status'
In file included from /usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2_cs.c:3:
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c: In function `prism2mgmt_low_level':
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c:1950: error: structure has no member named `resp0'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c:1951: error: structure has no member named `resp1'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c:1952: error: structure has no member named `resp2'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c: In function `prism2mgmt_test_command':
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c:1999: error: structure has no member named `status'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c:2001: error: structure has no member named `resp0'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c:2003: error: structure has no member named `resp1'
/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2mgmt.c:2005: error: structure has no member named `resp2'
make[5]: *** [/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver/prism2_cs.o] Error 1
make[4]: *** [_module_/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
make[3]: *** [default] Error 2
make[3]: Leaving directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2/driver'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src/prism2'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-wlan-ng-0.2.1-pre26/src'
make: *** [all] Error 2

---

