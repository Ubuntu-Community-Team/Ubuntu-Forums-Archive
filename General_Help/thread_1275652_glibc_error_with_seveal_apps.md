---
title: "glibc error with seveal apps"
date: 2009-09-26
forum: General Help
---

### Post by MrIdentical on 2009-09-26
Hi guys,

Having some problems with certain apps, such as opera and gtk-gnutella. When I attempt to open them, I get a few lines shouted back at me about some glibc error. Been a while since I used Ubuntu so I'm not sure what to do. It's a relatively new install and I haven't run any massive updates or anything. Here's what happens when I try to open Opera.

josh@lappy:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.2.3' not found (required by /usr/lib/opera/opera)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/opera/opera)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libqt-mt.so.3)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/libqt-mt.so.3)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libX11.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/libX11.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libX11.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.2' not found (required by /usr/lib/libX11.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libXext.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libXext.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libSM.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libSM.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libICE.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/libICE.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.2' not found (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_PRIVATE' not found (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.2.4' not found (required by /lib/libgcc_s.so.1)
/usr/lib/opera/opera: /lib/ld-linux.so.2: version `GLIBC_2.1.1' not found (required by /usr/lib/libc.so.6)
/usr/lib/opera/opera: /lib/ld-linux.so.2: version `GLIBC_2.2' not found (required by /usr/lib/libc.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libfontconfig.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libfontconfig.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libaudio.so.2)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/libaudio.so.2)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libaudio.so.2)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libXt.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/libXt.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libXt.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.2' not found (required by /usr/lib/libXt.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libpng12.so.0)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libpng12.so.0)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libXi.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libXi.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libXcursor.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/libXcursor.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libXft.so.2)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib/libXft.so.2)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libXft.so.2)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libfreetype.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libfreetype.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libxcb.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libxcb.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.2' not found (required by /usr/lib/libxcb.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libXau.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib/libXau.so.6)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /lib/libuuid.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3' not found (required by /lib/libuuid.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /lib/libuuid.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libexpat.so.1)
/usr/lib/opera/opera: /usr/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libXdmcp.so.6)

And here's the result of uname -a

Linux lappy 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

It's a Toshiba Satellite L300/0FM if that's any help

thanks in advance!

:guitar:

---

### Post by MrIdentical on 2009-09-27
Hey thanks for the help guys!

Slowly everything disintegrated until I couldn't even get nano to work! And this is the third time in three weeks it's done it!

Seems like Ubuntu has dropped a few balls since Breezy, I've lost my faith. Going back to Vista.

:mad:

---

