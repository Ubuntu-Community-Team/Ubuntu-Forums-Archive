---
title: "Error building ATI package"
date: 2010-03-23
forum: General Help
---

### Post by JuLx6 on 2010-03-23
Hi there !

I'm trying to install the latest ATI proprietary driver on Karmic.

I do everything as stated on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI/](https://help.ubuntu.com/community/BinaryDriverHowto/ATI/) but the package build ends with the errors below.

Can Anyone help ? Thanks !


dh_shlibdeps -pxorg-driver-fglrx   "-Xlib32" 
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx from: /usr/lib/libGL.so.1.2
dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: symbol XextCreateExtension used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XRead used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextAddDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XReply used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol _XFlush used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextRemoveDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: warning: symbol XextFindDisplay used by debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0 found in none of the libraries.
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/xorg-driver-fglrx/usr/sbin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: *** [binary-predeb-IMPL/xorg-driver-fglrx] Error 1
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.AnTBUw

---

### Post by davidjellison on 2010-03-31
I have run in to the same issue building the Ubuntu packages from the AIT/AMD 10.3 drivers

I am building on 9.10 64bit desktop.

dpkg-shlibdeps: warning: diversions involved - output may be incorrect
 diversion by xorg-driver-fglrx to: /usr/lib/fglrx/libGL.so.1.2.xlibmesa

---

### Post by dabby_yo on 2010-03-31
Why are you doing that? Just select the automatic option.

---

