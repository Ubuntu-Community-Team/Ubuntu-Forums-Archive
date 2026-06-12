---
title: "time to give up cant fix resultion problem"
date: 2010-03-05
forum: General Help
---

### Post by legend_018 on 2010-03-05
I'm a newbie. All I wanted to do was install Ubuntu so that my 3 year old can do some basic web browsing. Thought I've give Ubuntu a try. I have a nice flat screen monitor. However of course display options shows unknown and the highest resolution I can go is 800x600. I read tons of information that has tons of notes about running commands or editing files. There never detailed on exactly what to do. I'm a newbie? I've been poking at stuff and reading stuff and trying a few things off and on for weeks now. I even posted something awhile back and got no replys and now I can't find the original message.

800X600 is too big on my large flat screen monitor.  we have to scroll right and left and up and down in firefox just to play a little dora game on dora's website.  It's just too silly. When I used to have Windows loaded, it would never do this. 

Can anyone help me with specific instructions. I did get xrandr to run and it does only show 800X600 as the highest resolution.  What do I have to do EXACTLY to get it to a higher resolution. I hit control Alt f1 to get to the command line and ran the xrandr to see what the results were. I than hit control Alt F7 to get back to my screen where firefox is running.

---

### Post by flippo on 2010-03-05
Sadly, linux and video cards is a weak area.  The linux community is actively working to provide better "default" video support, but is a work in progress.  For now there are some, sometimes difficult, user configurations required.

I can do my very best to walk you through getting video working on your computer, but I need some information first, and "I don't know" is a fine answer.

