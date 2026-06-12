---
title: "Google Earth : slowness"
date: 2011-07-22
forum: General Help
---

### Post by jawaka. on 2011-07-22
Hello !

I've got a Xubunt 11.04 with an ATI RADEON 9550 on a desktop pc.
I've installed Google Earth with the .deb from the google earth website.
The problem is that it is too slow.

Direct Rendering works with glxinfo but it seems that it's not a "true" direct rendering because I've got an ATI card.

Then I've tried to install driconf : but when I run it, it says :

"Could not detect any configurable direct rendering capable devices"

If I change the graphic card, can the problem be solved ?
Or if I switch to Ubuntu ?

Thank you for any help : )

---

### Post by Toz on 2011-07-22
Which video driver is your computer using (open source or proprietary)? Open a terminal window (Accessories->Terminal Emulator), type in the following command and post back the results:
```
lspci -vnn
```

And can you also post back the contents of **/var/log/Xorg.0.log**?

If you go to System->Additional Drivers, is anything displayed there?

---

### Post by jawaka. on 2011-07-22
There's nothing in "additional drivers".[B]

lspci -cnn :[/B]

```

00:00.0 Host bridge [0600]: nVidia Corporation nForce3 250Gb Host Bridge [10de:00e1] (rev a1)
    Subsystem: ASUSTeK Computer Inc. K8N-E [1043:813f]
    Flags: bus master, 66MHz, fast devsel, latency 0
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Capabilities: <access denied>

00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 250Gb LPC Bridge [10de:00e0] (rev a2)
    Subsystem: ASUSTeK Computer Inc. K8N-E [1043:813f]
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus [0c05]: nVidia Corporation nForce 250Gb PCI System Management [10de:00e4] (rev a1)
    Subsystem: ASUSTeK Computer Inc. K8N-E [1043:813f]
    Flags: 66MHz, fast devsel
    I/O ports at 5080 [size=32]
    I/O ports at 5000 [size=64]
    I/O ports at 5040 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:02.0 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. K8N-E [1043:813f]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at ff6fd000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.1 USB Controller [0c03]: nVidia Corporation CK8S USB Controller [10de:00e7] (rev a1) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. K8N-E [1043:813f]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at ff6fe000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 EHCI USB 2.0 Controller [10de:00e8] (rev a2) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. K8N-E [1043:813f]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at ff6ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:05.0 Bridge [0680]: nVidia Corporation CK8S Ethernet Controller [10de:00df] (rev a2)
    Subsystem: ASUSTeK Computer Inc. K8N-E [1043:80a7]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at ff6fc000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at ec00 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce3 250Gb AC'97 Audio Controller [10de:00ea] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:812a]
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    I/O ports at e800 [size=256]
    I/O ports at e400 [size=128]
    Memory at ff6fb000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:08.0 IDE interface [0101]: nVidia Corporation CK8S Parallel ATA Controller (v2.5) [10de:00e5] (rev a2) (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. K8N-E [1043:813f]
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd
    Kernel modules: pata_amd

00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge [10de:00e2] (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, medium devsel, latency 16
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: ff500000-ff5fffff
    Prefetchable memory behind bridge: 9eb00000-deafffff
    Kernel modules: shpchp

00:0e.0 PCI bridge [0604]: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge [10de:00ed] (rev a2) (prog-if 00 [Normal decode])
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
    Kernel modules: shpchp

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
    Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
    Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AS [Radeon 9550] [1002:4153] (prog-if 00 [VGA controller])
    Subsystem: C.P. Technology Co. Ltd Device [148c:2084]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at d800 [size=256]
    Memory at ff5f0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at ff5c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-amd64
    Kernel modules: radeon, radeonfb

01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary) [1002:4173]
    Subsystem: C.P. Technology Co. Ltd Device [148c:2085]
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at b0000000 (32-bit, prefetchable) [size=256M]
    Memory at ff5e0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>


```

**/var/log/Xorg.0.log :**

