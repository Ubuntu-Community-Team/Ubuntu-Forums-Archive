---
title: "HD Radeon 6450 graphics problems"
date: 2012-08-03
forum: General Help
---

### Post by rossmounce on 2012-08-03
I changed my motherboard (to Asus M5A78L/USB3) recently and got a new graphics card (HD Radeon 6450) and RAM (2x4GB).

When I boot into Ubuntu 11.10 from a USB stick livesystem it looks rather odd (see below):

[IMG]http://i.imgur.com/2VLV8.png[/IMG]

When I try to install from the USB to the hard disk, the subsequent installation won't boot successfully upon restart (but from USB livesystem it works reasonably well aside from the odd graphics)

I think this is a graphics problem, it doesn't seem to detect the resolution properly, nor perhaps the right driver(?)  Any ideas I could try?

```
$ lspci -vvv -s 01:00.0
01:00.0 VGA compatible controller: ATI Technologies Inc NI Caicos [AMD RADEON HD 6450] (prog-if 00 [VGA controller])
    Subsystem: Hightech Information System Ltd. Device 2311
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 48
    Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at feac0000 (64-bit, non-prefetchable) [size=128K]
    Region 4: I/O ports at d000 [size=256]
    Expansion ROM at feaa0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: fglrx_updates, radeon


```how can I go about fixing / debugging this?

some logs:

kern.log (of a liveUSB session):

```
Aug  3 10:33:49 ubuntu kernel: [  194.456090] radeon 0000:01:00.0: GPU lockup CP stall for more than 10000msec
Aug  3 10:33:49 ubuntu kernel: [  194.456100] ------------[ cut here ]------------
Aug  3 10:33:49 ubuntu kernel: [  194.456163] WARNING: at /build/buildd/linux-3.0.0/drivers/gpu/drm/radeon/radeon_fence.c:267 radeon_fence_w$
Aug  3 10:33:49 ubuntu kernel: [  194.456170] Hardware name: System Product Name
Aug  3 10:33:49 ubuntu kernel: [  194.456175] GPU lockup (waiting for 0x0000187E last fence id 0x0000187D)
Aug  3 10:33:49 ubuntu kernel: [  194.456180] Modules linked in: dm_crypt lp bnep rfcomm gspca_zc3xx gspca_main bluetooth videodev v4l2_comp$
Aug  3 10:33:49 ubuntu kernel: [  194.456279] Pid: 2159, comm: Xorg Not tainted 3.0.0-12-generic #20-Ubuntu
Aug  3 10:33:49 ubuntu kernel: [  194.456284] Call Trace:
Aug  3 10:33:49 ubuntu kernel: [  194.456300]  [<ffffffff8105e83f>] warn_slowpath_common+0x7f/0xc0
Aug  3 10:33:49 ubuntu kernel: [  194.456310]  [<ffffffff8105e936>] warn_slowpath_fmt+0x46/0x50
Aug  3 10:33:49 ubuntu kernel: [  194.456353]  [<ffffffffa00fa26b>] radeon_fence_wait+0x3fb/0x430 [radeon]
Aug  3 10:33:49 ubuntu kernel: [  194.456364]  [<ffffffff81153ead>] ? kmem_cache_alloc_trace+0x11d/0x140
Aug  3 10:33:49 ubuntu kernel: [  194.456373]  [<ffffffff81081cb0>] ? add_wait_queue+0x60/0x60
Aug  3 10:33:49 ubuntu kernel: [  194.456420]  [<ffffffffa0115510>] radeon_ib_get+0x110/0x1a0 [radeon]
Aug  3 10:33:49 ubuntu kernel: [  194.456466]  [<ffffffffa0116eb8>] radeon_cs_ioctl+0x98/0x1e0 [radeon]
Aug  3 10:33:49 ubuntu kernel: [  194.456495]  [<ffffffffa000b574>] drm_ioctl+0x3e4/0x4c0 [drm]
Aug  3 10:33:49 ubuntu kernel: [  194.456542]  [<ffffffffa0116e20>] ? radeon_cs_finish_pages+0xe0/0xe0 [radeon]
Aug  3 10:33:49 ubuntu kernel: [  194.456552]  [<ffffffff8117939a>] do_vfs_ioctl+0x8a/0x340
Aug  3 10:33:49 ubuntu kernel: [  194.456560]  [<ffffffff811679ed>] ? vfs_read+0x10d/0x180
Aug  3 10:33:49 ubuntu kernel: [  194.456567]  [<ffffffff811796e1>] sys_ioctl+0x91/0xa0
Aug  3 10:33:49 ubuntu kernel: [  194.456575]  [<ffffffff815eb22e>] ? do_device_not_available+0xe/0x10
Aug  3 10:33:49 ubuntu kernel: [  194.456585]  [<ffffffff815f22c2>] system_call_fastpath+0x16/0x1b
Aug  3 10:33:49 ubuntu kernel: [  194.456591] ---[ end trace ced0e75b0e71a602 ]---
Aug  3 10:33:49 ubuntu kernel: [  194.457798] radeon 0000:01:00.0: GPU softreset
Aug  3 10:33:49 ubuntu kernel: [  194.457804] radeon 0000:01:00.0:   GRBM_STATUS=0xA0003828
Aug  3 10:33:49 ubuntu kernel: [  194.457810] radeon 0000:01:00.0:   GRBM_STATUS_SE0=0x00000007
Aug  3 10:33:49 ubuntu kernel: [  194.457816] radeon 0000:01:00.0:   GRBM_STATUS_SE1=0x00000007
Aug  3 10:33:49 ubuntu kernel: [  194.457822] radeon 0000:01:00.0:   SRBM_STATUS=0x200000C0
Aug  3 10:33:49 ubuntu kernel: [  194.457836] radeon 0000:01:00.0:   GRBM_SOFT_RESET=0x00007F6B
Aug  3 10:33:49 ubuntu kernel: [  194.457943] radeon 0000:01:00.0:   GRBM_STATUS=0x00003828
Aug  3 10:33:49 ubuntu kernel: [  194.457948] radeon 0000:01:00.0:   GRBM_STATUS_SE0=0x00000007
Aug  3 10:33:49 ubuntu kernel: [  194.457954] radeon 0000:01:00.0:   GRBM_STATUS_SE1=0x00000007
Aug  3 10:33:49 ubuntu kernel: [  194.457959] radeon 0000:01:00.0:   SRBM_STATUS=0x200000C0
Aug  3 10:33:49 ubuntu kernel: [  194.458956] radeon 0000:01:00.0: GPU reset succeed
Aug  3 10:33:49 ubuntu kernel: [  194.483684] radeon 0000:01:00.0: WB enabled

```
jockey.log:
```

ValueError: package linux-firmware-nonfree does not exist
2012-08-03 10:32:00,725 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-08-03 10:32:00,734 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2012-08-03 10:32:00,740 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2012-08-03 10:32:00,740 DEBUG: Disabling fglrx driver on live system
2012-08-03 10:32:00,740 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) not available
2012-08-03 10:32:00,744 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-08-03 10:32:00,750 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-08-03 10:32:00,750 DEBUG: Disabling fglrx driver on live system
2012-08-03 10:32:00,750 DEBUG: ATI/AMD proprietary FGLRX graphics driver not available
2012-08-03 10:32:00,750 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-08-03 10:32:00,755 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
```
Xorg.0.log:

