---
title: "Error while compiling RTL8187 patched driver"
date: 2009-07-26
forum: General Help
---

### Post by JayUK20 on 2009-07-26
I have already got this working but I am trying it again within a Virtual Machine in Windows. The driver is the patched driver for RTL8187 and I am following the guide from [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187) - I have tried both versions of the patch but I keep getting this error.

However when I try the "make" command I get this error:

> rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/2.6.28-13-generic/build M=/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_tx.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_module.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211-rtl.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211-rtl.ko
  CC      /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_crypt_wep-rtl.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: Leaving directory `/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/ieee80211'
chmod +x symvers
./symvers
make -C beta-8187 all
make[1]: Entering directory `/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/beta-8187'
make -C /lib/modules/2.6.28-13-generic/build M=/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/beta-8187 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-13-generic'
  CC [M]  /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o
In file included from /home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:65:
/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:47:27: error: asm/semaphore.h: No such file or directory
make[3]: *** [/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.o] Error 1
make[2]: *** [_module_/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/beta-8187] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/vbox/Aircrack/rtl8187_linux_26.1010.0622.2006/beta-8187'
make: *** [all] Error 2

---

### Post by Murdoc_of_puts on 2009-10-10
Do you have the build-essentials/and the sqlite dev files?  Just trying to cover some basics.

---

### Post by 3rdalbum on 2009-10-10
Whoa, that's a big thread bump.

---

### Post by Murdoc_of_puts on 2009-10-11
Ok, so now I'm getting the same error message as JayUK20.  When I tried patching it pooped out this error file. So now I'm Kind of at a loss of wtf is going on. GRRRR.

--JayUK20 what kernel version is compiled on your v-box? ( check with 'uname -mr' ), I ask because there's alot of different kernel patches in the aircrack/patches folder (which is also all of the ones they have on their site)....so you might want to try a couple, or maybe you were trying the wrong k ver.  My comp is eternally F!d so hopefully yours isn't.

---

