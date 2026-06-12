---
title: "Can't compile after upgrade to 12.04"
date: 2012-04-29
forum: General Help
---

### Post by DAFlippers on 2012-04-29
Both 32 and 64 bit compiles worked and then I upgraded from 11.10 to 12.04. Now -m64 works but -m32 can't find libraries.
 
I've tried reinstalling libraries, and gcc-multilib but no joy. Anyone spot something I've missed? 
 
 
David
 
```
gcc -m32 -Wall -W -L/usr/lib/x86_64-linux-gnu/libusb-1.0.so.0 -lusb-1.0
-lX11 LMSS.c -o LMSS32
/usr/bin/ld: skipping incompatible /usr/local/lib/libusb-1.0.so when searching for -lusb-1.0
/usr/bin/ld: skipping incompatible /usr/local/lib/libusb-1.0.a when searching for -lusb-1.0
/usr/bin/ld: cannot find -lusb-1.0
/usr/bin/ld: cannot find -lX11
collect2: ld returned 1 exit status
 
locate libusb-1.0
/home/david/Downloads/libusb-1.0.8
/home/david/Downloads/libusb-1.0.8.tar.bz2
/home/david/Downloads/libusb-1.0.8/AUTHORS
/home/david/Downloads/libusb-1.0.8/COPYING
/home/david/Downloads/libusb-1.0.8/ChangeLog
/home/david/Downloads/libusb-1.0.8/INSTALL
/home/david/Downloads/libusb-1.0.8/Makefile
/home/david/Downloads/libusb-1.0.8/Makefile.am
/home/david/Downloads/libusb-1.0.8/Makefile.in
/home/david/Downloads/libusb-1.0.8/NEWS
/home/david/Downloads/libusb-1.0.8/PORTING
/home/david/Downloads/libusb-1.0.8/README
/home/david/Downloads/libusb-1.0.8/THANKS
/home/david/Downloads/libusb-1.0.8/TODO
/home/david/Downloads/libusb-1.0.8/aclocal.m4
/home/david/Downloads/libusb-1.0.8/compile
/home/david/Downloads/libusb-1.0.8/config.guess
/home/david/Downloads/libusb-1.0.8/config.h
/home/david/Downloads/libusb-1.0.8/config.h.in
/home/david/Downloads/libusb-1.0.8/config.log
/home/david/Downloads/libusb-1.0.8/config.status
/home/david/Downloads/libusb-1.0.8/config.sub
/home/david/Downloads/libusb-1.0.8/configure
/home/david/Downloads/libusb-1.0.8/configure.ac
/home/david/Downloads/libusb-1.0.8/depcomp
/home/david/Downloads/libusb-1.0.8/doc
/home/david/Downloads/libusb-1.0.8/examples
/home/david/Downloads/libusb-1.0.8/install-sh
/home/david/Downloads/libusb-1.0.8/libtool
/home/david/Downloads/libusb-1.0.8/libusb
/home/david/Downloads/libusb-1.0.8/libusb-1.0.pc
/home/david/Downloads/libusb-1.0.8/libusb-1.0.pc.in
/home/david/Downloads/libusb-1.0.8/ltmain.sh
/home/david/Downloads/libusb-1.0.8/missing
/home/david/Downloads/libusb-1.0.8/stamp-h1
/home/david/Downloads/libusb-1.0.8/doc/Makefile
/home/david/Downloads/libusb-1.0.8/doc/Makefile.am
/home/david/Downloads/libusb-1.0.8/doc/Makefile.in
/home/david/Downloads/libusb-1.0.8/doc/doxygen.cfg
/home/david/Downloads/libusb-1.0.8/doc/doxygen.cfg.in
/home/david/Downloads/libusb-1.0.8/examples/.deps
/home/david/Downloads/libusb-1.0.8/examples/Makefile
/home/david/Downloads/libusb-1.0.8/examples/Makefile.am
/home/david/Downloads/libusb-1.0.8/examples/Makefile.in
/home/david/Downloads/libusb-1.0.8/examples/dpfp.c
/home/david/Downloads/libusb-1.0.8/examples/dpfp_threaded.c
/home/david/Downloads/libusb-1.0.8/examples/lsusb.c
/home/david/Downloads/libusb-1.0.8/examples/.deps/dpfp.Po
/home/david/Downloads/libusb-1.0.8/examples/.deps/dpfp_threaded-dpfp_threaded.Po
/home/david/Downloads/libusb-1.0.8/examples/.deps/lsusb.Po
/home/david/Downloads/libusb-1.0.8/libusb/.deps
/home/david/Downloads/libusb-1.0.8/libusb/.libs
/home/david/Downloads/libusb-1.0.8/libusb/Makefile
/home/david/Downloads/libusb-1.0.8/libusb/Makefile.am
/home/david/Downloads/libusb-1.0.8/libusb/Makefile.in
/home/david/Downloads/libusb-1.0.8/libusb/core.c
/home/david/Downloads/libusb-1.0.8/libusb/descriptor.c
/home/david/Downloads/libusb-1.0.8/libusb/io.c
/home/david/Downloads/libusb-1.0.8/libusb/libusb-1.0.la
/home/david/Downloads/libusb-1.0.8/libusb/libusb.h
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-core.lo
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-core.o
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-descriptor.lo
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-descriptor.o
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-io.lo
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-io.o
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-linux_usbfs.lo
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-linux_usbfs.o
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-sync.lo
/home/david/Downloads/libusb-1.0.8/libusb/libusb_1_0_la-sync.o
/home/david/Downloads/libusb-1.0.8/libusb/libusbi.h
/home/david/Downloads/libusb-1.0.8/libusb/os
/home/david/Downloads/libusb-1.0.8/libusb/sync.c
/home/david/Downloads/libusb-1.0.8/libusb/.deps/libusb_1_0_la-core.Plo
/home/david/Downloads/libusb-1.0.8/libusb/.deps/libusb_1_0_la-darwin_usb.Plo
/home/david/Downloads/libusb-1.0.8/libusb/.deps/libusb_1_0_la-descriptor.Plo
/home/david/Downloads/libusb-1.0.8/libusb/.deps/libusb_1_0_la-io.Plo
/home/david/Downloads/libusb-1.0.8/libusb/.deps/libusb_1_0_la-linux_usbfs.Plo
/home/david/Downloads/libusb-1.0.8/libusb/.deps/libusb_1_0_la-sync.Plo
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb-1.0.a
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb-1.0.la
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb-1.0.lai
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb-1.0.so
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb-1.0.so.0
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb-1.0.so.0.0.0
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb_1_0_la-core.o
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb_1_0_la-descriptor.o
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb_1_0_la-io.o
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb_1_0_la-linux_usbfs.o
/home/david/Downloads/libusb-1.0.8/libusb/.libs/libusb_1_0_la-sync.o
/home/david/Downloads/libusb-1.0.8/libusb/os/darwin_usb.c
/home/david/Downloads/libusb-1.0.8/libusb/os/darwin_usb.h
/home/david/Downloads/libusb-1.0.8/libusb/os/linux_usbfs.c
/home/david/Downloads/libusb-1.0.8/libusb/os/linux_usbfs.h
/lib/x86_64-linux-gnu/libusb-1.0.so.0
/lib/x86_64-linux-gnu/libusb-1.0.so.0.1.0
/usr/include/libusb-1.0
/usr/include/libusb-1.0/libusb.h
/usr/lib/x86_64-linux-gnu/libusb-1.0.a
/usr/lib/x86_64-linux-gnu/libusb-1.0.so
/usr/lib/x86_64-linux-gnu/libusb-1.0.so.0
/usr/lib/x86_64-linux-gnu/pkgconfig/libusb-1.0.pc
/usr/local/include/libusb-1.0
/usr/local/include/libusb-1.0/libusb.h
/usr/local/lib/libusb-1.0.a
/usr/local/lib/libusb-1.0.la
/usr/local/lib/libusb-1.0.so
/usr/local/lib/libusb-1.0.so.0
/usr/local/lib/libusb-1.0.so.0.0.0
/usr/local/lib/pkgconfig/libusb-1.0.pc
/usr/share/doc/libusb-1.0-0
/usr/share/doc/libusb-1.0-0-dev
/usr/share/doc/libusb-1.0-0/README
/usr/share/doc/libusb-1.0-0/changelog.Debian.gz
/usr/share/doc/libusb-1.0-0/copyright
/usr/share/doc/libusb-1.0-0-dev/PORTING
/usr/share/doc/libusb-1.0-0-dev/README
/usr/share/doc/libusb-1.0-0-dev/changelog.Debian.gz
/usr/share/doc/libusb-1.0-0-dev/copyright
/usr/share/doc/libusb-1.0-0-dev/html
/usr/share/doc/libusb-1.0-0-dev/html/annotated.html
/usr/share/doc/libusb-1.0-0-dev/html/bc_s.png
/usr/share/doc/libusb-1.0-0-dev/html/caveats.html
/usr/share/doc/libusb-1.0-0-dev/html/classes.html
/usr/share/doc/libusb-1.0-0-dev/html/closed.png
/usr/share/doc/libusb-1.0-0-dev/html/contexts.html
/usr/share/doc/libusb-1.0-0-dev/html/doxygen.css
/usr/share/doc/libusb-1.0-0-dev/html/doxygen.png
/usr/share/doc/libusb-1.0-0-dev/html/dynsections.js
/usr/share/doc/libusb-1.0-0-dev/html/files.html
/usr/share/doc/libusb-1.0-0-dev/html/functions.html
/usr/share/doc/libusb-1.0-0-dev/html/functions_vars.html
/usr/share/doc/libusb-1.0-0-dev/html/group__asyncio.html
/usr/share/doc/libusb-1.0-0-dev/html/group__desc.html
/usr/share/doc/libusb-1.0-0-dev/html/group__dev.html
/usr/share/doc/libusb-1.0-0-dev/html/group__lib.html
/usr/share/doc/libusb-1.0-0-dev/html/group__misc.html
/usr/share/doc/libusb-1.0-0-dev/html/group__poll.html
/usr/share/doc/libusb-1.0-0-dev/html/group__syncio.html
/usr/share/doc/libusb-1.0-0-dev/html/index.html
/usr/share/doc/libusb-1.0-0-dev/html/io.html
/usr/share/doc/libusb-1.0-0-dev/html/libusb_8h_source.html
/usr/share/doc/libusb-1.0-0-dev/html/modules.html
/usr/share/doc/libusb-1.0-0-dev/html/mtasync.html
/usr/share/doc/libusb-1.0-0-dev/html/nav_f.png
/usr/share/doc/libusb-1.0-0-dev/html/nav_h.png
/usr/share/doc/libusb-1.0-0-dev/html/open.png
/usr/share/doc/libusb-1.0-0-dev/html/packetoverflow.html
/usr/share/doc/libusb-1.0-0-dev/html/pages.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__config__descriptor.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__control__setup.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__device__descriptor.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__endpoint__descriptor.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__interface.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__interface__descriptor.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__iso__packet__descriptor.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__pollfd.html
/usr/share/doc/libusb-1.0-0-dev/html/structlibusb__transfer.html
/usr/share/doc/libusb-1.0-0-dev/html/tab_a.png
/usr/share/doc/libusb-1.0-0-dev/html/tab_b.png
/usr/share/doc/libusb-1.0-0-dev/html/tab_h.png
/usr/share/doc/libusb-1.0-0-dev/html/tab_s.png
/usr/share/doc/libusb-1.0-0-dev/html/tabs.css
/usr/share/doc/libusb-1.0-0-dev/html/version_8h_source.html
/usr/share/doc-base/libusb-1.0-0-dev
/var/cache/apt/archives/libusb-1.0-0-dev_2%3a1.0.9~rc3-2ubuntu1_amd64.deb
/var/cache/apt/archives/libusb-1.0-0_2%3a1.0.9~rc3-2ubuntu1_amd64.deb
/var/lib/doc-base/documents/libusb-1.0-0-dev
/var/lib/doc-base/omf/libusb-1.0-0-dev
/var/lib/doc-base/omf/libusb-1.0-0-dev/libusb-1.0-0-dev-C.omf
/var/lib/dpkg/info/libusb-1.0-0-dev.list
/var/lib/dpkg/info/libusb-1.0-0-dev.md5sums
/var/lib/dpkg/info/libusb-1.0-0:amd64.list
/var/lib/dpkg/info/libusb-1.0-0:amd64.md5sums
/var/lib/dpkg/info/libusb-1.0-0:amd64.postinst
/var/lib/dpkg/info/libusb-1.0-0:amd64.postrm
/var/lib/dpkg/info/libusb-1.0-0:amd64.shlibs
```

