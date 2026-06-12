---
title: "Ubuntu 11.10 gnome fallback"
date: 2011-10-13
forum: General Help
---

### Post by melvinsim on 2011-10-13
hi guys,

i need some help regarding gnome.

i am able to log into ubuntu using unity without falling back to unity 2d.

however, when i choose to log in with gnome 3, i end up falling back to classic gnome.

I prefer using gnome 3 so is there any way that i can use gnome 3 instead of falling back. 

i am quite new to ubuntu so i would appreciated step by step help.

Thanks!

---

### Post by harlequin_ on 2011-10-13
I am having the same problem. I upgraded to 11.10 and after the reboot everything was fine. Then I opened compiz-configuration-settings (which were not enlisted in the system settings for some reason) and when I browsed to one of the configuration panels in it, the computer sort of frooze and I had to reboot. After the reboot now I see that I have no Unity whatsoever, only the old GNOME top panel (like in 10.04) but for instance I cannot launch a terminal from there.

Any solutions? 

ps: When I login with Unity 2D after the reboot it strangly opens normal Unity.

---

### Post by crdlb on 2011-10-13
> **melvinsim said:**
> however, when i choose to log in with gnome 3, i end up falling back to classic gnome.

I prefer using gnome 3 so is there any way that i can use gnome 3 instead of falling back.

Is gnome-shell installed? If so, do you get a message saying that gnome-shell failed to start?

---

### Post by melvinsim on 2011-10-13
> **crdlb said:**
> Is gnome-shell installed? If so, do you get a message saying that gnome-shell failed to start?


I have gnome shell installed and terminal says that I have the latest version when I update it.

And i didn't get any msg telling my that gnome shell failed to start. It automatically goes into fallback mode

---

### Post by crdlb on 2011-10-13
OK, what happens if you run```
gnome-shell --replace
``` in a terminal from the fallback session? Does it print an error?

---

### Post by melvinsim on 2011-10-14
> **crdlb said:**
> OK, what happens if you run```
gnome-shell --replace
``` in a terminal from the fallback session? Does it print an error?

Hi,

i did as told and got the following errors.

Xlib:  extension "GLX" missing on display ":0.0".

(gnome-shell:2046): Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined
Window manager error: Unable to initialize Clutter.

Next step?

Thanks!

---

### Post by crdlb on 2011-10-14
> **melvinsim said:**
> Hi,

i did as told and got the following errors.

Xlib:  extension "GLX" missing on display ":0.0".

(gnome-shell:2046): Clutter-CRITICAL **: Unable to initialize Clutter: The OpenGL version could not be determined
Window manager error: Unable to initialize Clutter.


Attach your /var/log/Xorg.0.log

---

### Post by melvinsim on 2011-10-14
> **crdlb said:**
> Attach your /var/log/Xorg.0.log

Hi, this is my /var/log/Xorg.0.log.