```

[    21.949] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    21.949] X Protocol Version 11, Revision 0
[    21.949] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    21.949] Current Operating System: Linux andre-ordi 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    21.949] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=686cc968-f667-47fe-ad91-c46c67c6af9f ro quiet splash vt.handoff=7
[    21.949] Build Date: 21 May 2011  11:38:35AM
[    21.949] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    21.949] Current version of pixman: 0.20.2
[    21.949]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.949] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.949] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 22 15:42:22 2011
[    21.977] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.985] (==) No Layout section.  Using the first Screen section.
[    21.985] (==) No screen section available. Using defaults.
[    21.985] (**) |-->Screen "Default Screen Section" (0)
[    21.985] (**) |   |-->Monitor "<default monitor>"
[    21.985] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    21.985] (==) Automatically adding devices
[    21.985] (==) Automatically enabling devices
[    21.986] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.986]     Entry deleted from font path.
[    21.986] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.986]     Entry deleted from font path.
[    21.986] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.986]     Entry deleted from font path.
[    21.986] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.986]     Entry deleted from font path.
[    21.986] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.986]     Entry deleted from font path.
[    21.986] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.986] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.986] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.986] (II) Loader magic: 0x81ffde0
[    21.986] (II) Module ABI versions:
[    21.986]     X.Org ANSI C Emulation: 0.4
[    21.986]     X.Org Video Driver: 10.0
[    21.986]     X.Org XInput driver : 12.3
[    21.986]     X.Org Server Extension : 5.0
[    21.987] (--) PCI:*(0:1:0:0) 1002:4153:148c:2084 rev 0, Mem @ 0xc0000000/268435456, 0xff5f0000/65536, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
[    21.987] (--) PCI: (0:1:0:1) 1002:4173:148c:2085 rev 0, Mem @ 0xb0000000/268435456, 0xff5e0000/65536
[    21.987] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.987] (II) LoadModule: "extmod"
[    22.065] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.072] (II) Module extmod: vendor="X.Org Foundation"
[    22.072]     compiled for 1.10.1, module version = 1.0.0
[    22.072]     Module class: X.Org Server Extension
[    22.072]     ABI class: X.Org Server Extension, version 5.0
[    22.072] (II) Loading extension MIT-SCREEN-SAVER
[    22.072] (II) Loading extension XFree86-VidModeExtension
[    22.072] (II) Loading extension XFree86-DGA
[    22.072] (II) Loading extension DPMS
[    22.072] (II) Loading extension XVideo
[    22.072] (II) Loading extension XVideo-MotionCompensation
[    22.072] (II) Loading extension X-Resource
[    22.072] (II) LoadModule: "dbe"
[    22.073] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.073] (II) Module dbe: vendor="X.Org Foundation"
[    22.073]     compiled for 1.10.1, module version = 1.0.0
[    22.073]     Module class: X.Org Server Extension
[    22.073]     ABI class: X.Org Server Extension, version 5.0
[    22.073] (II) Loading extension DOUBLE-BUFFER
[    22.073] (II) LoadModule: "glx"
[    22.073] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.073] (II) Module glx: vendor="X.Org Foundation"
[    22.073]     compiled for 1.10.1, module version = 1.0.0
[    22.073]     ABI class: X.Org Server Extension, version 5.0
[    22.073] (==) AIGLX enabled
[    22.073] (II) Loading extension GLX
[    22.073] (II) LoadModule: "record"
[    22.074] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.074] (II) Module record: vendor="X.Org Foundation"
[    22.074]     compiled for 1.10.1, module version = 1.13.0
[    22.074]     Module class: X.Org Server Extension
[    22.074]     ABI class: X.Org Server Extension, version 5.0
[    22.074] (II) Loading extension RECORD
[    22.074] (II) LoadModule: "dri"
[    22.074] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.074] (II) Module dri: vendor="X.Org Foundation"
[    22.074]     compiled for 1.10.1, module version = 1.0.0
[    22.074]     ABI class: X.Org Server Extension, version 5.0
[    22.074] (II) Loading extension XFree86-DRI
[    22.074] (II) LoadModule: "dri2"
[    22.074] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.075] (II) Module dri2: vendor="X.Org Foundation"
[    22.075]     compiled for 1.10.1, module version = 1.2.0
[    22.075]     ABI class: X.Org Server Extension, version 5.0
[    22.075] (II) Loading extension DRI2
[    22.075] (==) Matched fglrx as autoconfigured driver 0
[    22.075] (==) Matched ati as autoconfigured driver 1
[    22.075] (==) Matched vesa as autoconfigured driver 2
[    22.075] (==) Matched fbdev as autoconfigured driver 3
[    22.075] (==) Assigned the driver to the xf86ConfigLayout
[    22.075] (II) LoadModule: "fglrx"
[    22.076] (WW) Warning, couldn't open module fglrx
[    22.076] (II) UnloadModule: "fglrx"
[    22.076] (II) Unloading fglrx
[    22.076] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    22.076] (II) LoadModule: "ati"
[    22.076] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    22.076] (II) Module ati: vendor="X.Org Foundation"
[    22.076]     compiled for 1.10.1, module version = 6.14.0
[    22.076]     Module class: X.Org Video Driver
[    22.076]     ABI class: X.Org Video Driver, version 10.0
[    22.076] (II) LoadModule: "radeon"
[    22.077] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    22.077] (II) Module radeon: vendor="X.Org Foundation"
[    22.077]     compiled for 1.10.1, module version = 6.14.0
[    22.077]     Module class: X.Org Video Driver
[    22.077]     ABI class: X.Org Video Driver, version 10.0
[    22.077] (II) LoadModule: "vesa"
[    22.078] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.078] (II) Module vesa: vendor="X.Org Foundation"
[    22.078]     compiled for 1.10.0, module version = 2.3.0
[    22.078]     Module class: X.Org Video Driver
[    22.078]     ABI class: X.Org Video Driver, version 10.0
[    22.078] (II) LoadModule: "fbdev"
[    22.078] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.078] (II) Module fbdev: vendor="X.Org Foundation"
[    22.078]     compiled for 1.10.0, module version = 0.4.2
[    22.078]     ABI class: X.Org Video Driver, version 10.0
[    22.078] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, AMD Radeon HD 6900M Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS,
    Mobility Radeon HD 6000 Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, BARTS, BARTS, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6800 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS
[    22.086] (II) VESA: driver for VESA chipsets: vesa
[    22.086] (II) FBDEV: driver for framebuffer: fbdev
[    22.086] (++) using VT number 7

[    22.087] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    22.087] (II) [KMS] drm report modesetting isn't supported.
[    22.087] (WW) Falling back to old probe method for vesa
[    22.087] (WW) Falling back to old probe method for fbdev
[    22.087] (II) Loading sub module "fbdevhw"
[    22.087] (II) LoadModule: "fbdevhw"
[    22.087] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.087] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.087]     compiled for 1.10.1, module version = 0.0.2
[    22.087]     ABI class: X.Org Video Driver, version 10.0
[    22.087] (II) RADEON(0): TOTO SAYS 00000000ff5f0000
[    22.087] (II) RADEON(0): MMIO registers at 0x00000000ff5f0000: size 64KB
[    22.088] (II) RADEON(0): PCI bus 1 card 0 func 0
[    22.088] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.088] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    22.088] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    22.088] (==) RADEON(0): Default visual is TrueColor
[    22.088] (II) Loading sub module "vgahw"
[    22.088] (II) LoadModule: "vgahw"
[    22.088] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    22.088] (II) Module vgahw: vendor="X.Org Foundation"
[    22.088]     compiled for 1.10.1, module version = 0.1.0
[    22.088]     ABI class: X.Org Video Driver, version 10.0
[    22.088] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    22.088] (==) RADEON(0): RGB weight 888
[    22.088] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    22.088] (--) RADEON(0): Chipset: "ATI Radeon 9600 AS (AGP)" (ChipID = 0x4153)
[    22.088] (--) RADEON(0): Linear framebuffer at 0x00000000c0000000
[    22.088] (II) RADEON(0): AGP card detected
[    22.089] (II) Loading sub module "int10"
[    22.089] (II) LoadModule: "int10"
[    22.089] (II) Loading /usr/lib/xorg/modules/libint10.so
[    22.089] (II) Module int10: vendor="X.Org Foundation"
[    22.089]     compiled for 1.10.1, module version = 1.0.0
[    22.089]     ABI class: X.Org Video Driver, version 10.0
[    22.089] (II) RADEON(0): initializing int10
[    22.094] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    22.095] (II) RADEON(0): Legacy BIOS detected
[    22.095] drmOpenDevice: node name is /dev/dri/card0
[    22.210] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    22.210] drmOpenDevice: node name is /dev/dri/card0
[    22.214] drmOpenByBusid: drmOpenMinor returns -1
[    22.214] drmOpenDevice: node name is /dev/dri/card1
[    22.218] drmOpenByBusid: drmOpenMinor returns -1
[    22.218] drmOpenDevice: node name is /dev/dri/card2
[    22.222] drmOpenByBusid: drmOpenMinor returns -1
[    22.222] drmOpenDevice: node name is /dev/dri/card3
[    22.226] drmOpenByBusid: drmOpenMinor returns -1
[    22.226] drmOpenDevice: node name is /dev/dri/card4
[    22.230] drmOpenByBusid: drmOpenMinor returns -1
[    22.230] drmOpenDevice: node name is /dev/dri/card5
[    22.234] drmOpenByBusid: drmOpenMinor returns -1
[    22.234] drmOpenDevice: node name is /dev/dri/card6
[    22.237] drmOpenByBusid: drmOpenMinor returns -1
[    22.237] drmOpenDevice: node name is /dev/dri/card7
[    22.241] drmOpenByBusid: drmOpenMinor returns -1
[    22.241] drmOpenDevice: node name is /dev/dri/card8
[    22.245] drmOpenByBusid: drmOpenMinor returns -1
[    22.245] drmOpenDevice: node name is /dev/dri/card9
[    22.249] drmOpenByBusid: drmOpenMinor returns -1
[    22.249] drmOpenDevice: node name is /dev/dri/card10
[    22.253] drmOpenByBusid: drmOpenMinor returns -1
[    22.253] drmOpenDevice: node name is /dev/dri/card11
[    22.257] drmOpenByBusid: drmOpenMinor returns -1
[    22.257] drmOpenDevice: node name is /dev/dri/card12
[    22.261] drmOpenByBusid: drmOpenMinor returns -1
[    22.261] drmOpenDevice: node name is /dev/dri/card13
[    22.265] drmOpenByBusid: drmOpenMinor returns -1
[    22.265] drmOpenDevice: node name is /dev/dri/card14
[    22.269] drmOpenByBusid: drmOpenMinor returns -1
[    22.269] drmOpenDevice: node name is /dev/dri/card15
[    22.273] drmOpenByBusid: drmOpenMinor returns -1
[    22.273] drmOpenDevice: node name is /dev/dri/card0
[    22.279] drmOpenDevice: node name is /dev/dri/card0
[    22.282] drmOpenDevice: node name is /dev/dri/card1
[    22.286] drmOpenDevice: node name is /dev/dri/card2
[    22.290] drmOpenDevice: node name is /dev/dri/card3
[    22.294] drmOpenDevice: node name is /dev/dri/card4
[    22.298] drmOpenDevice: node name is /dev/dri/card5
[    22.302] drmOpenDevice: node name is /dev/dri/card6
[    22.306] drmOpenDevice: node name is /dev/dri/card7
[    22.310] drmOpenDevice: node name is /dev/dri/card8
[    22.313] drmOpenDevice: node name is /dev/dri/card9
[    22.317] drmOpenDevice: node name is /dev/dri/card10
[    22.321] drmOpenDevice: node name is /dev/dri/card11
[    22.325] drmOpenDevice: node name is /dev/dri/card12
[    22.329] drmOpenDevice: node name is /dev/dri/card13
[    22.333] drmOpenDevice: node name is /dev/dri/card14
[    22.337] drmOpenDevice: node name is /dev/dri/card15
[    22.341] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    22.341] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    22.341] (II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
[    22.341] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[    22.341] (II) RADEON(0): Color tiling enabled by default
[    22.341] (II) Loading sub module "ddc"
[    22.341] (II) LoadModule: "ddc"
[    22.341] (II) Module "ddc" already built-in
[    22.341] (II) Loading sub module "i2c"
[    22.341] (II) LoadModule: "i2c"
[    22.341] (II) Module "i2c" already built-in
[    22.341] (II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 20000, sclk: 250.000000, mclk: 200.000000
[    22.341] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=20000
[    22.341] (II) RADEON(0): DFP table revision: 3
[    22.341] (II) RADEON(0): Output VGA-0 has no monitor section
[    22.341] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    22.341] (II) RADEON(0): Output DVI-0 has no monitor section
[    22.341] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    22.341] (II) RADEON(0): Output S-video has no monitor section
[    22.341] (II) RADEON(0): Default TV standard: PAL
[    22.341] (II) RADEON(0): TV standards supported by chip: NTSC PAL 
[    22.341] (II) RADEON(0): Port0:
[    22.341]   XRANDR name: VGA-0
[    22.341]   Connector: VGA
[    22.341]   CRT1: INTERNAL_DAC1
[    22.341]   DDC reg: 0x60
[    22.341] (II) RADEON(0): Port1:
[    22.341]   XRANDR name: DVI-0
[    22.341]   Connector: DVI-I
[    22.341]   CRT2: INTERNAL_DAC2
[    22.341]   DFP1: INTERNAL_TMDS1
[    22.341]   DDC reg: 0x64
[    22.341] (II) RADEON(0): Port2:
[    22.341]   XRANDR name: S-video
[    22.341]   Connector: S-video
[    22.341]   TV1: INTERNAL_DAC2
[    22.341]   DDC reg: 0x0
[    22.341] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    22.347] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    22.347] finished output detect: 0
[    22.347] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    22.434] (II) RADEON(0): EDID for output DVI-0
[    22.434] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    22.434] (II) RADEON(0): Year: 2006  Week: 33
[    22.434] (II) RADEON(0): EDID Version: 1.3
[    22.434] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    22.434] (II) RADEON(0): Sync:  Separate  Composite
[    22.434] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    22.434] (II) RADEON(0): Gamma: 2.20
[    22.434] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    22.434] (II) RADEON(0): First detailed timing is preferred mode
[    22.434] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    22.434] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    22.434] (II) RADEON(0): Supported established timings:
[    22.434] (II) RADEON(0): 720x400@70Hz
[    22.434] (II) RADEON(0): 640x480@60Hz
[    22.434] (II) RADEON(0): 640x480@67Hz
[    22.434] (II) RADEON(0): 640x480@72Hz
[    22.434] (II) RADEON(0): 640x480@75Hz
[    22.434] (II) RADEON(0): 800x600@60Hz
[    22.434] (II) RADEON(0): 800x600@72Hz
[    22.434] (II) RADEON(0): 800x600@75Hz
[    22.434] (II) RADEON(0): 832x624@75Hz
[    22.434] (II) RADEON(0): 1024x768@60Hz
[    22.434] (II) RADEON(0): 1024x768@70Hz
[    22.434] (II) RADEON(0): 1024x768@75Hz
[    22.434] (II) RADEON(0): 1280x1024@75Hz
[    22.435] (II) RADEON(0): 1152x864@75Hz
[    22.435] (II) RADEON(0): Manufacturer's mask: 0
[    22.435] (II) RADEON(0): Supported standard timings:
[    22.435] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    22.435] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    22.435] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    22.435] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    22.435] (II) RADEON(0): Supported detailed timing:
[    22.435] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    22.435] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    22.435] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    22.435] (II) RADEON(0): Supported detailed timing:
[    22.435] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    22.435] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    22.435] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    22.435] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    22.435] (II) RADEON(0): Monitor name: BenQ FP91G+
[    22.435] (II) RADEON(0): EDID (in hex):
[    22.435] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    22.435] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    22.435] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    22.435] (II) RADEON(0):     010101010101302a009851002a403070
[    22.435] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    22.435] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    22.435] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    22.435] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    22.435] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    22.435] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    22.435] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    22.435] (II) RADEON(0): Year: 2006  Week: 33
[    22.435] (II) RADEON(0): EDID Version: 1.3
[    22.435] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    22.435] (II) RADEON(0): Sync:  Separate  Composite
[    22.435] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    22.435] (II) RADEON(0): Gamma: 2.20
[    22.435] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    22.435] (II) RADEON(0): First detailed timing is preferred mode
[    22.435] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    22.435] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    22.435] (II) RADEON(0): Supported established timings:
[    22.435] (II) RADEON(0): 720x400@70Hz
[    22.435] (II) RADEON(0): 640x480@60Hz
[    22.435] (II) RADEON(0): 640x480@67Hz
[    22.435] (II) RADEON(0): 640x480@72Hz
[    22.435] (II) RADEON(0): 640x480@75Hz
[    22.435] (II) RADEON(0): 800x600@60Hz
[    22.435] (II) RADEON(0): 800x600@72Hz
[    22.435] (II) RADEON(0): 800x600@75Hz
[    22.435] (II) RADEON(0): 832x624@75Hz
[    22.435] (II) RADEON(0): 1024x768@60Hz
[    22.435] (II) RADEON(0): 1024x768@70Hz
[    22.435] (II) RADEON(0): 1024x768@75Hz
[    22.435] (II) RADEON(0): 1280x1024@75Hz
[    22.435] (II) RADEON(0): 1152x864@75Hz
[    22.435] (II) RADEON(0): Manufacturer's mask: 0
[    22.435] (II) RADEON(0): Supported standard timings:
[    22.435] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    22.435] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    22.435] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    22.435] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    22.435] (II) RADEON(0): Supported detailed timing:
[    22.440] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    22.440] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    22.440] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    22.440] (II) RADEON(0): Supported detailed timing:
[    22.440] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    22.440] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    22.440] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    22.440] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    22.440] (II) RADEON(0): Monitor name: BenQ FP91G+
[    22.440] (II) RADEON(0): EDID (in hex):
[    22.440] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    22.440] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    22.440] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    22.440] (II) RADEON(0):     010101010101302a009851002a403070
[    22.440] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    22.440] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    22.440] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    22.440] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    22.440] finished output detect: 1
[    22.440] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    22.440] finished output detect: 2
[    22.440] finished all detect
[    22.450] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    22.450] (II) RADEON(0): EDID for output VGA-0
[    22.528] (II) RADEON(0): EDID for output DVI-0
[    22.528] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    22.528] (II) RADEON(0): Year: 2006  Week: 33
[    22.528] (II) RADEON(0): EDID Version: 1.3
[    22.528] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    22.528] (II) RADEON(0): Sync:  Separate  Composite
[    22.528] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    22.528] (II) RADEON(0): Gamma: 2.20
[    22.528] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    22.528] (II) RADEON(0): First detailed timing is preferred mode
[    22.528] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    22.528] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    22.528] (II) RADEON(0): Supported established timings:
[    22.528] (II) RADEON(0): 720x400@70Hz
[    22.528] (II) RADEON(0): 640x480@60Hz
[    22.528] (II) RADEON(0): 640x480@67Hz
[    22.528] (II) RADEON(0): 640x480@72Hz
[    22.528] (II) RADEON(0): 640x480@75Hz
[    22.528] (II) RADEON(0): 800x600@60Hz
[    22.528] (II) RADEON(0): 800x600@72Hz
[    22.528] (II) RADEON(0): 800x600@75Hz
[    22.528] (II) RADEON(0): 832x624@75Hz
[    22.528] (II) RADEON(0): 1024x768@60Hz
[    22.528] (II) RADEON(0): 1024x768@70Hz
[    22.529] (II) RADEON(0): 1024x768@75Hz
[    22.529] (II) RADEON(0): 1280x1024@75Hz
[    22.529] (II) RADEON(0): 1152x864@75Hz
[    22.529] (II) RADEON(0): Manufacturer's mask: 0
[    22.529] (II) RADEON(0): Supported standard timings:
[    22.529] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    22.529] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    22.529] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    22.529] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    22.529] (II) RADEON(0): Supported detailed timing:
[    22.529] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    22.529] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    22.529] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    22.529] (II) RADEON(0): Supported detailed timing:
[    22.529] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    22.529] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    22.529] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    22.529] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    22.529] (II) RADEON(0): Monitor name: BenQ FP91G+
[    22.529] (II) RADEON(0): EDID (in hex):
[    22.529] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    22.529] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    22.529] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    22.529] (II) RADEON(0):     010101010101302a009851002a403070
[    22.529] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    22.529] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    22.529] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    22.529] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    22.529] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    22.529] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    22.529] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    22.529] (II) RADEON(0): Year: 2006  Week: 33
[    22.529] (II) RADEON(0): EDID Version: 1.3
[    22.529] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    22.529] (II) RADEON(0): Sync:  Separate  Composite
[    22.529] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    22.529] (II) RADEON(0): Gamma: 2.20
[    22.529] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    22.529] (II) RADEON(0): First detailed timing is preferred mode
[    22.529] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    22.529] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    22.529] (II) RADEON(0): Supported established timings:
[    22.529] (II) RADEON(0): 720x400@70Hz
[    22.529] (II) RADEON(0): 640x480@60Hz
[    22.529] (II) RADEON(0): 640x480@67Hz
[    22.529] (II) RADEON(0): 640x480@72Hz
[    22.529] (II) RADEON(0): 640x480@75Hz
[    22.529] (II) RADEON(0): 800x600@60Hz
[    22.529] (II) RADEON(0): 800x600@72Hz
[    22.529] (II) RADEON(0): 800x600@75Hz
[    22.529] (II) RADEON(0): 832x624@75Hz
[    22.529] (II) RADEON(0): 1024x768@60Hz
[    22.529] (II) RADEON(0): 1024x768@70Hz
[    22.529] (II) RADEON(0): 1024x768@75Hz
[    22.529] (II) RADEON(0): 1280x1024@75Hz
[    22.529] (II) RADEON(0): 1152x864@75Hz
[    22.529] (II) RADEON(0): Manufacturer's mask: 0
[    22.529] (II) RADEON(0): Supported standard timings:
[    22.529] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    22.529] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    22.529] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    22.529] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    22.529] (II) RADEON(0): Supported detailed timing:
[    22.529] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    22.530] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    22.530] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    22.530] (II) RADEON(0): Supported detailed timing:
[    22.530] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    22.530] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    22.530] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    22.530] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    22.530] (II) RADEON(0): Monitor name: BenQ FP91G+
[    22.530] (II) RADEON(0): EDID (in hex):
[    22.530] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    22.530] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    22.530] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    22.530] (II) RADEON(0):     010101010101302a009851002a403070
[    22.530] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    22.530] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    22.530] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    22.530] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    22.530] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    22.530] (II) RADEON(0): Printing probed modes for output DVI-0
[    22.530] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.530] (II) RADEON(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[    22.530] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    22.530] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    22.530] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    22.530] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    22.530] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    22.530] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.530] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.530] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    22.530] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.530] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.530] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    22.530] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    22.530] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    22.530] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.530] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.530] (II) RADEON(0): Modeline "640x350"x70.1   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    22.530] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    22.530] (II) RADEON(0): EDID for output S-video
[    22.530] (II) RADEON(0): Output VGA-0 disconnected
[    22.530] (II) RADEON(0): Output DVI-0 connected
[    22.530] (II) RADEON(0): Output S-video disconnected
[    22.530] (II) RADEON(0): Using exact sizes for initial modes
[    22.530] (II) RADEON(0): Output DVI-0 using initial mode 1280x1024
[    22.530] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.530] (==) RADEON(0): DPI set to (96, 96)
[    22.530] (II) Loading sub module "fb"
[    22.530] (II) LoadModule: "fb"
[    22.531] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.531] (II) Module fb: vendor="X.Org Foundation"
[    22.531]     compiled for 1.10.1, module version = 1.0.0
[    22.531]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.531] (II) Loading sub module "ramdac"
[    22.531] (II) LoadModule: "ramdac"
[    22.531] (II) Module "ramdac" already built-in
[    22.531] (==) RADEON(0): Using XAA acceleration architecture
[    22.531] (II) Loading sub module "xaa"
[    22.531] (II) LoadModule: "xaa"
[    22.531] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    22.531] (II) Module xaa: vendor="X.Org Foundation"
[    22.531]     compiled for 1.10.1, module version = 1.2.1
[    22.531]     ABI class: X.Org Video Driver, version 10.0
[    22.531] (==) RADEON(0): Assuming overlay scaler buffer width is 1920
[    22.531] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    22.532] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    22.532] (II) UnloadModule: "vesa"
[    22.532] (II) Unloading vesa
[    22.532] (II) UnloadModule: "fbdev"
[    22.532] (II) Unloading fbdev
[    22.532] (II) UnloadModule: "fbdevhw"
[    22.532] (II) Unloading fbdevhw
[    22.532] (--) Depth 24 pixmap format is 32 bpp
[    22.532] (II) RADEON(0): RADEONScreenInit c0000000 0 0
[    22.565] Entering TV Save
[    22.565] Save TV timing tables
[    22.565] saveTimingTables: reading timing tables
[    22.565] TV Save done
[    22.565] disable TVDAC
[    22.565] (II) RADEON(0): Dynamic Power Management Disabled
[    22.565] (II) RADEON(0): RADEONInitMemoryMap() : 
[    22.565] (II) RADEON(0):   mem_size         : 0x10000000
[    22.565] (II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000
[    22.565] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    22.565] (II) RADEON(0): Depth moves disabled by default
[    22.565] (II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
[    22.565] (II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
[    22.565] (II) RADEON(0): Largest offscreen area available: 1280 x 6909
[    22.566] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    22.566] (II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0x1fff0000
[    22.566] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    22.766] (==) RADEON(0): Backing store disabled
[    22.766] (WW) RADEON(0): Direct rendering disabled
[    22.766] (II) RADEON(0): Render acceleration disabled
[    22.766] (II) RADEON(0): num quad-pipes is 1
[    22.766] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    22.766]     Screen to screen bit blits
[    22.766]     Solid filled rectangles
[    22.766]     8x8 mono pattern filled rectangles
[    22.766]     Indirect CPU to Screen color expansion
[    22.766]     Solid Lines
[    22.766]     Scanline Image Writes
[    22.766]     Setting up tile and stipple cache:
[    22.766]         32 128x128 slots
[    22.766]         32 256x256 slots
[    22.766]         16 512x512 slots
[    22.766] (II) RADEON(0): Acceleration enabled
[    22.766] (==) RADEON(0): DPMS enabled
[    22.766] (==) RADEON(0): Silken mouse enabled
[    22.766] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
[    22.767] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
[    22.767] (II) RADEON(0): Largest offscreen area available: 1280 x 6901
[    22.767] (II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
[    22.767] (II) Loading sub module "theatre_detect"
[    22.767] (II) LoadModule: "theatre_detect"
[    22.767] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    22.767] (II) Module theatre_detect: vendor="X.Org Foundation"
[    22.767]     compiled for 1.10.1, module version = 1.0.0
[    22.767]     ABI class: X.Org Video Driver, version 10.0
[    22.767] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    22.767] (II) RADEON(0): Set up overlay video
[    22.767] (II) RADEON(0): Set up textured video
[    22.823] disable primary dac
[    22.823] disable TVDAC
[    22.823] disable TV
[    22.823] disable TVDAC
[    22.823] init memmap
[    22.823] init common
[    22.823] init crtc1
[    22.823] init pll1
[    22.823] freq: 108000000
[    22.823] best_freq: 108000000
[    22.823] best_feedback_div: 16
[    22.823] best_frac_feedback_div: 0
[    22.823] best_ref_div: 2
[    22.823] best_post_div: 2
[    22.823] restore memmap
[    22.823] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    22.823] (II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
[    22.823] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    22.924] restore common
[    22.924] restore crtc1
[    22.924] restore pll1
[    22.974] finished PLL1
[    22.974] set RMX
[    22.974] set TVDAC
[    22.974] enable TVDAC
[    22.974] disable primary dac
[    22.974] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.975] (--) RandR disabled
[    22.975] (II) Initializing built-in extension Generic Event Extension
[    22.975] (II) Initializing built-in extension SHAPE
[    22.975] (II) Initializing built-in extension MIT-SHM
[    22.975] (II) Initializing built-in extension XInputExtension
[    22.975] (II) Initializing built-in extension XTEST
[    22.975] (II) Initializing built-in extension BIG-REQUESTS
[    22.975] (II) Initializing built-in extension SYNC
[    22.975] (II) Initializing built-in extension XKEYBOARD
[    22.975] (II) Initializing built-in extension XC-MISC
[    22.975] (II) Initializing built-in extension SECURITY
[    22.975] (II) Initializing built-in extension XINERAMA
[    22.975] (II) Initializing built-in extension XFIXES
[    22.975] (II) Initializing built-in extension RENDER
[    22.975] (II) Initializing built-in extension RANDR
[    22.975] (II) Initializing built-in extension COMPOSITE
[    22.975] (II) Initializing built-in extension DAMAGE
[    22.975] (II) Initializing built-in extension GESTURE
[    22.988] (II) AIGLX: Screen 0 is not DRI2 capable
[    22.988] (II) AIGLX: Screen 0 is not DRI capable
[    22.988] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    23.486] (II) AIGLX: Loaded and initialized swrast
[    23.486] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    23.486] (II) RADEON(0): Setting screen physical size to 338 x 270
[    23.524] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.535] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.535] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.535] (II) LoadModule: "evdev"
[    23.535] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.536] (II) Module evdev: vendor="X.Org Foundation"
[    23.536]     compiled for 1.10.0.902, module version = 2.6.0
[    23.536]     Module class: X.Org XInput Driver
[    23.536]     ABI class: X.Org XInput driver, version 12.3
[    23.536] (II) Using input driver 'evdev' for 'Power Button'
[    23.536] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.536] (**) Power Button: always reports core events
[    23.536] (**) Power Button: Device: "/dev/input/event1"
[    23.536] (--) Power Button: Found keys
[    23.536] (II) Power Button: Configuring as keyboard
[    23.536] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.536] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.536] (**) Option "xkb_rules" "evdev"
[    23.536] (**) Option "xkb_model" "pc105"
[    23.536] (**) Option "xkb_layout" "fr"
[    23.536] (**) Option "xkb_variant" "oss"
[    23.540] (II) XKB: reuse xkmfile /var/lib/xkb/server-6CCE7350BC740BB33D520367F4A10E64192A358C.xkm
[    23.544] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.544] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.544] (II) Using input driver 'evdev' for 'Power Button'
[    23.544] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.544] (**) Power Button: always reports core events
[    23.544] (**) Power Button: Device: "/dev/input/event0"
[    23.544] (--) Power Button: Found keys
[    23.544] (II) Power Button: Configuring as keyboard
[    23.544] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    23.544] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.544] (**) Option "xkb_rules" "evdev"
[    23.544] (**) Option "xkb_model" "pc105"
[    23.544] (**) Option "xkb_layout" "fr"
[    23.544] (**) Option "xkb_variant" "oss"
[    23.547] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event2)
[    23.547] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    23.547] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    23.547] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.547] (**) HID 04f3:0103: always reports core events
[    23.547] (**) HID 04f3:0103: Device: "/dev/input/event2"
[    23.547] (--) HID 04f3:0103: Found keys
[    23.547] (II) HID 04f3:0103: Configuring as keyboard
[    23.547] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input2/event2"
[    23.547] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[    23.547] (**) Option "xkb_rules" "evdev"
[    23.547] (**) Option "xkb_model" "pc105"
[    23.547] (**) Option "xkb_layout" "fr"
[    23.547] (**) Option "xkb_variant" "oss"
[    23.549] (II) config/udev: Adding input device HID 04f3:0103 (/dev/input/event3)
[    23.549] (**) HID 04f3:0103: Applying InputClass "evdev keyboard catchall"
[    23.549] (II) Using input driver 'evdev' for 'HID 04f3:0103'
[    23.549] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.549] (**) HID 04f3:0103: always reports core events
[    23.549] (**) HID 04f3:0103: Device: "/dev/input/event3"
[    23.549] (--) HID 04f3:0103: Found 1 mouse buttons
[    23.549] (--) HID 04f3:0103: Found scroll wheel(s)
[    23.549] (--) HID 04f3:0103: Found relative axes
[    23.549] (--) HID 04f3:0103: Found absolute axes
[    23.549] (II) evdev-grail: failed to open grail, no gesture support
[    23.549] (--) HID 04f3:0103: Found keys
[    23.549] (II) HID 04f3:0103: Configuring as mouse
[    23.549] (II) HID 04f3:0103: Configuring as keyboard
[    23.549] (II) HID 04f3:0103: Adding scrollwheel support
[    23.549] (**) HID 04f3:0103: YAxisMapping: buttons 4 and 5
[    23.549] (**) HID 04f3:0103: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.549] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.1/input/input3/event3"
[    23.549] (II) XINPUT: Adding extended input device "HID 04f3:0103" (type: KEYBOARD)
[    23.549] (**) Option "xkb_rules" "evdev"
[    23.549] (**) Option "xkb_model" "pc105"
[    23.549] (**) Option "xkb_layout" "fr"
[    23.549] (**) Option "xkb_variant" "oss"
[    23.550] (EE) HID 04f3:0103: failed to initialize for relative axes.
[    23.550] (II) HID 04f3:0103: initialized for absolute axes.
[    23.550] (**) HID 04f3:0103: (accel) keeping acceleration scheme 1
[    23.550] (**) HID 04f3:0103: (accel) acceleration profile 0
[    23.550] (**) HID 04f3:0103: (accel) acceleration factor: 2.000
[    23.550] (**) HID 04f3:0103: (accel) acceleration threshold: 4
[    23.556] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[    23.556] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    23.556] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    23.556] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.556] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    23.556] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
[    23.556] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    23.556] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    23.556] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    23.556] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    23.556] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    23.556] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    23.556] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    23.556] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.556] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    23.556] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    23.557] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    23.557] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    23.557] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    23.557] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    23.557] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    23.557] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    23.557] (II) No input driver/identifier specified (ignoring)
[    25.278] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    25.343] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    25.343] (II) RADEON(0): Using EDID range info for horizontal sync
[    25.343] (II) RADEON(0): Using EDID range info for vertical refresh
[    25.343] (II) RADEON(0): Printing DDC gathered Modelines:
[    25.343] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.343] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    25.343] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.343] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.343] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.343] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    25.343] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.343] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    25.343] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    25.343] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.343] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.343] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.343] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.343] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.343] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.343] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    25.343] (II) RADEON(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[    25.343] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    25.343] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    25.343] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    25.343] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    25.344] (II) RADEON(0): Year: 2006  Week: 33
[    25.344] (II) RADEON(0): EDID Version: 1.3
[    25.344] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    25.344] (II) RADEON(0): Sync:  Separate  Composite
[    25.344] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    25.344] (II) RADEON(0): Gamma: 2.20
[    25.344] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    25.344] (II) RADEON(0): First detailed timing is preferred mode
[    25.344] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    25.344] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    25.344] (II) RADEON(0): Supported established timings:
[    25.344] (II) RADEON(0): 720x400@70Hz
[    25.344] (II) RADEON(0): 640x480@60Hz
[    25.344] (II) RADEON(0): 640x480@67Hz
[    25.344] (II) RADEON(0): 640x480@72Hz
[    25.344] (II) RADEON(0): 640x480@75Hz
[    25.344] (II) RADEON(0): 800x600@60Hz
[    25.344] (II) RADEON(0): 800x600@72Hz
[    25.344] (II) RADEON(0): 800x600@75Hz
[    25.344] (II) RADEON(0): 832x624@75Hz
[    25.344] (II) RADEON(0): 1024x768@60Hz
[    25.344] (II) RADEON(0): 1024x768@70Hz
[    25.344] (II) RADEON(0): 1024x768@75Hz
[    25.344] (II) RADEON(0): 1280x1024@75Hz
[    25.344] (II) RADEON(0): 1152x864@75Hz
[    25.344] (II) RADEON(0): Manufacturer's mask: 0
[    25.344] (II) RADEON(0): Supported standard timings:
[    25.344] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    25.344] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    25.344] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    25.344] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    25.344] (II) RADEON(0): Supported detailed timing:
[    25.344] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    25.344] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    25.344] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    25.344] (II) RADEON(0): Supported detailed timing:
[    25.344] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    25.344] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    25.344] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    25.344] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    25.344] (II) RADEON(0): Monitor name: BenQ FP91G+
[    25.344] (II) RADEON(0): EDID (in hex):
[    25.344] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    25.344] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    25.344] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    25.344] (II) RADEON(0):     010101010101302a009851002a403070
[    25.344] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    25.344] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    25.344] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    25.344] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    25.344] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    25.344] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    25.351] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    25.411] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    25.411] (II) RADEON(0): Using hsync ranges from config file
[    25.411] (II) RADEON(0): Using vrefresh ranges from config file
[    25.411] (II) RADEON(0): Printing DDC gathered Modelines:
[    25.411] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.411] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    25.411] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.411] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.411] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.411] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    25.411] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.411] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    25.411] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    25.411] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.411] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.411] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.411] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.411] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.411] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.411] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    25.411] (II) RADEON(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[    25.411] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    25.411] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    25.411] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    25.411] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    25.411] (II) RADEON(0): Year: 2006  Week: 33
[    25.411] (II) RADEON(0): EDID Version: 1.3
[    25.411] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    25.411] (II) RADEON(0): Sync:  Separate  Composite
[    25.411] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    25.411] (II) RADEON(0): Gamma: 2.20
[    25.411] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    25.411] (II) RADEON(0): First detailed timing is preferred mode
[    25.411] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    25.412] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    25.412] (II) RADEON(0): Supported established timings:
[    25.412] (II) RADEON(0): 720x400@70Hz
[    25.412] (II) RADEON(0): 640x480@60Hz
[    25.412] (II) RADEON(0): 640x480@67Hz
[    25.412] (II) RADEON(0): 640x480@72Hz
[    25.412] (II) RADEON(0): 640x480@75Hz
[    25.412] (II) RADEON(0): 800x600@60Hz
[    25.412] (II) RADEON(0): 800x600@72Hz
[    25.412] (II) RADEON(0): 800x600@75Hz
[    25.412] (II) RADEON(0): 832x624@75Hz
[    25.412] (II) RADEON(0): 1024x768@60Hz
[    25.412] (II) RADEON(0): 1024x768@70Hz
[    25.412] (II) RADEON(0): 1024x768@75Hz
[    25.412] (II) RADEON(0): 1280x1024@75Hz
[    25.412] (II) RADEON(0): 1152x864@75Hz
[    25.412] (II) RADEON(0): Manufacturer's mask: 0
[    25.412] (II) RADEON(0): Supported standard timings:
[    25.412] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    25.412] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    25.412] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    25.412] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    25.412] (II) RADEON(0): Supported detailed timing:
[    25.412] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    25.412] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    25.412] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    25.412] (II) RADEON(0): Supported detailed timing:
[    25.412] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    25.412] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    25.412] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    25.412] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    25.412] (II) RADEON(0): Monitor name: BenQ FP91G+
[    25.412] (II) RADEON(0): EDID (in hex):
[    25.412] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    25.412] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    25.412] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    25.412] (II) RADEON(0):     010101010101302a009851002a403070
[    25.412] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    25.412] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    25.412] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    25.412] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    25.412] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    25.412] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    27.031] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    27.151] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    27.151] (II) RADEON(0): Using hsync ranges from config file
[    27.151] (II) RADEON(0): Using vrefresh ranges from config file
[    27.151] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.151] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.151] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    27.151] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.151] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.151] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    27.151] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    27.151] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.151] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.151] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.151] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.151] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    27.151] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.151] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.151] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.156] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    27.156] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.156] (II) RADEON(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[    27.156] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    27.156] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    27.156] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    27.156] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    27.156] (II) RADEON(0): Year: 2006  Week: 33
[    27.156] (II) RADEON(0): EDID Version: 1.3
[    27.156] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    27.156] (II) RADEON(0): Sync:  Separate  Composite
[    27.156] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    27.156] (II) RADEON(0): Gamma: 2.20
[    27.156] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    27.156] (II) RADEON(0): First detailed timing is preferred mode
[    27.156] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    27.156] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    27.156] (II) RADEON(0): Supported established timings:
[    27.156] (II) RADEON(0): 720x400@70Hz
[    27.156] (II) RADEON(0): 640x480@60Hz
[    27.156] (II) RADEON(0): 640x480@67Hz
[    27.156] (II) RADEON(0): 640x480@72Hz
[    27.156] (II) RADEON(0): 640x480@75Hz
[    27.156] (II) RADEON(0): 800x600@60Hz
[    27.156] (II) RADEON(0): 800x600@72Hz
[    27.156] (II) RADEON(0): 800x600@75Hz
[    27.156] (II) RADEON(0): 832x624@75Hz
[    27.156] (II) RADEON(0): 1024x768@60Hz
[    27.156] (II) RADEON(0): 1024x768@70Hz
[    27.156] (II) RADEON(0): 1024x768@75Hz
[    27.156] (II) RADEON(0): 1280x1024@75Hz
[    27.156] (II) RADEON(0): 1152x864@75Hz
[    27.156] (II) RADEON(0): Manufacturer's mask: 0
[    27.156] (II) RADEON(0): Supported standard timings:
[    27.156] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    27.156] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    27.156] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.156] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    27.156] (II) RADEON(0): Supported detailed timing:
[    27.156] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    27.156] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    27.156] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    27.156] (II) RADEON(0): Supported detailed timing:
[    27.156] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    27.156] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    27.156] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    27.156] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    27.156] (II) RADEON(0): Monitor name: BenQ FP91G+
[    27.156] (II) RADEON(0): EDID (in hex):
[    27.156] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    27.156] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    27.156] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    27.156] (II) RADEON(0):     010101010101302a009851002a403070
[    27.156] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    27.157] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    27.157] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    27.157] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    27.157] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    27.157] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    27.172] disable TVDAC
[    27.172] init memmap
[    27.172] init common
[    27.172] init crtc1
[    27.172] init pll1
[    27.172] freq: 108000000
[    27.173] best_freq: 108000000
[    27.173] best_feedback_div: 16
[    27.173] best_frac_feedback_div: 0
[    27.173] best_ref_div: 2
[    27.173] best_post_div: 2
[    27.173] restore memmap
[    27.173] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    27.173] (II) RADEON(0):   MC_FB_LOCATION   : 0xcfffc000 0xcfffc000
[    27.173] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    27.192] restore common
[    27.192] restore crtc1
[    27.192] restore pll1
[    27.212] finished PLL1
[    27.212] set RMX
[    27.212] set TVDAC
[    27.213] enable TVDAC
[    27.213] disable primary dac
[    27.231] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    27.385] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    27.385] (II) RADEON(0): Using hsync ranges from config file
[    27.385] (II) RADEON(0): Using vrefresh ranges from config file
[    27.385] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.385] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.385] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    27.385] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.385] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.385] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    27.385] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    27.385] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.385] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.385] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.385] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.385] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    27.385] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.385] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.385] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.385] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    27.385] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.385] (II) RADEON(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[    27.385] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    27.385] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    27.385] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    27.385] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    27.385] (II) RADEON(0): Year: 2006  Week: 33
[    27.385] (II) RADEON(0): EDID Version: 1.3
[    27.385] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    27.386] (II) RADEON(0): Sync:  Separate  Composite
[    27.386] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    27.386] (II) RADEON(0): Gamma: 2.20
[    27.386] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    27.386] (II) RADEON(0): First detailed timing is preferred mode
[    27.386] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    27.386] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    27.386] (II) RADEON(0): Supported established timings:
[    27.386] (II) RADEON(0): 720x400@70Hz
[    27.386] (II) RADEON(0): 640x480@60Hz
[    27.386] (II) RADEON(0): 640x480@67Hz
[    27.386] (II) RADEON(0): 640x480@72Hz
[    27.386] (II) RADEON(0): 640x480@75Hz
[    27.386] (II) RADEON(0): 800x600@60Hz
[    27.386] (II) RADEON(0): 800x600@72Hz
[    27.386] (II) RADEON(0): 800x600@75Hz
[    27.386] (II) RADEON(0): 832x624@75Hz
[    27.386] (II) RADEON(0): 1024x768@60Hz
[    27.386] (II) RADEON(0): 1024x768@70Hz
[    27.386] (II) RADEON(0): 1024x768@75Hz
[    27.386] (II) RADEON(0): 1280x1024@75Hz
[    27.386] (II) RADEON(0): 1152x864@75Hz
[    27.386] (II) RADEON(0): Manufacturer's mask: 0
[    27.386] (II) RADEON(0): Supported standard timings:
[    27.386] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    27.386] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    27.386] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.386] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    27.386] (II) RADEON(0): Supported detailed timing:
[    27.386] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    27.386] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    27.386] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    27.386] (II) RADEON(0): Supported detailed timing:
[    27.386] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    27.386] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    27.386] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    27.386] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    27.386] (II) RADEON(0): Monitor name: BenQ FP91G+
[    27.386] (II) RADEON(0): EDID (in hex):
[    27.386] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    27.386] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    27.386] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    27.386] (II) RADEON(0):     010101010101302a009851002a403070
[    27.386] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    27.386] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    27.386] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    27.386] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    27.386] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    27.386] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    27.407] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    27.601] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    27.601] (II) RADEON(0): Using hsync ranges from config file
[    27.601] (II) RADEON(0): Using vrefresh ranges from config file
[    27.601] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.601] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.601] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    27.601] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.601] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.601] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    27.601] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    27.602] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.602] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.602] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.602] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.602] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    27.602] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.602] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.602] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.602] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    27.602] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.602] (II) RADEON(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[    27.602] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    27.602] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    27.602] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    27.602] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    27.602] (II) RADEON(0): Year: 2006  Week: 33
[    27.602] (II) RADEON(0): EDID Version: 1.3
[    27.602] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    27.602] (II) RADEON(0): Sync:  Separate  Composite
[    27.602] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    27.602] (II) RADEON(0): Gamma: 2.20
[    27.602] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    27.602] (II) RADEON(0): First detailed timing is preferred mode
[    27.602] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    27.602] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    27.602] (II) RADEON(0): Supported established timings:
[    27.602] (II) RADEON(0): 720x400@70Hz
[    27.602] (II) RADEON(0): 640x480@60Hz
[    27.602] (II) RADEON(0): 640x480@67Hz
[    27.602] (II) RADEON(0): 640x480@72Hz
[    27.602] (II) RADEON(0): 640x480@75Hz
[    27.602] (II) RADEON(0): 800x600@60Hz
[    27.602] (II) RADEON(0): 800x600@72Hz
[    27.602] (II) RADEON(0): 800x600@75Hz
[    27.602] (II) RADEON(0): 832x624@75Hz
[    27.602] (II) RADEON(0): 1024x768@60Hz
[    27.602] (II) RADEON(0): 1024x768@70Hz
[    27.602] (II) RADEON(0): 1024x768@75Hz
[    27.602] (II) RADEON(0): 1280x1024@75Hz
[    27.602] (II) RADEON(0): 1152x864@75Hz
[    27.602] (II) RADEON(0): Manufacturer's mask: 0
[    27.602] (II) RADEON(0): Supported standard timings:
[    27.602] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    27.602] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    27.602] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.602] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    27.602] (II) RADEON(0): Supported detailed timing:
[    27.602] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    27.602] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    27.602] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    27.602] (II) RADEON(0): Supported detailed timing:
[    27.602] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    27.602] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    27.602] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    27.602] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    27.602] (II) RADEON(0): Monitor name: BenQ FP91G+
[    27.602] (II) RADEON(0): EDID (in hex):
[    27.602] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    27.602] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    27.603] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    27.603] (II) RADEON(0):     010101010101302a009851002a403070
[    27.603] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    27.603] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    27.603] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    27.603] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    27.603] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    27.603] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    27.643] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    27.831] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    27.831] (II) RADEON(0): Using hsync ranges from config file
[    27.831] (II) RADEON(0): Using vrefresh ranges from config file
[    27.831] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.831] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.831] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    27.831] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.831] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.831] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    27.831] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    27.831] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.831] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.831] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.831] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.831] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    27.831] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.831] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.831] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.831] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    27.831] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.831] (II) RADEON(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[    27.831] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    27.831] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    27.831] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    27.831] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    27.831] (II) RADEON(0): Year: 2006  Week: 33
[    27.831] (II) RADEON(0): EDID Version: 1.3
[    27.831] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    27.836] (II) RADEON(0): Sync:  Separate  Composite
[    27.836] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    27.836] (II) RADEON(0): Gamma: 2.20
[    27.836] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    27.836] (II) RADEON(0): First detailed timing is preferred mode
[    27.836] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    27.836] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    27.836] (II) RADEON(0): Supported established timings:
[    27.836] (II) RADEON(0): 720x400@70Hz
[    27.836] (II) RADEON(0): 640x480@60Hz
[    27.836] (II) RADEON(0): 640x480@67Hz
[    27.836] (II) RADEON(0): 640x480@72Hz
[    27.836] (II) RADEON(0): 640x480@75Hz
[    27.836] (II) RADEON(0): 800x600@60Hz
[    27.836] (II) RADEON(0): 800x600@72Hz
[    27.836] (II) RADEON(0): 800x600@75Hz
[    27.836] (II) RADEON(0): 832x624@75Hz
[    27.836] (II) RADEON(0): 1024x768@60Hz
[    27.836] (II) RADEON(0): 1024x768@70Hz
[    27.836] (II) RADEON(0): 1024x768@75Hz
[    27.836] (II) RADEON(0): 1280x1024@75Hz
[    27.836] (II) RADEON(0): 1152x864@75Hz
[    27.836] (II) RADEON(0): Manufacturer's mask: 0
[    27.836] (II) RADEON(0): Supported standard timings:
[    27.836] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    27.836] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    27.836] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    27.836] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    27.836] (II) RADEON(0): Supported detailed timing:
[    27.836] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    27.836] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    27.836] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    27.836] (II) RADEON(0): Supported detailed timing:
[    27.836] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    27.836] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    27.836] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    27.836] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    27.836] (II) RADEON(0): Monitor name: BenQ FP91G+
[    27.836] (II) RADEON(0): EDID (in hex):
[    27.836] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    27.836] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    27.836] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    27.836] (II) RADEON(0):     010101010101302a009851002a403070
[    27.836] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    27.836] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    27.836] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    27.836] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    27.836] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    27.836] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    27.856] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    28.065] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    28.116] (II) RADEON(0): Using hsync ranges from config file
[    28.116] (II) RADEON(0): Using vrefresh ranges from config file
[    28.116] (II) RADEON(0): Printing DDC gathered Modelines:
[    28.117] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    28.117] (II) RADEON(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
[    28.117] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    28.117] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    28.117] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    28.117] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    28.117] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    28.117] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    28.117] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    28.117] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    28.117] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    28.117] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    28.117] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    28.117] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    28.117] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    28.117] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    28.117] (II) RADEON(0): Modeline "1280x1024"x76.0  141.82  1280 1376 1512 1744  1024 1025 1028 1070 -hsync +vsync (81.3 kHz)
[    28.117] (II) RADEON(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz)
[    28.117] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    28.117] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    28.117] (II) RADEON(0): Manufacturer: BNQ  Model: 76a5  Serial#: 7275
[    28.117] (II) RADEON(0): Year: 2006  Week: 33
[    28.117] (II) RADEON(0): EDID Version: 1.3
[    28.117] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    28.117] (II) RADEON(0): Sync:  Separate  Composite
[    28.117] (II) RADEON(0): Max Image Size [cm]: horiz.: 38  vert.: 30
[    28.117] (II) RADEON(0): Gamma: 2.20
[    28.117] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    28.117] (II) RADEON(0): First detailed timing is preferred mode
[    28.117] (II) RADEON(0): redX: 0.634 redY: 0.354   greenX: 0.300 greenY: 0.614
[    28.117] (II) RADEON(0): blueX: 0.138 blueY: 0.076   whiteX: 0.310 whiteY: 0.330
[    28.117] (II) RADEON(0): Supported established timings:
[    28.117] (II) RADEON(0): 720x400@70Hz
[    28.117] (II) RADEON(0): 640x480@60Hz
[    28.117] (II) RADEON(0): 640x480@67Hz
[    28.117] (II) RADEON(0): 640x480@72Hz
[    28.117] (II) RADEON(0): 640x480@75Hz
[    28.117] (II) RADEON(0): 800x600@60Hz
[    28.117] (II) RADEON(0): 800x600@72Hz
[    28.117] (II) RADEON(0): 800x600@75Hz
[    28.117] (II) RADEON(0): 832x624@75Hz
[    28.117] (II) RADEON(0): 1024x768@60Hz
[    28.117] (II) RADEON(0): 1024x768@70Hz
[    28.117] (II) RADEON(0): 1024x768@75Hz
[    28.117] (II) RADEON(0): 1280x1024@75Hz
[    28.117] (II) RADEON(0): 1152x864@75Hz
[    28.117] (II) RADEON(0): Manufacturer's mask: 0
[    28.117] (II) RADEON(0): Supported standard timings:
[    28.117] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    28.117] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
[    28.117] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    28.117] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    28.117] (II) RADEON(0): Supported detailed timing:
[    28.117] (II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
[    28.117] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    28.117] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    28.117] (II) RADEON(0): Supported detailed timing:
[    28.118] (II) RADEON(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
[    28.118] (II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
[    28.118] (II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
[    28.118] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    28.118] (II) RADEON(0): Monitor name: BenQ FP91G+
[    28.118] (II) RADEON(0): EDID (in hex):
[    28.118] (II) RADEON(0):     00ffffffffffff0009d1a5766b1c0000
[    28.118] (II) RADEON(0):     211001036c261e78ea6d66a25a4c9d23
[    28.118] (II) RADEON(0):     134f54bdef80714f81908180818c0101
[    28.118] (II) RADEON(0):     010101010101302a009851002a403070
[    28.118] (II) RADEON(0):     1300782d1100001ed50980a0205e6310
[    28.118] (II) RADEON(0):     10605208782d1100001a000000fd0038
[    28.118] (II) RADEON(0):     4c1f530e000a202020202020000000fc
[    28.118] (II) RADEON(0):     0042656e512046503931472b0a2000f9
[    28.118] (II) RADEON(0): EDID vendor "BNQ", prod id 30373
[    28.118] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0


```