---

### Post by DAFlippers on 2012-04-30
Resolved.

It appears ia32-libs no longer works.

I added 32 bit version of libusb-1.0 with:
sudo apt-get install libusb-1.0-0-dev:i386

and that also removed gcc

X11 32 bit lib added with:

sudo apt-get install libx11-dev:i386

gcc reinstalled with

apt-get install gcc

32 bit compile gcc LMSS.c -m32 -Wall -W -L//usr/lib/i386-linux-gnu -lusb-1.0 -lX11 -o LMSS32
or even gcc LMSS.c -m32 -Wall -W -lusb-1.0 -lX11 -o LMSS32

64 bit compile gcc LMSS.c -m64 -Wall -W -lusb-1.0 -lX11 -o LMSS64


David

---

### Post by zancoste on 2012-09-12
David, 

I just wanted to post this to say thanks! A lot of people don't update their threads once they find a solution. You, my good sir, did so. Thanks a lot, it helped.

---

### Post by Ubunterrific on 2012-09-12
> **DAFlippers said:**
> Resolved.

It appears ia32-libs no longer works.

I added 32 bit version of libusb-1.0 with:
sudo apt-get install libusb-1.0-0-dev:i386

and that also removed gcc

X11 32 bit lib added with:

sudo apt-get install libx11-dev:i386

gcc reinstalled with

apt-get install gcc

32 bit compile gcc LMSS.c -m32 -Wall -W -L//usr/lib/i386-linux-gnu -lusb-1.0 -lX11 -o LMSS32
or even gcc LMSS.c -m32 -Wall -W -lusb-1.0 -lX11 -o LMSS32

64 bit compile gcc LMSS.c -m64 -Wall -W -lusb-1.0 -lX11 -o LMSS64


David


Could you mark the thread as Solved please? :D

---

