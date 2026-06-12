---
title: "Some problems in Ubuntu.."
date: 2012-07-18
forum: General Help
---

### Post by stepking2 on 2012-07-18
I have some minor problems in Ubuntu.

There is always popping up a "Ubuntu has encountered an error, would you like to send a bug report?".

Sometimes when I am in the middle of doing something, Ubuntu just logs out of my user. And sometimes it will not even log in.

I have alot of pentesting tools installed, such as Kismet, Pyrit etc.
And every time, after I quit Kismet, Ubuntu ecounters a problem. And I think the problem there is because I use Ath5k are a source instead of Ath9k (Ath9k doesn't work in Kismet).

Yesterday when I used Pyrit, in the middle of typing a command, Ubuntu logged me out of my user, and when I logged in there was vertical black strips on my screen every time something moved.

Is these problems because of the programs/tools I've installed, are buggy?

I run Ubuntu 12.04 LTS 64bit, and have upgraded to a SSD, Crucial M4 512GB.

---

### Post by David Andersson on 2012-07-18
> **stepking2 said:**
> 
There is always popping up a "Ubuntu has encountered an error, would you like to send a bug report?".


Is there any details about what program caused the error, or an error message?

> **stepking2 said:**
> 
Sometimes when I am in the middle of doing something, Ubuntu just logs out of my user. And sometimes it will not even log in.


You mean you are immediately taken to the login scren, not a re-boot? Then maybe there is a problem with the graphics. What graphics card? Have you installed proprietary drivers? (See System settings > Hardware Drivers). Check the logs /var/log/Xorg.0.log or /var/log/Xorg.0.log.old or /home/your_name/.xsession-errors

---

### Post by stepking2 on 2012-07-19
As you said, I get immediately taken back to the login screen. 

I have a Radeon HD6600M graphics card with the proprietary drivers installed and activated.

Just now, I got logged out, and the screen gets vertical, black stripes every time something moves.
Here is Xorg.0.log: 
```
[  2617.339] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[  2617.339] X Protocol Version 11, Revision 0
[  2617.339] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[  2617.339] Current Operating System: Linux 5552G 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64
[  2617.339] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=a82815eb-9fdb-4303-94b0-595cc4777cc6 ro quiet splash vt.handoff=7
[  2617.339] Build Date: 16 July 2012  08:06:31PM
[  2617.339] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  2617.339] Current version of pixman: 0.24.4
[  2617.339]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[  2617.339] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2617.339] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 19 22:17:36 2012
[  2617.339] (==) Using config file: "/etc/X11/xorg.conf"
[  2617.339] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2617.339] (==) No Layout section.  Using the first Screen section.
[  2617.339] (**) |-->Screen "Default Screen" (0)
[  2617.339] (**) |   |-->Monitor "<default monitor>"
[  2617.340] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[  2617.340] (==) Automatically adding devices
[  2617.340] (==) Automatically enabling devices
[  2617.340] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2617.340]     Entry deleted from font path.
[  2617.340] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  2617.340]     Entry deleted from font path.
[  2617.340] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  2617.340]     Entry deleted from font path.
[  2617.340] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  2617.340]     Entry deleted from font path.
[  2617.340] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  2617.340]     Entry deleted from font path.
[  2617.340] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[  2617.340]     Entry deleted from font path.
[  2617.340] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[  2617.340] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  2617.340] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  2617.340] (II) Loader magic: 0x7fbdf2c1db00
[  2617.340] (II) Module ABI versions:
[  2617.340]     X.Org ANSI C Emulation: 0.4
[  2617.340]     X.Org Video Driver: 11.0
[  2617.340]     X.Org XInput driver : 16.0
[  2617.340]     X.Org Server Extension : 6.0
[  2617.341] (--) PCI:*(0:1:0:0) 1002:6741:1025:0489 rev 0, Mem @ 0xe0000000/268435456, 0xf2100000/131072, I/O @ 0x00006000/256, BIOS @ 0x????????/131072
[  2617.344] (II) Open ACPI successful (/var/run/acpid.socket)
[  2617.344] (II) "extmod" will be loaded by default.
[  2617.344] (II) "dbe" will be loaded by default.
[  2617.344] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  2617.344] (II) "record" will be loaded by default.
[  2617.344] (II) "dri" will be loaded by default.
[  2617.344] (II) "dri2" will be loaded by default.
[  2617.344] (II) LoadModule: "glx"
[  2617.344] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[  2617.344] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[  2617.344]     compiled for 6.9.0, module version = 1.0.0
[  2617.344] (II) Loading extension GLX
[  2617.344] (II) LoadModule: "extmod"
[  2617.345] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2617.345] (II) Module extmod: vendor="X.Org Foundation"
[  2617.345]     compiled for 1.11.3, module version = 1.0.0
[  2617.345]     Module class: X.Org Server Extension
[  2617.345]     ABI class: X.Org Server Extension, version 6.0
[  2617.345] (II) Loading extension MIT-SCREEN-SAVER
[  2617.345] (II) Loading extension XFree86-VidModeExtension
[  2617.345] (II) Loading extension XFree86-DGA
[  2617.345] (II) Loading extension DPMS
[  2617.345] (II) Loading extension XVideo
[  2617.345] (II) Loading extension XVideo-MotionCompensation
[  2617.345] (II) Loading extension X-Resource
[  2617.345] (II) LoadModule: "dbe"
[  2617.345] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2617.345] (II) Module dbe: vendor="X.Org Foundation"
[  2617.345]     compiled for 1.11.3, module version = 1.0.0
[  2617.345]     Module class: X.Org Server Extension
[  2617.345]     ABI class: X.Org Server Extension, version 6.0
[  2617.345] (II) Loading extension DOUBLE-BUFFER
[  2617.345] (II) LoadModule: "record"
[  2617.346] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2617.346] (II) Module record: vendor="X.Org Foundation"
[  2617.346]     compiled for 1.11.3, module version = 1.13.0
[  2617.346]     Module class: X.Org Server Extension
[  2617.346]     ABI class: X.Org Server Extension, version 6.0
[  2617.346] (II) Loading extension RECORD
[  2617.346] (II) LoadModule: "dri"
[  2617.347] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2617.347] (II) Module dri: vendor="X.Org Foundation"
[  2617.347]     compiled for 1.11.3, module version = 1.0.0
[  2617.347]     ABI class: X.Org Server Extension, version 6.0
[  2617.347] (II) Loading extension XFree86-DRI
[  2617.347] (II) LoadModule: "dri2"
[  2617.347] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2617.347] (II) Module dri2: vendor="X.Org Foundation"
[  2617.347]     compiled for 1.11.3, module version = 1.2.0
[  2617.347]     ABI class: X.Org Server Extension, version 6.0
[  2617.347] (II) Loading extension DRI2
[  2617.347] (==) Matched fglrx as autoconfigured driver 0
[  2617.347] (==) Matched ati as autoconfigured driver 1
[  2617.347] (==) Matched vesa as autoconfigured driver 2
[  2617.347] (==) Matched fbdev as autoconfigured driver 3
[  2617.347] (==) Assigned the driver to the xf86ConfigLayout
[  2617.347] (II) LoadModule: "fglrx"
[  2617.347] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[  2617.392] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[  2617.392]     compiled for 1.4.99.906, module version = 8.96.4
[  2617.392]     Module class: X.Org Video Driver
[  2617.392] (II) Loading sub module "fglrxdrm"
[  2617.392] (II) LoadModule: "fglrxdrm"
[  2617.392] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[  2617.393] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[  2617.393]     compiled for 1.4.99.906, module version = 8.96.4
[  2617.393] (II) LoadModule: "ati"
[  2617.393] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  2617.393] (II) Module ati: vendor="X.Org Foundation"
[  2617.393]     compiled for 1.11.3, module version = 6.14.99
[  2617.393]     Module class: X.Org Video Driver
[  2617.393]     ABI class: X.Org Video Driver, version 11.0
[  2617.393] (II) LoadModule: "radeon"
[  2617.393] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  2617.394] (II) Module radeon: vendor="X.Org Foundation"
[  2617.394]     compiled for 1.11.3, module version = 6.14.99
[  2617.394]     Module class: X.Org Video Driver
[  2617.394]     ABI class: X.Org Video Driver, version 11.0
[  2617.394] (II) LoadModule: "vesa"
[  2617.394] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  2617.394] (II) Module vesa: vendor="X.Org Foundation"
[  2617.394]     compiled for 1.11.3, module version = 2.3.0
[  2617.394]     Module class: X.Org Video Driver
[  2617.394]     ABI class: X.Org Video Driver, version 11.0
[  2617.394] (II) LoadModule: "fbdev"
[  2617.395] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  2617.395] (II) Module fbdev: vendor="X.Org Foundation"
[  2617.395]     compiled for 1.11.3, module version = 0.4.2
[  2617.395]     ABI class: X.Org Video Driver, version 11.0
[  2617.395] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[  2617.395] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[  2617.395] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:50
[  2617.395] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
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
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[  2617.398] (II) VESA: driver for VESA chipsets: vesa
[  2617.398] (II) FBDEV: driver for framebuffer: fbdev
[  2617.398] (++) using VT number 7

[  2617.398] (WW) Falling back to old probe method for fglrx
[  2617.404] (II) Loading PCS database from /etc/ati/amdpcsdb
[  2617.405] (--) Assigning device section with no busID to primary device
[  2617.405] (--) Chipset Supported AMD Graphics Processor (0x6741) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[  2617.405] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[  2617.405] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[  2617.406] (II) AMD Video driver is signed
[  2617.406] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[  2617.406] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[  2617.406] (II) fglrx(0): pEnt->device->identifier=0x7fbdf29d052f
[  2617.406] (WW) Falling back to old probe method for vesa
[  2617.406] (WW) Falling back to old probe method for fbdev
[  2617.406] (II) Loading sub module "fbdevhw"
[  2617.406] (II) LoadModule: "fbdevhw"
[  2617.406] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  2617.406] (II) Module fbdevhw: vendor="X.Org Foundation"
[  2617.406]     compiled for 1.11.3, module version = 0.0.2
[  2617.406]     ABI class: X.Org Video Driver, version 11.0
[  2617.406] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[  2617.406] (II) Loading sub module "vgahw"
[  2617.406] (II) LoadModule: "vgahw"
[  2617.407] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[  2617.407] (II) Module vgahw: vendor="X.Org Foundation"
[  2617.407]     compiled for 1.11.3, module version = 0.1.0
[  2617.407]     ABI class: X.Org Video Driver, version 11.0
[  2617.407] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[  2617.407] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[  2617.407] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  2617.407] (==) fglrx(0): Default visual is TrueColor
[  2617.407] (==) fglrx(0): RGB weight 888
[  2617.407] (II) fglrx(0): Using 8 bits per RGB 
[  2617.407] (==) fglrx(0): Buffer Tiling is ON
[  2617.407] (II) Loading sub module "fglrxdrm"
[  2617.407] (II) LoadModule: "fglrxdrm"
[  2617.407] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[  2617.407] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[  2617.407]     compiled for 1.4.99.906, module version = 8.96.4
[  2617.420] ukiDynamicMajor: found major device number 251
[  2617.420] ukiDynamicMajor: found major device number 251
[  2617.420] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[  2617.420] ukiOpenDevice: node name is /dev/ati/card0
[  2617.420] ukiOpenDevice: open result is 12, (OK)
[  2617.420] ukiOpenByBusid: ukiOpenMinor returns 12
[  2617.420] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[  2617.421] (**) fglrx(0): NoAccel = NO
[  2617.421] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[  2617.421] (--) fglrx(0): Chipset: "AMD Radeon 6600M and 6700M Series" (Chipset = 0x6741)
[  2617.421] (--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x0489)
[  2617.421] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[  2617.421] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[  2617.421] (--) fglrx(0): MMIO registers at 0xf2100000
[  2617.421] (--) fglrx(0): I/O port at 0x00006000
[  2617.421] (==) fglrx(0): ROM-BIOS at 0x000c0000
[  2617.421] (II) fglrx(0): ATIF platform detected
[  2617.424] (II) fglrx(0): AC Adapter is used
[  2617.440] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[  2617.546] (II) Loading sub module "vbe"
[  2617.546] (II) LoadModule: "vbe"
[  2617.546] (II) Loading /usr/lib/xorg/modules/libvbe.so
[  2617.547] (II) Module vbe: vendor="X.Org Foundation"
[  2617.547]     compiled for 1.11.3, module version = 1.1.0
[  2617.547]     ABI class: X.Org Video Driver, version 11.0
[  2617.547] (II) fglrx(0): VESA BIOS detected
[  2617.547] (II) fglrx(0): VESA VBE Version 3.0
[  2617.547] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[  2617.547] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[  2617.547] (II) fglrx(0): VESA VBE OEM Software Rev: 13.7
[  2617.547] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[  2617.547] (II) fglrx(0): VESA VBE OEM Product: WHISTLER
[  2617.547] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[  2617.585] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[  2617.586] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[  2617.586] (II) fglrx(0): PCIE card detected
[  2617.586] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[  2617.586] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[  2617.590] (II) fglrx(0): Using adapter: 1:0.0.
[  2617.590] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[  2617.590] (II) fglrx(0): Interrupt handler installed at IRQ 46.
[  2617.591] (II) fglrx(0): RandR 1.2 support is enabled!
[  2617.591] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[  2617.591] (==) fglrx(0): Center Mode is disabled 
[  2617.591] (II) Loading sub module "fb"
[  2617.591] (II) LoadModule: "fb"
[  2617.591] (II) Loading /usr/lib/xorg/modules/libfb.so
[  2617.591] (II) Module fb: vendor="X.Org Foundation"
[  2617.591]     compiled for 1.11.3, module version = 1.0.0
[  2617.591]     ABI class: X.Org ANSI C Emulation, version 0.4
[  2617.591] (II) Loading sub module "ddc"
[  2617.591] (II) LoadModule: "ddc"
[  2617.591] (II) Module "ddc" already built-in
[  2617.692] (II) fglrx(0): Finished Initialize PPLIB!
[  2617.693] (II) fglrx(0): Output LVDS has no monitor section
[  2617.693] (II) fglrx(0): Output DFP1 has no monitor section
[  2617.693] (II) fglrx(0): Output CRT1 has no monitor section
[  2617.693] (II) Loading sub module "ddc"
[  2617.693] (II) LoadModule: "ddc"
[  2617.693] (II) Module "ddc" already built-in
[  2617.693] (II) fglrx(0): Connected Display0: LVDS
[  2617.693] (II) fglrx(0): Display0 EDID data ---------------------------
[  2617.693] (II) fglrx(0): Manufacturer: LGD  Model: 250  Serial#: 0
[  2617.693] (II) fglrx(0): Year: 2010  Week: 0
[  2617.693] (II) fglrx(0): EDID Version: 1.3
[  2617.693] (II) fglrx(0): Digital Display Input
[  2617.693] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[  2617.693] (II) fglrx(0): Gamma: 2.20
[  2617.693] (II) fglrx(0): No DPMS capabilities specified
[  2617.693] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  2617.693] (II) fglrx(0): First detailed timing is preferred mode
[  2617.693] (II) fglrx(0): redX: 0.612 redY: 0.375   greenX: 0.332 greenY: 0.619
[  2617.693] (II) fglrx(0): blueX: 0.151 blueY: 0.099   whiteX: 0.313 whiteY: 0.329
[  2617.693] (II) fglrx(0): Manufacturer's mask: 0
[  2617.693] (II) fglrx(0): Supported detailed timing:
[  2617.693] (II) fglrx(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[  2617.693] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[  2617.693] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[  2617.693] (II) fglrx(0):  LG Display
[  2617.693] (II) fglrx(0):  LP156WH2-TLEA
[  2617.693] (II) fglrx(0): EDID (in hex):
[  2617.693] (II) fglrx(0):     00ffffffffffff0030e4500200000000
[  2617.693] (II) fglrx(0):     00140103802313780ac2d59c60559e26
[  2617.693] (II) fglrx(0):     19505400000001010101010101010101
[  2617.693] (II) fglrx(0):     0101010101013e1c56a0500016303020
[  2617.693] (II) fglrx(0):     350059c2100000190000000000000000
[  2617.693] (II) fglrx(0):     00000000000000000000000000fe004c
[  2617.693] (II) fglrx(0):     4720446973706c61790a2020000000fe
[  2617.693] (II) fglrx(0):     004c503135365748322d544c454100fd
[  2617.693] (II) fglrx(0): End of Display0 EDID data --------------------
[  2617.694] (II) fglrx(0): EDID for output LVDS
[  2617.694] (II) fglrx(0): Manufacturer: LGD  Model: 250  Serial#: 0
[  2617.694] (II) fglrx(0): Year: 2010  Week: 0
[  2617.694] (II) fglrx(0): EDID Version: 1.3
[  2617.694] (II) fglrx(0): Digital Display Input
[  2617.694] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[  2617.694] (II) fglrx(0): Gamma: 2.20
[  2617.694] (II) fglrx(0): No DPMS capabilities specified
[  2617.694] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  2617.694] (II) fglrx(0): First detailed timing is preferred mode
[  2617.694] (II) fglrx(0): redX: 0.612 redY: 0.375   greenX: 0.332 greenY: 0.619
[  2617.694] (II) fglrx(0): blueX: 0.151 blueY: 0.099   whiteX: 0.313 whiteY: 0.329
[  2617.694] (II) fglrx(0): Manufacturer's mask: 0
[  2617.694] (II) fglrx(0): Supported detailed timing:
[  2617.694] (II) fglrx(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[  2617.694] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[  2617.694] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[  2617.694] (II) fglrx(0):  LG Display
[  2617.694] (II) fglrx(0):  LP156WH2-TLEA
[  2617.694] (II) fglrx(0): EDID (in hex):
[  2617.694] (II) fglrx(0):     00ffffffffffff0030e4500200000000
[  2617.694] (II) fglrx(0):     00140103802313780ac2d59c60559e26
[  2617.694] (II) fglrx(0):     19505400000001010101010101010101
[  2617.694] (II) fglrx(0):     0101010101013e1c56a0500016303020
[  2617.694] (II) fglrx(0):     350059c2100000190000000000000000
[  2617.694] (II) fglrx(0):     00000000000000000000000000fe004c
[  2617.694] (II) fglrx(0):     4720446973706c61790a2020000000fe
[  2617.694] (II) fglrx(0):     004c503135365748322d544c454100fd
[  2617.694] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2617.694] (II) fglrx(0): Printing DDC gathered Modelines:
[  2617.694] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Printing probed modes for output LVDS
[  2617.694] (II) fglrx(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Modeline "1360x768"x60.0   72.30  1360 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Modeline "1280x768"x60.0   72.30  1280 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Modeline "1280x720"x60.0   72.30  1280 1414 1446 1526  720 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Modeline "1024x768"x60.0   72.30  1024 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Modeline "1024x600"x60.0   72.30  1024 1414 1446 1526  600 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Modeline "800x600"x60.0   72.30  800 1414 1446 1526  600 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Modeline "800x480"x60.0   72.30  800 1414 1446 1526  480 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): Modeline "640x480"x60.0   72.30  640 1414 1446 1526  480 771 776 790 -hsync -vsync (47.4 kHz)
[  2617.694] (II) fglrx(0): EDID for output DFP1
[  2617.694] (II) fglrx(0): EDID for output CRT1
[  2617.694] (II) fglrx(0): Output LVDS connected
[  2617.694] (II) fglrx(0): Output DFP1 disconnected
[  2617.694] (II) fglrx(0): Output CRT1 disconnected
[  2617.694] (II) fglrx(0): Using exact sizes for initial modes
[  2617.694] (II) fglrx(0): Output LVDS using initial mode 1366x768
[  2617.694] (II) fglrx(0): Display dimensions: (350, 190) mm
[  2617.694] (II) fglrx(0): DPI set to (99, 102)
[  2617.694] (II) fglrx(0): Eyefinity capable adapter detected.
[  2617.695] (II) fglrx(0): Adapter AMD Radeon 6600M and 6700M Series has 6 configurable heads and 1 displays connected.
[  2617.695] (==) fglrx(0):  PseudoColor visuals disabled
[  2617.695] (II) Loading sub module "ramdac"
[  2617.695] (II) LoadModule: "ramdac"
[  2617.695] (II) Module "ramdac" already built-in
[  2617.695] (==) fglrx(0): NoDRI = NO
[  2617.695] (==) fglrx(0): Capabilities: 0x00000000
[  2617.695] (==) fglrx(0): CapabilitiesEx: 0x00000000
[  2617.695] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[  2617.695] (==) fglrx(0): UseFastTLS=0
[  2617.695] (==) fglrx(0): BlockSignalsOnLock=1
[  2617.695] (II) UnloadModule: "radeon"
[  2617.695] (II) Unloading radeon
[  2617.695] (II) UnloadModule: "vesa"
[  2617.695] (II) Unloading vesa
[  2617.695] (II) UnloadModule: "fbdev"
[  2617.695] (II) Unloading fbdev
[  2617.695] (II) UnloadModule: "fbdevhw"
[  2617.695] (II) Unloading fbdevhw
[  2617.695] (--) Depth 24 pixmap format is 32 bpp
[  2617.695] (II) Loading extension ATIFGLRXDRI
[  2617.695] (II) fglrx(0): doing swlDriScreenInit
[  2617.695] (II) fglrx(0): swlDriScreenInit for fglrx driver
[  2617.695] ukiDynamicMajor: found major device number 251
[  2617.695] ukiDynamicMajor: found major device number 251
[  2617.695] ukiDynamicMajor: found major device number 251
[  2617.695] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[  2617.695] ukiOpenDevice: node name is /dev/ati/card0
[  2617.695] ukiOpenDevice: open result is 17, (OK)
[  2617.695] ukiOpenByBusid: ukiOpenMinor returns 17
[  2617.695] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[  2617.695] (II) fglrx(0): [uki] DRM interface version 1.0
[  2617.695] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[  2617.695] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x5d84000
[  2617.695] (II) fglrx(0): [uki] mapped SAREA 0x5d84000 to 0x7fbdf281e000
[  2617.695] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[  2617.695] (II) fglrx(0): [uki] added 1 reserved context for kernel
[  2617.695] (II) fglrx(0): swlDriScreenInit done
[  2617.695] (II) fglrx(0): Kernel Module Version Information:
[  2617.695] (II) fglrx(0):     Name: fglrx
[  2617.695] (II) fglrx(0):     Version: 8.96.4
[  2617.695] (II) fglrx(0):     Date: Mar 12 2012
[  2617.695] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[  2617.695] (II) fglrx(0): Kernel Module version matches driver.
[  2617.695] (II) fglrx(0): Kernel Module Build Time Information:
[  2617.695] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-26-generic
[  2617.695] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[  2617.695] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[  2617.695] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[  2617.695] (II) fglrx(0): [uki] register handle = 0x00004000
[  2617.699] (II) fglrx(0): DRI initialization successfull
[  2617.699] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000
[  2617.699] (==) fglrx(0): Backing store disabled
[  2617.699] (II) Loading extension FGLRXEXTENSION
[  2617.699] (==) fglrx(0): DPMS enabled
[  2617.699] (II) fglrx(0): Initialized in-driver Xinerama extension
[  2617.699] (**) fglrx(0): Textured Video is enabled.
[  2617.699] (II) LoadModule: "glesx"
[  2617.699] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[  2617.700] (II) Module glesx: vendor="X.Org Foundation"
[  2617.700]     compiled for 1.4.99.906, module version = 1.0.0
[  2617.700] (II) Loading extension GLESX
[  2617.700] (II) fglrx(0): GLESX enableFlags = 592
[  2617.700] (II) fglrx(0): GLESX is enabled
[  2617.700] (II) LoadModule: "amdxmm"
[  2617.701] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[  2617.701] (II) Module amdxmm: vendor="X.Org Foundation"
[  2617.701]     compiled for 1.4.99.906, module version = 2.0.0
[  2617.709] (II) Loading extension AMDXVOPL
[  2617.709] (II) Loading extension AMDXVBA
[  2617.711] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[  2617.713] (II) fglrx(0): Enable composite support successfully
[  2617.713] (II) fglrx(0): X context handle = 0x9
[  2617.713] (II) fglrx(0): [DRI] installation complete
[  2617.713] (==) fglrx(0): Silken mouse enabled
[  2617.713] (==) fglrx(0): Using HW cursor of display infrastructure!
[  2617.714] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[  2617.714] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[  2617.714] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[  2618.103] (EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
[  2618.103] (EE) fglrx(0):        ulEventType = 00000007, ulEventData = 00000000
[  2618.124] (EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
[  2618.124] (EE) fglrx(0):        ulEventType = 00000007, ulEventData = 00000000
[  2618.126] (EE) fglrx(0): PPLIB: swlPPLibNotifyEventToPPLib() failed!
[  2618.126] (EE) fglrx(0):        ulEventType = 00000007, ulEventData = 00000000
[  2618.141] (--) RandR disabled
[  2618.141] (II) Initializing built-in extension Generic Event Extension
[  2618.141] (II) Initializing built-in extension SHAPE
[  2618.141] (II) Initializing built-in extension MIT-SHM
[  2618.141] (II) Initializing built-in extension XInputExtension
[  2618.141] (II) Initializing built-in extension XTEST
[  2618.141] (II) Initializing built-in extension BIG-REQUESTS
[  2618.141] (II) Initializing built-in extension SYNC
[  2618.141] (II) Initializing built-in extension XKEYBOARD
[  2618.141] (II) Initializing built-in extension XC-MISC
[  2618.141] (II) Initializing built-in extension SECURITY
[  2618.141] (II) Initializing built-in extension XINERAMA
[  2618.141] (II) Initializing built-in extension XFIXES
[  2618.141] (II) Initializing built-in extension RENDER
[  2618.141] (II) Initializing built-in extension RANDR
[  2618.141] (II) Initializing built-in extension COMPOSITE
[  2618.141] (II) Initializing built-in extension DAMAGE
[  2618.162] ukiDynamicMajor: found major device number 251
[  2618.162] ukiDynamicMajor: found major device number 251
[  2618.162] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[  2618.162] ukiOpenDevice: node name is /dev/ati/card0
[  2618.162] ukiOpenDevice: open result is 19, (OK)
[  2618.162] ukiOpenByBusid: ukiOpenMinor returns 19
[  2618.162] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[  2618.264] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[  2618.264] (II) fglrx(0): Enable the clock gating!
[  2618.264] (II) fglrx(0): Setting screen physical size to 361 x 203
[  2618.273] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  2618.276] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[  2618.277] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2618.277] (II) LoadModule: "evdev"
[  2618.277] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2618.277] (II) Module evdev: vendor="X.Org Foundation"
[  2618.277]     compiled for 1.11.3, module version = 2.7.0
[  2618.277]     Module class: X.Org XInput Driver
[  2618.277]     ABI class: X.Org XInput driver, version 16.0
[  2618.277] (II) Using input driver 'evdev' for 'Power Button'
[  2618.277] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2618.277] (**) Power Button: always reports core events
[  2618.277] (**) evdev: Power Button: Device: "/dev/input/event3"
[  2618.277] (--) evdev: Power Button: Vendor 0 Product 0x1
[  2618.277] (--) evdev: Power Button: Found keys
[  2618.277] (II) evdev: Power Button: Configuring as keyboard
[  2618.277] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[  2618.277] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[  2618.277] (**) Option "xkb_rules" "evdev"
[  2618.277] (**) Option "xkb_model" "pc105"
[  2618.277] (**) Option "xkb_layout" "no"
[  2618.279] (II) XKB: reuse xkmfile /var/lib/xkb/server-5F8E417E6ED2D276BE32A8CA0E3DB916C21A8CA2.xkm
[  2618.280] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[  2618.280] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  2618.280] (II) Using input driver 'evdev' for 'Video Bus'
[  2618.280] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2618.280] (**) Video Bus: always reports core events
[  2618.280] (**) evdev: Video Bus: Device: "/dev/input/event5"
[  2618.280] (--) evdev: Video Bus: Vendor 0 Product 0x6
[  2618.280] (--) evdev: Video Bus: Found keys
[  2618.280] (II) evdev: Video Bus: Configuring as keyboard
[  2618.280] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/LNXVIDEO:01/input/input5/event5"
[  2618.280] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  2618.280] (**) Option "xkb_rules" "evdev"
[  2618.280] (**) Option "xkb_model" "pc105"
[  2618.280] (**) Option "xkb_layout" "no"
[  2618.281] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[  2618.281] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  2618.281] (II) Using input driver 'evdev' for 'Power Button'
[  2618.281] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2618.281] (**) Power Button: always reports core events
[  2618.281] (**) evdev: Power Button: Device: "/dev/input/event0"
[  2618.281] (--) evdev: Power Button: Vendor 0 Product 0x1
[  2618.281] (--) evdev: Power Button: Found keys
[  2618.281] (II) evdev: Power Button: Configuring as keyboard
[  2618.281] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[  2618.281] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[  2618.281] (**) Option "xkb_rules" "evdev"
[  2618.281] (**) Option "xkb_model" "pc105"
[  2618.281] (**) Option "xkb_layout" "no"
[  2618.282] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[  2618.282] (II) No input driver specified, ignoring this device.
[  2618.282] (II) This device may have been added with another device file.
[  2618.282] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[  2618.282] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  2618.282] (II) Using input driver 'evdev' for 'Sleep Button'
[  2618.282] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2618.282] (**) Sleep Button: always reports core events
[  2618.282] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[  2618.282] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[  2618.282] (--) evdev: Sleep Button: Found keys
[  2618.282] (II) evdev: Sleep Button: Configuring as keyboard
[  2618.282] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[  2618.282] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[  2618.282] (**) Option "xkb_rules" "evdev"
[  2618.282] (**) Option "xkb_model" "pc105"
[  2618.282] (**) Option "xkb_layout" "no"
[  2618.283] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event9)
[  2618.283] (II) No input driver specified, ignoring this device.
[  2618.283] (II) This device may have been added with another device file.
[  2618.283] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[  2618.283] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[  2618.283] (II) Using input driver 'evdev' for '1.3M WebCam'
[  2618.283] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2618.283] (**) 1.3M WebCam: always reports core events
[  2618.283] (**) evdev: 1.3M WebCam: Device: "/dev/input/event8"
[  2618.283] (--) evdev: 1.3M WebCam: Vendor 0x402 Product 0x9665
[  2618.283] (--) evdev: 1.3M WebCam: Found keys
[  2618.283] (II) evdev: 1.3M WebCam: Configuring as keyboard
[  2618.283] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input17/event8"
[  2618.283] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[  2618.283] (**) Option "xkb_rules" "evdev"
[  2618.283] (**) Option "xkb_model" "pc105"
[  2618.283] (**) Option "xkb_layout" "no"
[  2618.284] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event6)
[  2618.284] (II) No input driver specified, ignoring this device.
[  2618.284] (II) This device may have been added with another device file.
[  2618.284] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event7)
[  2618.284] (II) No input driver specified, ignoring this device.
[  2618.284] (II) This device may have been added with another device file.
[  2618.285] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[  2618.285] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  2618.285] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  2618.285] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2618.285] (**) AT Translated Set 2 keyboard: always reports core events
[  2618.285] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[  2618.285] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[  2618.285] (--) evdev: AT Translated Set 2 keyboard: Found keys
[  2618.285] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[  2618.285] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[  2618.285] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[  2618.285] (**) Option "xkb_rules" "evdev"
[  2618.285] (**) Option "xkb_model" "pc105"
[  2618.285] (**) Option "xkb_layout" "no"
[  2618.285] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event11)
[  2618.285] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[  2618.285] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[  2618.285] (II) LoadModule: "synaptics"
[  2618.286] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  2618.286] (II) Module synaptics: vendor="X.Org Foundation"
[  2618.286]     compiled for 1.11.3, module version = 1.6.2
[  2618.286]     Module class: X.Org XInput Driver
[  2618.286]     ABI class: X.Org XInput driver, version 16.0
[  2618.286] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[  2618.286] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  2618.286] (**) ETPS/2 Elantech Touchpad: always reports core events
[  2618.286] (**) Option "Device" "/dev/input/event11"
[  2618.288] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[  2618.288] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 1408
[  2618.288] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 640
[  2618.288] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[  2618.288] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[  2618.288] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[  2618.288] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[  2618.288] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  2618.288] (**) ETPS/2 Elantech Touchpad: always reports core events
[  2618.296] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[  2618.296] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[  2618.296] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[  2618.296] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[  2618.296] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.129
[  2618.296] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[  2618.296] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[  2618.296] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[  2618.296] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[  2618.296] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  2618.297] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[  2618.297] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[  2618.298] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event10)
[  2618.298] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[  2618.298] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[  2618.298] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2618.298] (**) Acer WMI hotkeys: always reports core events
[  2618.298] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event10"
[  2618.298] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[  2618.298] (--) evdev: Acer WMI hotkeys: Found keys
[  2618.298] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[  2618.298] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[  2618.299] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[  2618.299] (**) Option "xkb_rules" "evdev"
[  2618.299] (**) Option "xkb_model" "pc105"
[  2618.299] (**) Option "xkb_layout" "no"
[  2618.304] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[  2618.679] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2618.679] (II) fglrx(0): Printing DDC gathered Modelines:
[  2618.679] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2618.783] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2618.783] (II) fglrx(0): Printing DDC gathered Modelines:
[  2618.783] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2623.552] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2623.552] (II) fglrx(0): Printing DDC gathered Modelines:
[  2623.552] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2623.762] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2623.762] (II) fglrx(0): Printing DDC gathered Modelines:
[  2623.762] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2623.876] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2623.876] (II) fglrx(0): Printing DDC gathered Modelines:
[  2623.876] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2626.786] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF9B8E92C8E4E24C73654D7686830142D22482A2.xkm
[  2644.314] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2644.314] (II) fglrx(0): Printing DDC gathered Modelines:
[  2644.314] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
```

Xorg.0.log.old:
```
[     4.470] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     4.470] X Protocol Version 11, Revision 0
[     4.470] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[     4.470] Current Operating System: Linux 5552G 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64
[     4.470] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=a82815eb-9fdb-4303-94b0-595cc4777cc6 ro quiet splash vt.handoff=7
[     4.470] Build Date: 16 July 2012  08:06:31PM
[     4.470] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     4.470] Current version of pixman: 0.24.4
[     4.470]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     4.470] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     4.470] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 18 23:47:41 2012
[     4.471] (==) Using config file: "/etc/X11/xorg.conf"
[     4.471] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     4.474] (==) No Layout section.  Using the first Screen section.
[     4.474] (**) |-->Screen "Default Screen" (0)
[     4.474] (**) |   |-->Monitor "<default monitor>"
[     4.474] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[     4.474] (==) Automatically adding devices
[     4.474] (==) Automatically enabling devices
[     4.476] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     4.476]     Entry deleted from font path.
[     4.476] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     4.476]     Entry deleted from font path.
[     4.476] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     4.476]     Entry deleted from font path.
[     4.476] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     4.476]     Entry deleted from font path.
[     4.476] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     4.476]     Entry deleted from font path.
[     4.476] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     4.476]     Entry deleted from font path.
[     4.476] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     4.476] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     4.476] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     4.476] (II) Loader magic: 0x7f09357d4b00
[     4.476] (II) Module ABI versions:
[     4.476]     X.Org ANSI C Emulation: 0.4
[     4.476]     X.Org Video Driver: 11.0
[     4.476]     X.Org XInput driver : 16.0
[     4.476]     X.Org Server Extension : 6.0
[     4.477] (--) PCI:*(0:1:0:0) 1002:6741:1025:0489 rev 0, Mem @ 0xe0000000/268435456, 0xf2100000/131072, I/O @ 0x00006000/256, BIOS @ 0x????????/131072
[     4.477] (II) Open ACPI successful (/var/run/acpid.socket)
[     4.477] (II) "extmod" will be loaded by default.
[     4.477] (II) "dbe" will be loaded by default.
[     4.477] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[     4.477] (II) "record" will be loaded by default.
[     4.477] (II) "dri" will be loaded by default.
[     4.477] (II) "dri2" will be loaded by default.
[     4.477] (II) LoadModule: "glx"
[     4.480] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[     4.484] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     4.484]     compiled for 6.9.0, module version = 1.0.0
[     4.484] (II) Loading extension GLX
[     4.484] (II) LoadModule: "extmod"
[     4.486] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     4.488] (II) Module extmod: vendor="X.Org Foundation"
[     4.488]     compiled for 1.11.3, module version = 1.0.0
[     4.488]     Module class: X.Org Server Extension
[     4.488]     ABI class: X.Org Server Extension, version 6.0
[     4.488] (II) Loading extension MIT-SCREEN-SAVER
[     4.488] (II) Loading extension XFree86-VidModeExtension
[     4.488] (II) Loading extension XFree86-DGA
[     4.488] (II) Loading extension DPMS
[     4.488] (II) Loading extension XVideo
[     4.488] (II) Loading extension XVideo-MotionCompensation
[     4.488] (II) Loading extension X-Resource
[     4.488] (II) LoadModule: "dbe"
[     4.489] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     4.490] (II) Module dbe: vendor="X.Org Foundation"
[     4.490]     compiled for 1.11.3, module version = 1.0.0
[     4.490]     Module class: X.Org Server Extension
[     4.490]     ABI class: X.Org Server Extension, version 6.0
[     4.490] (II) Loading extension DOUBLE-BUFFER
[     4.490] (II) LoadModule: "record"
[     4.490] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     4.492] (II) Module record: vendor="X.Org Foundation"
[     4.492]     compiled for 1.11.3, module version = 1.13.0
[     4.492]     Module class: X.Org Server Extension
[     4.492]     ABI class: X.Org Server Extension, version 6.0
[     4.492] (II) Loading extension RECORD
[     4.492] (II) LoadModule: "dri"
[     4.492] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     4.494] (II) Module dri: vendor="X.Org Foundation"
[     4.494]     compiled for 1.11.3, module version = 1.0.0
[     4.494]     ABI class: X.Org Server Extension, version 6.0
[     4.494] (II) Loading extension XFree86-DRI
[     4.494] (II) LoadModule: "dri2"
[     4.494] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     4.495] (II) Module dri2: vendor="X.Org Foundation"
[     4.495]     compiled for 1.11.3, module version = 1.2.0
[     4.495]     ABI class: X.Org Server Extension, version 6.0
[     4.495] (II) Loading extension DRI2
[     4.495] (==) Matched fglrx as autoconfigured driver 0
[     4.495] (==) Matched ati as autoconfigured driver 1
[     4.495] (==) Matched vesa as autoconfigured driver 2
[     4.495] (==) Matched fbdev as autoconfigured driver 3
[     4.495] (==) Assigned the driver to the xf86ConfigLayout
[     4.495] (II) LoadModule: "fglrx"
[     4.495] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     4.571] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[     4.571]     compiled for 1.4.99.906, module version = 8.96.4
[     4.571]     Module class: X.Org Video Driver
[     4.572] (II) Loading sub module "fglrxdrm"
[     4.572] (II) LoadModule: "fglrxdrm"
[     4.572] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     4.574] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     4.574]     compiled for 1.4.99.906, module version = 8.96.4
[     4.575] (II) LoadModule: "ati"
[     4.575] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     4.576] (II) Module ati: vendor="X.Org Foundation"
[     4.576]     compiled for 1.11.3, module version = 6.14.99
[     4.576]     Module class: X.Org Video Driver
[     4.576]     ABI class: X.Org Video Driver, version 11.0
[     4.576] (II) LoadModule: "radeon"
[     4.576] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     4.581] (II) Module radeon: vendor="X.Org Foundation"
[     4.581]     compiled for 1.11.3, module version = 6.14.99
[     4.581]     Module class: X.Org Video Driver
[     4.581]     ABI class: X.Org Video Driver, version 11.0
[     4.581] (II) LoadModule: "vesa"
[     4.582] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     4.583] (II) Module vesa: vendor="X.Org Foundation"
[     4.583]     compiled for 1.11.3, module version = 2.3.0
[     4.583]     Module class: X.Org Video Driver
[     4.583]     ABI class: X.Org Video Driver, version 11.0
[     4.583] (II) LoadModule: "fbdev"
[     4.583] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     4.584] (II) Module fbdev: vendor="X.Org Foundation"
[     4.584]     compiled for 1.11.3, module version = 0.4.2
[     4.584]     ABI class: X.Org Video Driver, version 11.0
[     4.584] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[     4.584] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[     4.584] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:50
[     4.584] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
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
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[     4.587] (II) VESA: driver for VESA chipsets: vesa
[     4.587] (II) FBDEV: driver for framebuffer: fbdev
[     4.587] (++) using VT number 7

[     4.587] (WW) Falling back to old probe method for fglrx
[     4.600] (II) Loading PCS database from /etc/ati/amdpcsdb
[     4.602] (--) Assigning device section with no busID to primary device
[     4.602] (--) Chipset Supported AMD Graphics Processor (0x6741) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[     4.603] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     4.604] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[     4.604] (II) AMD Video driver is signed
[     4.604] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     4.604] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     4.604] (II) fglrx(0): pEnt->device->identifier=0x7f093558752f
[     4.604] (WW) Falling back to old probe method for vesa
[     4.604] (WW) Falling back to old probe method for fbdev
[     4.604] (II) Loading sub module "fbdevhw"
[     4.604] (II) LoadModule: "fbdevhw"
[     4.605] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     4.606] (II) Module fbdevhw: vendor="X.Org Foundation"
[     4.606]     compiled for 1.11.3, module version = 0.0.2
[     4.606]     ABI class: X.Org Video Driver, version 11.0
[     4.606] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[     4.606] (II) Loading sub module "vgahw"
[     4.606] (II) LoadModule: "vgahw"
[     4.606] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     4.607] (II) Module vgahw: vendor="X.Org Foundation"
[     4.607]     compiled for 1.11.3, module version = 0.1.0
[     4.607]     ABI class: X.Org Video Driver, version 11.0
[     4.607] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[     4.607] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     4.607] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     4.607] (==) fglrx(0): Default visual is TrueColor
[     4.607] (==) fglrx(0): RGB weight 888
[     4.607] (II) fglrx(0): Using 8 bits per RGB 
[     4.607] (==) fglrx(0): Buffer Tiling is ON
[     4.608] (II) Loading sub module "fglrxdrm"
[     4.608] (II) LoadModule: "fglrxdrm"
[     4.608] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     4.608] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     4.608]     compiled for 1.4.99.906, module version = 8.96.4
[     4.610] ukiDynamicMajor: found major device number 251
[     4.610] ukiDynamicMajor: found major device number 251
[     4.610] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     4.610] ukiOpenDevice: node name is /dev/ati/card0
[     4.610] ukiOpenDevice: open result is 12, (OK)
[     4.610] ukiOpenByBusid: ukiOpenMinor returns 12
[     4.610] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     4.610] (**) fglrx(0): NoAccel = NO
[     4.610] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[     4.610] (--) fglrx(0): Chipset: "AMD Radeon 6600M and 6700M Series" (Chipset = 0x6741)
[     4.610] (--) fglrx(0): (PciSubVendor = 0x1025, PciSubDevice = 0x0489)
[     4.610] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[     4.610] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     4.610] (--) fglrx(0): MMIO registers at 0xf2100000
[     4.610] (--) fglrx(0): I/O port at 0x00006000
[     4.610] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     4.692] (II) fglrx(0): ATIF platform detected
[     4.696] (II) fglrx(0): AC Adapter is used
[     4.706] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     4.708] (II) Loading sub module "vbe"
[     4.708] (II) LoadModule: "vbe"
[     4.709] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     4.709] (II) Module vbe: vendor="X.Org Foundation"
[     4.710]     compiled for 1.11.3, module version = 1.1.0
[     4.710]     ABI class: X.Org Video Driver, version 11.0
[     4.710] (II) fglrx(0): VESA BIOS detected
[     4.710] (II) fglrx(0): VESA VBE Version 3.0
[     4.710] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     4.710] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[     4.710] (II) fglrx(0): VESA VBE OEM Software Rev: 13.7
[     4.710] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[     4.710] (II) fglrx(0): VESA VBE OEM Product: WHISTLER
[     4.710] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     4.746] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[     4.746] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[     4.746] (II) fglrx(0): PCIE card detected
[     4.746] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     4.746] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     4.754] (II) fglrx(0): Using adapter: 1:0.0.
[     4.796] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[     4.809] (II) fglrx(0): Interrupt handler installed at IRQ 46.
[     4.809] (II) fglrx(0): RandR 1.2 support is enabled!
[     4.809] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     4.809] (==) fglrx(0): Center Mode is disabled 
[     4.809] (II) Loading sub module "fb"
[     4.809] (II) LoadModule: "fb"
[     4.810] (II) Loading /usr/lib/xorg/modules/libfb.so
[     4.811] (II) Module fb: vendor="X.Org Foundation"
[     4.811]     compiled for 1.11.3, module version = 1.0.0
[     4.811]     ABI class: X.Org ANSI C Emulation, version 0.4
[     4.811] (II) Loading sub module "ddc"
[     4.811] (II) LoadModule: "ddc"
[     4.811] (II) Module "ddc" already built-in
[     4.964] (II) fglrx(0): Finished Initialize PPLIB!
[     4.966] (II) fglrx(0): Output LVDS has no monitor section
[     4.966] (II) fglrx(0): Output DFP1 has no monitor section
[     4.966] (II) fglrx(0): Output CRT1 has no monitor section
[     4.966] (II) Loading sub module "ddc"
[     4.966] (II) LoadModule: "ddc"
[     4.966] (II) Module "ddc" already built-in
[     4.966] (II) fglrx(0): Connected Display0: LVDS
[     4.966] (II) fglrx(0): Display0 EDID data ---------------------------
[     4.966] (II) fglrx(0): Manufacturer: LGD  Model: 250  Serial#: 0
[     4.966] (II) fglrx(0): Year: 2010  Week: 0
[     4.966] (II) fglrx(0): EDID Version: 1.3
[     4.966] (II) fglrx(0): Digital Display Input
[     4.966] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[     4.966] (II) fglrx(0): Gamma: 2.20
[     4.966] (II) fglrx(0): No DPMS capabilities specified
[     4.966] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     4.966] (II) fglrx(0): First detailed timing is preferred mode
[     4.966] (II) fglrx(0): redX: 0.612 redY: 0.375   greenX: 0.332 greenY: 0.619
[     4.966] (II) fglrx(0): blueX: 0.151 blueY: 0.099   whiteX: 0.313 whiteY: 0.329
[     4.966] (II) fglrx(0): Manufacturer's mask: 0
[     4.966] (II) fglrx(0): Supported detailed timing:
[     4.966] (II) fglrx(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[     4.967] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[     4.967] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[     4.967] (II) fglrx(0):  LG Display
[     4.967] (II) fglrx(0):  LP156WH2-TLEA
[     4.967] (II) fglrx(0): EDID (in hex):
[     4.967] (II) fglrx(0):     00ffffffffffff0030e4500200000000
[     4.967] (II) fglrx(0):     00140103802313780ac2d59c60559e26
[     4.967] (II) fglrx(0):     19505400000001010101010101010101
[     4.967] (II) fglrx(0):     0101010101013e1c56a0500016303020
[     4.967] (II) fglrx(0):     350059c2100000190000000000000000
[     4.967] (II) fglrx(0):     00000000000000000000000000fe004c
[     4.967] (II) fglrx(0):     4720446973706c61790a2020000000fe
[     4.967] (II) fglrx(0):     004c503135365748322d544c454100fd
[     4.967] (II) fglrx(0): End of Display0 EDID data --------------------
[     4.967] (II) fglrx(0): EDID for output LVDS
[     4.967] (II) fglrx(0): Manufacturer: LGD  Model: 250  Serial#: 0
[     4.967] (II) fglrx(0): Year: 2010  Week: 0
[     4.967] (II) fglrx(0): EDID Version: 1.3
[     4.967] (II) fglrx(0): Digital Display Input
[     4.967] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[     4.967] (II) fglrx(0): Gamma: 2.20
[     4.967] (II) fglrx(0): No DPMS capabilities specified
[     4.967] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[     4.967] (II) fglrx(0): First detailed timing is preferred mode
[     4.967] (II) fglrx(0): redX: 0.612 redY: 0.375   greenX: 0.332 greenY: 0.619
[     4.967] (II) fglrx(0): blueX: 0.151 blueY: 0.099   whiteX: 0.313 whiteY: 0.329
[     4.967] (II) fglrx(0): Manufacturer's mask: 0
[     4.967] (II) fglrx(0): Supported detailed timing:
[     4.967] (II) fglrx(0): clock: 72.3 MHz   Image Size:  345 x 194 mm
[     4.967] (II) fglrx(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[     4.967] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[     4.967] (II) fglrx(0):  LG Display
[     4.968] (II) fglrx(0):  LP156WH2-TLEA
[     4.968] (II) fglrx(0): EDID (in hex):
[     4.968] (II) fglrx(0):     00ffffffffffff0030e4500200000000
[     4.968] (II) fglrx(0):     00140103802313780ac2d59c60559e26
[     4.968] (II) fglrx(0):     19505400000001010101010101010101
[     4.968] (II) fglrx(0):     0101010101013e1c56a0500016303020
[     4.968] (II) fglrx(0):     350059c2100000190000000000000000
[     4.968] (II) fglrx(0):     00000000000000000000000000fe004c
[     4.968] (II) fglrx(0):     4720446973706c61790a2020000000fe
[     4.968] (II) fglrx(0):     004c503135365748322d544c454100fd
[     4.968] (II) fglrx(0): EDID vendor "LGD", prod id 592
[     4.968] (II) fglrx(0): Printing DDC gathered Modelines:
[     4.968] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Printing probed modes for output LVDS
[     4.968] (II) fglrx(0): Modeline "1366x768"x60.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Modeline "1360x768"x60.0   72.30  1360 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Modeline "1280x768"x60.0   72.30  1280 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Modeline "1280x720"x60.0   72.30  1280 1414 1446 1526  720 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Modeline "1024x768"x60.0   72.30  1024 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Modeline "1024x600"x60.0   72.30  1024 1414 1446 1526  600 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Modeline "800x600"x60.0   72.30  800 1414 1446 1526  600 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Modeline "800x480"x60.0   72.30  800 1414 1446 1526  480 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): Modeline "640x480"x60.0   72.30  640 1414 1446 1526  480 771 776 790 -hsync -vsync (47.4 kHz)
[     4.968] (II) fglrx(0): EDID for output DFP1
[     4.968] (II) fglrx(0): EDID for output CRT1
[     4.968] (II) fglrx(0): Output LVDS connected
[     4.968] (II) fglrx(0): Output DFP1 disconnected
[     4.968] (II) fglrx(0): Output CRT1 disconnected
[     4.968] (II) fglrx(0): Using exact sizes for initial modes
[     4.968] (II) fglrx(0): Output LVDS using initial mode 1366x768
[     4.968] (II) fglrx(0): Display dimensions: (350, 190) mm
[     4.968] (II) fglrx(0): DPI set to (99, 102)
[     4.968] (II) fglrx(0): Eyefinity capable adapter detected.
[     4.968] (II) fglrx(0): Adapter AMD Radeon 6600M and 6700M Series has 6 configurable heads and 1 displays connected.
[     4.968] (==) fglrx(0):  PseudoColor visuals disabled
[     4.968] (II) Loading sub module "ramdac"
[     4.968] (II) LoadModule: "ramdac"
[     4.968] (II) Module "ramdac" already built-in
[     4.968] (==) fglrx(0): NoDRI = NO
[     4.968] (==) fglrx(0): Capabilities: 0x00000000
[     4.968] (==) fglrx(0): CapabilitiesEx: 0x00000000
[     4.968] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[     4.968] (==) fglrx(0): UseFastTLS=0
[     4.968] (==) fglrx(0): BlockSignalsOnLock=1
[     4.968] (II) UnloadModule: "radeon"
[     4.968] (II) Unloading radeon
[     4.968] (II) UnloadModule: "vesa"
[     4.968] (II) Unloading vesa
[     4.968] (II) UnloadModule: "fbdev"
[     4.968] (II) Unloading fbdev
[     4.968] (II) UnloadModule: "fbdevhw"
[     4.968] (II) Unloading fbdevhw
[     4.968] (--) Depth 24 pixmap format is 32 bpp
[     4.969] (II) Loading extension ATIFGLRXDRI
[     4.969] (II) fglrx(0): doing swlDriScreenInit
[     4.969] (II) fglrx(0): swlDriScreenInit for fglrx driver
[     4.969] ukiDynamicMajor: found major device number 251
[     4.969] ukiDynamicMajor: found major device number 251
[     4.969] ukiDynamicMajor: found major device number 251
[     4.969] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     4.969] ukiOpenDevice: node name is /dev/ati/card0
[     4.969] ukiOpenDevice: open result is 17, (OK)
[     4.969] ukiOpenByBusid: ukiOpenMinor returns 17
[     4.969] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     4.969] (II) fglrx(0): [uki] DRM interface version 1.0
[     4.969] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[     4.969] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[     4.969] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f09353c5000
[     4.969] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[     4.969] (II) fglrx(0): [uki] added 1 reserved context for kernel
[     4.969] (II) fglrx(0): swlDriScreenInit done
[     4.969] (II) fglrx(0): Kernel Module Version Information:
[     4.969] (II) fglrx(0):     Name: fglrx
[     4.969] (II) fglrx(0):     Version: 8.96.4
[     4.969] (II) fglrx(0):     Date: Mar 12 2012
[     4.969] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[     4.969] (II) fglrx(0): Kernel Module version matches driver.
[     4.969] (II) fglrx(0): Kernel Module Build Time Information:
[     4.969] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-26-generic
[     4.969] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[     4.969] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[     4.969] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[     4.969] (II) fglrx(0): [uki] register handle = 0x00004000
[     4.993] (II) fglrx(0): DRI initialization successfull
[     4.994] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01004000
[     4.995] (==) fglrx(0): Backing store disabled
[     4.995] (II) Loading extension FGLRXEXTENSION
[     4.996] (==) fglrx(0): DPMS enabled
[     4.996] (II) fglrx(0): Initialized in-driver Xinerama extension
[     4.996] (**) fglrx(0): Textured Video is enabled.
[     4.996] (II) LoadModule: "glesx"
[     4.996] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[     5.012] (II) Module glesx: vendor="X.Org Foundation"
[     5.012]     compiled for 1.4.99.906, module version = 1.0.0
[     5.012] (II) Loading extension GLESX
[     5.012] (II) fglrx(0): GLESX enableFlags = 592
[     5.013] (II) fglrx(0): GLESX is enabled
[     5.013] (II) LoadModule: "amdxmm"
[     5.013] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[     5.015] (II) Module amdxmm: vendor="X.Org Foundation"
[     5.015]     compiled for 1.4.99.906, module version = 2.0.0
[     5.024] (II) Loading extension AMDXVOPL
[     5.024] (II) Loading extension AMDXVBA
[     5.027] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[     5.030] (II) fglrx(0): Enable composite support successfully
[     5.030] (II) fglrx(0): X context handle = 0x1
[     5.030] (II) fglrx(0): [DRI] installation complete
[     5.030] (==) fglrx(0): Silken mouse enabled
[     5.030] (==) fglrx(0): Using HW cursor of display infrastructure!
[     5.031] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[     5.031] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[     5.031] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[     5.450] (--) RandR disabled
[     5.450] (II) Initializing built-in extension Generic Event Extension
[     5.450] (II) Initializing built-in extension SHAPE
[     5.450] (II) Initializing built-in extension MIT-SHM
[     5.450] (II) Initializing built-in extension XInputExtension
[     5.450] (II) Initializing built-in extension XTEST
[     5.450] (II) Initializing built-in extension BIG-REQUESTS
[     5.450] (II) Initializing built-in extension SYNC
[     5.450] (II) Initializing built-in extension XKEYBOARD
[     5.450] (II) Initializing built-in extension XC-MISC
[     5.450] (II) Initializing built-in extension SECURITY
[     5.450] (II) Initializing built-in extension XINERAMA
[     5.450] (II) Initializing built-in extension XFIXES
[     5.450] (II) Initializing built-in extension RENDER
[     5.450] (II) Initializing built-in extension RANDR
[     5.450] (II) Initializing built-in extension COMPOSITE
[     5.450] (II) Initializing built-in extension DAMAGE
[     5.482] ukiDynamicMajor: found major device number 251
[     5.482] ukiDynamicMajor: found major device number 251
[     5.482] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     5.482] ukiOpenDevice: node name is /dev/ati/card0
[     5.482] ukiOpenDevice: open result is 19, (OK)
[     5.482] ukiOpenByBusid: ukiOpenMinor returns 19
[     5.482] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     5.696] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[     5.696] (II) fglrx(0): Enable the clock gating!
[     5.696] (II) fglrx(0): Setting screen physical size to 361 x 203
[     5.711] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     5.714] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     5.714] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.714] (II) LoadModule: "evdev"
[     5.715] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.717] (II) Module evdev: vendor="X.Org Foundation"
[     5.717]     compiled for 1.11.3, module version = 2.7.0
[     5.717]     Module class: X.Org XInput Driver
[     5.717]     ABI class: X.Org XInput driver, version 16.0
[     5.717] (II) Using input driver 'evdev' for 'Power Button'
[     5.717] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.717] (**) Power Button: always reports core events
[     5.717] (**) evdev: Power Button: Device: "/dev/input/event3"
[     5.717] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.717] (--) evdev: Power Button: Found keys
[     5.717] (II) evdev: Power Button: Configuring as keyboard
[     5.717] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     5.717] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     5.718] (**) Option "xkb_rules" "evdev"
[     5.718] (**) Option "xkb_model" "pc105"
[     5.718] (**) Option "xkb_layout" "no"
[     5.719] (II) XKB: reuse xkmfile /var/lib/xkb/server-5F8E417E6ED2D276BE32A8CA0E3DB916C21A8CA2.xkm
[     5.721] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     5.721] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     5.721] (II) Using input driver 'evdev' for 'Video Bus'
[     5.721] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.721] (**) Video Bus: always reports core events
[     5.721] (**) evdev: Video Bus: Device: "/dev/input/event5"
[     5.721] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     5.721] (--) evdev: Video Bus: Found keys
[     5.721] (II) evdev: Video Bus: Configuring as keyboard
[     5.721] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/LNXVIDEO:01/input/input5/event5"
[     5.721] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     5.721] (**) Option "xkb_rules" "evdev"
[     5.721] (**) Option "xkb_model" "pc105"
[     5.721] (**) Option "xkb_layout" "no"
[     5.722] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     5.722] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     5.722] (II) Using input driver 'evdev' for 'Power Button'
[     5.722] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.722] (**) Power Button: always reports core events
[     5.722] (**) evdev: Power Button: Device: "/dev/input/event0"
[     5.722] (--) evdev: Power Button: Vendor 0 Product 0x1
[     5.722] (--) evdev: Power Button: Found keys
[     5.722] (II) evdev: Power Button: Configuring as keyboard
[     5.722] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     5.722] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     5.722] (**) Option "xkb_rules" "evdev"
[     5.722] (**) Option "xkb_model" "pc105"
[     5.722] (**) Option "xkb_layout" "no"
[     5.722] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[     5.722] (II) No input driver specified, ignoring this device.
[     5.722] (II) This device may have been added with another device file.
[     5.723] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     5.723] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     5.723] (II) Using input driver 'evdev' for 'Sleep Button'
[     5.723] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.723] (**) Sleep Button: always reports core events
[     5.723] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[     5.723] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     5.723] (--) evdev: Sleep Button: Found keys
[     5.723] (II) evdev: Sleep Button: Configuring as keyboard
[     5.723] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[     5.723] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     5.723] (**) Option "xkb_rules" "evdev"
[     5.723] (**) Option "xkb_model" "pc105"
[     5.723] (**) Option "xkb_layout" "no"
[     5.723] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event9)
[     5.724] (II) No input driver specified, ignoring this device.
[     5.724] (II) This device may have been added with another device file.
[     5.724] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[     5.724] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[     5.724] (II) Using input driver 'evdev' for '1.3M WebCam'
[     5.724] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.724] (**) 1.3M WebCam: always reports core events
[     5.724] (**) evdev: 1.3M WebCam: Device: "/dev/input/event8"
[     5.724] (--) evdev: 1.3M WebCam: Vendor 0x402 Product 0x9665
[     5.724] (--) evdev: 1.3M WebCam: Found keys
[     5.724] (II) evdev: 1.3M WebCam: Configuring as keyboard
[     5.724] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input8/event8"
[     5.724] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[     5.724] (**) Option "xkb_rules" "evdev"
[     5.724] (**) Option "xkb_model" "pc105"
[     5.724] (**) Option "xkb_layout" "no"
[     5.725] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event6)
[     5.725] (II) No input driver specified, ignoring this device.
[     5.725] (II) This device may have been added with another device file.
[     5.725] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event7)
[     5.725] (II) No input driver specified, ignoring this device.
[     5.725] (II) This device may have been added with another device file.
[     5.725] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     5.725] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     5.725] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     5.725] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.725] (**) AT Translated Set 2 keyboard: always reports core events
[     5.725] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     5.725] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     5.725] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     5.725] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     5.725] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     5.725] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[     5.725] (**) Option "xkb_rules" "evdev"
[     5.725] (**) Option "xkb_model" "pc105"
[     5.725] (**) Option "xkb_layout" "no"
[     5.728] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event10)
[     5.728] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     5.728] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[     5.728] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     5.728] (**) Acer WMI hotkeys: always reports core events
[     5.728] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event10"
[     5.728] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[     5.728] (--) evdev: Acer WMI hotkeys: Found keys
[     5.728] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[     5.728] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[     5.728] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 12)
[     5.728] (**) Option "xkb_rules" "evdev"
[     5.728] (**) Option "xkb_model" "pc105"
[     5.728] (**) Option "xkb_layout" "no"
[     5.755] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[     6.092] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[     6.092] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[     6.092] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event11)
[     6.093] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[     6.093] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[     6.093] (II) LoadModule: "synaptics"
[     6.093] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.094] (II) Module synaptics: vendor="X.Org Foundation"
[     6.094]     compiled for 1.11.3, module version = 1.6.2
[     6.094]     Module class: X.Org XInput Driver
[     6.094]     ABI class: X.Org XInput driver, version 16.0
[     6.094] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[     6.094] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.094] (**) ETPS/2 Elantech Touchpad: always reports core events
[     6.094] (**) Option "Device" "/dev/input/event11"
[     6.152] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[     6.152] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 1408
[     6.152] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 640
[     6.152] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[     6.152] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[     6.152] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[     6.152] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[     6.152] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     6.152] (**) ETPS/2 Elantech Touchpad: always reports core events
[     6.184] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[     6.184] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 13)
[     6.184] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[     6.184] (**) synaptics: ETPS/2 Elantech Touchpad: MaxSpeed is now 1.75
[     6.184] (**) synaptics: ETPS/2 Elantech Touchpad: AccelFactor is now 0.129
[     6.184] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[     6.184] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[     6.184] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[     6.184] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[     6.184] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[     6.306] (II) fglrx(0): EDID vendor "LGD", prod id 592
[     6.306] (II) fglrx(0): Printing DDC gathered Modelines:
[     6.306] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[     7.074] (II) fglrx(0): EDID vendor "LGD", prod id 592
[     7.074] (II) fglrx(0): Printing DDC gathered Modelines:
[     7.074] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    16.571] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    16.571] (II) fglrx(0): Printing DDC gathered Modelines:
[    16.571] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    16.986] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    16.986] (II) fglrx(0): Printing DDC gathered Modelines:
[    16.986] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    17.391] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    17.391] (II) fglrx(0): Printing DDC gathered Modelines:
[    17.391] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    20.611] (II) XKB: reuse xkmfile /var/lib/xkb/server-CF9B8E92C8E4E24C73654D7686830142D22482A2.xkm
[    37.456] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    37.456] (II) fglrx(0): Printing DDC gathered Modelines:
[    37.456] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    43.996] (II) fglrx(0): Lid Close Received
[    44.018] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    44.018] (II) fglrx(0): Printing DDC gathered Modelines:
[    44.018] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[    47.296] (II) AIGLX: Suspending AIGLX clients for VT switch
[    47.297] (II) fglrx(0): Backup framebuffer data.
[    47.342] (II) fglrx(0): Backup complete.
[    51.553] (II) config/udev: removing device 1.3M WebCam
[    51.553] (II) evdev: 1.3M WebCam: Close
[    51.553] (II) UnloadModule: "evdev"
[    51.553] (II) Unloading evdev
[    51.652] (II) AIGLX: Resuming AIGLX clients after VT switch
[    51.656] (II) fglrx(0): Restore framebuffer data.
[    51.706] (II) fglrx(0): Restore complete.
[    51.728] (II) fglrx(0): AC Adapter is used
[    51.821] (II) fglrx(0): Lid Open Received
[    51.845] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    51.958] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[    51.958] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[    51.958] (II) Using input driver 'evdev' for '1.3M WebCam'
[    51.958] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    51.958] (**) 1.3M WebCam: always reports core events
[    51.958] (**) evdev: 1.3M WebCam: Device: "/dev/input/event8"
[    51.958] (--) evdev: 1.3M WebCam: Vendor 0x402 Product 0x9665
[    51.958] (--) evdev: 1.3M WebCam: Found keys
[    51.958] (II) evdev: 1.3M WebCam: Configuring as keyboard
[    51.958] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input12/event8"
[    51.958] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[    51.958] (**) Option "xkb_rules" "evdev"
[    51.958] (**) Option "xkb_model" "pc105"
[    51.958] (**) Option "xkb_layout" "no"
[    53.972] (II) fglrx(0): EDID vendor "LGD", prod id 592
[    53.972] (II) fglrx(0): Printing DDC gathered Modelines:
[    53.972] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   294.457] (II) fglrx(0): Lid Close Received
[   294.487] (II) fglrx(0): EDID vendor "LGD", prod id 592
[   294.488] (II) fglrx(0): Printing DDC gathered Modelines:
[   294.488] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   297.060] (II) AIGLX: Suspending AIGLX clients for VT switch
[   297.061] (II) fglrx(0): Backup framebuffer data.
[   297.106] (II) fglrx(0): Backup complete.
[   301.360] (II) config/udev: removing device 1.3M WebCam
[   301.360] (II) evdev: 1.3M WebCam: Close
[   301.360] (II) UnloadModule: "evdev"
[   301.360] (II) Unloading evdev
[   301.437] (II) AIGLX: Resuming AIGLX clients after VT switch
[   301.444] (II) fglrx(0): Restore framebuffer data.
[   301.483] (II) fglrx(0): Restore complete.
[   301.489] (II) fglrx(0): AC Adapter is used
[   301.564] (II) fglrx(0): Lid Open Received
[   301.594] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   301.751] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[   301.751] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[   301.752] (II) Using input driver 'evdev' for '1.3M WebCam'
[   301.752] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   301.752] (**) 1.3M WebCam: always reports core events
[   301.752] (**) evdev: 1.3M WebCam: Device: "/dev/input/event8"
[   301.752] (--) evdev: 1.3M WebCam: Vendor 0x402 Product 0x9665
[   301.752] (--) evdev: 1.3M WebCam: Found keys
[   301.752] (II) evdev: 1.3M WebCam: Configuring as keyboard
[   301.752] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input13/event8"
[   301.752] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[   301.752] (**) Option "xkb_rules" "evdev"
[   301.752] (**) Option "xkb_model" "pc105"
[   301.752] (**) Option "xkb_layout" "no"
[   304.752] (II) fglrx(0): EDID vendor "LGD", prod id 592
[   304.752] (II) fglrx(0): Printing DDC gathered Modelines:
[   304.752] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   383.996] (II) fglrx(0): Lid Close Received
[   384.018] (II) fglrx(0): EDID vendor "LGD", prod id 592
[   384.018] (II) fglrx(0): Printing DDC gathered Modelines:
[   384.018] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   386.380] (II) AIGLX: Suspending AIGLX clients for VT switch
[   386.381] (II) fglrx(0): Backup framebuffer data.
[   386.425] (II) fglrx(0): Backup complete.
[   390.628] (II) config/udev: removing device 1.3M WebCam
[   390.629] (II) evdev: 1.3M WebCam: Close
[   390.629] (II) UnloadModule: "evdev"
[   390.629] (II) Unloading evdev
[   390.723] (II) AIGLX: Resuming AIGLX clients after VT switch
[   390.732] (II) fglrx(0): Restore framebuffer data.
[   390.769] (II) fglrx(0): Restore complete.
[   390.776] (II) fglrx(0): Battery is used
[   390.842] (II) fglrx(0): AC Offline
[   390.864] (II) fglrx(0): Lid Open Received
[   390.890] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[   391.049] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[   391.049] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[   391.049] (II) Using input driver 'evdev' for '1.3M WebCam'
[   391.049] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   391.049] (**) 1.3M WebCam: always reports core events
[   391.049] (**) evdev: 1.3M WebCam: Device: "/dev/input/event8"
[   391.049] (--) evdev: 1.3M WebCam: Vendor 0x402 Product 0x9665
[   391.049] (--) evdev: 1.3M WebCam: Found keys
[   391.050] (II) evdev: 1.3M WebCam: Configuring as keyboard
[   391.050] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input14/event8"
[   391.050] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[   391.050] (**) Option "xkb_rules" "evdev"
[   391.050] (**) Option "xkb_model" "pc105"
[   391.050] (**) Option "xkb_layout" "no"
[   394.047] (II) fglrx(0): EDID vendor "LGD", prod id 592
[   394.047] (II) fglrx(0): Printing DDC gathered Modelines:
[   394.047] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[   629.840] (II) fglrx(0): AC Online
[  1985.201] (II) fglrx(0): Lid Close Received
[  1985.222] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  1985.222] (II) fglrx(0): Printing DDC gathered Modelines:
[  1985.222] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  1987.848] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1987.849] (II) fglrx(0): Backup framebuffer data.
[  1987.899] (II) fglrx(0): Backup complete.
[  1992.085] (II) config/udev: removing device 1.3M WebCam
[  1992.086] (II) evdev: 1.3M WebCam: Close
[  1992.086] (II) UnloadModule: "evdev"
[  1992.086] (II) Unloading evdev
[  1992.194] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1992.204] (II) fglrx(0): Restore framebuffer data.
[  1992.250] (II) fglrx(0): Restore complete.
[  1992.272] (II) fglrx(0): AC Adapter is used
[  1992.380] (II) fglrx(0): Lid Open Received
[  1992.422] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  1992.521] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[  1992.521] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[  1992.521] (II) Using input driver 'evdev' for '1.3M WebCam'
[  1992.521] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1992.521] (**) 1.3M WebCam: always reports core events
[  1992.521] (**) evdev: 1.3M WebCam: Device: "/dev/input/event8"
[  1992.521] (--) evdev: 1.3M WebCam: Vendor 0x402 Product 0x9665
[  1992.521] (--) evdev: 1.3M WebCam: Found keys
[  1992.521] (II) evdev: 1.3M WebCam: Configuring as keyboard
[  1992.521] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input15/event8"
[  1992.521] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[  1992.521] (**) Option "xkb_rules" "evdev"
[  1992.521] (**) Option "xkb_model" "pc105"
[  1992.521] (**) Option "xkb_layout" "no"
[  1995.580] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  1995.580] (II) fglrx(0): Printing DDC gathered Modelines:
[  1995.580] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2114.220] (II) fglrx(0): Lid Close Received
[  2114.243] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2114.243] (II) fglrx(0): Printing DDC gathered Modelines:
[  2114.243] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2116.819] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2116.820] (II) fglrx(0): Backup framebuffer data.
[  2116.867] (II) fglrx(0): Backup complete.
[  2121.086] (II) config/udev: removing device 1.3M WebCam
[  2121.087] (II) evdev: 1.3M WebCam: Close
[  2121.087] (II) UnloadModule: "evdev"
[  2121.087] (II) Unloading evdev
[  2121.140] (II) AIGLX: Resuming AIGLX clients after VT switch
[  2121.144] (II) fglrx(0): Restore framebuffer data.
[  2121.195] (II) fglrx(0): Restore complete.
[  2121.212] (II) fglrx(0): AC Adapter is used
[  2121.287] (II) fglrx(0): Lid Open Received
[  2121.319] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  2121.473] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[  2121.473] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[  2121.473] (II) Using input driver 'evdev' for '1.3M WebCam'
[  2121.473] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2121.473] (**) 1.3M WebCam: always reports core events
[  2121.473] (**) evdev: 1.3M WebCam: Device: "/dev/input/event8"
[  2121.473] (--) evdev: 1.3M WebCam: Vendor 0x402 Product 0x9665
[  2121.473] (--) evdev: 1.3M WebCam: Found keys
[  2121.473] (II) evdev: 1.3M WebCam: Configuring as keyboard
[  2121.473] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input16/event8"
[  2121.473] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[  2121.473] (**) Option "xkb_rules" "evdev"
[  2121.473] (**) Option "xkb_model" "pc105"
[  2121.473] (**) Option "xkb_layout" "no"
[  2124.079] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2124.079] (II) fglrx(0): Printing DDC gathered Modelines:
[  2124.079] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2598.180] (II) fglrx(0): Lid Close Received
[  2598.201] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2598.201] (II) fglrx(0): Printing DDC gathered Modelines:
[  2598.201] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2598.682] [mi] Increasing EQ size to 512 to prevent dropped events.
[  2600.820] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2600.821] (II) fglrx(0): Backup framebuffer data.
[  2600.869] (II) fglrx(0): Backup complete.
[  2605.105] (II) config/udev: removing device 1.3M WebCam
[  2605.106] (II) evdev: 1.3M WebCam: Close
[  2605.106] (II) UnloadModule: "evdev"
[  2605.106] (II) Unloading evdev
[  2605.235] (II) AIGLX: Resuming AIGLX clients after VT switch
[  2605.240] (II) fglrx(0): Restore framebuffer data.
[  2605.315] (II) fglrx(0): Restore complete.
[  2605.348] (II) fglrx(0): AC Adapter is used
[  2605.503] (II) fglrx(0): Lid Open Received
[  2605.561] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[  2605.563] (II) config/udev: Adding input device 1.3M WebCam (/dev/input/event8)
[  2605.563] (**) 1.3M WebCam: Applying InputClass "evdev keyboard catchall"
[  2605.563] (II) Using input driver 'evdev' for '1.3M WebCam'
[  2605.563] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  2605.563] (**) 1.3M WebCam: always reports core events
[  2605.563] (**) evdev: 1.3M WebCam: Device: "/dev/input/event8"
[  2605.563] (--) evdev: 1.3M WebCam: Vendor 0x402 Product 0x9665
[  2605.563] (--) evdev: 1.3M WebCam: Found keys
[  2605.563] (II) evdev: 1.3M WebCam: Configuring as keyboard
[  2605.563] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input17/event8"
[  2605.563] (II) XINPUT: Adding extended input device "1.3M WebCam" (type: KEYBOARD, id 10)
[  2605.563] (**) Option "xkb_rules" "evdev"
[  2605.563] (**) Option "xkb_model" "pc105"
[  2605.563] (**) Option "xkb_layout" "no"
[  2608.479] (II) fglrx(0): EDID vendor "LGD", prod id 592
[  2608.479] (II) fglrx(0): Printing DDC gathered Modelines:
[  2608.479] (II) fglrx(0): Modeline "1366x768"x0.0   72.30  1366 1414 1446 1526  768 771 776 790 -hsync -vsync (47.4 kHz)
[  2610.004] 
Backtrace:
[  2610.005] 0: /usr/bin/X (xorg_backtrace+0x26) [0x7f093556a816]
[  2610.005] 1: /usr/bin/X (0x7f09353e2000+0x18c6ba) [0x7f093556e6ba]
[  2610.005] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f0934708000+0xfcb0) [0x7f0934717cb0]
[  2610.005] 3: /usr/bin/X (XIChangeDeviceProperty+0x1c8) [0x7f093550a188]
[  2610.005] 4: /usr/bin/X (0x7f09353e2000+0x1287fb) [0x7f093550a7fb]
[  2610.005] 5: /usr/bin/X (0x7f09353e2000+0x4e8a1) [0x7f09354308a1]
[  2610.005] 6: /usr/bin/X (0x7f09353e2000+0x3d7ba) [0x7f093541f7ba]
[  2610.005] 7: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f093359d76d]
[  2610.005] 8: /usr/bin/X (0x7f09353e2000+0x3daad) [0x7f093541faad]
[  2610.005] Segmentation fault at address 0x7f0900000010
[  2610.006] 
Caught signal 11 (Segmentation fault). Server aborting
[  2610.006] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  2610.006] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2610.006] 
[  2610.013] (II) evdev: Power Button: Close
[  2610.013] (II) UnloadModule: "evdev"
[  2610.013] (II) Unloading evdev
[  2610.014] (II) evdev: Video Bus: Close
[  2610.014] (II) UnloadModule: "evdev"
[  2610.014] (II) Unloading evdev
[  2610.016] (II) evdev: Power Button: Close
[  2610.016] (II) UnloadModule: "evdev"
[  2610.016] (II) Unloading evdev
[  2610.025] (II) evdev: Sleep Button: Close
[  2610.025] (II) UnloadModule: "evdev"
[  2610.025] (II) Unloading evdev
[  2610.029] (II) evdev: AT Translated Set 2 keyboard: Close
[  2610.029] (II) UnloadModule: "evdev"
[  2610.029] (II) Unloading evdev
[  2610.049] (II) evdev: Acer WMI hotkeys: Close
[  2610.049] (II) UnloadModule: "evdev"
[  2610.049] (II) Unloading evdev
```

The last application I used was Pyrit.

Thanks in advance for helping me :-)

