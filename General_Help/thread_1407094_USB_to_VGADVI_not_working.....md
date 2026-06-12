---
title: "USB to VGA/DVI not working...."
date: 2010-02-14
forum: General Help
---

### Post by maghajan on 2010-02-14
Hi everyone, 

I just bought a Tritton See2 Xtreme USB to DVI external video adapter and was hoping to use it as a primary display for my computer.  The reason I want to use it as a primary display is because my current computer has a very weak video card and I cannot add any internal video cards; so external is my only option.  I tried doing many google searches and edited my xorg.conf file a variety of ways, but still have no luck.  I'd appreciate any help.  

Here my output from "lsusb" command:

Bus 001 Device 008: ID 0711:0950 Magic Control Technology Corp. 
Bus 001 Device 007: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 006: ID 413c:0000 Dell Computer Corp. 
Bus 001 Device 005: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 002: ID 413c:a001 Dell Computer Corp. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

EDIT:  Also, the computer is a Dell Poweredge 1950, hence the weak built-on video card, but 8GB RAM and 8-core processor.  Can't be re-purposed as a server so I am re-purposing it as a desktop instead and therefore need more video.

---

### Post by MooPi on 2010-02-14
Are you able to get a viewable monitor while you use the external video adapter ? Also if you boot from a live CD does it function ?

---

### Post by maghajan on 2010-02-14
> **MooPi said:**
> Are you able to get a viewable monitor while you use the external video adapter ? Also if you boot from a live CD does it function ?

Your first question:  I left the monitor that plugs directly into the computer's original video card plugged in so that I can see what I'm doing to the computer, but I added a 2nd monitor to the Tritton usb to dvi adapter.

Your second question:  I have not tried booting from a live cd.  Should that make a difference?  I plugged the adapter in from before turning on the computer and at no point did anything display on the monitor that connected to the usb to dvi adapter.

Did my answers help in anyway?  I hope so...

---

### Post by flippo on 2010-02-14
Can you restart X with the device pluggin in and post your /var/log/Xorg.0.log?  That should tell if the device is being detected.  If it is you just need to make an appropriate xorg.conf.

---

### Post by maghajan on 2010-02-15
> **flippo said:**
> Can you restart X with the device pluggin in and post your /var/log/Xorg.0.log?  That should tell if the device is being detected.  If it is you just need to make an appropriate xorg.conf.

Based on my google searches prior to starting this thread, I edited my /etc/X11/xorg.conf file many times with no luck.  I created screens, monitors, devices based on what other people posted on other forums and no luck.  Each time I made a change I would log out and log back in and/or restart my computer altogether and no luck.  Eventually I just reverted my xorg.conf file back to it's original state.  I will post the contents of "/var/log/Xorg.0.log" tomorrow as soon as I have access to the server again.  Thank you and everyone for helping with this so far!!

---

### Post by maghajan on 2010-02-15
> **flippo said:**
> Can you restart X with the device pluggin in and post your /var/log/Xorg.0.log?  That should tell if the device is being detected.  If it is you just need to make an appropriate xorg.conf.

Hi there, here is the output from Xorg.0.log file that you asked about.  Before plugging in the usb-to-dvi device, I unplugged the mouse and replugged it into another usb port.  Then I plugged in the usb-to-dvi device.  From what I can tell, this log file saw the mouse being plugged into the other port, but nothing after that :-(  Thanks for looking into this!!!
[FONT="Courier New"]
II) config/hal: removing device Dell Dell USB Optical Mouse
(II) Dell Dell USB Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device Dell Dell USB Optical Mouse
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event3"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(**) Dell Dell USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Dell Dell USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Dell Dell USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Dell Dell USB Optical Mouse: (accel) set acceleration profile 0
(II) Dell Dell USB Optical Mouse: initialized for relative axes.
[/FONT]

---