```

[   278.144] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   278.144] X Protocol Version 11, Revision 0
[   278.144] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   278.144] Current Operating System: Linux Melvin-Laptop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[   278.144] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=3474738e-23a7-4138-b769-d0456994168c ro quiet splash vt.handoff=7
[   278.144] Build Date: 29 September 2011  02:45:13AM
[   278.144] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   278.144] Current version of pixman: 0.22.2
[   278.144]     Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
[   278.144] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   278.144] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 14 18:23:29 2011
[   278.144] (==) Using config file: "/etc/X11/xorg.conf"
[   278.144] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   278.145] (==) No Layout section.  Using the first Screen section.
[   278.145] (==) No screen section available. Using defaults.
[   278.145] (**) |-->Screen "Default Screen Section" (0)
[   278.145] (**) |   |-->Monitor "<default monitor>"
[   278.145] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[   278.145] (**) |   |-->Device "Default Device"
[   278.145] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   278.145] (==) Automatically adding devices
[   278.145] (==) Automatically enabling devices
[   278.145] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   278.145]     Entry deleted from font path.
[   278.145] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   278.145]     Entry deleted from font path.
[   278.145] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   278.145]     Entry deleted from font path.
[   278.145] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   278.145]     Entry deleted from font path.
[   278.145] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   278.145]     Entry deleted from font path.
[   278.145] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   278.145] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   278.145] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   278.145] (II) Loader magic: 0x7e0220
[   278.145] (II) Module ABI versions:
[   278.145]     X.Org ANSI C Emulation: 0.4
[   278.145]     X.Org Video Driver: 10.0
[   278.145]     X.Org XInput driver : 12.3
[   278.145]     X.Org Server Extension : 5.0
[   278.146] (--) PCI:*(0:0:2:0) 8086:0046:1043:12d2 rev 24, Mem @ 0xd3400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e080/8
[   278.146] (--) PCI: (0:1:0:0) 10de:0a70:1043:12d2 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[   278.146] (II) Open ACPI successful (/var/run/acpid.socket)
[   278.146] (II) LoadModule: "extmod"
[   278.147] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   278.147] (II) Module extmod: vendor="X.Org Foundation"
[   278.147]     compiled for 1.10.4, module version = 1.0.0
[   278.147]     Module class: X.Org Server Extension
[   278.147]     ABI class: X.Org Server Extension, version 5.0
[   278.147] (II) Loading extension MIT-SCREEN-SAVER
[   278.147] (II) Loading extension XFree86-VidModeExtension
[   278.147] (II) Loading extension XFree86-DGA
[   278.147] (II) Loading extension DPMS
[   278.147] (II) Loading extension XVideo
[   278.147] (II) Loading extension XVideo-MotionCompensation
[   278.147] (II) Loading extension X-Resource
[   278.147] (II) LoadModule: "dbe"
[   278.148] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   278.148] (II) Module dbe: vendor="X.Org Foundation"
[   278.148]     compiled for 1.10.4, module version = 1.0.0
[   278.148]     Module class: X.Org Server Extension
[   278.148]     ABI class: X.Org Server Extension, version 5.0
[   278.148] (II) Loading extension DOUBLE-BUFFER
[   278.148] (II) LoadModule: "glx"
[   278.148] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   278.159] (II) Module glx: vendor="NVIDIA Corporation"
[   278.159]     compiled for 4.0.2, module version = 1.0.0
[   278.159]     Module class: X.Org Server Extension
[   278.159] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[   278.159] (II) Loading extension GLX
[   278.159] (II) LoadModule: "record"
[   278.159] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   278.159] (II) Module record: vendor="X.Org Foundation"
[   278.159]     compiled for 1.10.4, module version = 1.13.0
[   278.159]     Module class: X.Org Server Extension
[   278.160]     ABI class: X.Org Server Extension, version 5.0
[   278.160] (II) Loading extension RECORD
[   278.160] (II) LoadModule: "dri"
[   278.160] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   278.160] (II) Module dri: vendor="X.Org Foundation"
[   278.160]     compiled for 1.10.4, module version = 1.0.0
[   278.160]     ABI class: X.Org Server Extension, version 5.0
[   278.160] (II) Loading extension XFree86-DRI
[   278.160] (II) LoadModule: "dri2"
[   278.160] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   278.160] (II) Module dri2: vendor="X.Org Foundation"
[   278.160]     compiled for 1.10.4, module version = 1.2.0
[   278.160]     ABI class: X.Org Server Extension, version 5.0
[   278.160] (II) Loading extension DRI2
[   278.160] (==) Matched intel as autoconfigured driver 0
[   278.160] (==) Matched vesa as autoconfigured driver 1
[   278.160] (==) Matched fbdev as autoconfigured driver 2
[   278.160] (==) Assigned the driver to the xf86ConfigLayout
[   278.160] (II) LoadModule: "intel"
[   278.160] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   278.160] (II) Module intel: vendor="X.Org Foundation"
[   278.160]     compiled for 1.10.2.902, module version = 2.15.901
[   278.160]     Module class: X.Org Video Driver
[   278.160]     ABI class: X.Org Video Driver, version 10.0
[   278.160] (II) LoadModule: "vesa"
[   278.161] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   278.161] (II) Module vesa: vendor="X.Org Foundation"
[   278.161]     compiled for 1.10.2, module version = 2.3.0
[   278.161]     Module class: X.Org Video Driver
[   278.161]     ABI class: X.Org Video Driver, version 10.0
[   278.161] (II) LoadModule: "fbdev"
[   278.161] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   278.161] (II) Module fbdev: vendor="X.Org Foundation"
[   278.161]     compiled for 1.10.0, module version = 0.4.2
[   278.161]     ABI class: X.Org Video Driver, version 10.0
[   278.161] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   278.161] (II) VESA: driver for VESA chipsets: vesa
[   278.161] (II) FBDEV: driver for framebuffer: fbdev
[   278.161] (++) using VT number 7

[   278.163] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   278.163] (WW) Falling back to old probe method for vesa
[   278.163] (WW) Falling back to old probe method for fbdev
[   278.163] (II) Loading sub module "fbdevhw"
[   278.163] (II) LoadModule: "fbdevhw"
[   278.163] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   278.163] (II) Module fbdevhw: vendor="X.Org Foundation"
[   278.163]     compiled for 1.10.4, module version = 0.0.2
[   278.163]     ABI class: X.Org Video Driver, version 10.0
[   278.164] drmOpenDevice: node name is /dev/dri/card0
[   278.164] drmOpenDevice: open result is 12, (OK)
[   278.164] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   278.164] drmOpenDevice: node name is /dev/dri/card0
[   278.164] drmOpenDevice: open result is 12, (OK)
[   278.164] drmOpenByBusid: drmOpenMinor returns 12
[   278.164] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   278.164] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   278.164] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   278.164] (==) intel(0): RGB weight 888
[   278.164] (==) intel(0): Default visual is TrueColor
[   278.164] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[   278.164] (--) intel(0): Chipset: "Arrandale"
[   278.164] (**) intel(0): Relaxed fencing enabled
[   278.164] (**) intel(0): Wait on SwapBuffers? enabled
[   278.164] (**) intel(0): Triple buffering? enabled
[   278.164] (**) intel(0): Framebuffer tiled
[   278.164] (**) intel(0): Pixmaps tiled
[   278.164] (**) intel(0): 3D buffers tiled
[   278.164] (**) intel(0): SwapBuffers wait enabled
[   278.164] (==) intel(0): video overlay key set to 0x101fe
[   278.164] (II) intel(0): Output LVDS1 has no monitor section
[   278.164] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[   278.164] (II) intel(0): Output VGA1 has no monitor section
[   278.187] (II) intel(0): Output HDMI1 has no monitor section
[   278.236] (II) intel(0): Output DP1 has no monitor section
[   278.236] (II) intel(0): EDID for output LVDS1
[   278.236] (II) intel(0): Manufacturer: AUO  Model: 213c  Serial#: 0
[   278.236] (II) intel(0): Year: 2008  Week: 1
[   278.236] (II) intel(0): EDID Version: 1.3
[   278.236] (II) intel(0): Digital Display Input
[   278.236] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[   278.236] (II) intel(0): Gamma: 2.20
[   278.236] (II) intel(0): No DPMS capabilities specified
[   278.236] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   278.236] (II) intel(0): First detailed timing is preferred mode
[   278.236] (II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.330 greenY: 0.575
[   278.236] (II) intel(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[   278.236] (II) intel(0): Manufacturer's mask: 0
[   278.236] (II) intel(0): Supported detailed timing:
[   278.236] (II) intel(0): clock: 72.0 MHz   Image Size:  309 x 174 mm
[   278.236] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1494 h_border: 0
[   278.236] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[   278.236] (II) intel(0): Unknown vendor-specific block f
[   278.236] (II) intel(0):  AUO
[   278.236] (II) intel(0):  B140XW02 V1
[   278.236] (II) intel(0): EDID (in hex):
[   278.236] (II) intel(0):     00ffffffffffff0006af3c2100000000
[   278.236] (II) intel(0):     01120103801f11780a09e59757549327
[   278.236] (II) intel(0):     22505400000001010101010101010101
[   278.236] (II) intel(0):     010101010101201c5680500023303020
[   278.236] (II) intel(0):     360035ae100000180000000f00000000
[   278.236] (II) intel(0):     00000000000000000020000000fe0041
[   278.236] (II) intel(0):     554f0a202020202020202020000000fe
[   278.236] (II) intel(0):     004231343058573032205631200a00b2
[   278.236] (II) intel(0): EDID vendor "AUO", prod id 8508
[   278.236] (II) intel(0): Printing DDC gathered Modelines:
[   278.236] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   278.236] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   278.236] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   278.236] (II) intel(0): Printing probed modes for output LVDS1
[   278.236] (II) intel(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   278.236] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[   278.236] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[   278.236] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   278.236] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   278.237] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   278.237] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   278.237] (II) intel(0): EDID for output VGA1
[   278.259] (II) intel(0): EDID for output HDMI1
[   278.308] (II) intel(0): EDID for output DP1
[   278.308] (II) intel(0): Output LVDS1 connected
[   278.308] (II) intel(0): Output VGA1 disconnected
[   278.308] (II) intel(0): Output HDMI1 disconnected
[   278.308] (II) intel(0): Output DP1 disconnected
[   278.308] (II) intel(0): Using exact sizes for initial modes
[   278.308] (II) intel(0): Output LVDS1 using initial mode 1366x768
[   278.308] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   278.308] (II) intel(0): Kernel page flipping support detected, enabling
[   278.308] (**) intel(0): Display dimensions: (310, 170) mm
[   278.308] (**) intel(0): DPI set to (111, 114)
[   278.308] (II) Loading sub module "fb"
[   278.308] (II) LoadModule: "fb"
[   278.308] (II) Loading /usr/lib/xorg/modules/libfb.so
[   278.308] (II) Module fb: vendor="X.Org Foundation"
[   278.308]     compiled for 1.10.4, module version = 1.0.0
[   278.308]     ABI class: X.Org ANSI C Emulation, version 0.4
[   278.308] (II) Loading sub module "dri2"
[   278.308] (II) LoadModule: "dri2"
[   278.308] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   278.308] (II) Module dri2: vendor="X.Org Foundation"
[   278.308]     compiled for 1.10.4, module version = 1.2.0
[   278.308]     ABI class: X.Org Server Extension, version 5.0
[   278.308] (II) UnloadModule: "vesa"
[   278.308] (II) Unloading vesa
[   278.308] (II) UnloadModule: "fbdev"
[   278.308] (II) Unloading fbdev
[   278.308] (II) UnloadModule: "fbdevhw"
[   278.308] (II) Unloading fbdevhw
[   278.308] (==) Depth 24 pixmap format is 32 bpp
[   278.309] (II) intel(0): [DRI2] Setup complete
[   278.309] (II) intel(0): [DRI2]   DRI driver: i965
[   278.309] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[   278.319] (II) UXA(0): Driver registered support for the following operations:
[   278.319] (II)         solid
[   278.319] (II)         copy
[   278.319] (II)         composite (RENDER acceleration)
[   278.319] (II)         put_image
[   278.319] (II)         get_image
[   278.319] (==) intel(0): Backing store disabled
[   278.319] (==) intel(0): Silken mouse enabled
[   278.319] (II) intel(0): Initializing HW Cursor
[   278.388] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   278.389] (==) intel(0): DPMS enabled
[   278.389] (==) intel(0): Intel XvMC decoder enabled
[   278.389] (II) intel(0): Set up textured video
[   278.389] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   278.389] (II) intel(0): direct rendering: DRI2 Enabled
[   278.389] (WW) intel(0): Option "NoLogo" is not used
[   278.389] (==) intel(0): hotplug detection: "enabled"
[   278.390] (--) RandR disabled
[   278.390] (II) Initializing built-in extension Generic Event Extension
[   278.390] (II) Initializing built-in extension SHAPE
[   278.390] (II) Initializing built-in extension MIT-SHM
[   278.390] (II) Initializing built-in extension XInputExtension
[   278.390] (II) Initializing built-in extension XTEST
[   278.390] (II) Initializing built-in extension BIG-REQUESTS
[   278.390] (II) Initializing built-in extension SYNC
[   278.390] (II) Initializing built-in extension XKEYBOARD
[   278.390] (II) Initializing built-in extension XC-MISC
[   278.390] (II) Initializing built-in extension SECURITY
[   278.390] (II) Initializing built-in extension XINERAMA
[   278.390] (II) Initializing built-in extension XFIXES
[   278.390] (II) Initializing built-in extension RENDER
[   278.390] (II) Initializing built-in extension RANDR
[   278.390] (II) Initializing built-in extension COMPOSITE
[   278.390] (II) Initializing built-in extension DAMAGE
[   278.390] (II) Initializing built-in extension GESTURE
[   278.393] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[   278.397] (II) intel(0): Setting screen physical size to 361 x 203
[   278.403] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   278.409] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   278.409] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   278.409] (II) LoadModule: "evdev"
[   278.409] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.410] (II) Module evdev: vendor="X.Org Foundation"
[   278.410]     compiled for 1.10.2, module version = 2.6.0
[   278.410]     Module class: X.Org XInput Driver
[   278.410]     ABI class: X.Org XInput driver, version 12.3
[   278.410] (II) Using input driver 'evdev' for 'Power Button'
[   278.410] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.410] (**) Power Button: always reports core events
[   278.410] (**) Power Button: Device: "/dev/input/event2"
[   278.410] (--) Power Button: Found keys
[   278.410] (II) Power Button: Configuring as keyboard
[   278.410] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   278.410] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   278.410] (**) Option "xkb_rules" "evdev"
[   278.410] (**) Option "xkb_model" "pc105"
[   278.410] (**) Option "xkb_layout" "us"
[   278.411] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[   278.411] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   278.411] (II) Using input driver 'evdev' for 'Video Bus'
[   278.411] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.411] (**) Video Bus: always reports core events
[   278.411] (**) Video Bus: Device: "/dev/input/event8"
[   278.411] (--) Video Bus: Found keys
[   278.411] (II) Video Bus: Configuring as keyboard
[   278.411] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input8/event8"
[   278.411] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   278.411] (**) Option "xkb_rules" "evdev"
[   278.411] (**) Option "xkb_model" "pc105"
[   278.411] (**) Option "xkb_layout" "us"
[   278.412] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[   278.412] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   278.412] (II) Using input driver 'evdev' for 'Video Bus'
[   278.412] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.412] (**) Video Bus: always reports core events
[   278.412] (**) Video Bus: Device: "/dev/input/event7"
[   278.412] (--) Video Bus: Found keys
[   278.412] (II) Video Bus: Configuring as keyboard
[   278.412] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7/event7"
[   278.412] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[   278.412] (**) Option "xkb_rules" "evdev"
[   278.412] (**) Option "xkb_model" "pc105"
[   278.412] (**) Option "xkb_layout" "us"
[   278.414] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   278.414] (II) No input driver/identifier specified (ignoring)
[   278.414] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   278.414] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   278.415] (II) Using input driver 'evdev' for 'Sleep Button'
[   278.415] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.415] (**) Sleep Button: always reports core events
[   278.415] (**) Sleep Button: Device: "/dev/input/event1"
[   278.415] (--) Sleep Button: Found keys
[   278.415] (II) Sleep Button: Configuring as keyboard
[   278.415] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   278.415] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   278.415] (**) Option "xkb_rules" "evdev"
[   278.415] (**) Option "xkb_model" "pc105"
[   278.415] (**) Option "xkb_layout" "us"
[   278.416] (II) config/udev: Adding input device USB 2.0 UVC 0.3M Webcam (/dev/input/event6)
[   278.416] (**) USB 2.0 UVC 0.3M Webcam: Applying InputClass "evdev keyboard catchall"
[   278.416] (II) Using input driver 'evdev' for 'USB 2.0 UVC 0.3M Webcam'
[   278.416] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.416] (**) USB 2.0 UVC 0.3M Webcam: always reports core events
[   278.416] (**) USB 2.0 UVC 0.3M Webcam: Device: "/dev/input/event6"
[   278.416] (--) USB 2.0 UVC 0.3M Webcam: Found keys
[   278.416] (II) USB 2.0 UVC 0.3M Webcam: Configuring as keyboard
[   278.416] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6/event6"
[   278.416] (II) XINPUT: Adding extended input device "USB 2.0 UVC 0.3M Webcam" (type: KEYBOARD)
[   278.417] (**) Option "xkb_rules" "evdev"
[   278.417] (**) Option "xkb_model" "pc105"
[   278.417] (**) Option "xkb_layout" "us"
[   278.417] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[   278.417] (II) No input driver/identifier specified (ignoring)
[   278.418] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event11)
[   278.418] (II) No input driver/identifier specified (ignoring)
[   278.418] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event9)
[   278.418] (II) No input driver/identifier specified (ignoring)
[   278.419] (II) config/udev: Adding input device MLK PROLiNK Wireless Laser Mouse (/dev/input/event4)
[   278.419] (**) MLK PROLiNK Wireless Laser Mouse: Applying InputClass "evdev pointer catchall"
[   278.419] (**) MLK PROLiNK Wireless Laser Mouse: Applying InputClass "evdev keyboard catchall"
[   278.419] (II) Using input driver 'evdev' for 'MLK PROLiNK Wireless Laser Mouse'
[   278.419] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.419] (**) MLK PROLiNK Wireless Laser Mouse: always reports core events
[   278.419] (**) MLK PROLiNK Wireless Laser Mouse: Device: "/dev/input/event4"
[   278.419] (--) MLK PROLiNK Wireless Laser Mouse: Found 9 mouse buttons
[   278.419] (--) MLK PROLiNK Wireless Laser Mouse: Found scroll wheel(s)
[   278.419] (--) MLK PROLiNK Wireless Laser Mouse: Found relative axes
[   278.419] (--) MLK PROLiNK Wireless Laser Mouse: Found x and y relative axes
[   278.419] (--) MLK PROLiNK Wireless Laser Mouse: Found absolute axes
[   278.419] (II) evdev-grail: failed to open grail, no gesture support
[   278.419] (--) MLK PROLiNK Wireless Laser Mouse: Found keys
[   278.419] (II) MLK PROLiNK Wireless Laser Mouse: Configuring as mouse
[   278.419] (II) MLK PROLiNK Wireless Laser Mouse: Configuring as keyboard
[   278.419] (II) MLK PROLiNK Wireless Laser Mouse: Adding scrollwheel support
[   278.419] (**) MLK PROLiNK Wireless Laser Mouse: YAxisMapping: buttons 4 and 5
[   278.419] (**) MLK PROLiNK Wireless Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   278.419] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4/event4"
[   278.419] (II) XINPUT: Adding extended input device "MLK PROLiNK Wireless Laser Mouse" (type: KEYBOARD)
[   278.419] (**) Option "xkb_rules" "evdev"
[   278.419] (**) Option "xkb_model" "pc105"
[   278.419] (**) Option "xkb_layout" "us"
[   278.420] (II) MLK PROLiNK Wireless Laser Mouse: initialized for relative axes.
[   278.420] (WW) MLK PROLiNK Wireless Laser Mouse: ignoring absolute axes.
[   278.420] (**) MLK PROLiNK Wireless Laser Mouse: (accel) keeping acceleration scheme 1
[   278.420] (**) MLK PROLiNK Wireless Laser Mouse: (accel) acceleration profile 0
[   278.420] (**) MLK PROLiNK Wireless Laser Mouse: (accel) acceleration factor: 2.000
[   278.420] (**) MLK PROLiNK Wireless Laser Mouse: (accel) acceleration threshold: 4
[   278.420] (II) config/udev: Adding input device MLK PROLiNK Wireless Laser Mouse (/dev/input/mouse0)
[   278.420] (II) No input driver/identifier specified (ignoring)
[   278.422] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event5)
[   278.422] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[   278.422] (II) Using input driver 'evdev' for 'Asus Laptop extra buttons'
[   278.422] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.422] (**) Asus Laptop extra buttons: always reports core events
[   278.422] (**) Asus Laptop extra buttons: Device: "/dev/input/event5"
[   278.422] (--) Asus Laptop extra buttons: Found keys
[   278.422] (II) Asus Laptop extra buttons: Configuring as keyboard
[   278.422] (**) Option "config_info" "udev:/sys/devices/platform/asus_laptop/input/input5/event5"
[   278.422] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
[   278.422] (**) Option "xkb_rules" "evdev"
[   278.422] (**) Option "xkb_model" "pc105"
[   278.422] (**) Option "xkb_layout" "us"
[   278.423] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   278.423] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   278.423] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   278.423] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   278.423] (**) AT Translated Set 2 keyboard: always reports core events
[   278.423] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   278.423] (--) AT Translated Set 2 keyboard: Found keys
[   278.423] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   278.423] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   278.423] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   278.423] (**) Option "xkb_rules" "evdev"
[   278.423] (**) Option "xkb_model" "pc105"
[   278.423] (**) Option "xkb_layout" "us"
[   278.423] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event12)
[   278.423] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[   278.423] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[   278.423] (II) LoadModule: "synaptics"
[   278.423] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   278.424] (II) Module synaptics: vendor="X.Org Foundation"
[   278.424]     compiled for 1.10.4, module version = 1.4.1
[   278.424]     Module class: X.Org XInput Driver
[   278.424]     ABI class: X.Org XInput driver, version 12.3
[   278.424] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[   278.424] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   278.424] (**) ETPS/2 Elantech Touchpad: always reports core events
[   278.424] (**) Option "Device" "/dev/input/event12"
[   278.424] (--) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[   278.424] (--) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[   278.424] (--) ETPS/2 Elantech Touchpad: pressure range 0 - 255
[   278.424] (--) ETPS/2 Elantech Touchpad: finger width range 0 - 15
[   278.424] (--) ETPS/2 Elantech Touchpad: buttons: left right double triple
[   278.428] (--) ETPS/2 Elantech Touchpad: touchpad found
[   278.428] (**) ETPS/2 Elantech Touchpad: always reports core events
[   278.428] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input12/event12"
[   278.428] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[   278.428] (**) ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[   278.428] (**) ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[   278.428] (**) ETPS/2 Elantech Touchpad: AccelFactor is now 0.147
[   278.428] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[   278.428] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[   278.428] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[   278.428] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[   278.428] (--) ETPS/2 Elantech Touchpad: touchpad found
[   278.429] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[   278.429] (II) No input driver/identifier specified (ignoring)
[   278.716] (II) intel(0): EDID vendor "AUO", prod id 8508
[   278.716] (II) intel(0): Printing DDC gathered Modelines:
[   278.716] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   278.819] (II) intel(0): EDID vendor "AUO", prod id 8508
[   278.819] (II) intel(0): Printing DDC gathered Modelines:
[   278.819] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   278.916] (II) intel(0): EDID vendor "AUO", prod id 8508
[   278.916] (II) intel(0): Printing DDC gathered Modelines:
[   278.916] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   284.242] (II) intel(0): EDID vendor "AUO", prod id 8508
[   284.242] (II) intel(0): Printing DDC gathered Modelines:
[   284.242] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   284.504] (II) intel(0): EDID vendor "AUO", prod id 8508
[   284.504] (II) intel(0): Printing DDC gathered Modelines:
[   284.504] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   284.583] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   284.630] (II) intel(0): EDID vendor "AUO", prod id 8508
[   284.630] (II) intel(0): Printing DDC gathered Modelines:
[   284.630] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   284.874] (II) intel(0): EDID vendor "AUO", prod id 8508
[   284.874] (II) intel(0): Printing DDC gathered Modelines:
[   284.874] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   284.944] (II) intel(0): EDID vendor "AUO", prod id 8508
[   284.944] (II) intel(0): Printing DDC gathered Modelines:
[   284.944] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.026] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.026] (II) intel(0): Printing DDC gathered Modelines:
[   285.026] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.124] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.124] (II) intel(0): Printing DDC gathered Modelines:
[   285.124] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.240] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.240] (II) intel(0): Printing DDC gathered Modelines:
[   285.240] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.312] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.312] (II) intel(0): Printing DDC gathered Modelines:
[   285.312] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.430] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.430] (II) intel(0): Printing DDC gathered Modelines:
[   285.430] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.504] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.504] (II) intel(0): Printing DDC gathered Modelines:
[   285.504] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.588] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.588] (II) intel(0): Printing DDC gathered Modelines:
[   285.588] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.677] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.677] (II) intel(0): Printing DDC gathered Modelines:
[   285.677] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.764] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.764] (II) intel(0): Printing DDC gathered Modelines:
[   285.764] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.850] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.850] (II) intel(0): Printing DDC gathered Modelines:
[   285.850] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   285.921] (II) intel(0): EDID vendor "AUO", prod id 8508
[   285.921] (II) intel(0): Printing DDC gathered Modelines:
[   285.921] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.003] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.003] (II) intel(0): Printing DDC gathered Modelines:
[   286.003] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.085] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.085] (II) intel(0): Printing DDC gathered Modelines:
[   286.085] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.168] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.168] (II) intel(0): Printing DDC gathered Modelines:
[   286.168] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.258] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.258] (II) intel(0): Printing DDC gathered Modelines:
[   286.258] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.390] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.390] (II) intel(0): Printing DDC gathered Modelines:
[   286.390] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.484] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.485] (II) intel(0): Printing DDC gathered Modelines:
[   286.485] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.569] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.569] (II) intel(0): Printing DDC gathered Modelines:
[   286.569] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.662] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.662] (II) intel(0): Printing DDC gathered Modelines:
[   286.662] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.748] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.748] (II) intel(0): Printing DDC gathered Modelines:
[   286.748] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.841] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.846] (II) intel(0): Printing DDC gathered Modelines:
[   286.846] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   286.924] (II) intel(0): EDID vendor "AUO", prod id 8508
[   286.924] (II) intel(0): Printing DDC gathered Modelines:
[   286.924] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   289.999] (II) intel(0): EDID vendor "AUO", prod id 8508
[   289.999] (II) intel(0): Printing DDC gathered Modelines:
[   289.999] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
```

