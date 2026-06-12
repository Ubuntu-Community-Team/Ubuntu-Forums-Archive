---
title: "Random freezing"
date: 2012-07-07
forum: General Help
---

### Post by bluewish on 2012-07-07
For some reason my entire desktop freezes for about 30 - 40 seconds randomly.
For the life of me I can't work out why or what triggers it.

I am using an nVidia GeForce GTX 260 with non-free nVidia drivers.

---

### Post by bluewish on 2012-07-07
No one?

---

### Post by Rexilion on 2012-07-08
Could you please post the output of:

> cat /proc/interrupts
dmesg
lspci -v
cat /var/log/Xorg.0.log

Providing information like this could help getting more response. Your symptoms are very generic and it could be anything.

Furthermore, you could have mentioned whether you are experiencing these freezes without the nvidia binary module??

---

### Post by bluewish on 2012-07-10
Sorry I wasn't very specific. Thanks for replying.
I didn't have the issue before I installed the nVidia drivers.

Outputs:```

** $ cat /proc/interrupts**
           CPU0       CPU1       
  0:         42          2   IO-APIC-edge      timer
  1:          1          1   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          2          2   IO-APIC-edge      i8042
 14:       6763       6346   IO-APIC-edge      ata_piix
 15:        420        418   IO-APIC-edge      ata_piix
 16:       1859       3671   IO-APIC-fasteoi   uhci_hcd:usb5, nvidia
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          7         19   IO-APIC-fasteoi   uhci_hcd:usb3, snd_ens1371
 23:      74337      13502   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
 43:        237        173   PCI-MSI-edge      snd_hda_intel
 44:          1          1   PCI-MSI-edge      eth0
NMI:         27         33   Non-maskable interrupts
LOC:      23551      24410   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:         27         33   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RES:      55186      62652   Rescheduling interrupts
CAL:        265       2063   Function call interrupts
TLB:        989        856   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          2          2   Machine check polls
ERR:          0
MIS:          0

**$ dmesg | grep nvidia**
[   21.924596] nvidia: module license 'NVIDIA' taints kernel.
[   22.121310] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.121317] nvidia 0000:01:00.0: setting latency timer to 64

**$ lspci -v**
01:00.0 VGA compatible controller: NVIDIA Corporation GT200 [GeForce GTX 260] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device 068e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at da000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at cf00 [size=128]
    [virtual] Expansion ROM at dd000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

[B]$ cat /var/log/Xorg.0.log
[/B][    23.660] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    23.660] X Protocol Version 11, Revision 0
[    23.660] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[    23.660] Current Operating System: Linux Skaro 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64
[    23.660] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=fdebe57d-12c9-4aff-b4bc-e923da503f62 ro quiet splash vt.handoff=7
[    23.660] Build Date: 26 June 2012  06:59:03AM
[    23.660] xorg-server 2:1.11.4-0ubuntu10.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    23.660] Current version of pixman: 0.24.4
[    23.660]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    23.660] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.660] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 11 01:03:11 2012
[    23.660] (==) Using config file: "/etc/X11/xorg.conf"
[    23.660] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.660] (==) No Layout section.  Using the first Screen section.
[    23.660] (==) No screen section available. Using defaults.
[    23.660] (**) |-->Screen "Default Screen Section" (0)
[    23.660] (**) |   |-->Monitor "<default monitor>"
[    23.660] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    23.661] (**) |   |-->Device "Default Device"
[    23.661] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    23.661] (==) Automatically adding devices
[    23.661] (==) Automatically enabling devices
[    23.661] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.661]     Entry deleted from font path.
[    23.661] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.661]     Entry deleted from font path.
[    23.661] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.661]     Entry deleted from font path.
[    23.661] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.661]     Entry deleted from font path.
[    23.661] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.661]     Entry deleted from font path.
[    23.661] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    23.661]     Entry deleted from font path.
[    23.661] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    23.661] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.661] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.661] (II) Loader magic: 0x7fe2f657db00
[    23.661] (II) Module ABI versions:
[    23.661]     X.Org ANSI C Emulation: 0.4
[    23.661]     X.Org Video Driver: 11.0
[    23.661]     X.Org XInput driver : 16.0
[    23.661]     X.Org Server Extension : 6.0
[    23.661] (--) PCI:*(0:1:0:0) 10de:05e2:10de:068e rev 161, Mem @ 0xdc000000/16777216, 0xc0000000/268435456, 0xda000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/524288
[    23.661] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.661] (II) LoadModule: "extmod"
[    23.662] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.662] (II) Module extmod: vendor="X.Org Foundation"
[    23.662]     compiled for 1.11.3, module version = 1.0.0
[    23.662]     Module class: X.Org Server Extension
[    23.662]     ABI class: X.Org Server Extension, version 6.0
[    23.662] (II) Loading extension MIT-SCREEN-SAVER
[    23.662] (II) Loading extension XFree86-VidModeExtension
[    23.662] (II) Loading extension XFree86-DGA
[    23.662] (II) Loading extension DPMS
[    23.662] (II) Loading extension XVideo
[    23.662] (II) Loading extension XVideo-MotionCompensation
[    23.662] (II) Loading extension X-Resource
[    23.662] (II) LoadModule: "dbe"
[    23.662] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.662] (II) Module dbe: vendor="X.Org Foundation"
[    23.662]     compiled for 1.11.3, module version = 1.0.0
[    23.662]     Module class: X.Org Server Extension
[    23.662]     ABI class: X.Org Server Extension, version 6.0
[    23.662] (II) Loading extension DOUBLE-BUFFER
[    23.662] (II) LoadModule: "glx"
[    23.662] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    23.673] (II) Module glx: vendor="NVIDIA Corporation"
[    23.673]     compiled for 4.0.2, module version = 1.0.0
[    23.673]     Module class: X.Org Server Extension
[    23.673] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    23.673] (II) Loading extension GLX
[    23.673] (II) LoadModule: "record"
[    23.673] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.673] (II) Module record: vendor="X.Org Foundation"
[    23.673]     compiled for 1.11.3, module version = 1.13.0
[    23.673]     Module class: X.Org Server Extension
[    23.673]     ABI class: X.Org Server Extension, version 6.0
[    23.673] (II) Loading extension RECORD
[    23.673] (II) LoadModule: "dri"
[    23.674] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.674] (II) Module dri: vendor="X.Org Foundation"
[    23.674]     compiled for 1.11.3, module version = 1.0.0
[    23.674]     ABI class: X.Org Server Extension, version 6.0
[    23.674] (II) Loading extension XFree86-DRI
[    23.674] (II) LoadModule: "dri2"
[    23.674] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.674] (II) Module dri2: vendor="X.Org Foundation"
[    23.674]     compiled for 1.11.3, module version = 1.2.0
[    23.674]     ABI class: X.Org Server Extension, version 6.0
[    23.674] (II) Loading extension DRI2
[    23.674] (==) Matched nvidia as autoconfigured driver 0
[    23.674] (==) Matched nouveau as autoconfigured driver 1
[    23.674] (==) Matched nv as autoconfigured driver 2
[    23.674] (==) Matched vesa as autoconfigured driver 3
[    23.674] (==) Matched fbdev as autoconfigured driver 4
[    23.674] (==) Assigned the driver to the xf86ConfigLayout
[    23.674] (II) LoadModule: "nvidia"
[    23.674] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.675] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.675]     compiled for 4.0.2, module version = 1.0.0
[    23.675]     Module class: X.Org Video Driver
[    23.675] (II) LoadModule: "nouveau"
[    23.675] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.675] (II) Module nouveau: vendor="X.Org Foundation"
[    23.675]     compiled for 1.11.3, module version = 0.0.16
[    23.675]     Module class: X.Org Video Driver
[    23.675]     ABI class: X.Org Video Driver, version 11.0
[    23.675] (II) LoadModule: "nv"
[    23.700] (WW) Warning, couldn't open module nv
[    23.700] (II) UnloadModule: "nv"
[    23.700] (II) Unloading nv
[    23.700] (EE) Failed to load module "nv" (module does not exist, 0)
[    23.700] (II) LoadModule: "vesa"
[    23.700] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.700] (II) Module vesa: vendor="X.Org Foundation"
[    23.700]     compiled for 1.11.3, module version = 2.3.0
[    23.700]     Module class: X.Org Video Driver
[    23.700]     ABI class: X.Org Video Driver, version 11.0
[    23.700] (II) LoadModule: "fbdev"
[    23.700] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.700] (II) Module fbdev: vendor="X.Org Foundation"
[    23.700]     compiled for 1.11.3, module version = 0.4.2
[    23.700]     ABI class: X.Org Video Driver, version 11.0
[    23.700] (==) Matched nvidia as autoconfigured driver 0
[    23.700] (==) Matched nouveau as autoconfigured driver 1
[    23.700] (==) Matched nv as autoconfigured driver 2
[    23.700] (==) Matched vesa as autoconfigured driver 3
[    23.700] (==) Matched fbdev as autoconfigured driver 4
[    23.700] (==) Assigned the driver to the xf86ConfigLayout
[    23.700] (II) LoadModule: "nvidia"
[    23.700] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.700] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.700]     compiled for 4.0.2, module version = 1.0.0
[    23.700]     Module class: X.Org Video Driver
[    23.700] (II) UnloadModule: "nvidia"
[    23.700] (II) Unloading nvidia
[    23.700] (II) Failed to load module "nvidia" (already loaded, 32738)
[    23.700] (II) LoadModule: "nouveau"
[    23.700] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.700] (II) Module nouveau: vendor="X.Org Foundation"
[    23.700]     compiled for 1.11.3, module version = 0.0.16
[    23.700]     Module class: X.Org Video Driver
[    23.700]     ABI class: X.Org Video Driver, version 11.0
[    23.700] (II) UnloadModule: "nouveau"
[    23.700] (II) Unloading nouveau
[    23.700] (II) Failed to load module "nouveau" (already loaded, 32738)
[    23.700] (II) LoadModule: "nv"
[    23.701] (WW) Warning, couldn't open module nv
[    23.701] (II) UnloadModule: "nv"
[    23.701] (II) Unloading nv
[    23.701] (EE) Failed to load module "nv" (module does not exist, 0)
[    23.701] (II) LoadModule: "vesa"
[    23.701] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.701] (II) Module vesa: vendor="X.Org Foundation"
[    23.701]     compiled for 1.11.3, module version = 2.3.0
[    23.701]     Module class: X.Org Video Driver
[    23.701]     ABI class: X.Org Video Driver, version 11.0
[    23.701] (II) UnloadModule: "vesa"
[    23.701] (II) Unloading vesa
[    23.701] (II) Failed to load module "vesa" (already loaded, 0)
[    23.701] (II) LoadModule: "fbdev"
[    23.701] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.701] (II) Module fbdev: vendor="X.Org Foundation"
[    23.701]     compiled for 1.11.3, module version = 0.4.2
[    23.701]     ABI class: X.Org Video Driver, version 11.0
[    23.701] (II) UnloadModule: "fbdev"
[    23.701] (II) Unloading fbdev
[    23.701] (II) Failed to load module "fbdev" (already loaded, 0)
[    23.701] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[    23.701] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    23.701] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[    23.701] (II) NOUVEAU driver for NVIDIA chipset families :
[    23.701]     RIVA TNT        (NV04)
[    23.701]     RIVA TNT2       (NV05)
[    23.701]     GeForce 256     (NV10)
[    23.701]     GeForce 2       (NV11, NV15)
[    23.701]     GeForce 4MX     (NV17, NV18)
[    23.701]     GeForce 3       (NV20)
[    23.701]     GeForce 4Ti     (NV25, NV28)
[    23.701]     GeForce FX      (NV3x)
[    23.701]     GeForce 6       (NV4x)
[    23.702]     GeForce 7       (G7x)
[    23.702]     GeForce 8       (G8x)
[    23.702]     GeForce GTX 200 (NVA0)
[    23.702]     GeForce GTX 400 (NVC0)
[    23.702] (II) VESA: driver for VESA chipsets: vesa
[    23.702] (II) FBDEV: driver for framebuffer: fbdev
[    23.702] (++) using VT number 7

[    23.702] (II) Loading sub module "fb"
[    23.702] (II) LoadModule: "fb"
[    23.702] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.702] (II) Module fb: vendor="X.Org Foundation"
[    23.702]     compiled for 1.11.3, module version = 1.0.0
[    23.702]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.702] (II) Loading sub module "wfb"
[    23.702] (II) LoadModule: "wfb"
[    23.702] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.702] (II) Module wfb: vendor="X.Org Foundation"
[    23.702]     compiled for 1.11.3, module version = 1.0.0
[    23.702]     ABI class: X.Org ANSI C Emulation, version 0.4
[    23.702] (II) Loading sub module "ramdac"
[    23.702] (II) LoadModule: "ramdac"
[    23.702] (II) Module "ramdac" already built-in
[    23.702] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.702] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.702] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.702] (WW) Falling back to old probe method for vesa
[    23.702] (WW) Falling back to old probe method for fbdev
[    23.702] (II) Loading sub module "fbdevhw"
[    23.702] (II) LoadModule: "fbdevhw"
[    23.702] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.702] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.702]     compiled for 1.11.3, module version = 0.0.2
[    23.702]     ABI class: X.Org Video Driver, version 11.0
[    23.703] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.703] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    23.703] (==) NVIDIA(0): RGB weight 888
[    23.703] (==) NVIDIA(0): Default visual is TrueColor
[    23.703] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.703] (**) NVIDIA(0): Option "NoLogo" "True"
[    23.703] (**) NVIDIA(0): Enabling 2D acceleration
[    25.378] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc ASUS VH242H (DFP-1)) does
[    25.378] (II) NVIDIA(GPU-0):     not support NVIDIA 3D Vision stereo.
[    25.379] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 260 (GT200) at PCI:1:0:0 (GPU-0)
[    25.379] (--) NVIDIA(0): Memory: 917504 kBytes
[    25.379] (--) NVIDIA(0): VideoBIOS: 62.00.4c.00.02
[    25.379] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    25.379] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    25.381] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 260 at PCI:1:0:0
[    25.381] (--) NVIDIA(0):     Ancor Communications Inc ASUS VH242H (DFP-1)
[    25.381] (--) NVIDIA(0): Ancor Communications Inc ASUS VH242H (DFP-1): 330.0 MHz
[    25.381] (--) NVIDIA(0):     maximum pixel clock
[    25.381] (--) NVIDIA(0): Ancor Communications Inc ASUS VH242H (DFP-1): Internal Dual
[    25.381] (--) NVIDIA(0):     Link TMDS
[    25.416] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    25.416] (**) NVIDIA(0):     device Ancor Communications Inc ASUS VH242H (DFP-1) (Using
[    25.416] (**) NVIDIA(0):     EDID frequencies has been enabled on all display
[    25.416] (**) NVIDIA(0):     devices.)
[    25.461] (II) NVIDIA(0): Assigned Display Device: DFP-1
[    25.462] (==) NVIDIA(0): 
[    25.462] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    25.462] (==) NVIDIA(0):     will be used as the requested mode.
[    25.462] (==) NVIDIA(0): 
[    25.462] (II) NVIDIA(0): Validated modes:
[    25.462] (II) NVIDIA(0):     "nvidia-auto-select"
[    25.462] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    25.499] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    25.499] (--) NVIDIA(0):     option
[    25.499] (II) UnloadModule: "nouveau"
[    25.499] (II) Unloading nouveau
[    25.499] (II) UnloadModule: "vesa"
[    25.499] (II) Unloading vesa
[    25.499] (II) UnloadModule: "fbdev"
[    25.499] (II) Unloading fbdev
[    25.499] (II) UnloadModule: "fbdevhw"
[    25.499] (II) Unloading fbdevhw
[    25.499] (--) Depth 24 pixmap format is 32 bpp
[    25.499] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    25.504] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    25.525] (II) Loading extension NV-GLX
[    25.559] (==) NVIDIA(0): Disabling shared memory pixmaps
[    25.559] (==) NVIDIA(0): Backing store disabled
[    25.559] (==) NVIDIA(0): Silken mouse enabled
[    25.559] (==) NVIDIA(0): DPMS enabled
[    25.559] (II) Loading extension NV-CONTROL
[    25.560] (II) Loading extension XINERAMA
[    25.560] (II) Loading sub module "dri2"
[    25.560] (II) LoadModule: "dri2"
[    25.560] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.560] (II) Module dri2: vendor="X.Org Foundation"
[    25.560]     compiled for 1.11.3, module version = 1.2.0
[    25.560]     ABI class: X.Org Server Extension, version 6.0
[    25.560] (II) NVIDIA(0): [DRI2] Setup complete
[    25.560] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    25.560] (==) RandR enabled
[    25.560] (II) Initializing built-in extension Generic Event Extension
[    25.560] (II) Initializing built-in extension SHAPE
[    25.560] (II) Initializing built-in extension MIT-SHM
[    25.560] (II) Initializing built-in extension XInputExtension
[    25.560] (II) Initializing built-in extension XTEST
[    25.560] (II) Initializing built-in extension BIG-REQUESTS
[    25.560] (II) Initializing built-in extension SYNC
[    25.560] (II) Initializing built-in extension XKEYBOARD
[    25.560] (II) Initializing built-in extension XC-MISC
[    25.560] (II) Initializing built-in extension SECURITY
[    25.560] (II) Initializing built-in extension XINERAMA
[    25.560] (II) Initializing built-in extension XFIXES
[    25.560] (II) Initializing built-in extension RENDER
[    25.560] (II) Initializing built-in extension RANDR
[    25.560] (II) Initializing built-in extension COMPOSITE
[    25.560] (II) Initializing built-in extension DAMAGE
[    25.562] (II) Initializing extension GLX
[    25.576] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.579] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    25.579] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.579] (II) LoadModule: "evdev"
[    25.579] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.579] (II) Module evdev: vendor="X.Org Foundation"
[    25.579]     compiled for 1.11.3, module version = 2.7.0
[    25.579]     Module class: X.Org XInput Driver
[    25.579]     ABI class: X.Org XInput driver, version 16.0
[    25.579] (II) Using input driver 'evdev' for 'Power Button'
[    25.579] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.579] (**) Power Button: always reports core events
[    25.579] (**) evdev: Power Button: Device: "/dev/input/event1"
[    25.579] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.579] (--) evdev: Power Button: Found keys
[    25.579] (II) evdev: Power Button: Configuring as keyboard
[    25.579] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    25.579] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.579] (**) Option "xkb_rules" "evdev"
[    25.579] (**) Option "xkb_model" "pc105"
[    25.579] (**) Option "xkb_layout" "us"
[    25.580] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.580] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.580] (II) Using input driver 'evdev' for 'Power Button'
[    25.580] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.580] (**) Power Button: always reports core events
[    25.580] (**) evdev: Power Button: Device: "/dev/input/event0"
[    25.580] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.580] (--) evdev: Power Button: Found keys
[    25.580] (II) evdev: Power Button: Configuring as keyboard
[    25.580] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    25.580] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    25.580] (**) Option "xkb_rules" "evdev"
[    25.580] (**) Option "xkb_model" "pc105"
[    25.580] (**) Option "xkb_layout" "us"
[    25.580] (II) config/udev: Adding input device HDA Intel Line-Out (/dev/input/event10)
[    25.580] (II) No input driver specified, ignoring this device.
[    25.581] (II) This device may have been added with another device file.
[    25.581] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event6)
[    25.581] (II) No input driver specified, ignoring this device.
[    25.581] (II) This device may have been added with another device file.
[    25.581] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event7)
[    25.581] (II) No input driver specified, ignoring this device.
[    25.581] (II) This device may have been added with another device file.
[    25.581] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event8)
[    25.581] (II) No input driver specified, ignoring this device.
[    25.581] (II) This device may have been added with another device file.
[    25.581] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event9)
[    25.581] (II) No input driver specified, ignoring this device.
[    25.581] (II) This device may have been added with another device file.
[    25.582] (II) config/udev: Adding input device Gaming Keyboard (/dev/input/event2)
[    25.582] (**) Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    25.582] (II) Using input driver 'evdev' for 'Gaming Keyboard'
[    25.582] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.582] (**) Gaming Keyboard: always reports core events
[    25.582] (**) evdev: Gaming Keyboard: Device: "/dev/input/event2"
[    25.582] (--) evdev: Gaming Keyboard: Vendor 0x46d Product 0xc221
[    25.582] (--) evdev: Gaming Keyboard: Found keys
[    25.582] (II) evdev: Gaming Keyboard: Configuring as keyboard
[    25.582] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.1/5-2.1:1.0/input/input2/event2"
[    25.582] (II) XINPUT: Adding extended input device "Gaming Keyboard" (type: KEYBOARD, id 8)
[    25.582] (**) Option "xkb_rules" "evdev"
[    25.582] (**) Option "xkb_model" "pc105"
[    25.582] (**) Option "xkb_layout" "us"
[    25.582] (II) config/udev: Adding input device Gaming Keyboard (/dev/input/event3)
[    25.582] (**) Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    25.582] (II) Using input driver 'evdev' for 'Gaming Keyboard'
[    25.582] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.582] (**) Gaming Keyboard: always reports core events
[    25.582] (**) evdev: Gaming Keyboard: Device: "/dev/input/event3"
[    25.582] (--) evdev: Gaming Keyboard: Vendor 0x46d Product 0xc221
[    25.582] (--) evdev: Gaming Keyboard: Found keys
[    25.582] (II) evdev: Gaming Keyboard: Configuring as keyboard
[    25.582] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.1/5-2.1:1.1/input/input3/event3"
[    25.582] (II) XINPUT: Adding extended input device "Gaming Keyboard" (type: KEYBOARD, id 9)
[    25.582] (**) Option "xkb_rules" "evdev"
[    25.582] (**) Option "xkb_model" "pc105"
[    25.582] (**) Option "xkb_layout" "us"
[    25.583] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
[    25.583] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[    25.583] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[    25.583] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.583] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[    25.583] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[    25.583] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc045
[    25.583] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[    25.583] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[    25.583] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes
[    25.583] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[    25.583] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[    25.583] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[    25.583] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[    25.583] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    25.583] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.3/5-2.3:1.0/input/input4/event4"
[    25.583] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 10)
[    25.583] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[    25.583] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[    25.583] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[    25.583] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[    25.583] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[    25.584] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[    25.584] (II) No input driver specified, ignoring this device.
[    25.584] (II) This device may have been added with another device file.
[    25.584] (II) config/udev: Adding input device G11 Keyboard (/dev/input/event5)
[    25.584] (**) G11 Keyboard: Applying InputClass "evdev keyboard catchall"
[    25.584] (II) Using input driver 'evdev' for 'G11 Keyboard'
[    25.584] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.584] (**) G11 Keyboard: always reports core events
[    25.584] (**) evdev: G11 Keyboard: Device: "/dev/input/event5"
[    25.584] (--) evdev: G11 Keyboard: Vendor 0x46d Product 0xc225
[    25.584] (--) evdev: G11 Keyboard: Found keys
[    25.584] (II) evdev: G11 Keyboard: Configuring as keyboard
[    25.584] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2.4/5-2.4:1.0/input/input5/event5"
[    25.584] (II) XINPUT: Adding extended input device "G11 Keyboard" (type: KEYBOARD, id 11)
[    25.584] (**) Option "xkb_rules" "evdev"
[    25.584] (**) Option "xkb_model" "pc105"
[    25.584] (**) Option "xkb_layout" "us"
[    25.584] (II) config/udev: Adding input device Microsoft® LifeCam HD-5000 (/dev/input/event11)
[    25.584] (**) Microsoft® LifeCam HD-5000: Applying InputClass "evdev keyboard catchall"
[    25.584] (II) Using input driver 'evdev' for 'Microsoft® LifeCam HD-5000'
[    25.584] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.584] (**) Microsoft® LifeCam HD-5000: always reports core events
[    25.584] (**) evdev: Microsoft® LifeCam HD-5000: Device: "/dev/input/event11"
[    25.585] (--) evdev: Microsoft® LifeCam HD-5000: Vendor 0x45e Product 0x76d
[    25.585] (--) evdev: Microsoft® LifeCam HD-5000: Found keys
[    25.585] (II) evdev: Microsoft® LifeCam HD-5000: Configuring as keyboard
[    25.585] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input11/event11"
[    25.585] (II) XINPUT: Adding extended input device "Microsoft® LifeCam HD-5000" (type: KEYBOARD, id 12)
[    25.585] (**) Option "xkb_rules" "evdev"
[    25.585] (**) Option "xkb_model" "pc105"
[    25.585] (**) Option "xkb_layout" "us"

```

---

### Post by Rexilion on 2012-08-25
>     Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

Big red flag!

---

