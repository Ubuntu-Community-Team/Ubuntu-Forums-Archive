---
title: "Via Drivers"
date: 2009-10-21
forum: General Help
---

### Post by n2gadgts on 2009-10-21
I've been searching for a way to get my VIA Technologies drivers loaded in Ubuntu 9.04.

When I do a lspci | grep VGA, I get this:
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

So I did some searching and found that I could use the Openchrome drivers or download the VIA drivers from their website here:

[http://www.via.com.tw/en/support/drivers.jsp](http://www.via.com.tw/en/support/drivers.jsp)

I downloaded "via-xserver-86a-50283_src.tgz" and placed it in the /root directory and followed the readme.  When I run the make command from the XServer directory I get errors and the driver is never created.

I also followed the directions from here: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Item 3 "VIA Proprietary  graphics driver" with no luck.  Here's the output from the make:

 make
make  all-recursive
make[1]: Entering directory `/root/via-xserver-86a-50283_src/XServer'
Making all in src
make[2]: Entering directory `/root/via-xserver-86a-50283_src/XServer/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -O2 -I/usr/include/xorg -I/usr/include/pixman-1   -DXFree86LOADER -I/usr/include/drm -I/usr/include/X11/dri   -I/usr/include/X11  -I/usr/include/X11/extensions -I.. -I.  -O2 -MT via_common.lo -MD -MP -MF .deps/via_common.Tpo -c -o via_common.lo via_common.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -DXFree86LOADER -I/usr/include/drm -I/usr/include/X11/dri -I/usr/include/X11 -I/usr/include/X11/extensions -I.. -I. -O2 -MT via_common.lo -MD -MP -MF .deps/via_common.Tpo -c via_common.c  -fPIC -DPIC -o .libs/via_common.o
In file included from via_driver.h:66,
                 from via_common.h:29,
                 from via_common.c:32:
via_bios.h:37:21: error: xf86drm.h: No such file or directory
In file included from via_bios.h:38,
                 from via_driver.h:66,
                 from via_common.h:29,
                 from via_common.c:32:
/usr/include/xorg/sarea.h:84: error: expected specifier-qualifier-list before ‘drmLock’
/usr/include/xorg/sarea.h:93: error: expected specifier-qualifier-list before ‘drmLock’
In file included from via_driver.h:66,
                 from via_common.h:29,
                 from via_common.c:32:
via_bios.h:325: error: expected specifier-qualifier-list before ‘drmLock’
In file included from via_driver.h:73,
                 from via_common.h:29,
                 from via_common.c:32:
/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from via_driver.h:73,
                 from via_common.h:29,
                 from via_common.c:32:
/usr/include/GL/glxint.h:95: error: expected specifier-qualifier-list before ‘GLboolean’
In file included from via_driver.h:74,
                 from via_common.h:29,
                 from via_common.c:32:
via_dri.h:416: error: expected specifier-qualifier-list before ‘drmSize’
In file included from via_common.h:29,
                 from via_common.c:32:
via_driver.h:734: error: expected specifier-qualifier-list before ‘drmAddress’
via_common.c: In function ‘viaGetVgaIoAddress’:
via_common.c:53: warning: cast from pointer to integer of different size
via_common.c: In function ‘viaReadVgaIo’:
via_common.c:109: warning: cast to pointer from integer of different size
via_common.c:110: warning: cast to pointer from integer of different size
via_common.c: In function ‘viaWriteVgaIo’:
via_common.c:131: warning: cast to pointer from integer of different size
via_common.c:132: warning: cast to pointer from integer of different size
via_common.c: In function ‘viaWriteVgaIoBits’:
via_common.c:154: warning: cast to pointer from integer of different size
via_common.c:155: warning: cast to pointer from integer of different size
via_common.c:156: warning: cast to pointer from integer of different size
make[2]: *** [via_common.lo] Error 1
make[2]: Leaving directory `/root/via-xserver-86a-50283_src/XServer/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/via-xserver-86a-50283_src/XServer'
make: *** [all] Error 2


I don't know where to go from here.  Any help would be greatly appreciated!

---

### Post by Woody1987 on 2009-10-21
in a terminal run 
```
sudo apt-get install xserver-xorg-video-openchrome
```
That will install the driver for you. although im pretty sure it is installed automatically when you install ubuntu.

---

### Post by n2gadgts on 2009-10-21
How does the openchrome differ from the VIA driver?  I'm pretty sure I have the openchrome driver installed now and am trying to update it with the proprietary drivers from VIA.

---

### Post by Woody1987 on 2009-10-21
run sudo apt-get install xserver-xorg-video-via in that case, im not sure on the difference as i dont use via graphics.

---

### Post by n2gadgts on 2009-10-21
I did the VIA install as you stated above and then hit CTRL-ALT-F1 and tried to do X: 1 and got:

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux thezone 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Wed Oct 21 22:02:31 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(**) Option "RandR" "false"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/TTF/" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/OTF" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/fonts/X11/misc/,
        /usr/share/fonts/X11/Type1/,
        /usr/share/fonts/X11/100dpi/,
        /usr/share/fonts/X11/75dpi/,
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0xb40
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0@1:0:0) VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] rev 1, Mem @ 0xf0000000/67108864, 0xf8000000/16777216, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]......

(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "xtrap"
(WW) Warning, couldn't open module xtrap
(II) UnloadModule: "xtrap"
(EE) Failed to load module "xtrap" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "via"
(WW) Warning, couldn't open module via
(II) UnloadModule: "via"
(EE) Failed to load module "via" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log


Where do I go from here?  When I look in the xorg.conf file it is still looking for a VIA driver:

Section "Device"
        #BusID "PCI:01:00:0"
        Identifier  "Card0"
        Driver      "via"
        VendorName  "VIA Technologies, Inc."

but when I look at the /usr/lib/xorg/modules/drivers directory there is no via_drv.so driver.

---

### Post by P4man on 2009-10-21
The proprietary VIA driver doesnt support your chipset (it only supports chrome9, not your unichrome) Youre basially stuck with using the openchrome which should be installed by default.

---

