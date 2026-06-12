---
title: "[ubuntu] fglrx doesn't work with switchable graphics"
date: 2011-01-05
forum: General Help
---

### Post by papaapa on 2011-01-05
flgrx won't work w/switchable graphics using non-AMD chipset
i use core i5 with ati mobility radeon 5470 (so it doesn't have amd chipset)

this is the X output when graphics mode in BIOS is set to switchable
> 
[    22.909] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    22.909] X Protocol Version 11, Revision 0
[    22.909] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    22.909] Current Operating System: Linux xmonki-laptop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
[    22.909] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=ec81127a-4c19-4930-aff6-f2704d368f34 ro quiet splash
[    22.909] Build Date: 16 September 2010  05:39:22PM
[    22.909] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.909] Current version of pixman: 0.18.4
[    22.909]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    22.909] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.909] (==) Log file: "/var/log/Xorg.5.log", Time: Fri Dec 31 21:21:48 2010
[    22.909] (==) Using config file: "/etc/X11/xorg.conf"
[    22.909] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.910] (==) ServerLayout "X.org Configured"
[    22.910] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    22.910] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    22.910] (**) |   |-->Device "aticonfig-Device[0]-0"
[    22.910] (**) |-->Input Device "Mouse0"
[    22.910] (**) |-->Input Device "Keyboard0"
[    22.910] (==) Automatically adding devices
[    22.910] (==) Automatically enabling devices
[    22.910] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.910]     Entry deleted from font path.
[    22.910] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.910]     Entry deleted from font path.
[    22.910] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    22.910] (**) ModulePath set to "/usr/lib/xorg/modules"
[    22.910] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    22.910] (WW) Disabling Mouse0
[    22.910] (WW) Disabling Keyboard0
[    22.910] (II) Loader magic: 0x81f8e00
[    22.911] (II) Module ABI versions:
[    22.911]     X.Org ANSI C Emulation: 0.4
[    22.911]     X.Org Video Driver: 8.0
[    22.911]     X.Org XInput driver : 11.0
[    22.911]     X.Org Server Extension : 4.0
[    22.911] (--) PCI:*(0:0:2:0) 8086:0046:1025:0357 rev 24, Mem @ 0x98000000/4194304, 0x80000000/268435456, I/O @ 0x00004050/8
[    22.912] (--) PCI: (0:1:0:0) 1002:68e0:1025:0357 rev 0, Mem @ 0x90000000/134217728, 0x9c400000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    22.912] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    22.912] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    22.912] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    22.912] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    22.912] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    22.912] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    22.912] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    22.912] (II) LoadModule: "dri"
[    22.912] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.912] (II) Module dri: vendor="X.Org Foundation"
[    22.912]     compiled for 1.9.0, module version = 1.0.0
[    22.912]     ABI class: X.Org Server Extension, version 4.0
[    22.912] (II) Loading extension XFree86-DRI
[    22.912] (II) LoadModule: "dbe"
[    22.912] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.912] (II) Module dbe: vendor="X.Org Foundation"
[    22.912]     compiled for 1.9.0, module version = 1.0.0
[    22.912]     Module class: X.Org Server Extension
[    22.912]     ABI class: X.Org Server Extension, version 4.0
[    22.912] (II) Loading extension DOUBLE-BUFFER
[    22.912] (II) LoadModule: "extmod"
[    22.912] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.912] (II) Module extmod: vendor="X.Org Foundation"
[    22.912]     compiled for 1.9.0, module version = 1.0.0
[    22.912]     Module class: X.Org Server Extension
[    22.912]     ABI class: X.Org Server Extension, version 4.0
[    22.912] (II) Loading extension MIT-SCREEN-SAVER
[    22.912] (II) Loading extension XFree86-VidModeExtension
[    22.912] (II) Loading extension XFree86-DGA
[    22.912] (II) Loading extension DPMS
[    22.913] (II) Loading extension XVideo
[    22.913] (II) Loading extension XVideo-MotionCompensation
[    22.913] (II) Loading extension X-Resource
[    22.913] (II) LoadModule: "dri2"
[    22.913] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.913] (II) Module dri2: vendor="X.Org Foundation"
[    22.913]     compiled for 1.9.0, module version = 1.2.0
[    22.913]     ABI class: X.Org Server Extension, version 4.0
[    22.913] (II) Loading extension DRI2
[    22.913] (II) LoadModule: "glx"
[    22.913] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.913] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    22.913]     compiled for 7.6.0, module version = 1.0.0
[    22.913] (II) Loading extension GLX
[    22.913] (II) LoadModule: "record"
[    22.913] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.913] (II) Module record: vendor="X.Org Foundation"
[    22.913]     compiled for 1.9.0, module version = 1.13.0
[    22.913]     Module class: X.Org Server Extension
[    22.913]     ABI class: X.Org Server Extension, version 4.0
[    22.913] (II) Loading extension RECORD
[    22.913] (II) LoadModule: "fglrx"
[    22.914] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    22.929] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    22.929]     compiled for 1.4.99.906, module version = 8.80.5
[    22.929]     Module class: X.Org Video Driver
[    22.929] (II) Loading sub module "fglrxdrm"
[    22.929] (II) LoadModule: "fglrxdrm"
[    22.929] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    22.929] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    22.929]     compiled for 1.4.99.906, module version = 8.80.5
[    22.929] (II) ATI Proprietary Linux Driver Version Identifier:8.80.5
[    22.929] (II) ATI Proprietary Linux Driver Release Identifier: 8.801                                
[    22.929] (II) ATI Proprietary Linux Driver Build Date: Nov 25 2010 21:35:47
[    22.930] (--) using VT number 2