```
[    18.336] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    18.336] X Protocol Version 11, Revision 0
[    18.336] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    18.336] Current Operating System: Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    18.336] Kernel command line: BOOT_IMAGE=(loop)/casper/vmlinuz root=UUID=EF91-7550 debian-installer/language=en keyboard-configuration/layoutcode=gb iso-scan/filename=/ubuntu-11.10-desktop-amd64.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash --
[    18.336] Build Date: 29 September 2011  02:45:13AM
[    18.336] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    18.336] Current version of pixman: 0.22.2
[    18.336]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    18.336] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.337] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  3 10:30:53 2012
[    18.343] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.349] (==) No Layout section.  Using the first Screen section.
[    18.349] (==) No screen section available. Using defaults.
[    18.349] (**) |-->Screen "Default Screen Section" (0)
[    18.349] (**) |   |-->Monitor "<default monitor>"
[    18.349] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    18.349] (==) Automatically adding devices
[    18.349] (==) Automatically enabling devices
[    18.350] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.350]     Entry deleted from font path.
[    18.350] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.350]     Entry deleted from font path.
[    18.350] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.350]     Entry deleted from font path.
[    18.353] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.353]     Entry deleted from font path.
[    18.353] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.353]     Entry deleted from font path.
[    18.353] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    18.353] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.353] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.353] (II) Loader magic: 0x7e0220
[    18.353] (II) Module ABI versions:
[    18.353]     X.Org ANSI C Emulation: 0.4
[    18.353]     X.Org Video Driver: 10.0
[    18.353]     X.Org XInput driver : 12.3
[    18.353]     X.Org Server Extension : 5.0
[    18.354] (--) PCI:*(0:1:0:0) 1002:6779:1787:2311 rev 0, Mem @ 0xd0000000/268435456, 0xfeac0000/131072, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    18.356] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.356] (II) LoadModule: "extmod"
[    18.370] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.377] (II) Module extmod: vendor="X.Org Foundation"
[    18.377]     compiled for 1.10.4, module version = 1.0.0
[    18.377]     Module class: X.Org Server Extension
[    18.377]     ABI class: X.Org Server Extension, version 5.0
[    18.377] (II) Loading extension MIT-SCREEN-SAVER
[    18.377] (II) Loading extension XFree86-VidModeExtension
[    18.377] (II) Loading extension XFree86-DGA
[    18.377] (II) Loading extension DPMS
[    18.377] (II) Loading extension XVideo
[    18.377] (II) Loading extension XVideo-MotionCompensation
[    18.377] (II) Loading extension X-Resource
[    18.377] (II) LoadModule: "dbe"
[    18.377] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.382] (II) Module dbe: vendor="X.Org Foundation"
[    18.382]     compiled for 1.10.4, module version = 1.0.0
[    18.382]     Module class: X.Org Server Extension
[    18.382]     ABI class: X.Org Server Extension, version 5.0
[    18.382] (II) Loading extension DOUBLE-BUFFER
[    18.382] (II) LoadModule: "glx"
[    18.383] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.396] (II) Module glx: vendor="X.Org Foundation"
[    18.396]     compiled for 1.10.4, module version = 1.0.0
[    18.396]     ABI class: X.Org Server Extension, version 5.0
[    18.397] (==) AIGLX enabled
[    18.397] (II) Loading extension GLX
[    18.397] (II) LoadModule: "record"
[    18.398] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.405] (II) Module record: vendor="X.Org Foundation"
[    18.405]     compiled for 1.10.4, module version = 1.13.0
[    18.405]     Module class: X.Org Server Extension
[    18.405]     ABI class: X.Org Server Extension, version 5.0
[    18.406] (II) Loading extension RECORD
[    18.406] (II) LoadModule: "dri"
[    18.406] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.410] (II) Module dri: vendor="X.Org Foundation"
[    18.410]     compiled for 1.10.4, module version = 1.0.0
[    18.410]     ABI class: X.Org Server Extension, version 5.0
[    18.410] (II) Loading extension XFree86-DRI
[    18.410] (II) LoadModule: "dri2"
[    18.410] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.411] (II) Module dri2: vendor="X.Org Foundation"
[    18.411]     compiled for 1.10.4, module version = 1.2.0
[    18.411]     ABI class: X.Org Server Extension, version 5.0
[    18.411] (II) Loading extension DRI2
[    18.411] (==) Matched fglrx as autoconfigured driver 0
[    18.411] (==) Matched ati as autoconfigured driver 1
[    18.411] (==) Matched vesa as autoconfigured driver 2
[    18.411] (==) Matched fbdev as autoconfigured driver 3
[    18.411] (==) Assigned the driver to the xf86ConfigLayout
[    18.411] (II) LoadModule: "fglrx"
[    18.412] (WW) Warning, couldn't open module fglrx
[    18.412] (II) UnloadModule: "fglrx"
[    18.412] (II) Unloading fglrx
[    18.412] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    18.412] (II) LoadModule: "ati"
[    18.412] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.418] (II) Module ati: vendor="X.Org Foundation"
[    18.418]     compiled for 1.10.2.902, module version = 6.14.99
[    18.418]     Module class: X.Org Video Driver
[    18.418]     ABI class: X.Org Video Driver, version 10.0
[    18.418] (II) LoadModule: "radeon"
[    18.418] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.461] (II) Module radeon: vendor="X.Org Foundation"
[    18.461]     compiled for 1.10.2.902, module version = 6.14.99
[    18.461]     Module class: X.Org Video Driver
[    18.461]     ABI class: X.Org Video Driver, version 10.0
[    18.463] (II) LoadModule: "vesa"
[    18.464] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.464] (II) Module vesa: vendor="X.Org Foundation"
[    18.464]     compiled for 1.10.2, module version = 2.3.0
[    18.464]     Module class: X.Org Video Driver
[    18.464]     ABI class: X.Org Video Driver, version 10.0
[    18.465] (II) LoadModule: "fbdev"
[    18.465] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.465] (II) Module fbdev: vendor="X.Org Foundation"
[    18.465]     compiled for 1.10.0, module version = 0.4.2
[    18.465]     ABI class: X.Org Video Driver, version 10.0
[    18.465] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
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
    ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS
[    18.466] (II) VESA: driver for VESA chipsets: vesa
[    18.466] (II) FBDEV: driver for framebuffer: fbdev
[    18.466] (++) using VT number 7

[    18.466] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    18.466] (II) [KMS] Kernel modesetting enabled.
[    18.466] (WW) Falling back to old probe method for vesa
[    18.466] (WW) Falling back to old probe method for fbdev
[    18.466] (II) Loading sub module "fbdevhw"
[    18.466] (II) LoadModule: "fbdevhw"
[    18.467] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.467] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.467]     compiled for 1.10.4, module version = 0.0.2
[    18.467]     ABI class: X.Org Video Driver, version 10.0
[    18.468] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    18.468] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    18.468] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.468] (==) RADEON(0): Default visual is TrueColor
[    18.468] (==) RADEON(0): RGB weight 888
[    18.468] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    18.468] (--) RADEON(0): Chipset: "CAICOS" (ChipID = 0x6779)
[    18.468] (II) RADEON(0): PCIE card detected
[    18.468] drmOpenDevice: node name is /dev/dri/card0
[    18.468] drmOpenDevice: open result is 12, (OK)
[    18.468] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    18.468] drmOpenDevice: node name is /dev/dri/card0
[    18.468] drmOpenDevice: open result is 12, (OK)
[    18.468] drmOpenByBusid: drmOpenMinor returns 12
[    18.468] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    18.468] (II) Loading sub module "exa"
[    18.468] (II) LoadModule: "exa"
[    18.468] (II) Loading /usr/lib/xorg/modules/libexa.so
[    18.468] (II) Module exa: vendor="X.Org Foundation"
[    18.468]     compiled for 1.10.4, module version = 2.5.0
[    18.468]     ABI class: X.Org Video Driver, version 10.0
[    18.468] (II) RADEON(0): KMS Color Tiling: enabled
[    18.468] (II) RADEON(0): KMS Pageflipping: enabled
[    18.468] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    18.476] (II) RADEON(0): Output HDMI-0 has no monitor section
[    18.483] (II) RADEON(0): Output DVI-0 has no monitor section
[    18.573] (II) RADEON(0): Output VGA-0 has no monitor section
[    18.577] (II) RADEON(0): EDID for output HDMI-0
[    18.584] (II) RADEON(0): EDID for output DVI-0
[    18.642] (II) RADEON(0): EDID for output VGA-0
[    18.642] (II) RADEON(0): Manufacturer: CVT  Model: 1  Serial#: 1
[    18.642] (II) RADEON(0): Year: 2006  Week: 29
[    18.642] (II) RADEON(0): EDID Version: 1.3
[    18.642] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    18.642] (II) RADEON(0): Sync:  Separate
[    18.642] (II) RADEON(0): Indeterminate output size
[    18.642] (II) RADEON(0): Gamma: 1.00
[    18.642] (II) RADEON(0): DPMS capabilities: StandBy; RGB/Color Display
[    18.642] (II) RADEON(0): First detailed timing is preferred mode
[    18.642] (II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.285 greenY: 0.605
[    18.642] (II) RADEON(0): blueX: 0.148 blueY: 0.063   whiteX: 0.281 whiteY: 0.308
[    18.642] (II) RADEON(0): Supported established timings:
[    18.642] (II) RADEON(0): 720x400@70Hz
[    18.642] (II) RADEON(0): 640x480@60Hz
[    18.642] (II) RADEON(0): 640x480@72Hz
[    18.642] (II) RADEON(0): 640x480@75Hz
[    18.642] (II) RADEON(0): 800x600@56Hz
[    18.642] (II) RADEON(0): 800x600@60Hz
[    18.642] (II) RADEON(0): 800x600@72Hz
[    18.642] (II) RADEON(0): 800x600@75Hz
[    18.642] (II) RADEON(0): 1024x768@60Hz
[    18.642] (II) RADEON(0): 1024x768@70Hz
[    18.642] (II) RADEON(0): 1024x768@75Hz
[    18.642] (II) RADEON(0): 1280x1024@75Hz
[    18.642] (II) RADEON(0): Manufacturer's mask: 0
[    18.642] (II) RADEON(0): Supported standard timings:
[    18.642] (II) RADEON(0): #0: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    18.642] (II) RADEON(0): #1: hsize: 1024  vsize 768  refresh: 72  vid: 19553
[    18.642] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.642] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 70  vid: 35457
[    18.642] (II) RADEON(0): #4: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    18.642] (II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 75  vid: 20353
[    18.642] (II) RADEON(0): #6: hsize: 1280  vsize 720  refresh: 75  vid: 53121
[    18.642] (II) RADEON(0): #7: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    18.642] (II) RADEON(0): Supported detailed timing:
[    18.642] (II) RADEON(0): clock: 138.7 MHz   Image Size:  0 x 0 mm
[    18.642] (II) RADEON(0): h_active: 1920  h_sync: 1952  h_sync_end 2016 h_blank_end 2080 h_border: 0
[    18.642] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1089 v_blanking: 1111 v_border: 0
[    18.642] (II) RADEON(0): Supported detailed timing:
[    18.642] (II) RADEON(0): clock: 144.2 MHz   Image Size:  410 x 256 mm
[    18.642] (II) RADEON(0): h_active: 1680  h_sync: 1760  h_sync_end 1912 h_blank_end 2240 h_border: 0
[    18.642] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    18.642] (II) RADEON(0): Monitor name: 1080A
[    18.642] (II) RADEON(0): EDID (in hex):
[    18.642] (II) RADEON(0):     00ffffffffffff000ed4010001000000
[    18.642] (II) RADEON(0):     1d100103080000008a0013a057499b26
[    18.642] (II) RADEON(0):     10484eafcf00454a614c8180818a81c0
[    18.642] (II) RADEON(0):     814f81cf8140293680a070381f402040
[    18.642] (II) RADEON(0):     360000000000001858389030621a2740
[    18.642] (II) RADEON(0):     509836009a001100001c000000fc0031
[    18.642] (II) RADEON(0):     303830410a0a0a0a0a0a0a0a00000010
[    18.642] (II) RADEON(0):     000a0a0a0a0a0a0a0a0a0a0a0a0a0089
[    18.642] (II) RADEON(0): Printing probed modes for output VGA-0
[    18.642] (II) RADEON(0): Modeline "1920x1080"x60.0  138.65  1920 1952 2016 2080  1080 1083 1089 1111 -hsync -vsync (66.7 kHz)
[    18.642] (II) RADEON(0): Modeline "1680x1050"x59.1  144.24  1680 1760 1912 2240  1050 1053 1059 1089 -hsync +vsync (64.4 kHz)
[    18.642] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.642] (II) RADEON(0): Modeline "1280x1024"x70.0  128.95  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[    18.642] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.643] (II) RADEON(0): Modeline "1280x960"x75.0  129.94  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.2 kHz)
[    18.643] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.643] (II) RADEON(0): Modeline "1280x720"x75.0   95.68  1280 1352 1488 1696  720 721 724 752 -hsync +vsync (56.4 kHz)
[    18.643] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[    18.643] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    18.643] (II) RADEON(0): Modeline "1024x768"x72.0   78.44  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[    18.643] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.643] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.643] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.643] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.643] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    18.643] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.643] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.643] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    18.643] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.643] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.643] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.643] (II) RADEON(0): Output HDMI-0 disconnected
[    18.643] (II) RADEON(0): Output DVI-0 disconnected
[    18.643] (II) RADEON(0): Output VGA-0 connected
[    18.643] (II) RADEON(0): Using exact sizes for initial modes
[    18.643] (II) RADEON(0): Output VGA-0 using initial mode 1920x1080
[    18.643] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.643] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:40000000 visible:f7d7000
[    18.643] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    18.643] (==) RADEON(0): DPI set to (96, 96)
[    18.643] (II) Loading sub module "fb"
[    18.643] (II) LoadModule: "fb"
[    18.643] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.646] (II) Module fb: vendor="X.Org Foundation"
[    18.646]     compiled for 1.10.4, module version = 1.0.0
[    18.646]     ABI class: X.Org ANSI C Emulation, version 0.4
[    18.646] (II) Loading sub module "ramdac"
[    18.646] (II) LoadModule: "ramdac"
[    18.646] (II) Module "ramdac" already built-in
[    18.646] (II) UnloadModule: "vesa"
[    18.646] (II) Unloading vesa
[    18.646] (II) UnloadModule: "fbdev"
[    18.646] (II) Unloading fbdev
[    18.646] (II) UnloadModule: "fbdevhw"
[    18.646] (II) Unloading fbdevhw
[    18.646] (--) Depth 24 pixmap format is 32 bpp
[    18.646] (II) RADEON(0): [DRI2] Setup complete
[    18.646] (II) RADEON(0): [DRI2]   DRI driver: r600
[    18.646] (II) RADEON(0): Front buffer size: 8100K
[    18.646] (II) RADEON(0): VRAM usage limit set to 221119K
[    18.673] (==) RADEON(0): Backing store disabled
[    18.673] (II) RADEON(0): Direct rendering enabled
[    18.676] (II) RADEON(0): Setting EXA maxPitchBytes
[    18.676] (II) EXA(0): Driver allocated offscreen pixmaps
[    18.676] (II) EXA(0): Driver registered support for the following operations:
[    18.676] (II)         Solid
[    18.676] (II)         Copy
[    18.676] (II)         Composite (RENDER acceleration)
[    18.676] (II)         UploadToScreen
[    18.676] (II)         DownloadFromScreen
[    18.676] (II) RADEON(0): Acceleration enabled
[    18.676] (==) RADEON(0): DPMS enabled
[    18.676] (==) RADEON(0): Silken mouse enabled
[    18.676] (II) RADEON(0): Set up textured video
[    18.677] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    18.677] (II) RADEON(0): [XvMC] Extension initialized.
[    18.677] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.677] (--) RandR disabled
[    18.677] (II) Initializing built-in extension Generic Event Extension
[    18.677] (II) Initializing built-in extension SHAPE
[    18.677] (II) Initializing built-in extension MIT-SHM
[    18.677] (II) Initializing built-in extension XInputExtension
[    18.677] (II) Initializing built-in extension XTEST
[    18.677] (II) Initializing built-in extension BIG-REQUESTS
[    18.677] (II) Initializing built-in extension SYNC
[    18.677] (II) Initializing built-in extension XKEYBOARD
[    18.677] (II) Initializing built-in extension XC-MISC
[    18.677] (II) Initializing built-in extension SECURITY
[    18.677] (II) Initializing built-in extension XINERAMA
[    18.677] (II) Initializing built-in extension XFIXES
[    18.677] (II) Initializing built-in extension RENDER
[    18.677] (II) Initializing built-in extension RANDR
[    18.677] (II) Initializing built-in extension COMPOSITE
[    18.677] (II) Initializing built-in extension DAMAGE
[    18.677] (II) Initializing built-in extension GESTURE
[    18.682] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/r600_dri.so
[    19.170] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    19.170] (II) AIGLX: enabled GLX_INTEL_swap_event
[    19.170] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    19.170] (II) AIGLX: enabled GLX_SGI_make_current_read
[    19.170] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    19.170] (II) AIGLX: Loaded and initialized r600
[    19.170] (II) GLX: Initialized DRI2 GL provider for screen 0
[    19.172] (II) RADEON(0): Setting screen physical size to 508 x 285
[    19.236] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.355] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.355] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.355] (II) LoadModule: "evdev"
[    19.355] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.407] (II) Module evdev: vendor="X.Org Foundation"
[    19.407]     compiled for 1.10.2, module version = 2.6.0
[    19.407]     Module class: X.Org XInput Driver
[    19.408]     ABI class: X.Org XInput driver, version 12.3
[    19.408] (II) Using input driver 'evdev' for 'Power Button'
[    19.408] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.408] (**) Power Button: always reports core events
[    19.408] (**) Power Button: Device: "/dev/input/event1"
[    19.408] (--) Power Button: Found keys
[    19.408] (II) Power Button: Configuring as keyboard
[    19.408] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.408] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.408] (**) Option "xkb_rules" "evdev"
[    19.408] (**) Option "xkb_model" "pc105"
[    19.408] (**) Option "xkb_layout" "gb"
[    19.408] (**) Option "xkb_options" "lv3:ralt_switch"
[    19.409] (II) XKB: generating xkmfile /var/lib/xkb/server-884C6C7246E5186E4DB7A4CD26B9F16BE06DFFDC.xkm
[    19.446] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.446] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.446] (II) Using input driver 'evdev' for 'Power Button'
[    19.446] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.446] (**) Power Button: always reports core events
[    19.446] (**) Power Button: Device: "/dev/input/event0"
[    19.446] (--) Power Button: Found keys
[    19.446] (II) Power Button: Configuring as keyboard
[    19.446] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    19.446] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.446] (**) Option "xkb_rules" "evdev"
[    19.446] (**) Option "xkb_model" "pc105"
[    19.446] (**) Option "xkb_layout" "gb"
[    19.446] (**) Option "xkb_options" "lv3:ralt_switch"
[    19.447] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event4)
[    19.447] (II) No input driver/identifier specified (ignoring)
[    19.448] (II) config/udev: Adding input device zc3xx (/dev/input/event6)
[    19.448] (**) zc3xx: Applying InputClass "evdev keyboard catchall"
[    19.448] (II) Using input driver 'evdev' for 'zc3xx'
[    19.448] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.448] (**) zc3xx: always reports core events
[    19.448] (**) zc3xx: Device: "/dev/input/event6"
[    19.448] (--) zc3xx: Found keys
[    19.448] (II) zc3xx: Configuring as keyboard
[    19.448] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:07.0/0000:03:00.0/usb8/8-1/input/input6/event6"
[    19.448] (II) XINPUT: Adding extended input device "zc3xx" (type: KEYBOARD)
[    19.448] (**) Option "xkb_rules" "evdev"
[    19.448] (**) Option "xkb_model" "pc105"
[    19.448] (**) Option "xkb_layout" "gb"
[    19.448] (**) Option "xkb_options" "lv3:ralt_switch"
[    19.451] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event3)
[    19.451] (II) No input driver/identifier specified (ignoring)
[    19.465] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    19.465] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.465] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.465] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.465] (**) AT Translated Set 2 keyboard: always reports core events
[    19.465] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    19.465] (--) AT Translated Set 2 keyboard: Found keys
[    19.465] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.465] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    19.465] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.465] (**) Option "xkb_rules" "evdev"
[    19.465] (**) Option "xkb_model" "pc105"
[    19.465] (**) Option "xkb_layout" "gb"
[    19.465] (**) Option "xkb_options" "lv3:ralt_switch"
[    19.465] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
[    19.465] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    19.465] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    19.465] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.465] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    19.465] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
[    19.465] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    19.465] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    19.465] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    19.465] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    19.465] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    19.465] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    19.465] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    19.465] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.465] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    19.465] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    19.465] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    19.465] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    19.465] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    19.465] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    19.465] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    19.466] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    19.466] (II) No input driver/identifier specified (ignoring)
[    20.642] (II) RADEON(0): EDID vendor "CVT", prod id 1
[    20.642] (II) RADEON(0): Printing DDC gathered Modelines:
[    20.642] (II) RADEON(0): Modeline "1920x1080"x0.0  138.65  1920 1952 2016 2080  1080 1083 1089 1111 -hsync -vsync (66.7 kHz)
[    20.642] (II) RADEON(0): Modeline "1680x1050"x0.0  144.24  1680 1760 1912 2240  1050 1053 1059 1089 -hsync +vsync (64.4 kHz)
[    20.642] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.642] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    20.642] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    20.642] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    20.642] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.642] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    20.642] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    20.642] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    20.642] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    20.642] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    20.642] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    20.642] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    20.642] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    20.642] (II) RADEON(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[    20.643] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    20.643] (II) RADEON(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[    20.643] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    20.643] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.1 kHz)
[    20.643] (II) RADEON(0): Modeline "1280x720"x75.0   95.65  1280 1352 1488 1696  720 721 724 752 -hsync +vsync (56.4 kHz)
[    20.643] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    21.393] (II) RADEON(0): EDID vendor "CVT", prod id 1
[    21.393] (II) RADEON(0): Printing DDC gathered Modelines:
[    21.393] (II) RADEON(0): Modeline "1920x1080"x0.0  138.65  1920 1952 2016 2080  1080 1083 1089 1111 -hsync -vsync (66.7 kHz)
[    21.393] (II) RADEON(0): Modeline "1680x1050"x0.0  144.24  1680 1760 1912 2240  1050 1053 1059 1089 -hsync +vsync (64.4 kHz)
[    21.393] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.393] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.393] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.393] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    21.393] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.393] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    21.393] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    21.393] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.393] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    21.393] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.393] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.393] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    21.393] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    21.393] (II) RADEON(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[    21.393] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    21.393] (II) RADEON(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[    21.393] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    21.393] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.1 kHz)
[    21.393] (II) RADEON(0): Modeline "1280x720"x75.0   95.65  1280 1352 1488 1696  720 721 724 752 -hsync +vsync (56.4 kHz)
[    21.393] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.449] (II) RADEON(0): EDID vendor "CVT", prod id 1
[    23.450] (II) RADEON(0): Printing DDC gathered Modelines:
[    23.450] (II) RADEON(0): Modeline "1920x1080"x0.0  138.65  1920 1952 2016 2080  1080 1083 1089 1111 -hsync -vsync (66.7 kHz)
[    23.450] (II) RADEON(0): Modeline "1680x1050"x0.0  144.24  1680 1760 1912 2240  1050 1053 1059 1089 -hsync +vsync (64.4 kHz)
[    23.450] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.450] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.450] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.450] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    23.450] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.450] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.450] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    23.450] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.450] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    23.450] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.450] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.450] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    23.450] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    23.450] (II) RADEON(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[    23.450] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.450] (II) RADEON(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[    23.450] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    23.450] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.1 kHz)
[    23.450] (II) RADEON(0): Modeline "1280x720"x75.0   95.65  1280 1352 1488 1696  720 721 724 752 -hsync +vsync (56.4 kHz)
[    23.450] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    24.687] (II) RADEON(0): EDID vendor "CVT", prod id 1
[    24.687] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.687] (II) RADEON(0): Modeline "1920x1080"x0.0  138.65  1920 1952 2016 2080  1080 1083 1089 1111 -hsync -vsync (66.7 kHz)
[    24.687] (II) RADEON(0): Modeline "1680x1050"x0.0  144.24  1680 1760 1912 2240  1050 1053 1059 1089 -hsync +vsync (64.4 kHz)
[    24.687] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.687] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    24.687] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.687] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    24.687] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.687] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    24.687] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    24.687] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.687] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    24.687] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.687] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.687] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    24.687] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    24.687] (II) RADEON(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[    24.687] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.687] (II) RADEON(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[    24.687] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    24.687] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.1 kHz)
[    24.687] (II) RADEON(0): Modeline "1280x720"x75.0   95.65  1280 1352 1488 1696  720 721 724 752 -hsync +vsync (56.4 kHz)
[    24.687] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    25.023] (II) XKB: generating xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  2565.085] (II) RADEON(0): EDID vendor "CVT", prod id 1
[  2565.085] (II) RADEON(0): Printing DDC gathered Modelines:
[  2565.085] (II) RADEON(0): Modeline "1920x1080"x0.0  138.65  1920 1952 2016 2080  1080 1083 1089 1111 -hsync -vsync (66.7 kHz)
[  2565.085] (II) RADEON(0): Modeline "1680x1050"x0.0  144.24  1680 1760 1912 2240  1050 1053 1059 1089 -hsync +vsync (64.4 kHz)
[  2565.085] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  2565.085] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  2565.085] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  2565.085] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  2565.085] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  2565.085] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  2565.085] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  2565.085] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  2565.085] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  2565.085] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  2565.085] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  2565.085] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  2565.085] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[  2565.085] (II) RADEON(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[  2565.085] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  2565.085] (II) RADEON(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[  2565.085] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[  2565.085] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.1 kHz)
[  2565.085] (II) RADEON(0): Modeline "1280x720"x75.0   95.65  1280 1352 1488 1696  720 721 724 752 -hsync +vsync (56.4 kHz)
[  2565.085] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  4550.431] (II) RADEON(0): EDID vendor "CVT", prod id 1
[  4550.431] (II) RADEON(0): Printing DDC gathered Modelines:
[  4550.431] (II) RADEON(0): Modeline "1920x1080"x0.0  138.65  1920 1952 2016 2080  1080 1083 1089 1111 -hsync -vsync (66.7 kHz)
[  4550.431] (II) RADEON(0): Modeline "1680x1050"x0.0  144.24  1680 1760 1912 2240  1050 1053 1059 1089 -hsync +vsync (64.4 kHz)
[  4550.431] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  4550.431] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  4550.431] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  4550.431] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  4550.431] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  4550.431] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  4550.431] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  4550.431] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  4550.431] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  4550.431] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  4550.431] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  4550.431] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  4550.431] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[  4550.431] (II) RADEON(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[  4550.431] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  4550.431] (II) RADEON(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[  4550.431] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[  4550.431] (II) RADEON(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 -hsync +vsync (75.1 kHz)
[  4550.431] (II) RADEON(0): Modeline "1280x720"x75.0   95.65  1280 1352 1488 1696  720 721 724 752 -hsync +vsync (56.4 kHz)
[  4550.431] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
```

---

### Post by rossmounce on 2012-08-07
*bump*

Further info.

I've switched out the RAM & the PSU so it's neither of those at fault. It's either the graphics card, mobo or CPU.

Booting from a live USB distro works-ish but as shown in the screenshot, it suffers from strange visual artifacts and is not stable (will tend towards system halt "general protection fault") if left on and used for a while.

Booting from HDD it just won't much further at all after the BIOS / POST screen.

Will try swapping in a different graphics card.

Is there an equivalent to memtest86 for checking graphics cards? Is there any kind of diagnostic tests I could run from a live USB stick to test my graphics card?


UPDATE: Bought a new graphics card (a GeForce 210), it seems to have solved my problems. Thanks

---