My questions:
What kind of video card do you have? 
If you dont know list the output of ```
sudo lspci
```
What drivers are you using?
If you dont know list the output of ```
sudo cat /var/log/Xorg.0.log | grep module
```
Do you have a xorg.conf?
If you don't know list the output of ```
sudo cat /etc/X11/xorg.conf
```

Finally,
What ubuntu version are you running?

---

### Post by Agent ME on 2010-03-05
What video card do you have? Does the Hardware Drivers tool (under System -> Administration) list any available drivers?

---

### Post by legend_018 on 2010-03-05
just wanted to let you know that I got your messages and will be working on this and getting answers back to you as soon as possible. probably tomorrow morning at some point since it's 10:30pm right now and have a baby in the house crying.  I will write back as soon as I can. Please check back.  Thanks. : )

---

### Post by legend_018 on 2010-03-05
ok sudo lspci says vga compatible nVidia Corp NV18 Geforce4 MX 440 AGP

I dont think I have a xorg.conf. Said it couldnt find it. I'll look again. I'm running the latest version as it was just installed a few weeks ago. 9.10 is the version

when I go into hardware drivers, yes it sees nvidia accelerates graphics card. It's not activated right now, but I did previously install and activate it. It than makes you go into the nvidia settings to look and/or change stuff. at that point, 800X600 was no longer available and there was only 2 "lower than 800X600", available. So I deactivated it.

as far as the grepping from the log. not sure how to get all the stuff that showed up on the command line into this mail message so here is the entire log:

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux chayse-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=a18a856a-f3e9-4033-83aa-83fd55f3fb26 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  5 15:09:17 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0181:10de:01b6 nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 162, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default nv Device 0"
        Driver    "nv"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default nv Screen 0"
        Device    "Builtin Default nv Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default nv Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default nv Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default nv Device 0"
(==) No monitor specified for screen "Builtin Default nv Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.1.14
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
     RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
     GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
     GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
     Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
     GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
     GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
     Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
     Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
     GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
     GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
     GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
     GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
     GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
     Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
     GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
     Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
     GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
     Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
     GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
     GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
     GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
     GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 440 Go 64M,
     Quadro NVS,  Quadro4 500 GoGL,  GeForce4 410 Go 16M,
     GeForce4 MX 440 with AGP8X,  GeForce4 MX 440SE with AGP8X,
     GeForce4 MX 420 with AGP8X,  GeForce4 MX 4000,  GeForce4 448 Go,
     GeForce4 488 Go,  Quadro4 580 XGL,  Quadro4 NVS 280 SD,
     Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
     GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
     Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
     GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
     GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
     GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
     Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
     GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
     GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
     GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
     GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
     GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
     GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
     Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
     GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
     Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
     GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
     GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
     GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
     Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
     Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
     Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
     GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
     GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
     GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
     GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
     GeForce FX 5100,  GeForce FX Go5200 32M/64M,  Quadro NVS 55/280 PCI,
     Quadro FX 500/600 PCI,  GeForce FX Go53xx Series,
     GeForce FX Go5100,  GeForce FX 5900 Ultra,  GeForce FX 5900,
     GeForce FX 590T,  GeForce FX 5950 Ultra,  GeForce FX 5900ZT,
     Quadro FX 3000,  Quadro FX 700,  GeForce FX 5700 Ultra,
     GeForce FX 5700,  GeForce FX 5700LE,  GeForce FX 5700VE,
     GeForce FX Go5700,  GeForce FX Go5700,  Quadro FX Go1000,
     Quadro FX 1100,  GeForce 7650 GS,  GeForce 7600 GT,
     GeForce 7600 GS,  GeForce 7300 GT,  GeForce 7600 LE,
     GeForce 7300 GT,  GeForce Go 7700,  GeForce Go 7600,
     GeForce Go 7600 GT},  Quadro NVS 300M,  GeForce Go 7900 SE,
     Quadro FX 550M,  Quadro FX 560,  GeForce 6150SE,
     GeForce 6100 nForce 405,  GeForce 6100 nForce 400,
     GeForce 6100 nForce 420,  GeForce 8600 GTS,  GeForce 8600 GT,
     GeForce 8600 GT,  GeForce 8600 GS,  GeForce 8400 GS,
     GeForce 9500M GS,  GeForce 8600M GT,  GeForce 9650M GS,
     GeForce 8700M GT,  Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,
     Quadro FX 1600M,  Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,
     GeForce 8500 GT,  GeForce 8400 GS,  GeForce 8300 GS,
     GeForce 8400 GS,  GeForce 8600M GS,  GeForce 8400M GT,
     GeForce 8400M GS,  GeForce 8400M G,  Quadro NVS 140M,
     Quadro NVS 130M,  Quadro NVS 135M,  GeForce 9400 GT,
     Quadro FX 360M,  GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
     GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
     GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
     Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
     GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
     GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
     GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
     GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
     GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
     GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
     Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
     GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
     GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
     GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
     GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
     GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
     GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
     GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
     Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
     GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
     GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
     Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
     Quadro NVS 450,  Quadro NVS 295
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA  GeForce4 MX 440 with AGP8X at 01@00:00:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: " GeForce4 MX 440 with AGP8X"
(II) NV(0): Creating default Display subsection in Screen section
    "Builtin Default nv Screen 0" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF0000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 65536 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (hsync out of range)
(II) NV(0): Not using default mode "960x540" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.

---

### Post by 2hot6ft2 on 2010-03-05
I have the PCI version of that graphics card
nVidia Corp NV18 Geforce4 MX 440 AGP
mine is 
nVidia Corp Geforce4 MX 440 PCI

So there is a driver for it in
System > Administration > Hardware Drivers
Just select the driver in the top window and at the bottom click on Activate Driver for it to download it and activate it for you.

Missed this
> when I go into hardware drivers, yes it sees nvidia accelerates graphics card. It's not activated right now, but I did previously install and activate it. It than makes you go into the nvidia settings to look and/or change stuff. at that point, 800X600 was no longer available and there was only 2 "lower than 800X600", available. So I deactivated it.

Might check the version against the one on their website then.

I think it's the same version as the one as on the nvidia.com website but I may be wrong.

---

### Post by flippo on 2010-03-05
Yes, I would highly recommend using the proprietary driver.  Right now your log says your using the nv driver, which is a very weak driver.  It is provided by nvidia as a minimal driver, just so you can have free working software.  Nvidia does not intend on improving it.  The proprietary driver is very good, and it comes with a configuration utility "nvidia-settings" which will take care of all the screen resolution goodies for you.

If you have any more troubles please post them.

---

### Post by 2hot6ft2 on 2010-03-05
There is a new driver for it on their website here
[http://www.nvidia.com/object/linux_display_ia32_96.43.16.html](http://www.nvidia.com/object/linux_display_ia32_96.43.16.html)

Release Date:
	
2010.02.11

---

### Post by 2hot6ft2 on 2010-03-05
Installing it:
Download it to your home folder.
Personally I reboot to do the NVIDIA installs so
Reboot and go into recovery mode
When you get to the choices choose Shell prompt (it will show the prompt almost immediately at the bottom of the screen)
Put your cursor at the prompt and use
```
cd /home/<yourusername>/
```
Where <yourusername> is the name you log in with without the arrows<>
then
```
ls
```
You should see the driver listed.
Then use
```
sh NVID
```
And hit the Tab button and it will complete the name for you, then hit Enter
(unless you WANT to type the whole name in)

Agree using your arrow keys to choose. It will take a little while .
When it asks if you want it to replace Xorg select Yes

When it finishes type
```
reboot
```
And hit Enter
All done

That's how I do it.

---

### Post by legend_018 on 2010-03-05
> **2hot6ft2 said:**
> There is a new driver for it on their website here
[http://www.nvidia.com/object/linux_display_ia32_96.43.16.html](http://www.nvidia.com/object/linux_display_ia32_96.43.16.html)

Release Date:
    
2010.02.11

The version I have says version 96, sounds pretty close, but regardless...I downloaded the .run file and tried to run it out at control alt F1 and it keeps saying I have to close out of X (?). I'm not sure what to do to close out of X. I tried running /ect/init.dl/gdm stop but it doesn't seem to do the trick.

also, just as a fyi: I activated the driver again for nvidia. as I mentioned, unfortunately it still limits me with display options.

---

### Post by legend_018 on 2010-03-05
after reactivating the version says 96.43.13
after reboot there is a new nvidia xserver settings option.
under display configuration it says hidden and than resolution says auto, 640X480 and 320X240. As mentioned before, installing these drivers is even worse since 800X600 isn't even available anymore.

---

### Post by flippo on 2010-03-06
Are those the options that pop up running```
gksudo nvidia-settings
```

If so, please post your /var/log/Xorg.0.log using the proprietary drivers.

---

### Post by legend_018 on 2010-03-06
> **2hot6ft2 said:**
> Installing it:
That's how I do it.

ok will work on this in the morning. Do I have to hit anything while rebooting to get it to come up in recovery mode? I know in windows you hit the F8 key and it comes up with a menu for troubleshooting stuff.

---

### Post by flippo on 2010-03-06
The command I gave you is a GUI based command, so you want to boot in normal mode.

EDIT:
Ooops, didn't notice you were talking about the .run file...
I always kill my X server ("sudo /etc/init.d/gdm stop" from tty1 <ctrl+alt+f1 when at the login screen>) to run the .run file...  I don't actually remember how to boot recovery mode, I pulled it off my grub a while ago....

---

### Post by akand074 on 2010-03-06
> **legend_018 said:**
> The version I have says version 96, sounds pretty close, but regardless...I downloaded the .run file and tried to run it out at control alt F1 and it keeps saying I have to close out of X (?). I'm not sure what to do to close out of X. I tried running /ect/init.dl/gdm stop but it doesn't seem to do the trick.

also, just as a fyi: I activated the driver again for nvidia. as I mentioned, unfortunately it still limits me with display options.

Did you go to System > Administration > NVIDIA X Server Settings

and then the second section called X Server Display Configuration and change your resolution from there? Odd that your having your problem, on every computer I've had Ubuntu installed on it automatically set it to the best resolution even before installing the proprietary drivers. All of them have been connected through PCIe and not AGP but I don't see why that would matter. Though I do believe it has less OEM support. Still. Hope you manage to solve your problem!

---

### Post by legend_018 on 2010-03-06
> **flippo said:**
> Are those the options that pop up running```
gksudo nvidia-settings
```If so, please post your /var/log/Xorg.0.log using the proprietary drivers.

sorry tried this but get error cannot open display when running this command.  : (

here is the log anyways:

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux chayse-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=a18a856a-f3e9-4033-83aa-83fd55f3fb26 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  5 23:54:47 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0181:10de:01b6 nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 162, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 440 with AGP8X at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.18.20.21.15
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 440 with AGP8X at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.

---

### Post by flippo on 2010-03-06
Odd, your xorg.0.log doesn't indicate that its looking available screen resolutions.  

Did you mention what version of ubuntu your running?

Also, what error do you get running```
gksudo nvidia-settings
```(NOTE: you should run this once logged-in from a terminal in a graphical environment)

---

### Post by legend_018 on 2010-03-06
When I run gksudo nvidia settings I can't cant open display.

I'm stuck because I can't run gksudo to give you the information you requested.
I'm also stuck because I can't  run the .run file because it says I have to close out of X and if I try running sudo /etc/init.d/gdm stop, it doesn't work.

9.10 is the version for Ubuntu.

Yes, I am going through that path to get to the settings for the Nvidia.

---

### Post by legend_018 on 2010-03-06
great, got the .run file to run and installed the latest nvidia drivers. file was nvidia-linux-x86-96.43.16-pkg1.run

not the gui screen wont show up because there is a black screen that says out of range. tried rebooting. alt, control F1 does bring me to a prompt.

Now I cant even see anything. darn.

---

### Post by PARO on 2010-03-06
I'd forget about the NVIDIA legacy drivers if you only want the machine to do web browsing and such.  I haven't got them working on karmic either (you are using karmic right?) 

Your resolution problem is the same that many people have had (myself included).  If you can still get into your desktop with the nv drivers i'd do that for now.  Then follow sharaq's instructions in post number 6 here: [http://ubuntuforums.org/showthread.php?t=1364460](http://ubuntuforums.org/showthread.php?t=1364460) to manually set a new resolution option for your monitor.

Hope this helps.

---

### Post by legend_018 on 2010-03-06
reinstalled ubuntu and ran all updates, had to since didn't know how to get it up and running from the last problem.

back to display stuff. following all those steps but when I run the newmode line, which I know I'm running correctly it says named color or font doesnt exist

---

### Post by PARO on 2010-03-06
hm.. that's a strange sounding error. You can copy and paste from within the terminal to make sure you have your modeline correct. Beyond that, I dont know why it would say that. sorry.

---

### Post by flippo on 2010-03-06
Can you paste the exact error your getting? (to copy & paste from gnome-terminal (your default terminal) its ctrl+shift+c and ctrl+shift+v).

---

### Post by legend_018 on 2010-03-06
> **flippo said:**
> Can you paste the exact error your getting? (to copy & paste from gnome-terminal (your default terminal) its ctrl+shift+c and ctrl+shift+v).

sorry, cant get to it right now, but it think its the same as this one....although where I found this, the person never got any help to why it was happening.

Hello, I have the same 800x600 problem. I followed your advice to stage 3 and got this reply:-
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  21
  Current serial number in output stream:  21
If you can help in any way I'd be very grateful
Thankyou.......sarum

---

### Post by flippo on 2010-03-06
Okay, I've never tried the xrandr method.  Please post the output of ```
xrandr
```
and please give the exact line that produces the error

---

### Post by legend_018 on 2010-03-06
output is:
Screen 0: minimum 320 x 240, current 640 x 480, maximum 1024 x 768
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
   1024x768_60.00   59.9 

Also the line where I get the error is:

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18


and as a fyi:  cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

---

### Post by flippo on 2010-03-06
According to you xrandr output you have a modeline for 1024x768 resolution, you should be able to set it to run:```
 $xrandr --output default --mode 1024x768_60.00 
