---
title: "Please Help, Xorg  itself up"
date: 2010-01-24
forum: General Help
---

### Post by Valleyman1988 on 2010-01-24
Hello,

I seem to be having some difficulty with my Xorg server, I can get it to run from time to time but most of the times I end up with a couple of abstract lines across my screen, nothing more, no mouse, no keyboard, no keyboardlights even.

Now please don't start about trying different versions of the driver, I've tried them all.
Also tested the computer with some different operating systems to check the hardware, nothing wrong there, when I use the "nv"-driver option, it's able to get itself together.
I have a Geforce FX 5200 AGP card in a somewhat "older" machine running on 1,5 GB of RAM, an AMD Sempron clocked to about 1,6 Ghz.

I've looked around, google'd my *** off, nothing seems to be relevant.
Any Ideas here or do I just buy me a windows? :-p

Edit: Forgot to mention, I'm running a fully updated Karmic...

Also, I've got some Xorg.log entries below...
```

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
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [24] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [25] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [26] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [27] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [28] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [29] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [30] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [31] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [32] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [33] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [34] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [35] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [36] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [37] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [38] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [39] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [40] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [41] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [42] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [43] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [44] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [45] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [46] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [47] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [48] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [49] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [50] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [51] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [52] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [53] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [54] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [55] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [56] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [57] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [58] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [59] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.16.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
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
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [20] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [21] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [22] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [23] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [24] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [25] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [26] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [27] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [28] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [29] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [30] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [31] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [32] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [33] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [34] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [35] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [36] -1 0       0xffffffff - 0xffffffff (0x1) MX[B]
        [37] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [38] -1 0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [39] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [40] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [41] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [42] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [43] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [44] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [45] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [46] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [47] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [48] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [49] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [50] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [51] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [52] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [53] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [54] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [55] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [56] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [57] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
        [58] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [59] -1 0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.
(II) NVIDIA(0): Initialized GART.
(EE) NVIDIA(0): Failed to allocate clip rectangle
(EE) NVIDIA(0):  *** Aborting ***
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) Loading extension NV-GLX 
```

---

### Post by danastasio on 2010-01-24
can you post the actual xorg.conf file for us?

also if you run Xorg --configure under sudo, you should be able to generate a very basic, very general xorg.conf that should get the display working. (Not with the nvidia driver, but working)

and can you post the output of

```
lspci
```

so i can see your video card?

thanks

---

### Post by rogue_0111 on 2010-01-24
These may be of some help:

[http://ubuntuforums.org/archive/index.php/t-478560.html](http://ubuntuforums.org/archive/index.php/t-478560.html)

or

[http://www.computing.net/answers/linux/messed-up-xorgconf/29482.html](http://www.computing.net/answers/linux/messed-up-xorgconf/29482.html)

or

[http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/](http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/)

or

[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

---

### Post by Valleyman1988 on 2010-01-25
> **danastasio said:**
> can you post the actual xorg.conf file for us?

also if you run Xorg --configure under sudo, you should be able to generate a very basic, very general xorg.conf that should get the display working. (Not with the nvidia driver, but working)

and can you post the output of

```
lspci
```so i can see your video card?

thanks

XORG.CONF :

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Thu Jun 25 18:57:07 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
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
    ModelName      "Unknown"
    HorizSync       30.0 - 60.0
    VertRefresh     50 - 75,1
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "640x480"
    EndSubSection
EndSection

LSPCI :

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 Sout                                                                                        h]
00:09.0 FireWire (IEEE 1394): Hitachi Micro Systems Device 00f2 (rev 05)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/                                                                                        C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                                         (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                                         (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                                         (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                                         (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T89                                                                                        0 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 A                                                                                        C97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra                                                                                        nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address                                                                                         Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con                                                                                        troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella                                                                                        neous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (re                                                                                        v a1)


And yes indeed, without the driver it will work, but what bothers me is that now for instance, just got to my desk, booted it up. didn't work, pressed reset, went into single user to check something, gave an init 6, got distracted, looked back over and there is the damn desktop again, in correct resolution with effect and all other stuff :-s
I really think it has something to do with that "GART"-thingy...

---

### Post by danastasio on 2010-01-25
Alright, I diff'd your config file to mine, and yours was kinda messy with a few grammer issues (like a comma inplace of a period). So I re-wrote the file (which seems like a totally generic nvidia config) I re-organized a few sections so that it made more sense, I don't guarentee that it'll work, if it breaks your computer, well you get to keep both halves :P
Make sure you backup your current file

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

then replace the current xorg.conf with the one that I rewrote, and lemme know what happens.

(make sure you change .txt to .conf, the uploader wouldn't let me upload it as is)

---

### Post by Valleyman1988 on 2010-01-25
I'm afraid I still get the GART-stuff in the log files mentioned above, got running again after a couple of tries :-s 
This is so strange....
Thanks for the corrections anyway, I didn't really know what I was doing and since it kept breaking and I kept trying...

I thought it had something to do with my DMA or agpgart but I checked and DMA is enabled in the Bios and I have the modules for both :-s

---

### Post by danastasio on 2010-01-25
have you tried that last link in rouge's post?
It could also be that the card has finally died...

---

### Post by Valleyman1988 on 2010-01-26
Got the same result out of that to, a friend of mine has a card I can use to test it, I'm going to try it out just to see if the motherboard is ok, and we'll try the card in a different computer as well if possible.
But I guess it probably died a silent death or is doing so then.
Thanks for the help anyway!

---