---

### Post by crdlb on 2011-10-14
> [ 278.393] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

You appear to have the proprietary nvidia driver installed which is conflicting with the intel driver. ```
sudo apt-get remove nvidia-current
``` should fix it.

---

### Post by melvinsim on 2011-10-14
> **crdlb said:**
> You appear to have the proprietary nvidia driver installed which is conflicting with the intel driver. ```
sudo apt-get remove nvidia-current
``` should fix it.

I did sudo apt-get remove nvidia-current and restarted my com. However, it is still in gnome fallback mode.

this is my log after removing nvidia..
```


[    14.275] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    14.275] X Protocol Version 11, Revision 0
[    14.275] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.275] Current Operating System: Linux Melvin-Laptop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    14.276] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=3474738e-23a7-4138-b769-d0456994168c ro quiet splash vt.handoff=7
[    14.276] Build Date: 29 September 2011  02:45:13AM
[    14.276] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    14.276] Current version of pixman: 0.22.2
[    14.276]     Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
[    14.276] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.276] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 15 00:48:27 2011
[    14.276] (==) Using config file: "/etc/X11/xorg.conf"
[    14.276] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.276] (==) No Layout section.  Using the first Screen section.
[    14.276] (==) No screen section available. Using defaults.
[    14.276] (**) |-->Screen "Default Screen Section" (0)
[    14.276] (**) |   |-->Monitor "<default monitor>"
[    14.276] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    14.276] (**) |   |-->Device "Default Device"
[    14.276] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.276] (==) Automatically adding devices
[    14.276] (==) Automatically enabling devices
[    14.276] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.276]     Entry deleted from font path.
[    14.276] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.276]     Entry deleted from font path.
[    14.276] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.276]     Entry deleted from font path.
[    14.277] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.277]     Entry deleted from font path.
[    14.277] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.277]     Entry deleted from font path.
[    14.277] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.277] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.277] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.277] (II) Loader magic: 0x7e0220
[    14.277] (II) Module ABI versions:
[    14.277]     X.Org ANSI C Emulation: 0.4
[    14.277]     X.Org Video Driver: 10.0
[    14.277]     X.Org XInput driver : 12.3
[    14.277]     X.Org Server Extension : 5.0
[    14.279] (--) PCI:*(0:0:2:0) 8086:0046:1043:12d2 rev 24, Mem @ 0xd3400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e080/8
[    14.279] (--) PCI: (0:1:0:0) 10de:0a70:1043:12d2 rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[    14.279] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.279] (II) LoadModule: "extmod"
[    14.279] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.279] (II) Module extmod: vendor="X.Org Foundation"
[    14.279]     compiled for 1.10.4, module version = 1.0.0
[    14.279]     Module class: X.Org Server Extension
[    14.279]     ABI class: X.Org Server Extension, version 5.0
[    14.279] (II) Loading extension MIT-SCREEN-SAVER
[    14.279] (II) Loading extension XFree86-VidModeExtension
[    14.279] (II) Loading extension XFree86-DGA
[    14.279] (II) Loading extension DPMS
[    14.279] (II) Loading extension XVideo
[    14.279] (II) Loading extension XVideo-MotionCompensation
[    14.279] (II) Loading extension X-Resource
[    14.279] (II) LoadModule: "dbe"
[    14.279] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.279] (II) Module dbe: vendor="X.Org Foundation"
[    14.279]     compiled for 1.10.4, module version = 1.0.0
[    14.279]     Module class: X.Org Server Extension
[    14.279]     ABI class: X.Org Server Extension, version 5.0
[    14.280] (II) Loading extension DOUBLE-BUFFER
[    14.280] (II) LoadModule: "glx"
[    14.280] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    15.353] (II) Module glx: vendor="NVIDIA Corporation"
[    15.371]     compiled for 4.0.2, module version = 1.0.0
[    15.371]     Module class: X.Org Server Extension
[    15.371] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[    15.371] (II) Loading extension GLX
[    15.371] (II) LoadModule: "record"
[    15.372] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.372] (II) Module record: vendor="X.Org Foundation"
[    15.372]     compiled for 1.10.4, module version = 1.13.0
[    15.372]     Module class: X.Org Server Extension
[    15.372]     ABI class: X.Org Server Extension, version 5.0
[    15.372] (II) Loading extension RECORD
[    15.372] (II) LoadModule: "dri"
[    15.372] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.372] (II) Module dri: vendor="X.Org Foundation"
[    15.372]     compiled for 1.10.4, module version = 1.0.0
[    15.372]     ABI class: X.Org Server Extension, version 5.0
[    15.372] (II) Loading extension XFree86-DRI
[    15.372] (II) LoadModule: "dri2"
[    15.373] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.373] (II) Module dri2: vendor="X.Org Foundation"
[    15.373]     compiled for 1.10.4, module version = 1.2.0
[    15.373]     ABI class: X.Org Server Extension, version 5.0
[    15.373] (II) Loading extension DRI2
[    15.373] (==) Matched intel as autoconfigured driver 0
[    15.373] (==) Matched vesa as autoconfigured driver 1
[    15.373] (==) Matched fbdev as autoconfigured driver 2
[    15.373] (==) Assigned the driver to the xf86ConfigLayout
[    15.373] (II) LoadModule: "intel"
[    15.518] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.518] (II) Module intel: vendor="X.Org Foundation"
[    15.518]     compiled for 1.10.2.902, module version = 2.15.901
[    15.518]     Module class: X.Org Video Driver
[    15.518]     ABI class: X.Org Video Driver, version 10.0
[    15.518] (II) LoadModule: "vesa"
[    15.518] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.518] (II) Module vesa: vendor="X.Org Foundation"
[    15.518]     compiled for 1.10.2, module version = 2.3.0
[    15.518]     Module class: X.Org Video Driver
[    15.518]     ABI class: X.Org Video Driver, version 10.0
[    15.518] (II) LoadModule: "fbdev"
[    15.518] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.518] (II) Module fbdev: vendor="X.Org Foundation"
[    15.518]     compiled for 1.10.0, module version = 0.4.2
[    15.518]     ABI class: X.Org Video Driver, version 10.0
[    15.518] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    15.519] (II) VESA: driver for VESA chipsets: vesa
[    15.519] (II) FBDEV: driver for framebuffer: fbdev
[    15.519] (++) using VT number 7

[    15.521] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.521] (WW) Falling back to old probe method for vesa
[    15.521] (WW) Falling back to old probe method for fbdev
[    15.521] (II) Loading sub module "fbdevhw"
[    15.521] (II) LoadModule: "fbdevhw"
[    15.521] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.521] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.521]     compiled for 1.10.4, module version = 0.0.2
[    15.521]     ABI class: X.Org Video Driver, version 10.0
[    15.521] drmOpenDevice: node name is /dev/dri/card0
[    15.521] drmOpenDevice: open result is 12, (OK)
[    15.521] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    15.521] drmOpenDevice: node name is /dev/dri/card0
[    15.521] drmOpenDevice: open result is 12, (OK)
[    15.521] drmOpenByBusid: drmOpenMinor returns 12
[    15.521] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    15.521] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    15.521] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    15.521] (==) intel(0): RGB weight 888
[    15.521] (==) intel(0): Default visual is TrueColor
[    15.521] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    15.521] (--) intel(0): Chipset: "Arrandale"
[    15.521] (**) intel(0): Relaxed fencing enabled
[    15.521] (**) intel(0): Wait on SwapBuffers? enabled
[    15.521] (**) intel(0): Triple buffering? enabled
[    15.521] (**) intel(0): Framebuffer tiled
[    15.521] (**) intel(0): Pixmaps tiled
[    15.521] (**) intel(0): 3D buffers tiled
[    15.521] (**) intel(0): SwapBuffers wait enabled
[    15.521] (==) intel(0): video overlay key set to 0x101fe
[    15.522] (II) intel(0): Output LVDS1 has no monitor section
[    15.522] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video1
[    15.522] (II) intel(0): Output VGA1 has no monitor section
[    15.544] (II) intel(0): Output HDMI1 has no monitor section
[    15.836] (II) intel(0): Output DP1 has no monitor section
[    15.836] (II) intel(0): EDID for output LVDS1
[    15.836] (II) intel(0): Manufacturer: AUO  Model: 213c  Serial#: 0
[    15.836] (II) intel(0): Year: 2008  Week: 1
[    15.836] (II) intel(0): EDID Version: 1.3
[    15.836] (II) intel(0): Digital Display Input
[    15.836] (II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 17
[    15.836] (II) intel(0): Gamma: 2.20
[    15.836] (II) intel(0): No DPMS capabilities specified
[    15.836] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.836] (II) intel(0): First detailed timing is preferred mode
[    15.836] (II) intel(0): redX: 0.590 redY: 0.340   greenX: 0.330 greenY: 0.575
[    15.836] (II) intel(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[    15.836] (II) intel(0): Manufacturer's mask: 0
[    15.836] (II) intel(0): Supported detailed timing:
[    15.836] (II) intel(0): clock: 72.0 MHz   Image Size:  309 x 174 mm
[    15.836] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1494 h_border: 0
[    15.836] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 803 v_border: 0
[    15.836] (II) intel(0): Unknown vendor-specific block f
[    15.836] (II) intel(0):  AUO
[    15.836] (II) intel(0):  B140XW02 V1
[    15.836] (II) intel(0): EDID (in hex):
[    15.836] (II) intel(0):     00ffffffffffff0006af3c2100000000
[    15.836] (II) intel(0):     01120103801f11780a09e59757549327
[    15.836] (II) intel(0):     22505400000001010101010101010101
[    15.836] (II) intel(0):     010101010101201c5680500023303020
[    15.836] (II) intel(0):     360035ae100000180000000f00000000
[    15.836] (II) intel(0):     00000000000000000020000000fe0041
[    15.836] (II) intel(0):     554f0a202020202020202020000000fe
[    15.836] (II) intel(0):     004231343058573032205631200a00b2
[    15.836] (II) intel(0): EDID vendor "AUO", prod id 8508
[    15.836] (II) intel(0): Printing DDC gathered Modelines:
[    15.836] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    15.837] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    15.837] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    15.837] (II) intel(0): Printing probed modes for output LVDS1
[    15.837] (II) intel(0): Modeline "1366x768"x60.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    15.837] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    15.837] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    15.837] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.837] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.837] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.837] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.837] (II) intel(0): EDID for output VGA1
[    15.860] (II) intel(0): EDID for output HDMI1
[    15.908] (II) intel(0): EDID for output DP1
[    15.908] (II) intel(0): Output LVDS1 connected
[    15.908] (II) intel(0): Output VGA1 disconnected
[    15.908] (II) intel(0): Output HDMI1 disconnected
[    15.908] (II) intel(0): Output DP1 disconnected
[    15.908] (II) intel(0): Using exact sizes for initial modes
[    15.908] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    15.908] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.908] (II) intel(0): Kernel page flipping support detected, enabling
[    15.908] (**) intel(0): Display dimensions: (310, 170) mm
[    15.908] (**) intel(0): DPI set to (111, 114)
[    15.908] (II) Loading sub module "fb"
[    15.908] (II) LoadModule: "fb"
[    15.908] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.908] (II) Module fb: vendor="X.Org Foundation"
[    15.908]     compiled for 1.10.4, module version = 1.0.0
[    15.908]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.908] (II) Loading sub module "dri2"
[    15.908] (II) LoadModule: "dri2"
[    15.908] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.908] (II) Module dri2: vendor="X.Org Foundation"
[    15.909]     compiled for 1.10.4, module version = 1.2.0
[    15.909]     ABI class: X.Org Server Extension, version 5.0
[    15.909] (II) UnloadModule: "vesa"
[    15.909] (II) Unloading vesa
[    15.909] (II) UnloadModule: "fbdev"
[    15.909] (II) Unloading fbdev
[    15.909] (II) UnloadModule: "fbdevhw"
[    15.909] (II) Unloading fbdevhw
[    15.909] (==) Depth 24 pixmap format is 32 bpp
[    15.909] (II) intel(0): [DRI2] Setup complete
[    15.909] (II) intel(0): [DRI2]   DRI driver: i965
[    15.909] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    15.917] (II) UXA(0): Driver registered support for the following operations:
[    15.917] (II)         solid
[    15.917] (II)         copy
[    15.917] (II)         composite (RENDER acceleration)
[    15.918] (II)         put_image
[    15.918] (II)         get_image
[    15.918] (==) intel(0): Backing store disabled
[    15.918] (==) intel(0): Silken mouse enabled
[    15.918] (II) intel(0): Initializing HW Cursor
[    15.984] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.985] (==) intel(0): DPMS enabled
[    15.985] (==) intel(0): Intel XvMC decoder enabled
[    15.985] (II) intel(0): Set up textured video
[    15.985] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    15.985] (II) intel(0): direct rendering: DRI2 Enabled
[    15.985] (WW) intel(0): Option "NoLogo" is not used
[    15.985] (==) intel(0): hotplug detection: "enabled"
[    15.986] (--) RandR disabled
[    15.986] (II) Initializing built-in extension Generic Event Extension
[    15.986] (II) Initializing built-in extension SHAPE
[    15.986] (II) Initializing built-in extension MIT-SHM
[    15.986] (II) Initializing built-in extension XInputExtension
[    15.986] (II) Initializing built-in extension XTEST
[    15.986] (II) Initializing built-in extension BIG-REQUESTS
[    15.986] (II) Initializing built-in extension SYNC
[    15.986] (II) Initializing built-in extension XKEYBOARD
[    15.986] (II) Initializing built-in extension XC-MISC
[    15.986] (II) Initializing built-in extension SECURITY
[    15.986] (II) Initializing built-in extension XINERAMA
[    15.986] (II) Initializing built-in extension XFIXES
[    15.986] (II) Initializing built-in extension RENDER
[    15.986] (II) Initializing built-in extension RANDR
[    15.986] (II) Initializing built-in extension COMPOSITE
[    15.986] (II) Initializing built-in extension DAMAGE
[    15.986] (II) Initializing built-in extension GESTURE
[    15.990] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    16.002] (II) intel(0): Setting screen physical size to 361 x 203
[    16.009] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.015] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    16.015] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.015] (II) LoadModule: "evdev"
[    16.015] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.016] (II) Module evdev: vendor="X.Org Foundation"
[    16.016]     compiled for 1.10.2, module version = 2.6.0
[    16.016]     Module class: X.Org XInput Driver
[    16.016]     ABI class: X.Org XInput driver, version 12.3
[    16.016] (II) Using input driver 'evdev' for 'Power Button'
[    16.016] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.016] (**) Power Button: always reports core events
[    16.016] (**) Power Button: Device: "/dev/input/event2"
[    16.016] (--) Power Button: Found keys
[    16.016] (II) Power Button: Configuring as keyboard
[    16.016] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    16.016] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.016] (**) Option "xkb_rules" "evdev"
[    16.016] (**) Option "xkb_model" "pc105"
[    16.016] (**) Option "xkb_layout" "us"
[    16.017] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    16.017] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.017] (II) Using input driver 'evdev' for 'Video Bus'
[    16.017] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.017] (**) Video Bus: always reports core events
[    16.017] (**) Video Bus: Device: "/dev/input/event8"
[    16.017] (--) Video Bus: Found keys
[    16.017] (II) Video Bus: Configuring as keyboard
[    16.017] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input8/event8"
[    16.017] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    16.017] (**) Option "xkb_rules" "evdev"
[    16.017] (**) Option "xkb_model" "pc105"
[    16.017] (**) Option "xkb_layout" "us"
[    16.018] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    16.018] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.018] (II) Using input driver 'evdev' for 'Video Bus'
[    16.018] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.018] (**) Video Bus: always reports core events
[    16.018] (**) Video Bus: Device: "/dev/input/event7"
[    16.018] (--) Video Bus: Found keys
[    16.018] (II) Video Bus: Configuring as keyboard
[    16.018] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input7/event7"
[    16.018] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    16.018] (**) Option "xkb_rules" "evdev"
[    16.018] (**) Option "xkb_model" "pc105"
[    16.018] (**) Option "xkb_layout" "us"
[    16.020] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    16.020] (II) No input driver/identifier specified (ignoring)
[    16.020] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    16.020] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    16.020] (II) Using input driver 'evdev' for 'Sleep Button'
[    16.020] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.020] (**) Sleep Button: always reports core events
[    16.020] (**) Sleep Button: Device: "/dev/input/event1"
[    16.020] (--) Sleep Button: Found keys
[    16.020] (II) Sleep Button: Configuring as keyboard
[    16.020] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    16.020] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    16.020] (**) Option "xkb_rules" "evdev"
[    16.020] (**) Option "xkb_model" "pc105"
[    16.020] (**) Option "xkb_layout" "us"
[    16.022] (II) config/udev: Adding input device USB 2.0 UVC 0.3M Webcam (/dev/input/event6)
[    16.022] (**) USB 2.0 UVC 0.3M Webcam: Applying InputClass "evdev keyboard catchall"
[    16.022] (II) Using input driver 'evdev' for 'USB 2.0 UVC 0.3M Webcam'
[    16.022] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.022] (**) USB 2.0 UVC 0.3M Webcam: always reports core events
[    16.022] (**) USB 2.0 UVC 0.3M Webcam: Device: "/dev/input/event6"
[    16.022] (--) USB 2.0 UVC 0.3M Webcam: Found keys
[    16.022] (II) USB 2.0 UVC 0.3M Webcam: Configuring as keyboard
[    16.022] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6/event6"
[    16.022] (II) XINPUT: Adding extended input device "USB 2.0 UVC 0.3M Webcam" (type: KEYBOARD)
[    16.022] (**) Option "xkb_rules" "evdev"
[    16.022] (**) Option "xkb_model" "pc105"
[    16.022] (**) Option "xkb_layout" "us"
[    16.023] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event10)
[    16.023] (II) No input driver/identifier specified (ignoring)
[    16.023] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event11)
[    16.023] (II) No input driver/identifier specified (ignoring)
[    16.024] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event12)
[    16.024] (II) No input driver/identifier specified (ignoring)
[    16.025] (II) config/udev: Adding input device MLK PROLiNK Wireless Laser Mouse (/dev/input/event4)
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: Applying InputClass "evdev pointer catchall"
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: Applying InputClass "evdev keyboard catchall"
[    16.025] (II) Using input driver 'evdev' for 'MLK PROLiNK Wireless Laser Mouse'
[    16.025] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: always reports core events
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: Device: "/dev/input/event4"
[    16.025] (--) MLK PROLiNK Wireless Laser Mouse: Found 9 mouse buttons
[    16.025] (--) MLK PROLiNK Wireless Laser Mouse: Found scroll wheel(s)
[    16.025] (--) MLK PROLiNK Wireless Laser Mouse: Found relative axes
[    16.025] (--) MLK PROLiNK Wireless Laser Mouse: Found x and y relative axes
[    16.025] (--) MLK PROLiNK Wireless Laser Mouse: Found absolute axes
[    16.025] (II) evdev-grail: failed to open grail, no gesture support
[    16.025] (--) MLK PROLiNK Wireless Laser Mouse: Found keys
[    16.025] (II) MLK PROLiNK Wireless Laser Mouse: Configuring as mouse
[    16.025] (II) MLK PROLiNK Wireless Laser Mouse: Configuring as keyboard
[    16.025] (II) MLK PROLiNK Wireless Laser Mouse: Adding scrollwheel support
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: YAxisMapping: buttons 4 and 5
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.025] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4/event4"
[    16.025] (II) XINPUT: Adding extended input device "MLK PROLiNK Wireless Laser Mouse" (type: KEYBOARD)
[    16.025] (**) Option "xkb_rules" "evdev"
[    16.025] (**) Option "xkb_model" "pc105"
[    16.025] (**) Option "xkb_layout" "us"
[    16.025] (II) MLK PROLiNK Wireless Laser Mouse: initialized for relative axes.
[    16.025] (WW) MLK PROLiNK Wireless Laser Mouse: ignoring absolute axes.
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: (accel) keeping acceleration scheme 1
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: (accel) acceleration profile 0
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: (accel) acceleration factor: 2.000
[    16.025] (**) MLK PROLiNK Wireless Laser Mouse: (accel) acceleration threshold: 4
[    16.026] (II) config/udev: Adding input device MLK PROLiNK Wireless Laser Mouse (/dev/input/mouse0)
[    16.026] (II) No input driver/identifier specified (ignoring)
[    16.028] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event5)
[    16.028] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[    16.028] (II) Using input driver 'evdev' for 'Asus Laptop extra buttons'
[    16.028] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.028] (**) Asus Laptop extra buttons: always reports core events
[    16.028] (**) Asus Laptop extra buttons: Device: "/dev/input/event5"
[    16.028] (--) Asus Laptop extra buttons: Found keys
[    16.028] (II) Asus Laptop extra buttons: Configuring as keyboard
[    16.028] (**) Option "config_info" "udev:/sys/devices/platform/asus_laptop/input/input5/event5"
[    16.028] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
[    16.028] (**) Option "xkb_rules" "evdev"
[    16.028] (**) Option "xkb_model" "pc105"
[    16.028] (**) Option "xkb_layout" "us"
[    16.029] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    16.029] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.029] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.029] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.029] (**) AT Translated Set 2 keyboard: always reports core events
[    16.029] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    16.029] (--) AT Translated Set 2 keyboard: Found keys
[    16.029] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    16.029] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    16.029] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    16.029] (**) Option "xkb_rules" "evdev"
[    16.029] (**) Option "xkb_model" "pc105"
[    16.029] (**) Option "xkb_layout" "us"
[    16.029] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event9)
[    16.029] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    16.029] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    16.029] (II) LoadModule: "synaptics"
[    16.029] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.029] (II) Module synaptics: vendor="X.Org Foundation"
[    16.029]     compiled for 1.10.4, module version = 1.4.1
[    16.029]     Module class: X.Org XInput Driver
[    16.029]     ABI class: X.Org XInput driver, version 12.3
[    16.029] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    16.029] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.029] (**) ETPS/2 Elantech Touchpad: always reports core events
[    16.029] (**) Option "Device" "/dev/input/event9"
[    16.088] (--) ETPS/2 Elantech Touchpad: x-axis range 8 - 1144
[    16.088] (--) ETPS/2 Elantech Touchpad: y-axis range 8 - 760
[    16.088] (--) ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    16.088] (--) ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    16.088] (--) ETPS/2 Elantech Touchpad: buttons: left right double triple
[    16.120] (--) ETPS/2 Elantech Touchpad: touchpad found
[    16.120] (**) ETPS/2 Elantech Touchpad: always reports core events
[    16.136] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input9/event9"
[    16.136] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD)
[    16.136] (**) ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    16.136] (**) ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[    16.136] (**) ETPS/2 Elantech Touchpad: AccelFactor is now 0.147
[    16.136] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    16.136] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    16.136] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    16.136] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    16.137] (--) ETPS/2 Elantech Touchpad: touchpad found
[    16.137] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    16.137] (II) No input driver/identifier specified (ignoring)
[    17.344] (II) intel(0): EDID vendor "AUO", prod id 8508
[    17.344] (II) intel(0): Printing DDC gathered Modelines:
[    17.344] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    17.455] (II) intel(0): EDID vendor "AUO", prod id 8508
[    17.455] (II) intel(0): Printing DDC gathered Modelines:
[    17.455] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    21.430] (II) intel(0): EDID vendor "AUO", prod id 8508
[    21.430] (II) intel(0): Printing DDC gathered Modelines:
[    21.430] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    21.929] (II) intel(0): EDID vendor "AUO", prod id 8508
[    21.929] (II) intel(0): Printing DDC gathered Modelines:
[    21.929] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    22.763] (II) intel(0): EDID vendor "AUO", prod id 8508
[    22.763] (II) intel(0): Printing DDC gathered Modelines:
[    22.763] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    22.884] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    25.232] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.232] (II) intel(0): Printing DDC gathered Modelines:
[    25.232] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.300] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.300] (II) intel(0): Printing DDC gathered Modelines:
[    25.300] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.368] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.368] (II) intel(0): Printing DDC gathered Modelines:
[    25.368] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.445] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.445] (II) intel(0): Printing DDC gathered Modelines:
[    25.445] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.517] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.517] (II) intel(0): Printing DDC gathered Modelines:
[    25.517] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.588] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.588] (II) intel(0): Printing DDC gathered Modelines:
[    25.588] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.661] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.661] (II) intel(0): Printing DDC gathered Modelines:
[    25.661] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.733] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.733] (II) intel(0): Printing DDC gathered Modelines:
[    25.733] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.809] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.809] (II) intel(0): Printing DDC gathered Modelines:
[    25.809] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.881] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.881] (II) intel(0): Printing DDC gathered Modelines:
[    25.881] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    25.959] (II) intel(0): EDID vendor "AUO", prod id 8508
[    25.960] (II) intel(0): Printing DDC gathered Modelines:
[    25.960] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    26.045] (II) intel(0): EDID vendor "AUO", prod id 8508
[    26.045] (II) intel(0): Printing DDC gathered Modelines:
[    26.045] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    26.137] (II) intel(0): EDID vendor "AUO", prod id 8508
[    26.137] (II) intel(0): Printing DDC gathered Modelines:
[    26.137] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    26.215] (II) intel(0): EDID vendor "AUO", prod id 8508
[    26.215] (II) intel(0): Printing DDC gathered Modelines:
[    26.215] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    26.288] (II) intel(0): EDID vendor "AUO", prod id 8508
[    26.288] (II) intel(0): Printing DDC gathered Modelines:
[    26.288] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    26.357] (II) intel(0): EDID vendor "AUO", prod id 8508
[    26.357] (II) intel(0): Printing DDC gathered Modelines:
[    26.357] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    26.433] (II) intel(0): EDID vendor "AUO", prod id 8508
[    26.433] (II) intel(0): Printing DDC gathered Modelines:
[    26.433] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    28.798] (II) intel(0): EDID vendor "AUO", prod id 8508
[    28.798] (II) intel(0): Printing DDC gathered Modelines:
[    28.798] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    28.874] (II) intel(0): EDID vendor "AUO", prod id 8508
[    28.874] (II) intel(0): Printing DDC gathered Modelines:
[    28.874] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    28.961] (II) intel(0): EDID vendor "AUO", prod id 8508
[    28.961] (II) intel(0): Printing DDC gathered Modelines:
[    28.961] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    29.038] (II) intel(0): EDID vendor "AUO", prod id 8508
[    29.038] (II) intel(0): Printing DDC gathered Modelines:
[    29.038] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    29.113] (II) intel(0): EDID vendor "AUO", prod id 8508
[    29.113] (II) intel(0): Printing DDC gathered Modelines:
[    29.113] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    29.190] (II) intel(0): EDID vendor "AUO", prod id 8508
[    29.190] (II) intel(0): Printing DDC gathered Modelines:
[    29.190] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    29.264] (II) intel(0): EDID vendor "AUO", prod id 8508
[    29.264] (II) intel(0): Printing DDC gathered Modelines:
[    29.264] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[    31.496] (II) intel(0): EDID vendor "AUO", prod id 8508
[    31.496] (II) intel(0): Printing DDC gathered Modelines:
[    31.496] (II) intel(0): Modeline "1366x768"x0.0   72.00  1366 1414 1446 1494  768 771 777 803 -hsync -vsync (48.2 kHz)
[   170.462] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   843.322] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
```

