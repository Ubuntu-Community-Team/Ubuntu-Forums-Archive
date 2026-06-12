---
title: "VirtualBox: WinXP Host: Ubuntu 9.04 Guest: Terrible 3D Acceleration"
date: 2009-09-02
forum: General Help
---

### Post by cdoran06093 on 2009-09-02
VirtualBox 3.0.4
Host: WinXP Pro SP3, nVidia GeForce Go 7900GTX 512MB RAM
Guest: Ubuntu 9.04

I'm currently experiencing terrible performance when using anything other than the "No Effects".  I've installed Guest Additions, which allowed my resolution to change, but the 3d acceleration is still terrible.
[FONT=Courier New]
/etc/X11/xorg.conf[/FONT] is this.  I added the Driver line based on [this post]("http://tombuntu.com/index.php/2008/09/22/install-virtualbox-2-guest-additions-in-ubuntu/"), but to no avail.

[FONT=Courier New]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vboxvideo"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/FONT]

[FONT=Arial]Any ideas?[/FONT]

---

### Post by cdoran06093 on 2009-09-02
For whatever it's worth, here are the video driver contents of [FONT=Courier New]Xorg.0.log


[/FONT][FONT=Courier New](II) LoadModule: "vboxvideo"
(II) Loading /usr/lib/xorg/modules/drivers//vboxvideo_drv.so
(II) Module vboxvideo: vendor="Sun Microsystems, Inc."
    compiled for 1.5.99.901, module version = 1.0.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(**) Load address of symbol "VBOXVIDEO" is 0xb79d62c0
(II) VBoxVideo: guest driver for VirtualBox: vbox
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) VBoxVideo(0): VirtualBox guest additions video driver version 3.0.4
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) VBoxVideo(0): initializing int10
(II) VBoxVideo(0): Primary V_BIOS segment is: 0xc000
(II) VBoxVideo(0): VESA BIOS detected
(II) VBoxVideo(0): VESA VBE Version 2.0
(II) VBoxVideo(0): VESA VBE Total Mem: 131072 kB
(II) VBoxVideo(0): VESA VBE OEM: VirtualBox VBE BIOS [http://www.virtualbox.org/](http://www.virtualbox.org/)
(II) VBoxVideo(0): VESA VBE OEM Software Rev: 0.2
(II) VBoxVideo(0): VESA VBE OEM Vendor: Sun Microsystems, Inc.
(II) VBoxVideo(0): VESA VBE OEM Product: VirtualBox VBE Adapter
(II) VBoxVideo(0): VESA VBE OEM Product Rev: Sun VirtualBox Version 3.0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) VBoxVideo(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) VBoxVideo(0): Depth 24, (--) framebuffer bpp 32
(II) VBoxVideo(0): Output VBOX1 using monitor section Configured Monitor
(II) VBoxVideo(0): Output VBOX1 has no monitor section
(II) VBoxVideo(0): Output VBOX1 connected
(II) VBoxVideo(0): Using exact sizes for initial modes
(II) VBoxVideo(0): Output VBOX1 using initial mode 1920x1200
(==) VBoxVideo(0): RGB weight 888
(==) VBoxVideo(0): Default visual is TrueColor
(==) VBoxVideo(0): Using gamma correction (1.0, 1.0, 1.0)
(==) VBoxVideo(0): DPI set to (96, 96)
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(==) VBoxVideo(0): Default visual is TrueColor
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) VBoxVideo(0): [drm] Using the DRM lock SAREA also for drawables.
(II) VBoxVideo(0): [drm] framebuffer handle = 0xe0000000
(II) VBoxVideo(0): [drm] added 1 reserved context for kernel
(II) VBoxVideo(0): X context handle = 0x1
(II) VBoxVideo(0): [drm] installed DRM signal handler
(II) VBoxVideo(0): visual configurations initialized
(==) VBoxVideo(0): Backing store disabled
(II) VBoxVideo(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) VBoxVideo(0): DPMS enabled
(II) VBoxVideo(0): The VBox video extensions are now enabled.
(II) VBoxVideo(0): [DRI] installation complete
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 12, (OK)
drmOpenByBusid: drmOpenMinor returns 12
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) Next line is added to allow vboxvideo_drv.so to appear as whitelisted driver
(II) The file referenced, is *NOT* loaded
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(EE) AIGLX error: vboxvideo does not export required DRI extension
(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) VBoxVideo(0): Setting screen physical size to 507 x 317
(II) config/hal: Adding input device AT Translated Set 2 keyboard[/FONT]

---