---

### Post by Shadius on 2012-07-19
Sounds like it could be a graphics card issue. Check your drivers as described by *David Andersson*. Also, it'd be better if you edit your previous post and surround the code in between the [CODE] tags by clicking a "#" symbol. It's easier to read that way.

---

### Post by stepking2 on 2012-07-19
I didn't get spoiler tags to work :-P

But, it's wierd, I've never had these issues before. And what could I do about my graphics drivers? Download them for AMD's website, instead of using Jockey?

Here is xSession-Errors log:
```

(gnome-settings-daemon:10152): color-plugin-WARNING **: failed to get edid: unable to get EDID for output

(gnome-settings-daemon:10152): color-plugin-WARNING **: unable to get EDID for xrandr-LVDS: unable to get EDID for output
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
Initializing opengl options...done
Initializing decor options...done
Initializing vpswitch options...done

(nautilus:10190): Gdk-WARNING **: The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadPixmap (invalid Pixmap parameter)'.
  (Details: serial 594 error_code 4 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Initializing snap options...done
Initializing mousepoll options...done
Initializing resize options...done
Initializing place options...done
Initializing move options...done
Initializing wall options...done
Initializing grid options...done
I/O warning : failed to load external entity "/home/peter/.compiz/session/1078c4235fb26b7f6a134272906292499400000101050030"
Initializing session options...done
Initializing gnomecompat options...done
Initializing animation options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing workarounds options...done
Initializing scale options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing ezoom options...done

(compiz:10174): GConf-CRITICAL **: gconf_client_add_dir: assertion `gconf_valid_key (dirname, NULL)' failed
Initializing unityshell options...done
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "icon_size"
** Message: moving back from GtkStatusIcon to indicator

