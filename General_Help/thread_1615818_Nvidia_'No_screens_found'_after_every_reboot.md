---
title: "Nvidia 'No screens found' after every reboot"
date: 2010-11-07
forum: General Help
---

### Post by michaelm3 on 2010-11-07
Some background to summarise, I have installed 10.10 clean over the top of 10.04. I did not have X/display problems on 10.04. 

After installing the Nvidia display driver for my device (Asus 8800GT - display driver: NVIDIA-Linux-x86_64-260.19.12.run) in order to get dual-headed display working under TwinView (as I had previously have used on 10.04 problem-free) I cannot reboot/shutdown my machine without a Fatal Error No Screens Found message appearing at boot time.

I can hibernate, but this is less than ideal, especially after installing updates which require a restart. Every time this does happen I can re-run the driver installation and all is well again.

Below are two copies of my Xorg log. The first is the erroneous log, the second the successful log. Below that is my xorg config file generated via nvidia-xconfig. 

ERRONEOUS XORG LOG FILE 
---------------------------------------------------------------------

[    29.712] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    29.712] X Protocol Version 11, Revision 0
[    29.712] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    29.713] Current Operating System: Linux mdesk 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
[    29.713] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic root=UUID=9169187b-526d-4302-b70c-2d5dc69f98ce ro quiet splash nomodeset
[    29.713] Build Date: 16 September 2010  06:18:41PM
[    29.713] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    29.713] Current version of pixman: 0.18.4
[    29.713]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    29.714] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.715] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  6 15:20:02 2010
[    29.715] (==) Using config file: "/etc/X11/xorg.conf"
[    29.715] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.715] (==) ServerLayout "Layout0"
[    29.715] (**) |-->Screen "Screen0" (0)
[    29.715] (**) |   |-->Monitor "Monitor0"
[    29.716] (**) |   |-->Device "Device0"
[    29.716] (**) |-->Input Device "Keyboard0"
[    29.716] (**) |-->Input Device "Mouse0"
[    29.716] (**) Option "Xinerama" "0"
[    29.716] (==) Automatically adding devices
[    29.716] (==) Automatically enabling devices
[    29.716] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.716]     Entry deleted from font path.
[    29.716] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    29.716] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.716] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    29.716] (WW) Disabling Keyboard0
[    29.716] (WW) Disabling Mouse0
[    29.716] (II) Loader magic: 0x7d0200
[    29.716] (II) Module ABI versions:
[    29.716]     X.Org ANSI C Emulation: 0.4
[    29.716]     X.Org Video Driver: 8.0
[    29.716]     X.Org XInput driver : 11.0
[    29.716]     X.Org Server Extension : 4.0
[    29.717] (--) PCI:*(0:5:0:0) 10de:0611:1043:8260 rev 162, Mem @ 0xfc000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
[    29.717] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.717] (II) "extmod" will be loaded by default.
[    29.717] (II) "dbe" will be loaded by default.
[    29.717] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    29.717] (II) "record" will be loaded by default.
[    29.717] (II) "dri" will be loaded by default.
[    29.717] (II) "dri2" will be loaded by default.
[    29.717] (II) LoadModule: "glx"
[    29.717] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.732] (II) Module glx: vendor="NVIDIA Corporation"
[    29.732]     compiled for 4.0.2, module version = 1.0.0
[    29.732]     Module class: X.Org Server Extension
[    29.732] (II) NVIDIA GLX Module  260.19.12  Fri Oct  8 11:41:55 PDT 2010
[    29.732] (II) Loading extension GLX
[    29.732] (II) LoadModule: "extmod"
[    29.732] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.732] (II) Module extmod: vendor="X.Org Foundation"
[    29.732]     compiled for 1.9.0, module version = 1.0.0
[    29.732]     Module class: X.Org Server Extension
[    29.732]     ABI class: X.Org Server Extension, version 4.0
[    29.732] (II) Loading extension MIT-SCREEN-SAVER
[    29.732] (II) Loading extension XFree86-VidModeExtension
[    29.732] (II) Loading extension XFree86-DGA
[    29.732] (II) Loading extension DPMS
[    29.732] (II) Loading extension XVideo
[    29.732] (II) Loading extension XVideo-MotionCompensation
[    29.732] (II) Loading extension X-Resource
[    29.732] (II) LoadModule: "dbe"
[    29.732] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.733] (II) Module dbe: vendor="X.Org Foundation"
[    29.733]     compiled for 1.9.0, module version = 1.0.0
[    29.733]     Module class: X.Org Server Extension
[    29.733]     ABI class: X.Org Server Extension, version 4.0
[    29.733] (II) Loading extension DOUBLE-BUFFER
[    29.733] (II) LoadModule: "record"
[    29.733] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.733] (II) Module record: vendor="X.Org Foundation"
[    29.733]     compiled for 1.9.0, module version = 1.13.0
[    29.733]     Module class: X.Org Server Extension
[    29.733]     ABI class: X.Org Server Extension, version 4.0
[    29.733] (II) Loading extension RECORD
[    29.733] (II) LoadModule: "dri"
[    29.733] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.733] (II) Module dri: vendor="X.Org Foundation"
[    29.733]     compiled for 1.9.0, module version = 1.0.0
[    29.733]     ABI class: X.Org Server Extension, version 4.0
[    29.733] (II) Loading extension XFree86-DRI
[    29.733] (II) LoadModule: "dri2"
[    29.733] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.734] (II) Module dri2: vendor="X.Org Foundation"
[    29.734]     compiled for 1.9.0, module version = 1.2.0
[    29.734]     ABI class: X.Org Server Extension, version 4.0
[    29.734] (II) Loading extension DRI2
[    29.734] (II) LoadModule: "nvidia"
[    29.734] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    29.734] (II) Module nvidia: vendor="NVIDIA Corporation"
[    29.734]     compiled for 4.0.2, module version = 1.0.0
[    29.734]     Module class: X.Org Video Driver
[    29.735] (II) NVIDIA dlloader X Driver  260.19.12  Fri Oct  8 11:19:20 PDT 2010
[    29.735] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    29.735] (--) using VT number 8

