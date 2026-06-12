---
title: "FailsafeX only way to boot into 11.04"
date: 2011-09-18
forum: General Help
---

### Post by Inphernal on 2011-09-18
Hi all,
I've had this problem for a while, and I've been putting off fixing it for too long. My chipset is an Intel Mobile 4 chipset. I had 11.04 working fine, booting normally except off a restart. I don't what I did to make this happen, but now I must go through recovery mode and use the failsafeX option to boot. Everything works completely fine otherwise.
What can I do?

Thank you

---

### Post by varunendra on 2011-09-19
In the recovery menu, choose dpkg (fix broken packages) > then reboot. If this doesn't help, post back the output of:
```
sudo lshw -C display
```

---

### Post by sikander3786 on 2011-09-19
And also, please post the output of this command as well:

```
cat /etc/X11/xorg.conf
```

---

### Post by Inphernal on 2011-09-19
> **varunendra said:**
> In the recovery menu, choose dpkg (fix broken  packages) > then reboot. If this doesn't help, post back the output  of:
```
sudo lshw -C display
```

dpkg does nothing, just read out a bunch of "failed to fetch..."'s and "could not resolve..."'s

```
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:90000000-903fffff memory:80000000-8fffffff ioport:5110(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:93400000-934fffff

```> **sikander3786 said:**
> And also, please post the output of this command as well:

```
cat /etc/X11/xorg.conf
```

```
cat: /etc/X11/xorg.conf: No such file or directory
```

---

### Post by varunendra on 2011-09-20
> **Inphernal said:**
> dpkg does nothing, just read out a bunch of "failed to fetch..."'s and "could not resolve..."'s

Make sure you are connected to internet while using dpkg option.

> **Inphernal said:**
> ```
[COLOR=Red]cat: /etc/X11/xorg.conf[/COLOR]: No such file or directory
``` I don't think xorg.conf is used these days unless it is created manually or by a third party software/driver. If the dpkg option in recovery menu fails again (even with the internet connection), you may try this:
```
dpkg-reconfigure -a
```
but as per my knowledge (which is quite immature), this 'may' work only if there is a configuration error, not a case of broken package.

---

### Post by Inphernal on 2011-09-21
Well I removed and reinstalled xorg and can now boot normally. However, it boots in the same UI as failsafeX mode, and with an unchangeable resolution of 1024x768. When I go into monitors it says "Monitor: Unknown" and will not let me change anything.

---

### Post by realzippy on 2011-09-21
> **Inphernal said:**
> 
I don't what I did to make this happen

..did you (try to) install something?
..did you update your system ?
..add a ppa ?

Show output from

```
xrandr -q
```

---

### Post by Inphernal on 2011-09-21
> **realzippy said:**
> ..did you (try to) install something?
..did you update your system ?
..add a ppa ?

Show output from

```
xrandr -q
```

It was a while ago, so I am not sure, but I think it was an update. Could have been installing something, but definitely not adding a ppa.

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 

```

---

### Post by realzippy on 2011-09-21
post your
```
/var/log/Xorg.0.log
```
file....

---

### Post by Inphernal on 2011-09-22
> **realzippy said:**
> post your
```
/var/log/Xorg.0.log
```file....

```
[    32.517] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    32.517] X Protocol Version 11, Revision 0
[    32.517] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    32.517] Current Operating System: Linux lt1 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64
[    32.517] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=1d38748a-3f98-471d-aef7-488b6aa2036e ro nomodeset
[    32.517] Build Date: 11 August 2011  03:43:05PM
[    32.517] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    32.517] Current version of pixman: 0.20.2
[    32.517]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    32.517] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.517] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 21 23:12:15 2011
[    32.758] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    32.759] (==) No Layout section.  Using the first Screen section.
[    32.759] (==) No screen section available. Using defaults.
[    32.759] (**) |-->Screen "Default Screen Section" (0)
[    32.759] (**) |   |-->Monitor "<default monitor>"
[    32.759] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    32.759] (==) Automatically adding devices
[    32.759] (==) Automatically enabling devices
[    32.759] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    32.759]     Entry deleted from font path.
[    32.759] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    32.759]     Entry deleted from font path.
[    32.759] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    32.759]     Entry deleted from font path.
[    32.759] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    32.759]     Entry deleted from font path.
[    32.759] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    32.759]     Entry deleted from font path.
[    32.759] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    32.759] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    32.759] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    32.759] (II) Loader magic: 0x7e17e0
[    32.759] (II) Module ABI versions:
[    32.759]     X.Org ANSI C Emulation: 0.4
[    32.759]     X.Org Video Driver: 10.0
[    32.759]     X.Org XInput driver : 12.3
[    32.759]     X.Org Server Extension : 5.0
[    32.760] (--) PCI:*(0:0:2:0) 8086:2a42:1179:fde0 rev 7, Mem @ 0x90000000/4194304, 0x80000000/268435456, I/O @ 0x00005110/8
[    32.760] (--) PCI: (0:0:2:1) 8086:2a43:1179:fde0 rev 7, Mem @ 0x93400000/1048576
[    32.761] (II) Open ACPI successful (/var/run/acpid.socket)
[    32.761] (II) LoadModule: "extmod"
[    32.784] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    32.791] (II) Module extmod: vendor="X.Org Foundation"
[    32.791]     compiled for 1.10.1, module version = 1.0.0
[    32.791]     Module class: X.Org Server Extension
[    32.791]     ABI class: X.Org Server Extension, version 5.0
[    32.791] (II) Loading extension MIT-SCREEN-SAVER
[    32.791] (II) Loading extension XFree86-VidModeExtension
[    32.791] (II) Loading extension XFree86-DGA
[    32.791] (II) Loading extension DPMS
[    32.791] (II) Loading extension XVideo
[    32.791] (II) Loading extension XVideo-MotionCompensation
[    32.791] (II) Loading extension X-Resource
[    32.791] (II) LoadModule: "dbe"
[    32.791] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    32.791] (II) Module dbe: vendor="X.Org Foundation"
[    32.791]     compiled for 1.10.1, module version = 1.0.0
[    32.791]     Module class: X.Org Server Extension
[    32.791]     ABI class: X.Org Server Extension, version 5.0
[    32.791] (II) Loading extension DOUBLE-BUFFER
[    32.791] (II) LoadModule: "glx"
[    32.791] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    32.791] (II) Module glx: vendor="X.Org Foundation"
[    32.791]     compiled for 1.10.1, module version = 1.0.0
[    32.791]     ABI class: X.Org Server Extension, version 5.0
[    32.791] (==) AIGLX enabled
[    32.791] (II) Loading extension GLX
[    32.791] (II) LoadModule: "record"
[    32.792] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    32.792] (II) Module record: vendor="X.Org Foundation"
[    32.792]     compiled for 1.10.1, module version = 1.13.0
[    32.792]     Module class: X.Org Server Extension
[    32.792]     ABI class: X.Org Server Extension, version 5.0
[    32.792] (II) Loading extension RECORD
[    32.792] (II) LoadModule: "dri"
[    32.792] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    32.792] (II) Module dri: vendor="X.Org Foundation"
[    32.792]     compiled for 1.10.1, module version = 1.0.0
[    32.792]     ABI class: X.Org Server Extension, version 5.0
[    32.792] (II) Loading extension XFree86-DRI
[    32.792] (II) LoadModule: "dri2"
[    32.793] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    32.793] (II) Module dri2: vendor="X.Org Foundation"
[    32.793]     compiled for 1.10.1, module version = 1.2.0
[    32.793]     ABI class: X.Org Server Extension, version 5.0
[    32.793] (II) Loading extension DRI2
[    32.793] (==) Matched intel as autoconfigured driver 0
[    32.793] (==) Matched vesa as autoconfigured driver 1
[    32.793] (==) Matched fbdev as autoconfigured driver 2
[    32.793] (==) Assigned the driver to the xf86ConfigLayout
[    32.793] (II) LoadModule: "intel"
[    32.793] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    32.793] (II) Module intel: vendor="X.Org Foundation"
[    32.793]     compiled for 1.10.1, module version = 2.14.0
[    32.793]     Module class: X.Org Video Driver
[    32.793]     ABI class: X.Org Video Driver, version 10.0
[    32.793] (II) LoadModule: "vesa"
[    32.793] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.793] (II) Module vesa: vendor="X.Org Foundation"
[    32.793]     compiled for 1.10.0, module version = 2.3.0
[    32.793]     Module class: X.Org Video Driver
[    32.793]     ABI class: X.Org Video Driver, version 10.0
[    32.793] (II) LoadModule: "fbdev"
[    32.794] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    32.794] (II) Module fbdev: vendor="X.Org Foundation"
[    32.794]     compiled for 1.10.0, module version = 0.4.2
[    32.794]     ABI class: X.Org Video Driver, version 10.0
[    32.794] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    32.794] (II) VESA: driver for VESA chipsets: vesa
[    32.794] (II) FBDEV: driver for framebuffer: fbdev
[    32.794] (++) using VT number 7

