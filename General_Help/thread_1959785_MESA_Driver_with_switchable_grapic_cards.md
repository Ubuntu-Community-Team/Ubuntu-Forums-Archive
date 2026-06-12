---
title: "MESA Driver with switchable grapic cards"
date: 2012-04-16
forum: General Help
---

### Post by apochry on 2012-04-16
Hello,
I have the following problem/question and will be very happy, if someone can help to clear this up.
[B]
Short sys info:[/B]
Dell Vostro Laptop
Ubuntu 11.10 32bit with Unity3D
AMD Radeon 6630M
Switchable integrated Intel graphics

**And my problem:**
I've spent several nights trying to get rid off the horizontal video tearing, that often comes with  FGLRX drivers, without any success. This made me switch back from AMD's proprietary FGLRX driver to the open source Mesa.
Since my laptop has switchable graphics I am now wondering if the AMD card is being used at all.

Here is what I get when I type "xvinfo" in the terminal:

```
$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Textured Video"
    number of ports: 16
    port base: 77
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
    number of attributes: 3
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is -1)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 127)
      "XV_SYNC_TO_VBLANK" (range -1 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 5
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x434d5658 (XVMC)
        guid: 58564d43-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)

```and "glxinfo | grep OpenGL"
```
~$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:

```Nowhere an AMD/ATI card is mentioned. Does it mean that I'm running the system only on the integrated Intel card?

And thoughts will be appreciated!


Thanks,
Christo

---

### Post by 2F4U on 2012-04-16
From the information you provide it looks as if the Intel card is used. What does /var/log/Xorg.0.log say? It would tell you if the ATI card is considered and also if there are errors.

---

### Post by 2F4U on 2012-04-16
Just in case you didn't notice, there is a thread dedicated on how to get ATI/Intel hybrid graphics to work:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by apochry on 2012-04-16
> **2F4U said:**
> Just in case you didn't notice, there is a thread dedicated on how to get ATI/Intel hybrid graphics to work:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

I didn't.
Thank you very much!

[EDIT]
Wow, I've just taken a look on this thread! This is exactly my hardware! Sounds great, I'll just wait another 9 days till the 12.04 and give it a try!

Thanks a lot one more time!

---

### Post by apochry on 2012-04-16
> **2F4U said:**
> From the information you provide it looks as if the Intel card is used. What does /var/log/Xorg.0.log say? It would tell you if the ATI card is considered and also if there are errors.