[    29.746] (II) Loading sub module "fb"
[    29.746] (II) LoadModule: "fb"
[    29.747] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.747] (II) Module fb: vendor="X.Org Foundation"
[    29.747]     compiled for 1.9.0, module version = 1.0.0
[    29.747]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.747] (II) Loading sub module "wfb"
[    29.747] (II) LoadModule: "wfb"
[    29.747] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    29.747] (II) Module wfb: vendor="X.Org Foundation"
[    29.747]     compiled for 1.9.0, module version = 1.0.0
[    29.747]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.747] (II) Loading sub module "ramdac"
[    29.747] (II) LoadModule: "ramdac"
[    29.747] (II) Module "ramdac" already built-in
[    29.747] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    29.747] (==) NVIDIA(0): RGB weight 888
[    29.747] (==) NVIDIA(0): Default visual is TrueColor
[    29.747] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    29.747] (**) NVIDIA(0): Option "NoLogo" "True"
[    29.747] (**) NVIDIA(0): Option "TwinView" "1"
[    29.747] (**) NVIDIA(0): Option "MetaModes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
[    29.747] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    29.748] (**) NVIDIA(0): Enabling RENDER acceleration
[    29.748] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    29.748] (II) NVIDIA(0):     enabled.
[    29.748] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    29.748] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    29.748] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    29.748] (EE) NVIDIA(0):  *** Aborting ***
[    29.748] (II) UnloadModule: "nvidia"
[    29.748] (II) UnloadModule: "wfb"
[    29.748] (II) UnloadModule: "fb"
[    29.748] (EE) Screen(s) found, but none have a usable configuration.
[    29.748] 
Fatal server error:
[    29.748] no screens found
[    29.748] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    29.748] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    29.748] 
[    29.760]  ddxSigGiveUp: Closing log

-------------------------------------------------------------------- 
SUCCESSFUL LOG FILE
--------------------------------------------------------------------