** (zeitgeist-datahub:10458): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3800081

```

---

### Post by David Andersson on 2012-07-19
At 2610.005 seconds something goes wrong
> **stepking2 said:**
> 
```

[  2610.005] Segmentation fault at address 0x7f0900000010
[  2610.006] 
Caught signal 11 (Segmentation fault). Server aborting

```

A few seconds earlier it talks about Lid Open. Can you see if the graphic crashes are related to wake ups after suspend or hibernate?

Or is it only related to using the Pyrit application?

> **stepking2 said:**
> I have a Radeon HD6600M graphics card with the proprietary drivers installed and activated.

Can you try deactivate proprietary drivers? Does it still crash? Is resolution correct and performance good enough?

(Do you use Unity 3D or compiz effects? Then deactivating proprietary drivers may not be the right solution even if it stops crashing.)

---

### Post by stepking2 on 2012-07-20
Before I started using Pyrit, this was never a problem.

I think I am using Unity 3D, I haven't added any effects or such. I have the desktop as it came when I installed Ubuntu.

But, I think I discovered something. When I give Pyrit a folder that doesn't exist, as an input, a error from Pyrit shows up in the terminal, and usually it's now the xServer crashes.

---

### Post by stepking2 on 2012-07-21
Bump..

---

### Post by David Andersson on 2012-07-22
> **stepking2 said:**
> Bump..

Did you try deactivate proprietary driver for ATI?

---