[    22.933] (WW) Falling back to old probe method for fglrx
[    22.938] (II) Loading PCS database from /etc/ati/amdpcsdb
[    22.939] (--) Chipset Supported AMD Graphics Processor (0x68E0) found
[    22.939] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    22.940] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    22.940] (II) AMD Video driver is signed
[    22.940] (II) fglrx(0): pEnt->device->identifier=0x8d10200
[    22.940] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    22.940] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    22.940] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    22.940] (==) fglrx(0): Default visual is TrueColor
[    22.940] (**) fglrx(0): Option "DPMS" "true"
[    22.940] (==) fglrx(0): RGB weight 888
[    22.940] (II) fglrx(0): Using 8 bits per RGB 
[    22.940] (==) fglrx(0): Buffer Tiling is ON
[    22.940] (II) Loading sub module "fglrxdrm"
[    22.940] (II) LoadModule: "fglrxdrm"
[    22.941] (II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    22.942] ukiDynamicMajor: found major device number 250
[    22.942] ukiDynamicMajor: found major device number 250
[    22.942] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    22.942] ukiOpenDevice: node name is /dev/ati/card0
[    22.942] ukiOpenDevice: open result is 10, (OK)
[    22.942] ukiOpenByBusid: ukiOpenMinor returns 10
[    22.942] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    22.942] (==) fglrx(0): NoAccel = NO
[    22.942] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    22.942] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 5400 Series " (Chipset = 0x68e0)
[    22.942] (--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x0357)
[    22.943] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    22.943] (--) fglrx(0): Linear framebuffer (phys) at 0x90000000
[    22.943] (--) fglrx(0): MMIO registers at 0x9c400000
[    22.943] (--) fglrx(0): I/O port at 0x00003000
[    22.943] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    22.944] (II) fglrx(0): AC Adapter is used
[    22.946] (II) fglrx(0): Detected: Switchable-graphics system with a non-AMD chipset
[    22.946] (EE) fglrx(0): Please disable switchable-graphics feature and configure the discrete card as the default adapter
[    22.946] (EE) fglrx(0): GetBIOSParameter failed
[    22.946] (EE) fglrx(0): PreInitAdapter failed
[    22.946] (EE) fglrx(0): PreInit failed
[    22.946] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === end
[    22.948] (II) UnloadModule: "fglrx"
[    22.948] (II) UnloadModule: "fglrxdrm"
[    22.948] (II) UnloadModule: "fglrxdrm"
[    22.948] (EE) Screen(s) found, but none have a usable configuration.
[    22.948] 
Fatal server error:
[    22.948] no screens found
[    22.948] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    22.948] Please also check the log file at "/var/log/Xorg.5.log" for additional information.
[    22.948] 
[    22.955]  ddxSigGiveUp: Closing log

any workarounds/solution?
#sorry for my bad english#

---

### Post by Mark Phelps on 2011-01-06
I've read about this before and the error message 

> (EE) fglrx(0): Please disable switchable-graphics feature and configure the discrete card as the default adapter

indicates that you have to disable that feature.

I don't believe that there is a workaround for this -- but I could be wrong.

---

### Post by SaddamRU on 2011-02-27
I have same problem.
And I need to switch between graphics adapters.
Error happends every time when I installing proprietary driver.

---

