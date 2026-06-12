---
title: "Can someone take a look at this, tell me whats going on"
date: 2011-03-16
forum: General Help
---

### Post by Jon Anderson on 2011-03-16
What video driver is it using and notice 21.998= invalid argument, is that a problem that needs to be resolved ------------------------------------------------------------------------------------------------------------
[    21.930] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    21.930] X Protocol Version 11, Revision 0
[    21.930] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    21.930] Current Operating System: Linux ubuntujon 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:40:58 UTC 2011 i686
[    21.930] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=7b5363fb-8ece-44ed-a48b-0be53af47b52 ro quiet splash
[    21.930] Build Date: 09 January 2011  12:14:58PM
[    21.930] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.930] Current version of pixman: 0.18.4
[    21.930]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    21.930] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.930] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 14 19:37:56 2011
[    21.949] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.949] (==) No Layout section.  Using the first Screen section.
[    21.949] (==) No screen section available. Using defaults.
[    21.949] (**) |-->Screen "Default Screen Section" (0)
[    21.949] (**) |   |-->Monitor "<default monitor>"
[    21.950] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.950] (==) Automatically adding devices
[    21.950] (==) Automatically enabling devices
[    21.950] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.950]     Entry deleted from font path.
[    21.950] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.950] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.950] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.950] (II) Loader magic: 0x81f9b00
[    21.950] (II) Module ABI versions:
[    21.950]     X.Org ANSI C Emulation: 0.4
[    21.950]     X.Org Video Driver: 8.0
[    21.950]     X.Org XInput driver : 11.0
[    21.950]     X.Org Server Extension : 4.0
[    21.951] (--) PCI:*(0:1:0:0) 10de:00f1:0000:0000 rev 162, Mem @ 0xe8000000/16777216, 0xd0000000/268435456, 0xe9000000/16777216, BIOS @ 0x????????/131072
[    21.951] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    21.951] (II) LoadModule: "extmod"
[    21.960] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.960] (II) Module extmod: vendor="X.Org Foundation"
[    21.960]     compiled for 1.9.0, module version = 1.0.0
[    21.960]     Module class: X.Org Server Extension
[    21.960]     ABI class: X.Org Server Extension, version 4.0
[    21.960] (II) Loading extension MIT-SCREEN-SAVER
[    21.960] (II) Loading extension XFree86-VidModeExtension
[    21.960] (II) Loading extension XFree86-DGA
[    21.960] (II) Loading extension DPMS
[    21.960] (II) Loading extension XVideo
[    21.960] (II) Loading extension XVideo-MotionCompensation
[    21.960] (II) Loading extension X-Resource
[    21.960] (II) LoadModule: "dbe"
[    21.960] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.961] (II) Module dbe: vendor="X.Org Foundation"
[    21.961]     compiled for 1.9.0, module version = 1.0.0
[    21.961]     Module class: X.Org Server Extension
[    21.961]     ABI class: X.Org Server Extension, version 4.0
[    21.961] (II) Loading extension DOUBLE-BUFFER
[    21.961] (II) LoadModule: "glx"
[    21.961] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.961] (II) Module glx: vendor="X.Org Foundation"
[    21.961]     compiled for 1.9.0, module version = 1.0.0
[    21.961]     ABI class: X.Org Server Extension, version 4.0
[    21.961] (==) AIGLX enabled
[    21.961] (II) Loading extension GLX
[    21.961] (II) LoadModule: "record"
[    21.961] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.961] (II) Module record: vendor="X.Org Foundation"
[    21.961]     compiled for 1.9.0, module version = 1.13.0
[    21.961]     Module class: X.Org Server Extension
[    21.961]     ABI class: X.Org Server Extension, version 4.0
[    21.961] (II) Loading extension RECORD
[    21.961] (II) LoadModule: "dri"
[    21.962] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.962] (II) Module dri: vendor="X.Org Foundation"
[    21.962]     compiled for 1.9.0, module version = 1.0.0
[    21.962]     ABI class: X.Org Server Extension, version 4.0
[    21.962] (II) Loading extension XFree86-DRI
[    21.962] (II) LoadModule: "dri2"
[    21.962] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.962] (II) Module dri2: vendor="X.Org Foundation"
[    21.962]     compiled for 1.9.0, module version = 1.2.0
[    21.962]     ABI class: X.Org Server Extension, version 4.0
[    21.962] (II) Loading extension DRI2
[    21.962] (==) Matched nouveau as autoconfigured driver 0
[    21.962] (==) Matched nv as autoconfigured driver 1
[    21.962] (==) Matched vesa as autoconfigured driver 2
[    21.962] (==) Matched fbdev as autoconfigured driver 3
[    21.962] (==) Assigned the driver to the xf86ConfigLayout
[    21.962] (II) LoadModule: "nouveau"
[    21.970] (WW) Warning, couldn't open module nouveau
[    21.970] (II) UnloadModule: "nouveau"
[    21.970] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    21.970] (II) LoadModule: "nv"
[    21.970] (II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
[    21.970] (II) Module nv: vendor="X.Org Foundation"
[    21.970]     compiled for 1.8.99.905, module version = 2.1.17
[    21.970]     Module class: X.Org Video Driver
[    21.970]     ABI class: X.Org Video Driver, version 8.0
[    21.970] (II) LoadModule: "vesa"
[    21.971] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.971] (II) Module vesa: vendor="X.Org Foundation"
[    21.971]     compiled for 1.8.99.905, module version = 2.3.0
[    21.971]     Module class: X.Org Video Driver
[    21.971]     ABI class: X.Org Video Driver, version 8.0
[    21.971] (II) LoadModule: "fbdev"
[    21.971] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.971] (II) Module fbdev: vendor="X.Org Foundation"
[    21.971]     compiled for 1.8.99.905, module version = 0.4.2
[    21.971]     ABI class: X.Org Video Driver, version 8.0
[    21.971] (II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
    Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
    Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
    GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
    GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
    Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
    GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
    GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
    GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
    GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
    GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
    GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
    Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
    GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
    GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
    GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
    Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
    GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
    Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
    GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
    GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
    GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
    GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
    GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
    GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
    Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
    GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
    GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
    GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
    GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
    GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
    Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
    GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
    GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
    GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
    GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
    Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
    GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
    GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
    GeForce Go 6600, GeForce Go 6600 GT, Quadro NVS 440, Quadro FX 550,
    Quadro FX 550, Quadro FX 540, GeForce 6200, GeForce 6500,
    GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
    GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
    GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
    GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT,
    GeForce 6200, GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
    GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
    GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7350 LE,
    GeForce 7300 LE, GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300,
    GeForce Go 7400, GeForce Go 7400 GS, Quadro NVS 110M,
    Quadro NVS 120M, Quadro FX 350M, GeForce 7500 LE, Quadro FX 350,
    GeForce 7300 GS, GeForce 7650 GS, GeForce 7600 GT, GeForce 7600 GS,
    GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT, GeForce Go 7700,
    GeForce Go 7600, GeForce Go 7600 GT, Quadro NVS 300M,
    GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560, GeForce 7900 GTX,
    GeForce 7900 GT, GeForce 7900 GS, GeForce 7950 GX2, GeForce 7950 GX2,
    GeForce 7950 GT, GeForce Go 7950 GTX, GeForce Go 7900 GS,
    GeForce Go 7900 GTX, Quadro FX 2500M, Quadro FX 1500M,
    Quadro FX 5500, Quadro FX 3500, Quadro FX 1500, Quadro FX 4500 X2,
    GeForce 6150, GeForce 6150 LE, GeForce 6100, GeForce Go 6150,
    Quadro NVS 210S / NVIDIA GeForce 6150LE, GeForce Go 6100,
    GeForce 6150SE, GeForce 6100 nForce 405, GeForce 6100 nForce 400,
    GeForce 6100 nForce 420, GeForce 7150M / nForce 630M,
    GeForce 7000M / nForce 610M, GeForce 7050 PV / nForce 630a,
    GeForce 7050 PV / nForce 630a, GeForce 7025 / nForce 630a,
    GeForce 8800 GTX, GeForce 8800 GTS, GeForce 8800 Ultra,
    Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS, GeForce 8600 GT,
    GeForce 8600 GT, GeForce 8600 GS, GeForce 8400 GS, GeForce 9500M GS,
    GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
    Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
    Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
    GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
    GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
    Quadro NVS 135M, GeForce 9400 GT, Quadro FX 360M, GeForce 9300M G,
    Quadro NVS 290, GeForce GTX 295, GeForce GTX 280, GeForce GTX 260,
    GeForce GTX 285, GeForce GTX 275, GeForce GTX 295, Quadro CX,
    Quadro FX 5800, Quadro FX 4800, Quadro FX 3800, GeForce 8800 GTS 512,
    GeForce 9800 GT, GeForce 8800 GT, GeForce 9800 GX2, GeForce 9800 GT,
    GeForce 8800 GS, GeForce GTS 240, GeForce 9800M GTX,
    GeForce 8800M GTS, GeForce GTX 280M, GeForce 9800M GT,
    GeForce 8800M GTX, GeForce 8800 GS, GeForce 9600 GSO,
    GeForce 8800 GT, GeForce 9800 GTX, GeForce 9800 GTX+,
    GeForce 9800 GT, GeForce GTS 250, GeForce 9800M GTX,
    GeForce GTX 260M, Quadro FX 3700, Quadro FX 3600M, Quadro FX 2800M,
    Quadro FX 3700M, Quadro FX 3800M, GeForce 9600 GT, GeForce 9600 GS,
    GeForce 9600 GSO 512, GeForce GT 130, GeForce GT 140,
    GeForce 9800M GTS, GeForce 9700M GTS, GeForce 9800M GS,
    GeForce 9800M GTS, Quadro FX 1800, Quadro FX 2700M, GeForce 9500 GT,
    GeForce 9400 GT, GeForce 9500 GT, GeForce 9500 GS, GeForce GT 120,
    GeForce 9600M GT, GeForce 9600M GS, GeForce 9600M GT,
    GeForce 9700M GT, GeForce 9500M G, GeForce 9650M GT, GeForce GT 130M,
    GeForce 9500 GT, Quadro FX 380, Quadro FX 580, Quadro FX 1700M,
    Quadro FX 770M, GeForce 9300 GE, GeForce 9300 GS, GeForce 8400 GS,
    GeForce 9300M GS, GeForce G100, GeForce 9200M GS, GeForce 9300M GS,
    Quadro NVS 150M, Quadro NVS 160M, GeForce G 105M, GeForce G 103M,
    Quadro NVS 420, Quadro FX 370 LP, Quadro NVS 450, Quadro NVS 295,
    GeForce 9100, GeForce 8300, GeForce 8200, nForce 730a, GeForce 9200,
    nForce 980a/780a SLI, nForce 750a SLI, GeForce 8100 / nForce 720a,
    GeForce 9100M G, GeForce 8200M G, GeForce 9400, GeForce 9400M G,
    GeForce 9400M, GeForce 9300 / nForce 730i, GeForce G102M,
    GeForce G102M, GeForce 9400, ION, ION LE, GeForce GT 220,
    GeForce 210, GeForce GT 230M, GeForce GT 240M, GeForce G210,
    GeForce 205, GeForce 310, GeForce 210, GeForce 310, GeForce G210M,
    Quadro FX 380 LP, GeForce GT 240, GeForce GTS 260M, GeForce GTS 250M
[    21.978] (II) VESA: driver for VESA chipsets: vesa
[    21.979] (II) FBDEV: driver for framebuffer: fbdev
[    21.979] (++) using VT number 7

[    21.979] (--) NV: Found NVIDIA GeForce 6600 GT at 01@00:00:0
[    21.979] (EE) NV: Kernel modesetting driver in use, refusing to load
[    21.979] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    21.979] (WW) Falling back to old probe method for vesa
[    21.979] (II) Loading sub module "fbdevhw"
[    21.979] (II) LoadModule: "fbdevhw"
[    21.979] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.979] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.980]     compiled for 1.9.0, module version = 0.0.2
[    21.980]     ABI class: X.Org Video Driver, version 8.0
[    21.981] (**) FBDEV(0): claimed PCI slot 1@0:0:0
[    21.981] (II) FBDEV(0): using default device
[    21.981] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    21.981] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    21.981] (==) FBDEV(0): RGB weight 888
[    21.981] (==) FBDEV(0): Default visual is TrueColor
[    21.981] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.981] (II) FBDEV(0): hardware: nouveaufb (video memory: 5176kB)
[    21.981] (II) FBDEV(0): checking modes against framebuffer device...
[    21.981] (II) FBDEV(0): checking modes against monitor...
[    21.981] (--) FBDEV(0): Virtual size is 1440x900 (pitch 1440)
[    21.981] (**) FBDEV(0):  Built-in mode "current"
[    21.981] (==) FBDEV(0): DPI set to (96, 96)
[    21.981] (II) Loading sub module "fb"
[    21.981] (II) LoadModule: "fb"
[    21.982] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.982] (II) Module fb: vendor="X.Org Foundation"
[    21.982]     compiled for 1.9.0, module version = 1.0.0
[    21.982]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.982] (**) FBDEV(0): using shadow framebuffer
[    21.982] (II) Loading sub module "shadow"
[    21.982] (II) LoadModule: "shadow"
[    21.982] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    21.982] (II) Module shadow: vendor="X.Org Foundation"
[    21.982]     compiled for 1.9.0, module version = 1.1.0
[    21.982]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.982] (==) Depth 24 pixmap format is 32 bpp
[    21.995] (==) FBDEV(0): Backing store disabled
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.997] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.998] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    21.999] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.000] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.002] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    22.003] (==) FBDEV(0): DPMS enabled
[    22.004] (==) RandR enabled
[    22.004] (II) Initializing built-in extension Generic Event Extension
[    22.004] (II) Initializing built-in extension SHAPE
[    22.004] (II) Initializing built-in extension MIT-SHM
[    22.004] (II) Initializing built-in extension XInputExtension
[    22.004] (II) Initializing built-in extension XTEST
[    22.004] (II) Initializing built-in extension BIG-REQUESTS
[    22.004] (II) Initializing built-in extension SYNC
[    22.004] (II) Initializing built-in extension XKEYBOARD
[    22.004] (II) Initializing built-in extension XC-MISC
[    22.004] (II) Initializing built-in extension SECURITY
[    22.004] (II) Initializing built-in extension XINERAMA
[    22.004] (II) Initializing built-in extension XFIXES
[    22.004] (II) Initializing built-in extension RENDER
[    22.004] (II) Initializing built-in extension RANDR
[    22.004] (II) Initializing built-in extension COMPOSITE
[    22.004] (II) Initializing built-in extension DAMAGE
[    22.004] (II) Initializing built-in extension GESTURE
[    22.023] (II) AIGLX: Screen 0 is not DRI2 capable
[    22.023] (II) AIGLX: Screen 0 is not DRI capable
[    22.029] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    22.029] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    22.071] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.096] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.096] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.096] (II) LoadModule: "evdev"
[    22.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.097] (II) Module evdev: vendor="X.Org Foundation"
[    22.097]     compiled for 1.9.0, module version = 2.3.2
[    22.097]     Module class: X.Org XInput Driver
[    22.097]     ABI class: X.Org XInput driver, version 11.0
[    22.097] (**) Power Button: always reports core events
[    22.097] (**) Power Button: Device: "/dev/input/event1"
[    22.097] (II) Power Button: Found keys
[    22.097] (II) Power Button: Configuring as keyboard
[    22.097] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.097] (**) Option "xkb_rules" "evdev"
[    22.097] (**) Option "xkb_model" "emachines"
[    22.097] (**) Option "xkb_layout" "us"
[    22.097] (**) Option "xkb_options" "lv3:ralt_switch,grp:shift_caps_toggle"
[    22.110] (II) XKB: reuse xkmfile /var/lib/xkb/server-022DC8FF986A565D353D8FA64471557ADABA5D5B.xkm
[    22.116] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.116] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.116] (**) Power Button: always reports core events
[    22.116] (**) Power Button: Device: "/dev/input/event0"
[    22.116] (II) Power Button: Found keys
[    22.116] (II) Power Button: Configuring as keyboard
[    22.116] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.116] (**) Option "xkb_rules" "evdev"
[    22.116] (**) Option "xkb_model" "emachines"
[    22.116] (**) Option "xkb_layout" "us"
[    22.116] (**) Option "xkb_options" "lv3:ralt_switch,grp:shift_caps_toggle"
[    22.132] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    22.133] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.133] (**) AT Translated Set 2 keyboard: always reports core events
[    22.133] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    22.133] (II) AT Translated Set 2 keyboard: Found keys
[    22.133] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    22.133] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    22.133] (**) Option "xkb_rules" "evdev"
[    22.133] (**) Option "xkb_model" "emachines"
[    22.133] (**) Option "xkb_layout" "us"
[    22.133] (**) Option "xkb_options" "lv3:ralt_switch,grp:shift_caps_toggle"
[    22.133] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    22.133] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    22.134] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    22.134] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    22.134] (II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    22.134] (II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    22.134] (II) ImPS/2 Generic Wheel Mouse: Found relative axes
[    22.134] (II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    22.134] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    22.134] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    22.134] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.134] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    22.134] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    22.134] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    22.134] (II) No input driver/identifier specified (ignoring)

---

### Post by 3rdalbum on 2011-03-16
Ubuntu's default Nouveau driver is in use.

---