```

---

### Post by legend_018 on 2010-03-06
unfortunately I run that and get this:

xrandr --output default --mode 1024x768_60.00
xrandr: Configure crtc 0 failed

---

### Post by PARO on 2010-03-06
i just found a neat little program called lxrandr (its in the repos) and have tested that on 3 computers, it's saving me some time in typing in the commands by hand. You might want to give that a try and see if you don't get the same error that way. Hope it works.

---

### Post by legend_018 on 2010-03-06
> **PARO said:**
> i just found a neat little program called lxrandr (its in the repos) and have tested that on 3 computers, it's saving me some time in typing in the commands by hand. You might want to give that a try and see if you don't get the same error that way. Hope it works.

I could give it a try, but where do I get it? What does repos mean? Is there a site where I can get it from?

---

### Post by PARO on 2010-03-06
that means you go to synaptic package manager and search for lxrandr and check off the box, easy as pie :) .

---

### Post by legend_018 on 2010-03-06
> **PARO said:**
> that means you go to synaptic package manager and search for lxrandr and check off the box, easy as pie :) .


I did install it, but where do I find how to run this lxrandr. Is it on the menu's anywhere? I don't seem to see it.

---

### Post by legend_018 on 2010-03-06
got it to run from terminal. doesn't work. only allows allows 2 resolution sizes, 640x480 is the largest which brings me back to the entire original problem.

---

### Post by legend_018 on 2010-03-06
> **legend_018 said:**
> output is:
Screen 0: minimum 320 x 240, current 640 x 480, maximum 1024 x 768
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
   1024x768_60.00   59.9 

Also the line where I get the error is:

xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18


and as a fyi:  cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

If I could get thru what ever is happening here with this error, maybe I could get further with this, don't know. Must be some way to be able to change my resolution. This is pretty silly.

---

### Post by patchwork on 2010-03-06
Instead of trying with xrandr, have you added the mode and modeline manually to your /etc/X11/xorg.conf?  The modeline goes in the monitor section, and the mode goes in the screen section, like this 

```
kevin@crystalpepsi:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen0" 0 0
EndSection

