---
title: "Natty reboots when booting"
date: 2011-05-07
forum: General Help
---

### Post by lavinog on 2011-05-07
I usually have had a easy time installing previous versions of Ubuntu, however I am having a difficult time with Natty on my main computer.

I have:
Motherboard: Gigabyte GA-MA78GM-S2H with embedded ATI Radeon HD3200
Video Card: ATI Radeon HD3650
Processor: AMD Athlon X2e
4G of memory

I installed Natty 64 from live cd.

The issue is that the system reboots when it tries to load X.
This occurs with the live cd as well.  I was able to boot into the live cd in 2d mode by using the following:
```

acpi=off noapic nolapic edd=on nodmraid nomodeset

```
I am not able to use those commands in grub to get the system to boot.

I have removed the video card, and re-enabled the onboard video and got the same results.

I booted into recovery mode and selected failsafex where i am greeted with the "Ubuntu is running in low-graphics mode", but when I select "Run Ubuntu in low-graphics mode for just one session" the system reboots almost instantly.

Checking the logs doesn't seem to help, because the system reboots before the logs get synced to the disk.

Natty live cd works on my wife's computer which is almost identical except her motherboard is a GA-MA78GM-US2H (it's pretty much a newer version of the same board)

When investigating the original issue, I was suspecting the sp5900_tco module since it was a new thing and it was the last message I saw on many cases, but blacklisting it didn't help.

My next step is to try an alt-install disk and see if that makes a difference

Does anyone know of any other boot options to try?

---

### Post by wilee-nilee on 2011-05-07
So your getting a grub menu it sounds like, I'm a little confused with the you can't add the commands to the kernel.

I presume you know of hitting e at the grub menu and editing using the arrow and backspace key. Or you have inserted these and they don't work.

---

### Post by lavinog on 2011-05-07
I inserted them and they don't work.

---

### Post by lavinog on 2011-05-07
Good news.
I updated the bios...and the time it takes to get to grub is many times faster.
However it didn't fix the problem.

I wound up installing the fglrx driver using apt in the recovery console, and I was able to boot just fine.

I am a little disappointed that I have to use the binary driver and not the foss driver though.

Marking as solved, however I will need to file a bug against the foss drivers i guess.

---

### Post by alex2399 on 2011-05-08
I have the same problem with 11.04 installed via the alternate installer, I can see the login screen for 1 sec or so and then it reboots. Normal liveCD of the desktop does the same, it reboots and in some cases completely powers off my PC when getting into a GUI for maybe 1 second.
On Lucid, where i'm typing from the FOSS drivers work like a charm for normal desktop usage.

I already tried another kernel, 2.6.39.xx, X-swat ppa, X -configure, all stuff you can think of from the command line for a normal human being etc... Only thing that works is fglrx, but it is choppy and fails to start Gnome when Xinerama is enabled. 

And I do have a similar setup to yours Lavinog,

Athlon X2 5600+
ATI Radeon HD3870, dual screen attached (2*1680*1050)
Gigabyte MA790X-DS4 mainboard
4GB Ram (2*2)

So did you or anyone else find a way to get the FOSS Radeon driver to work?

I do find error an message constantly with the FOSS driver,
"Number of created screens does not match number of detected devices. Configuration failed." Not sure if it is related...

Attached a log of Xorg, not completely but pretty sure I didn't do anything to the system as of then in regard to FGLRX.