[    32.797] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    32.797] (WW) Falling back to old probe method for fbdev
[    32.797] (II) Loading sub module "fbdevhw"
[    32.797] (II) LoadModule: "fbdevhw"
[    32.839] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    32.839] (II) Module fbdevhw: vendor="X.Org Foundation"
[    32.840]     compiled for 1.10.1, module version = 0.0.2
[    32.840]     ABI class: X.Org Video Driver, version 10.0
[    32.840] (EE) open /dev/fb0: No such file or directory
[    32.840] (II) Loading sub module "vbe"
[    32.840] (II) LoadModule: "vbe"
[    32.840] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    32.840] (II) Module vbe: vendor="X.Org Foundation"
[    32.840]     compiled for 1.10.1, module version = 1.1.0
[    32.840]     ABI class: X.Org Video Driver, version 10.0
[    32.840] (II) Loading sub module "int10"
[    32.840] (II) LoadModule: "int10"
[    32.840] (II) Loading /usr/lib/xorg/modules/libint10.so
[    32.840] (II) Module int10: vendor="X.Org Foundation"
[    32.840]     compiled for 1.10.1, module version = 1.0.0
[    32.840]     ABI class: X.Org Video Driver, version 10.0
[    32.840] (II) VESA(0): initializing int10
[    32.841] (II) VESA(0): Bad V_BIOS checksum
[    32.841] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    32.841] (II) VESA(0): VESA BIOS detected
[    32.841] (II) VESA(0): VESA VBE Version 3.0
[    32.841] (II) VESA(0): VESA VBE Total Mem: 131008 kB
[    32.841] (II) VESA(0): VESA VBE OEM: Intel(R)Cantiga Graphics Chipset Accelerated VGA BIOS
[    32.841] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    32.841] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    32.841] (II) VESA(0): VESA VBE OEM Product: Intel(R)Cantiga Graphics Controller
[    32.841] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    32.847] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    32.847] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    32.847] (==) VESA(0): RGB weight 888
[    32.847] (==) VESA(0): Default visual is TrueColor
[    32.847] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.847] (II) Loading sub module "ddc"
[    32.847] (II) LoadModule: "ddc"
[    32.847] (II) Module "ddc" already built-in
[    32.847] (II) VESA(0): VESA VBE DDC supported
[    32.847] (II) VESA(0): VESA VBE DDC Level 2
[    32.847] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    32.860] (II) VESA(0): VESA VBE DDC read successfully
[    32.860] (II) VESA(0): Manufacturer: LGD  Model: 230  Serial#: 0
[    32.860] (II) VESA(0): Year: 2009  Week: 0
[    32.860] (II) VESA(0): EDID Version: 1.3
[    32.860] (II) VESA(0): Digital Display Input
[    32.860] (II) VESA(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    32.860] (II) VESA(0): Gamma: 2.20
[    32.860] (II) VESA(0): No DPMS capabilities specified
[    32.860] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    32.860] (II) VESA(0): First detailed timing is preferred mode
[    32.860] (II) VESA(0): redX: 0.622 redY: 0.365   greenX: 0.340 greenY: 0.607
[    32.860] (II) VESA(0): blueX: 0.145 blueY: 0.100   whiteX: 0.313 whiteY: 0.329
[    32.860] (II) VESA(0): Manufacturer's mask: 0
[    32.860] (II) VESA(0): Supported detailed timing:
[    32.860] (II) VESA(0): clock: 72.3 MHz   Image Size:  344 x 194 mm
[    32.860] (II) VESA(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[    32.860] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    32.860] (II) VESA(0):  LG Display
[    32.860] (II) VESA(0): Monitor name: LP156WH2-TLAA
[    32.860] (II) VESA(0): EDID (in hex):
[    32.860] (II) VESA(0):     00ffffffffffff0030e4300200000000
[    32.860] (II) VESA(0):     00130103802213780a62259f5d579b25
[    32.860] (II) VESA(0):     19505400000001010101010101010101
[    32.860] (II) VESA(0):     0101010101013e1c56a0500016303020
[    32.860] (II) VESA(0):     350058c2100000190000000000000000
[    32.860] (II) VESA(0):     00000000000000000000000000fe004c
[    32.860] (II) VESA(0):     4720446973706c61790a2020000000fc
[    32.860] (II) VESA(0):     004c503135365748322d544c41410038
[    32.860] (II) VESA(0): EDID vendor "LGD", prod id 560
[    32.860] (II) VESA(0): Printing DDC gathered Modelines:
[    32.860] (II) VESA(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    32.860] (II) VESA(0): Searching for matching VESA mode(s):
[    32.860] Mode: 160 (0x0)
[    32.860]     ModeAttributes: 0x0
[    32.860]     WinAAttributes: 0x0
[    32.860]     WinBAttributes: 0x0
[    32.860]     WinGranularity: 0
[    32.860]     WinSize: 0
[    32.860]     WinASegment: 0x0
[    32.860]     WinBSegment: 0x0
[    32.860]     WinFuncPtr: 0x0
[    32.860]     BytesPerScanline: 0
[    32.860]     XResolution: 0
[    32.860]     YResolution: 0
[    32.860]     XCharSize: 0
[    32.860]     YCharSize: 0
[    32.860]     NumberOfPlanes: 0
[    32.860]     BitsPerPixel: 0
[    32.860]     NumberOfBanks: 0
[    32.860]     MemoryModel: 0
[    32.860]     BankSize: 0
[    32.860]     NumberOfImages: 0
[    32.860]     RedMaskSize: 0
[    32.860]     RedFieldPosition: 0
[    32.860]     GreenMaskSize: 0
[    32.860]     GreenFieldPosition: 0
[    32.860]     BlueMaskSize: 0
[    32.860]     BlueFieldPosition: 0
[    32.860]     RsvdMaskSize: 0
[    32.860]     RsvdFieldPosition: 0
[    32.860]     DirectColorModeInfo: 0
[    32.860]     PhysBasePtr: 0x0
[    32.860]     LinBytesPerScanLine: 0
[    32.860]     BnkNumberOfImagePages: 0
[    32.860]     LinNumberOfImagePages: 0
[    32.860]     LinRedMaskSize: 0
[    32.860]     LinRedFieldPosition: 0
[    32.860]     LinGreenMaskSize: 0
[    32.860]     LinGreenFieldPosition: 0
[    32.860]     LinBlueMaskSize: 0
[    32.860]     LinBlueFieldPosition: 0
[    32.861]     LinRsvdMaskSize: 0
[    32.861]     LinRsvdFieldPosition: 0
[    32.861]     MaxPixelClock: 0
[    32.861] Mode: 161 (0x0)
[    32.861]     ModeAttributes: 0x0
[    32.861]     WinAAttributes: 0x0
[    32.861]     WinBAttributes: 0x0
[    32.861]     WinGranularity: 0
[    32.861]     WinSize: 0
[    32.861]     WinASegment: 0x0
[    32.861]     WinBSegment: 0x0
[    32.861]     WinFuncPtr: 0x0
[    32.861]     BytesPerScanline: 0
[    32.861]     XResolution: 0
[    32.861]     YResolution: 0
[    32.861]     XCharSize: 0
[    32.861]     YCharSize: 0
[    32.861]     NumberOfPlanes: 0
[    32.861]     BitsPerPixel: 0
[    32.861]     NumberOfBanks: 0
[    32.861]     MemoryModel: 0
[    32.861]     BankSize: 0
[    32.861]     NumberOfImages: 0
[    32.861]     RedMaskSize: 0
[    32.861]     RedFieldPosition: 0
[    32.861]     GreenMaskSize: 0
[    32.861]     GreenFieldPosition: 0
[    32.861]     BlueMaskSize: 0
[    32.861]     BlueFieldPosition: 0
[    32.861]     RsvdMaskSize: 0
[    32.861]     RsvdFieldPosition: 0
[    32.861]     DirectColorModeInfo: 0
[    32.861]     PhysBasePtr: 0x0
[    32.861]     LinBytesPerScanLine: 0
[    32.861]     BnkNumberOfImagePages: 0
[    32.861]     LinNumberOfImagePages: 0
[    32.861]     LinRedMaskSize: 0
[    32.861]     LinRedFieldPosition: 0
[    32.861]     LinGreenMaskSize: 0
[    32.861]     LinGreenFieldPosition: 0
[    32.861]     LinBlueMaskSize: 0
[    32.861]     LinBlueFieldPosition: 0
[    32.861]     LinRsvdMaskSize: 0
[    32.861]     LinRsvdFieldPosition: 0
[    32.861]     MaxPixelClock: 0
[    32.861] Mode: 162 (0x0)
[    32.861]     ModeAttributes: 0x0
[    32.861]     WinAAttributes: 0x0
[    32.861]     WinBAttributes: 0x0
[    32.861]     WinGranularity: 0
[    32.861]     WinSize: 0
[    32.861]     WinASegment: 0x0
[    32.861]     WinBSegment: 0x0
[    32.861]     WinFuncPtr: 0x0
[    32.861]     BytesPerScanline: 0
[    32.861]     XResolution: 0
[    32.861]     YResolution: 0
[    32.861]     XCharSize: 0
[    32.861]     YCharSize: 0
[    32.861]     NumberOfPlanes: 0
[    32.861]     BitsPerPixel: 0
[    32.861]     NumberOfBanks: 0
[    32.861]     MemoryModel: 0
[    32.861]     BankSize: 0
[    32.861]     NumberOfImages: 0
[    32.861]     RedMaskSize: 0
[    32.861]     RedFieldPosition: 0
[    32.861]     GreenMaskSize: 0
[    32.861]     GreenFieldPosition: 0
[    32.861]     BlueMaskSize: 0
[    32.861]     BlueFieldPosition: 0
[    32.861]     RsvdMaskSize: 0
[    32.861]     RsvdFieldPosition: 0
[    32.861]     DirectColorModeInfo: 0
[    32.861]     PhysBasePtr: 0x0
[    32.861]     LinBytesPerScanLine: 0
[    32.861]     BnkNumberOfImagePages: 0
[    32.861]     LinNumberOfImagePages: 0
[    32.861]     LinRedMaskSize: 0
[    32.861]     LinRedFieldPosition: 0
[    32.861]     LinGreenMaskSize: 0
[    32.861]     LinGreenFieldPosition: 0
[    32.861]     LinBlueMaskSize: 0
[    32.861]     LinBlueFieldPosition: 0
[    32.861]     LinRsvdMaskSize: 0
[    32.861]     LinRsvdFieldPosition: 0
[    32.861]     MaxPixelClock: 0
[    32.861] Mode: 163 (0x0)
[    32.861]     ModeAttributes: 0x0
[    32.861]     WinAAttributes: 0x0
[    32.861]     WinBAttributes: 0x0
[    32.861]     WinGranularity: 0
[    32.861]     WinSize: 0
[    32.861]     WinASegment: 0x0
[    32.861]     WinBSegment: 0x0
[    32.861]     WinFuncPtr: 0x0
[    32.861]     BytesPerScanline: 0
[    32.861]     XResolution: 0
[    32.861]     YResolution: 0
[    32.861]     XCharSize: 0
[    32.861]     YCharSize: 0
[    32.861]     NumberOfPlanes: 0
[    32.861]     BitsPerPixel: 0
[    32.861]     NumberOfBanks: 0
[    32.861]     MemoryModel: 0
[    32.861]     BankSize: 0
[    32.861]     NumberOfImages: 0
[    32.861]     RedMaskSize: 0
[    32.862]     RedFieldPosition: 0
[    32.862]     GreenMaskSize: 0
[    32.862]     GreenFieldPosition: 0
[    32.862]     BlueMaskSize: 0
[    32.862]     BlueFieldPosition: 0
[    32.862]     RsvdMaskSize: 0
[    32.862]     RsvdFieldPosition: 0
[    32.862]     DirectColorModeInfo: 0
[    32.862]     PhysBasePtr: 0x0
[    32.862]     LinBytesPerScanLine: 0
[    32.862]     BnkNumberOfImagePages: 0
[    32.862]     LinNumberOfImagePages: 0
[    32.862]     LinRedMaskSize: 0
[    32.862]     LinRedFieldPosition: 0
[    32.862]     LinGreenMaskSize: 0
[    32.862]     LinGreenFieldPosition: 0
[    32.862]     LinBlueMaskSize: 0
[    32.862]     LinBlueFieldPosition: 0
[    32.862]     LinRsvdMaskSize: 0
[    32.862]     LinRsvdFieldPosition: 0
[    32.862]     MaxPixelClock: 0
[    32.862] Mode: 164 (0x0)
[    32.862]     ModeAttributes: 0x0
[    32.862]     WinAAttributes: 0x0
[    32.862]     WinBAttributes: 0x0
[    32.862]     WinGranularity: 0
[    32.862]     WinSize: 0
[    32.862]     WinASegment: 0x0
[    32.862]     WinBSegment: 0x0
[    32.862]     WinFuncPtr: 0x0
[    32.862]     BytesPerScanline: 0
[    32.862]     XResolution: 0
[    32.862]     YResolution: 0
[    32.862]     XCharSize: 0
[    32.862]     YCharSize: 0
[    32.862]     NumberOfPlanes: 0
[    32.862]     BitsPerPixel: 0
[    32.862]     NumberOfBanks: 0
[    32.862]     MemoryModel: 0
[    32.862]     BankSize: 0
[    32.862]     NumberOfImages: 0
[    32.862]     RedMaskSize: 0
[    32.862]     RedFieldPosition: 0
[    32.862]     GreenMaskSize: 0
[    32.862]     GreenFieldPosition: 0
[    32.862]     BlueMaskSize: 0
[    32.862]     BlueFieldPosition: 0
[    32.862]     RsvdMaskSize: 0
[    32.862]     RsvdFieldPosition: 0
[    32.862]     DirectColorModeInfo: 0
[    32.862]     PhysBasePtr: 0x0
[    32.862]     LinBytesPerScanLine: 0
[    32.862]     BnkNumberOfImagePages: 0
[    32.862]     LinNumberOfImagePages: 0
[    32.862]     LinRedMaskSize: 0
[    32.862]     LinRedFieldPosition: 0
[    32.862]     LinGreenMaskSize: 0
[    32.862]     LinGreenFieldPosition: 0
[    32.862]     LinBlueMaskSize: 0
[    32.862]     LinBlueFieldPosition: 0
[    32.862]     LinRsvdMaskSize: 0
[    32.862]     LinRsvdFieldPosition: 0
[    32.862]     MaxPixelClock: 0
[    32.862] Mode: 165 (0x0)
[    32.863]     ModeAttributes: 0x0
[    32.863]     WinAAttributes: 0x0
[    32.863]     WinBAttributes: 0x0
[    32.863]     WinGranularity: 0
[    32.863]     WinSize: 0
[    32.863]     WinASegment: 0x0
[    32.863]     WinBSegment: 0x0
[    32.863]     WinFuncPtr: 0x0
[    32.863]     BytesPerScanline: 0
[    32.863]     XResolution: 0
[    32.863]     YResolution: 0
[    32.863]     XCharSize: 0
[    32.863]     YCharSize: 0
[    32.863]     NumberOfPlanes: 0
[    32.863]     BitsPerPixel: 0
[    32.863]     NumberOfBanks: 0
[    32.863]     MemoryModel: 0
[    32.863]     BankSize: 0
[    32.863]     NumberOfImages: 0
[    32.863]     RedMaskSize: 0
[    32.863]     RedFieldPosition: 0
[    32.863]     GreenMaskSize: 0
[    32.863]     GreenFieldPosition: 0
[    32.863]     BlueMaskSize: 0
[    32.863]     BlueFieldPosition: 0
[    32.863]     RsvdMaskSize: 0
[    32.863]     RsvdFieldPosition: 0
[    32.863]     DirectColorModeInfo: 0
[    32.863]     PhysBasePtr: 0x0
[    32.863]     LinBytesPerScanLine: 0
[    32.863]     BnkNumberOfImagePages: 0
[    32.863]     LinNumberOfImagePages: 0
[    32.863]     LinRedMaskSize: 0
[    32.863]     LinRedFieldPosition: 0
[    32.863]     LinGreenMaskSize: 0
[    32.863]     LinGreenFieldPosition: 0
[    32.863]     LinBlueMaskSize: 0
[    32.863]     LinBlueFieldPosition: 0
[    32.863]     LinRsvdMaskSize: 0
[    32.863]     LinRsvdFieldPosition: 0
[    32.863]     MaxPixelClock: 0
[    32.863] Mode: 166 (0x0)
[    32.863]     ModeAttributes: 0x0
[    32.863]     WinAAttributes: 0x0
[    32.863]     WinBAttributes: 0x0
[    32.863]     WinGranularity: 0
[    32.863]     WinSize: 0
[    32.863]     WinASegment: 0x0
[    32.863]     WinBSegment: 0x0
[    32.863]     WinFuncPtr: 0x0
[    32.863]     BytesPerScanline: 0
[    32.863]     XResolution: 0
[    32.863]     YResolution: 0
[    32.863]     XCharSize: 0
[    32.863]     YCharSize: 0
[    32.863]     NumberOfPlanes: 0
[    32.863]     BitsPerPixel: 0
[    32.863]     NumberOfBanks: 0
[    32.863]     MemoryModel: 0
[    32.863]     BankSize: 0
[    32.863]     NumberOfImages: 0
[    32.863]     RedMaskSize: 0
[    32.863]     RedFieldPosition: 0
[    32.863]     GreenMaskSize: 0
[    32.863]     GreenFieldPosition: 0
[    32.863]     BlueMaskSize: 0
[    32.863]     BlueFieldPosition: 0
[    32.863]     RsvdMaskSize: 0
[    32.863]     RsvdFieldPosition: 0
[    32.863]     DirectColorModeInfo: 0
[    32.863]     PhysBasePtr: 0x0
[    32.863]     LinBytesPerScanLine: 0
[    32.863]     BnkNumberOfImagePages: 0
[    32.863]     LinNumberOfImagePages: 0
[    32.863]     LinRedMaskSize: 0
[    32.863]     LinRedFieldPosition: 0
[    32.863]     LinGreenMaskSize: 0
[    32.863]     LinGreenFieldPosition: 0
[    32.863]     LinBlueMaskSize: 0
[    32.863]     LinBlueFieldPosition: 0
[    32.863]     LinRsvdMaskSize: 0
[    32.863]     LinRsvdFieldPosition: 0
[    32.863]     MaxPixelClock: 0
[    32.863] Mode: 167 (0x0)
[    32.863]     ModeAttributes: 0x0
[    32.863]     WinAAttributes: 0x0
[    32.863]     WinBAttributes: 0x0
[    32.863]     WinGranularity: 0
[    32.863]     WinSize: 0
[    32.863]     WinASegment: 0x0
[    32.863]     WinBSegment: 0x0
[    32.863]     WinFuncPtr: 0x0
[    32.863]     BytesPerScanline: 0
[    32.863]     XResolution: 0
[    32.863]     YResolution: 0
[    32.863]     XCharSize: 0
[    32.863]     YCharSize: 0
[    32.863]     NumberOfPlanes: 0
[    32.863]     BitsPerPixel: 0
[    32.863]     NumberOfBanks: 0
[    32.863]     MemoryModel: 0
[    32.863]     BankSize: 0
[    32.863]     NumberOfImages: 0
[    32.863]     RedMaskSize: 0
[    32.863]     RedFieldPosition: 0
[    32.863]     GreenMaskSize: 0
[    32.863]     GreenFieldPosition: 0
[    32.863]     BlueMaskSize: 0
[    32.863]     BlueFieldPosition: 0
[    32.863]     RsvdMaskSize: 0
[    32.863]     RsvdFieldPosition: 0
[    32.863]     DirectColorModeInfo: 0
[    32.863]     PhysBasePtr: 0x0
[    32.863]     LinBytesPerScanLine: 0
[    32.863]     BnkNumberOfImagePages: 0
[    32.863]     LinNumberOfImagePages: 0
[    32.863]     LinRedMaskSize: 0
[    32.863]     LinRedFieldPosition: 0
[    32.863]     LinGreenMaskSize: 0
[    32.863]     LinGreenFieldPosition: 0
[    32.863]     LinBlueMaskSize: 0
[    32.863]     LinBlueFieldPosition: 0
[    32.863]     LinRsvdMaskSize: 0
[    32.864]     LinRsvdFieldPosition: 0
[    32.864]     MaxPixelClock: 0
[    32.864] Mode: 168 (0x0)
[    32.864]     ModeAttributes: 0x0
[    32.864]     WinAAttributes: 0x0
[    32.864]     WinBAttributes: 0x0
[    32.864]     WinGranularity: 0
[    32.864]     WinSize: 0
[    32.864]     WinASegment: 0x0
[    32.864]     WinBSegment: 0x0
[    32.864]     WinFuncPtr: 0x0
[    32.864]     BytesPerScanline: 0
[    32.864]     XResolution: 0
[    32.864]     YResolution: 0
[    32.864]     XCharSize: 0
[    32.864]     YCharSize: 0
[    32.864]     NumberOfPlanes: 0
[    32.864]     BitsPerPixel: 0
[    32.864]     NumberOfBanks: 0
[    32.864]     MemoryModel: 0
[    32.864]     BankSize: 0
[    32.864]     NumberOfImages: 0
[    32.864]     RedMaskSize: 0
[    32.864]     RedFieldPosition: 0
[    32.864]     GreenMaskSize: 0
[    32.864]     GreenFieldPosition: 0
[    32.864]     BlueMaskSize: 0
[    32.864]     BlueFieldPosition: 0
[    32.864]     RsvdMaskSize: 0
[    32.864]     RsvdFieldPosition: 0
[    32.864]     DirectColorModeInfo: 0
[    32.864]     PhysBasePtr: 0x0
[    32.864]     LinBytesPerScanLine: 0
[    32.864]     BnkNumberOfImagePages: 0
[    32.864]     LinNumberOfImagePages: 0
[    32.864]     LinRedMaskSize: 0
[    32.864]     LinRedFieldPosition: 0
[    32.864]     LinGreenMaskSize: 0
[    32.864]     LinGreenFieldPosition: 0
[    32.864]     LinBlueMaskSize: 0
[    32.864]     LinBlueFieldPosition: 0
[    32.864]     LinRsvdMaskSize: 0
[    32.864]     LinRsvdFieldPosition: 0
[    32.864]     MaxPixelClock: 0
[    32.864] Mode: 169 (0x0)
[    32.864]     ModeAttributes: 0x0
[    32.864]     WinAAttributes: 0x0
[    32.864]     WinBAttributes: 0x0
[    32.864]     WinGranularity: 0
[    32.864]     WinSize: 0
[    32.864]     WinASegment: 0x0
[    32.864]     WinBSegment: 0x0
[    32.864]     WinFuncPtr: 0x0
[    32.864]     BytesPerScanline: 0
[    32.864]     XResolution: 0
[    32.864]     YResolution: 0
[    32.864]     XCharSize: 0
[    32.864]     YCharSize: 0
[    32.864]     NumberOfPlanes: 0
[    32.864]     BitsPerPixel: 0
[    32.864]     NumberOfBanks: 0
[    32.864]     MemoryModel: 0
[    32.864]     BankSize: 0
[    32.864]     NumberOfImages: 0
[    32.864]     RedMaskSize: 0
[    32.864]     RedFieldPosition: 0
[    32.864]     GreenMaskSize: 0
[    32.864]     GreenFieldPosition: 0
[    32.864]     BlueMaskSize: 0
[    32.864]     BlueFieldPosition: 0
[    32.864]     RsvdMaskSize: 0
[    32.864]     RsvdFieldPosition: 0
[    32.864]     DirectColorModeInfo: 0
[    32.864]     PhysBasePtr: 0x0
[    32.864]     LinBytesPerScanLine: 0
[    32.864]     BnkNumberOfImagePages: 0
[    32.864]     LinNumberOfImagePages: 0
[    32.864]     LinRedMaskSize: 0
[    32.864]     LinRedFieldPosition: 0
[    32.864]     LinGreenMaskSize: 0
[    32.864]     LinGreenFieldPosition: 0
[    32.864]     LinBlueMaskSize: 0
[    32.864]     LinBlueFieldPosition: 0
[    32.864]     LinRsvdMaskSize: 0
[    32.864]     LinRsvdFieldPosition: 0
[    32.864]     MaxPixelClock: 0
[    32.864] Mode: 16a (0x0)
[    32.864]     ModeAttributes: 0x0
[    32.864]     WinAAttributes: 0x0
[    32.864]     WinBAttributes: 0x0
[    32.864]     WinGranularity: 0
[    32.864]     WinSize: 0
[    32.864]     WinASegment: 0x0
[    32.864]     WinBSegment: 0x0
[    32.864]     WinFuncPtr: 0x0
[    32.864]     BytesPerScanline: 0
[    32.864]     XResolution: 0
[    32.864]     YResolution: 0
[    32.864]     XCharSize: 0
[    32.864]     YCharSize: 0
[    32.864]     NumberOfPlanes: 0
[    32.864]     BitsPerPixel: 0
[    32.864]     NumberOfBanks: 0
[    32.864]     MemoryModel: 0
[    32.864]     BankSize: 0
[    32.864]     NumberOfImages: 0
[    32.864]     RedMaskSize: 0
[    32.864]     RedFieldPosition: 0
[    32.865]     GreenMaskSize: 0
[    32.865]     GreenFieldPosition: 0
[    32.865]     BlueMaskSize: 0
[    32.865]     BlueFieldPosition: 0
[    32.865]     RsvdMaskSize: 0
[    32.865]     RsvdFieldPosition: 0
[    32.865]     DirectColorModeInfo: 0
[    32.865]     PhysBasePtr: 0x0
[    32.865]     LinBytesPerScanLine: 0
[    32.865]     BnkNumberOfImagePages: 0
[    32.865]     LinNumberOfImagePages: 0
[    32.865]     LinRedMaskSize: 0
[    32.865]     LinRedFieldPosition: 0
[    32.865]     LinGreenMaskSize: 0
[    32.865]     LinGreenFieldPosition: 0
[    32.865]     LinBlueMaskSize: 0
[    32.865]     LinBlueFieldPosition: 0
[    32.865]     LinRsvdMaskSize: 0
[    32.865]     LinRsvdFieldPosition: 0
[    32.865]     MaxPixelClock: 0
[    32.865] Mode: 16b (0x0)
[    32.865]     ModeAttributes: 0x0
[    32.865]     WinAAttributes: 0x0
[    32.865]     WinBAttributes: 0x0
[    32.865]     WinGranularity: 0
[    32.865]     WinSize: 0
[    32.865]     WinASegment: 0x0
[    32.865]     WinBSegment: 0x0
[    32.865]     WinFuncPtr: 0x0
[    32.865]     BytesPerScanline: 0
[    32.865]     XResolution: 0
[    32.865]     YResolution: 0
[    32.865]     XCharSize: 0
[    32.865]     YCharSize: 0
[    32.865]     NumberOfPlanes: 0
[    32.865]     BitsPerPixel: 0
[    32.865]     NumberOfBanks: 0
[    32.865]     MemoryModel: 0
[    32.865]     BankSize: 0
[    32.865]     NumberOfImages: 0
[    32.865]     RedMaskSize: 0
[    32.865]     RedFieldPosition: 0
[    32.865]     GreenMaskSize: 0
[    32.865]     GreenFieldPosition: 0
[    32.865]     BlueMaskSize: 0
[    32.865]     BlueFieldPosition: 0
[    32.865]     RsvdMaskSize: 0
[    32.865]     RsvdFieldPosition: 0
[    32.865]     DirectColorModeInfo: 0
[    32.865]     PhysBasePtr: 0x0
[    32.865]     LinBytesPerScanLine: 0
[    32.865]     BnkNumberOfImagePages: 0
[    32.865]     LinNumberOfImagePages: 0
[    32.865]     LinRedMaskSize: 0
[    32.865]     LinRedFieldPosition: 0
[    32.865]     LinGreenMaskSize: 0
[    32.865]     LinGreenFieldPosition: 0
[    32.865]     LinBlueMaskSize: 0
[    32.865]     LinBlueFieldPosition: 0
[    32.865]     LinRsvdMaskSize: 0
[    32.865]     LinRsvdFieldPosition: 0
[    32.865]     MaxPixelClock: 0
[    32.865] Mode: 16c (0x0)
[    32.865]     ModeAttributes: 0x0
[    32.865]     WinAAttributes: 0x0
[    32.865]     WinBAttributes: 0x0
[    32.865]     WinGranularity: 0
[    32.865]     WinSize: 0
[    32.865]     WinASegment: 0x0
[    32.865]     WinBSegment: 0x0
[    32.865]     WinFuncPtr: 0x0
[    32.865]     BytesPerScanline: 0
[    32.865]     XResolution: 0
[    32.865]     YResolution: 0
[    32.865]     XCharSize: 0
[    32.865]     YCharSize: 0
[    32.865]     NumberOfPlanes: 0
[    32.865]     BitsPerPixel: 0
[    32.865]     NumberOfBanks: 0
[    32.865]     MemoryModel: 0
[    32.865]     BankSize: 0
[    32.865]     NumberOfImages: 0
[    32.865]     RedMaskSize: 0
[    32.865]     RedFieldPosition: 0
[    32.865]     GreenMaskSize: 0
[    32.865]     GreenFieldPosition: 0
[    32.865]     BlueMaskSize: 0
[    32.865]     BlueFieldPosition: 0
[    32.865]     RsvdMaskSize: 0
[    32.865]     RsvdFieldPosition: 0
[    32.865]     DirectColorModeInfo: 0
[    32.865]     PhysBasePtr: 0x0
[    32.865]     LinBytesPerScanLine: 0
[    32.865]     BnkNumberOfImagePages: 0
[    32.865]     LinNumberOfImagePages: 0
[    32.865]     LinRedMaskSize: 0
[    32.865]     LinRedFieldPosition: 0
[    32.865]     LinGreenMaskSize: 0
[    32.865]     LinGreenFieldPosition: 0
[    32.865]     LinBlueMaskSize: 0
[    32.865]     LinBlueFieldPosition: 0
[    32.865]     LinRsvdMaskSize: 0
[    32.865]     LinRsvdFieldPosition: 0
[    32.865]     MaxPixelClock: 0
[    32.865] Mode: 16d (0x0)
[    32.865]     ModeAttributes: 0x0
[    32.865]     WinAAttributes: 0x0
[    32.865]     WinBAttributes: 0x0
[    32.866]     WinGranularity: 0
[    32.866]     WinSize: 0
[    32.866]     WinASegment: 0x0
[    32.866]     WinBSegment: 0x0
[    32.866]     WinFuncPtr: 0x0
[    32.866]     BytesPerScanline: 0
[    32.866]     XResolution: 0
[    32.866]     YResolution: 0
[    32.866]     XCharSize: 0
[    32.866]     YCharSize: 0
[    32.866]     NumberOfPlanes: 0
[    32.866]     BitsPerPixel: 0
[    32.866]     NumberOfBanks: 0
[    32.866]     MemoryModel: 0
[    32.866]     BankSize: 0
[    32.866]     NumberOfImages: 0
[    32.866]     RedMaskSize: 0
[    32.866]     RedFieldPosition: 0
[    32.866]     GreenMaskSize: 0
[    32.866]     GreenFieldPosition: 0
[    32.866]     BlueMaskSize: 0
[    32.866]     BlueFieldPosition: 0
[    32.866]     RsvdMaskSize: 0
[    32.866]     RsvdFieldPosition: 0
[    32.866]     DirectColorModeInfo: 0
[    32.866]     PhysBasePtr: 0x0
[    32.866]     LinBytesPerScanLine: 0
[    32.866]     BnkNumberOfImagePages: 0
[    32.866]     LinNumberOfImagePages: 0
[    32.866]     LinRedMaskSize: 0
[    32.866]     LinRedFieldPosition: 0
[    32.866]     LinGreenMaskSize: 0
[    32.866]     LinGreenFieldPosition: 0
[    32.866]     LinBlueMaskSize: 0
[    32.866]     LinBlueFieldPosition: 0
[    32.866]     LinRsvdMaskSize: 0
[    32.866]     LinRsvdFieldPosition: 0
[    32.866]     MaxPixelClock: 0
[    32.866] Mode: 16e (0x0)
[    32.866]     ModeAttributes: 0x0
[    32.866]     WinAAttributes: 0x0
[    32.866]     WinBAttributes: 0x0
[    32.866]     WinGranularity: 0
[    32.866]     WinSize: 0
[    32.866]     WinASegment: 0x0
[    32.866]     WinBSegment: 0x0
[    32.866]     WinFuncPtr: 0x0
[    32.866]     BytesPerScanline: 0
[    32.866]     XResolution: 0
[    32.866]     YResolution: 0
[    32.866]     XCharSize: 0
[    32.866]     YCharSize: 0
[    32.866]     NumberOfPlanes: 0
[    32.866]     BitsPerPixel: 0
[    32.866]     NumberOfBanks: 0
[    32.866]     MemoryModel: 0
[    32.866]     BankSize: 0
[    32.866]     NumberOfImages: 0
[    32.866]     RedMaskSize: 0
[    32.866]     RedFieldPosition: 0
[    32.866]     GreenMaskSize: 0
[    32.866]     GreenFieldPosition: 0
[    32.866]     BlueMaskSize: 0
[    32.866]     BlueFieldPosition: 0
[    32.866]     RsvdMaskSize: 0
[    32.866]     RsvdFieldPosition: 0
[    32.866]     DirectColorModeInfo: 0
[    32.866]     PhysBasePtr: 0x0
[    32.866]     LinBytesPerScanLine: 0
[    32.866]     BnkNumberOfImagePages: 0
[    32.866]     LinNumberOfImagePages: 0
[    32.866]     LinRedMaskSize: 0
[    32.866]     LinRedFieldPosition: 0
[    32.866]     LinGreenMaskSize: 0
[    32.866]     LinGreenFieldPosition: 0
[    32.866]     LinBlueMaskSize: 0
[    32.866]     LinBlueFieldPosition: 0
[    32.866]     LinRsvdMaskSize: 0
[    32.866]     LinRsvdFieldPosition: 0
[    32.866]     MaxPixelClock: 0
[    32.866] Mode: 16f (0x0)
[    32.866]     ModeAttributes: 0x0
[    32.866]     WinAAttributes: 0x0
[    32.866]     WinBAttributes: 0x0
[    32.866]     WinGranularity: 0
[    32.866]     WinSize: 0
[    32.866]     WinASegment: 0x0
[    32.866]     WinBSegment: 0x0
[    32.866]     WinFuncPtr: 0x0
[    32.866]     BytesPerScanline: 0
[    32.866]     XResolution: 0
[    32.866]     YResolution: 0
[    32.866]     XCharSize: 0
[    32.866]     YCharSize: 0
[    32.866]     NumberOfPlanes: 0
[    32.866]     BitsPerPixel: 0
[    32.866]     NumberOfBanks: 0
[    32.866]     MemoryModel: 0
[    32.866]     BankSize: 0
[    32.866]     NumberOfImages: 0
[    32.866]     RedMaskSize: 0
[    32.866]     RedFieldPosition: 0
[    32.866]     GreenMaskSize: 0
[    32.866]     GreenFieldPosition: 0
[    32.866]     BlueMaskSize: 0
[    32.866]     BlueFieldPosition: 0
[    32.866]     RsvdMaskSize: 0
[    32.866]     RsvdFieldPosition: 0
[    32.866]     DirectColorModeInfo: 0
[    32.866]     PhysBasePtr: 0x0
[    32.866]     LinBytesPerScanLine: 0
[    32.866]     BnkNumberOfImagePages: 0
[    32.866]     LinNumberOfImagePages: 0
[    32.866]     LinRedMaskSize: 0
[    32.866]     LinRedFieldPosition: 0
[    32.866]     LinGreenMaskSize: 0
[    32.866]     LinGreenFieldPosition: 0
[    32.866]     LinBlueMaskSize: 0
[    32.866]     LinBlueFieldPosition: 0
[    32.866]     LinRsvdMaskSize: 0
[    32.866]     LinRsvdFieldPosition: 0
[    32.866]     MaxPixelClock: 0
[    32.867] Mode: 170 (0x0)
[    32.867]     ModeAttributes: 0x0
[    32.867]     WinAAttributes: 0x0
[    32.867]     WinBAttributes: 0x0
[    32.867]     WinGranularity: 0
[    32.867]     WinSize: 0
[    32.867]     WinASegment: 0x0
[    32.867]     WinBSegment: 0x0
[    32.867]     WinFuncPtr: 0x0
[    32.867]     BytesPerScanline: 0
[    32.867]     XResolution: 0
[    32.867]     YResolution: 0
[    32.867]     XCharSize: 0
[    32.867]     YCharSize: 0
[    32.867]     NumberOfPlanes: 0
[    32.867]     BitsPerPixel: 0
[    32.867]     NumberOfBanks: 0
[    32.867]     MemoryModel: 0
[    32.867]     BankSize: 0
[    32.867]     NumberOfImages: 0
[    32.867]     RedMaskSize: 0
[    32.867]     RedFieldPosition: 0
[    32.867]     GreenMaskSize: 0
[    32.867]     GreenFieldPosition: 0
[    32.867]     BlueMaskSize: 0
[    32.867]     BlueFieldPosition: 0
[    32.867]     RsvdMaskSize: 0
[    32.867]     RsvdFieldPosition: 0
[    32.867]     DirectColorModeInfo: 0
[    32.867]     PhysBasePtr: 0x0
[    32.867]     LinBytesPerScanLine: 0
[    32.867]     BnkNumberOfImagePages: 0
[    32.867]     LinNumberOfImagePages: 0
[    32.867]     LinRedMaskSize: 0
[    32.867]     LinRedFieldPosition: 0
[    32.867]     LinGreenMaskSize: 0
[    32.867]     LinGreenFieldPosition: 0
[    32.867]     LinBlueMaskSize: 0
[    32.867]     LinBlueFieldPosition: 0
[    32.867]     LinRsvdMaskSize: 0
[    32.867]     LinRsvdFieldPosition: 0
[    32.867]     MaxPixelClock: 0
[    32.867] Mode: 171 (0x0)
[    32.867]     ModeAttributes: 0x0
[    32.867]     WinAAttributes: 0x0
[    32.867]     WinBAttributes: 0x0
[    32.867]     WinGranularity: 0
[    32.867]     WinSize: 0
[    32.867]     WinASegment: 0x0
[    32.867]     WinBSegment: 0x0
[    32.867]     WinFuncPtr: 0x0
[    32.867]     BytesPerScanline: 0
[    32.867]     XResolution: 0
[    32.867]     YResolution: 0
[    32.867]     XCharSize: 0
[    32.867]     YCharSize: 0
[    32.867]     NumberOfPlanes: 0
[    32.867]     BitsPerPixel: 0
[    32.867]     NumberOfBanks: 0
[    32.867]     MemoryModel: 0
[    32.867]     BankSize: 0
[    32.867]     NumberOfImages: 0
[    32.867]     RedMaskSize: 0
[    32.867]     RedFieldPosition: 0
[    32.867]     GreenMaskSize: 0
[    32.867]     GreenFieldPosition: 0
[    32.867]     BlueMaskSize: 0
[    32.867]     BlueFieldPosition: 0
[    32.867]     RsvdMaskSize: 0
[    32.867]     RsvdFieldPosition: 0
[    32.867]     DirectColorModeInfo: 0
[    32.867]     PhysBasePtr: 0x0
[    32.867]     LinBytesPerScanLine: 0
[    32.867]     BnkNumberOfImagePages: 0
[    32.867]     LinNumberOfImagePages: 0
[    32.867]     LinRedMaskSize: 0
[    32.867]     LinRedFieldPosition: 0
[    32.867]     LinGreenMaskSize: 0
[    32.867]     LinGreenFieldPosition: 0
[    32.867]     LinBlueMaskSize: 0
[    32.867]     LinBlueFieldPosition: 0
[    32.867]     LinRsvdMaskSize: 0
[    32.867]     LinRsvdFieldPosition: 0
[    32.867]     MaxPixelClock: 0
[    32.867] Mode: 13c (0x0)
[    32.867]     ModeAttributes: 0x0
[    32.867]     WinAAttributes: 0x0
[    32.867]     WinBAttributes: 0x0
[    32.867]     WinGranularity: 0
[    32.867]     WinSize: 0
[    32.867]     WinASegment: 0x0
[    32.867]     WinBSegment: 0x0
[    32.867]     WinFuncPtr: 0x0
[    32.867]     BytesPerScanline: 0
[    32.867]     XResolution: 0
[    32.867]     YResolution: 0
[    32.867]     XCharSize: 0
[    32.868]     YCharSize: 0
[    32.868]     NumberOfPlanes: 0
[    32.868]     BitsPerPixel: 0
[    32.868]     NumberOfBanks: 0
[    32.868]     MemoryModel: 0
[    32.868]     BankSize: 0
[    32.868]     NumberOfImages: 0
[    32.868]     RedMaskSize: 0
[    32.868]     RedFieldPosition: 0
[    32.868]     GreenMaskSize: 0
[    32.868]     GreenFieldPosition: 0
[    32.868]     BlueMaskSize: 0
[    32.868]     BlueFieldPosition: 0
[    32.868]     RsvdMaskSize: 0
[    32.868]     RsvdFieldPosition: 0
[    32.868]     DirectColorModeInfo: 0
[    32.868]     PhysBasePtr: 0x0
[    32.868]     LinBytesPerScanLine: 0
[    32.868]     BnkNumberOfImagePages: 0
[    32.868]     LinNumberOfImagePages: 0
[    32.868]     LinRedMaskSize: 0
[    32.868]     LinRedFieldPosition: 0
[    32.868]     LinGreenMaskSize: 0
[    32.868]     LinGreenFieldPosition: 0
[    32.868]     LinBlueMaskSize: 0
[    32.868]     LinBlueFieldPosition: 0
[    32.868]     LinRsvdMaskSize: 0
[    32.868]     LinRsvdFieldPosition: 0
[    32.868]     MaxPixelClock: 0
[    32.868] Mode: 14d (0x0)
[    32.868]     ModeAttributes: 0x0
[    32.868]     WinAAttributes: 0x0
[    32.868]     WinBAttributes: 0x0
[    32.868]     WinGranularity: 0
[    32.868]     WinSize: 0
[    32.868]     WinASegment: 0x0
[    32.868]     WinBSegment: 0x0
[    32.868]     WinFuncPtr: 0x0
[    32.868]     BytesPerScanline: 0
[    32.868]     XResolution: 0
[    32.868]     YResolution: 0
[    32.868]     XCharSize: 0
[    32.868]     YCharSize: 0
[    32.868]     NumberOfPlanes: 0
[    32.868]     BitsPerPixel: 0
[    32.868]     NumberOfBanks: 0
[    32.868]     MemoryModel: 0
[    32.868]     BankSize: 0
[    32.868]     NumberOfImages: 0
[    32.868]     RedMaskSize: 0
[    32.868]     RedFieldPosition: 0
[    32.868]     GreenMaskSize: 0
[    32.868]     GreenFieldPosition: 0
[    32.868]     BlueMaskSize: 0
[    32.868]     BlueFieldPosition: 0
[    32.868]     RsvdMaskSize: 0
[    32.868]     RsvdFieldPosition: 0
[    32.868]     DirectColorModeInfo: 0
[    32.868]     PhysBasePtr: 0x0
[    32.868]     LinBytesPerScanLine: 0
[    32.868]     BnkNumberOfImagePages: 0
[    32.868]     LinNumberOfImagePages: 0
[    32.868]     LinRedMaskSize: 0
[    32.868]     LinRedFieldPosition: 0
[    32.868]     LinGreenMaskSize: 0
[    32.868]     LinGreenFieldPosition: 0
[    32.868]     LinBlueMaskSize: 0
[    32.868]     LinBlueFieldPosition: 0
[    32.868]     LinRsvdMaskSize: 0
[    32.868]     LinRsvdFieldPosition: 0
[    32.868]     MaxPixelClock: 0
[    32.868] Mode: 15c (0x0)
[    32.868]     ModeAttributes: 0x0
[    32.868]     WinAAttributes: 0x0
[    32.868]     WinBAttributes: 0x0
[    32.868]     WinGranularity: 0
[    32.868]     WinSize: 0
[    32.868]     WinASegment: 0x0
[    32.868]     WinBSegment: 0x0
[    32.868]     WinFuncPtr: 0x0
[    32.868]     BytesPerScanline: 0
[    32.868]     XResolution: 0
[    32.868]     YResolution: 0
[    32.868]     XCharSize: 0
[    32.868]     YCharSize: 0
[    32.868]     NumberOfPlanes: 0
[    32.868]     BitsPerPixel: 0
[    32.868]     NumberOfBanks: 0
[    32.868]     MemoryModel: 0
[    32.868]     BankSize: 0
[    32.868]     NumberOfImages: 0
[    32.868]     RedMaskSize: 0
[    32.868]     RedFieldPosition: 0
[    32.868]     GreenMaskSize: 0
[    32.868]     GreenFieldPosition: 0
[    32.869]     BlueMaskSize: 0
[    32.869]     BlueFieldPosition: 0
[    32.869]     RsvdMaskSize: 0
[    32.869]     RsvdFieldPosition: 0
[    32.869]     DirectColorModeInfo: 0
[    32.869]     PhysBasePtr: 0x0
[    32.869]     LinBytesPerScanLine: 0
[    32.869]     BnkNumberOfImagePages: 0
[    32.869]     LinNumberOfImagePages: 0
[    32.869]     LinRedMaskSize: 0
[    32.869]     LinRedFieldPosition: 0
[    32.869]     LinGreenMaskSize: 0
[    32.869]     LinGreenFieldPosition: 0
[    32.869]     LinBlueMaskSize: 0
[    32.869]     LinBlueFieldPosition: 0
[    32.869]     LinRsvdMaskSize: 0
[    32.869]     LinRsvdFieldPosition: 0
[    32.869]     MaxPixelClock: 0
[    32.869] Mode: 13a (0x0)
[    32.869]     ModeAttributes: 0x0
[    32.869]     WinAAttributes: 0x0
[    32.869]     WinBAttributes: 0x0
[    32.869]     WinGranularity: 0
[    32.869]     WinSize: 0
[    32.869]     WinASegment: 0x0
[    32.869]     WinBSegment: 0x0
[    32.869]     WinFuncPtr: 0x0
[    32.869]     BytesPerScanline: 0
[    32.869]     XResolution: 0
[    32.869]     YResolution: 0
[    32.869]     XCharSize: 0
[    32.869]     YCharSize: 0
[    32.869]     NumberOfPlanes: 0
[    32.869]     BitsPerPixel: 0
[    32.869]     NumberOfBanks: 0
[    32.869]     MemoryModel: 0
[    32.869]     BankSize: 0
[    32.869]     NumberOfImages: 0
[    32.869]     RedMaskSize: 0
[    32.869]     RedFieldPosition: 0
[    32.869]     GreenMaskSize: 0
[    32.869]     GreenFieldPosition: 0
[    32.869]     BlueMaskSize: 0
[    32.869]     BlueFieldPosition: 0
[    32.869]     RsvdMaskSize: 0
[    32.869]     RsvdFieldPosition: 0
[    32.869]     DirectColorModeInfo: 0
[    32.869]     PhysBasePtr: 0x0
[    32.869]     LinBytesPerScanLine: 0
[    32.869]     BnkNumberOfImagePages: 0
[    32.869]     LinNumberOfImagePages: 0
[    32.869]     LinRedMaskSize: 0
[    32.869]     LinRedFieldPosition: 0
[    32.869]     LinGreenMaskSize: 0
[    32.869]     LinGreenFieldPosition: 0
[    32.869]     LinBlueMaskSize: 0
[    32.869]     LinBlueFieldPosition: 0
[    32.869]     LinRsvdMaskSize: 0
[    32.869]     LinRsvdFieldPosition: 0
[    32.869]     MaxPixelClock: 0
[    32.869] Mode: 14b (0x0)
[    32.869]     ModeAttributes: 0x0
[    32.869]     WinAAttributes: 0x0
[    32.869]     WinBAttributes: 0x0
[    32.869]     WinGranularity: 0
[    32.869]     WinSize: 0
[    32.869]     WinASegment: 0x0
[    32.869]     WinBSegment: 0x0
[    32.869]     WinFuncPtr: 0x0
[    32.869]     BytesPerScanline: 0
[    32.869]     XResolution: 0
[    32.869]     YResolution: 0
[    32.869]     XCharSize: 0
[    32.869]     YCharSize: 0
[    32.869]     NumberOfPlanes: 0
[    32.869]     BitsPerPixel: 0
[    32.869]     NumberOfBanks: 0
[    32.869]     MemoryModel: 0
[    32.869]     BankSize: 0
[    32.869]     NumberOfImages: 0
[    32.869]     RedMaskSize: 0
[    32.869]     RedFieldPosition: 0
[    32.869]     GreenMaskSize: 0
[    32.869]     GreenFieldPosition: 0
[    32.869]     BlueMaskSize: 0
[    32.869]     BlueFieldPosition: 0
[    32.869]     RsvdMaskSize: 0
[    32.869]     RsvdFieldPosition: 0
[    32.869]     DirectColorModeInfo: 0
[    32.869]     PhysBasePtr: 0x0
[    32.869]     LinBytesPerScanLine: 0
[    32.869]     BnkNumberOfImagePages: 0
[    32.869]     LinNumberOfImagePages: 0
[    32.869]     LinRedMaskSize: 0
[    32.869]     LinRedFieldPosition: 0
[    32.869]     LinGreenMaskSize: 0
[    32.869]     LinGreenFieldPosition: 0
[    32.869]     LinBlueMaskSize: 0
[    32.869]     LinBlueFieldPosition: 0
[    32.869]     LinRsvdMaskSize: 0
[    32.869]     LinRsvdFieldPosition: 0
[    32.869]     MaxPixelClock: 0
[    32.870] Mode: 15a (0x0)
[    32.870]     ModeAttributes: 0x0
[    32.870]     WinAAttributes: 0x0
[    32.870]     WinBAttributes: 0x0
[    32.870]     WinGranularity: 0
[    32.870]     WinSize: 0
[    32.870]     WinASegment: 0x0
[    32.870]     WinBSegment: 0x0
[    32.870]     WinFuncPtr: 0x0
[    32.870]     BytesPerScanline: 0
[    32.870]     XResolution: 0
[    32.870]     YResolution: 0
[    32.870]     XCharSize: 0
[    32.870]     YCharSize: 0
[    32.870]     NumberOfPlanes: 0
[    32.870]     BitsPerPixel: 0
[    32.870]     NumberOfBanks: 0
[    32.870]     MemoryModel: 0
[    32.870]     BankSize: 0
[    32.870]     NumberOfImages: 0
[    32.870]     RedMaskSize: 0
[    32.870]     RedFieldPosition: 0
[    32.870]     GreenMaskSize: 0
[    32.870]     GreenFieldPosition: 0
[    32.870]     BlueMaskSize: 0
[    32.870]     BlueFieldPosition: 0
[    32.870]     RsvdMaskSize: 0
[    32.870]     RsvdFieldPosition: 0
[    32.870]     DirectColorModeInfo: 0
[    32.870]     PhysBasePtr: 0x0
[    32.870]     LinBytesPerScanLine: 0
[    32.870]     BnkNumberOfImagePages: 0
[    32.870]     LinNumberOfImagePages: 0
[    32.870]     LinRedMaskSize: 0
[    32.870]     LinRedFieldPosition: 0
[    32.870]     LinGreenMaskSize: 0
[    32.870]     LinGreenFieldPosition: 0
[    32.870]     LinBlueMaskSize: 0
[    32.870]     LinBlueFieldPosition: 0
[    32.870]     LinRsvdMaskSize: 0
[    32.870]     LinRsvdFieldPosition: 0
[    32.870]     MaxPixelClock: 0
[    32.870] Mode: 107 (0x0)
[    32.870]     ModeAttributes: 0x0
[    32.870]     WinAAttributes: 0x0
[    32.870]     WinBAttributes: 0x0
[    32.870]     WinGranularity: 0
[    32.870]     WinSize: 0
[    32.870]     WinASegment: 0x0
[    32.870]     WinBSegment: 0x0
[    32.870]     WinFuncPtr: 0x0
[    32.870]     BytesPerScanline: 0
[    32.870]     XResolution: 0
[    32.870]     YResolution: 0
[    32.870]     XCharSize: 0
[    32.870]     YCharSize: 0
[    32.870]     NumberOfPlanes: 0
[    32.870]     BitsPerPixel: 0
[    32.870]     NumberOfBanks: 0
[    32.870]     MemoryModel: 0
[    32.870]     BankSize: 0
[    32.870]     NumberOfImages: 0
[    32.870]     RedMaskSize: 0
[    32.870]     RedFieldPosition: 0
[    32.870]     GreenMaskSize: 0
[    32.870]     GreenFieldPosition: 0
[    32.870]     BlueMaskSize: 0
[    32.870]     BlueFieldPosition: 0
[    32.870]     RsvdMaskSize: 0
[    32.870]     RsvdFieldPosition: 0
[    32.870]     DirectColorModeInfo: 0
[    32.870]     PhysBasePtr: 0x0
[    32.870]     LinBytesPerScanLine: 0
[    32.870]     BnkNumberOfImagePages: 0
[    32.870]     LinNumberOfImagePages: 0
[    32.870]     LinRedMaskSize: 0
[    32.870]     LinRedFieldPosition: 0
[    32.870]     LinGreenMaskSize: 0
[    32.870]     LinGreenFieldPosition: 0
[    32.870]     LinBlueMaskSize: 0
[    32.870]     LinBlueFieldPosition: 0
[    32.870]     LinRsvdMaskSize: 0
[    32.870]     LinRsvdFieldPosition: 0
[    32.870]     MaxPixelClock: 0
[    32.871] Mode: 11a (0x0)
[    32.871]     ModeAttributes: 0x0
[    32.871]     WinAAttributes: 0x0
[    32.871]     WinBAttributes: 0x0
[    32.871]     WinGranularity: 0
[    32.871]     WinSize: 0
[    32.871]     WinASegment: 0x0
[    32.871]     WinBSegment: 0x0
[    32.871]     WinFuncPtr: 0x0
[    32.871]     BytesPerScanline: 0
[    32.871]     XResolution: 0
[    32.871]     YResolution: 0
[    32.871]     XCharSize: 0
[    32.871]     YCharSize: 0
[    32.871]     NumberOfPlanes: 0
[    32.871]     BitsPerPixel: 0
[    32.871]     NumberOfBanks: 0
[    32.871]     MemoryModel: 0
[    32.871]     BankSize: 0
[    32.871]     NumberOfImages: 0
[    32.871]     RedMaskSize: 0
[    32.871]     RedFieldPosition: 0
[    32.871]     GreenMaskSize: 0
[    32.871]     GreenFieldPosition: 0
[    32.871]     BlueMaskSize: 0
[    32.871]     BlueFieldPosition: 0
[    32.871]     RsvdMaskSize: 0
[    32.871]     RsvdFieldPosition: 0
[    32.871]     DirectColorModeInfo: 0
[    32.871]     PhysBasePtr: 0x0
[    32.871]     LinBytesPerScanLine: 0
[    32.871]     BnkNumberOfImagePages: 0
[    32.871]     LinNumberOfImagePages: 0
[    32.871]     LinRedMaskSize: 0
[    32.871]     LinRedFieldPosition: 0
[    32.871]     LinGreenMaskSize: 0
[    32.871]     LinGreenFieldPosition: 0
[    32.871]     LinBlueMaskSize: 0
[    32.871]     LinBlueFieldPosition: 0
[    32.871]     LinRsvdMaskSize: 0
[    32.871]     LinRsvdFieldPosition: 0
[    32.871]     MaxPixelClock: 0
[    32.871] Mode: 11b (0x0)
[    32.871]     ModeAttributes: 0x0
[    32.871]     WinAAttributes: 0x0
[    32.871]     WinBAttributes: 0x0
[    32.871]     WinGranularity: 0
[    32.871]     WinSize: 0
[    32.871]     WinASegment: 0x0
[    32.871]     WinBSegment: 0x0
[    32.871]     WinFuncPtr: 0x0
[    32.871]     BytesPerScanline: 0
[    32.871]     XResolution: 0
[    32.871]     YResolution: 0
[    32.871]     XCharSize: 0
[    32.871]     YCharSize: 0
[    32.871]     NumberOfPlanes: 0
[    32.871]     BitsPerPixel: 0
[    32.871]     NumberOfBanks: 0
[    32.871]     MemoryModel: 0
[    32.871]     BankSize: 0
[    32.871]     NumberOfImages: 0
[    32.871]     RedMaskSize: 0
[    32.871]     RedFieldPosition: 0
[    32.871]     GreenMaskSize: 0
[    32.871]     GreenFieldPosition: 0
[    32.871]     BlueMaskSize: 0
[    32.871]     BlueFieldPosition: 0
[    32.871]     RsvdMaskSize: 0
[    32.871]     RsvdFieldPosition: 0
[    32.871]     DirectColorModeInfo: 0
[    32.871]     PhysBasePtr: 0x0
[    32.871]     LinBytesPerScanLine: 0
[    32.871]     BnkNumberOfImagePages: 0
[    32.871]     LinNumberOfImagePages: 0
[    32.871]     LinRedMaskSize: 0
[    32.871]     LinRedFieldPosition: 0
[    32.871]     LinGreenMaskSize: 0
[    32.871]     LinGreenFieldPosition: 0
[    32.871]     LinBlueMaskSize: 0
[    32.871]     LinBlueFieldPosition: 0
[    32.871]     LinRsvdMaskSize: 0
[    32.871]     LinRsvdFieldPosition: 0
[    32.871]     MaxPixelClock: 0
[    32.872] Mode: 105 (1024x768)
[    32.872]     ModeAttributes: 0x9b
[    32.872]     WinAAttributes: 0x7
[    32.872]     WinBAttributes: 0x0
[    32.872]     WinGranularity: 64
[    32.872]     WinSize: 64
[    32.872]     WinASegment: 0xa000
[    32.872]     WinBSegment: 0x0
[    32.872]     WinFuncPtr: 0xc000853d
[    32.872]     BytesPerScanline: 1024
[    32.872]     XResolution: 1024
[    32.872]     YResolution: 768
[    32.872]     XCharSize: 8
[    32.872]     YCharSize: 16
[    32.872]     NumberOfPlanes: 1
[    32.872]     BitsPerPixel: 8
[    32.872]     NumberOfBanks: 1
[    32.872]     MemoryModel: 4
[    32.872]     BankSize: 0
[    32.872]     NumberOfImages: 169
[    32.872]     RedMaskSize: 0
[    32.872]     RedFieldPosition: 0
[    32.872]     GreenMaskSize: 0
[    32.872]     GreenFieldPosition: 0
[    32.872]     BlueMaskSize: 0
[    32.872]     BlueFieldPosition: 0
[    32.872]     RsvdMaskSize: 0
[    32.872]     RsvdFieldPosition: 0
[    32.872]     DirectColorModeInfo: 0
[    32.872]     PhysBasePtr: 0x80000000
[    32.872]     LinBytesPerScanLine: 1024
[    32.872]     BnkNumberOfImagePages: 169
[    32.872]     LinNumberOfImagePages: 169
[    32.872]     LinRedMaskSize: 0
[    32.872]     LinRedFieldPosition: 0
[    32.872]     LinGreenMaskSize: 0
[    32.872]     LinGreenFieldPosition: 0
[    32.872]     LinBlueMaskSize: 0
[    32.872]     LinBlueFieldPosition: 0
[    32.872]     LinRsvdMaskSize: 0
[    32.872]     LinRsvdFieldPosition: 0
[    32.872]     MaxPixelClock: 230000000
[    32.872] Mode: 117 (1024x768)
[    32.872]     ModeAttributes: 0x9b
[    32.872]     WinAAttributes: 0x7
[    32.872]     WinBAttributes: 0x0
[    32.872]     WinGranularity: 64
[    32.872]     WinSize: 64
[    32.872]     WinASegment: 0xa000
[    32.872]     WinBSegment: 0x0
[    32.872]     WinFuncPtr: 0xc000853d
[    32.872]     BytesPerScanline: 2048
[    32.872]     XResolution: 1024
[    32.872]     YResolution: 768
[    32.872]     XCharSize: 8
[    32.872]     YCharSize: 16
[    32.872]     NumberOfPlanes: 1
[    32.872]     BitsPerPixel: 16
[    32.872]     NumberOfBanks: 1
[    32.872]     MemoryModel: 6
[    32.872]     BankSize: 0
[    32.872]     NumberOfImages: 84
[    32.872]     RedMaskSize: 5
[    32.872]     RedFieldPosition: 11
[    32.872]     GreenMaskSize: 6
[    32.872]     GreenFieldPosition: 5
[    32.872]     BlueMaskSize: 5
[    32.872]     BlueFieldPosition: 0
[    32.872]     RsvdMaskSize: 0
[    32.872]     RsvdFieldPosition: 0
[    32.872]     DirectColorModeInfo: 0
[    32.872]     PhysBasePtr: 0x80000000
[    32.872]     LinBytesPerScanLine: 2048
[    32.872]     BnkNumberOfImagePages: 84
[    32.872]     LinNumberOfImagePages: 84
[    32.872]     LinRedMaskSize: 5
[    32.872]     LinRedFieldPosition: 11
[    32.872]     LinGreenMaskSize: 6
[    32.872]     LinGreenFieldPosition: 5
[    32.872]     LinBlueMaskSize: 5
[    32.872]     LinBlueFieldPosition: 0
[    32.872]     LinRsvdMaskSize: 0
[    32.872]     LinRsvdFieldPosition: 0
[    32.873]     MaxPixelClock: 230000000
[    32.873] *Mode: 118 (1024x768)
[    32.873]     ModeAttributes: 0x9b
[    32.873]     WinAAttributes: 0x7
[    32.873]     WinBAttributes: 0x0
[    32.873]     WinGranularity: 64
[    32.873]     WinSize: 64
[    32.873]     WinASegment: 0xa000
[    32.873]     WinBSegment: 0x0
[    32.873]     WinFuncPtr: 0xc000853d
[    32.873]     BytesPerScanline: 4096
[    32.873]     XResolution: 1024
[    32.873]     YResolution: 768
[    32.873]     XCharSize: 8
[    32.873]     YCharSize: 16
[    32.873]     NumberOfPlanes: 1
[    32.873]     BitsPerPixel: 32
[    32.873]     NumberOfBanks: 1
[    32.873]     MemoryModel: 6
[    32.873]     BankSize: 0
[    32.873]     NumberOfImages: 41
[    32.873]     RedMaskSize: 8
[    32.873]     RedFieldPosition: 16
[    32.873]     GreenMaskSize: 8
[    32.873]     GreenFieldPosition: 8
[    32.873]     BlueMaskSize: 8
[    32.873]     BlueFieldPosition: 0
[    32.873]     RsvdMaskSize: 8
[    32.873]     RsvdFieldPosition: 24
[    32.873]     DirectColorModeInfo: 0
[    32.873]     PhysBasePtr: 0x80000000
[    32.873]     LinBytesPerScanLine: 4096
[    32.873]     BnkNumberOfImagePages: 41
[    32.873]     LinNumberOfImagePages: 41
[    32.873]     LinRedMaskSize: 8
[    32.873]     LinRedFieldPosition: 16
[    32.873]     LinGreenMaskSize: 8
[    32.873]     LinGreenFieldPosition: 8
[    32.873]     LinBlueMaskSize: 8
[    32.873]     LinBlueFieldPosition: 0
[    32.873]     LinRsvdMaskSize: 8
[    32.873]     LinRsvdFieldPosition: 24
[    32.873]     MaxPixelClock: 230000000
[    32.874] *Mode: 112 (640x480)
[    32.874]     ModeAttributes: 0x9b
[    32.874]     WinAAttributes: 0x7
[    32.874]     WinBAttributes: 0x0
[    32.874]     WinGranularity: 64
[    32.874]     WinSize: 64
[    32.874]     WinASegment: 0xa000
[    32.874]     WinBSegment: 0x0
[    32.874]     WinFuncPtr: 0xc000853d
[    32.874]     BytesPerScanline: 2560
[    32.874]     XResolution: 640
[    32.874]     YResolution: 480
[    32.874]     XCharSize: 8
[    32.874]     YCharSize: 16
[    32.874]     NumberOfPlanes: 1
[    32.874]     BitsPerPixel: 32
[    32.874]     NumberOfBanks: 1
[    32.874]     MemoryModel: 6
[    32.874]     BankSize: 0
[    32.874]     NumberOfImages: 106
[    32.874]     RedMaskSize: 8
[    32.874]     RedFieldPosition: 16
[    32.874]     GreenMaskSize: 8
[    32.874]     GreenFieldPosition: 8
[    32.874]     BlueMaskSize: 8
[    32.874]     BlueFieldPosition: 0
[    32.874]     RsvdMaskSize: 8
[    32.874]     RsvdFieldPosition: 24
[    32.874]     DirectColorModeInfo: 0
[    32.874]     PhysBasePtr: 0x80000000
[    32.874]     LinBytesPerScanLine: 2560
[    32.874]     BnkNumberOfImagePages: 106
[    32.874]     LinNumberOfImagePages: 106
[    32.874]     LinRedMaskSize: 8
[    32.874]     LinRedFieldPosition: 16
[    32.874]     LinGreenMaskSize: 8
[    32.874]     LinGreenFieldPosition: 8
[    32.874]     LinBlueMaskSize: 8
[    32.874]     LinBlueFieldPosition: 0
[    32.874]     LinRsvdMaskSize: 8
[    32.874]     LinRsvdFieldPosition: 24
[    32.874]     MaxPixelClock: 230000000
[    32.874] Mode: 114 (800x600)
[    32.874]     ModeAttributes: 0x9b
[    32.874]     WinAAttributes: 0x7
[    32.874]     WinBAttributes: 0x0
[    32.874]     WinGranularity: 64
[    32.874]     WinSize: 64
[    32.874]     WinASegment: 0xa000
[    32.874]     WinBSegment: 0x0
[    32.874]     WinFuncPtr: 0xc000853d
[    32.874]     BytesPerScanline: 1600
[    32.874]     XResolution: 800
[    32.874]     YResolution: 600
[    32.874]     XCharSize: 8
[    32.874]     YCharSize: 16
[    32.874]     NumberOfPlanes: 1
[    32.874]     BitsPerPixel: 16
[    32.874]     NumberOfBanks: 1
[    32.874]     MemoryModel: 6
[    32.874]     BankSize: 0
[    32.874]     NumberOfImages: 135
[    32.874]     RedMaskSize: 5
[    32.874]     RedFieldPosition: 11
[    32.874]     GreenMaskSize: 6
[    32.874]     GreenFieldPosition: 5
[    32.874]     BlueMaskSize: 5
[    32.874]     BlueFieldPosition: 0
[    32.874]     RsvdMaskSize: 0
[    32.874]     RsvdFieldPosition: 0
[    32.874]     DirectColorModeInfo: 0
[    32.874]     PhysBasePtr: 0x80000000
[    32.874]     LinBytesPerScanLine: 1600
[    32.874]     BnkNumberOfImagePages: 135
[    32.874]     LinNumberOfImagePages: 135
[    32.874]     LinRedMaskSize: 5
[    32.874]     LinRedFieldPosition: 11
[    32.874]     LinGreenMaskSize: 6
[    32.874]     LinGreenFieldPosition: 5
[    32.874]     LinBlueMaskSize: 5
[    32.874]     LinBlueFieldPosition: 0
[    32.874]     LinRsvdMaskSize: 0
[    32.874]     LinRsvdFieldPosition: 0
[    32.874]     MaxPixelClock: 230000000
[    32.875] *Mode: 115 (800x600)
[    32.875]     ModeAttributes: 0x9b
[    32.875]     WinAAttributes: 0x7
[    32.875]     WinBAttributes: 0x0
[    32.875]     WinGranularity: 64
[    32.875]     WinSize: 64
[    32.875]     WinASegment: 0xa000
[    32.875]     WinBSegment: 0x0
[    32.875]     WinFuncPtr: 0xc000853d
[    32.875]     BytesPerScanline: 3200
[    32.875]     XResolution: 800
[    32.875]     YResolution: 600
[    32.875]     XCharSize: 8
[    32.875]     YCharSize: 16
[    32.875]     NumberOfPlanes: 1
[    32.875]     BitsPerPixel: 32
[    32.875]     NumberOfBanks: 1
[    32.875]     MemoryModel: 6
[    32.875]     BankSize: 0
[    32.875]     NumberOfImages: 67
[    32.875]     RedMaskSize: 8
[    32.875]     RedFieldPosition: 16
[    32.875]     GreenMaskSize: 8
[    32.875]     GreenFieldPosition: 8
[    32.875]     BlueMaskSize: 8
[    32.875]     BlueFieldPosition: 0
[    32.875]     RsvdMaskSize: 8
[    32.875]     RsvdFieldPosition: 24
[    32.875]     DirectColorModeInfo: 0
[    32.875]     PhysBasePtr: 0x80000000
[    32.875]     LinBytesPerScanLine: 3200
[    32.875]     BnkNumberOfImagePages: 67
[    32.875]     LinNumberOfImagePages: 67
[    32.875]     LinRedMaskSize: 8
[    32.875]     LinRedFieldPosition: 16
[    32.875]     LinGreenMaskSize: 8
[    32.875]     LinGreenFieldPosition: 8
[    32.875]     LinBlueMaskSize: 8
[    32.875]     LinBlueFieldPosition: 0
[    32.875]     LinRsvdMaskSize: 8
[    32.875]     LinRsvdFieldPosition: 24
[    32.875]     MaxPixelClock: 230000000
[    32.875] Mode: 101 (640x480)
[    32.875]     ModeAttributes: 0x9b
[    32.875]     WinAAttributes: 0x7
[    32.875]     WinBAttributes: 0x0
[    32.875]     WinGranularity: 64
[    32.875]     WinSize: 64
[    32.875]     WinASegment: 0xa000
[    32.875]     WinBSegment: 0x0
[    32.875]     WinFuncPtr: 0xc000853d
[    32.875]     BytesPerScanline: 640
[    32.875]     XResolution: 640
[    32.875]     YResolution: 480
[    32.875]     XCharSize: 8
[    32.875]     YCharSize: 16
[    32.875]     NumberOfPlanes: 1
[    32.876]     BitsPerPixel: 8
[    32.876]     NumberOfBanks: 1
[    32.876]     MemoryModel: 4
[    32.876]     BankSize: 0
[    32.876]     NumberOfImages: 152
[    32.876]     RedMaskSize: 0
[    32.876]     RedFieldPosition: 0
[    32.876]     GreenMaskSize: 0
[    32.876]     GreenFieldPosition: 0
[    32.876]     BlueMaskSize: 0
[    32.876]     BlueFieldPosition: 0
[    32.876]     RsvdMaskSize: 0
[    32.876]     RsvdFieldPosition: 0
[    32.876]     DirectColorModeInfo: 0
[    32.876]     PhysBasePtr: 0x80000000
[    32.876]     LinBytesPerScanLine: 640
[    32.876]     BnkNumberOfImagePages: 152
[    32.876]     LinNumberOfImagePages: 152
[    32.876]     LinRedMaskSize: 0
[    32.876]     LinRedFieldPosition: 0
[    32.876]     LinGreenMaskSize: 0
[    32.876]     LinGreenFieldPosition: 0
[    32.876]     LinBlueMaskSize: 0
[    32.876]     LinBlueFieldPosition: 0
[    32.876]     LinRsvdMaskSize: 0
[    32.876]     LinRsvdFieldPosition: 0
[    32.876]     MaxPixelClock: 230000000
[    32.876] Mode: 103 (800x600)
[    32.876]     ModeAttributes: 0x9b
[    32.876]     WinAAttributes: 0x7
[    32.876]     WinBAttributes: 0x0
[    32.876]     WinGranularity: 64
[    32.876]     WinSize: 64
[    32.876]     WinASegment: 0xa000
[    32.876]     WinBSegment: 0x0
[    32.876]     WinFuncPtr: 0xc000853d
[    32.876]     BytesPerScanline: 832
[    32.876]     XResolution: 800
[    32.876]     YResolution: 600
[    32.876]     XCharSize: 8
[    32.876]     YCharSize: 16
[    32.876]     NumberOfPlanes: 1
[    32.876]     BitsPerPixel: 8
[    32.876]     NumberOfBanks: 1
[    32.876]     MemoryModel: 4
[    32.876]     BankSize: 0
[    32.876]     NumberOfImages: 254
[    32.876]     RedMaskSize: 0
[    32.876]     RedFieldPosition: 0
[    32.876]     GreenMaskSize: 0
[    32.876]     GreenFieldPosition: 0
[    32.876]     BlueMaskSize: 0
[    32.876]     BlueFieldPosition: 0
[    32.876]     RsvdMaskSize: 0
[    32.876]     RsvdFieldPosition: 0
[    32.876]     DirectColorModeInfo: 0
[    32.876]     PhysBasePtr: 0x80000000
[    32.876]     LinBytesPerScanLine: 832
[    32.876]     BnkNumberOfImagePages: 254
[    32.876]     LinNumberOfImagePages: 254
[    32.876]     LinRedMaskSize: 0
[    32.876]     LinRedFieldPosition: 0
[    32.876]     LinGreenMaskSize: 0
[    32.876]     LinGreenFieldPosition: 0
[    32.876]     LinBlueMaskSize: 0
[    32.876]     LinBlueFieldPosition: 0
[    32.876]     LinRsvdMaskSize: 0
[    32.876]     LinRsvdFieldPosition: 0
[    32.876]     MaxPixelClock: 230000000
[    32.877] Mode: 111 (640x480)
[    32.877]     ModeAttributes: 0x9b
[    32.877]     WinAAttributes: 0x7
[    32.877]     WinBAttributes: 0x0
[    32.877]     WinGranularity: 64
[    32.877]     WinSize: 64
[    32.877]     WinASegment: 0xa000
[    32.877]     WinBSegment: 0x0
[    32.877]     WinFuncPtr: 0xc000853d
[    32.877]     BytesPerScanline: 1280
[    32.877]     XResolution: 640
[    32.877]     YResolution: 480
[    32.877]     XCharSize: 8
[    32.877]     YCharSize: 16
[    32.877]     NumberOfPlanes: 1
[    32.877]     BitsPerPixel: 16
[    32.877]     NumberOfBanks: 1
[    32.877]     MemoryModel: 6
[    32.877]     BankSize: 0
[    32.877]     NumberOfImages: 203
[    32.877]     RedMaskSize: 5
[    32.877]     RedFieldPosition: 11
[    32.877]     GreenMaskSize: 6
[    32.877]     GreenFieldPosition: 5
[    32.877]     BlueMaskSize: 5
[    32.877]     BlueFieldPosition: 0
[    32.877]     RsvdMaskSize: 0
[    32.877]     RsvdFieldPosition: 0
[    32.877]     DirectColorModeInfo: 0
[    32.877]     PhysBasePtr: 0x80000000
[    32.877]     LinBytesPerScanLine: 1280
[    32.877]     BnkNumberOfImagePages: 203
[    32.877]     LinNumberOfImagePages: 203
[    32.877]     LinRedMaskSize: 5
[    32.877]     LinRedFieldPosition: 11
[    32.877]     LinGreenMaskSize: 6
[    32.877]     LinGreenFieldPosition: 5
[    32.877]     LinBlueMaskSize: 5
[    32.877]     LinBlueFieldPosition: 0
[    32.877]     LinRsvdMaskSize: 0
[    32.877]     LinRsvdFieldPosition: 0
[    32.877]     MaxPixelClock: 230000000
[    32.877] 
[    32.877] (II) VESA(0): Total Memory: 2047 64KB banks (131008kB)
[    32.877] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    32.877] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    32.877] (WW) VESA(0): Unable to estimate virtual size
[    32.877] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    32.877] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    32.877] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    32.877] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    32.877] (II) VESA(0): <default monitor>: Using hsync value of 47.38 kHz
[    32.877] (II) VESA(0): <default monitor>: Using vrefresh value of 59.97 Hz
[    32.877] (WW) VESA(0): Unable to estimate virtual size
[    32.877] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    32.877] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    32.877] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    32.877] (**) VESA(0): *Built-in mode "1024x768"
[    32.877] (**) VESA(0): Display dimensions: (340, 190) mm
[    32.877] (**) VESA(0): DPI set to (76, 102)
[    32.877] (**) VESA(0): Using "Shadow Framebuffer"
[    32.877] (II) Loading sub module "shadow"
[    32.877] (II) LoadModule: "shadow"
[    32.877] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    32.877] (II) Module shadow: vendor="X.Org Foundation"
[    32.877]     compiled for 1.10.1, module version = 1.1.0
[    32.878]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.878] (II) Loading sub module "fb"
[    32.878] (II) LoadModule: "fb"
[    32.878] (II) Loading /usr/lib/xorg/modules/libfb.so
[    32.878] (II) Module fb: vendor="X.Org Foundation"
[    32.878]     compiled for 1.10.1, module version = 1.0.0
[    32.878]     ABI class: X.Org ANSI C Emulation, version 0.4
[    32.878] (II) UnloadModule: "fbdev"
[    32.878] (II) Unloading fbdev
[    32.878] (II) UnloadModule: "fbdevhw"
[    32.878] (II) Unloading fbdevhw
[    32.878] (==) Depth 24 pixmap format is 32 bpp
[    32.878] (II) Loading sub module "int10"
[    32.878] (II) LoadModule: "int10"
[    32.878] (II) Loading /usr/lib/xorg/modules/libint10.so
[    32.878] (II) Module int10: vendor="X.Org Foundation"
[    32.878]     compiled for 1.10.1, module version = 1.0.0
[    32.878]     ABI class: X.Org Video Driver, version 10.0
[    32.878] (II) VESA(0): initializing int10
[    32.879] (II) VESA(0): Bad V_BIOS checksum
[    32.879] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    32.879] (II) VESA(0): VESA BIOS detected
[    32.879] (II) VESA(0): VESA VBE Version 3.0
[    32.879] (II) VESA(0): VESA VBE Total Mem: 131008 kB
[    32.879] (II) VESA(0): VESA VBE OEM: Intel(R)Cantiga Graphics Chipset Accelerated VGA BIOS
[    32.879] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    32.879] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    32.879] (II) VESA(0): VESA VBE OEM Product: Intel(R)Cantiga Graphics Controller
[    32.879] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    32.908] (II) VESA(0): virtual address = 0x7fd78d97d000,
    physical address = 0x80000000, size = 134152192
