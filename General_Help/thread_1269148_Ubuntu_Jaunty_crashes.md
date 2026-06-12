---
title: "Ubuntu Jaunty crashes"
date: 2009-09-17
forum: General Help
---

### Post by rasmusero on 2009-09-17
Hey everyone! I decided to post because I can't find the solution to this problem I'm having with Ubuntu 9.04. I'm pretty new at using Ubuntu, so logs are not familiar to me, nor I know how to read them. The problem is that Ubuntu crashes sometimes when I'm doing multitasking and other times when I'm just using gedit. Someone told me it might be useful (though not useful to me) to type this commands. I'll transcribe them:

~$ lspci

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)

~$ cat /var/log/Xorg.0.log |less

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux andromeda 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 
i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 17 22:24:07 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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

(--) PCI:*(0@1:0:0) nVidia Corporation G72 [GeForce 7300 SE] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
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
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
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
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 SE/7200 GS (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.80.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 SE/7200 GS at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     LG M197WA (DFP-0)
(--) NVIDIA(0): LG M197WA (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): LG M197WA (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1360 x 768
(--) NVIDIA(0): DPI set to (84, 84); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
        compiled for 1.6.0, module version = 2.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) AT Translated Set 2 keyboard: xkb_layout: "es"
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
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0

~$ cat /var/log/messages |less

Sep 17 20:46:21 andromeda kernel: [  344.272361] USB Mass Storage support registered.
Sep 17 20:46:26 andromeda kernel: [  349.277364] scsi 4:0:0:0: Direct-Access     Kingston DT 101 II        PMAP PQ: 0 ANSI: 0 CCS
Sep 17 20:46:29 andromeda kernel: [  351.618639] sd 4:0:0:0: [sdb] 15667200 512-byte hardware sectors: (8.02 GB/7.47 GiB)
Sep 17 20:46:29 andromeda kernel: [  351.619125] sd 4:0:0:0: [sdb] Write Protect is off
Sep 17 20:46:29 andromeda kernel: [  351.622387] sd 4:0:0:0: [sdb] 15667200 512-byte hardware sectors: (8.02 GB/7.47 GiB)
Sep 17 20:46:29 andromeda kernel: [  351.622876] sd 4:0:0:0: [sdb] Write Protect is off
Sep 17 20:46:29 andromeda kernel: [  351.622892]  sdb: sdb1
Sep 17 20:46:29 andromeda kernel: [  351.623568] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Sep 17 20:46:29 andromeda kernel: [  351.623680] sd 4:0:0:0: Attached scsi generic sg2 type 0
Sep 17 21:00:50 andromeda -- MARK --
Sep 17 21:20:50 andromeda -- MARK --
Sep 17 21:40:50 andromeda -- MARK --
Sep 17 22:00:50 andromeda -- MARK --
Sep 17 22:13:23 andromeda kernel: [ 5565.931133] usb 1-6: USB disconnect, address 3
Sep 17 22:24:04 andromeda syslogd 1.5.0#5ubuntu3: restart.
Sep 17 22:24:05 andromeda kernel: Inspecting /boot/System.map-2.6.28-15-generic
Sep 17 22:24:05 andromeda kernel: Cannot find map file.
Sep 17 22:24:05 andromeda kernel: Loaded 72796 symbols from 41 modules.
Sep 17 22:24:05 andromeda kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Sep 17 22:24:05 andromeda kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 17 22:24:05 andromeda kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 17 22:24:05 andromeda kernel: [    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
Sep 17 22:24:05 andromeda kernel: [    0.000000] KERNEL supported cpus:
Sep 17 22:24:05 andromeda kernel: [    0.000000]   Intel GenuineIntel
Sep 17 22:24:05 andromeda kernel: [    0.000000]   AMD AuthenticAMD
Sep 17 22:24:05 andromeda kernel: [    0.000000]   NSC Geode by NSC
Sep 17 22:24:05 andromeda kernel: [    0.000000]   Cyrix CyrixInstead
Sep 17 22:24:05 andromeda kernel: [    0.000000]   Centaur CentaurHauls
Sep 17 22:24:05 andromeda kernel: [    0.000000]   Transmeta GenuineTMx86
Sep 17 22:24:05 andromeda kernel: [    0.000000]   Transmeta TransmetaCPU
Sep 17 22:24:05 andromeda kernel: [    0.000000]   UMC UMC UMC UMC
Sep 17 22:24:05 andromeda kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Sep 17 22:24:05 andromeda kernel: [    0.000000] DMI present.
Sep 17 22:24:05 andromeda kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
Sep 17 22:24:05 andromeda kernel: [    0.000000] last_pfn = 0xbffa0 max_arch_pfn = 0x100000
Sep 17 22:24:05 andromeda kernel: [    0.000000] Scanning 0 areas for low memory corruption
Sep 17 22:24:05 andromeda kernel: [    0.000000] modified physical RAM map:
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 0000000000100000 - 00000000bffa0000 (usable)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 00000000bffa0000 - 00000000bffae000 (ACPI data)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Sep 17 22:24:05 andromeda kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Sep 17 22:24:05 andromeda kernel: [    0.000000] RAMDISK: 378ba000 - 37fef752
Sep 17 22:24:05 andromeda kernel: [    0.000000] Allocated new RAMDISK: 0087d000 - 00fb2752
Sep 17 22:24:05 andromeda kernel: [    0.000000] Move RAMDISK from 00000000378ba000 - 0000000037fef751 to 0087d000 - 00fb2751
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: RSDP 000FB650, 0014 (r0 ACPIAM)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: RSDT BFFA0000, 003C (r1 091707 RSDT1623 20070917 MSFT       97)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: FACP BFFA0200, 0084 (r1 091707 FACP1623 20070917 MSFT       97)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: DSDT BFFA0610, 67F4 (r1  A0857 A0857000        0 INTL 20051117)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: FACS BFFAE000, 0040
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: APIC BFFA0390, 006C (r1 091707 APIC1623 20070917 MSFT       97)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: MCFG BFFA0400, 003C (r1 091707 OEMMCFG  20070917 MSFT       97)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: WDRT BFFA05C0, 0047 (r1 091707 OEMWDRT  20070917 MSFT       97)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: OEMB BFFAE040, 0071 (r1 091707 OEMB1623 20070917 MSFT       97)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: HPET BFFA6E10, 0038 (r1 091707 OEMHPET  20070917 MSFT       97)
Sep 17 22:24:05 andromeda kernel: [    0.000000] 2187MB HIGHMEM available.
Sep 17 22:24:05 andromeda kernel: [    0.000000] 883MB LOWMEM available.
Sep 17 22:24:05 andromeda kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Sep 17 22:24:05 andromeda kernel: [    0.000000]   low ram: 00000000 - 373fe000
Sep 17 22:24:05 andromeda kernel: [    0.000000]   bootmap 00012000 - 00018e80
Sep 17 22:24:05 andromeda kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #7 [000087d000 - 0000fb2752]      NEW RAMDISK ==> [000087d000 - 0000fb2752]
Sep 17 22:24:05 andromeda kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Sep 17 22:24:05 andromeda kernel: [    0.000000] found SMP MP-table at [c00ff780] 000ff780
Sep 17 22:24:05 andromeda kernel: [    0.000000] Zone PFN ranges:
Sep 17 22:24:05 andromeda kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Sep 17 22:24:05 andromeda kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Sep 17 22:24:05 andromeda kernel: [    0.000000]   HighMem  0x000373fe -> 0x000bffa0
Sep 17 22:24:05 andromeda kernel: [    0.000000] Movable zone start PFN for each node
Sep 17 22:24:05 andromeda kernel: [    0.000000] early_node_map[2] active PFN ranges
Sep 17 22:24:05 andromeda kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Sep 17 22:24:05 andromeda kernel: [    0.000000]     0: 0x00000100 -> 0x000bffa0
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep 17 22:24:05 andromeda kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Sep 17 22:24:05 andromeda kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 17 22:24:05 andromeda kernel: [    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
Sep 17 22:24:05 andromeda kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 17 22:24:05 andromeda kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Sep 17 22:24:05 andromeda kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 22:24:05 andromeda kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Sep 17 22:24:05 andromeda kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Sep 17 22:24:05 andromeda kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ee00000)
Sep 17 22:24:05 andromeda kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Sep 17 22:24:05 andromeda kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780079
Sep 17 22:24:05 andromeda kernel: [    0.000000] Kernel command line: root=UUID=c1e568dd-41b0-46ef-a6f8-291b40ef534e ro quiet splash 
Sep 17 22:24:05 andromeda kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 17 22:24:05 andromeda kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 17 22:24:05 andromeda kernel: [    0.000000] Initializing CPU#0
Sep 17 22:24:05 andromeda kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep 17 22:24:05 andromeda kernel: [    0.000000] Fast TSC calibration using PIT
Sep 17 22:24:05 andromeda kernel: [    0.000000] Detected 1800.039 MHz processor.
Sep 17 22:24:05 andromeda kernel: [    0.004000] Console: colour VGA+ 80x25
Sep 17 22:24:05 andromeda kernel: [    0.004000] console [tty0] enabled
Sep 17 22:24:05 andromeda kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 17 22:24:05 andromeda kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 17 22:24:05 andromeda kernel: [    0.004000] allocated 15726400 bytes of page_cgroup
Sep 17 22:24:05 andromeda kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Sep 17 22:24:05 andromeda kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Sep 17 22:24:05 andromeda kernel: [    0.004000] Memory: 3087908k/3145344k available (4115k kernel code, 56048k reserved, 2199k data, 532k init, 2240136k highmem)
Sep 17 22:24:05 andromeda kernel: [    0.004000] virtual kernel memory layout:
Sep 17 22:24:05 andromeda kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Sep 17 22:24:05 andromeda kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Sep 17 22:24:05 andromeda kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Sep 17 22:24:05 andromeda kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Sep 17 22:24:05 andromeda kernel: [    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
Sep 17 22:24:05 andromeda kernel: [    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
Sep 17 22:24:05 andromeda kernel: [    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
Sep 17 22:24:05 andromeda kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Sep 17 22:24:05 andromeda kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Sep 17 22:24:05 andromeda kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Sep 17 22:24:05 andromeda kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.07 BogoMIPS (lpj=7200156)
Sep 17 22:24:05 andromeda kernel: [    0.004000] Security Framework initialized
Sep 17 22:24:05 andromeda kernel: [    0.004000] SELinux:  Disabled at boot.
Sep 17 22:24:05 andromeda kernel: [    0.004000] AppArmor: AppArmor initialized
Sep 17 22:24:05 andromeda kernel: [    0.004000] Mount-cache hash table entries: 512
Sep 17 22:24:05 andromeda kernel: [    0.004000] Initializing cgroup subsys ns
Sep 17 22:24:05 andromeda kernel: [    0.004000] Initializing cgroup subsys cpuacct
Sep 17 22:24:05 andromeda kernel: [    0.004000] Initializing cgroup subsys memory
Sep 17 22:24:05 andromeda kernel: [    0.004000] Initializing cgroup subsys freezer
Sep 17 22:24:05 andromeda kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 17 22:24:05 andromeda kernel: [    0.004000] CPU: L2 cache: 1024K
Sep 17 22:24:05 andromeda kernel: [    0.004000] CPU: Physical Processor ID: 0
Sep 17 22:24:05 andromeda kernel: [    0.004000] CPU: Processor Core ID: 0
Sep 17 22:24:05 andromeda kernel: [    0.004000] using mwait in idle threads.
Sep 17 22:24:05 andromeda kernel: [    0.004000] Checking 'hlt' instruction... OK.
Sep 17 22:24:05 andromeda kernel: [    0.018842] ACPI: Core revision 20080926
Sep 17 22:24:05 andromeda kernel: [    0.022335] ACPI: Checking initramfs for custom DSDT
Sep 17 22:24:05 andromeda kernel: [    0.350534] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 17 22:24:05 andromeda kernel: [    0.390232] CPU0: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz stepping 0d
Sep 17 22:24:05 andromeda kernel: [    0.392001] Booting processor 1 APIC 0x1 ip 0x6000
Sep 17 22:24:05 andromeda kernel: [    0.004000] Initializing CPU#1
Sep 17 22:24:05 andromeda kernel: [    0.004000] Calibrating delay using timer specific routine.. 3599.90 BogoMIPS (lpj=7199802)
Sep 17 22:24:05 andromeda kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 17 22:24:05 andromeda kernel: [    0.004000] CPU: L2 cache: 1024K
Sep 17 22:24:05 andromeda kernel: [    0.004000] CPU: Physical Processor ID: 0
Sep 17 22:24:05 andromeda kernel: [    0.004000] CPU: Processor Core ID: 1
Sep 17 22:24:05 andromeda kernel: [    0.476404] CPU1: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz stepping 0d
Sep 17 22:24:05 andromeda kernel: [    0.476422] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Sep 17 22:24:05 andromeda kernel: [    0.480051] Brought up 2 CPUs
Sep 17 22:24:05 andromeda kernel: [    0.480055] Total of 2 processors activated (7199.97 BogoMIPS).
Sep 17 22:24:05 andromeda kernel: [    0.480203] net_namespace: 776 bytes
Sep 17 22:24:05 andromeda kernel: [    0.480203] Booting paravirtualized kernel on bare hardware
Sep 17 22:24:05 andromeda kernel: [    0.480387] Time: 22:23:51  Date: 09/17/09
Sep 17 22:24:05 andromeda kernel: [    0.480387] regulator: core version 0.5
Sep 17 22:24:05 andromeda kernel: [    0.480387] NET: Registered protocol family 16
Sep 17 22:24:05 andromeda kernel: [    0.480387] EISA bus registered
Sep 17 22:24:05 andromeda kernel: [    0.480387] ACPI: bus type pci registered
Sep 17 22:24:05 andromeda kernel: [    0.480387] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Sep 17 22:24:05 andromeda kernel: [    0.480387] PCI: Not using MMCONFIG.
Sep 17 22:24:05 andromeda kernel: [    0.481420] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
Sep 17 22:24:05 andromeda kernel: [    0.481422] PCI: Using configuration type 1 for base access
Sep 17 22:24:05 andromeda kernel: [    0.495487] ACPI: Interpreter enabled
Sep 17 22:24:05 andromeda kernel: [    0.495494] ACPI: (supports S0 S1 S3 S4 S5)
Sep 17 22:24:05 andromeda kernel: [    0.495517] ACPI: Using IOAPIC for interrupt routing
Sep 17 22:24:05 andromeda kernel: [    0.495577] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Sep 17 22:24:05 andromeda kernel: [    0.499500] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Sep 17 22:24:05 andromeda kernel: [    0.499502] PCI: Using MMCONFIG for extended config space
Sep 17 22:24:05 andromeda kernel: [    0.506726] ACPI: No dock devices found.
Sep 17 22:24:05 andromeda kernel: [    0.506790] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 17 22:24:05 andromeda kernel: [    0.506908] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Sep 17 22:24:05 andromeda kernel: [    0.506913] pci 0000:00:01.0: PME# disabled
Sep 17 22:24:05 andromeda kernel: [    0.507050] pci 0000:00:02.5: PME# supported from D3cold
Sep 17 22:24:05 andromeda kernel: [    0.507054] pci 0000:00:02.5: PME# disabled
Sep 17 22:24:05 andromeda kernel: [    0.507235] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
Sep 17 22:24:05 andromeda kernel: [    0.507239] pci 0000:00:03.3: PME# disabled
Sep 17 22:24:05 andromeda kernel: [    0.507322] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 17 22:24:05 andromeda kernel: [    0.507326] pci 0000:00:04.0: PME# disabled
Sep 17 22:24:05 andromeda kernel: [    0.507412] pci 0000:00:05.0: PME# supported from D3cold
Sep 17 22:24:05 andromeda kernel: [    0.507416] pci 0000:00:05.0: PME# disabled
Sep 17 22:24:05 andromeda kernel: [    0.507476] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Sep 17 22:24:05 andromeda kernel: [    0.507480] pci 0000:00:06.0: PME# disabled
Sep 17 22:24:05 andromeda kernel: [    0.507547] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Sep 17 22:24:05 andromeda kernel: [    0.507552] pci 0000:00:07.0: PME# disabled
Sep 17 22:24:05 andromeda kernel: [    0.507642] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
Sep 17 22:24:05 andromeda kernel: [    0.507647] pci 0000:00:0f.0: PME# disabled
Sep 17 22:24:05 andromeda kernel: [    0.513972] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
Sep 17 22:24:05 andromeda kernel: [    0.514119] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Sep 17 22:24:05 andromeda kernel: [    0.514265] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
Sep 17 22:24:05 andromeda kernel: [    0.514409] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
Sep 17 22:24:05 andromeda kernel: [    0.514553] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
Sep 17 22:24:05 andromeda kernel: [    0.514696] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
Sep 17 22:24:05 andromeda kernel: [    0.514843] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 *15)
Sep 17 22:24:05 andromeda kernel: [    0.514986] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Sep 17 22:24:05 andromeda kernel: [    0.515149] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 47, should be 3A [20080926]
Sep 17 22:24:05 andromeda kernel: [    0.515187] ACPI: WMI: Mapper loaded
Sep 17 22:24:05 andromeda kernel: [    0.515244] SCSI subsystem initialized
Sep 17 22:24:05 andromeda kernel: [    0.515244] usbcore: registered new interface driver usbfs
Sep 17 22:24:05 andromeda kernel: [    0.515244] usbcore: registered new interface driver hub
Sep 17 22:24:05 andromeda kernel: [    0.515244] usbcore: registered new device driver usb
Sep 17 22:24:05 andromeda kernel: [    0.515244] PCI: Using ACPI for IRQ routing
Sep 17 22:24:05 andromeda kernel: [    0.520015] Bluetooth: Core ver 2.13
Sep 17 22:24:05 andromeda kernel: [    0.520042] NET: Registered protocol family 31
Sep 17 22:24:05 andromeda kernel: [    0.520042] Bluetooth: HCI device and connection manager initialized
Sep 17 22:24:05 andromeda kernel: [    0.520042] Bluetooth: HCI socket layer initialized
Sep 17 22:24:05 andromeda kernel: [    0.520042] NET: Registered protocol family 8
Sep 17 22:24:05 andromeda kernel: [    0.520042] NET: Registered protocol family 20
Sep 17 22:24:05 andromeda kernel: [    0.520054] NetLabel: Initializing
Sep 17 22:24:05 andromeda kernel: [    0.520057] NetLabel:  domain hash size = 128
Sep 17 22:24:05 andromeda kernel: [    0.520060] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 17 22:24:05 andromeda kernel: [    0.520083] NetLabel:  unlabeled traffic allowed by default
Sep 17 22:24:05 andromeda kernel: [    0.520099] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep 17 22:24:05 andromeda kernel: [    0.520104] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Sep 17 22:24:05 andromeda kernel: [    0.524109] AppArmor: AppArmor Filesystem Enabled
Sep 17 22:24:05 andromeda kernel: [    0.532038] pnp: PnP ACPI init
Sep 17 22:24:05 andromeda kernel: [    0.532055] ACPI: bus type pnp registered
Sep 17 22:24:05 andromeda kernel: [    0.536971] pnp: PnP ACPI: found 16 devices
Sep 17 22:24:05 andromeda kernel: [    0.536974] ACPI: ACPI bus type pnp unregistered
Sep 17 22:24:05 andromeda kernel: [    0.536979] PnPBIOS: Disabled by ACPI PNP
Sep 17 22:24:05 andromeda kernel: [    0.536992] system 00:06: ioport range 0x290-0x297 has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.536995] system 00:06: ioport range 0xc00-0xc05 has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.536998] system 00:06: ioport range 0xd00-0xd05 has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537001] system 00:06: ioport range 0x480-0x48f has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537004] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537006] system 00:06: ioport range 0x800-0x87f has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537009] system 00:06: ioport range 0x880-0x8ff has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537012] system 00:06: ioport range 0xc00-0xc7f could not be reserved
Sep 17 22:24:05 andromeda kernel: [    0.537016] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537019] system 00:06: iomem range 0xffb80000-0xffbfffff has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537022] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537025] system 00:06: iomem range 0xfed10000-0xfed8ffff has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537033] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537036] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537043] system 00:0c: ioport range 0x290-0x297 has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537049] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
Sep 17 22:24:05 andromeda kernel: [    0.537056] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
Sep 17 22:24:05 andromeda kernel: [    0.537059] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
Sep 17 22:24:05 andromeda kernel: [    0.537062] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Sep 17 22:24:05 andromeda kernel: [    0.537065] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
Sep 17 22:24:05 andromeda kernel: [    0.537068] system 00:0f: iomem range 0xfec00000-0xffffffff could not be reserved
Sep 17 22:24:05 andromeda kernel: [    0.571765] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Sep 17 22:24:05 andromeda kernel: [    0.571768] pci 0000:00:01.0:   IO window: disabled
Sep 17 22:24:05 andromeda kernel: [    0.571774] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfebfffff
Sep 17 22:24:05 andromeda kernel: [    0.571779] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Sep 17 22:24:05 andromeda kernel: [    0.571786] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Sep 17 22:24:05 andromeda kernel: [    0.571788] pci 0000:00:06.0:   IO window: disabled
Sep 17 22:24:05 andromeda kernel: [    0.571793] pci 0000:00:06.0:   MEM window: disabled
Sep 17 22:24:05 andromeda kernel: [    0.571798] pci 0000:00:06.0:   PREFETCH window: disabled
Sep 17 22:24:05 andromeda kernel: [    0.571805] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
Sep 17 22:24:05 andromeda kernel: [    0.571806] pci 0000:00:07.0:   IO window: disabled
Sep 17 22:24:05 andromeda kernel: [    0.571812] pci 0000:00:07.0:   MEM window: disabled
Sep 17 22:24:05 andromeda kernel: [    0.571816] pci 0000:00:07.0:   PREFETCH window: disabled
Sep 17 22:24:05 andromeda kernel: [    0.571857] bus: 00 index 0 io port: [0x00-0xffff]
Sep 17 22:24:05 andromeda kernel: [    0.571859] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Sep 17 22:24:05 andromeda kernel: [    0.571862] bus: 01 index 0 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571864] bus: 01 index 1 mmio: [0xfc000000-0xfebfffff]
Sep 17 22:24:05 andromeda kernel: [    0.571866] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
Sep 17 22:24:05 andromeda kernel: [    0.571869] bus: 01 index 3 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571870] bus: 02 index 0 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571872] bus: 02 index 1 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571874] bus: 02 index 2 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571876] bus: 02 index 3 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571878] bus: 03 index 0 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571880] bus: 03 index 1 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571882] bus: 03 index 2 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571884] bus: 03 index 3 mmio: [0x0-0x0]
Sep 17 22:24:05 andromeda kernel: [    0.571895] NET: Registered protocol family 2
Sep 17 22:24:05 andromeda kernel: [    0.584109] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 17 22:24:05 andromeda kernel: [    0.584398] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 17 22:24:05 andromeda kernel: [    0.585117] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 17 22:24:05 andromeda kernel: [    0.585642] TCP: Hash tables configured (established 131072 bind 65536)
Sep 17 22:24:05 andromeda kernel: [    0.585646] TCP reno registered
Sep 17 22:24:05 andromeda kernel: [    0.592221] NET: Registered protocol family 1
Sep 17 22:24:05 andromeda kernel: [    0.592388] checking if image is initramfs... it is
Sep 17 22:24:05 andromeda kernel: [    1.259523] Freeing initrd memory: 7381k freed
Sep 17 22:24:05 andromeda kernel: [    1.259831] cpufreq: No nForce2 chipset.
Sep 17 22:24:05 andromeda kernel: [    1.260031] audit: initializing netlink socket (disabled)
Sep 17 22:24:05 andromeda kernel: [    1.260074] type=2000 audit(1253226232.260:1): initialized
Sep 17 22:24:05 andromeda kernel: [    1.268109] highmem bounce pool size: 64 pages
Sep 17 22:24:05 andromeda kernel: [    1.268114] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Sep 17 22:24:05 andromeda kernel: [    1.269591] VFS: Disk quotas dquot_6.5.1
Sep 17 22:24:05 andromeda kernel: [    1.269657] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 17 22:24:05 andromeda kernel: [    1.270325] fuse init (API version 7.10)
Sep 17 22:24:05 andromeda kernel: [    1.270418] msgmni has been set to 1672
Sep 17 22:24:05 andromeda kernel: [    1.270628] alg: No test for stdrng (krng)
Sep 17 22:24:05 andromeda kernel: [    1.270640] io scheduler noop registered
Sep 17 22:24:05 andromeda kernel: [    1.270642] io scheduler anticipatory registered
Sep 17 22:24:05 andromeda kernel: [    1.270645] io scheduler deadline registered
Sep 17 22:24:05 andromeda kernel: [    1.270661] io scheduler cfq registered (default)
Sep 17 22:24:05 andromeda kernel: [    1.274272] pcieport-driver 0000:00:01.0: found MSI capability
Sep 17 22:24:05 andromeda kernel: [    1.274448] pcieport-driver 0000:00:06.0: found MSI capability
Sep 17 22:24:05 andromeda kernel: [    1.274621] pcieport-driver 0000:00:07.0: found MSI capability
Sep 17 22:24:05 andromeda kernel: [    1.274743] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 17 22:24:05 andromeda kernel: [    1.274754] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 17 22:24:05 andromeda kernel: [    1.274909] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Sep 17 22:24:05 andromeda kernel: [    1.274912] ACPI: Power Button (FF) [PWRF]
Sep 17 22:24:05 andromeda kernel: [    1.274967] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Sep 17 22:24:05 andromeda kernel: [    1.274970] ACPI: Power Button (CM) [PWRB]
Sep 17 22:24:05 andromeda kernel: [    1.275486] ACPI: SSDT BFFAE0C0, 01D2 (r1    AMI   CPU1PM        1 INTL 20051117)
Sep 17 22:24:05 andromeda kernel: [    1.275845] processor ACPI_CPU:00: registered as cooling_device0
Sep 17 22:24:05 andromeda kernel: [    1.275849] ACPI: Processor [CPU1] (supports 8 throttling states)
Sep 17 22:24:05 andromeda kernel: [    1.276192] ACPI: SSDT BFFAE2A0, 0143 (r1    AMI   CPU2PM        1 INTL 20051117)
Sep 17 22:24:05 andromeda kernel: [    1.276522] processor ACPI_CPU:01: registered as cooling_device1
Sep 17 22:24:05 andromeda kernel: [    1.276526] ACPI: Processor [CPU2] (supports 8 throttling states)
Sep 17 22:24:05 andromeda kernel: [    1.278899] isapnp: Scanning for PnP cards...
Sep 17 22:24:05 andromeda kernel: [    1.632342] isapnp: No Plug & Play device found
Sep 17 22:24:05 andromeda kernel: [    1.640821] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Sep 17 22:24:05 andromeda kernel: [    1.640914] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 17 22:24:05 andromeda kernel: [    1.641415] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 17 22:24:05 andromeda kernel: [    1.642233] brd: module loaded
Sep 17 22:24:05 andromeda kernel: [    1.642577] loop: module loaded
Sep 17 22:24:05 andromeda kernel: [    1.642655] Fixed MDIO Bus: probed
Sep 17 22:24:05 andromeda kernel: [    1.642661] PPP generic driver version 2.4.2
Sep 17 22:24:05 andromeda kernel: [    1.642724] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Sep 17 22:24:05 andromeda kernel: [    1.642758] Driver 'sd' needs updating - please use bus_type methods
Sep 17 22:24:05 andromeda kernel: [    1.642768] Driver 'sr' needs updating - please use bus_type methods
Sep 17 22:24:05 andromeda kernel: [    1.642928] sata_sis 0000:00:05.0: version 1.0
Sep 17 22:24:05 andromeda kernel: [    1.642953] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Sep 17 22:24:05 andromeda kernel: [    1.642959] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
Sep 17 22:24:05 andromeda kernel: [    1.643077] scsi0 : sata_sis
Sep 17 22:24:05 andromeda kernel: [    1.643184] scsi1 : sata_sis
Sep 17 22:24:05 andromeda kernel: [    1.643810] ata1: PATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 17
Sep 17 22:24:05 andromeda kernel: [    1.643813] ata2: PATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 17
Sep 17 22:24:05 andromeda kernel: [    1.831656] ata1.00: ATA-8: ST31000333AS, CC1H, max UDMA/133
Sep 17 22:24:05 andromeda kernel: [    1.831661] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Sep 17 22:24:05 andromeda kernel: [    1.887678] ata1.00: configured for UDMA/133
Sep 17 22:24:05 andromeda kernel: [    2.050903] scsi 0:0:0:0: Direct-Access     ATA      ST31000333AS     CC1H PQ: 0 ANSI: 5
Sep 17 22:24:05 andromeda kernel: [    2.051013] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Sep 17 22:24:05 andromeda kernel: [    2.051031] sd 0:0:0:0: [sda] Write Protect is off
Sep 17 22:24:05 andromeda kernel: [    2.051061] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 17 22:24:05 andromeda kernel: [    2.051142] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Sep 17 22:24:05 andromeda kernel: [    2.051157] sd 0:0:0:0: [sda] Write Protect is off
Sep 17 22:24:05 andromeda kernel: [    2.051186] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 17 22:24:05 andromeda kernel: [    2.051190]  sda: sda1 sda2 < sda5 sda6 sda7 >
Sep 17 22:24:05 andromeda kernel: [    2.114004] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 17 22:24:05 andromeda kernel: [    2.114058] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 17 22:24:05 andromeda kernel: [    2.114642] scsi2 : pata_sis
Sep 17 22:24:05 andromeda kernel: [    2.114707] scsi3 : pata_sis
Sep 17 22:24:05 andromeda kernel: [    2.115332] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
Sep 17 22:24:05 andromeda kernel: [    2.115336] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
Sep 17 22:24:05 andromeda kernel: [    2.276264] ata3.01: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
Sep 17 22:24:05 andromeda kernel: [    2.292275] ata3.01: configured for UDMA/66
Sep 17 22:24:05 andromeda kernel: [    2.298135] scsi 2:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
Sep 17 22:24:05 andromeda kernel: [    2.309730] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 17 22:24:05 andromeda kernel: [    2.309735] Uniform CD-ROM driver Revision: 3.20
Sep 17 22:24:05 andromeda kernel: [    2.309937] sr 2:0:1:0: Attached scsi generic sg1 type 5
Sep 17 22:24:05 andromeda kernel: [    2.310061] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 17 22:24:05 andromeda kernel: [    2.310087] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Sep 17 22:24:05 andromeda kernel: [    2.310117] ehci_hcd 0000:00:03.3: EHCI Host Controller
Sep 17 22:24:05 andromeda kernel: [    2.310189] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
Sep 17 22:24:05 andromeda kernel: [    2.310232] ehci_hcd 0000:00:03.3: irq 22, io mem 0xfbffd000
Sep 17 22:24:05 andromeda kernel: [    2.320029] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
Sep 17 22:24:05 andromeda kernel: [    2.320140] usb usb1: configuration #1 chosen from 1 choice
Sep 17 22:24:05 andromeda kernel: [    2.320176] hub 1-0:1.0: USB hub found
Sep 17 22:24:05 andromeda kernel: [    2.320184] hub 1-0:1.0: 8 ports detected
Sep 17 22:24:05 andromeda kernel: [    2.320312] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 17 22:24:05 andromeda kernel: [    2.320332] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Sep 17 22:24:05 andromeda kernel: [    2.320343] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep 17 22:24:05 andromeda kernel: [    2.320386] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
Sep 17 22:24:05 andromeda kernel: [    2.320404] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfbfff000
Sep 17 22:24:05 andromeda kernel: [    2.378063] usb usb2: configuration #1 chosen from 1 choice
Sep 17 22:24:05 andromeda kernel: [    2.378090] hub 2-0:1.0: USB hub found
Sep 17 22:24:05 andromeda kernel: [    2.378099] hub 2-0:1.0: 4 ports detected
Sep 17 22:24:05 andromeda kernel: [    2.378188] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Sep 17 22:24:05 andromeda kernel: [    2.378198] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep 17 22:24:05 andromeda kernel: [    2.378245] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
Sep 17 22:24:05 andromeda kernel: [    2.378261] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfbffe000
Sep 17 22:24:05 andromeda kernel: [    2.434064] usb usb3: configuration #1 chosen from 1 choice
Sep 17 22:24:05 andromeda kernel: [    2.434090] hub 3-0:1.0: USB hub found
Sep 17 22:24:05 andromeda kernel: [    2.434098] hub 3-0:1.0: 4 ports detected
Sep 17 22:24:05 andromeda kernel: [    2.434192] uhci_hcd: USB Universal Host Controller Interface driver
Sep 17 22:24:05 andromeda kernel: [    2.434289] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Sep 17 22:24:05 andromeda kernel: [    2.436972] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 17 22:24:05 andromeda kernel: [    2.436979] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 17 22:24:05 andromeda kernel: [    2.440064] mice: PS/2 mouse device common for all mice
Sep 17 22:24:05 andromeda kernel: [    2.452114] rtc_cmos 00:08: RTC can wake from S4
Sep 17 22:24:05 andromeda kernel: [    2.452171] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Sep 17 22:24:05 andromeda kernel: [    2.452194] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
Sep 17 22:24:05 andromeda kernel: [    2.452258] device-mapper: uevent: version 1.0.3
Sep 17 22:24:05 andromeda kernel: [    2.452368] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Sep 17 22:24:05 andromeda kernel: [    2.452441] device-mapper: multipath: version 1.0.5 loaded
Sep 17 22:24:05 andromeda kernel: [    2.452444] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 17 22:24:05 andromeda kernel: [    2.452523] EISA: Probing bus 0 at eisa.0
Sep 17 22:24:05 andromeda kernel: [    2.452558] EISA: Detected 0 cards.
Sep 17 22:24:05 andromeda kernel: [    2.452607] cpuidle: using governor ladder
Sep 17 22:24:05 andromeda kernel: [    2.452610] cpuidle: using governor menu
Sep 17 22:24:05 andromeda kernel: [    2.453169] TCP cubic registered
Sep 17 22:24:05 andromeda kernel: [    2.453273] NET: Registered protocol family 10
Sep 17 22:24:05 andromeda kernel: [    2.453745] lo: Disabled Privacy Extensions
Sep 17 22:24:05 andromeda kernel: [    2.454106] NET: Registered protocol family 17
Sep 17 22:24:05 andromeda kernel: [    2.454127] Bluetooth: L2CAP ver 2.11
Sep 17 22:24:05 andromeda kernel: [    2.454129] Bluetooth: L2CAP socket layer initialized
Sep 17 22:24:05 andromeda kernel: [    2.454132] Bluetooth: SCO (Voice Link) ver 0.6
Sep 17 22:24:05 andromeda kernel: [    2.454134] Bluetooth: SCO socket layer initialized
Sep 17 22:24:05 andromeda kernel: [    2.454170] Bluetooth: RFCOMM socket layer initialized
Sep 17 22:24:05 andromeda kernel: [    2.454180] Bluetooth: RFCOMM TTY layer initialized
Sep 17 22:24:05 andromeda kernel: [    2.454182] Bluetooth: RFCOMM ver 1.10
Sep 17 22:24:05 andromeda kernel: [    2.454742] Using IPI No-Shortcut mode
Sep 17 22:24:05 andromeda kernel: [    2.454829] registered taskstats version 1
Sep 17 22:24:05 andromeda kernel: [    2.454949]   Magic number: 9:453:401
Sep 17 22:24:05 andromeda kernel: [    2.455034] rtc_cmos 00:08: setting system clock to 2009-09-17 22:23:53 UTC (1253226233)
Sep 17 22:24:05 andromeda kernel: [    2.455038] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 17 22:24:05 andromeda kernel: [    2.455040] EDD information not available.
Sep 17 22:24:05 andromeda kernel: [    2.455314] Freeing unused kernel memory: 532k freed
Sep 17 22:24:05 andromeda kernel: [    2.455453] Write protecting the kernel text: 4116k
Sep 17 22:24:05 andromeda kernel: [    2.455501] Write protecting the kernel read-only data: 1528k
Sep 17 22:24:05 andromeda kernel: [    2.471133] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Sep 17 22:24:05 andromeda kernel: [    2.713499] Floppy drive(s): fd0 is 1.44M
Sep 17 22:24:05 andromeda kernel: [    2.906954] FDC 0 is a post-1991 82077
Sep 17 22:24:05 andromeda kernel: [    3.013086] usb 2-2: new full speed USB device using ohci_hcd and address 2
Sep 17 22:24:05 andromeda kernel: [    3.307040] usb 2-2: configuration #1 chosen from 1 choice
Sep 17 22:24:05 andromeda kernel: [    3.387662] PM: Starting manual resume from disk
Sep 17 22:24:05 andromeda kernel: [    3.402402] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep 17 22:24:05 andromeda kernel: [    3.402406] EXT3-fs: write access will be enabled during recovery.
Sep 17 22:24:05 andromeda kernel: [    4.474901] kjournald starting.  Commit interval 5 seconds
Sep 17 22:24:05 andromeda kernel: [    4.474925] EXT3-fs: sda6: orphan cleanup on readonly fs
Sep 17 22:24:05 andromeda kernel: [    4.474973] EXT3-fs: sda6: 1 orphan inode deleted
Sep 17 22:24:05 andromeda kernel: [    4.474975] EXT3-fs: recovery complete.
Sep 17 22:24:05 andromeda kernel: [    4.503329] EXT3-fs: mounted filesystem with ordered data mode.
Sep 17 22:24:05 andromeda kernel: [    9.544848] udev: starting version 141
Sep 17 22:24:05 andromeda kernel: [    9.947786] parport_pc 00:05: reported by Plug and Play ACPI
Sep 17 22:24:05 andromeda kernel: [    9.947897] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Sep 17 22:24:05 andromeda kernel: [   10.061909] ppdev: user-space parallel port driver
Sep 17 22:24:05 andromeda kernel: [   10.063081] input: PC Speaker as /devices/platform/pcspkr/input/input4
Sep 17 22:24:05 andromeda kernel: [   10.066176] Linux video capture interface: v2.00
Sep 17 22:24:05 andromeda kernel: [   10.086639] gspca: main v2.3.0 registered
Sep 17 22:24:05 andromeda kernel: [   10.089564] gspca: probing 093a:2471
Sep 17 22:24:05 andromeda kernel: [   10.093785] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
Sep 17 22:24:05 andromeda kernel: [   10.093789] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2471)
Sep 17 22:24:05 andromeda kernel: [   10.105924] gspca: probe ok
Sep 17 22:24:05 andromeda kernel: [   10.105952] usbcore: registered new interface driver pac207
Sep 17 22:24:05 andromeda kernel: [   10.105978] pac207: registered
Sep 17 22:24:05 andromeda kernel: [   10.158501] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Sep 17 22:24:05 andromeda kernel: [   10.171607] sis190 Gigabit Ethernet driver 1.2 loaded.
Sep 17 22:24:05 andromeda kernel: [   10.171644] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep 17 22:24:05 andromeda kernel: [   10.171864] 0000:00:04.0: Read MAC address from EEPROM
Sep 17 22:24:05 andromeda kernel: [   10.171867] 0000:00:04.0: Error EEPROM read 0.
Sep 17 22:24:05 andromeda kernel: [   10.171870] 0000:00:04.0: Read MAC address from APC.
Sep 17 22:24:05 andromeda kernel: [   10.178079] Linux agpgart interface v0.103
Sep 17 22:24:05 andromeda kernel: [   10.216038] 0000:00:04.0: Atheros PHY AR8012 transceiver at address 1.
Sep 17 22:24:05 andromeda kernel: [   10.674030] nvidia: module license 'NVIDIA' taints kernel.
Sep 17 22:24:05 andromeda kernel: [   10.713987] 0000:00:04.0: Using transceiver at address 1 as default.
Sep 17 22:24:05 andromeda kernel: [   10.745251] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f7da4c00 (IRQ: 19), 00:1e:8c:07:a9:8e
Sep 17 22:24:05 andromeda kernel: [   10.745255] eth0: GMII mode.
Sep 17 22:24:05 andromeda kernel: [   10.745262] eth0: Enabling Auto-negotiation.
Sep 17 22:24:05 andromeda kernel: [   10.930629] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Sep 17 22:24:05 andromeda kernel: [   11.100182] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 17 22:24:05 andromeda kernel: [   11.311761] lp0: using parport0 (interrupt-driven).
Sep 17 22:24:05 andromeda kernel: [   11.402148] Adding 9116848k swap on /dev/sda7.  Priority:-1 extents:1 across:9116848k
Sep 17 22:24:05 andromeda kernel: [   11.471694] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Sep 17 22:24:05 andromeda kernel: [   11.946799] EXT3 FS on sda6, internal journal
Sep 17 22:24:05 andromeda kernel: [   12.973385] type=1505 audit(1253237044.016:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1911
Sep 17 22:24:05 andromeda kernel: [   13.025746] type=1505 audit(1253237044.068:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1917
Sep 17 22:24:05 andromeda kernel: [   13.025927] type=1505 audit(1253237044.068:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1917
Sep 17 22:24:05 andromeda kernel: [   13.025981] type=1505 audit(1253237044.068:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1917
Sep 17 22:24:05 andromeda kernel: [   13.026033] type=1505 audit(1253237044.068:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1917
Sep 17 22:24:05 andromeda kernel: [   13.171307] type=1505 audit(1253237044.212:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1922
Sep 17 22:24:05 andromeda kernel: [   13.171593] type=1505 audit(1253237044.212:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1922
Sep 17 22:24:05 andromeda kernel: [   13.203077] type=1505 audit(1253237044.244:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1926
Sep 17 22:24:05 andromeda kernel: [   14.006330] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 17 22:24:07 andromeda kernel: [   16.055577] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 17 22:24:07 andromeda kernel: [   16.055581] Bluetooth: BNEP filters: protocol multicast
Sep 17 22:24:07 andromeda kernel: [   16.066435] Bridge firewalling registered
Sep 17 22:24:15 andromeda kernel: [   24.036025] eth0: mii ext = 0000.
Sep 17 22:24:15 andromeda kernel: [   24.052086] eth0: mii lpa = 45e1 adv = 01e1.
Sep 17 22:24:15 andromeda kernel: [   24.052091] eth0: link on 100 Mbps Full Duplex mode.
Sep 17 22:24:15 andromeda kernel: [   24.052314] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 17 22:24:15 andromeda kernel: [   24.492025] eth0: mii ext = 0000.
Sep 17 22:24:15 andromeda kernel: [   24.508023] eth0: mii lpa = 45e1 adv = 01e1.
Sep 17 22:24:15 andromeda kernel: [   24.508026] eth0: link on 100 Mbps Full Duplex mode.
Sep 17 22:24:25 andromeda kernel: [   33.597709] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Sep 17 22:41:12 andromeda syslogd 1.5.0#5ubuntu3: restart.
Sep 17 22:41:12 andromeda kernel: Inspecting /boot/System.map-2.6.28-15-generic
Sep 17 22:41:12 andromeda kernel: Cannot find map file.
Sep 17 22:41:12 andromeda kernel: Loaded 72796 symbols from 41 modules.
Sep 17 22:41:12 andromeda kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Sep 17 22:41:12 andromeda kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 17 22:41:12 andromeda kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 17 22:41:12 andromeda kernel: [    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
Sep 17 22:41:12 andromeda kernel: [    0.000000] KERNEL supported cpus:
Sep 17 22:41:12 andromeda kernel: [    0.000000]   Intel GenuineIntel
Sep 17 22:41:12 andromeda kernel: [    0.000000]   AMD AuthenticAMD
Sep 17 22:41:12 andromeda kernel: [    0.000000]   NSC Geode by NSC
Sep 17 22:41:12 andromeda kernel: [    0.000000]   Cyrix CyrixInstead
Sep 17 22:41:12 andromeda kernel: [    0.000000]   Centaur CentaurHauls
Sep 17 22:41:12 andromeda kernel: [    0.000000]   Transmeta GenuineTMx86
Sep 17 22:41:12 andromeda kernel: [    0.000000]   Transmeta TransmetaCPU
Sep 17 22:41:12 andromeda kernel: [    0.000000]   UMC UMC UMC UMC
Sep 17 22:41:12 andromeda kernel: [    0.000000] BIOS-provided physical RAM map:
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Sep 17 22:41:12 andromeda kernel: [    0.000000] DMI present.
Sep 17 22:41:12 andromeda kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
Sep 17 22:41:12 andromeda kernel: [    0.000000] last_pfn = 0xbffa0 max_arch_pfn = 0x100000
Sep 17 22:41:12 andromeda kernel: [    0.000000] Scanning 0 areas for low memory corruption
Sep 17 22:41:12 andromeda kernel: [    0.000000] modified physical RAM map:
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 0000000000100000 - 00000000bffa0000 (usable)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 00000000bffa0000 - 00000000bffae000 (ACPI data)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
Sep 17 22:41:12 andromeda kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Sep 17 22:41:12 andromeda kernel: [    0.000000] RAMDISK: 378ba000 - 37fef752
Sep 17 22:41:12 andromeda kernel: [    0.000000] Allocated new RAMDISK: 0087d000 - 00fb2752
Sep 17 22:41:12 andromeda kernel: [    0.000000] Move RAMDISK from 00000000378ba000 - 0000000037fef751 to 0087d000 - 00fb2751
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: RSDP 000FB650, 0014 (r0 ACPIAM)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: RSDT BFFA0000, 003C (r1 091707 RSDT1623 20070917 MSFT       97)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: FACP BFFA0200, 0084 (r1 091707 FACP1623 20070917 MSFT       97)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: DSDT BFFA0610, 67F4 (r1  A0857 A0857000        0 INTL 20051117)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: FACS BFFAE000, 0040
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: APIC BFFA0390, 006C (r1 091707 APIC1623 20070917 MSFT       97)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: MCFG BFFA0400, 003C (r1 091707 OEMMCFG  20070917 MSFT       97)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: WDRT BFFA05C0, 0047 (r1 091707 OEMWDRT  20070917 MSFT       97)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: OEMB BFFAE040, 0071 (r1 091707 OEMB1623 20070917 MSFT       97)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: HPET BFFA6E10, 0038 (r1 091707 OEMHPET  20070917 MSFT       97)
Sep 17 22:41:12 andromeda kernel: [    0.000000] 2187MB HIGHMEM available.
Sep 17 22:41:12 andromeda kernel: [    0.000000] 883MB LOWMEM available.
Sep 17 22:41:12 andromeda kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Sep 17 22:41:12 andromeda kernel: [    0.000000]   low ram: 00000000 - 373fe000
Sep 17 22:41:12 andromeda kernel: [    0.000000]   bootmap 00012000 - 00018e80
Sep 17 22:41:12 andromeda kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #7 [000087d000 - 0000fb2752]      NEW RAMDISK ==> [000087d000 - 0000fb2752]
Sep 17 22:41:12 andromeda kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Sep 17 22:41:12 andromeda kernel: [    0.000000] found SMP MP-table at [c00ff780] 000ff780
Sep 17 22:41:12 andromeda kernel: [    0.000000] Zone PFN ranges:
Sep 17 22:41:12 andromeda kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Sep 17 22:41:12 andromeda kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Sep 17 22:41:12 andromeda kernel: [    0.000000]   HighMem  0x000373fe -> 0x000bffa0
Sep 17 22:41:12 andromeda kernel: [    0.000000] Movable zone start PFN for each node
Sep 17 22:41:12 andromeda kernel: [    0.000000] early_node_map[2] active PFN ranges
Sep 17 22:41:12 andromeda kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Sep 17 22:41:12 andromeda kernel: [    0.000000]     0: 0x00000100 -> 0x000bffa0
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep 17 22:41:12 andromeda kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Sep 17 22:41:12 andromeda kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep 17 22:41:12 andromeda kernel: [    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
Sep 17 22:41:12 andromeda kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep 17 22:41:12 andromeda kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Sep 17 22:41:12 andromeda kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 22:41:12 andromeda kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Sep 17 22:41:12 andromeda kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Sep 17 22:41:12 andromeda kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ee00000)
Sep 17 22:41:12 andromeda kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Sep 17 22:41:12 andromeda kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780079
Sep 17 22:41:12 andromeda kernel: [    0.000000] Kernel command line: root=UUID=c1e568dd-41b0-46ef-a6f8-291b40ef534e ro quiet splash 
Sep 17 22:41:12 andromeda kernel: [    0.000000] Enabling fast FPU save and restore... done.
Sep 17 22:41:12 andromeda kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Sep 17 22:41:12 andromeda kernel: [    0.000000] Initializing CPU#0
Sep 17 22:41:12 andromeda kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Sep 17 22:41:12 andromeda kernel: [    0.000000] Fast TSC calibration using PIT
Sep 17 22:41:12 andromeda kernel: [    0.000000] Detected 1800.040 MHz processor.
Sep 17 22:41:12 andromeda kernel: [    0.004000] Console: colour VGA+ 80x25
Sep 17 22:41:12 andromeda kernel: [    0.004000] console [tty0] enabled
Sep 17 22:41:12 andromeda kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep 17 22:41:12 andromeda kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep 17 22:41:12 andromeda kernel: [    0.004000] allocated 15726400 bytes of page_cgroup
Sep 17 22:41:12 andromeda kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Sep 17 22:41:12 andromeda kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Sep 17 22:41:12 andromeda kernel: [    0.004000] Memory: 3087908k/3145344k available (4115k kernel code, 56048k reserved, 2199k data, 532k init, 2240136k highmem)
Sep 17 22:41:12 andromeda kernel: [    0.004000] virtual kernel memory layout:
Sep 17 22:41:12 andromeda kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Sep 17 22:41:12 andromeda kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Sep 17 22:41:12 andromeda kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Sep 17 22:41:12 andromeda kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Sep 17 22:41:12 andromeda kernel: [    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
Sep 17 22:41:12 andromeda kernel: [    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
Sep 17 22:41:12 andromeda kernel: [    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
Sep 17 22:41:12 andromeda kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Sep 17 22:41:12 andromeda kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Sep 17 22:41:12 andromeda kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Sep 17 22:41:12 andromeda kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3600.08 BogoMIPS (lpj=7200160)
Sep 17 22:41:12 andromeda kernel: [    0.004000] Security Framework initialized
Sep 17 22:41:12 andromeda kernel: [    0.004000] SELinux:  Disabled at boot.
Sep 17 22:41:12 andromeda kernel: [    0.004000] AppArmor: AppArmor initialized
Sep 17 22:41:12 andromeda kernel: [    0.004000] Mount-cache hash table entries: 512
Sep 17 22:41:12 andromeda kernel: [    0.004000] Initializing cgroup subsys ns
Sep 17 22:41:12 andromeda kernel: [    0.004000] Initializing cgroup subsys cpuacct
Sep 17 22:41:12 andromeda kernel: [    0.004000] Initializing cgroup subsys memory
Sep 17 22:41:12 andromeda kernel: [    0.004000] Initializing cgroup subsys freezer
Sep 17 22:41:12 andromeda kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 17 22:41:12 andromeda kernel: [    0.004000] CPU: L2 cache: 1024K
Sep 17 22:41:12 andromeda kernel: [    0.004000] CPU: Physical Processor ID: 0
Sep 17 22:41:12 andromeda kernel: [    0.004000] CPU: Processor Core ID: 0
Sep 17 22:41:12 andromeda kernel: [    0.004000] using mwait in idle threads.
Sep 17 22:41:12 andromeda kernel: [    0.004000] Checking 'hlt' instruction... OK.
Sep 17 22:41:12 andromeda kernel: [    0.018843] ACPI: Core revision 20080926
Sep 17 22:41:12 andromeda kernel: [    0.022338] ACPI: Checking initramfs for custom DSDT
Sep 17 22:41:12 andromeda kernel: [    0.350544] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep 17 22:41:12 andromeda kernel: [    0.390242] CPU0: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz stepping 0d
Sep 17 22:41:12 andromeda kernel: [    0.392001] Booting processor 1 APIC 0x1 ip 0x6000
Sep 17 22:41:12 andromeda kernel: [    0.004000] Initializing CPU#1
Sep 17 22:41:12 andromeda kernel: [    0.004000] Calibrating delay using timer specific routine.. 3599.90 BogoMIPS (lpj=7199811)
Sep 17 22:41:12 andromeda kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 17 22:41:12 andromeda kernel: [    0.004000] CPU: L2 cache: 1024K
Sep 17 22:41:12 andromeda kernel: [    0.004000] CPU: Physical Processor ID: 0
Sep 17 22:41:12 andromeda kernel: [    0.004000] CPU: Processor Core ID: 1
Sep 17 22:41:12 andromeda kernel: [    0.476402] CPU1: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz stepping 0d
Sep 17 22:41:12 andromeda kernel: [    0.476420] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Sep 17 22:41:12 andromeda kernel: [    0.480058] Brought up 2 CPUs
Sep 17 22:41:12 andromeda kernel: [    0.480061] Total of 2 processors activated (7199.98 BogoMIPS).
Sep 17 22:41:12 andromeda kernel: [    0.480208] net_namespace: 776 bytes
Sep 17 22:41:12 andromeda kernel: [    0.480208] Booting paravirtualized kernel on bare hardware
Sep 17 22:41:12 andromeda kernel: [    0.480392] Time: 22:40:59  Date: 09/17/09
Sep 17 22:41:12 andromeda kernel: [    0.480392] regulator: core version 0.5
Sep 17 22:41:12 andromeda kernel: [    0.480392] NET: Registered protocol family 16
Sep 17 22:41:12 andromeda kernel: [    0.480392] EISA bus registered
Sep 17 22:41:12 andromeda kernel: [    0.480392] ACPI: bus type pci registered
Sep 17 22:41:12 andromeda kernel: [    0.480392] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Sep 17 22:41:12 andromeda kernel: [    0.480392] PCI: Not using MMCONFIG.
Sep 17 22:41:12 andromeda kernel: [    0.481422] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
Sep 17 22:41:12 andromeda kernel: [    0.481424] PCI: Using configuration type 1 for base access
Sep 17 22:41:12 andromeda kernel: [    0.495512] ACPI: Interpreter enabled
Sep 17 22:41:12 andromeda kernel: [    0.495519] ACPI: (supports S0 S1 S3 S4 S5)
Sep 17 22:41:12 andromeda kernel: [    0.495541] ACPI: Using IOAPIC for interrupt routing
Sep 17 22:41:12 andromeda kernel: [    0.495603] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Sep 17 22:41:12 andromeda kernel: [    0.499519] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Sep 17 22:41:12 andromeda kernel: [    0.499522] PCI: Using MMCONFIG for extended config space
Sep 17 22:41:12 andromeda kernel: [    0.506744] ACPI: No dock devices found.
Sep 17 22:41:12 andromeda kernel: [    0.506808] ACPI: PCI Root Bridge [PCI0] (0000:00)
Sep 17 22:41:12 andromeda kernel: [    0.506926] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Sep 17 22:41:12 andromeda kernel: [    0.506930] pci 0000:00:01.0: PME# disabled
Sep 17 22:41:12 andromeda kernel: [    0.507067] pci 0000:00:02.5: PME# supported from D3cold
Sep 17 22:41:12 andromeda kernel: [    0.507072] pci 0000:00:02.5: PME# disabled
Sep 17 22:41:12 andromeda kernel: [    0.507253] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
Sep 17 22:41:12 andromeda kernel: [    0.507257] pci 0000:00:03.3: PME# disabled
Sep 17 22:41:12 andromeda kernel: [    0.507339] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Sep 17 22:41:12 andromeda kernel: [    0.507344] pci 0000:00:04.0: PME# disabled
Sep 17 22:41:12 andromeda kernel: [    0.507429] pci 0000:00:05.0: PME# supported from D3cold
Sep 17 22:41:12 andromeda kernel: [    0.507434] pci 0000:00:05.0: PME# disabled
Sep 17 22:41:12 andromeda kernel: [    0.507494] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Sep 17 22:41:12 andromeda kernel: [    0.507498] pci 0000:00:06.0: PME# disabled
Sep 17 22:41:12 andromeda kernel: [    0.507565] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Sep 17 22:41:12 andromeda kernel: [    0.507569] pci 0000:00:07.0: PME# disabled
Sep 17 22:41:12 andromeda kernel: [    0.507660] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
Sep 17 22:41:12 andromeda kernel: [    0.507664] pci 0000:00:0f.0: PME# disabled
Sep 17 22:41:12 andromeda kernel: [    0.513985] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
Sep 17 22:41:12 andromeda kernel: [    0.514132] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Sep 17 22:41:12 andromeda kernel: [    0.514277] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
Sep 17 22:41:12 andromeda kernel: [    0.514421] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 11 12 14 15)
Sep 17 22:41:12 andromeda kernel: [    0.514565] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
Sep 17 22:41:12 andromeda kernel: [    0.514708] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
Sep 17 22:41:12 andromeda kernel: [    0.514856] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 *15)
Sep 17 22:41:12 andromeda kernel: [    0.515000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Sep 17 22:41:12 andromeda kernel: [    0.515162] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 47, should be 3A [20080926]
Sep 17 22:41:12 andromeda kernel: [    0.515200] ACPI: WMI: Mapper loaded
Sep 17 22:41:12 andromeda kernel: [    0.515259] SCSI subsystem initialized
Sep 17 22:41:12 andromeda kernel: [    0.515259] usbcore: registered new interface driver usbfs
Sep 17 22:41:12 andromeda kernel: [    0.515259] usbcore: registered new interface driver hub
Sep 17 22:41:12 andromeda kernel: [    0.515259] usbcore: registered new device driver usb
Sep 17 22:41:12 andromeda kernel: [    0.515259] PCI: Using ACPI for IRQ routing
Sep 17 22:41:12 andromeda kernel: [    0.520015] Bluetooth: Core ver 2.13
Sep 17 22:41:12 andromeda kernel: [    0.520041] NET: Registered protocol family 31
Sep 17 22:41:12 andromeda kernel: [    0.520041] Bluetooth: HCI device and connection manager initialized
Sep 17 22:41:12 andromeda kernel: [    0.520041] Bluetooth: HCI socket layer initialized
Sep 17 22:41:12 andromeda kernel: [    0.520041] NET: Registered protocol family 8
Sep 17 22:41:12 andromeda kernel: [    0.520041] NET: Registered protocol family 20
Sep 17 22:41:12 andromeda kernel: [    0.520054] NetLabel: Initializing
Sep 17 22:41:12 andromeda kernel: [    0.520057] NetLabel:  domain hash size = 128
Sep 17 22:41:12 andromeda kernel: [    0.520060] NetLabel:  protocols = UNLABELED CIPSOv4
Sep 17 22:41:12 andromeda kernel: [    0.520084] NetLabel:  unlabeled traffic allowed by default
Sep 17 22:41:12 andromeda kernel: [    0.520099] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Sep 17 22:41:12 andromeda kernel: [    0.520104] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Sep 17 22:41:12 andromeda kernel: [    0.524109] AppArmor: AppArmor Filesystem Enabled
Sep 17 22:41:12 andromeda kernel: [    0.532037] pnp: PnP ACPI init
Sep 17 22:41:12 andromeda kernel: [    0.532055] ACPI: bus type pnp registered
Sep 17 22:41:12 andromeda kernel: [    0.536971] pnp: PnP ACPI: found 16 devices
Sep 17 22:41:12 andromeda kernel: [    0.536973] ACPI: ACPI bus type pnp unregistered
Sep 17 22:41:12 andromeda kernel: [    0.536978] PnPBIOS: Disabled by ACPI PNP
Sep 17 22:41:12 andromeda kernel: [    0.536991] system 00:06: ioport range 0x290-0x297 has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.536994] system 00:06: ioport range 0xc00-0xc05 has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.536997] system 00:06: ioport range 0xd00-0xd05 has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537000] system 00:06: ioport range 0x480-0x48f has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537003] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537006] system 00:06: ioport range 0x800-0x87f has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537008] system 00:06: ioport range 0x880-0x8ff has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537011] system 00:06: ioport range 0xc00-0xc7f could not be reserved
Sep 17 22:41:12 andromeda kernel: [    0.537015] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537018] system 00:06: iomem range 0xffb80000-0xffbfffff has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537021] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537024] system 00:06: iomem range 0xfed10000-0xfed8ffff has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537032] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537035] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537041] system 00:0c: ioport range 0x290-0x297 has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537048] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
Sep 17 22:41:12 andromeda kernel: [    0.537055] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
Sep 17 22:41:12 andromeda kernel: [    0.537058] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
Sep 17 22:41:12 andromeda kernel: [    0.537061] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
Sep 17 22:41:12 andromeda kernel: [    0.537064] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
Sep 17 22:41:12 andromeda kernel: [    0.537067] system 00:0f: iomem range 0xfec00000-0xffffffff could not be reserved
Sep 17 22:41:12 andromeda kernel: [    0.571765] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Sep 17 22:41:12 andromeda kernel: [    0.571768] pci 0000:00:01.0:   IO window: disabled
Sep 17 22:41:12 andromeda kernel: [    0.571774] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfebfffff
Sep 17 22:41:12 andromeda kernel: [    0.571779] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Sep 17 22:41:12 andromeda kernel: [    0.571786] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Sep 17 22:41:12 andromeda kernel: [    0.571788] pci 0000:00:06.0:   IO window: disabled
Sep 17 22:41:12 andromeda kernel: [    0.571794] pci 0000:00:06.0:   MEM window: disabled
Sep 17 22:41:12 andromeda kernel: [    0.571798] pci 0000:00:06.0:   PREFETCH window: disabled
Sep 17 22:41:12 andromeda kernel: [    0.571805] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
Sep 17 22:41:12 andromeda kernel: [    0.571807] pci 0000:00:07.0:   IO window: disabled
Sep 17 22:41:12 andromeda kernel: [    0.571812] pci 0000:00:07.0:   MEM window: disabled
Sep 17 22:41:12 andromeda kernel: [    0.571817] pci 0000:00:07.0:   PREFETCH window: disabled
Sep 17 22:41:12 andromeda kernel: [    0.571858] bus: 00 index 0 io port: [0x00-0xffff]
Sep 17 22:41:12 andromeda kernel: [    0.571860] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Sep 17 22:41:12 andromeda kernel: [    0.571863] bus: 01 index 0 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571865] bus: 01 index 1 mmio: [0xfc000000-0xfebfffff]
Sep 17 22:41:12 andromeda kernel: [    0.571868] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
Sep 17 22:41:12 andromeda kernel: [    0.571870] bus: 01 index 3 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571872] bus: 02 index 0 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571874] bus: 02 index 1 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571876] bus: 02 index 2 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571877] bus: 02 index 3 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571879] bus: 03 index 0 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571881] bus: 03 index 1 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571883] bus: 03 index 2 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571885] bus: 03 index 3 mmio: [0x0-0x0]
Sep 17 22:41:12 andromeda kernel: [    0.571896] NET: Registered protocol family 2
Sep 17 22:41:12 andromeda kernel: [    0.584109] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Sep 17 22:41:12 andromeda kernel: [    0.584394] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Sep 17 22:41:12 andromeda kernel: [    0.585112] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Sep 17 22:41:12 andromeda kernel: [    0.585637] TCP: Hash tables configured (established 131072 bind 65536)
Sep 17 22:41:12 andromeda kernel: [    0.585641] TCP reno registered
Sep 17 22:41:12 andromeda kernel: [    0.592223] NET: Registered protocol family 1
Sep 17 22:41:12 andromeda kernel: [    0.592387] checking if image is initramfs... it is
Sep 17 22:41:12 andromeda kernel: [    1.259586] Freeing initrd memory: 7381k freed
Sep 17 22:41:12 andromeda kernel: [    1.259896] cpufreq: No nForce2 chipset.
Sep 17 22:41:12 andromeda kernel: [    1.260092] audit: initializing netlink socket (disabled)
Sep 17 22:41:12 andromeda kernel: [    1.260134] type=2000 audit(1253227259.260:1): initialized
Sep 17 22:41:12 andromeda kernel: [    1.268171] highmem bounce pool size: 64 pages
Sep 17 22:41:12 andromeda kernel: [    1.268176] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Sep 17 22:41:12 andromeda kernel: [    1.269650] VFS: Disk quotas dquot_6.5.1
Sep 17 22:41:12 andromeda kernel: [    1.269716] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Sep 17 22:41:12 andromeda kernel: [    1.270383] fuse init (API version 7.10)
Sep 17 22:41:12 andromeda kernel: [    1.270476] msgmni has been set to 1672
Sep 17 22:41:12 andromeda kernel: [    1.270685] alg: No test for stdrng (krng)
Sep 17 22:41:12 andromeda kernel: [    1.270696] io scheduler noop registered
Sep 17 22:41:12 andromeda kernel: [    1.270699] io scheduler anticipatory registered
Sep 17 22:41:12 andromeda kernel: [    1.270701] io scheduler deadline registered
Sep 17 22:41:12 andromeda kernel: [    1.270716] io scheduler cfq registered (default)
Sep 17 22:41:12 andromeda kernel: [    1.274324] pcieport-driver 0000:00:01.0: found MSI capability
Sep 17 22:41:12 andromeda kernel: [    1.274500] pcieport-driver 0000:00:06.0: found MSI capability
Sep 17 22:41:12 andromeda kernel: [    1.274673] pcieport-driver 0000:00:07.0: found MSI capability
Sep 17 22:41:12 andromeda kernel: [    1.274794] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep 17 22:41:12 andromeda kernel: [    1.274805] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Sep 17 22:41:12 andromeda kernel: [    1.274959] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Sep 17 22:41:12 andromeda kernel: [    1.274962] ACPI: Power Button (FF) [PWRF]
Sep 17 22:41:12 andromeda kernel: [    1.275017] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Sep 17 22:41:12 andromeda kernel: [    1.275020] ACPI: Power Button (CM) [PWRB]
Sep 17 22:41:12 andromeda kernel: [    1.275536] ACPI: SSDT BFFAE0C0, 01D2 (r1    AMI   CPU1PM        1 INTL 20051117)
Sep 17 22:41:12 andromeda kernel: [    1.275893] processor ACPI_CPU:00: registered as cooling_device0
Sep 17 22:41:12 andromeda kernel: [    1.275898] ACPI: Processor [CPU1] (supports 8 throttling states)
Sep 17 22:41:12 andromeda kernel: [    1.276239] ACPI: SSDT BFFAE2A0, 0143 (r1    AMI   CPU2PM        1 INTL 20051117)
Sep 17 22:41:12 andromeda kernel: [    1.276566] processor ACPI_CPU:01: registered as cooling_device1
Sep 17 22:41:12 andromeda kernel: [    1.276570] ACPI: Processor [CPU2] (supports 8 throttling states)
Sep 17 22:41:12 andromeda kernel: [    1.278943] isapnp: Scanning for PnP cards...
Sep 17 22:41:12 andromeda kernel: [    1.632385] isapnp: No Plug & Play device found
Sep 17 22:41:12 andromeda kernel: [    1.640821] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Sep 17 22:41:12 andromeda kernel: [    1.640913] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 17 22:41:12 andromeda kernel: [    1.641414] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Sep 17 22:41:12 andromeda kernel: [    1.642233] brd: module loaded
Sep 17 22:41:12 andromeda kernel: [    1.642578] loop: module loaded
Sep 17 22:41:12 andromeda kernel: [    1.642655] Fixed MDIO Bus: probed
Sep 17 22:41:12 andromeda kernel: [    1.642661] PPP generic driver version 2.4.2
Sep 17 22:41:12 andromeda kernel: [    1.642723] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Sep 17 22:41:12 andromeda kernel: [    1.642758] Driver 'sd' needs updating - please use bus_type methods
Sep 17 22:41:12 andromeda kernel: [    1.642768] Driver 'sr' needs updating - please use bus_type methods
Sep 17 22:41:12 andromeda kernel: [    1.642928] sata_sis 0000:00:05.0: version 1.0
Sep 17 22:41:12 andromeda kernel: [    1.642952] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Sep 17 22:41:12 andromeda kernel: [    1.642957] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
Sep 17 22:41:12 andromeda kernel: [    1.643076] scsi0 : sata_sis
Sep 17 22:41:12 andromeda kernel: [    1.643185] scsi1 : sata_sis
Sep 17 22:41:12 andromeda kernel: [    1.643811] ata1: PATA max UDMA/133 cmd 0xe800 ctl 0xe400 bmdma 0xd800 irq 17
Sep 17 22:41:12 andromeda kernel: [    1.643814] ata2: PATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd808 irq 17
Sep 17 22:41:12 andromeda kernel: [    1.831647] ata1.00: ATA-8: ST31000333AS, CC1H, max UDMA/133
Sep 17 22:41:12 andromeda kernel: [    1.831652] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Sep 17 22:41:12 andromeda kernel: [    1.887671] ata1.00: configured for UDMA/133
Sep 17 22:41:12 andromeda kernel: [    2.050904] scsi 0:0:0:0: Direct-Access     ATA      ST31000333AS     CC1H PQ: 0 ANSI: 5
Sep 17 22:41:12 andromeda kernel: [    2.051014] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Sep 17 22:41:12 andromeda kernel: [    2.051033] sd 0:0:0:0: [sda] Write Protect is off
Sep 17 22:41:12 andromeda kernel: [    2.051063] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 17 22:41:12 andromeda kernel: [    2.051144] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Sep 17 22:41:12 andromeda kernel: [    2.051159] sd 0:0:0:0: [sda] Write Protect is off
Sep 17 22:41:12 andromeda kernel: [    2.051188] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 17 22:41:12 andromeda kernel: [    2.051192]  sda: sda1 sda2 < sda5 sda6 sda7 >
Sep 17 22:41:12 andromeda kernel: [    2.120968] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 17 22:41:12 andromeda kernel: [    2.121021] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 17 22:41:12 andromeda kernel: [    2.121605] scsi2 : pata_sis
Sep 17 22:41:12 andromeda kernel: [    2.121670] scsi3 : pata_sis
Sep 17 22:41:12 andromeda kernel: [    2.122296] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
Sep 17 22:41:12 andromeda kernel: [    2.122299] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
Sep 17 22:41:12 andromeda kernel: [    2.284256] ata3.01: ATAPI: HL-DT-ST DVDRAM GSA-H42N, RL00, max UDMA/66
Sep 17 22:41:12 andromeda kernel: [    2.300274] ata3.01: configured for UDMA/66
Sep 17 22:41:12 andromeda kernel: [    2.306135] scsi 2:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
Sep 17 22:41:12 andromeda kernel: [    2.317736] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 17 22:41:12 andromeda kernel: [    2.317741] Uniform CD-ROM driver Revision: 3.20
Sep 17 22:41:12 andromeda kernel: [    2.317945] sr 2:0:1:0: Attached scsi generic sg1 type 5
Sep 17 22:41:12 andromeda kernel: [    2.318067] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Sep 17 22:41:12 andromeda kernel: [    2.318093] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Sep 17 22:41:12 andromeda kernel: [    2.318122] ehci_hcd 0000:00:03.3: EHCI Host Controller
Sep 17 22:41:12 andromeda kernel: [    2.318195] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
Sep 17 22:41:12 andromeda kernel: [    2.318238] ehci_hcd 0000:00:03.3: irq 22, io mem 0xfbffd000
Sep 17 22:41:12 andromeda kernel: [    2.328030] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
Sep 17 22:41:12 andromeda kernel: [    2.328140] usb usb1: configuration #1 chosen from 1 choice
Sep 17 22:41:12 andromeda kernel: [    2.328177] hub 1-0:1.0: USB hub found
Sep 17 22:41:12 andromeda kernel: [    2.328185] hub 1-0:1.0: 8 ports detected
Sep 17 22:41:12 andromeda kernel: [    2.328313] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Sep 17 22:41:12 andromeda kernel: [    2.328333] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Sep 17 22:41:12 andromeda kernel: [    2.328345] ohci_hcd 0000:00:03.0: OHCI Host Controller
Sep 17 22:41:12 andromeda kernel: [    2.328389] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
Sep 17 22:41:12 andromeda kernel: [    2.328407] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfbfff000
Sep 17 22:41:12 andromeda kernel: [    2.386062] usb usb2: configuration #1 chosen from 1 choice
Sep 17 22:41:12 andromeda kernel: [    2.386088] hub 2-0:1.0: USB hub found
Sep 17 22:41:12 andromeda kernel: [    2.386097] hub 2-0:1.0: 4 ports detected
Sep 17 22:41:12 andromeda kernel: [    2.386185] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Sep 17 22:41:12 andromeda kernel: [    2.386196] ohci_hcd 0000:00:03.1: OHCI Host Controller
Sep 17 22:41:12 andromeda kernel: [    2.386243] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
Sep 17 22:41:12 andromeda kernel: [    2.386259] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfbffe000
Sep 17 22:41:12 andromeda kernel: [    2.442063] usb usb3: configuration #1 chosen from 1 choice
Sep 17 22:41:12 andromeda kernel: [    2.442089] hub 3-0:1.0: USB hub found
Sep 17 22:41:12 andromeda kernel: [    2.442097] hub 3-0:1.0: 4 ports detected
Sep 17 22:41:12 andromeda kernel: [    2.442190] uhci_hcd: USB Universal Host Controller Interface driver
Sep 17 22:41:12 andromeda kernel: [    2.442286] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Sep 17 22:41:12 andromeda kernel: [    2.444566] serio: i8042 KBD port at 0x60,0x64 irq 1
Sep 17 22:41:12 andromeda kernel: [    2.444572] serio: i8042 AUX port at 0x60,0x64 irq 12
Sep 17 22:41:12 andromeda kernel: [    2.448065] mice: PS/2 mouse device common for all mice
Sep 17 22:41:12 andromeda kernel: [    2.460114] rtc_cmos 00:08: RTC can wake from S4
Sep 17 22:41:12 andromeda kernel: [    2.460170] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Sep 17 22:41:12 andromeda kernel: [    2.460193] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
Sep 17 22:41:12 andromeda kernel: [    2.460256] device-mapper: uevent: version 1.0.3
Sep 17 22:41:12 andromeda kernel: [    2.460366] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Sep 17 22:41:12 andromeda kernel: [    2.460439] device-mapper: multipath: version 1.0.5 loaded
Sep 17 22:41:12 andromeda kernel: [    2.460442] device-mapper: multipath round-robin: version 1.0.0 loaded
Sep 17 22:41:12 andromeda kernel: [    2.460521] EISA: Probing bus 0 at eisa.0
Sep 17 22:41:12 andromeda kernel: [    2.460557] EISA: Detected 0 cards.
Sep 17 22:41:12 andromeda kernel: [    2.460607] cpuidle: using governor ladder
Sep 17 22:41:12 andromeda kernel: [    2.460609] cpuidle: using governor menu
Sep 17 22:41:12 andromeda kernel: [    2.461171] TCP cubic registered
Sep 17 22:41:12 andromeda kernel: [    2.461276] NET: Registered protocol family 10
Sep 17 22:41:12 andromeda kernel: [    2.461747] lo: Disabled Privacy Extensions
Sep 17 22:41:12 andromeda kernel: [    2.462108] NET: Registered protocol family 17
Sep 17 22:41:12 andromeda kernel: [    2.462129] Bluetooth: L2CAP ver 2.11
Sep 17 22:41:12 andromeda kernel: [    2.462131] Bluetooth: L2CAP socket layer initialized
Sep 17 22:41:12 andromeda kernel: [    2.462135] Bluetooth: SCO (Voice Link) ver 0.6
Sep 17 22:41:12 andromeda kernel: [    2.462136] Bluetooth: SCO socket layer initialized
Sep 17 22:41:12 andromeda kernel: [    2.462171] Bluetooth: RFCOMM socket layer initialized
Sep 17 22:41:12 andromeda kernel: [    2.462181] Bluetooth: RFCOMM TTY layer initialized
Sep 17 22:41:12 andromeda kernel: [    2.462183] Bluetooth: RFCOMM ver 1.10
Sep 17 22:41:12 andromeda kernel: [    2.462742] Using IPI No-Shortcut mode
Sep 17 22:41:12 andromeda kernel: [    2.462829] registered taskstats version 1
Sep 17 22:41:12 andromeda kernel: [    2.462948]   Magic number: 9:762:704
Sep 17 22:41:12 andromeda kernel: [    2.463034] rtc_cmos 00:08: setting system clock to 2009-09-17 22:41:01 UTC (1253227261)
Sep 17 22:41:12 andromeda kernel: [    2.463039] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Sep 17 22:41:12 andromeda kernel: [    2.463040] EDD information not available.
Sep 17 22:41:12 andromeda kernel: [    2.463315] Freeing unused kernel memory: 532k freed
Sep 17 22:41:12 andromeda kernel: [    2.463454] Write protecting the kernel text: 4116k
Sep 17 22:41:12 andromeda kernel: [    2.463502] Write protecting the kernel read-only data: 1528k
Sep 17 22:41:12 andromeda kernel: [    2.478956] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Sep 17 22:41:12 andromeda kernel: [    2.683624] Floppy drive(s): fd0 is 1.44M
Sep 17 22:41:12 andromeda kernel: [    2.700280] FDC 0 is a post-1991 82077
Sep 17 22:41:12 andromeda kernel: [    3.028561] usb 2-2: new full speed USB device using ohci_hcd and address 2
Sep 17 22:41:12 andromeda kernel: [    3.338349] usb 2-2: configuration #1 chosen from 1 choice
Sep 17 22:41:12 andromeda kernel: [    3.349763] PM: Starting manual resume from disk
Sep 17 22:41:12 andromeda kernel: [    3.363867] EXT3-fs: INFO: recovery required on readonly filesystem.
Sep 17 22:41:12 andromeda kernel: [    3.363872] EXT3-fs: write access will be enabled during recovery.
Sep 17 22:41:12 andromeda kernel: [    3.788162] kjournald starting.  Commit interval 5 seconds
Sep 17 22:41:12 andromeda kernel: [    3.788187] EXT3-fs: sda6: orphan cleanup on readonly fs
Sep 17 22:41:12 andromeda kernel: [    3.788272] EXT3-fs: sda6: 3 orphan inodes deleted
Sep 17 22:41:12 andromeda kernel: [    3.788274] EXT3-fs: recovery complete.
Sep 17 22:41:12 andromeda kernel: [    3.810012] EXT3-fs: mounted filesystem with ordered data mode.
Sep 17 22:41:12 andromeda kernel: [    8.827282] udev: starting version 141
Sep 17 22:41:12 andromeda kernel: [    9.415597] Linux agpgart interface v0.103
Sep 17 22:41:12 andromeda kernel: [    9.684089] parport_pc 00:05: reported by Plug and Play ACPI
Sep 17 22:41:12 andromeda kernel: [    9.684188] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Sep 17 22:41:12 andromeda kernel: [    9.685448] input: PC Speaker as /devices/platform/pcspkr/input/input4
Sep 17 22:41:12 andromeda kernel: [    9.720598] sis190 Gigabit Ethernet driver 1.2 loaded.
Sep 17 22:41:12 andromeda kernel: [    9.720625] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep 17 22:41:12 andromeda kernel: [    9.720821] 0000:00:04.0: Read MAC address from EEPROM
Sep 17 22:41:12 andromeda kernel: [    9.720823] 0000:00:04.0: Error EEPROM read 0.
Sep 17 22:41:12 andromeda kernel: [    9.720827] 0000:00:04.0: Read MAC address from APC.
Sep 17 22:41:12 andromeda kernel: [    9.729319] Linux video capture interface: v2.00
Sep 17 22:41:12 andromeda kernel: [    9.768806] 0000:00:04.0: Atheros PHY AR8012 transceiver at address 1.
Sep 17 22:41:12 andromeda kernel: [    9.772690] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Sep 17 22:41:12 andromeda kernel: [    9.914740] nvidia: module license 'NVIDIA' taints kernel.
Sep 17 22:41:12 andromeda kernel: [   10.169951] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep 17 22:41:12 andromeda kernel: [   10.171246] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Sep 17 22:41:12 andromeda kernel: [   10.202017] ppdev: user-space parallel port driver
Sep 17 22:41:12 andromeda kernel: [   10.218759] gspca: main v2.3.0 registered
Sep 17 22:41:12 andromeda kernel: [   10.229274] gspca: probing 093a:2471
Sep 17 22:41:12 andromeda kernel: [   10.234081] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
Sep 17 22:41:12 andromeda kernel: [   10.234085] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2471)
Sep 17 22:41:12 andromeda kernel: [   10.250022] gspca: probe ok
Sep 17 22:41:12 andromeda kernel: [   10.250056] usbcore: registered new interface driver pac207
Sep 17 22:41:12 andromeda kernel: [   10.250082] pac207: registered
Sep 17 22:41:12 andromeda kernel: [   10.268562] 0000:00:04.0: Using transceiver at address 1 as default.
Sep 17 22:41:12 andromeda kernel: [   10.301324] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f7d88c00 (IRQ: 19), 00:1e:8c:07:a9:8e
Sep 17 22:41:12 andromeda kernel: [   10.301329] eth0: GMII mode.
Sep 17 22:41:12 andromeda kernel: [   10.301337] eth0: Enabling Auto-negotiation.
Sep 17 22:41:12 andromeda kernel: [   10.349188] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep 17 22:41:12 andromeda kernel: [   10.658497] Adding 9116848k swap on /dev/sda7.  Priority:-1 extents:1 across:9116848k
Sep 17 22:41:12 andromeda kernel: [   11.087381] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Sep 17 22:41:12 andromeda kernel: [   11.203288] EXT3 FS on sda6, internal journal
Sep 17 22:41:12 andromeda kernel: [   12.221794] type=1505 audit(1253238071.256:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1915
Sep 17 22:41:12 andromeda kernel: [   12.273201] type=1505 audit(1253238071.308:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1919
Sep 17 22:41:12 andromeda kernel: [   12.273383] type=1505 audit(1253238071.308:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1919
Sep 17 22:41:12 andromeda kernel: [   12.273434] type=1505 audit(1253238071.308:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1919
Sep 17 22:41:12 andromeda kernel: [   12.273478] type=1505 audit(1253238071.308:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1919
Sep 17 22:41:12 andromeda kernel: [   12.398801] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 17 22:41:12 andromeda kernel: [   12.420324] type=1505 audit(1253238071.456:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1924
Sep 17 22:41:12 andromeda kernel: [   12.420616] type=1505 audit(1253238071.456:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1924
Sep 17 22:41:12 andromeda kernel: [   12.453792] type=1505 audit(1253238071.488:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1940
Sep 17 22:41:14 andromeda kernel: [   15.263007] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 17 22:41:14 andromeda kernel: [   15.263011] Bluetooth: BNEP filters: protocol multicast
Sep 17 22:41:14 andromeda kernel: [   15.274304] Bridge firewalling registered
Sep 17 22:41:21 andromeda kernel: [   22.428023] eth0: mii ext = 0000.
Sep 17 22:41:21 andromeda kernel: [   22.444047] eth0: mii lpa = 45e1 adv = 01e1.
Sep 17 22:41:21 andromeda kernel: [   22.444052] eth0: link on 100 Mbps Full Duplex mode.
Sep 17 22:41:21 andromeda kernel: [   22.444293] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Sep 17 22:41:21 andromeda kernel: [   22.680025] eth0: mii ext = 0000.
Sep 17 22:41:21 andromeda kernel: [   22.696023] eth0: mii lpa = 45e1 adv = 01e1.
Sep 17 22:41:21 andromeda kernel: [   22.696027] eth0: link on 100 Mbps Full Duplex mode.
Sep 17 22:43:10 andromeda kernel: [  131.444033] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

Last log had 2 crashes in that time. I'll really appreciate any help anyone can give me. I'm sorry if I haven't posted correctly!

Thank you!

---