---

### Post by crdlb on 2011-10-14
The nvidia glx module is still present. Do you have nvidia-current-updates installed? if so, uninstall that. (I'm not sure what the difference between those two is.) If not, you could try reinstalling the regular glx module and libgl: ```
sudo apt-get --reinstall install xserver-xorg-core libgl1-mesa-glx
``` and reboot again.

---

### Post by Lexas on 2011-10-15
Hello, I've got the exact same problem with the same errors, I just upgraded my ubuntu today (fresh install) and followed your steps, still nothing, I will do some research and see if I come up with something D:

---

### Post by Lexas on 2011-10-15
Repost from my reply on [this thread:]("http://ubuntuforums.org/showthread.php?p=11349853#post11349853")

Hello, I just mannaged to get gnome3 running, Try installing Ironhide ([https://launchpad.net/~mj-casalogic/+archive/ironhide/]("https://launchpad.net/%7Emj-casalogic/+archive/ironhide/")) from this PPA
 **ppa:mj-casalogic/ironhide**. 

Then reinstall nvidia-current and write the command:

```
 sudo ironhide-configuration
```Once you've finished the  configuration, reboot your PC and try to get in gnome3, you shouldn't  fallback.

If you need to run an application that requires 3d acceleration, install ironhide UI and check those programs, or run 
```
optirun your-program
```to definitely enable/disable 3d acceleration write respectively:
```
sudo ironhide-enablecard
``````
sudo ironhide-disablecard
```

---

### Post by melvinsim on 2011-10-16
thanks crdlb and Lexas.

i did the ironhide method and it works for me too.

finally have gnome 3 without falling back :)

thanks for both your help!

---

