---
title: "screen with unreadable characters  ubuntu 11.10"
date: 2011-12-12
forum: General Help
---

### Post by jgsantillana on 2011-12-12
Hello

I have a Dell computer with ubuntu, after updated from 11.04 to 11.10 something happened to my screen, it seems when I have many applications running, the characters in the screen become unreadable (I've attached  2  screenshots).  What should I do?   PLease help.

Gerry

---

### Post by shakabra on 2011-12-13
What video driver are you using?

What is the output of
```
cat /var/log/Xorg.0.log
```

---

### Post by Mark Phelps on 2011-12-13
Please open a terminal, enter "lspci" and post the output of the line containing "VGA" -- so we can see what video chipset you are using.

---

### Post by jgsantillana on 2011-12-13
after doing this
cat /var/log/Xorg.0.log
this is the result
```
[    31.649]     Module class: X.Org Server Extension
[    31.649]     ABI class: X.Org Server Extension, version 5.0
[    31.649] (II) Loading extension RECORD
[    31.649] (II) LoadModule: "dri"
[    31.649] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    31.650] (II) Module dri: vendor="X.Org Foundation"
[    31.650]     compiled for 1.10.4, module version = 1.0.0
[    31.650]     ABI class: X.Org Server Extension, version 5.0
[    31.650] (II) Loading extension XFree86-DRI
[    31.650] (II) LoadModule: "dri2"
[    31.650] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    31.650] (II) Module dri2: vendor="X.Org Foundation"
[    31.650]     compiled for 1.10.4, module version = 1.2.0
[    31.650]     ABI class: X.Org Server Extension, version 5.0
[    31.651] (II) Loading extension DRI2
[    31.651] (==) Matched intel as autoconfigured driver 0
[    31.651] (==) Matched vesa as autoconfigured driver 1
[    31.651] (==) Matched fbdev as autoconfigured driver 2
[    31.651] (==) Assigned the driver to the xf86ConfigLayout
[    31.651] (II) LoadModule: "intel"
[    31.651] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    31.658] (II) Module intel: vendor="X.Org Foundation"
[    31.658]     compiled for 1.10.4, module version = 2.15.901
[    31.658]     Module class: X.Org Video Driver
[    31.658]     ABI class: X.Org Video Driver, version 10.0
[    31.658] (II) LoadModule: "vesa"
[    31.659] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.659] (II) Module vesa: vendor="X.Org Foundation"
[    31.659]     compiled for 1.10.2, module version = 2.3.0
[    31.659]     Module class: X.Org Video Driver
[    31.659]     ABI class: X.Org Video Driver, version 10.0
[    31.659] (II) LoadModule: "fbdev"
[    31.660] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.660] (II) Module fbdev: vendor="X.Org Foundation"
[    31.660]     compiled for 1.10.0, module version = 0.4.2
[    31.660]     ABI class: X.Org Video Driver, version 10.0
[    31.660] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    31.661] (II) VESA: driver for VESA chipsets: vesa
[    31.661] (II) FBDEV: driver for framebuffer: fbdev
[    31.661] (++) using VT number 7

[    31.665] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    31.666] (WW) Falling back to old probe method for vesa
[    31.666] (WW) Falling back to old probe method for fbdev
[    31.666] (II) Loading sub module "fbdevhw"
[    31.666] (II) LoadModule: "fbdevhw"
[    31.735] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    31.735] (II) Module fbdevhw: vendor="X.Org Foundation"
[    31.735]     compiled for 1.10.4, module version = 0.0.2
[    31.735]     ABI class: X.Org Video Driver, version 10.0
[    31.736] drmOpenDevice: node name is /dev/dri/card0
[    31.736] drmOpenDevice: open result is 12, (OK)
[    31.736] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    31.736] drmOpenDevice: node name is /dev/dri/card0
[    31.736] drmOpenDevice: open result is 12, (OK)
[    31.736] drmOpenByBusid: drmOpenMinor returns 12
[    31.736] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    31.736] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    31.736] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    31.736] (==) intel(0): RGB weight 888
[    31.736] (==) intel(0): Default visual is TrueColor
[    31.736] (II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
[    31.736] (--) intel(0): Chipset: "915G"
[    31.736] (**) intel(0): Relaxed fencing disabled
[    31.736] (**) intel(0): Wait on SwapBuffers? enabled
[    31.736] (**) intel(0): Triple buffering? enabled
[    31.736] (**) intel(0): Framebuffer tiled
[    31.736] (**) intel(0): Pixmaps tiled
[    31.736] (**) intel(0): 3D buffers tiled
[    31.736] (**) intel(0): SwapBuffers wait enabled
[    31.737] (==) intel(0): video overlay key set to 0x101fe
[    31.884] (II) intel(0): Output VGA1 has no monitor section
[    31.994] (II) intel(0): EDID for output VGA1
[    31.994] (II) intel(0): Manufacturer: DEL  Model: 4023  Serial#: 809709897
[    31.994] (II) intel(0): Year: 2007  Week: 24
[    31.994] (II) intel(0): EDID Version: 1.3
[    31.994] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    31.994] (II) intel(0): Sync:  Separate  SyncOnGreen
[    31.994] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    31.994] (II) intel(0): Gamma: 2.20
[    31.994] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    31.994] (II) intel(0): Default color space is primary color space
[    31.994] (II) intel(0): First detailed timing is preferred mode
[    31.994] (II) intel(0): redX: 0.646 redY: 0.336   greenX: 0.296 greenY: 0.606
[    31.994] (II) intel(0): blueX: 0.149 blueY: 0.074   whiteX: 0.313 whiteY: 0.329
[    31.994] (II) intel(0): Supported established timings:
[    31.994] (II) intel(0): 720x400@70Hz
[    31.994] (II) intel(0): 640x480@60Hz
[    31.994] (II) intel(0): 640x480@75Hz
[    31.994] (II) intel(0): 800x600@60Hz
[    31.994] (II) intel(0): 800x600@75Hz
[    31.994] (II) intel(0): 1024x768@60Hz
[    31.994] (II) intel(0): 1024x768@75Hz
[    31.994] (II) intel(0): 1280x1024@75Hz
[    31.994] (II) intel(0): Manufacturer's mask: 0
[    31.994] (II) intel(0): Supported standard timings:
[    31.994] (II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    31.994] (II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    31.994] (II) intel(0): Supported detailed timing:
[    31.994] (II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    31.994] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    31.994] (II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    31.995] (II) intel(0): Serial No: PM37276E0C1I
[    31.995] (II) intel(0): Monitor name: DELL 1708FP
[    31.995] (II) intel(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    31.995] (II) intel(0): EDID (in hex):
[    31.995] (II) intel(0):     00ffffffffffff0010ac234049314330
[    31.995] (II) intel(0):     181101036a221b78ee8d45a5564b9b26
[    31.995] (II) intel(0):     135054a54b008180714f010101010101
[    31.995] (II) intel(0):     010101010101302a009851002a403070
[    31.995] (II) intel(0):     1300520e1100001e000000ff00504d33
[    31.995] (II) intel(0):     3732373645304331490a000000fc0044
[    31.995] (II) intel(0):     454c4c203137303846500a20000000fd
[    31.995] (II) intel(0):     00384c1e510e000a202020202020000e
[    31.995] (II) intel(0): EDID vendor "DEL", prod id 16419
[    31.995] (II) intel(0): Using EDID range info for horizontal sync
[    31.995] (II) intel(0): Using EDID range info for vertical refresh
[    31.995] (II) intel(0): Printing DDC gathered Modelines:
[    31.995] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    31.995] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    31.995] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    31.995] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    31.995] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    31.995] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    31.995] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    31.995] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    31.995] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    31.995] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    31.995] (II) intel(0): Printing probed modes for output VGA1
[    31.995] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    31.996] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    31.996] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    31.996] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    31.996] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    31.996] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    31.996] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    31.996] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    31.996] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    31.996] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    31.996] (II) intel(0): Output VGA1 connected
[    31.996] (II) intel(0): Using exact sizes for initial modes
[    31.996] (II) intel(0): Output VGA1 using initial mode 1280x1024
[    31.996] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    31.996] (II) intel(0): Kernel page flipping support detected, enabling
[    31.996] (**) intel(0): Display dimensions: (340, 270) mm
[    31.996] (**) intel(0): DPI set to (95, 96)
[    31.996] (II) Loading sub module "fb"
[    31.996] (II) LoadModule: "fb"
[    31.997] (II) Loading /usr/lib/xorg/modules/libfb.so
[    31.997] (II) Module fb: vendor="X.Org Foundation"
[    31.997]     compiled for 1.10.4, module version = 1.0.0
[    31.997]     ABI class: X.Org ANSI C Emulation, version 0.4
[    31.997] (II) Loading sub module "dri2"
[    31.997] (II) LoadModule: "dri2"
[    31.997] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    31.998] (II) Module dri2: vendor="X.Org Foundation"
[    31.998]     compiled for 1.10.4, module version = 1.2.0
[    31.998]     ABI class: X.Org Server Extension, version 5.0
[    31.998] (II) UnloadModule: "vesa"
[    31.998] (II) Unloading vesa
[    31.998] (II) UnloadModule: "fbdev"
[    31.998] (II) Unloading fbdev
[    31.998] (II) UnloadModule: "fbdevhw"
[    31.998] (II) Unloading fbdevhw
[    31.998] (==) Depth 24 pixmap format is 32 bpp
[    31.998] (II) intel(0): [DRI2] Setup complete
[    31.998] (II) intel(0): [DRI2]   DRI driver: i915
[    31.998] (II) intel(0): Allocated new frame buffer 1280x1024 stride 8192, tiled
[    31.998] (II) UXA(0): Driver registered support for the following operations:
[    31.998] (II)         solid
[    31.998] (II)         copy
[    31.998] (II)         composite (RENDER acceleration)
[    31.998] (II)         put_image
[    31.998] (II)         get_image
[    31.998] (==) intel(0): Backing store disabled
[    31.998] (==) intel(0): Silken mouse enabled
[    31.999] (II) intel(0): Initializing HW Cursor
[    32.028] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    32.028] (==) intel(0): DPMS enabled
[    32.028] (==) intel(0): Intel XvMC decoder disabled
[    32.028] (II) intel(0): Set up textured video
[    32.028] (II) intel(0): Set up overlay video
[    32.028] (II) intel(0): direct rendering: DRI2 Enabled
[    32.028] (==) intel(0): hotplug detection: "enabled"
[    32.028] (--) RandR disabled
[    32.028] (II) Initializing built-in extension Generic Event Extension
[    32.029] (II) Initializing built-in extension SHAPE
[    32.029] (II) Initializing built-in extension MIT-SHM
[    32.029] (II) Initializing built-in extension XInputExtension
[    32.029] (II) Initializing built-in extension XTEST
[    32.029] (II) Initializing built-in extension BIG-REQUESTS
[    32.029] (II) Initializing built-in extension SYNC
[    32.029] (II) Initializing built-in extension XKEYBOARD
[    32.029] (II) Initializing built-in extension XC-MISC
[    32.029] (II) Initializing built-in extension SECURITY
[    32.029] (II) Initializing built-in extension XINERAMA
[    32.029] (II) Initializing built-in extension XFIXES
[    32.029] (II) Initializing built-in extension RENDER
[    32.029] (II) Initializing built-in extension RANDR
[    32.029] (II) Initializing built-in extension COMPOSITE
[    32.029] (II) Initializing built-in extension DAMAGE
[    32.029] (II) Initializing built-in extension GESTURE
[    32.074] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i915_dri.so
[    32.086] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    32.086] (II) AIGLX: enabled GLX_INTEL_swap_event
[    32.086] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    32.086] (II) AIGLX: enabled GLX_SGI_make_current_read
[    32.086] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    32.087] (II) AIGLX: Loaded and initialized i915
[    32.087] (II) GLX: Initialized DRI2 GL provider for screen 0
[    32.088] (II) intel(0): Setting screen physical size to 338 x 270
[    32.118] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.150] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    32.151] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.151] (II) LoadModule: "evdev"
[    32.151] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.154] (II) Module evdev: vendor="X.Org Foundation"
[    32.154]     compiled for 1.10.2, module version = 2.6.0
[    32.154]     Module class: X.Org XInput Driver
[    32.154]     ABI class: X.Org XInput driver, version 12.3
[    32.154] (II) Using input driver 'evdev' for 'Power Button'
[    32.154] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.154] (**) Power Button: always reports core events
[    32.154] (**) Power Button: Device: "/dev/input/event1"
[    32.154] (--) Power Button: Found keys
[    32.154] (II) Power Button: Configuring as keyboard
[    32.154] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    32.154] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    32.154] (**) Option "xkb_rules" "evdev"
[    32.154] (**) Option "xkb_model" "pc105"
[    32.154] (**) Option "xkb_layout" "us"
[    32.157] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    32.157] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.157] (II) Using input driver 'evdev' for 'Power Button'
[    32.157] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.157] (**) Power Button: always reports core events
[    32.157] (**) Power Button: Device: "/dev/input/event0"
[    32.157] (--) Power Button: Found keys
[    32.157] (II) Power Button: Configuring as keyboard
[    32.157] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    32.157] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    32.157] (**) Option "xkb_rules" "evdev"
[    32.157] (**) Option "xkb_model" "pc105"
[    32.157] (**) Option "xkb_layout" "us"
[    32.162] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[    32.163] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    32.163] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    32.163] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.163] (**) Dell Dell USB Keyboard: always reports core events
[    32.163] (**) Dell Dell USB Keyboard: Device: "/dev/input/event2"
[    32.163] (--) Dell Dell USB Keyboard: Found keys
[    32.163] (II) Dell Dell USB Keyboard: Configuring as keyboard
[    32.163] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input2/event2"
[    32.163] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
[    32.163] (**) Option "xkb_rules" "evdev"
[    32.163] (**) Option "xkb_model" "pc105"
[    32.163] (**) Option "xkb_layout" "us"
[    32.167] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[    32.167] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    32.167] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    32.167] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.167] (**) Logitech USB Optical Mouse: always reports core events
[    32.167] (**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
[    32.167] (--) Logitech USB Optical Mouse: Found 3 mouse buttons
[    32.167] (--) Logitech USB Optical Mouse: Found scroll wheel(s)
[    32.167] (--) Logitech USB Optical Mouse: Found relative axes
[    32.167] (--) Logitech USB Optical Mouse: Found x and y relative axes
[    32.167] (II) Logitech USB Optical Mouse: Configuring as mouse
[    32.167] (II) Logitech USB Optical Mouse: Adding scrollwheel support
[    32.167] (**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    32.167] (**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    32.167] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input3/event3"
[    32.167] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
[    32.167] (II) Logitech USB Optical Mouse: initialized for relative axes.
[    32.167] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    32.167] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    32.167] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    32.167] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    32.168] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    32.168] (II) No input driver/identifier specified (ignoring)
[    35.200] (II) intel(0): EDID vendor "DEL", prod id 16419
[    35.200] (II) intel(0): Using hsync ranges from config file
[    35.200] (II) intel(0): Using vrefresh ranges from config file
[    35.200] (II) intel(0): Printing DDC gathered Modelines:
[    35.200] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.200] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.200] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    35.200] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.200] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    35.200] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    35.200] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    35.200] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.200] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    35.200] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    35.391] (II) intel(0): EDID vendor "DEL", prod id 16419
[    35.391] (II) intel(0): Using hsync ranges from config file
[    35.391] (II) intel(0): Using vrefresh ranges from config file
[    35.391] (II) intel(0): Printing DDC gathered Modelines:
[    35.391] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.391] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.391] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    35.391] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.391] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    35.391] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    35.391] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    35.391] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.391] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    35.391] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    35.914] (II) intel(0): EDID vendor "DEL", prod id 16419
[    35.914] (II) intel(0): Using hsync ranges from config file
[    35.914] (II) intel(0): Using vrefresh ranges from config file
[    35.914] (II) intel(0): Printing DDC gathered Modelines:
[    35.914] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.914] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.914] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    35.914] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.915] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    35.915] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    35.915] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    35.915] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.915] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    35.915] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    64.838] (II) intel(0): EDID vendor "DEL", prod id 16419
[    64.838] (II) intel(0): Using hsync ranges from config file
[    64.838] (II) intel(0): Using vrefresh ranges from config file
[    64.838] (II) intel(0): Printing DDC gathered Modelines:
[    64.838] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    64.838] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    64.838] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    64.838] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    64.838] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    64.838] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    64.838] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    64.838] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    64.839] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    64.839] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    65.454] (II) intel(0): EDID vendor "DEL", prod id 16419
[    65.454] (II) intel(0): Using hsync ranges from config file
[    65.454] (II) intel(0): Using vrefresh ranges from config file
[    65.454] (II) intel(0): Printing DDC gathered Modelines:
[    65.454] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    65.454] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    65.454] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    65.454] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    65.454] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    65.454] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    65.455] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    65.455] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    65.455] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    65.455] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    65.716] (II) intel(0): EDID vendor "DEL", prod id 16419
[    65.716] (II) intel(0): Using hsync ranges from config file
[    65.716] (II) intel(0): Using vrefresh ranges from config file
[    65.716] (II) intel(0): Printing DDC gathered Modelines:
[    65.716] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    65.716] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    65.716] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    65.716] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    65.716] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    65.716] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    65.716] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    65.716] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    65.716] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    65.716] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    68.915] (II) intel(0): EDID vendor "DEL", prod id 16419
[    69.097] (II) intel(0): Using hsync ranges from config file
[    69.097] (II) intel(0): Using vrefresh ranges from config file
[    69.097] (II) intel(0): Printing DDC gathered Modelines:
[    69.097] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    69.097] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    69.097] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    69.097] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    69.097] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    69.097] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    69.098] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    69.098] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    69.098] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    69.098] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    80.656] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm
@Home-Dell:~$
```

---

### Post by jgsantillana on 2011-12-13
result of  lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

---

### Post by jgsantillana on 2012-01-03
I am still having this problem please help!

---