[   256.209] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   256.209] X Protocol Version 11, Revision 0
[   256.209] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[   256.210] Current Operating System: Linux mdesk 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64
[   256.210] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.35-22-generic root=UUID=9169187b-526d-4302-b70c-2d5dc69f98ce ro quiet splash nomodeset
[   256.210] Build Date: 16 September 2010  06:18:41PM
[   256.210] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   256.210] Current version of pixman: 0.18.4
[   256.211]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   256.211] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   256.212] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  6 15:23:49 2010
[   256.213] (==) Using config file: "/etc/X11/xorg.conf"
[   256.213] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   256.214] (==) ServerLayout "Layout0"
[   256.214] (**) |-->Screen "Screen0" (0)
[   256.214] (**) |   |-->Monitor "Monitor0"
[   256.214] (**) |   |-->Device "Device0"
[   256.214] (**) |-->Input Device "Keyboard0"
[   256.214] (**) |-->Input Device "Mouse0"
[   256.214] (**) Option "Xinerama" "0"
[   256.214] (==) Automatically adding devices
[   256.215] (==) Automatically enabling devices
[   256.215] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   256.215]     Entry deleted from font path.
[   256.215] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   256.215] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   256.215] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   256.215] (WW) Disabling Keyboard0
[   256.215] (WW) Disabling Mouse0
[   256.215] (II) Loader magic: 0x7d0200
[   256.215] (II) Module ABI versions:
[   256.215]     X.Org ANSI C Emulation: 0.4
[   256.215]     X.Org Video Driver: 8.0
[   256.215]     X.Org XInput driver : 11.0
[   256.215]     X.Org Server Extension : 4.0
[   256.216] (--) PCI:*(0:5:0:0) 10de:0611:1043:8260 rev 162, Mem @ 0xfc000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
[   256.217] (II) Open ACPI successful (/var/run/acpid.socket)
[   256.217] (II) "extmod" will be loaded by default.
[   256.217] (II) "dbe" will be loaded by default.
[   256.217] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   256.217] (II) "record" will be loaded by default.
[   256.217] (II) "dri" will be loaded by default.
[   256.217] (II) "dri2" will be loaded by default.
[   256.217] (II) LoadModule: "glx"
[   256.218] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   256.251] (II) Module glx: vendor="NVIDIA Corporation"
[   256.251]     compiled for 4.0.2, module version = 1.0.0
[   256.251]     Module class: X.Org Server Extension
[   256.251] (II) NVIDIA GLX Module  260.19.12  Fri Oct  8 11:41:55 PDT 2010
[   256.251] (II) Loading extension GLX
[   256.251] (II) LoadModule: "extmod"
[   256.251] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   256.252] (II) Module extmod: vendor="X.Org Foundation"
[   256.252]     compiled for 1.9.0, module version = 1.0.0
[   256.252]     Module class: X.Org Server Extension
[   256.252]     ABI class: X.Org Server Extension, version 4.0
[   256.252] (II) Loading extension MIT-SCREEN-SAVER
[   256.252] (II) Loading extension XFree86-VidModeExtension
[   256.252] (II) Loading extension XFree86-DGA
[   256.252] (II) Loading extension DPMS
[   256.252] (II) Loading extension XVideo
[   256.252] (II) Loading extension XVideo-MotionCompensation
[   256.252] (II) Loading extension X-Resource
[   256.252] (II) LoadModule: "dbe"
[   256.252] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   256.253] (II) Module dbe: vendor="X.Org Foundation"
[   256.253]     compiled for 1.9.0, module version = 1.0.0
[   256.253]     Module class: X.Org Server Extension
[   256.253]     ABI class: X.Org Server Extension, version 4.0
[   256.253] (II) Loading extension DOUBLE-BUFFER
[   256.253] (II) LoadModule: "record"
[   256.253] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   256.253] (II) Module record: vendor="X.Org Foundation"
[   256.253]     compiled for 1.9.0, module version = 1.13.0
[   256.253]     Module class: X.Org Server Extension
[   256.253]     ABI class: X.Org Server Extension, version 4.0
[   256.253] (II) Loading extension RECORD
[   256.253] (II) LoadModule: "dri"
[   256.254] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   256.254] (II) Module dri: vendor="X.Org Foundation"
[   256.254]     compiled for 1.9.0, module version = 1.0.0
[   256.254]     ABI class: X.Org Server Extension, version 4.0
[   256.254] (II) Loading extension XFree86-DRI
[   256.254] (II) LoadModule: "dri2"
[   256.255] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   256.255] (II) Module dri2: vendor="X.Org Foundation"
[   256.255]     compiled for 1.9.0, module version = 1.2.0
[   256.255]     ABI class: X.Org Server Extension, version 4.0
[   256.255] (II) Loading extension DRI2
[   256.255] (II) LoadModule: "nvidia"
[   256.256] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   256.257] (II) Module nvidia: vendor="NVIDIA Corporation"
[   256.257]     compiled for 4.0.2, module version = 1.0.0
[   256.257]     Module class: X.Org Video Driver
[   257.742] (II) NVIDIA dlloader X Driver  260.19.12  Fri Oct  8 11:19:20 PDT 2010
[   257.742] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   257.742] (--) using VT number 8

