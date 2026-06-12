---
title: "Incorrect resolution set despite correct EDID info"
date: 2010-06-23
forum: General Help
---

### Post by Praetor77 on 2010-06-23
Greetings,
My problem began recently when after connecting an external VGA monitor, my laptop monitor somehow changed it´s normal 1024x600 resolution to a 1024x768 resolution, and shrinks vertical pixels to fit it all on the screen (no panning).
I am on Lucid, 2.6.32-23 on an Asus 1005HA with integrated intel 945GM  graphics. I am using updated KMS-enabled xserver-xorg-video-intel  drivers (2.9.1-3ubuntu5)

I sincerely do not understand how or why this happened, but I know it has something to do with the intel driver, since creating a xorg.conf file (do not use one normally) and setting the driver to fbdev corrects the problem (although with lousy performance).

To my astonishment, Xorg correctly detects monitor modes as 1024x600, 800x600, and 640x480 as evidenced on the Xorg log below. For some reason, splash screen and X start fine, with correct full-screen 1024x600 resolution, but then the display is visibly shrinked/scaled (leaving a black bar below, which is then "filled" with screen) resulting in a full-screen 1024x768 resolution.

My xrandr output is:

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+   65.0  
   800x600        60.3  
   640x480        59.9  

```As you can see, for some reason the screen is using 1024x768 resolution, although it is not even in the listed supported modes below! Everything is correctly detected from EDID, including screen size (220x129mm). The only abnormal change I can see as compared to before is the ("LVDS1 connected 1024x768+0+0") which should be 1024x600+0+0.

If I try changing resolution to 1024x600 using xrandr (or the UBUNTU display settings), I get an unused black bar on the bottom of the screen, about 150pixels high. xrandr output after xrandr -s 1024x600:

```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+   65.0  
   800x600        60.3  
   640x480        59.9  
```When trying to set DPI to the value it should have (118DPI, though any dpi value used causes the exact same thing), the setting appears to not take effect (any DPI value used results in no image change), and the entire screen is used, but resolution goes back to 1024x768. xrandr output after xrandr --dpi 118:

```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+   65.0  
   800x600        60.3  
   640x480        59.9  
```I would REALLY appreciate some help with this bizarre issue. Googled and searched bug reports for days without finding an answer. Have tried all kinds of things on my xorg.conf. Have tried installing latest xserver-xorg-video-intel (2.11.0). Have tried removing xserver-xorg-video-intel with --purge and reinstalling. Nothing works. I have also tried booting using 2.6.31 kernel with no results. Lastly, also tried dpkg-reconfigure xserver-xorg-video-intel with no results.

Here is my Xorg.0.log:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux rodrigo-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic root=UUID=75a7c909-751f-4712-bb7a-32096e7997bc ro crashkernel=384M-2G:64M,2G-:128M i915.modeset=1 quiet splash acpi_osi=Linux
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun 23 11:17:17 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:0:2:0) 8086:27ae:1043:8340 Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf7e00000/524288, 0xd0000000/268435456, 0xf7dc0000/262144, I/O @ 0x0000dc00/8
(--) PCI: (0:0:2:1) 8086:27a6:1043:8340 Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf7e80000/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GME
(--) intel(0): Chipset: "945GME"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: HSD  Model: 3e9  Serial#: 322038
(II) intel(0): Year: 2009  Week: 21
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 22  vert.: 13
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.317 greenY: 0.564
(II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.310 whiteY: 0.330
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 45.0 MHz   Image Size:  220 x 129 mm
(II) intel(0): h_active: 1024  h_sync: 1077  h_sync_end 1112 h_blank_end 1200 h_border: 0
(II) intel(0): v_active: 600  v_sync: 604  v_sync_end 609 v_blanking: 625 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 51.4 MHz   Image Size:  220 x 129 mm
(II) intel(0): h_active: 1024  h_sync: 1117  h_sync_end 1152 h_blank_end 1240 h_border: 0
(II) intel(0): v_active: 600  v_sync: 617  v_sync_end 622 v_blanking: 638 v_border: 0
(II) intel(0):  
(II) intel(0):  
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff002264e903f6e90400
(II) intel(0):     1513010380160d780a86269457519027
(II) intel(0):     214f5400000001010101010101010101
(II) intel(0):     010101010101941100b0405819203523
(II) intel(0):     4500dc8100000019161400d840582620
(II) intel(0):     5d231504dc8100000000000000fe0000
(II) intel(0):     000000000000000000000000000000fe
(II) intel(0):     000000000000000000010000000000e1
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1024x600"x60.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x65.0   51.42  1024 1117 1152 1240  600 601 606 638 -hsync -vsync (41.5 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1024x600
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
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
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 158
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) XKB: reuse xkmfile /var/lib/xkb/server-EEE76AC18E53EDE3D19E026307AE3E38C6676B05.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event7)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event8)
(**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
(**) USB 2.0 Camera: always reports core events
(**) USB 2.0 Camera: Device: "/dev/input/event8"
(II) USB 2.0 Camera: Found keys
(II) USB 2.0 Camera: Configuring as keyboard
(II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device Asus EeePC extra buttons (/dev/input/event6)
(**) Asus EeePC extra buttons: Applying InputClass "evdev keyboard catchall"
(**) Asus EeePC extra buttons: always reports core events
(**) Asus EeePC extra buttons: Device: "/dev/input/event6"
(II) Asus EeePC extra buttons: Found keys
(II) Asus EeePC extra buttons: Configuring as keyboard
(II) XINPUT: Adding extended input device "Asus EeePC extra buttons" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "latam"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event10"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): Allocate new frame buffer 1024x768 stride 1024
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
(II) intel(0): EDID vendor "HSD", prod id 1001
(II) intel(0): DDCModeFromDetailedTiming: 1024x600 Warning: We only handle separate sync.
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   45.00  1024 1077 1112 1200  600 604 609 625 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "1024x600"x0.0   51.42  1024 1117 1152 1240  600 617 622 638 -hsync -vsync (41.5 kHz)
```

---

### Post by Praetor77 on 2010-06-23
xrandr --output LVDS1 --scale 1x1
Solved the problem! :)

---

