---
title: "Graphics/Screen Resolution Suddenly Died"
date: 2009-07-14
forum: General Help
---

### Post by phoenix910 on 2009-07-14
Hi guys, so basically, I've had the latest NVIDIA Drivers Binaries (official ones) installed for a while now, working, etc., on my 8600GT. No problem at all with it. Today, I rebooted - had changed no files or anything, and next time the PC restarted, the resolution was fixed at 640x480. Xorg.conf is still the same - I have tried reinstalling the drivers, completely removing and reinstall xserver-xorg, manually specifying resolutions, running nvidia-settings to try and change it, etc. What else should I be looking for? As this seems a really strange problemo. Thanks

PS: Also, might I mention, the Nvidia drivers still load - I'm able to use all the compiz effects etc., just at a stupidly low resolution.

---

### Post by dlmarti on 2009-07-14
did you try the nvidia tool to change the resolution?

/usr/bin/nvidia-settings

---

### Post by Wim Sturkenboom on 2009-07-14
What do the xorg logs say?

---

### Post by prshah on 2009-07-14
> **phoenix910 said:**
> 
PS: Also, might I mention, the Nvidia drivers still load - I'm able to use all the compiz effects etc., just at a stupidly low resolution.

How did you "manually specify" the resolution? I suggest you try as follows. Edit your /etc/X11/xorg.conf, find the section titled "Screen" and add/edit lines as follows```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x960@60"
    EndSubSection
EndSection

```

Note that you need to check if you have more than one "Screen" section; in that case, you need to study it to see which one is suitable, and then knock off (comment out) the other.

Replace the Modes parameters with resolution and refresh rates suitable to your monitor.

---

### Post by phoenix910 on 2009-07-14
> **dlmarti said:**
> did you try the nvidia tool to change the resolution?

/usr/bin/nvidia-settings

[QUOTE=phoenix910]running nvidia-settings to try and change it[/QUOTE]
Yes, I did, thanks anyway :)

For Wim, this is what the Xorg logs said relating to NVIDIA:
```
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.14  Wed May 27 02:32:54 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
(WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
(--) NVIDIA(GPU-0):
(--) NVIDIA(GPU-0): Raw EDID bytes:
(--) NVIDIA(GPU-0):
(--) NVIDIA(GPU-0):   00 ff ff ff ff ff ff 00  04 72 52 ad 5d 05 50 71
(--) NVIDIA(GPU-0):   0f 11 01 03 e8 29 1a 78  2e 4f a5 a4 59 49 99 24
(--) NVIDIA(GPU-0):   12 50 54 a4 ee 00 81 80  81 40 71 4f 95 00 01 01
(--) NVIDIA(GPU-0):   01 01 01 01 01 01 9a 29  a0 d0 51 84 22 30 50 98
(--) NVIDIA(GPU-0):   36 00 98 ff 10 00 00 1c  00 00 00 fd 00 38 4c 1e
(--) NVIDIA(GPU-0):   52 0e 00 0a 20 20 20 20  20 20 00 00 00 fc 00 41
(--) NVIDIA(GPU-0):   63 65 72 20 41 4c 31 39  31 36 57 0a 00 00 00 ff
(--) NVIDIA(GPU-0):   00 4c 35 32 30 39 31 35  38 36 33 35 31 0a 00 14
(--) NVIDIA(GPU-0):
(II) NVIDIA(0): NVIDIA GPU GeForce 8600 GT (G84) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 60.84.35.00.11
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600 GT at PCI:1:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0):
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0):
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device DFP-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from DFP-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled

```


@prshah - Thanks, but yes, have already done that this way, and with a modeline generating tool; neither of them worked :(

Now, after trying many things, I have set my Xorg.conf back to what it was. This is how it looks:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed May 27 03:15:36 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
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
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
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
    EndSubSection
EndSection

```

Thanks all

PS: Running Ubuntu 9.04


EDIT:
So, turns out that I booted up the Live Disc, and it still didn't work, so it obviously wasn't my config. Then booted up BackTrack, and had a little bit more verbose output, which was nice - didn't find any screen on any port. So, I swapped my DVI cable for a VGA cable on a DVI convertor on the same port, and works fine now. Thanks anyway guys :)

---