```

[   871.944] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   871.948] X Protocol Version 11, Revision 0
[   871.950] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   871.951] Current Operating System: Linux ubuntu-5600 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[   871.952] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=d0dcbaf4-f6f4-47bd-b3df-7662327a4c5d ro single
[   871.954] Build Date: 19 April 2011  03:40:45PM
[   871.955] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[   871.956] Current version of pixman: 0.20.2
[   871.958] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   871.961] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   871.965] (==) Log file: "/var/log/Xorg.0.1:1.2.log", Time: Sat May  7 17:41:49 2011
[   871.966] (II) Loader magic: 0x7e0280
[   871.966] (II) Module ABI versions:
[   871.966] 	X.Org ANSI C Emulation: 0.4
[   871.966] 	X.Org Video Driver: 10.0
[   871.966] 	X.Org XInput driver : 12.3
[   871.966] 	X.Org Server Extension : 5.0
[   871.967] (--) PCI:*(0:1:0:0) 1002:9501:1043:022a rev 0, Mem @ 0xd0000000/268435456, 0xfdee0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[   871.967] (--) PCI: (0:3:7:0) 109e:036e:0070:13eb rev 17, Mem @ 0xfdbff000/4096
[   871.968] List of video drivers:
[   871.969] 	radeon
[   871.970] 	trident
[   871.972] 	ati
[   871.973] 	vmwlegacy
[   871.974] 	r128
[   871.975] 	mach64
[   871.976] 	s3virge
[   871.978] 	intel
[   871.979] 	rendition
[   871.980] 	s3
[   871.981] 	chips
[   871.982] 	nouveau
[   871.983] 	i128
[   871.985] 	cirrus
[   871.986] 	qxl
[   871.987] 	voodoo
[   871.988] 	neomagic
[   871.989] 	ark
[   871.991] 	tseng
[   871.992] 	sisusb
[   871.993] 	sis
[   871.994] 	mga
[   871.995] 	savage
[   871.996] 	siliconmotion
[   871.998] 	apm
[   871.999] 	openchrome
[   872.000] 	vmware
[   872.001] 	tdfx
[   872.002] 	fbdev
[   872.003] 	vesa
[   872.005] (II) LoadModule: "radeon"
[   872.005] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   872.005] (II) Module radeon: vendor="X.Org Foundation"
[   872.005] 	compiled for 1.10.0, module version = 6.14.0
[   872.005] 	Module class: X.Org Video Driver
[   872.005] 	ABI class: X.Org Video Driver, version 10.0
[   872.005] (II) LoadModule: "trident"
[   872.005] (II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
[   872.005] (II) Module trident: vendor="X.Org Foundation"
[   872.005] 	compiled for 1.10.0, module version = 1.3.4
[   872.005] 	Module class: X.Org Video Driver
[   872.005] 	ABI class: X.Org Video Driver, version 10.0
[   872.005] (II) LoadModule: "ati"
[   872.005] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   872.006] (II) Module ati: vendor="X.Org Foundation"
[   872.006] 	compiled for 1.10.0, module version = 6.14.0
[   872.006] 	Module class: X.Org Video Driver
[   872.006] 	ABI class: X.Org Video Driver, version 10.0
[   872.006] (II) LoadModule: "vmwlegacy"
[   872.006] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[   872.006] (II) Module vmwlegacy: vendor="X.Org Foundation"
[   872.006] 	compiled for 1.10.0, module version = 11.0.3
[   872.006] 	Module class: X.Org Video Driver
[   872.006] 	ABI class: X.Org Video Driver, version 10.0
[   872.006] (II) LoadModule: "r128"
[   872.006] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[   872.006] (II) Module r128: vendor="X.Org Foundation"
[   872.006] 	compiled for 1.10.0, module version = 6.8.1
[   872.006] 	Module class: X.Org Video Driver
[   872.006] 	ABI class: X.Org Video Driver, version 10.0
[   872.006] (II) LoadModule: "mach64"
[   872.006] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[   872.006] (II) Module mach64: vendor="X.Org Foundation"
[   872.006] 	compiled for 1.10.0, module version = 6.8.2
[   872.006] 	Module class: X.Org Video Driver
[   872.006] 	ABI class: X.Org Video Driver, version 10.0
[   872.006] (II) LoadModule: "s3virge"
[   872.006] (II) Loading /usr/lib/xorg/modules/drivers/s3virge_drv.so
[   872.006] (II) Module s3virge: vendor="X.Org Foundation"
[   872.006] 	compiled for 1.10.0, module version = 1.10.4
[   872.006] 	Module class: X.Org Video Driver
[   872.006] 	ABI class: X.Org Video Driver, version 10.0
[   872.006] (II) LoadModule: "intel"
[   872.006] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   872.007] (II) Module intel: vendor="X.Org Foundation"
[   872.007] 	compiled for 1.10.1, module version = 2.14.0
[   872.007] 	Module class: X.Org Video Driver
[   872.007] 	ABI class: X.Org Video Driver, version 10.0
[   872.007] (II) LoadModule: "rendition"
[   872.007] (II) Loading /usr/lib/xorg/modules/drivers/rendition_drv.so
[   872.007] (II) Module rendition: vendor="X.Org Foundation"
[   872.007] 	compiled for 1.10.0, module version = 4.2.4
[   872.007] 	Module class: X.Org Video Driver
[   872.007] 	ABI class: X.Org Video Driver, version 10.0
[   872.007] (II) LoadModule: "s3"
[   872.007] (II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
[   872.007] (II) Module s3: vendor="X.Org Foundation"
[   872.007] 	compiled for 1.10.0, module version = 0.6.3
[   872.007] 	Module class: X.Org Video Driver
[   872.007] 	ABI class: X.Org Video Driver, version 10.0
[   872.007] (II) LoadModule: "chips"
[   872.007] (II) Loading /usr/lib/xorg/modules/drivers/chips_drv.so
[   872.007] (II) Module chips: vendor="X.Org Foundation"
[   872.007] 	compiled for 1.10.0, module version = 1.2.3
[   872.007] 	Module class: X.Org Video Driver
[   872.007] 	ABI class: X.Org Video Driver, version 10.0
[   872.007] (II) LoadModule: "nouveau"
[   872.007] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   872.008] (II) Module nouveau: vendor="X.Org Foundation"
[   872.008] 	compiled for 1.10.0, module version = 0.0.16
[   872.008] 	Module class: X.Org Video Driver
[   872.008] 	ABI class: X.Org Video Driver, version 10.0
[   872.008] (II) LoadModule: "i128"
[   872.008] (II) Loading /usr/lib/xorg/modules/drivers/i128_drv.so
[   872.008] (II) Module i128: vendor="X.Org Foundation"
[   872.008] 	compiled for 1.10.0, module version = 1.3.4
[   872.008] 	Module class: X.Org Video Driver
[   872.008] 	ABI class: X.Org Video Driver, version 10.0
[   872.008] (II) LoadModule: "cirrus"
[   872.008] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
[   872.008] (II) Module cirrus: vendor="X.Org Foundation"
[   872.008] 	compiled for 1.10.0, module version = 1.3.2
[   872.008] 	Module class: X.Org Video Driver
[   872.008] 	ABI class: X.Org Video Driver, version 10.0
[   872.008] (II) LoadModule: "qxl"
[   872.008] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[   872.008] (II) Module qxl: vendor="X.Org Foundation"
[   872.008] 	compiled for 1.10.0, module version = 0.0.0
[   872.008] 	Module class: X.Org Video Driver
[   872.008] 	ABI class: X.Org Video Driver, version 10.0
[   872.008] (II) LoadModule: "voodoo"
[   872.008] (II) Loading /usr/lib/xorg/modules/drivers/voodoo_drv.so
[   872.008] (II) Module voodoo: vendor="X.Org Foundation"
[   872.009] 	compiled for 1.10.0, module version = 1.1.0
[   872.009] 	Module class: X.Org Video Driver
[   872.009] 	ABI class: X.Org Video Driver, version 10.0
[   872.009] (II) LoadModule: "neomagic"
[   872.009] (II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
[   872.009] (II) Module neomagic: vendor="X.Org Foundation"
[   872.009] 	compiled for 1.10.0, module version = 1.2.5
[   872.009] 	Module class: X.Org Video Driver
[   872.009] 	ABI class: X.Org Video Driver, version 10.0
[   872.009] (II) LoadModule: "ark"
[   872.009] (II) Loading /usr/lib/xorg/modules/drivers/ark_drv.so
[   872.009] (II) Module ark: vendor="X.Org Foundation"
[   872.009] 	compiled for 1.10.0, module version = 0.7.3
[   872.009] 	Module class: X.Org Video Driver
[   872.009] 	ABI class: X.Org Video Driver, version 10.0
[   872.009] (II) LoadModule: "tseng"
[   872.009] (II) Loading /usr/lib/xorg/modules/drivers/tseng_drv.so
[   872.009] (II) Module tseng: vendor="X.Org Foundation"
[   872.009] 	compiled for 1.10.0, module version = 1.1.0
[   872.009] 	Module class: X.Org Video Driver
[   872.009] 	ABI class: X.Org Video Driver, version 10.0
[   872.009] (II) LoadModule: "sisusb"
[   872.009] (II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
[   872.009] (II) Module sisusb: vendor="X.Org Foundation"
[   872.009] 	compiled for 1.10.0, module version = 0.9.4
[   872.010] 	Module class: X.Org Video Driver
[   872.010] 	ABI class: X.Org Video Driver, version 10.0
[   872.010] (II) LoadModule: "sis"
[   872.010] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[   872.010] (II) Module sis: vendor="X.Org Foundation"
[   872.010] 	compiled for 1.10.0, module version = 0.10.3
[   872.010] 	Module class: X.Org Video Driver
[   872.010] 	ABI class: X.Org Video Driver, version 10.0
[   872.010] (II) LoadModule: "mga"
[   872.010] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[   872.010] (II) Module mga: vendor="X.Org Foundation"
[   872.010] 	compiled for 1.10.0, module version = 1.4.13
[   872.010] 	Module class: X.Org Video Driver
[   872.010] 	ABI class: X.Org Video Driver, version 10.0
[   872.010] (II) LoadModule: "savage"
[   872.010] (II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
[   872.010] (II) Module savage: vendor="X.Org Foundation"
[   872.010] 	compiled for 1.10.0, module version = 2.3.2
[   872.010] 	Module class: X.Org Video Driver
[   872.010] 	ABI class: X.Org Video Driver, version 10.0
[   872.010] (II) LoadModule: "siliconmotion"
[   872.011] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[   872.011] (II) Module siliconmotion: vendor="X.Org Foundation"
[   872.011] 	compiled for 1.10.0, module version = 1.7.4
[   872.011] 	Module class: X.Org Video Driver
[   872.011] 	ABI class: X.Org Video Driver, version 10.0
[   872.011] (II) LoadModule: "apm"
[   872.011] (II) Loading /usr/lib/xorg/modules/drivers/apm_drv.so
[   872.011] (II) Module apm: vendor="X.Org Foundation"
[   872.011] 	compiled for 1.10.0, module version = 1.2.3
[   872.011] 	Module class: X.Org Video Driver
[   872.011] 	ABI class: X.Org Video Driver, version 10.0
[   872.011] (II) LoadModule: "openchrome"
[   872.011] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[   872.011] (II) Module openchrome: vendor="http://openchrome.org/"
[   872.011] 	compiled for 1.10.0, module version = 0.2.904
[   872.011] 	Module class: X.Org Video Driver
[   872.011] 	ABI class: X.Org Video Driver, version 10.0
[   872.011] (II) LoadModule: "vmware"
[   872.011] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[   872.011] (II) Module vmware: vendor="X.Org Foundation"
[   872.011] 	compiled for 1.10.0, module version = 11.0.3
[   872.011] 	Module class: X.Org Video Driver
[   872.011] 	ABI class: X.Org Video Driver, version 10.0
[   872.011] (II) LoadModule: "vmwgfx"
[   872.012] (WW) Warning, couldn't open module vmwgfx
[   872.012] (II) UnloadModule: "vmwgfx"
[   872.012] (II) Unloading vmwgfx
[   872.012] (EE) Failed to load module "vmwgfx" (module does not exist, 0)
[   872.013] (EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
[   872.014] (II) vmware: Using vmwlegacy driver everything is fine.
[   872.014] (II) LoadModule: "vmwlegacy"
[   872.015] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[   872.015] (II) Module vmwlegacy: vendor="X.Org Foundation"
[   872.015] 	compiled for 1.10.0, module version = 11.0.3
[   872.015] 	Module class: X.Org Video Driver
[   872.015] 	ABI class: X.Org Video Driver, version 10.0
[   872.015] (II) UnloadModule: "vmwlegacy"
[   872.015] (II) Unloading vmwlegacy
[   872.015] (II) Failed to load module "vmwlegacy" (already loaded, 23391552)
[   872.015] (EE) vmware: Unexpected failure while loading the "vmwlegacy" driver. Giving up.
[   872.016] (II) UnloadModule: "vmware"
[   872.016] (II) Unloading vmware
[   872.016] (EE) Failed to load module "vmware" (a required submodule could not be loaded, 0)
[   872.017] (II) LoadModule: "tdfx"
[   872.017] (II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
[   872.018] (II) Module tdfx: vendor="X.Org Foundation"
[   872.018] 	compiled for 1.10.0, module version = 1.4.3
[   872.018] 	Module class: X.Org Video Driver
[   872.018] 	ABI class: X.Org Video Driver, version 10.0
[   872.018] (II) LoadModule: "fbdev"
[   872.018] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   872.018] (II) Module fbdev: vendor="X.Org Foundation"
[   872.018] 	compiled for 1.10.0, module version = 0.4.2
[   872.018] 	ABI class: X.Org Video Driver, version 10.0
[   872.018] (II) LoadModule: "vesa"
[   872.018] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   872.018] (II) Module vesa: vendor="X.Org Foundation"
[   872.018] 	compiled for 1.10.0, module version = 2.3.0
[   872.018] 	Module class: X.Org Video Driver
[   872.018] 	ABI class: X.Org Video Driver, version 10.0
[   872.018] (II) RADEON: Driver for ATI Radeon chipsets:
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
[   872.021] (WW) Falling back to old probe method for trident
[   872.021] (WW) Falling back to old probe method for s3virge
[   872.021] (WW) Falling back to old probe method for s3
[   872.021] (WW) Falling back to old probe method for i128
[   872.021] (WW) Falling back to old probe method for cirrus
[   872.021] (II) Loading sub module "cirrus_laguna"
[   872.021] (II) LoadModule: "cirrus_laguna"
[   872.021] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
[   872.021] (II) Module cirrus_laguna: vendor="X.Org Foundation"
[   872.021] 	compiled for 1.10.0, module version = 1.0.0
[   872.021] 	ABI class: X.Org Video Driver, version 10.0
[   872.021] (II) Loading sub module "cirrus_alpine"
[   872.021] (II) LoadModule: "cirrus_alpine"
[   872.021] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
[   872.021] (II) Module cirrus_alpine: vendor="X.Org Foundation"
[   872.021] 	compiled for 1.10.0, module version = 1.0.0
[   872.021] 	ABI class: X.Org Video Driver, version 10.0
[   872.021] (WW) Falling back to old probe method for voodoo
[   872.021] (WW) Falling back to old probe method for neomagic
[   872.021] (WW) Falling back to old probe method for ark
[   872.021] (WW) Falling back to old probe method for tseng
[   872.021] (WW) Falling back to old probe method for sisusb
[   872.021] (WW) Falling back to old probe method for sis
[   872.022] (WW) Falling back to old probe method for siliconmotion
[   872.022] (WW) Falling back to old probe method for apm
[   872.022] (II) FBDEV: driver for framebuffer: fbdev
[   872.022] (II) VESA: driver for VESA chipsets: vesa
[   872.030] (++) Using config file: "/home/alex/xorg.conf.new"
[   872.031] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   872.033] (==) ServerLayout "X.org Configured"
[   872.033] (**) |-->Screen "Screen0" (0)
[   872.033] (**) |   |-->Monitor "Monitor0"
[   872.033] (**) |   |-->Device "Card0"
[   872.033] (**) |-->Screen "Screen1" (1)
[   872.033] (**) |   |-->Monitor "Monitor1"
[   872.033] (**) |   |-->Device "Card1"
[   872.033] (**) |-->Screen "Screen2" (2)
[   872.033] (**) |   |-->Monitor "Monitor2"
[   872.034] (**) |   |-->Device "Card2"
[   872.034] (**) |-->Input Device "Mouse0"
[   872.034] (**) |-->Input Device "Keyboard0"
[   872.034] (==) Automatically adding devices
[   872.034] (==) Automatically enabling devices
[   872.034] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   872.034] 	Entry deleted from font path.
[   872.034] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   872.034] (**) ModulePath set to "/usr/lib/xorg/modules"
[   872.034] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   872.034] (WW) Disabling Mouse0
[   872.034] (WW) Disabling Keyboard0
[   872.034] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   872.034] (II) [KMS] No DRICreatePCIBusID symbol, no kernel modesetting.
[   872.035] (WW) Falling back to old probe method for fbdev
[   872.035] (II) Loading sub module "fbdevhw"
[   872.035] (II) LoadModule: "fbdevhw"
[   872.036] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   872.036] (II) Module fbdevhw: vendor="X.Org Foundation"
[   872.036] 	compiled for 1.10.1, module version = 0.0.2
[   872.036] 	ABI class: X.Org Video Driver, version 10.0
[   872.036] (WW) Falling back to old probe method for vesa
[   872.036] Number of created screens does not match number of detected devices.
  Configuration failed.
```