### Post by flippo on 2010-02-15
please plug in the device, start X (startup your machine) then give me the entire Xorg.0.log file.  I'm not sure if you can hotplug it.  USB devices can be detected, but I don't know if Xorg will.  Additionally what pops up on dmesg when you plug in the device?  (note dmesg will be very long, to get just the response from the device do the following:

```
<The device is not plugged in>
dmesg > dmesg_nodev
<plug in the device>
dmesg > dmesg_dev
diff dmesg_nodev dmesg_dev
rm dmesg_nodev dmesg_dev
```

The output of the diff will be the info I want.

---

### Post by maghajan on 2010-02-15
> **flippo said:**
> please plug in the device, start X (startup your machine) then give me the entire Xorg.0.log file.  I'm not sure if you can hotplug it.  USB devices can be detected, but I don't know if Xorg will.  Additionally what pops up on dmesg when you plug in the device?  (note dmesg will be very long, to get just the response from the device do the following:

```
<The device is not plugged in>
dmesg > dmesg_nodev
<plug in the device>
dmesg > dmesg_dev
diff dmesg_nodev dmesg_dev
rm dmesg_nodev dmesg_dev
```

The output of the diff will be the info I want.

Here is the entire Xorg.0.log file:

[FONT="Courier New"]
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux genomicscore-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64
Kernel command line: root=UUID=b4f3f7dd-8865-4095-bbe3-ea157b130c83 ro quiet splash 
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 15 15:12:04 2010
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
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:15:13:0) 1002:515e:1028:01b3 ATI Technologies Inc ES1000 rev 2, Mem @ 0xd8000000/134217728, 0xfc3d0000/65536, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
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
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
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
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
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
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
(II) Primary Device is: PCI 0f@00:0d:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[33] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[34] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[35] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[36] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[37] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[38] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[39] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[40] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[41] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[42] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[43] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[44] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[45] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[46] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[47] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[48] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[49] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[50] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000fc3d0000
(II) RADEON(0): MMIO registers at 0x00000000fc3d0000: size 64KB
(II) RADEON(0): PCI bus 15 card 13 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI ES1000 515E (PCI)" (ChipID = 0x515e)
(--) RADEON(0): Linear framebuffer at 0x00000000d8000000
(II) RADEON(0): PCI card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Bad V_BIOS checksum
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Direct rendering not officially supported on RN50
(II) RADEON(0): Detected total video RAM=16384K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 16384 kByte (16 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 50000, min_in_pll: 100, max_in_pll: 1350, xclk: 20000, sclk: 200.000000, mclk: 200.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=50000; xclk=20000
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC1
  DDC reg: 0x60
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
finished output detect: 0
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Not using mode "1280x1024" (mode requires too much memory bandwidth)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output VGA-0 using initial mode 1280x1024
(**) RADEON(0): Display dimensions: (340, 270) mm
(**) RADEON(0): DPI set to (95, 120)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[33] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[34] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[35] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[36] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[37] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[38] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[39] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[40] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[41] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[42] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[43] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[44] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[45] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[46] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[47] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[48] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[49] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[50] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit d8000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable primary dac
(II) RADEON(0): Dynamic Power Management Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1280,3276)
(II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
(II) RADEON(0): Largest offscreen area available: 1280 x 1994
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0xffff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		13 256x256 slots
		4 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 16 kb for hardware cursor 0 at offset 0x00642800
(II) RADEON(0): Largest offscreen area available: 1280 x 1990
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable primary dac
disable primary dac
init memmap
init common
init crtc1
init pll1
freq: 108000000
best_freq: 108000000
best_feedback_div: 16
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdbffd800 0xdbffd800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
set RMX
set primary dac
enable primary dac
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Setting vga for screen 0.
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
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 338 x 270
(II) config/hal: Adding input device Dell DRAC5
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Dell DRAC5: always reports core events
(**) Dell DRAC5: Device: "/dev/input/event3"
(II) Dell DRAC5: Found keys
(II) Dell DRAC5: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell DRAC5" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Dell Dell USB Keyboard
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event2"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event1"
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
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Dell Dell USB Optical Mouse
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event5"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(**) Dell Dell USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Dell Dell USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Dell Dell USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Dell Dell USB Optical Mouse: (accel) set acceleration profile 0
(II) Dell Dell USB Optical Mouse: initialized for relative axes.
(II) config/hal: Adding input device Dell DRAC5
(**) Dell DRAC5: always reports core events
(**) Dell DRAC5: Device: "/dev/input/event4"
(II) Dell DRAC5: Found 3 mouse buttons
(II) Dell DRAC5: Found scroll wheel(s)
(II) Dell DRAC5: Found x and y absolute axes
(II) Dell DRAC5: Configuring as mouse
(**) Dell DRAC5: YAxisMapping: buttons 4 and 5
(**) Dell DRAC5: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell DRAC5" (type: MOUSE)
(**) Dell DRAC5: (accel) keeping acceleration scheme 1
(**) Dell DRAC5: (accel) filter chain progression: 2.00
(**) Dell DRAC5: (accel) filter stage 0: 20.00 ms
(**) Dell DRAC5: (accel) set acceleration profile 0
(II) Dell DRAC5: initialized for absolute axes.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Not using mode "1280x1024" (mode requires too much memory bandwidth)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Not using mode "1280x1024" (mode requires too much memory bandwidth)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 3015  Serial#: 1095192887
(II) RADEON(0): Year: 2005  Week: 43
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: J66425AHAGQ7
(II) RADEON(0): Monitor name: DELL 1704FPV
(II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff0010ac153037514741
(II) RADEON(0): 	2b0f01030e221b78eeee95a3544c9926
(II) RADEON(0): 	0f5054a54b00714f8180010101010101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	1300520e1100001e000000ff004a3636
(II) RADEON(0): 	3432354148414751370a000000fc0044
(II) RADEON(0): 	454c4c20313730344650560a000000fd
(II) RADEON(0): 	00384c1e510e000a2020202020200068
(II) RADEON(0): EDID vendor "DEL", prod id 12309
(II) RADEON(0): Not using mode "1280x1024" (mode requires too much memory bandwidth)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[/FONT]

Here is the output of the dmesg diff you wanted:

[FONT="Courier New"] diff /home/genomicscore/dmesg_nodev /home/genomicscore/dmesg_dev 
872a873,874
> [  284.510011] usb 1-4: new high speed USB device using ehci_hcd and address 8
> [  284.660409] usb 1-4: configuration #1 chosen from 1 choice
[/FONT]

---

### Post by flippo on 2010-02-15
I see why you didn't post your xorg.log at first, its much longer than mine.

Okay, linux does not appear to associate your device with a driver when it is plugged in (from your dmesg output) and therefore it isn't even detected by xorg, and definitely not used.

according to this page: 
[http://www.happyassassin.net/2008/02/06/multiple-external-monitors-on-a-laptop-on-linux-with-tritton-see2-usb-video-adapter-sisusb/]("http://www.happyassassin.net/2008/02/06/multiple-external-monitors-on-a-laptop-on-linux-with-tritton-see2-usb-video-adapter-sisusb/")

The device your using requries the sisusbvga driver, which you should be able to assosciate with it using the line:
```
sudo modprobe sisusbvga vendor=0x<vendorcode> product=0x<productcode>
```

To get the vendor and product code do the following:
```
<unplug the device>
lsusb > lsusb_nodev
<plug in the device>
lsusb > lsusb_dev
diff lsusb_nodev lsusb_dev
rm lsusb_nodev lsusb_dev
```

the numbers your looking for will be represented "<busid> <devicenum> <vendornum>:<productnum> <description>"

Then you need to set up the device in your xorg.conf with something like this:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "sisusb"
    VendorName     "Tritton"
    BoardName      "See2 Xtreme"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
EndSection

```

you must also install the xorg sisusb driver:
```
sudo apt-get install xorg-video-sisusb
```

If that doesn't work you may have to specify a BusId for the USB device, I'm not sure how to do that in xorg.conf, but I'll help you figure it out when the time comes.  I'm sure it wont be too hard to look up.  Please let me know how this works and good luck :).

---

### Post by maghajan on 2010-02-15
> **flippo said:**
> I see why you didn't post your xorg.log at first, its much longer than mine.

Okay, linux does not appear to associate your device with a driver when it is plugged in (from your dmesg output) and therefore it isn't even detected by xorg, and definitely not used.

according to this page: 
[http://www.happyassassin.net/2008/02/06/multiple-external-monitors-on-a-laptop-on-linux-with-tritton-see2-usb-video-adapter-sisusb/]("http://www.happyassassin.net/2008/02/06/multiple-external-monitors-on-a-laptop-on-linux-with-tritton-see2-usb-video-adapter-sisusb/")

The device your using requries the sisusbvga driver, which you should be able to assosciate with it using the line:
```
sudo modprobe sisusbvga vendor=0x<vendorcode> product=0x<productcode>
```

To get the vendor and product code do the following:
```
<unplug the device>
lsusb > lsusb_nodev
<plug in the device>
lsusb > lsusb_dev
diff lsusb_nodev lsusb_dev
rm lsusb_nodev lsusb_dev
```

the numbers your looking for will be represented "<busid> <devicenum> <vendornum>:<productnum> <description>"

Then you need to set up the device in your xorg.conf with something like this:
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "sisusb"
    VendorName     "Tritton"
    BoardName      "See2 Xtreme"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
EndSection

```

you must also install the xorg sisusb driver:
```
sudo apt-get install xorg-video-sisusb
```

If that doesn't work you may have to specify a BusId for the USB device, I'm not sure how to do that in xorg.conf, but I'll help you figure it out when the time comes.  I'm sure it wont be too hard to look up.  Please let me know how this works and good luck :).

Thank you for all this information!  I will let you know as soon as I can try it, hopefully within a couple hours or by tomorrow.

---

### Post by flippo on 2010-02-15
I forgot to note, the modprobe will expire after you shut down your computer.  you can make it permanent by adding the line:
```
sisusbvgba vendor=0x<vendor> product=0x<product>
```

to /etc/modules

So, the order of doing things should be:
log on
drop to tty1 (ctrl+alt+f1)
stop X (sudo /etc/init.d/gdm stop)
get device vendor, product
modprobe
edit xorg
start X (sudo /etc/init.d/gdm start)

---

### Post by maghajan on 2010-02-15
> **flippo said:**
> I forgot to note, the modprobe will expire after you shut down your computer.  you can make it permanent by adding the line:
```
sisusbvgba vendor=0x<vendor> product=0x<product>
```

to /etc/modules

So, the order of doing things should be:
log on
drop to tty1 (ctrl+alt+f1)
stop X (sudo /etc/init.d/gdm stop)
get device vendor, product
modprobe
edit xorg
start X (sudo /etc/init.d/gdm start)

Hi there,

So I am fairly sure I followed your instructions, however, when it came to the "sudo modprobe sisusbvga..." command, I received some message saying that adding a "vendor" caused an error, the message also told me to check "dmesg" so I did and here's the output toward the end:

[FONT="Courier New"][   29.190088] eth0: no IPv6 routers present
[  378.235361] usb 1-4: USB disconnect, address 4
[  403.510033] usb 1-4: new high speed USB device using ehci_hcd and address 8
[  403.662353] usb 1-4: configuration #1 chosen from 1 choice
[ 1851.590325] mtrr: no MTRR for d8000000,1000000 found
[ 1916.949503] sisusbvga: Unknown parameter `vendor'
[/FONT]

Here is how I ran the command:

[FONT="Courier New"]sudo modprobe sisusbvga vendor=0x0711 product=0x0950 [/FONT] based on this information from lsusb_nodev/lsusb_dev, [FONT="Courier New"]Bus 001 Device 008: ID 0711:0950 Magic Control Technology Corp[/FONT].

Thank you for all your patience and help so far!

---

### Post by flippo on 2010-02-15
Ooops, should have checked that module myself first.  It doesn't use the vendor or product parameter, so just use:
```
sudo modprobe sisusbvga
```

For reference, if you ever need more information on a module use:
```
sudo modinfo <module>
```

---

### Post by maghajan on 2010-02-15
> **flippo said:**
> Ooops, should have checked that module myself first.  It doesn't use the vendor or product parameter, so just use:
```
sudo modprobe sisusbvga
```

For reference, if you ever need more information on a module use:
```
sudo modinfo <module>
```

Thanks for clearing that up, I will try it again momentarily and let you know what happens.  Also, should I remove what was previously in my xorg.conf and only put in what you wrote in the previous post?

---

### Post by flippo on 2010-02-15
You can merge your xorg with what I wrote if you'd like, but if you already have sections for the things I wrote I would replace them.  Make sure to make a backup of your current xorg.conf just in case things go poorly (I've never actually done this before, but I have a pretty good understanding of whats actually going on...)

---

### Post by maghajan on 2010-02-16
> **flippo said:**
> You can merge your xorg with what I wrote if you'd like, but if you already have sections for the things I wrote I would replace them.  Make sure to make a backup of your current xorg.conf just in case things go poorly (I've never actually done this before, but I have a pretty good understanding of whats actually going on...)

Not sure what to quote anymore, so here is where I am at and what I am doing:

With the files in the states shown below, I log in, drop to tty1, stop X (which gives me a message about how I should be doing this a "different" way, sudo modprobe sisusbvga, then try to start X (but this gives an error message).  Shouldn't the steps I just listed already be happening when I turn the computer on since they are present in /etc/module already?  

Also, when I do restart the computer and let it boot up, after the Xubuntu load screen is nearly done, the green light on my See2 Xtreme thing turns on for a second, then turns off, and then a message on the primary screen (the one plugged directly into the computer's internal video card) is displayed complaining that Ubuntu is running in low-graphics mode.  

Thanks for helping so much so far! 

After dropping to tty1...

[FONT="Courier New"]sudo /etc/init.d/gdm stop
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop

sudo /etc/init.d/gdm start
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm start
gdm start/running, process 2805[/FONT]

[FONT="Courier New"]sudo apt-get install xserver-xorg-video-sisusb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-sisusb is already the newest version.
The following packages were automatically installed and are no longer required:
  libdns50 libsigc++0c2 libgsf-gnome-1-114 binutils-static
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/FONT]


/etc/modules

[FONT="Courier New"]
lp
rtc
sisusbvga[/FONT]


xorg.conf file:
[FONT="Courier New"]
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"X.org Configured"
	Driver		"Screen0"
EndSection

Section "Device"
	Identifier	"Device0"
	Driver		"sisusb"
	VendorName	"Tritton"
	BoardName	"See2 Xtreme"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
EndSection[/FONT]

---

### Post by flippo on 2010-02-16
Once you stop X, try "sudo service gdm stop" (I'm running 8.04, they must have changed the "correct" way of doing things since then...) do the dmesg thing again to see if its being detected properly.  Also take a peek at your Xorg.0.log and see if that recognizes the USB hub as a video device or not.  

The sections you left in your xorg.conf (that I didn't tell you to put there) don't seem to actually be doing anything, you should be able remove them if you'd like (although I don't *think* they will mess anything up).

Furthermore, you are correct, if sisusbvga is in /etc/module then you don't have to worry about modprobeing it.

---

### Post by maghajan on 2010-02-16
> **flippo said:**
> Once you stop X, try "sudo service gdm stop" (I'm running 8.04, they must have changed the "correct" way of doing things since then...) do the dmesg thing again to see if its being detected properly.  Also take a peek at your Xorg.0.log and see if that recognizes the USB hub as a video device or not.  

The sections you left in your xorg.conf (that I didn't tell you to put there) don't seem to actually be doing anything, you should be able remove them if you'd like (although I don't *think* they will mess anything up).

Furthermore, you are correct, if sisusbvga is in /etc/module then you don't have to worry about modprobeing it.

Do i need to unplug it first then plug it in or anything, or should I just do?..

1) Turn computer on
2) Drop to tty1
3) sudo service gdm stop
4) look at Xorg.0.log
5) let you know what I see

---

### Post by maghajan on 2010-02-16
> **flippo said:**
> Once you stop X, try "sudo service gdm stop" (I'm running 8.04, they must have changed the "correct" way of doing things since then...) do the dmesg thing again to see if its being detected properly.  Also take a peek at your Xorg.0.log and see if that recognizes the USB hub as a video device or not.  

The sections you left in your xorg.conf (that I didn't tell you to put there) don't seem to actually be doing anything, you should be able remove them if you'd like (although I don't *think* they will mess anything up).

Furthermore, you are correct, if sisusbvga is in /etc/module then you don't have to worry about modprobeing it.

Ok, so here is what I did:

[FONT="Courier New"]1) Unplugged the usb to dvi device
2) Restarted the computer
3) Dropped into tty1 before even logging in
4) Ran "sudo service gdm stop"
5) Collected dmesg, lsusb and /var/log/Xorg.0.log output/info
6) Plugged in the usb to dvi device 
7) Collected dmesg, lsusb and /var/log/Xorg.0.log output/info[/FONT]

Here is the dmesg diff
[FONT="Courier New"]
diff dmesg_dev dmesg_nodev 
874,875d873
< [   75.460040] usb 1-4: new high speed USB device using ehci_hcd and address 7
< [   75.611661] usb 1-4: configuration #1 chosen from 1 choice
[/FONT]
Here is the lsusb diff

[FONT="Courier New"]diff lsusb_nodev lsusb_dev 
0a1
> Bus 001 Device 007: ID 0711:0950 Magic Control Technology Corp.[/FONT] 

[FONT="Courier New"]diff Xorg.0.log_dev Xorg.0.log_nodev[/FONT] produced nothing, I am showing the entire Xorg.0.log below anyway.

[FONT="Courier New"]X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux genomicscore-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64
Kernel command line: root=UUID=b4f3f7dd-8865-4095-bbe3-ea157b130c83 ro quiet splash 
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 16 13:25:48 2010
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 37 of section ServerLayout in file /etc/X11/xorg.conf
        "Driver" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log[/FONT]

Please let me know any other steps and information I should give you.  Thanks!!!!!!!

---

### Post by flippo on 2010-02-17
Hmmmmm, your system does not seem to recognize the usb device as a sisusbvga device, and there's an error in your xorg.conf.  We need to try and solve each of these issues to make this work:

First, the xorg.conf:
I see from your post of your xorg earlier that you have the line:
```
Driver  "Screen0"
```
under your "ServerLayout" section, this should actually be:
```
Screen  "Screen0"
```

Second, we need to have sisusbvga loaded to use your usb device:
Let's make sure the module driver for your usb device is being loaded at bootup, this command should tell you if it is:
```
sudo lsmod | grep sisusbvga
```
Please post the output of it.

---

### Post by maghajan on 2010-02-17
> **flippo said:**
> Hmmmmm, your system does not seem to recognize the usb device as a sisusbvga device, and there's an error in your xorg.conf.  We need to try and solve each of these issues to make this work:

First, the xorg.conf:
I see from your post of your xorg earlier that you have the line:
```
Driver  "Screen0"
```
under your "ServerLayout" section, this should actually be:
```
Screen  "Screen0"
```

Second, we need to have sisusbvga loaded to use your usb device:
Let's make sure the module driver for your usb device is being loaded at bootup, this command should tell you if it is:
```
sudo lsmod | grep sisusbvga
```
Please post the output of it.

Cool, I changed the xorg.conf and corrected the ServerLayout section.  Output of the command you asked for:

[FONT="Courier New"]sudo lsmod | grep sisusbvga
sisusbvga              30564  0 [/FONT]

---

### Post by flippo on 2010-02-17
Okay, it appears you have the module loaded.  Are you using a DVI or VGA cable on your device?  I ask this because VGA may be the only supported cable type.

It doesn't appear (from dmesg) that your computer is using the sisusbvga module...  can you give me the output of Xorg.0.log now that your xorg is corrected?

Also what does:
```
sudo lsmod | grep usbcore
```
give you?

(please put your Xorg.0.log in a code block, it makes it more readable)

---

### Post by EdwardMorris on 2010-02-17
Try this thread I started, try and do what I did and see if it helps,

[http://ubuntuforums.org/showthread.php?t=1398488](http://ubuntuforums.org/showthread.php?t=1398488)

Question for flippo:

   I bought an older version of the usb2vga device and configured x (see post above) and I got the display to show and it starts what seems like a new X session, but its very wierd, first off I can't drag anything onto that display and one I move the mouse pointer into that scree, its stuck there for good. Then, when I click on any options (Shutdown for ex) it pops-up the warning/are you sure window on the other screen where teh mouse won't go and I'm at the mercy of the keyboard IFF that popup windos is active. I can live with not being able to drag windows between the screens, and I can also put up with the windows popping up on the other screen but I really cannot do without having the mouse go back and forth between the screens, could you please take a look and advise how to achieve this?

---

### Post by flippo on 2010-02-17
@EdwardMorris
Excellent work on your video issue.

I will post on your thread, that way we can work on maghajen's issue here

---

### Post by maghajan on 2010-02-17
> **flippo said:**
> Okay, it appears you have the module loaded.  Are you using a DVI or VGA cable on your device?  I ask this because VGA may be the only supported cable type.

It doesn't appear (from dmesg) that your computer is using the sisusbvga module...  can you give me the output of Xorg.0.log now that your xorg is corrected?

Also what does:
```
sudo lsmod | grep usbcore
```
give you?

(please put your Xorg.0.log in a code block, it makes it more readable)

Here is my /var/log/Xorg.0.log...  Also there are a bunch of other Xorg.#.log files too:  ```
-rw-r--r-- 1 root              root    7074 2010-02-17 15:36 Xorg.0.log
-rw-r--r-- 1 root              root    1449 2010-02-17 13:07 Xorg.0.log.old
-rw-r--r-- 1 root              root   56632 2010-02-17 15:37 Xorg.1.log
-rw-r--r-- 1 root              root    7074 2010-02-17 15:36 Xorg.1.log.old
-rw-r--r-- 1 root              root   43607 2009-09-24 16:06 Xorg.20.log
-rw-r--r-- 1 root              root    7074 2010-02-17 15:36 Xorg.2.log
-rw-r--r-- 1 root              root    1449 2010-02-17 13:07 Xorg.2.log.old
-rw-r--r-- 1 root              root    7074 2010-02-17 15:36 Xorg.3.log
-rw-r--r-- 1 root              root    1449 2010-02-17 13:07 Xorg.3.log.old
-rw-r--r-- 1 root              root    7074 2010-02-17 15:37 Xorg.4.log
-rw-r--r-- 1 root              root    1449 2010-02-17 13:07 Xorg.4.log.old
-rw-r--r-- 1 root              root    7074 2010-02-17 15:37 Xorg.5.log
-rw-r--r-- 1 root              root    1449 2010-02-17 13:07 Xorg.5.log.old
-rw-r--r-- 1 root              root   30388 2010-02-14 19:55 Xorg.99.log
-rw-r--r-- 1 root              root   30388 2010-02-14 19:55 Xorg.99.log.old
-rw-r--r-- 1 root              root   56639 2010-02-17 15:37 Xorg.failsafe.log
-rw-r--r-- 1 root              root   57019 2010-02-17 13:42 Xorg.failsafe.log.old
```


```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux genomicscore-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64
Kernel command line: root=UUID=b4f3f7dd-8865-4095-bbe3-ea157b130c83 ro quiet splash 
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 17 15:36:59 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Device0"
(==) No monitor specified for screen "Screen0".
	Using a default monitor configuration.
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
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:15:13:0) 1002:515e:1028:01b3 ATI Technologies Inc ES1000 rev 2, Mem @ 0xd8000000/134217728, 0xfc3d0000/65536, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[36] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[37] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[38] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[39] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
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
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
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
(II) LoadModule: "sisusb"
(II) Loading /usr/lib/xorg/modules/drivers//sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) SISUSB: driver for SiSUSB chipsets: SIS315E/PRO USB
(WW) Falling back to old probe method for sisusb
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

I believe the device is DVI, this is what the unit looks like:  [http://www.slipperybrick.com/wp-content/uploads/2009/08/see2xtreme-sb.jpg](http://www.slipperybrick.com/wp-content/uploads/2009/08/see2xtreme-sb.jpg)

---

### Post by maghajan on 2010-02-17
> **flippo said:**
> Okay, it appears you have the module loaded.  Are you using a DVI or VGA cable on your device?  I ask this because VGA may be the only supported cable type.

It doesn't appear (from dmesg) that your computer is using the sisusbvga module...  can you give me the output of Xorg.0.log now that your xorg is corrected?

Also what does:
```
sudo lsmod | grep usbcore
```
give you?

(please put your Xorg.0.log in a code block, it makes it more readable)

Sorry, almost forgot ```
sudo lsmod | grep usbcore
``` returns nothing.  Is this a good or bad thing?

---

### Post by flippo on 2010-02-17
After thinking about it, it actually doesn't tell me much. The usbcore may be compiled into your kernel and not a module.

I'm not sure if I know of a driver for your device (I was looking at one with a VGA output when I did my searching, not only DVI).  You may still consider trying the advice on EdwardMorris's post (specifically the part about recompiling the driver).  If your device can use the sisusbvga driver then you will have to recompile it this way and see if that does any good for you.

If not then you may be out of luck for this device.  I'll keep my eyes open, and tell you if I have any luck.

---

### Post by rabby_ on 2010-06-15
Hi,

Did you find a solution or work-around for this so far?

Thanks a lot

---

### Post by -Cronos- on 2010-08-17
Bump.

Have such problem also. Patched sisusbvga module with my vendor and module, now it recognize device, but still black screen.

uname -a
```
Linux pchernyshev 2.6.32-3-amd64 #1 SMP Wed Feb 24 18:07:42 UTC 2010 x86_64 GNU/Linux
```

dmesg | tail -n 9
```
[95350.920039] usb 1-6: new high speed USB device using ehci_hcd and address 9
[95351.054343] usb 1-6: New USB device found, idVendor=0711, idProduct=5101
[95351.054352] usb 1-6: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[95351.054358] usb 1-6: Product: USBVGA
[95351.054362] usb 1-6: Manufacturer: MCT CORP 
[95351.054585] usb 1-6: configuration #1 chosen from 1 choice
[95351.056308] usb 1-6: USB2VGA dongle found at address 9
[95351.056536] usb 1-6: Allocated 8 output buffers
[95446.056020] usb 1-6: Failed to early initialize device
```

cat /var/log/Xorg.0.log | egrep -i "sis|usb|vga|\|"
```
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen[SISUSBVGA]" (1)
(**) |   |-->Monitor "Monitor[SISUSBVGA]"
(**) |   |-->Device "Device[SISUSBVGA]"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(II) LoadModule: "sisusb"
(II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
(II) SISUSB: driver for SiSUSB chipsets: SIS315E/PRO USB
(WW) Falling back to old probe method for sisusb
(II) UnloadModule: "sisusb"
(II) Unloading /usr/lib/xorg/modules/drivers/sisusb_drv.so
```

---

### Post by -Cronos- on 2010-08-17
Forgot to say: ST-Lab U-470

lsusb | grep -v "Linux"
```
Bus 001 Device 009: ID 0711:5101 Magic Control Technology Corp.
```

 lsmod | egrep "sis|usb|vga"
```
sisusbvga              44664  0 
usbcore               121703  4 sisusbvga,ohci_hcd,ehci_hcd
nls_base                6377  1 usbcore
```

---

### Post by jimbauwens on 2010-08-17
I've a Samsung U70 display (usb), and made it work using this manual:
[http://blogg.noonday.se/2010/01/28/linux-usb-video-adapter/](http://blogg.noonday.se/2010/01/28/linux-usb-video-adapter/)

Hope this helps for you.

Jim

---

### Post by -Cronos- on 2010-08-18
It's a pity, but my device is not DisplayLink, though I've compiled driver and explored its code.

I need some other usb-to-vga drivers.

---