Section "ServerFlags"
Option "Xinerama" "0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "AUO"
DisplaySize 344 193
#Modeline "1366x768" 69.50 1366 1414 1446 1446 768 771 775 806 -hsync -vsync
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
Option "PreferredMode" "1368x768_60.00"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce G 105M"
Option "NoLogo" "True"
Option "NvAGP" "0"
Option "UseEDID" "False"
Option "AllowSHMPixmaps" "True"
Option "ExactModeTimingsDVI" "True"
Option "ModeValidation" "NoHorizSyncCheck,NoDFPNativeResolutionCheck,NoExt endedGpuCapabilitiesCheck,NoWidthAlignmentCheck,No VertRefreshCheck"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
SubSection "Display"
Modes "1368x768_60.00" #"1366x768"
Depth 24
EndSubSection
EndSection

```

---

### Post by legend_018 on 2010-03-06
> **patchwork said:**
> Instead of trying with xrandr, have you added the mode and modeline manually to your /etc/X11/xorg.conf?  The modeline goes in the monitor section, and the mode goes in the screen section, like this 

```
kevin@crystalpepsi:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen0" 0 0
EndSection

Section "ServerFlags"
Option "Xinerama" "0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "AUO"
DisplaySize 344 193
#Modeline "1366x768" 69.50 1366 1414 1446 1446 768 771 775 806 -hsync -vsync
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
Option "PreferredMode" "1368x768_60.00"
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce G 105M"
Option "NoLogo" "True"
Option "NvAGP" "0"
Option "UseEDID" "False"
Option "AllowSHMPixmaps" "True"
Option "ExactModeTimingsDVI" "True"
Option "ModeValidation" "NoHorizSyncCheck,NoDFPNativeResolutionCheck,NoExt endedGpuCapabilitiesCheck,NoWidthAlignmentCheck,No VertRefreshCheck"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
Option "TwinView" "0"
SubSection "Display"
Modes "1368x768_60.00" #"1366x768"
Depth 24
EndSubSection
EndSection