---

### Post by lavinog on 2011-05-08
Thanks for the reply, I feel a little better knowing that I am not the only one then.

I did file a bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/779323](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/779323)

It might help if you attach that info there.

---

### Post by alex2399 on 2011-05-09
lavinog, I marked that I'm also affected by the bug. But I don't think my info would add something since this system is a bit "tainted" at the moment. Still could you please tell me how you collect all the logs for launchpad or do you all gather them by hand?

Back to this bug, it's getting a bit stranger, I'm typing this now from firefox in the Natty install but not in the usual way.

If I let the PC start up as usual it reboots. I went to the management console logging in as root and if I start X (cmd:startx) I get the wallpaper background without anything on it in terminal 2 (cmd:CTRL-ALT-F2). Pressing F1 gives me the help window and transperancy/desktop effects seem to work in there. I started firefox through the change background window that you can access via right click. Selected tab themes, get more themes online started firefox...

Anyway, if I as root instead of "startx" do "gdm" it is as always a reboot. This also happens when I'm logged in under my own username in the terminal.

At the moment updated with xorg edgers and kernel 2.6.39.05, and a minimal xorg.conf that I grabbed from the internet, but it doesn't seem to help.

Edit: I even have Unity running, completely normal desktop with effects and all, except it is as root. Did it by adding a starter to the desktop with "xterm" as command. Then starting "unity" as root. I can start everything normally except when I am logged in under my own username.

Edit2: removed gdm and installed kdm/kde and lxde. Kdm login screen works, but when logging in to any desktop environment under my own username it still reboots, only root works.

---

### Post by alex2399 on 2011-05-14
Still not getting really far but I am able to log in semi-normal under my own username.

I had to ```
apt-get remove --purge xserver-xorg-video-ati
``` **and use** ```
nomodeset
``` as bootparameter. Doing only one of those two results as always in a reboot. But with these options I get a non-optimal resolution...:(

---