[   257.753] (II) Loading sub module "fb"
[   257.753] (II) LoadModule: "fb"
[   257.754] (II) Loading /usr/lib/xorg/modules/libfb.so
[   257.754] (II) Module fb: vendor="X.Org Foundation"
[   257.754]     compiled for 1.9.0, module version = 1.0.0
[   257.754]     ABI class: X.Org ANSI C Emulation, version 0.4
[   257.754] (II) Loading sub module "wfb"
[   257.754] (II) LoadModule: "wfb"
[   257.754] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   257.754] (II) Module wfb: vendor="X.Org Foundation"
[   257.754]     compiled for 1.9.0, module version = 1.0.0
[   257.754]     ABI class: X.Org ANSI C Emulation, version 0.4
[   257.754] (II) Loading sub module "ramdac"
[   257.754] (II) LoadModule: "ramdac"
[   257.754] (II) Module "ramdac" already built-in
[   257.754] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   257.754] (==) NVIDIA(0): RGB weight 888
[   257.755] (==) NVIDIA(0): Default visual is TrueColor
[   257.755] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   257.755] (**) NVIDIA(0): Option "NoLogo" "True"
[   257.755] (**) NVIDIA(0): Option "TwinView" "1"
[   257.755] (**) NVIDIA(0): Option "MetaModes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
[   257.755] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[   257.755] (**) NVIDIA(0): Enabling RENDER acceleration
[   257.755] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   257.755] (II) NVIDIA(0):     enabled.
[   258.785] (II) NVIDIA(0): NVIDIA GPU GeForce 8800 GT (G92) at PCI:5:0:0 (GPU-0)
[   258.785] (--) NVIDIA(0): Memory: 524288 kBytes
[   258.785] (--) NVIDIA(0): VideoBIOS: 62.92.12.00.00
[   258.785] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   258.785] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   258.785] (--) NVIDIA(0): Connected display device(s) on GeForce 8800 GT at PCI:5:0:0
[   258.785] (--) NVIDIA(0):     NUL (CRT-0)
[   258.785] (--) NVIDIA(0):     NUL (CRT-1)
[   258.785] (--) NVIDIA(0): NUL (CRT-0): 400.0 MHz maximum pixel clock
[   258.785] (--) NVIDIA(0): NUL (CRT-1): 400.0 MHz maximum pixel clock
[   258.787] (**) NVIDIA(0): TwinView enabled
[   258.787] (II) NVIDIA(0): Display Devices found referenced in MetaMode: CRT-0, CRT-1
[   258.809] (II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
[   258.810] (II) NVIDIA(0): Validated modes:
[   258.810] (II) NVIDIA(0):     "CRT-0:1280x1024+0+0,CRT-1:1280x1024+1280+0"
[   258.810] (II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
[   258.826] (--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
[   258.826] (--) NVIDIA(0):     option
[   258.826] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[   258.826] (--) Depth 24 pixmap format is 32 bpp
[   258.826] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[   258.827] (II) NVIDIA(0): Initialized GPU GART.
[   258.832] (II) NVIDIA(0): Setting mode "CRT-0:1280x1024+0+0,CRT-1:1280x1024+1280+0"
[   258.905] (II) Loading extension NV-GLX
[   258.968] (II) NVIDIA(0): Initialized OpenGL Acceleration
[   258.989] (==) NVIDIA(0): Disabling shared memory pixmaps
[   258.989] (II) NVIDIA(0): Initialized X Rendering Acceleration
[   258.989] (==) NVIDIA(0): Backing store disabled
[   258.989] (==) NVIDIA(0): Silken mouse enabled
[   259.018] (**) NVIDIA(0): DPMS enabled
[   259.028] (II) Loading extension NV-CONTROL
[   259.028] (II) Loading extension XINERAMA
[   259.028] (II) Loading sub module "dri2"
[   259.028] (II) LoadModule: "dri2"
[   259.028] (II) Reloading /usr/lib/xorg/modules/extensions/libdri2.so
[   259.029] (II) NVIDIA(0): [DRI2] Setup complete
[   259.029] (==) RandR enabled
[   259.029] (II) Initializing built-in extension Generic Event Extension
[   259.029] (II) Initializing built-in extension SHAPE
[   259.029] (II) Initializing built-in extension MIT-SHM
[   259.029] (II) Initializing built-in extension XInputExtension
[   259.029] (II) Initializing built-in extension XTEST
[   259.029] (II) Initializing built-in extension BIG-REQUESTS
[   259.029] (II) Initializing built-in extension SYNC
[   259.029] (II) Initializing built-in extension XKEYBOARD
[   259.029] (II) Initializing built-in extension XC-MISC
[   259.029] (II) Initializing built-in extension SECURITY
[   259.029] (II) Initializing built-in extension XINERAMA
[   259.029] (II) Initializing built-in extension XFIXES
[   259.029] (II) Initializing built-in extension RENDER
[   259.029] (II) Initializing built-in extension RANDR
[   259.029] (II) Initializing built-in extension COMPOSITE
[   259.029] (II) Initializing built-in extension DAMAGE
[   259.029] (II) Initializing built-in extension GESTURE
[   259.029] (II) Initializing extension GLX
[   259.176] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   259.386] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   259.386] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   259.386] (II) LoadModule: "evdev"
[   259.387] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   259.420] (II) Module evdev: vendor="X.Org Foundation"
[   259.420]     compiled for 1.9.0, module version = 2.3.2
[   259.420]     Module class: X.Org XInput Driver
[   259.420]     ABI class: X.Org XInput driver, version 11.0
[   259.420] (**) Power Button: always reports core events
[   259.420] (**) Power Button: Device: "/dev/input/event1"
[   259.442] (II) Power Button: Found keys
[   259.442] (II) Power Button: Configuring as keyboard
[   259.442] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   259.442] (**) Option "xkb_rules" "evdev"
[   259.442] (**) Option "xkb_model" "evdev"
[   259.442] (**) Option "xkb_layout" "gb"
[   259.447] (II) XKB: generating xkmfile /tmp/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[   259.512] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   259.512] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   259.512] (**) Power Button: always reports core events
[   259.512] (**) Power Button: Device: "/dev/input/event0"
[   259.542] (II) Power Button: Found keys
[   259.542] (II) Power Button: Configuring as keyboard
[   259.542] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   259.542] (**) Option "xkb_rules" "evdev"
[   259.542] (**) Option "xkb_model" "evdev"
[   259.542] (**) Option "xkb_layout" "gb"
[   259.545] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event2)
[   259.545] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[   259.545] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[   259.545] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2"
[   259.570] (II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
[   259.570] (II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[   259.570] (II) Logitech USB-PS/2 Optical Mouse: Found relative axes
[   259.570] (II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[   259.570] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[   259.570] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[   259.570] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   259.570] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[   259.570] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[   259.571] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[   259.571] (II) No input driver/identifier specified (ignoring)
[   259.572] (II) config/udev: Adding input device USB-compliant keyboard (/dev/input/event3)
[   259.572] (**) USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[   259.572] (**) USB-compliant keyboard: always reports core events
[   259.572] (**) USB-compliant keyboard: Device: "/dev/input/event3"
[   259.600] (II) USB-compliant keyboard: Found keys
[   259.600] (II) USB-compliant keyboard: Configuring as keyboard
[   259.600] (II) XINPUT: Adding extended input device "USB-compliant keyboard" (type: KEYBOARD)
[   259.600] (**) Option "xkb_rules" "evdev"
[   259.600] (**) Option "xkb_model" "evdev"
[   259.600] (**) Option "xkb_layout" "gb"
[   259.601] (II) config/udev: Adding input device USB-compliant keyboard (/dev/input/event4)
[   259.601] (**) USB-compliant keyboard: Applying InputClass "evdev keyboard catchall"
[   259.601] (**) USB-compliant keyboard: always reports core events
[   259.601] (**) USB-compliant keyboard: Device: "/dev/input/event4"
[   259.602] (II) USB-compliant keyboard: Found 1 mouse buttons
[   259.602] (II) USB-compliant keyboard: Found scroll wheel(s)
[   259.602] (II) USB-compliant keyboard: Found relative axes
[   259.602] (II) USB-compliant keyboard: Found x and y relative axes
[   259.602] (II) USB-compliant keyboard: Found absolute axes
[   259.602] (II) evdev-grail: failed to open grail, no gesture support
[   259.602] (II) USB-compliant keyboard: Found keys
[   259.602] (II) USB-compliant keyboard: Configuring as mouse
[   259.602] (II) USB-compliant keyboard: Configuring as keyboard
[   259.602] (**) USB-compliant keyboard: YAxisMapping: buttons 4 and 5
[   259.602] (**) USB-compliant keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   259.602] (II) XINPUT: Adding extended input device "USB-compliant keyboard" (type: KEYBOARD)
[   259.602] (**) Option "xkb_rules" "evdev"
[   259.602] (**) Option "xkb_model" "evdev"
[   259.602] (**) Option "xkb_layout" "gb"
[   259.603] (II) USB-compliant keyboard: initialized for relative axes.
[   259.603] (WW) USB-compliant keyboard: ignoring absolute axes.
[   259.604] (II) config/udev: Adding input device USB-compliant keyboard (/dev/input/mouse1)
[   259.604] (II) No input driver/identifier specified (ignoring)


 ------------------------------------------------------------------------
 XORG CONFIG FILE
 ------------------------------------------------------------------------

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.12  (buildmeister@builder101)  Fri Oct  8 11:47:04 PDT 2010

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.12  (buildmeister@builder101)  Fri Oct  8 11:46:43 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NUL"
    HorizSync       31.5 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 640x480 +1280+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

------------------------------------------------------------------------

 Any ideas as to why this may be happening would be appreciated. 

I have use many versions of linux (fedora 9, 10, 11, 12) and ubuntu (8.04, 8.10, 9.04, 9.10, 10.04) with this graphics card with no problems.

I plan to try other driver versions to see if it is a driver issue but just wanted to get this out here too to see what other theories people may have. If I find a successful driver version I will post the number here. 

Thanks in advance, Michael.

---

### Post by dino99 on 2010-11-07
so its a xorg.conf issue. (rename or remove it, then run nvidia-settings)

why not using x-swat ppa or xorg-edgers for less trouble ?

---

### Post by P4man on 2010-11-07
You probably just have to disable kernel mode setting. See my sig, try the nomodeset solution. If that doesnt help, try blacklisting nouveau in  /etc/modprobe.d/blacklist.conf

---

### Post by michaelm3 on 2010-11-08
Thanks for your ideas P4Man, I tried both but sadly neither made any difference.  Thanks also Dino99, sadly I don't know what those things are so I'll have to do some research and get back to you.  I should state that simply re-running nvidia-xconfig doesn't fix the issue, only a full driver reinstall does (even though the xorg.conf is the same as xorg.conf.backup)

---

### Post by P4man on 2010-11-08
can you post the output of

```
cat /var/log/syslog | grep "NVRM"
```

(and please use [code] tage around the output)

---

### Post by michaelm3 on 2010-11-09
```

Nov  8 18:39:43 mdesk kernel: [   11.091286] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
Nov  8 18:39:43 mdesk kernel: [   15.678611] NVRM: API mismatch: the client has the version 260.19.12, but
Nov  8 18:39:43 mdesk kernel: [   15.678613] NVRM: this kernel module has the version 260.19.06.  Please
Nov  8 18:39:43 mdesk kernel: [   15.678614] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  8 18:39:43 mdesk kernel: [   15.678615] NVRM: components have the same version.
Nov  8 18:39:43 mdesk kernel: [   15.764870] NVRM: API mismatch: the client has the version 260.19.12, but
Nov  8 18:39:43 mdesk kernel: [   15.764873] NVRM: this kernel module has the version 260.19.06.  Please
Nov  8 18:39:43 mdesk kernel: [   15.764874] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  8 18:39:43 mdesk kernel: [   15.764875] NVRM: components have the same version.
Nov  8 18:39:43 mdesk kernel: [   15.844411] NVRM: API mismatch: the client has the version 260.19.12, but
Nov  8 18:39:43 mdesk kernel: [   15.844413] NVRM: this kernel module has the version 260.19.06.  Please
Nov  8 18:39:43 mdesk kernel: [   15.844414] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  8 18:39:43 mdesk kernel: [   15.844415] NVRM: components have the same version.
Nov  8 18:39:43 mdesk kernel: [   15.912069] NVRM: API mismatch: the client has the version 260.19.12, but
Nov  8 18:39:43 mdesk kernel: [   15.912071] NVRM: this kernel module has the version 260.19.06.  Please
Nov  8 18:39:43 mdesk kernel: [   15.912072] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  8 18:39:43 mdesk kernel: [   15.912073] NVRM: components have the same version.
Nov  8 18:39:43 mdesk kernel: [   15.979943] NVRM: API mismatch: the client has the version 260.19.12, but
Nov  8 18:39:43 mdesk kernel: [   15.979945] NVRM: this kernel module has the version 260.19.06.  Please
Nov  8 18:39:43 mdesk kernel: [   15.979946] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  8 18:39:43 mdesk kernel: [   15.979947] NVRM: components have the same version.
Nov  8 18:39:43 mdesk kernel: [   16.047301] NVRM: API mismatch: the client has the version 260.19.12, but
Nov  8 18:39:43 mdesk kernel: [   16.047303] NVRM: this kernel module has the version 260.19.06.  Please
Nov  8 18:39:43 mdesk kernel: [   16.047304] NVRM: make sure that this kernel module and all NVIDIA driver
Nov  8 18:39:43 mdesk kernel: [   16.047305] NVRM: components have the same version.
Nov  8 18:42:07 mdesk kernel: [  160.168826] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.12  Fri Oct  8 11:17:08 PDT 2010
Nov  8 18:43:16 mdesk kernel: [  229.182139] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.12  Fri Oct  8 11:17:08 PDT 2010

```

Ok I see the problem there, I've had errors similar to that when writing CUDA software, code was compiled against a different version of the driver which is now trying to run against this version - not sure what the resolution to that is in this context though.

---

### Post by dino99 on 2010-11-09
so the problem is: API mismatch 260.19.06/260.19.12 (thats all the fun when using .run driver)

open synaptic (system admin synaptic)

remove/purge (right click) each nvidia packages installed
goto repo tab (third parties) and add this ppa:

ppa:ubuntu-x-swat/x-updates
([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates))

update then search for "nvidia" and install: nvidia-current & nvidia-settings

reboot and check driver activation (system admin additional driver), then goto: system admin nvidia settings to set the twinview

---

### Post by P4man on 2010-11-09
That log says it all. You should have uninstalled the nvidia drivers from synaptic and  stopped X before installing the ones from nvidia website. Now you have a mismatch.

Have a look here how to solve that:
[http://ubuntuforums.org/showthread.php?t=650161](http://ubuntuforums.org/showthread.php?t=650161)

Its old but afaict, should still apply.

---

### Post by gschoper on 2010-11-09
> **dino99 said:**
> so the problem is: API mismatch 260.19.06/260.19.12 (thats all the fun when using .run driver)

open synaptic (system admin synaptic)

remove/purge (right click) each nvidia packages installed
goto repo tab (third parties) and add this ppa:

ppa:ubuntu-x-swat/x-updates
([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates))

update then search for "nvidia" and install: nvidia-current & nvidia-settings

reboot and check driver activation (system admin additional driver), then goto: system admin nvidia settings to set the twinview

Thanks,

This fixed it for me with one extra step though. I was still getting a kernel module mismatch because I had manually installed drivers from nvidia.com. to remove them I ran:

```

NVIDIA-Linux-x86-256.53.run --uninstall

```

as root. All is working great now.

---

### Post by michaelm3 on 2010-11-10
Thanks very much guys, that worked a treat. I didn't even need to do twin view again, it was all remembered. Excellent knowledge base here, very commendable.

---