```

I could try it. Is that best done using VI and use the commands to insert a line? haven't done that in a very very long time, played with Linux Redhat a longggg time ago. Is VI the best route to go to try making these changes?

---

### Post by flippo on 2010-03-06
```
gksudo gedit /etc/X11/xorg.conf
```is best for beginner (unless of course your a vi fan).

you want to change his device section to use the nv driver, and reflect your graphics card.  You also need to change his monitor section to reflect your screen resolutions.

---

### Post by patchwork on 2010-03-06
You can use any editor, as long as you do it by root.  I personally use sudo gedit



EDIT:   yes, what flippo said

---

### Post by legend_018 on 2010-03-06
this is what is in that file now? just wondering the best way to tackle this and what I should actually add and/or edit in this file

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by blackened on 2010-03-06
> **flippo said:**
> ```
gksudo gedit /etc/X11/xorg.conf
```is best for beginner (unless of course your a vi fan).

If you're still stuck in the CLI, then you can use nano instead of VI. The commands are a little more straight-forward, just edit appropriately and use ctrl+x (answer yes to overwrite) to save your changes.

Just for giggles, is your monitor properly reporting its EDID info?

```
sudo apt-get install xresprobe
```
then post the output of 
```
sudo ddcprobe
```

---

### Post by patchwork on 2010-03-06
type ```
cvt xres yres
```, where xres is your x resolution and yres is your y resolution ( ex. 1024 768)

copy the modeline portion into the monitor section, and enter Modes "<name of mode in modeline" in the screen section


EDIT: If your computer is not capturing the edid information (very likely since you are having this problem), add the
```
 Option "UseEDID" "false"
``` in the device section

---

### Post by legend_018 on 2010-03-06
> **blackened said:**
> If you're still stuck in the CLI, then you can use nano instead of VI. The commands are a little more straight-forward, just edit appropriately and use ctrl+x (answer yes to overwrite) to save your changes.

Just for giggles, is your monitor properly reporting its EDID info?

```
sudo apt-get install xresprobe
```then post the output of 
```
sudo ddcprobe
```

$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV18 Board - p162nz Chip Rev A2
memory: 65536kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 80x60 (text)
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail

---

### Post by blackened on 2010-03-06
And you said you already have an xorg.conf generated? Post it if you would:
```
cat /etc/X11/xorg.conf
```

---

### Post by flippo on 2010-03-06
Just for ease of use, copy and paste this into your xorg (overwrite whatever you put there)

```
Section "ServerLayout"
  Identifier "Default Layout"
  Screen 0 "Screen0" 0 0
EndSection

Section "Monitor"
  Identifier "Monitor0"
  Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
  Option "PreferredMode" "1024x786_60.00"
EndSection

Section "Device"
  Identifier "Device0"
  Driver "nv"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Device0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Modes "1024x768_60.00"
    Depth 24
  EndSubSection