Thank you for your help ! : )

---

### Post by Toz on 2011-07-22
From your Xorg.0.log file:
> [    22.341] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
.....is probably the reason for the slowness.

Googling a bit, I found:

[http://www.x.org/wiki/radeonBuildHowTo#radeon-KMSwithAGPgfxcards]("http://www.x.org/wiki/radeonBuildHowTo#radeon-KMSwithAGPgfxcards") - which suggests trying to boot with the kernel paramater **radeon.agpmode=-1**

[https://wiki.ubuntu.com/X/KernelModeSetting]("https://wiki.ubuntu.com/X/KernelModeSetting") - search for "RADEONDRIGetVersion failed". It suggests that the error is the result of a race condition and provides a potential solution.

Otherwise, it might be worth opening up a bug report at:[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati")

---

### Post by jawaka. on 2011-07-23
So I've put radeon.adgpmode=-1 and it's better !
But it's largely less fluent than under Windows unfortunately.

Then I've put "modprobe radeon" in gdm.conf, but nothing has changed : I also get
```
[    22.341] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
```

I've found this link : [http://readthefuckingmanual.net/error/814/](http://readthefuckingmanual.net/error/814/)
It is proposed to replace the "radeon" driver by the "ati" driver.
But I don't know where I can do that.

---

### Post by Toz on 2011-07-23
If the proprietary ati driver was available for your system, it would show up in the Additional Drivers section. Unfortunately, the news doesn't look good for this card when it comes to using the ATI catalyst drivers with Natty. See: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English") quoted:
> The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series


AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  [COLOR="Red"]The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.[/COLOR]

and

[http://ubuntuforums.org/showthread.php?t=1370758]("http://ubuntuforums.org/showthread.php?t=1370758").

---

### Post by Toz on 2011-07-23
You might want to have a look at xorg-edgers. Perhaps the radeon driver support is better for that card with those newer drivers. Link: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa").

---

### Post by jawaka. on 2011-07-24
Ok, so I think I will stop to try to fix it.
But, isn't it possible to change the graphic card ? 

Thank you for your help Toz ! :)

---