Here is what it says:
```

[    18.938] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    18.938] X Protocol Version 11, Revision 0
[    18.938] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    18.938] Current Operating System: Linux StupiDELL 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
[    18.938] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=4e0f2c9d-39fe-4093-9c8f-bb6d2574df69 ro quiet splash vt.handoff=7
[    18.938] Build Date: 19 October 2011  05:09:41AM
[    18.938] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.938] Current version of pixman: 0.22.2
[    18.938]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    18.938] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.938] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 17 00:54:46 2012
[    19.008] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.231] (==) No Layout section.  Using the first Screen section.
[    19.231] (==) No screen section available. Using defaults.
[    19.231] (**) |-->Screen "Default Screen Section" (0)
[    19.231] (**) |   |-->Monitor "<default monitor>"
[    19.232] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    19.232] (==) Automatically adding devices
[    19.232] (==) Automatically enabling devices
[    19.244] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.244]     Entry deleted from font path.
[    19.244] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.244]     Entry deleted from font path.
[    19.244] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.244]     Entry deleted from font path.
[    19.268] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.268]     Entry deleted from font path.
[    19.268] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.268]     Entry deleted from font path.
[    19.342] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    19.342] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.342] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.342] (II) Loader magic: 0x823ada0
[    19.342] (II) Module ABI versions:
[    19.342]     X.Org ANSI C Emulation: 0.4
[    19.342]     X.Org Video Driver: 10.0
[    19.342]     X.Org XInput driver : 12.3
[    19.342]     X.Org Server Extension : 5.0
[    19.342] (--) PCI:*(0:0:2:0) 8086:0126:1028:04c5 rev 9, Mem @ 0xe0000000/4194304, 0xd0000000/268435456, I/O @ 0x00005000/64
[    19.342] (--) PCI: (0:1:0:0) 1002:6741:1028:04c5 rev 0, Mem @ 0xc0000000/268435456, 0xe1700000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    19.343] (II) Open ACPI successful (/var/run/acpid.socket)
[    19.343] (II) LoadModule: "extmod"
[    19.487] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.495] (II) Module extmod: vendor="X.Org Foundation"
[    19.495]     compiled for 1.10.4, module version = 1.0.0
[    19.495]     Module class: X.Org Server Extension
[    19.495]     ABI class: X.Org Server Extension, version 5.0
[    19.495] (II) Loading extension MIT-SCREEN-SAVER
[    19.496] (II) Loading extension XFree86-VidModeExtension
[    19.496] (II) Loading extension XFree86-DGA
[    19.496] (II) Loading extension DPMS
[    19.497] (II) Loading extension XVideo
[    19.497] (II) Loading extension XVideo-MotionCompensation
[    19.497] (II) Loading extension X-Resource
[    19.497] (II) LoadModule: "dbe"
[    19.497] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.574] (II) Module dbe: vendor="X.Org Foundation"
[    19.574]     compiled for 1.10.4, module version = 1.0.0
[    19.574]     Module class: X.Org Server Extension
[    19.574]     ABI class: X.Org Server Extension, version 5.0
[    19.574] (II) Loading extension DOUBLE-BUFFER
[    19.574] (II) LoadModule: "glx"
[    19.575] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.592] (II) Module glx: vendor="X.Org Foundation"
[    19.592]     compiled for 1.10.4, module version = 1.0.0
[    19.592]     ABI class: X.Org Server Extension, version 5.0
[    19.592] (==) AIGLX enabled
[    19.592] (II) Loading extension GLX
[    19.592] (II) LoadModule: "record"
[    19.592] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.593] (II) Module record: vendor="X.Org Foundation"
[    19.593]     compiled for 1.10.4, module version = 1.13.0
[    19.593]     Module class: X.Org Server Extension
[    19.593]     ABI class: X.Org Server Extension, version 5.0
[    19.593] (II) Loading extension RECORD
[    19.593] (II) LoadModule: "dri"
[    19.593] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.604] (II) Module dri: vendor="X.Org Foundation"
[    19.604]     compiled for 1.10.4, module version = 1.0.0
[    19.604]     ABI class: X.Org Server Extension, version 5.0
[    19.604] (II) Loading extension XFree86-DRI
[    19.604] (II) LoadModule: "dri2"
[    19.604] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.606] (II) Module dri2: vendor="X.Org Foundation"
[    19.606]     compiled for 1.10.4, module version = 1.2.0
[    19.606]     ABI class: X.Org Server Extension, version 5.0
[    19.606] (II) Loading extension DRI2
[    19.606] (==) Matched intel as autoconfigured driver 0
[    19.606] (==) Matched vesa as autoconfigured driver 1
[    19.606] (==) Matched fbdev as autoconfigured driver 2
[    19.606] (==) Assigned the driver to the xf86ConfigLayout
[    19.606] (II) LoadModule: "intel"
[    19.606] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.620] (II) Module intel: vendor="X.Org Foundation"
[    19.620]     compiled for 1.10.4, module version = 2.15.901
[    19.620]     Module class: X.Org Video Driver
[    19.620]     ABI class: X.Org Video Driver, version 10.0
[    19.620] (II) LoadModule: "vesa"
[    19.620] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.625] (II) Module vesa: vendor="X.Org Foundation"
[    19.625]     compiled for 1.10.2, module version = 2.3.0
[    19.625]     Module class: X.Org Video Driver
[    19.625]     ABI class: X.Org Video Driver, version 10.0
[    19.625] (II) LoadModule: "fbdev"
[    19.625] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.633] (II) Module fbdev: vendor="X.Org Foundation"
[    19.633]     compiled for 1.10.0, module version = 0.4.2
[    19.633]     ABI class: X.Org Video Driver, version 10.0
[    19.633] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    19.633] (II) VESA: driver for VESA chipsets: vesa
[    19.634] (II) FBDEV: driver for framebuffer: fbdev
[    19.634] (++) using VT number 7

[    19.635] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.635] (WW) Falling back to old probe method for vesa
[    19.635] (WW) Falling back to old probe method for fbdev
[    19.635] (II) Loading sub module "fbdevhw"
[    19.635] (II) LoadModule: "fbdevhw"
[    19.635] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.638] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.638]     compiled for 1.10.4, module version = 0.0.2
[    19.638]     ABI class: X.Org Video Driver, version 10.0
[    19.638] drmOpenDevice: node name is /dev/dri/card0
[    19.638] drmOpenDevice: open result is 9, (OK)
[    19.638] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    19.639] drmOpenDevice: node name is /dev/dri/card0
[    19.639] drmOpenDevice: open result is 9, (OK)
[    19.639] drmOpenByBusid: drmOpenMinor returns 9
[    19.639] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    19.639] drmOpenDevice: node name is /dev/dri/card1
[    19.639] drmOpenDevice: open result is 9, (OK)
[    19.639] drmOpenByBusid: drmOpenMinor returns 9
[    19.639] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    19.639] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    19.639] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    19.639] (==) intel(0): RGB weight 888
[    19.639] (==) intel(0): Default visual is TrueColor
[    19.639] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2+)
[    19.639] (--) intel(0): Chipset: "Sandybridge Mobile (GT2+)"
[    19.639] (**) intel(0): Relaxed fencing enabled
[    19.639] (**) intel(0): Wait on SwapBuffers? enabled
[    19.639] (**) intel(0): Triple buffering? enabled
[    19.639] (**) intel(0): Framebuffer tiled
[    19.639] (**) intel(0): Pixmaps tiled
[    19.639] (**) intel(0): 3D buffers tiled
[    19.639] (**) intel(0): SwapBuffers wait enabled
[    19.639] (==) intel(0): video overlay key set to 0x101fe
[    19.639] (II) intel(0): Output LVDS1 has no monitor section
[    19.639] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    19.639] (II) intel(0): Output VGA1 has no monitor section
[    19.662] (II) intel(0): Output HDMI1 has no monitor section
[    19.708] (II) intel(0): Output DP1 has no monitor section
[    19.708] (II) intel(0): EDID for output LVDS1
[    19.708] (II) intel(0): Manufacturer: AUO  Model: 193c  Serial#: 0
[    19.708] (II) intel(0): Year: 2009  Week: 0
[    19.708] (II) intel(0): EDID Version: 1.4
[    19.708] (II) intel(0): Digital Display Input
[    19.708] (II) intel(0): 6 bits per channel
[    19.708] (II) intel(0): Digital interface is undefined
[    19.708] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[    19.708] (II) intel(0): Gamma: 2.20
[    19.708] (II) intel(0): No DPMS capabilities specified
[    19.708] (II) intel(0): Supported color encodings: RGB 4:4:4 
[    19.708] (II) intel(0): First detailed timing is preferred mode
[    19.708] (II) intel(0): Preferred mode is native pixel format and refresh rate
[    19.708] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[    19.708] (II) intel(0): blueX: 0.150 blueY: 0.600   whiteX: 0.313 whiteY: 0.329
[    19.708] (II) intel(0): Manufacturer's mask: 0
[    19.708] (II) intel(0): Supported detailed timing:
[    19.708] (II) intel(0): clock: 71.0 MHz   Image Size:  309 x 173 mm
[    19.708] (II) intel(0): h_active: 1366  h_sync: 1404  h_sync_end 1426 h_blank_end 1472 h_border: 0
[    19.708] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    19.708] (II) intel(0): Supported detailed timing:
[    19.708] (II) intel(0): clock: 71.0 MHz   Image Size:  309 x 173 mm
[    19.708] (II) intel(0): h_active: 1366  h_sync: 1404  h_sync_end 1426 h_blank_end 1760 h_border: 0
[    19.708] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 1008 v_border: 0
[    19.708] (II) intel(0):  GJ475\80B140XW1
[    19.708] (II) intel(0): Unknown vendor-specific block 0
[    19.708] (II) intel(0): EDID (in hex):
[    19.708] (II) intel(0):     00ffffffffffff0006af3c1900000000
[    19.708] (II) intel(0):     00130104901f117802c8a59e57549226
[    19.708] (II) intel(0):     99505400000001010101010101010101
[    19.708] (II) intel(0):     010101010101bc1b566a500023302616
[    19.708] (II) intel(0):     360035ad1000001abc1b568a5100f030
[    19.708] (II) intel(0):     2616360035ad1000001a000000fe0047
[    19.708] (II) intel(0):     4a343735804231343058573100000000
[    19.708] (II) intel(0):     00004122940101000001010a202000e6
[    19.708] (II) intel(0): EDID vendor "AUO", prod id 6460
[    19.708] (II) intel(0): Printing DDC gathered Modelines:
[    19.708] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1472  768 771 777 803 +hsync -vsync (48.2 kHz)
[    19.708] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1760  768 771 777 1008 +hsync -vsync (40.3 kHz)
[    19.708] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    19.708] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    19.708] (II) intel(0): Printing probed modes for output LVDS1
[    19.708] (II) intel(0): Modeline "1366x768"x60.1   71.00  1366 1404 1426 1472  768 771 777 803 +hsync -vsync (48.2 kHz)
[    19.708] (II) intel(0): Modeline "1366x768"x40.0   71.00  1366 1404 1426 1760  768 771 777 1008 +hsync -vsync (40.3 kHz)
[    19.708] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    19.708] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    19.708] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.708] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.708] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.708] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.708] (II) intel(0): EDID for output VGA1
[    19.732] (II) intel(0): EDID for output HDMI1
[    19.780] (II) intel(0): EDID for output DP1
[    19.780] (II) intel(0): Output LVDS1 connected
[    19.780] (II) intel(0): Output VGA1 disconnected
[    19.780] (II) intel(0): Output HDMI1 disconnected
[    19.780] (II) intel(0): Output DP1 disconnected
[    19.780] (II) intel(0): Using exact sizes for initial modes
[    19.780] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    19.780] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    19.780] (II) intel(0): Kernel page flipping support detected, enabling
[    19.780] (**) intel(0): Display dimensions: (310, 170) mm
[    19.780] (**) intel(0): DPI set to (111, 114)
[    19.780] (II) Loading sub module "fb"
[    19.780] (II) LoadModule: "fb"
[    19.780] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.803] (II) Module fb: vendor="X.Org Foundation"
[    19.803]     compiled for 1.10.4, module version = 1.0.0
[    19.803]     ABI class: X.Org ANSI C Emulation, version 0.4
[    19.803] (II) Loading sub module "dri2"
[    19.803] (II) LoadModule: "dri2"
[    19.803] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.803] (II) Module dri2: vendor="X.Org Foundation"
[    19.803]     compiled for 1.10.4, module version = 1.2.0
[    19.803]     ABI class: X.Org Server Extension, version 5.0
[    19.803] (II) UnloadModule: "vesa"
[    19.803] (II) Unloading vesa
[    19.803] (II) UnloadModule: "fbdev"
[    19.803] (II) Unloading fbdev
[    19.803] (II) UnloadModule: "fbdevhw"
[    19.803] (II) Unloading fbdevhw
[    19.803] (==) Depth 24 pixmap format is 32 bpp
[    19.803] (II) intel(0): [DRI2] Setup complete
[    19.803] (II) intel(0): [DRI2]   DRI driver: i965
[    19.803] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    19.812] (II) UXA(0): Driver registered support for the following operations:
[    19.812] (II)         solid
[    19.812] (II)         copy
[    19.812] (II)         composite (RENDER acceleration)
[    19.812] (II)         put_image
[    19.812] (II)         get_image
[    19.812] (==) intel(0): Backing store disabled
[    19.812] (==) intel(0): Silken mouse enabled
[    19.812] (II) intel(0): Initializing HW Cursor
[    19.872] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.872] (==) intel(0): DPMS enabled
[    19.872] (==) intel(0): Intel XvMC decoder enabled
[    19.872] (II) intel(0): Set up textured video
[    19.872] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    19.872] (II) intel(0): direct rendering: DRI2 Enabled
[    19.872] (==) intel(0): hotplug detection: "enabled"
[    19.872] (--) RandR disabled
[    19.872] (II) Initializing built-in extension Generic Event Extension
[    19.872] (II) Initializing built-in extension SHAPE
[    19.872] (II) Initializing built-in extension MIT-SHM
[    19.872] (II) Initializing built-in extension XInputExtension
[    19.872] (II) Initializing built-in extension XTEST
[    19.872] (II) Initializing built-in extension BIG-REQUESTS
[    19.872] (II) Initializing built-in extension SYNC
[    19.872] (II) Initializing built-in extension XKEYBOARD
[    19.872] (II) Initializing built-in extension XC-MISC
[    19.872] (II) Initializing built-in extension SECURITY
[    19.872] (II) Initializing built-in extension XINERAMA
[    19.872] (II) Initializing built-in extension XFIXES
[    19.872] (II) Initializing built-in extension RENDER
[    19.872] (II) Initializing built-in extension RANDR
[    19.872] (II) Initializing built-in extension COMPOSITE
[    19.872] (II) Initializing built-in extension DAMAGE
[    19.872] (II) Initializing built-in extension GESTURE
[    19.923] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[    20.033] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    20.033] (II) AIGLX: enabled GLX_INTEL_swap_event
[    20.033] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    20.033] (II) AIGLX: enabled GLX_SGI_make_current_read
[    20.033] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    20.033] (II) AIGLX: Loaded and initialized i965
[    20.033] (II) GLX: Initialized DRI2 GL provider for screen 0
[    20.033] (II) intel(0): Setting screen physical size to 361 x 203
[    20.155] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.173] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    20.173] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.173] (II) LoadModule: "evdev"
[    20.174] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.313] (II) Module evdev: vendor="X.Org Foundation"
[    20.313]     compiled for 1.10.2, module version = 2.6.0
[    20.313]     Module class: X.Org XInput Driver
[    20.313]     ABI class: X.Org XInput driver, version 12.3
[    20.313] (II) Using input driver 'evdev' for 'Power Button'
[    20.313] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.313] (**) Power Button: always reports core events
[    20.313] (**) Power Button: Device: "/dev/input/event3"
[    20.313] (--) Power Button: Found keys
[    20.313] (II) Power Button: Configuring as keyboard
[    20.313] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    20.313] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.313] (**) Option "xkb_rules" "evdev"
[    20.313] (**) Option "xkb_model" "pc105"
[    20.313] (**) Option "xkb_layout" "de"
[    20.315] (II) XKB: reuse xkmfile /var/lib/xkb/server-808BBA3D4C227BDB44C370226C34E44C5D69A4A9.xkm
[    20.416] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    20.416] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.416] (II) Using input driver 'evdev' for 'Video Bus'
[    20.416] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.416] (**) Video Bus: always reports core events
[    20.416] (**) Video Bus: Device: "/dev/input/event11"
[    20.416] (--) Video Bus: Found keys
[    20.416] (II) Video Bus: Configuring as keyboard
[    20.416] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input11/event11"
[    20.416] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    20.416] (**) Option "xkb_rules" "evdev"
[    20.416] (**) Option "xkb_model" "pc105"
[    20.416] (**) Option "xkb_layout" "de"
[    20.418] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    20.418] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.418] (II) Using input driver 'evdev' for 'Video Bus'
[    20.418] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.418] (**) Video Bus: always reports core events
[    20.418] (**) Video Bus: Device: "/dev/input/event10"
[    20.418] (--) Video Bus: Found keys
[    20.418] (II) Video Bus: Configuring as keyboard
[    20.418] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27/LNXVIDEO:00/input/input10/event10"
[    20.418] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    20.418] (**) Option "xkb_rules" "evdev"
[    20.418] (**) Option "xkb_model" "pc105"
[    20.418] (**) Option "xkb_layout" "de"
[    20.426] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.426] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.426] (II) Using input driver 'evdev' for 'Power Button'
[    20.426] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.426] (**) Power Button: always reports core events
[    20.426] (**) Power Button: Device: "/dev/input/event0"
[    20.426] (--) Power Button: Found keys
[    20.426] (II) Power Button: Configuring as keyboard
[    20.426] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    20.426] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.426] (**) Option "xkb_rules" "evdev"
[    20.426] (**) Option "xkb_model" "pc105"
[    20.426] (**) Option "xkb_layout" "de"
[    20.426] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    20.426] (II) No input driver/identifier specified (ignoring)
[    20.426] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    20.426] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    20.426] (II) Using input driver 'evdev' for 'Sleep Button'
[    20.426] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.426] (**) Sleep Button: always reports core events
[    20.426] (**) Sleep Button: Device: "/dev/input/event1"
[    20.427] (--) Sleep Button: Found keys
[    20.427] (II) Sleep Button: Configuring as keyboard
[    20.427] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    20.427] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    20.427] (**) Option "xkb_rules" "evdev"
[    20.427] (**) Option "xkb_model" "pc105"
[    20.427] (**) Option "xkb_layout" "de"
[    20.429] (II) config/udev: Adding input device Laptop_Integrated_Webcam_FHD (/dev/input/event9)
[    20.429] (**) Laptop_Integrated_Webcam_FHD: Applying InputClass "evdev keyboard catchall"
[    20.429] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_FHD'
[    20.429] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.429] (**) Laptop_Integrated_Webcam_FHD: always reports core events
[    20.429] (**) Laptop_Integrated_Webcam_FHD: Device: "/dev/input/event9"
[    20.429] (--) Laptop_Integrated_Webcam_FHD: Found keys
[    20.429] (II) Laptop_Integrated_Webcam_FHD: Configuring as keyboard
[    20.429] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input9/event9"
[    20.429] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_FHD" (type: KEYBOARD)
[    20.429] (**) Option "xkb_rules" "evdev"
[    20.429] (**) Option "xkb_model" "pc105"
[    20.429] (**) Option "xkb_layout" "de"
[    20.430] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    20.430] (II) No input driver/identifier specified (ignoring)
[    20.430] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event13)
[    20.430] (II) No input driver/identifier specified (ignoring)
[    20.430] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event14)
[    20.430] (II) No input driver/identifier specified (ignoring)
[    20.432] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    20.432] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    20.432] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    20.432] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.432] (**) Logitech USB Receiver: always reports core events
[    20.432] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    20.432] (--) Logitech USB Receiver: Found 20 mouse buttons
[    20.432] (--) Logitech USB Receiver: Found scroll wheel(s)
[    20.432] (--) Logitech USB Receiver: Found relative axes
[    20.432] (--) Logitech USB Receiver: Found x and y relative axes
[    20.432] (II) Logitech USB Receiver: Configuring as mouse
[    20.432] (II) Logitech USB Receiver: Adding scrollwheel support
[    20.432] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    20.432] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.432] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/usb3/3-2/3-2:1.0/input/input5/event5"
[    20.432] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
[    20.432] (II) Logitech USB Receiver: initialized for relative axes.
[    20.432] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    20.432] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    20.432] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    20.432] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    20.432] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    20.432] (II) No input driver/identifier specified (ignoring)
[    20.432] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    20.432] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    20.432] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    20.432] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.433] (**) Logitech USB Receiver: always reports core events
[    20.433] (**) Logitech USB Receiver: Device: "/dev/input/event6"
[    20.433] (--) Logitech USB Receiver: Found 1 mouse buttons
[    20.433] (--) Logitech USB Receiver: Found scroll wheel(s)
[    20.433] (--) Logitech USB Receiver: Found relative axes
[    20.433] (--) Logitech USB Receiver: Found absolute axes
[    20.433] (II) evdev-grail: failed to open grail, no gesture support
[    20.433] (--) Logitech USB Receiver: Found keys
[    20.433] (II) Logitech USB Receiver: Configuring as mouse
[    20.433] (II) Logitech USB Receiver: Configuring as keyboard
[    20.433] (II) Logitech USB Receiver: Adding scrollwheel support
[    20.433] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    20.433] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    20.433] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/usb3/3-2/3-2:1.1/input/input6/event6"
[    20.433] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    20.433] (**) Option "xkb_rules" "evdev"
[    20.433] (**) Option "xkb_model" "pc105"
[    20.433] (**) Option "xkb_layout" "de"
[    20.433] (EE) Logitech USB Receiver: failed to initialize for relative axes.
[    20.433] (II) Logitech USB Receiver: initialized for absolute axes.
[    20.433] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    20.433] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    20.433] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    20.433] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    20.437] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    20.437] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.437] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.437] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.437] (**) AT Translated Set 2 keyboard: always reports core events
[    20.437] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    20.437] (--) AT Translated Set 2 keyboard: Found keys
[    20.437] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    20.437] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    20.437] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    20.437] (**) Option "xkb_rules" "evdev"
[    20.437] (**) Option "xkb_model" "pc105"
[    20.437] (**) Option "xkb_layout" "de"
[    20.437] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    20.437] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    20.437] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    20.437] (II) LoadModule: "synaptics"
[    20.438] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.440] (II) Module synaptics: vendor="X.Org Foundation"
[    20.440]     compiled for 1.10.4, module version = 1.4.1
[    20.440]     Module class: X.Org XInput Driver
[    20.440]     ABI class: X.Org XInput driver, version 12.3
[    20.440] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    20.440] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    20.440] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    20.440] (**) Option "Device" "/dev/input/event8"
[    20.572] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5798
[    20.572] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4992
[    20.572] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    20.572] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    20.572] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    20.700] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    20.700] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    20.828] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    20.828] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    20.828] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    20.828] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    20.828] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.036
[    20.828] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    20.828] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    20.828] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    20.828] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    20.828] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    20.828] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    20.828] (II) No input driver/identifier specified (ignoring)
[    20.832] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[    20.832] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    20.832] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    20.832] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.832] (**) Dell WMI hotkeys: always reports core events
[    20.832] (**) Dell WMI hotkeys: Device: "/dev/input/event7"
[    20.832] (--) Dell WMI hotkeys: Found keys
[    20.832] (II) Dell WMI hotkeys: Configuring as keyboard
[    20.832] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    20.832] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    20.832] (**) Option "xkb_rules" "evdev"
[    20.832] (**) Option "xkb_model" "pc105"
[    20.832] (**) Option "xkb_layout" "de"
[    28.071] (II) intel(0): EDID vendor "AUO", prod id 6460
[    28.071] (II) intel(0): Printing DDC gathered Modelines:
[    28.071] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1472  768 771 777 803 +hsync -vsync (48.2 kHz)
[    28.071] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1760  768 771 777 1008 +hsync -vsync (40.3 kHz)
[    30.527] (II) intel(0): EDID vendor "AUO", prod id 6460
[    30.527] (II) intel(0): Printing DDC gathered Modelines:
[    30.527] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1472  768 771 777 803 +hsync -vsync (48.2 kHz)
[    30.527] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1760  768 771 777 1008 +hsync -vsync (40.3 kHz)
[    35.553] (II) intel(0): EDID vendor "AUO", prod id 6460
[    35.553] (II) intel(0): Printing DDC gathered Modelines:
[    35.553] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1472  768 771 777 803 +hsync -vsync (48.2 kHz)
[    35.553] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1760  768 771 777 1008 +hsync -vsync (40.3 kHz)
[    40.656] (II) intel(0): EDID vendor "AUO", prod id 6460
[    40.656] (II) intel(0): Printing DDC gathered Modelines:
[    40.656] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1472  768 771 777 803 +hsync -vsync (48.2 kHz)
[    40.656] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1760  768 771 777 1008 +hsync -vsync (40.3 kHz)
[    42.273] (II) XKB: reuse xkmfile /var/lib/xkb/server-35A53ED645D9304B183DE587930A3EECCCBB0D45.xkm

```
As much as I understand (and it's not a lot) the AMD card is not used at all, right?

Do you know what do these
```

[    19.708] (II) intel(0): Printing DDC gathered Modelines:
[    19.708] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1472  768 771 777 803 +hsync -vsync (48.2 kHz)
[    19.708] (II) intel(0): Modeline "1366x768"x0.0   71.00  1366 1404 1426 1760  768 771 777 1008 +hsync -vsync (40.3 kHz)

```
and these
```
[    19.708] (II) intel(0): Printing probed modes for output LVDS1
[    19.708] (II) intel(0): Modeline "1366x768"x60.1   71.00  1366 1404 1426 1472  768 771 777 803 +hsync -vsync (48.2 kHz)
[    19.708] (II) intel(0): Modeline "1366x768"x40.0   71.00  1366 1404 1426 1760  768 771 777 1008 +hsync -vsync (40.3 kHz)
[    19.708] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    19.708] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    19.708] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.708] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.708] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.708] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
```
lines mean?

I'm asking because I have horizontal tear problems with the proprietary driver and some people imply in various threads that it is usually related to the VSync and Refresh Rate.

Thanks a lot!
Christo

---