EndSection
```


EDIT:
lol... there are to many of us working on this, in the time it took me to write this there were 5 posts...

---

### Post by blackened on 2010-03-06
> **flippo said:**
> EDIT:
lol... there are to many of us working on this, in the time it took me to write this there were 5 posts...

The good part is that it seems we're all going in the same direction.

---

### Post by legend_018 on 2010-03-06
thanks so much for sticking with me. I'm just getting to these updates. I still can't believe what one has to go through though. 

I will work on this again tomorrow so I'll let you know the results. I would work on it right now, but I can't.  


Thanks

---

### Post by patchwork on 2010-03-06
I know it seems like a lot, but it normally isn't necessary (it's a problem with your monitor's edid information that's causing it), and once complete you shouldn't have to do it again.

---

### Post by PARO on 2010-03-06
> this is what is in that file now? just wondering the best way to tackle this and what I should actually add and/or edit in this file

Section "Screen"
Identifier "Default Screen"
DefaultDepth 24
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Default Device"
Driver "nvidia"
Option "NoLogo" "True"
EndSection

Oh you have the nvidia drivers working now? Did you try nvidia-settings then? That should fix your xorg.conf for you (unless you have an older card where nvidia settings won't even give you resolution options!) Maybe that's why your output looks like that...

---

### Post by patchwork on 2010-03-06
Without the edid information, no modes are validated, and he gets kicked to nvidia-auto-select.  Hence the custom modeline for the xorg.conf

---

### Post by legend_018 on 2010-03-07
Update at this time. wont let me go above 800X600. xorg looks like this (see xorg below).

xrandr results:
xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1024 x 768
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
   1024x768_60.00   59.9  

if I try to go into system preference display I now get it appears your graphics driver does not support the necessary extensions to use this tool

If I try to go into nvidia x server settings, it now says you dont appear to be using the nvidia x driver. 

this was after making the changes to the file and rebooting


[SIZE=6]**xorg**[/SIZE]

Section "ServerLayout"
  Identifier "Default Layout"
  Screen 0 "Screen0" 0 0
EndSection

Section "Monitor"
  Identifier "Monitor0"
  Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
  Option "PreferredMode" "1024x786_60.00"
EndSection

Section "Device"
  Identifier "Device0"
  Driver "nv"
 Option "UseEDID" "false"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Device0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Modes "1024x768_60.00"
    Depth 24
  EndSubSection
EndSection

---

### Post by patchwork on 2010-03-07
OK, it is safe to replace nv with nvidia ( I believe you are getting the error because the nv driver deosn't support the UseEDID and PreferredMode Options...I could be wrong, but I think those are nvidia driver specific).  

Also, what is the content of your /var/log/Xorg.0.log?

EDIT:  Didn't read close enough, error not from preferredmode or useedid, but from not having nvidia selected as driver.  Doesn't change my advice, however.

Also, don't worry about the Display Preferences or Nvidia-Xsettings just yet.  

You don't need to reboot the computer to restart the X server, just type ```
sudo service gdm restart
```

---

### Post by legend_018 on 2010-03-07
> **patchwork said:**
> OK, it is safe to replace nv with nvidia ( I believe you are getting the error because the nv driver deosn't support the UseEDID and PreferredMode Options...I could be wrong, but I think those are nvidia driver specific).  

Also, what is the content of your /var/log/Xorg.0.log?

EDIT:  Didn't read close enough, error not from preferredmode or useedid, but from not having nvidia selected as driver.  Doesn't change my advice, however.

Also, don't worry about the Display Preferences or Nvidia-Xsettings just yet.  

You don't need to reboot the computer to restart the X server, just type ```
sudo service gdm restart
```


here it is:

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux chayse-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=840cb1fb-2002-4018-ad17-38921d21ed7f ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar  7 08:04:16 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0181:10de:01b6 nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 162, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.1.14
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
     RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
     GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
     GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
     Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
     GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
     GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
     Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
     Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
     GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
     GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
     GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
     GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
     GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
     Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
     GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
     Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
     GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
     Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
     GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
     GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
     GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
     GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 440 Go 64M,
     Quadro NVS,  Quadro4 500 GoGL,  GeForce4 410 Go 16M,
     GeForce4 MX 440 with AGP8X,  GeForce4 MX 440SE with AGP8X,
     GeForce4 MX 420 with AGP8X,  GeForce4 MX 4000,  GeForce4 448 Go,
     GeForce4 488 Go,  Quadro4 580 XGL,  Quadro4 NVS 280 SD,
     Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
     GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
     Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
     GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
     GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
     GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
     Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
     GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
     GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
     GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
     GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
     GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
     GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
     GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
     Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
     GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
     Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
     GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
     GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
     GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
     Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
     Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
     Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
     GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
     GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
     GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
     GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
     GeForce FX 5100,  GeForce FX Go5200 32M/64M,  Quadro NVS 55/280 PCI,
     Quadro FX 500/600 PCI,  GeForce FX Go53xx Series,
     GeForce FX Go5100,  GeForce FX 5900 Ultra,  GeForce FX 5900,
     GeForce FX 590T,  GeForce FX 5950 Ultra,  GeForce FX 5900ZT,
     Quadro FX 3000,  Quadro FX 700,  GeForce FX 5700 Ultra,
     GeForce FX 5700,  GeForce FX 5700LE,  GeForce FX 5700VE,
     GeForce FX Go5700,  GeForce FX Go5700,  Quadro FX Go1000,
     Quadro FX 1100,  GeForce 7650 GS,  GeForce 7600 GT,
     GeForce 7600 GS,  GeForce 7300 GT,  GeForce 7600 LE,
     GeForce 7300 GT,  GeForce Go 7700,  GeForce Go 7600,
     GeForce Go 7600 GT},  Quadro NVS 300M,  GeForce Go 7900 SE,
     Quadro FX 550M,  Quadro FX 560,  GeForce 6150SE,
     GeForce 6100 nForce 405,  GeForce 6100 nForce 400,
     GeForce 6100 nForce 420,  GeForce 8600 GTS,  GeForce 8600 GT,
     GeForce 8600 GT,  GeForce 8600 GS,  GeForce 8400 GS,
     GeForce 9500M GS,  GeForce 8600M GT,  GeForce 9650M GS,
     GeForce 8700M GT,  Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,
     Quadro FX 1600M,  Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,
     GeForce 8500 GT,  GeForce 8400 GS,  GeForce 8300 GS,
     GeForce 8400 GS,  GeForce 8600M GS,  GeForce 8400M GT,
     GeForce 8400M GS,  GeForce 8400M G,  Quadro NVS 140M,
     Quadro NVS 130M,  Quadro NVS 135M,  GeForce 9400 GT,
     Quadro FX 360M,  GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
     GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
     GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
     Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
     GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
     GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
     GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
     GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
     GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
     GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
     Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
     GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
     GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
     GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
     GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
     GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
     GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
     GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
     Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
     GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
     GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
     Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
     Quadro NVS 450,  Quadro NVS 295
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA  GeForce4 MX 440 with AGP8X at 01@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: " GeForce4 MX 440 with AGP8X"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xF0000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 65536 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using mode "1024x768_60.00" (hsync out of range)
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (hsync out of range)
(II) NV(0): Not using default mode "960x540" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using mode "1024x768_60.00" (no mode of this name)
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(WW) NV(0): Option "UseEDID" is not used
(WW) NV(0): Option "PreferredMode" is not used
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.

---

### Post by legend_018 on 2010-03-07
> **patchwork said:**
> OK, it is safe to replace nv with nvidia ( I believe you are getting the error because the nv driver deosn't support the UseEDID and PreferredMode Options...I could be wrong, but I think those are nvidia driver specific).  

Also, what is the content of your /var/log/Xorg.0.log?

EDIT:  Didn't read close enough, error not from preferredmode or useedid, but from not having nvidia selected as driver.  Doesn't change my advice, however.

Also, don't worry about the Display Preferences or Nvidia-Xsettings just yet.  

You don't need to reboot the computer to restart the X server, just type ```
sudo service gdm restart
```


I changed it and can now go into the settings, but the highest I can choose is still 640x480.
Am I suppose to rerun any commands after editing that file?

---

### Post by patchwork on 2010-03-07
From your cvt (posted earlier):
```
and as a fyi:  cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3)** hsync: 47.82** kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```From your Xorg.0.log ```
II) NV(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using mode "1024x768_60.00" (hsync out of range)
```


Add 
```
 HorizSync 31.5-48.0
``` to your Monitor Section

---

### Post by legend_018 on 2010-03-07
> **patchwork said:**
> From your cvt (posted earlier):
```
and as a fyi:  cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3)** hsync: 47.82** kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```From your Xorg.0.log ```
II) NV(0): Monitor0: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Monitor0: Using default vrefresh range of 50.00-70.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using mode "1024x768_60.00" (hsync out of range)
```
Add 
```
 HorizSync 31.5-48.0
