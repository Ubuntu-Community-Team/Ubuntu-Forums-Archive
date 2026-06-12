---
title: "Adobe Reader/acroread won't start on 64 bit Natty machine"
date: 2011-05-03
forum: General Help
---

### Post by blimbo on 2011-05-03
Hi everyone,

I can't get acroread (9.4.2-0natty1) to start on my 64 bit Natty box. 

tnugent@translocon:/$ acroread 
/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libgdk_pixbuf_xlib-2.0.so.0: wrong ELF class: ELFCLASS64

The only version of that .so on the machine is the 64 bit version:

tnugent@translocon:/$ find /usr/ -name 'libgdk_pixbuf_xlib-2.0.so.0'
/usr/lib/libgdk_pixbuf_xlib-2.0.so.0
tnugent@translocon:/$ ll /usr/lib/libgdk_pixbuf_xlib-2.0.so.0
lrwxrwxrwx 1 root root 34 2011-05-03 11:41 /usr/lib/libgdk_pixbuf_xlib-2.0.so.0 -> libgdk_pixbuf_xlib-2.0.so.0.2300.3
tnugent@translocon:/$ file /usr/lib/libgdk_pixbuf_xlib-2.0.so.0.2300.3
/usr/lib/libgdk_pixbuf_xlib-2.0.so.0.2300.3: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

I have ia32-libs installed (20110310) and /usr/lib32 is populated with files.

I found some threads with similar problems that suggested including /usr/lib32 in LD_LIBRARY_PATH but this does not help.

Anyone had this issue?

Cheers,

Tim

---

### Post by blimbo on 2011-05-04
Managed to resolve this by looking at how it works on my Maverick box. Here I had a different version of ia32-libs installed (via the wine ppa) so I installed that on Natty (without any problems or needing to force) and now my acroread fires up :-)

[https://launchpad.net/~ubuntu-wine/+archive/ppa/+files/ia32-libs_20090808ubuntu10~wineppa4_amd64.deb](https://launchpad.net/~ubuntu-wine/+archive/ppa/+files/ia32-libs_20090808ubuntu10~wineppa4_amd64.deb)

---