[    32.919] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    32.956] (==) VESA(0): Default visual is TrueColor
[    32.956] (==) VESA(0): Backing store disabled
[    32.956] (==) VESA(0): DPMS enabled
[    32.956] (==) RandR enabled
[    32.956] (II) Initializing built-in extension Generic Event Extension
[    32.956] (II) Initializing built-in extension SHAPE
[    32.956] (II) Initializing built-in extension MIT-SHM
[    32.956] (II) Initializing built-in extension XInputExtension
[    32.956] (II) Initializing built-in extension XTEST
[    32.956] (II) Initializing built-in extension BIG-REQUESTS
[    32.956] (II) Initializing built-in extension SYNC
[    32.956] (II) Initializing built-in extension XKEYBOARD
[    32.956] (II) Initializing built-in extension XC-MISC
[    32.956] (II) Initializing built-in extension SECURITY
[    32.956] (II) Initializing built-in extension XINERAMA
[    32.956] (II) Initializing built-in extension XFIXES
[    32.956] (II) Initializing built-in extension RENDER
[    32.956] (II) Initializing built-in extension RANDR
[    32.956] (II) Initializing built-in extension COMPOSITE
[    32.956] (II) Initializing built-in extension DAMAGE
[    32.956] (II) Initializing built-in extension GESTURE
[    32.962] (II) AIGLX: Screen 0 is not DRI2 capable
[    32.962] (II) AIGLX: Screen 0 is not DRI capable
[    32.962] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    32.976] (II) AIGLX: Loaded and initialized swrast
[    32.976] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    32.986] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    32.995] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    32.995] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    32.995] (II) LoadModule: "evdev"
[    32.995] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.996] (II) Module evdev: vendor="X.Org Foundation"
[    32.996]     compiled for 1.10.0.902, module version = 2.6.0
[    32.996]     Module class: X.Org XInput Driver
[    32.996]     ABI class: X.Org XInput driver, version 12.3
[    32.996] (II) Using input driver 'evdev' for 'Power Button'
[    32.996] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.996] (**) Power Button: always reports core events
[    32.996] (**) Power Button: Device: "/dev/input/event2"
[    32.996] (--) Power Button: Found keys
[    32.996] (II) Power Button: Configuring as keyboard
[    32.996] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    32.996] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    32.996] (**) Option "xkb_rules" "evdev"
[    32.996] (**) Option "xkb_model" "pc105"
[    32.996] (**) Option "xkb_layout" "us"
[    32.997] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    32.997] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    32.997] (II) Using input driver 'evdev' for 'Video Bus'
[    32.997] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    32.997] (**) Video Bus: always reports core events
[    32.997] (**) Video Bus: Device: "/dev/input/event4"
[    32.997] (--) Video Bus: Found keys
[    32.997] (II) Video Bus: Configuring as keyboard
[    32.997] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    32.997] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    32.997] (**) Option "xkb_rules" "evdev"
[    32.997] (**) Option "xkb_model" "pc105"
[    32.997] (**) Option "xkb_layout" "us"
[    33.001] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.001] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    33.001] (II) Using input driver 'evdev' for 'Power Button'
[    33.001] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.001] (**) Power Button: always reports core events
[    33.001] (**) Power Button: Device: "/dev/input/event0"
[    33.001] (--) Power Button: Found keys
[    33.001] (II) Power Button: Configuring as keyboard
[    33.002] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    33.002] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    33.002] (**) Option "xkb_rules" "evdev"
[    33.002] (**) Option "xkb_model" "pc105"
[    33.002] (**) Option "xkb_layout" "us"
[    33.002] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    33.002] (II) No input driver/identifier specified (ignoring)
[    33.010] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    33.010] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    33.010] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    33.010] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    33.010] (**) AT Translated Set 2 keyboard: always reports core events
[    33.010] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    33.010] (--) AT Translated Set 2 keyboard: Found keys
[    33.010] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    33.010] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    33.010] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    33.010] (**) Option "xkb_rules" "evdev"
[    33.010] (**) Option "xkb_model" "pc105"
[    33.010] (**) Option "xkb_layout" "us"
[    33.010] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    33.010] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    33.011] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    33.011] (II) LoadModule: "synaptics"
[    33.011] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.011] (II) Module synaptics: vendor="X.Org Foundation"
[    33.011]     compiled for 1.10.1, module version = 1.3.99
[    33.011]     Module class: X.Org XInput Driver
[    33.011]     ABI class: X.Org XInput driver, version 12.3
[    33.011] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    33.011] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    33.011] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    33.011] (**) Option "Device" "/dev/input/event5"
[    33.011] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692
[    33.011] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680
[    33.011] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    33.011] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    33.011] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    33.011] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    33.011] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    33.011] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    33.011] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    33.011] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    33.011] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    33.011] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.037
[    33.011] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    33.011] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    33.011] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    33.011] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    33.012] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    33.012] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    33.012] (II) No input driver/identifier specified (ignoring)
```

---

### Post by realzippy on 2011-09-22
Try a simple xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

paste in:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync       28.0 - 51.0 
        VertRefresh     50.0 - 65.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```


Btw,a solution for your "reboot problem" might be here:

[http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html](http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html)

---

### Post by Inphernal on 2011-09-22
> **realzippy said:**
> Try a simple xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```paste in:

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
        HorizSync       28.0 - 51.0 
        VertRefresh     50.0 - 65.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
Btw,a solution for your "reboot problem" might be here:

[http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html](http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html)

This boots me into a command line.

Also, thank you for the suggestion on the reboot problem, I will look into that once I can get this figured out.

---