``` to your Monitor Section


I was going to do this, but for some reason when I go to Terminal, it just brings up this big white screen with no prompt for me to type anything. This has never happened and I've been using terminal and using gedit to modify the files.

---

### Post by patchwork on 2010-03-07
What driver is currently in your xorg.conf (nv or nvidia)?

If it's nvidia, did you remove the driver at some point over the past few days?

If it's nv, what happens when you drop to tty1?

---

### Post by legend_018 on 2010-03-07
> **patchwork said:**
> What driver is currently in your xorg.conf (nv or nvidia)?

If it's nvidia, did you remove the driver at some point over the past few days?

If it's nv, what happens when you drop to tty1?

xorg.conf now has nvidia. when I went to the windows terminal when it was set to nv, it worked fine meaning I could see the command prompt and type in stuff.

nvidia was not removed over the past few days. With xorg.conf set to nvidia, i can now get into the nvidia settings, but still 800X600 is the highest it will go as I mentioned earlier.

---

### Post by patchwork on 2010-03-07
You don't need to keep checking the nvidia-settings...when it is working properly the x server chooses the "best" mode (i.e. you'll see the difference)

You added the HorizSync line to your xorg?

Double check the following ```
lsmod | grep nvidia
```
You should see the nvidia module as being loaded.

Also, let's take another look at your Xorg.0.log for conflicts.

---

### Post by legend_018 on 2010-03-07
> **patchwork said:**
> You don't need to keep checking the nvidia-settings...when it is working properly the x server chooses the "best" mode (i.e. you'll see the difference)

You added the HorizSync line to your xorg?

Double check the following ```
lsmod | grep nvidia
```You should see the nvidia module as being loaded.

Also, let's take another look at your Xorg.0.log for conflicts.

no sorry I have not added the Horizsync line yet. I was running all my commands by going to the Terminal and now for some reason I go into the terminal and it's a big white screen with no prompt. now if I want to change anything, I'll have to hit control alt F1 and do it that way. I was comfortable using gedit and so now I'll have to figure out the best way to edit the files out at the control/alt/F1 area.

---

### Post by patchwork on 2010-03-07
sudo nano /etc/X11/xorg.conf

---

### Post by AgentZ86 on 2010-03-07
Hi

I'm sorry this is giving you trouble mostly things just work right out of the box for nvidia stuff mostly

Anyhow, I have this AGP card and had similar issue

Only thing I would recommend is re-install, then when installing the proprietary driver, or try this without re-installing too.

If the settings you want are not available then you have attempt to use the System/Preferences/Display

Make sure your doing this logged in as Admin user too

And a message will poppup saying that your graphix driver does not support the necessary extention to use this tool

Just hit No and use it anyway for now, just to change some settings.

See if you can make resolution settings here, and then they should be available with the nvidia interface also.

Thats what I had to do because the setting for my monitor were not available. This is something to do with the lack of detection of the monitor and not the vid card I believe.

You may notice when you use the display tool that your monitor is not listed or listed as unknown

Anyhow just try setting to 1024x768 for now and use HZ = 60,70,or maybe 75, but sometimes it might not give you an option and only lets you use like HZ = 56,57 or something, just leave it alone then and set your resolution

Once you apply changes it should make changes and should be available with the nvidia tool now too.

Anyhow I'm using 9.10 64 bit and 9.10 32 bit on different machines same senerio on each one.

I hope this helps and sorry it's giving you trouble.

---

### Post by legend_018 on 2010-03-07
> **patchwork said:**
> You don't need to keep checking the nvidia-settings...when it is working properly the x server chooses the "best" mode (i.e. you'll see the difference)

You added the HorizSync line to your xorg?

Double check the following ```
lsmod | grep nvidia
```You should see the nvidia module as being loaded.

Also, let's take another look at your Xorg.0.log for conflicts.

ok HorizSync is in my xorg now.
I typed in the lsmod code and it shows nvidia from what I can see.

Here is the xorg.0.log file
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux chayse-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=840cb1fb-2002-4018-ad17-38921d21ed7f ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar  7 09:06:11 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0181:10de:01b6 nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] rev 162, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  96.43.13  Thu Jun 25 18:56:56 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  96.43.13  Thu Jun 25 18:45:26 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "false"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on CRT-0.
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 440 with AGP8X at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.18.20.21.15
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 440 with AGP8X at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1024x768_60.00"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "PreferredMode" is not used
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.

---

### Post by legend_018 on 2010-03-07
> **legend_018 said:**
> no sorry I have not added the Horizsync line yet. I was running all my commands by going to the Terminal and now for some reason I go into the terminal and it's a big white screen with no prompt. now if I want to change anything, I'll have to hit control alt F1 and do it that way. I was comfortable using gedit and so now I'll have to figure out the best way to edit the files out at the control/alt/F1 area.


ok after adding the Horizsync line, things seem to work now. I'm double checking YEAH!!!!! finally, oh my goodness. Terrible for someone to have to go through this. Oh well, I'm not touching anything else at this point. especially since its working

---

### Post by legend_018 on 2010-03-07
after all that though, something caused the terminal to stop working (big blank white screen). at least I can go to control/alt/f1 and do stuff if need to though.

---

### Post by patchwork on 2010-03-07
Glad to see the resolution problem is fixed...I know it seemed like an awful process, but it isn't too bad after you do it once or twice....



Not sure what would cause the terminal to tweak like that...

Try ```
sudo dpkg --reconfigure gnome-terminal
```

---

### Post by legend_018 on 2010-03-07
> **patchwork said:**
> Glad to see the resolution problem is fixed...I know it seemed like an awful process, but it isn't too bad after you do it once or twice....



Not sure what would cause the terminal to tweak like that...

Try ```
sudo dpkg --reconfigure gnome-terminal
```

ill give it a try. thanks so much!!!!!! everyone for helping!!!!! Yipppie!!!!!

---

### Post by blackened on 2010-03-07
Glad you got it sorted out. I was heading you in the direction of adding monitor refresh and sync to xorg when you disappeared last night. All roads apparently *do* lead to Rome though eh?

---

### Post by dsdurkes on 2010-05-05
I, too have the problem of a standard 800x600 display. I had previously used Ubuntu with a much higher resolution but for some reason it has reset when I loaded 10.X today.

lspci | grep VGA
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)

I guess I don't have /etc/X11/xorg-conf as it shows up blank.

I am a relative newbie, which is why I am having trouble making this a new post.

Would appreciate the help. Trying to get this old box running with Ubuntu to migrate away from Win. Other option is Mac and I feel more comfortable with Linux, in general. (Old System V guy here).

Thanks much. gpt sny help, suggestions, etc. The monitor I am trying to drive is a 19" Fuji Plus LCD. Pretty bad with just 800x600 rez, though.

---

### Post by AgentZ86 on 2010-05-06
Hi

After reading through this post again I don't think your having a problem with the Nvidia

The problem is that the software keeps recognizing your display as a CRT monitor.

I can see this in your code you posted.

Ubuntu 9.10 should install and work perfect on your system however, to make sure you can get the resolution you want it would be best to plugin another monitor just to confirm that all this diagnosing is needed.

I know the Nvidia 440MX work well on linux and should be no problem.

So since your monitor says unknown then I suggest turning off the monitor then on again and rebooting and it may fix itself.

Or you might plugin and regular crt or some old monitor if you have laying around just to get the resolutions added, or at least to see if it's related to the monitor or the software/pc combo

At least to narrow things down,

But for sure I can see in the code that it's detecting CRT so that seems like it's related to the problem that it's not detected properly and thus the card is not auto configuring properly which then ubuntu doesn't know what to do so defaults to the lowest most probably fail safe features.

Anyhow I believe this is monitor related not pc/video related.
I don't know if this helps, but seems like you should be changing the monitor ID's that appear in all that code you posted.

I wish I knew how or which ID's to use for you but I don't know enough about, however I can see the CRT detected topic in your code for just about all the NV related stuff.

---

### Post by hatebreed on 2010-05-08
I had some problems with my geforce 3 just like what your going through. Heres how I fixed it. First go to your hardware drivers in system-administration-hardware drivers and enable your new driver then
Open up a root terminal and type nvidia-xconfig -mode "1024x768" "800x600" and whatever other resolutions you want to have available. Then reboot. this forces the nvidia driver to look at those resoulutions. p.s. you don't have to hit cntl-f1 to do this. Post back with results.

edit-didn't see it was solved, I don't know the config file for the intel driver but i'm sure if you know the config you could do the same thing with intel as I did with the nvidia driver.

---

### Post by hatebreed on 2010-05-08
Just found this link through google maybe give it a try.
[http://www.linwik.com/wiki/configuring+the+intel+graphics+media+accelerator+900-950+for+linux](http://www.linwik.com/wiki/configuring+the+intel+graphics+media+accelerator+900-950+for+linux)

---

