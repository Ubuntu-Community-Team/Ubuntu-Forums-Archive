---
title: "Xorg complains &quot;No devices detected.&quot;"
date: 2011-10-14
forum: General Help
---

### Post by pmatos on 2011-10-14
Hi,

I have a brand new Dell All-in-one Vostro 360, with a NVidia Geforce 525M. This video card is only supported by the latest nvidia-drivers 285.

So, I installed ubuntu 11.10. Then I installed nvidia-graphics-drivers from X-Ubuntu swat:
```
https://launchpad.net/~ubuntu-x-swat/+archive/x-updates
```

With my nvidia drivers installed, I ran nvidia-xconfig.

Running X gets me:
```
[    22.066] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    22.066] X Protocol Version 11, Revision 0
[    22.066] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    22.066] Current Operating System: Linux athena 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    22.066] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=907918e8-9093-461b-948b-2cc4631850d3 ro recovery nomodeset
[    22.066] Build Date: 29 September 2011  02:45:13AM
[    22.066] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    22.066] Current version of pixman: 0.22.2
[    22.066]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    22.066] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.066] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 14 23:07:43 2011
[    22.066] (==) Using config file: "/etc/X11/xorg.conf"
[    22.066] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.067] (==) ServerLayout "Layout0"
[    22.067] (**) |-->Screen "Screen0" (0)
[    22.067] (**) |   |-->Monitor "Monitor0"
[    22.067] (**) |   |-->Device "Device0"
[    22.067] (**) |-->Input Device "Keyboard0"
[    22.067] (**) |-->Input Device "Mouse0"
[    22.067] (==) Automatically adding devices
[    22.067] (==) Automatically enabling devices
[    22.067] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.067]    Entry deleted from font path.
[    22.067] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.067]    Entry deleted from font path.
[    22.067] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.067]    Entry deleted from font path.
[    22.067] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.067]    Entry deleted from font path.
[    22.067] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.067]    Entry deleted from font path.
[    22.067] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    22.067] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.067] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    22.067] (WW) Disabling Keyboard0
[    22.067] (WW) Disabling Mouse0
[    22.067] (II) Loader magic: 0x7e0220
[    22.067] (II) Module ABI versions:
[    22.067]    X.Org ANSI C Emulation: 0.4
[    22.067]    X.Org Video Driver: 10.0
[    22.067]    X.Org XInput driver : 12.3
[    22.067]    X.Org Server Extension : 5.0
[    22.067] (--) PCI:*(0:0:2:0) 8086:0102:1028:0512 rev 9, Mem @ 0xfb400000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    22.067] (--) PCI: (0:1:0:0) 10de:0df5:1028:0512 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    22.067] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.067] (II) LoadModule: "extmod"
[    22.084] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.084] (II) Module extmod: vendor="X.Org Foundation"
[    22.084]    compiled for 1.10.4, module version = 1.0.0
[    22.084]    Module class: X.Org Server Extension
[    22.084]    ABI class: X.Org Server Extension, version 5.0
[    22.084] (II) Loading extension MIT-SCREEN-SAVER
[    22.084] (II) Loading extension XFree86-VidModeExtension
[    22.084] (II) Loading extension XFree86-DGA
[    22.084] (II) Loading extension DPMS
[    22.084] (II) Loading extension XVideo
[    22.084] (II) Loading extension XVideo-MotionCompensation
[    22.084] (II) Loading extension X-Resource
[    22.084] (II) LoadModule: "dbe"
[    22.084] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.084] (II) Module dbe: vendor="X.Org Foundation"
[    22.084]    compiled for 1.10.4, module version = 1.0.0
[    22.084]    Module class: X.Org Server Extension
[    22.084]    ABI class: X.Org Server Extension, version 5.0
[    22.084] (II) Loading extension DOUBLE-BUFFER
[    22.084] (II) LoadModule: "glx"
[    22.084] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    22.639] (II) Module glx: vendor="NVIDIA Corporation"
[    22.648]    compiled for 4.0.2, module version = 1.0.0
[    22.648]    Module class: X.Org Server Extension
[    22.648] (II) NVIDIA GLX Module  285.05.09  Fri Sep 23 17:51:24 PDT 2011
[    22.648] (II) Loading extension GLX
[    22.648] (II) LoadModule: "record"
[    22.648] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.648] (II) Module record: vendor="X.Org Foundation"
[    22.648]    compiled for 1.10.4, module version = 1.13.0
[    22.648]    Module class: X.Org Server Extension
[    22.648]    ABI class: X.Org Server Extension, version 5.0
[    22.648] (II) Loading extension RECORD
[    22.648] (II) LoadModule: "dri"
[    22.649] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.649] (II) Module dri: vendor="X.Org Foundation"
[    22.649]    compiled for 1.10.4, module version = 1.0.0
[    22.649]    ABI class: X.Org Server Extension, version 5.0
[    22.649] (II) Loading extension XFree86-DRI
[    22.649] (II) LoadModule: "dri2"
[    22.649] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.649] (II) Module dri2: vendor="X.Org Foundation"
[    22.649]    compiled for 1.10.4, module version = 1.2.0
[    22.649]    ABI class: X.Org Server Extension, version 5.0
[    22.649] (II) Loading extension DRI2
[    22.649] (II) LoadModule: "nvidia"
[    22.649] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.870] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.870]    compiled for 4.0.2, module version = 1.0.0
[    22.870]    Module class: X.Org Video Driver
[    22.884] (II) NVIDIA dlloader X Driver  285.05.09  Fri Sep 23 17:33:35 PDT 2011
[    22.884] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    22.884] (++) using VT number 7

[    22.885] (EE) No devices detected.
[    22.902] 
Fatal server error:
[    22.902] no screens found
[    22.902] 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[    22.902] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    22.902]
```

Which is definitely strange because I have devices there. So, something else is going on. Here's what nvidia-xconfig generated:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 285.05.09  (buildmeister@swio-display-x86-rhel47-02.nvidia.com)  Fri Sep 23 17:55:57 PDT 2011

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

Any suggestions on how to get X working?

Cheers,
PMatos

---

### Post by gauravpadia on 2011-10-15
Guys somebody please help with this issue.

I have the same issue. I have Dell Inspiron N5110 laptop with NVIDIA Geforce GT 525M graphics card and have the same issue as mentioned above by pmatos. I am using Ubuntu 11.10.

I had search almost 90% of pages related to this issue on google but didn't find any working solution.

Please help.

---

### Post by pmatos on 2011-10-16
> **gauravpadia said:**
> Guys somebody please help with this issue.

I have the same issue. I have Dell Inspiron N5110 laptop with NVIDIA Geforce GT 525M graphics card and have the same issue as mentioned above by pmatos. I am using Ubuntu 11.10.

I had search almost 90% of pages related to this issue on google but didn't find any working solution.

Please help.

guaravpadia, have you installed the latest nvidia drivers (285)?
Do you still have the default xorg.conf that ubuntu generated for you? Can you post it?

---

### Post by DeadlyWolf on 2011-10-16
> **gauravpadia said:**
> 

I have the same issue. I have Dell Inspiron N5110 laptop with NVIDIA Geforce GT 525M graphics card and have the same issue as mentioned above by pmatos. I am using Ubuntu 11.10.

I had search almost 90% of pages related to this issue on google but didn't find any working solution.

Please help.


Me too with same Laptop.

---

### Post by pmatos on 2011-10-17
> **DeadlyWolf said:**
> Me too with same Laptop.

My guess is that if we want this sorted we will have to find a solution ourselves.

I stupidly deleted the original X config and deleted any backups. Do you still have it?

I was able to logon to X using the default config in compatibility mode. 

Lets work together to get this sorted.

If you don't have the original X config, do you remember how to generate it?

---

### Post by DeadlyWolf on 2011-10-17
> **pmatos said:**
> My guess is that if we want this sorted we will have to find a solution ourselves.

I stupidly deleted the original X config and deleted any backups. Do you still have it?



Yes, I do have an install that is fresh, that I have not changed anything with yet. But I am not at home so I'll post later today.

---

### Post by DeadlyWolf on 2011-10-18
```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

/etc/X11/xorg.conf

This is from an install where the drivers were installed during the installation of the system, when I had the install 3rd party software option selected, and Jockey indicates that the recommended driver is activated and currently in use. Nvidia current version. But using nvidia X server settings, I get, the "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root),and restart the X server", message, which I have not done.
 Other than the message my system seems to be running fine.

---

### Post by pmatos on 2011-10-18
> **DeadlyWolf said:**
> ```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

/etc/X11/xorg.conf

This is from an install where the drivers were installed during the installation of the system, when I had the install 3rd party software option selected, and Jockey indicates that the recommended driver is activated and currently in use. Nvidia current version. But using nvidia X server settings, I get, the "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root),and restart the X server", message, which I have not done.
 Other than the message my system seems to be running fine.

By 'system seems to be running fine' you mean that X is actually working with this video card?

---

### Post by pmatos on 2011-10-18
> **pmatos said:**
> By 'system seems to be running fine' you mean that X is actually working with this video card?

With your X config snippet, I am now inside X through compatibility mode (which sets nomodeset).
In normal mode I get a black screen and nothing else.

Do you actually get a high-resolution X? Mine is stuck to 1280x1024.

---

### Post by DeadlyWolf on 2011-10-19
> **pmatos said:**
> 
Do you actually get a high-resolution X? Mine is stuck to 1280x1024.

Yes, 1366x768 . This is why I have not run 'nvidia-xconfig' as root like the message advises. I had alpha's and the beta on this laptop and ran the command twice and twice it resulted in what you are experiencing. Maybe a fresh install done like I did may be the answer and I will submit a bug report. Like I posted before the only issue I have is the message and I can not use nvidia X server settings.

---

### Post by pmatos on 2011-10-19
> **DeadlyWolf said:**
> Yes, 1366x768 . This is why I have not run 'nvidia-xconfig' as root like the message advises. I had alpha's and the beta on this laptop and ran the command twice and twice it resulted in what you are experiencing. Maybe a fresh install done like I did may be the answer and I will submit a bug report. Like I posted before the only issue I have is the message and I can not use nvidia X server settings.


I can't get that... :(
Something is wierd. I will look at this once again later on once I get home and get back to you.

Thanks for the shot.

---

### Post by pmatos on 2011-10-19
> **DeadlyWolf said:**
> Yes, 1366x768 . This is why I have not run 'nvidia-xconfig' as root like the message advises. I had alpha's and the beta on this laptop and ran the command twice and twice it resulted in what you are experiencing. Maybe a fresh install done like I did may be the answer and I will submit a bug report. Like I posted before the only issue I have is the message and I can not use nvidia X server settings.

Can you please post your Xorg.0.log? Maybe that will help me understand what's the problem I am having here.

Thanks!

---

### Post by pmatos on 2011-10-19
For the record, this is my Xorg.0.log when starting Oneiric Ocelot in compatibility mode (which has 'nomodeset'). As you can see, it uses the intel_drv driver, not the NVidia one. That certainly one of the reasons why the resolution is so poor.

---

### Post by pmatos on 2011-10-19
Can you please also post your `lspci -vvv' ?

---

### Post by DeadlyWolf on 2011-10-19
lspci -vvv

```
lspci -vvv
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Dell Device 04b0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f5000000-f60fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 04ca
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 53
	Region 0: Memory at f6400000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Dell Device 04b0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7b0a000 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Dell Device 04b0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7b08000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: Dell Device 04b0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 55
	Region 0: Memory at f7b00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000f3200000-00000000f32fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=09, subordinate=0a, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: f7a00000-f7afffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=0b, subordinate=0c, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: f7900000-f79fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=11, subordinate=1f, sec-latency=0
	I/O behind bridge: 0000b000-0000cfff
	Memory behind bridge: f6800000-f78fffff
	Prefetchable memory behind bridge: 00000000f2100000-00000000f31fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
	Subsystem: Dell Device 04b0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at f7b07000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
	Subsystem: Dell Device 04b0
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 04b0
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 52
	Region 0: I/O ports at f0b0 [size=8]
	Region 1: I/O ports at f0a0 [size=4]
	Region 2: I/O ports at f090 [size=8]
	Region 3: I/O ports at f080 [size=4]
	Region 4: I/O ports at f060 [size=32]
	Region 5: Memory at f7b06000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: Dell Device 04b0
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 3
	Region 0: Memory at f7b05000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at f040 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 04ca
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f0000000 (64-bit, prefetchable) [size=32M]
	Region 5: I/O ports at e000 [size=128]
	Expansion ROM at f6000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb

01:00.1 Audio device: nVidia Corporation GF108 High Definition Audio Controller (rev a1)
	Subsystem: Dell Device 04ca
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at f6080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
	Subsystem: Dell Device 04b0
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 46
	Region 0: I/O ports at d000 [size=256]
	Region 2: Memory at f3204000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f3200000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

09:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230
	Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 54
	Region 0: Memory at f7a00000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

0b:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
	Subsystem: Dell Device 04b0
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7900000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd



```

There you go.

---

### Post by DeadlyWolf on 2011-10-19
I have Xubuntu 11.10 on the same Laptop and have the same situation with the nvidia driver, same message when I open nvidia-settings, so last night I ran nvidia-xconfig while I was using it and got the same result could not start X black screen etc; so I spent some time changing "/etc/X11/xorg.conf" around but the only way I could get it to boot properly was by returning "/etc/X11/xorg.conf" to the original one. Which is the same as Ubuntu 11.10. I got this error when I first ran nvidia-xconfig,

```
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

but as you know the New X configuration file written to '/etc/X11/xorg.conf' does not work. 

Device section "Default Device" must have a Driver line. This is what I tried to fix.

---

### Post by pmatos on 2011-10-20
isn't something missing in the beginning of your lspci output?

---

### Post by DeadlyWolf on 2011-10-20
> **pmatos said:**
> isn't something missing in the beginning of your lspci output?

Yes, I edited it.

---

### Post by pmatos on 2011-10-20
So, I think I have a pretty good idea of what's going on.

We have a Nvidia Optimus setup. I have never heard about this before but it is confirmed by your lspci. An integrated low power graphics card (intel) is supported by a heavier graphics card (nvidia) and they switch between one and the other depending on how graphics intensive is whatever you are doing. So, the problem is that using the nvidia drivers don't work because the nvidia card is in the background. The one in direct connection with everything else is the intel card. 

That's why you manage to run it using an intel driver but I bet that if you have several graphics intensive application everything will fall to the ground. We need to setup something like this:
[http://en.gentoo-wiki.com/wiki/X.Org/nVidia_Optimus](http://en.gentoo-wiki.com/wiki/X.Org/nVidia_Optimus)

However, the linux support for the automatic switching seems to be non-existent which means you have to do it manually.

I will try to set this up at home later and will let you know how I do.

If you do have any progress on your setup or find something new I haven't listed, let me know.

Thanks!

---

### Post by pmatos on 2011-10-20
You might keep track of what's happening in Ubuntu world by subscribing to these bugs:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/700646](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/700646)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/770685](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/770685)

---

### Post by DeadlyWolf on 2011-10-20
> **pmatos said:**
> You might keep track of what's happening in Ubuntu world by subscribing to these bugs:
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/660443)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/700646](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/700646)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/770685](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/770685)

 I have subscribed to the bugs as you suggested, I was aware of the  Nvidia Optimus setup but not sure of where development was in Linux. This will take some time before it's working properly out of the box. There are many computers being sold with this configuration Desktops and Laptops, so hopefully it will happen sometime soon.

---

### Post by pmatos on 2011-11-04
Still not working here, even if I just try to get the intel card going. The problem is however, not the graphics card, but the kernel. kworker gets stuck eating all of the processor. I will have to try and understand what's happening.

---

### Post by DeadlyWolf on 2011-11-07
This is lspci -vvv from an installation of openSUSE 12.1 RC2 KDE on the same computer, fresh install no configuration done.


```
lspci -vvv
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
        Subsystem: Dell Device 04b0
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
        Latency: 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>
        Kernel driver in use: agpgart-intel

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: f5000000-f60fffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000f1ffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [88] Subsystem: Dell Device 04b0
        Capabilities: [80] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4151
        Capabilities: [a0] Express (v2) Root Port (Slot+), MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #2, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <256ns, L1 <4us
                        ClockPM- Surprise- LLActRep- BwNot+
                LnkCtl: ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt+ ABWMgmt-
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
                        Slot #1, PowerLimit 75.000W; Interlock- NoCompl+
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
                        Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
                        Changed: MRL- PresDet+ LinkState-
                RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna+ CRSVisible-
                RootCap: CRSVisible-
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis- ARIFwd-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -3.5dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -3.5dB
        Capabilities: [100 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed+ WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [140 v1] Root Complex Link
                Desc:   PortNumber=02 ComponentID=01 EltType=Config
                Link0:  Desc:   TargetPort=00 TargetComponent=01 AssocRCRB- LinkType=MemMapped LinkValid+
                        Addr:   00000000fed19000
        Kernel driver in use: pcieport

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 04ca
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 47
        Region 0: Memory at f6400000 (64-bit, non-prefetchable) [size=4M]
        Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 4: I/O ports at f000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4191
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [a4] PCI Advanced Features
                AFCap: TP+ FLR+
                AFCtrl: FLR-
                AFStatus: TP-
        Kernel driver in use: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: Dell Device 04b0
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f7b0a000 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Kernel driver in use: mei

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI])
        Subsystem: Dell Device 04b0
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f7b08000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCI Advanced Features
                AFCap: TP+ FLR+
                AFCtrl: FLR-
                AFStatus: TP-
        Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: Dell Device 04b0
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 49
        Region 0: Memory at f7b00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee0f00c  Data: 41a9
        Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE- FLReset+
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=01
                        Status: NegoPending- InProgress-
                VC1:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=1 ArbSelect=Fixed TC/VC=22
                        Status: NegoPending- InProgress-
        Capabilities: [130 v1] Root Complex Link
                Desc:   PortNumber=0f ComponentID=00 EltType=Config
                Link0:  Desc:   TargetPort=00 TargetComponent=00 AssocRCRB- LinkType=MemMapped LinkValid+
                        Addr:   00000000fed1c000
        Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 0000f000-00000fff
        Memory behind bridge: fff00000-000fffff
        Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #1, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <16us
                        ClockPM- Surprise- LLActRep+ BwNot-
                LnkCtl: ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
                        Slot #0, PowerLimit 10.000W; Interlock- NoCompl+
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
                        Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
                        Changed: MRL- PresDet- LinkState-
                RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna+ CRSVisible-
                RootCap: CRSVisible-
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-
                DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -3.5dB
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4159
        Capabilities: [90] Subsystem: Dell Device 04b0
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fff00000-000fffff
        Prefetchable memory behind bridge: 00000000f3200000-00000000f32fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #2, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <16us
                        ClockPM- Surprise- LLActRep+ BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
                        Slot #1, PowerLimit 10.000W; Interlock- NoCompl+
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
                        Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
                        Changed: MRL- PresDet- LinkState+
                RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna+ CRSVisible-
                RootCap: CRSVisible-
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-
                DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -3.5dB
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4161
        Capabilities: [90] Subsystem: Dell Device 04b0
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=09, subordinate=0a, sec-latency=0
        I/O behind bridge: 0000f000-00000fff
        Memory behind bridge: f7a00000-f7afffff
        Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #4, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <16us
                        ClockPM- Surprise- LLActRep+ BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
                        Slot #3, PowerLimit 10.000W; Interlock- NoCompl+
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
                        Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
                        Changed: MRL- PresDet- LinkState+
                RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna+ CRSVisible-
                RootCap: CRSVisible-
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-
                DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -3.5dB
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4169
        Capabilities: [90] Subsystem: Dell Device 04b0
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=0b, subordinate=0c, sec-latency=0
        I/O behind bridge: 0000f000-00000fff
        Memory behind bridge: f7900000-f79fffff
        Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #5, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <16us
                        ClockPM- Surprise- LLActRep+ BwNot-
                LnkCtl: ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
                        Slot #4, PowerLimit 10.000W; Interlock- NoCompl+
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
                        Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet+ Interlock-
                        Changed: MRL- PresDet- LinkState+
                RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna+ CRSVisible-
                RootCap: CRSVisible-
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-
                DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4171
        Capabilities: [90] Subsystem: Dell Device 04b0
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pcieport

00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=11, subordinate=1f, sec-latency=0
        I/O behind bridge: 0000b000-0000cfff
        Memory behind bridge: f6800000-f78fffff
        Prefetchable memory behind bridge: 00000000f2100000-00000000f31fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
                PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
        Capabilities: [40] Express (v2) Root Port (Slot+), MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #8, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <1us, L1 <16us
                        ClockPM- Surprise- LLActRep+ BwNot-
                LnkCtl: ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x0, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                SltCap: AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+
                        Slot #7, PowerLimit 10.000W; Interlock- NoCompl+
                SltCtl: Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
                        Control: AttnInd Unknown, PwrInd Unknown, Power- Interlock-
                SltSta: Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
                        Changed: MRL- PresDet- LinkState-
                RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna+ CRSVisible-
                RootCap: CRSVisible-
                RootSta: PME ReqID 0000, PMEStatus- PMEPending-
                DevCap2: Completion Timeout: Range BC, TimeoutDis+ ARIFwd-
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis- ARIFwd-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -3.5dB
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4179
        Capabilities: [90] Subsystem: Dell Device 04b0
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: pcieport

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI])
        Subsystem: Dell Device 04b0
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at f7b07000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Debug port: BAR=1 offset=00a0
        Capabilities: [98] PCI Advanced Features
                AFCap: TP+ FLR+
                AFCtrl: FLR-
                AFStatus: TP-
        Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
        Subsystem: Dell Device 04b0
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Capabilities: [e0] Vendor Specific Information: Len=0c <?>

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Device 04b0
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin B routed to IRQ 46
        Region 0: I/O ports at f0b0 [size=8]
        Region 1: I/O ports at f0a0 [size=4]
        Region 2: I/O ports at f090 [size=8]
        Region 3: I/O ports at f080 [size=4]
        Region 4: I/O ports at f060 [size=32]
        Region 5: Memory at f7b06000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
                Address: fee0f00c  Data: 4181
        Capabilities: [70] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [a8] SATA HBA v1.0 BAR4 Offset=00000004
        Capabilities: [b0] PCI Advanced Features
                AFCap: TP+ FLR+
                AFCtrl: FLR-
                AFStatus: TP-
        Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
        Subsystem: Dell Device 04b0
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin C routed to IRQ 18
        Region 0: Memory at f7b05000 (64-bit, non-prefetchable) [size=256]
        Region 4: I/O ports at f040 [size=32]
        Kernel driver in use: i801_smbus

01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 04ca
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at f0000000 (64-bit, prefetchable) [size=32M]
        Region 5: I/O ports at e000 [size=128]
        Expansion ROM at f6000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [78] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 <64us
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <4us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -3.5dB
        Capabilities: [b4] Vendor Specific Information: Len=14 <?>
        Capabilities: [100 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [128 v1] Power Budgeting <?>
        Capabilities: [600 v1] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
        Kernel driver in use: nouveau

01:00.1 Audio device: nVidia Corporation GF108 High Definition Audio Controller (rev a1)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at f6080000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [78] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x16, ASPM L0s L1, Latency L0 <512ns, L1 <4us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -3.5dB
        Kernel driver in use: snd_hda_intel

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
        Subsystem: Dell Device 04b0
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 48
        Region 0: I/O ports at d000 [size=256]
        Region 2: Memory at f3204000 (64-bit, prefetchable) [size=4K]
        Region 4: Memory at f3200000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee0f00c  Data: 4199
        Capabilities: [70] Express (v2) Endpoint, MSI 01
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 <64us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
                Vector table: BAR=4 offset=00000000
                PBA: BAR=4 offset=00000800
        Capabilities: [d0] Vital Product Data
                Unknown small resource type 00, will not decode more.
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [140 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [160 v1] Device Serial Number 01-00-00-00-36-4c-e0-00
        Kernel driver in use: r8169

09:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230
        Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 50
        Region 0: Memory at f7a00000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
                Address: 00000000fee0f00c  Data: 41b1
        Capabilities: [e0] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <32us
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [140 v1] Device Serial Number 00-15-00-ff-ff-76-27-1c
        Kernel driver in use: iwlagn

0b:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
        Subsystem: Dell Device 04b0
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f7900000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [70] MSI: Enable- Count=1/8 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [90] MSI-X: Enable+ Count=8 Masked-
                Vector table: BAR=0 offset=00001000
                PBA: BAR=0 offset=00001080
        Capabilities: [a0] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 unlimited
                        ClockPM+ Surprise- LLActRep- BwNot-
                LnkCtl: ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [140 v1] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
        Capabilities: [150 v1] #18
        Kernel driver in use: xhci_hcd

linux-l6og:/home/michael # 

```

---

### Post by gauravpadia on 2011-11-07
Hello Guys,

I suggest don't waste time on setting up nvidia driver, because nvidia original driver don't have optimus support on linux and Nvidia company don't have any plan in near future to support it.

Nvidia optimus card works differently then normal graphics cards.

But there are some other good guys which are working on providing optimus support on linux. Here is the link to the project - [https://github.com/MrMEEE/ironhide](https://github.com/MrMEEE/ironhide)

So what you have to do is install nvidia drivers from restricted drives and then blacklist the nvidia module (because as you know you are all getting black screen after nvidia driver installation) then top of this install this ironhide project.

After installing ironhide, you can run 3D applications with nvidia card by running command "optirun application-name".

Sorry if I am not much clear, I'm not very good with English.

Thanks.

---

### Post by pmatos on 2011-11-07
> **gauravpadia said:**
> Hello Guys,

I suggest don't waste time on setting up nvidia driver, because nvidia original driver don't have optimus support on linux and Nvidia company don't have any plan in near future to support it.

Nvidia optimus card works differently then normal graphics cards.

But there are some other good guys which are working on providing optimus support on linux. Here is the link to the project - [https://github.com/MrMEEE/ironhide](https://github.com/MrMEEE/ironhide)

So what you have to do is install nvidia drivers from restricted drives and then blacklist the nvidia module (because as you know you are all getting black screen after nvidia driver installation) then top of this install this ironhide project.

After installing ironhide, you can run 3D applications with nvidia card by running command "optirun application-name".

Sorry if I am not much clear, I'm not very good with English.

Thanks.

I installed nvidia drivers and blacklisted it by adding:
```
blacklist nvidia 
```
to /etc/modprobe.d/blacklist.local

Unfortunately, I am still getting a black screen. I noted by ssh'ing the PC while black screen is on that 4 processes of kworker are eating my CPU. :-/ 

Argh... I hate this nvidia thingy... should have known better before buying this pc....

---

### Post by gauravpadia on 2011-11-07
pmatos, you also need to remove /etc/X11/xorg.conf file... you can rename with different name and then try. I think then blank screen should not come.

---

### Post by pmatos on 2011-11-09
> **gauravpadia said:**
> pmatos, you also need to remove /etc/X11/xorg.conf file... you can rename with different name and then try. I think then blank screen should not come.

Strange I added the blacklist nvidia to blacklist.conf but the driver is still being loaded...

---

### Post by pmatos on 2011-11-09
> **pmatos said:**
> Strange I added the blacklist nvidia to blacklist.conf but the driver is still being loaded...

OK, so I reinstalled ubuntu. Removed all nvidia-drivers and my aim is just to get the right resolution with the intel driver. Also blacklisted nouveau, just in case.

I can start if I write in the beginning 'nomodeset', otherwise with the intel card I still get the annoying black screen.

Here's the Xorg.0.log with nomodeset:
```
[    17.923] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    17.923] X Protocol Version 11, Revision 0
[    17.923] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    17.923] Current Operating System: Linux athena 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    17.923] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=6f471731-4074-41a1-b9ab-fea2c6469ac4 ro quiet splash vt.handoff=7 nomodeset
[    17.923] Build Date: 19 October 2011  05:21:26AM
[    17.923] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    17.923] Current version of pixman: 0.22.2
[    17.923] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.923] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.923] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  9 21:41:34 2011
[    17.923] (==) Using config file: "/etc/X11/xorg.conf"
[    17.923] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.923] (==) No Layout section.  Using the first Screen section.
[    17.923] (==) No screen section available. Using defaults.
[    17.923] (**) |-->Screen "Default Screen Section" (0)
[    17.923] (**) |   |-->Monitor "<default monitor>"
[    17.923] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    17.923] (**) |   |-->Device "Default Device"
[    17.923] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    17.923] (==) Automatically adding devices
[    17.923] (==) Automatically enabling devices
[    17.924] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.924] 	Entry deleted from font path.
[    17.924] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.924] 	Entry deleted from font path.
[    17.924] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.924] 	Entry deleted from font path.
[    17.924] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.924] 	Entry deleted from font path.
[    17.924] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.924] 	Entry deleted from font path.
[    17.924] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.924] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.924] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.924] (II) Loader magic: 0x7e0220
[    17.924] (II) Module ABI versions:
[    17.924] 	X.Org ANSI C Emulation: 0.4
[    17.924] 	X.Org Video Driver: 10.0
[    17.924] 	X.Org XInput driver : 12.3
[    17.924] 	X.Org Server Extension : 5.0
[    17.924] (--) PCI:*(0:0:2:0) 8086:0102:1028:0512 rev 9, Mem @ 0xfb400000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    17.924] (--) PCI: (0:1:0:0) 10de:0df5:1028:0512 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    17.924] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.924] (II) LoadModule: "extmod"
[    17.941] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.941] (II) Module extmod: vendor="X.Org Foundation"
[    17.941] 	compiled for 1.10.4, module version = 1.0.0
[    17.941] 	Module class: X.Org Server Extension
[    17.941] 	ABI class: X.Org Server Extension, version 5.0
[    17.941] (II) Loading extension MIT-SCREEN-SAVER
[    17.941] (II) Loading extension XFree86-VidModeExtension
[    17.941] (II) Loading extension XFree86-DGA
[    17.941] (II) Loading extension DPMS
[    17.941] (II) Loading extension XVideo
[    17.941] (II) Loading extension XVideo-MotionCompensation
[    17.941] (II) Loading extension X-Resource
[    17.941] (II) LoadModule: "dbe"
[    17.941] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.941] (II) Module dbe: vendor="X.Org Foundation"
[    17.941] 	compiled for 1.10.4, module version = 1.0.0
[    17.941] 	Module class: X.Org Server Extension
[    17.941] 	ABI class: X.Org Server Extension, version 5.0
[    17.941] (II) Loading extension DOUBLE-BUFFER
[    17.941] (II) LoadModule: "glx"
[    17.941] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.941] (II) Module glx: vendor="X.Org Foundation"
[    17.941] 	compiled for 1.10.4, module version = 1.0.0
[    17.941] 	ABI class: X.Org Server Extension, version 5.0
[    17.941] (==) AIGLX enabled
[    17.941] (II) Loading extension GLX
[    17.941] (II) LoadModule: "record"
[    17.942] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.942] (II) Module record: vendor="X.Org Foundation"
[    17.942] 	compiled for 1.10.4, module version = 1.13.0
[    17.942] 	Module class: X.Org Server Extension
[    17.942] 	ABI class: X.Org Server Extension, version 5.0
[    17.942] (II) Loading extension RECORD
[    17.942] (II) LoadModule: "dri"
[    17.942] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.942] (II) Module dri: vendor="X.Org Foundation"
[    17.942] 	compiled for 1.10.4, module version = 1.0.0
[    17.942] 	ABI class: X.Org Server Extension, version 5.0
[    17.942] (II) Loading extension XFree86-DRI
[    17.942] (II) LoadModule: "dri2"
[    17.942] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.942] (II) Module dri2: vendor="X.Org Foundation"
[    17.942] 	compiled for 1.10.4, module version = 1.2.0
[    17.942] 	ABI class: X.Org Server Extension, version 5.0
[    17.942] (II) Loading extension DRI2
[    17.942] (==) Matched intel as autoconfigured driver 0
[    17.942] (==) Matched vesa as autoconfigured driver 1
[    17.942] (==) Matched fbdev as autoconfigured driver 2
[    17.942] (==) Assigned the driver to the xf86ConfigLayout
[    17.942] (II) LoadModule: "intel"
[    17.942] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.942] (II) Module intel: vendor="X.Org Foundation"
[    17.942] 	compiled for 1.10.2.902, module version = 2.15.901
[    17.942] 	Module class: X.Org Video Driver
[    17.942] 	ABI class: X.Org Video Driver, version 10.0
[    17.942] (II) LoadModule: "vesa"
[    17.942] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.942] (II) Module vesa: vendor="X.Org Foundation"
[    17.942] 	compiled for 1.10.2, module version = 2.3.0
[    17.942] 	Module class: X.Org Video Driver
[    17.942] 	ABI class: X.Org Video Driver, version 10.0
[    17.942] (II) LoadModule: "fbdev"
[    17.943] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.943] (II) Module fbdev: vendor="X.Org Foundation"
[    17.943] 	compiled for 1.10.0, module version = 0.4.2
[    17.943] 	ABI class: X.Org Video Driver, version 10.0
[    17.943] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    17.943] (II) VESA: driver for VESA chipsets: vesa
[    17.943] (II) FBDEV: driver for framebuffer: fbdev
[    17.943] (++) using VT number 7

[    17.944] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.944] (WW) Falling back to old probe method for fbdev
[    17.944] (II) Loading sub module "fbdevhw"
[    17.944] (II) LoadModule: "fbdevhw"
[    17.944] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.944] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.944] 	compiled for 1.10.4, module version = 0.0.2
[    17.944] 	ABI class: X.Org Video Driver, version 10.0
[    17.944] (II) Loading sub module "vbe"
[    17.944] (II) LoadModule: "vbe"
[    17.945] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    17.982] (II) Module vbe: vendor="X.Org Foundation"
[    17.982] 	compiled for 1.10.4, module version = 1.1.0
[    17.982] 	ABI class: X.Org Video Driver, version 10.0
[    17.982] (II) Loading sub module "int10"
[    17.982] (II) LoadModule: "int10"
[    17.983] (II) Loading /usr/lib/xorg/modules/libint10.so
[    18.000] (II) Module int10: vendor="X.Org Foundation"
[    18.000] 	compiled for 1.10.4, module version = 1.0.0
[    18.000] 	ABI class: X.Org Video Driver, version 10.0
[    18.000] (II) VESA(0): initializing int10
[    18.001] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    18.001] (II) VESA(0): VESA BIOS detected
[    18.001] (II) VESA(0): VESA VBE Version 3.0
[    18.001] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[    18.001] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
[    18.001] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    18.001] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    18.001] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
[    18.001] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    18.005] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    18.005] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    18.005] (==) VESA(0): RGB weight 888
[    18.005] (==) VESA(0): Default visual is TrueColor
[    18.005] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.005] (II) Loading sub module "ddc"
[    18.005] (II) LoadModule: "ddc"
[    18.005] (II) Module "ddc" already built-in
[    18.049] (II) VESA(0): VESA VBE DDC supported
[    18.049] (II) VESA(0): VESA VBE DDC Level 2
[    18.049] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    18.057] (II) VESA(0): VESA VBE DDC read successfully
[    18.057] (II) VESA(0): Manufacturer: CHR  Model: 608  Serial#: 880
[    18.057] (II) VESA(0): Year: 2011  Week: 21
[    18.057] (II) VESA(0): EDID Version: 1.4
[    18.057] (II) VESA(0): Digital Display Input
[    18.057] (II) VESA(0): 8 bits per channel
[    18.057] (II) VESA(0): Digital interface is DisplayPort
[    18.057] (II) VESA(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    18.057] (II) VESA(0): Gamma: 2.20
[    18.057] (II) VESA(0): DPMS capabilities: StandBy Suspend Off
[    18.057] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.057] (II) VESA(0): First detailed timing is preferred mode
[    18.057] (II) VESA(0): Preferred mode is native pixel format and refresh rate
[    18.057] (II) VESA(0): redX: 0.674 redY: 0.316   greenX: 0.188 greenY: 0.703
[    18.057] (II) VESA(0): blueX: 0.146 blueY: 0.062   whiteX: 0.312 whiteY: 0.326
[    18.057] (II) VESA(0): Manufacturer's mask: 0
[    18.057] (II) VESA(0): Supported detailed timing:
[    18.057] (II) VESA(0): clock: 134.6 MHz   Image Size:  509 x 286 mm
[    18.057] (II) VESA(0): h_active: 1920  h_sync: 1936  h_sync_end 1968 h_blank_end 2020 h_border: 0
[    18.057] (II) VESA(0): v_active: 1080  v_sync: 1085  v_sync_end 1095 v_blanking: 1111 v_border: 0
[    18.057] (II) VESA(0): Established timings III: (not decoded)
[    18.057] (II) VESA(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    18.057] (II) VESA(0): Monitor name: 23" AIO
[    18.057] (II) VESA(0): EDID (in hex):
[    18.057] (II) VESA(0): 	00ffffffffffff000d12080670030000
[    18.057] (II) VESA(0): 	15150104a5342078ea8042ac5130b425
[    18.057] (II) VESA(0): 	10505300000001010101010101010101
[    18.057] (II) VESA(0): 	0101010101019434806470381f401020
[    18.057] (II) VESA(0): 	5a00fd1e1100001c000000f7000a0000
[    18.057] (II) VESA(0): 	00000000000000000000000000fd0038
[    18.057] (II) VESA(0): 	4c1e5311000a202020202020000000fc
[    18.057] (II) VESA(0): 	003233222041494f0a202020202000d8
[    18.057] (II) VESA(0): EDID vendor "CHR", prod id 1544
[    18.057] (II) VESA(0): Using EDID range info for horizontal sync
[    18.057] (II) VESA(0): Using EDID range info for vertical refresh
[    18.057] (II) VESA(0): Printing DDC gathered Modelines:
[    18.057] (II) VESA(0): Modeline "1920x1080"x0.0  134.60  1920 1936 1968 2020  1080 1085 1095 1111 -hsync +vsync (66.6 kHz)
[    18.057] (II) VESA(0): Searching for matching VESA mode(s):
[    18.057] Mode: 160 (0x0)
[    18.057] 	ModeAttributes: 0x0
[    18.057] 	WinAAttributes: 0x0
[    18.057] 	WinBAttributes: 0x0
[    18.057] 	WinGranularity: 0
[    18.057] 	WinSize: 0
[    18.057] 	WinASegment: 0x0
[    18.057] 	WinBSegment: 0x0
[    18.057] 	WinFuncPtr: 0x0
[    18.057] 	BytesPerScanline: 0
[    18.057] 	XResolution: 0
[    18.057] 	YResolution: 0
[    18.057] 	XCharSize: 0
[    18.057] 	YCharSize: 0
[    18.057] 	NumberOfPlanes: 0
[    18.057] 	BitsPerPixel: 0
[    18.057] 	NumberOfBanks: 0
[    18.057] 	MemoryModel: 0
[    18.057] 	BankSize: 0
[    18.057] 	NumberOfImages: 0
[    18.057] 	RedMaskSize: 0
[    18.057] 	RedFieldPosition: 0
[    18.057] 	GreenMaskSize: 0
[    18.057] 	GreenFieldPosition: 0
[    18.057] 	BlueMaskSize: 0
[    18.057] 	BlueFieldPosition: 0
[    18.057] 	RsvdMaskSize: 0
[    18.057] 	RsvdFieldPosition: 0
[    18.057] 	DirectColorModeInfo: 0
[    18.057] 	PhysBasePtr: 0x0
[    18.057] 	LinBytesPerScanLine: 0
[    18.057] 	BnkNumberOfImagePages: 0
[    18.057] 	LinNumberOfImagePages: 0
[    18.057] 	LinRedMaskSize: 0
[    18.057] 	LinRedFieldPosition: 0
[    18.057] 	LinGreenMaskSize: 0
[    18.057] 	LinGreenFieldPosition: 0
[    18.057] 	LinBlueMaskSize: 0
[    18.057] 	LinBlueFieldPosition: 0
[    18.057] 	LinRsvdMaskSize: 0
[    18.057] 	LinRsvdFieldPosition: 0
[    18.057] 	MaxPixelClock: 0
[    18.057] Mode: 161 (0x0)
[    18.057] 	ModeAttributes: 0x0
[    18.057] 	WinAAttributes: 0x0
[    18.057] 	WinBAttributes: 0x0
[    18.057] 	WinGranularity: 0
[    18.057] 	WinSize: 0
[    18.057] 	WinASegment: 0x0
[    18.057] 	WinBSegment: 0x0
[    18.057] 	WinFuncPtr: 0x0
[    18.057] 	BytesPerScanline: 0
[    18.057] 	XResolution: 0
[    18.057] 	YResolution: 0
[    18.057] 	XCharSize: 0
[    18.057] 	YCharSize: 0
[    18.057] 	NumberOfPlanes: 0
[    18.057] 	BitsPerPixel: 0
[    18.057] 	NumberOfBanks: 0
[    18.057] 	MemoryModel: 0
[    18.057] 	BankSize: 0
[    18.057] 	NumberOfImages: 0
[    18.057] 	RedMaskSize: 0
[    18.057] 	RedFieldPosition: 0
[    18.057] 	GreenMaskSize: 0
[    18.057] 	GreenFieldPosition: 0
[    18.057] 	BlueMaskSize: 0
[    18.057] 	BlueFieldPosition: 0
[    18.057] 	RsvdMaskSize: 0
[    18.057] 	RsvdFieldPosition: 0
[    18.057] 	DirectColorModeInfo: 0
[    18.057] 	PhysBasePtr: 0x0
[    18.057] 	LinBytesPerScanLine: 0
[    18.057] 	BnkNumberOfImagePages: 0
[    18.057] 	LinNumberOfImagePages: 0
[    18.057] 	LinRedMaskSize: 0
[    18.057] 	LinRedFieldPosition: 0
[    18.057] 	LinGreenMaskSize: 0
[    18.057] 	LinGreenFieldPosition: 0
[    18.057] 	LinBlueMaskSize: 0
[    18.057] 	LinBlueFieldPosition: 0
[    18.057] 	LinRsvdMaskSize: 0
[    18.057] 	LinRsvdFieldPosition: 0
[    18.057] 	MaxPixelClock: 0
[    18.057] Mode: 162 (0x0)
[    18.057] 	ModeAttributes: 0x0
[    18.057] 	WinAAttributes: 0x0
[    18.057] 	WinBAttributes: 0x0
[    18.057] 	WinGranularity: 0
[    18.057] 	WinSize: 0
[    18.057] 	WinASegment: 0x0
[    18.057] 	WinBSegment: 0x0
[    18.057] 	WinFuncPtr: 0x0
[    18.057] 	BytesPerScanline: 0
[    18.057] 	XResolution: 0
[    18.057] 	YResolution: 0
[    18.057] 	XCharSize: 0
[    18.057] 	YCharSize: 0
[    18.057] 	NumberOfPlanes: 0
[    18.057] 	BitsPerPixel: 0
[    18.057] 	NumberOfBanks: 0
[    18.057] 	MemoryModel: 0
[    18.057] 	BankSize: 0
[    18.057] 	NumberOfImages: 0
[    18.057] 	RedMaskSize: 0
[    18.057] 	RedFieldPosition: 0
[    18.057] 	GreenMaskSize: 0
[    18.057] 	GreenFieldPosition: 0
[    18.057] 	BlueMaskSize: 0
[    18.057] 	BlueFieldPosition: 0
[    18.057] 	RsvdMaskSize: 0
[    18.057] 	RsvdFieldPosition: 0
[    18.057] 	DirectColorModeInfo: 0
[    18.057] 	PhysBasePtr: 0x0
[    18.057] 	LinBytesPerScanLine: 0
[    18.057] 	BnkNumberOfImagePages: 0
[    18.057] 	LinNumberOfImagePages: 0
[    18.057] 	LinRedMaskSize: 0
[    18.057] 	LinRedFieldPosition: 0
[    18.057] 	LinGreenMaskSize: 0
[    18.057] 	LinGreenFieldPosition: 0
[    18.057] 	LinBlueMaskSize: 0
[    18.057] 	LinBlueFieldPosition: 0
[    18.057] 	LinRsvdMaskSize: 0
[    18.057] 	LinRsvdFieldPosition: 0
[    18.057] 	MaxPixelClock: 0
[    18.058] Mode: 163 (0x0)
[    18.058] 	ModeAttributes: 0x0
[    18.058] 	WinAAttributes: 0x0
[    18.058] 	WinBAttributes: 0x0
[    18.058] 	WinGranularity: 0
[    18.058] 	WinSize: 0
[    18.058] 	WinASegment: 0x0
[    18.058] 	WinBSegment: 0x0
[    18.058] 	WinFuncPtr: 0x0
[    18.058] 	BytesPerScanline: 0
[    18.058] 	XResolution: 0
[    18.058] 	YResolution: 0
[    18.058] 	XCharSize: 0
[    18.058] 	YCharSize: 0
[    18.058] 	NumberOfPlanes: 0
[    18.058] 	BitsPerPixel: 0
[    18.058] 	NumberOfBanks: 0
[    18.058] 	MemoryModel: 0
[    18.058] 	BankSize: 0
[    18.058] 	NumberOfImages: 0
[    18.058] 	RedMaskSize: 0
[    18.058] 	RedFieldPosition: 0
[    18.058] 	GreenMaskSize: 0
[    18.058] 	GreenFieldPosition: 0
[    18.058] 	BlueMaskSize: 0
[    18.058] 	BlueFieldPosition: 0
[    18.058] 	RsvdMaskSize: 0
[    18.058] 	RsvdFieldPosition: 0
[    18.058] 	DirectColorModeInfo: 0
[    18.058] 	PhysBasePtr: 0x0
[    18.058] 	LinBytesPerScanLine: 0
[    18.058] 	BnkNumberOfImagePages: 0
[    18.058] 	LinNumberOfImagePages: 0
[    18.058] 	LinRedMaskSize: 0
[    18.058] 	LinRedFieldPosition: 0
[    18.058] 	LinGreenMaskSize: 0
[    18.058] 	LinGreenFieldPosition: 0
[    18.058] 	LinBlueMaskSize: 0
[    18.058] 	LinBlueFieldPosition: 0
[    18.058] 	LinRsvdMaskSize: 0
[    18.058] 	LinRsvdFieldPosition: 0
[    18.058] 	MaxPixelClock: 0
[    18.058] Mode: 164 (0x0)
[    18.058] 	ModeAttributes: 0x0
[    18.058] 	WinAAttributes: 0x0
[    18.058] 	WinBAttributes: 0x0
[    18.058] 	WinGranularity: 0
[    18.058] 	WinSize: 0
[    18.058] 	WinASegment: 0x0
[    18.058] 	WinBSegment: 0x0
[    18.058] 	WinFuncPtr: 0x0
[    18.058] 	BytesPerScanline: 0
[    18.058] 	XResolution: 0
[    18.058] 	YResolution: 0
[    18.058] 	XCharSize: 0
[    18.058] 	YCharSize: 0
[    18.058] 	NumberOfPlanes: 0
[    18.058] 	BitsPerPixel: 0
[    18.058] 	NumberOfBanks: 0
[    18.058] 	MemoryModel: 0
[    18.058] 	BankSize: 0
[    18.058] 	NumberOfImages: 0
[    18.058] 	RedMaskSize: 0
[    18.058] 	RedFieldPosition: 0
[    18.058] 	GreenMaskSize: 0
[    18.058] 	GreenFieldPosition: 0
[    18.058] 	BlueMaskSize: 0
[    18.058] 	BlueFieldPosition: 0
[    18.058] 	RsvdMaskSize: 0
[    18.058] 	RsvdFieldPosition: 0
[    18.058] 	DirectColorModeInfo: 0
[    18.058] 	PhysBasePtr: 0x0
[    18.058] 	LinBytesPerScanLine: 0
[    18.058] 	BnkNumberOfImagePages: 0
[    18.058] 	LinNumberOfImagePages: 0
[    18.058] 	LinRedMaskSize: 0
[    18.058] 	LinRedFieldPosition: 0
[    18.058] 	LinGreenMaskSize: 0
[    18.058] 	LinGreenFieldPosition: 0
[    18.058] 	LinBlueMaskSize: 0
[    18.058] 	LinBlueFieldPosition: 0
[    18.058] 	LinRsvdMaskSize: 0
[    18.058] 	LinRsvdFieldPosition: 0
[    18.058] 	MaxPixelClock: 0
[    18.058] Mode: 165 (0x0)
[    18.058] 	ModeAttributes: 0x0
[    18.058] 	WinAAttributes: 0x0
[    18.058] 	WinBAttributes: 0x0
[    18.058] 	WinGranularity: 0
[    18.058] 	WinSize: 0
[    18.058] 	WinASegment: 0x0
[    18.058] 	WinBSegment: 0x0
[    18.058] 	WinFuncPtr: 0x0
[    18.058] 	BytesPerScanline: 0
[    18.058] 	XResolution: 0
[    18.058] 	YResolution: 0
[    18.058] 	XCharSize: 0
[    18.058] 	YCharSize: 0
[    18.058] 	NumberOfPlanes: 0
[    18.058] 	BitsPerPixel: 0
[    18.058] 	NumberOfBanks: 0
[    18.058] 	MemoryModel: 0
[    18.058] 	BankSize: 0
[    18.058] 	NumberOfImages: 0
[    18.058] 	RedMaskSize: 0
[    18.058] 	RedFieldPosition: 0
[    18.058] 	GreenMaskSize: 0
[    18.058] 	GreenFieldPosition: 0
[    18.058] 	BlueMaskSize: 0
[    18.058] 	BlueFieldPosition: 0
[    18.058] 	RsvdMaskSize: 0
[    18.058] 	RsvdFieldPosition: 0
[    18.058] 	DirectColorModeInfo: 0
[    18.058] 	PhysBasePtr: 0x0
[    18.058] 	LinBytesPerScanLine: 0
[    18.058] 	BnkNumberOfImagePages: 0
[    18.058] 	LinNumberOfImagePages: 0
[    18.058] 	LinRedMaskSize: 0
[    18.058] 	LinRedFieldPosition: 0
[    18.058] 	LinGreenMaskSize: 0
[    18.058] 	LinGreenFieldPosition: 0
[    18.058] 	LinBlueMaskSize: 0
[    18.058] 	LinBlueFieldPosition: 0
[    18.058] 	LinRsvdMaskSize: 0
[    18.058] 	LinRsvdFieldPosition: 0
[    18.058] 	MaxPixelClock: 0
[    18.058] Mode: 166 (0x0)
[    18.058] 	ModeAttributes: 0x0
[    18.058] 	WinAAttributes: 0x0
[    18.058] 	WinBAttributes: 0x0
[    18.058] 	WinGranularity: 0
[    18.058] 	WinSize: 0
[    18.058] 	WinASegment: 0x0
[    18.058] 	WinBSegment: 0x0
[    18.058] 	WinFuncPtr: 0x0
[    18.058] 	BytesPerScanline: 0
[    18.058] 	XResolution: 0
[    18.058] 	YResolution: 0
[    18.058] 	XCharSize: 0
[    18.058] 	YCharSize: 0
[    18.058] 	NumberOfPlanes: 0
[    18.058] 	BitsPerPixel: 0
[    18.058] 	NumberOfBanks: 0
[    18.058] 	MemoryModel: 0
[    18.058] 	BankSize: 0
[    18.058] 	NumberOfImages: 0
[    18.058] 	RedMaskSize: 0
[    18.058] 	RedFieldPosition: 0
[    18.058] 	GreenMaskSize: 0
[    18.058] 	GreenFieldPosition: 0
[    18.058] 	BlueMaskSize: 0
[    18.058] 	BlueFieldPosition: 0
[    18.058] 	RsvdMaskSize: 0
[    18.058] 	RsvdFieldPosition: 0
[    18.058] 	DirectColorModeInfo: 0
[    18.058] 	PhysBasePtr: 0x0
[    18.058] 	LinBytesPerScanLine: 0
[    18.058] 	BnkNumberOfImagePages: 0
[    18.058] 	LinNumberOfImagePages: 0
[    18.058] 	LinRedMaskSize: 0
[    18.058] 	LinRedFieldPosition: 0
[    18.058] 	LinGreenMaskSize: 0
[    18.058] 	LinGreenFieldPosition: 0
[    18.058] 	LinBlueMaskSize: 0
[    18.058] 	LinBlueFieldPosition: 0
[    18.058] 	LinRsvdMaskSize: 0
[    18.058] 	LinRsvdFieldPosition: 0
[    18.058] 	MaxPixelClock: 0
[    18.058] Mode: 167 (0x0)
[    18.058] 	ModeAttributes: 0x0
[    18.058] 	WinAAttributes: 0x0
[    18.058] 	WinBAttributes: 0x0
[    18.058] 	WinGranularity: 0
[    18.058] 	WinSize: 0
[    18.058] 	WinASegment: 0x0
[    18.058] 	WinBSegment: 0x0
[    18.058] 	WinFuncPtr: 0x0
[    18.058] 	BytesPerScanline: 0
[    18.058] 	XResolution: 0
[    18.058] 	YResolution: 0
[    18.058] 	XCharSize: 0
[    18.058] 	YCharSize: 0
[    18.058] 	NumberOfPlanes: 0
[    18.058] 	BitsPerPixel: 0
[    18.058] 	NumberOfBanks: 0
[    18.058] 	MemoryModel: 0
[    18.058] 	BankSize: 0
[    18.058] 	NumberOfImages: 0
[    18.058] 	RedMaskSize: 0
[    18.058] 	RedFieldPosition: 0
[    18.058] 	GreenMaskSize: 0
[    18.058] 	GreenFieldPosition: 0
[    18.058] 	BlueMaskSize: 0
[    18.058] 	BlueFieldPosition: 0
[    18.058] 	RsvdMaskSize: 0
[    18.058] 	RsvdFieldPosition: 0
[    18.058] 	DirectColorModeInfo: 0
[    18.058] 	PhysBasePtr: 0x0
[    18.058] 	LinBytesPerScanLine: 0
[    18.058] 	BnkNumberOfImagePages: 0
[    18.058] 	LinNumberOfImagePages: 0
[    18.058] 	LinRedMaskSize: 0
[    18.058] 	LinRedFieldPosition: 0
[    18.058] 	LinGreenMaskSize: 0
[    18.058] 	LinGreenFieldPosition: 0
[    18.058] 	LinBlueMaskSize: 0
[    18.058] 	LinBlueFieldPosition: 0
[    18.058] 	LinRsvdMaskSize: 0
[    18.058] 	LinRsvdFieldPosition: 0
[    18.058] 	MaxPixelClock: 0
[    18.058] Mode: 168 (0x0)
[    18.059] 	ModeAttributes: 0x0
[    18.059] 	WinAAttributes: 0x0
[    18.059] 	WinBAttributes: 0x0
[    18.059] 	WinGranularity: 0
[    18.059] 	WinSize: 0
[    18.059] 	WinASegment: 0x0
[    18.059] 	WinBSegment: 0x0
[    18.059] 	WinFuncPtr: 0x0
[    18.059] 	BytesPerScanline: 0
[    18.059] 	XResolution: 0
[    18.059] 	YResolution: 0
[    18.059] 	XCharSize: 0
[    18.059] 	YCharSize: 0
[    18.059] 	NumberOfPlanes: 0
[    18.059] 	BitsPerPixel: 0
[    18.059] 	NumberOfBanks: 0
[    18.059] 	MemoryModel: 0
[    18.059] 	BankSize: 0
[    18.059] 	NumberOfImages: 0
[    18.059] 	RedMaskSize: 0
[    18.059] 	RedFieldPosition: 0
[    18.059] 	GreenMaskSize: 0
[    18.059] 	GreenFieldPosition: 0
[    18.059] 	BlueMaskSize: 0
[    18.059] 	BlueFieldPosition: 0
[    18.059] 	RsvdMaskSize: 0
[    18.059] 	RsvdFieldPosition: 0
[    18.059] 	DirectColorModeInfo: 0
[    18.059] 	PhysBasePtr: 0x0
[    18.059] 	LinBytesPerScanLine: 0
[    18.059] 	BnkNumberOfImagePages: 0
[    18.059] 	LinNumberOfImagePages: 0
[    18.059] 	LinRedMaskSize: 0
[    18.059] 	LinRedFieldPosition: 0
[    18.059] 	LinGreenMaskSize: 0
[    18.059] 	LinGreenFieldPosition: 0
[    18.059] 	LinBlueMaskSize: 0
[    18.059] 	LinBlueFieldPosition: 0
[    18.059] 	LinRsvdMaskSize: 0
[    18.059] 	LinRsvdFieldPosition: 0
[    18.059] 	MaxPixelClock: 0
[    18.059] Mode: 13c (0x0)
[    18.059] 	ModeAttributes: 0x0
[    18.059] 	WinAAttributes: 0x0
[    18.059] 	WinBAttributes: 0x0
[    18.059] 	WinGranularity: 0
[    18.059] 	WinSize: 0
[    18.059] 	WinASegment: 0x0
[    18.059] 	WinBSegment: 0x0
[    18.059] 	WinFuncPtr: 0x0
[    18.059] 	BytesPerScanline: 0
[    18.059] 	XResolution: 0
[    18.059] 	YResolution: 0
[    18.059] 	XCharSize: 0
[    18.059] 	YCharSize: 0
[    18.059] 	NumberOfPlanes: 0
[    18.059] 	BitsPerPixel: 0
[    18.059] 	NumberOfBanks: 0
[    18.059] 	MemoryModel: 0
[    18.059] 	BankSize: 0
[    18.059] 	NumberOfImages: 0
[    18.059] 	RedMaskSize: 0
[    18.059] 	RedFieldPosition: 0
[    18.059] 	GreenMaskSize: 0
[    18.059] 	GreenFieldPosition: 0
[    18.059] 	BlueMaskSize: 0
[    18.059] 	BlueFieldPosition: 0
[    18.059] 	RsvdMaskSize: 0
[    18.059] 	RsvdFieldPosition: 0
[    18.059] 	DirectColorModeInfo: 0
[    18.059] 	PhysBasePtr: 0x0
[    18.059] 	LinBytesPerScanLine: 0
[    18.059] 	BnkNumberOfImagePages: 0
[    18.059] 	LinNumberOfImagePages: 0
[    18.059] 	LinRedMaskSize: 0
[    18.059] 	LinRedFieldPosition: 0
[    18.059] 	LinGreenMaskSize: 0
[    18.059] 	LinGreenFieldPosition: 0
[    18.059] 	LinBlueMaskSize: 0
[    18.059] 	LinBlueFieldPosition: 0
[    18.059] 	LinRsvdMaskSize: 0
[    18.059] 	LinRsvdFieldPosition: 0
[    18.059] 	MaxPixelClock: 0
[    18.059] Mode: 14d (0x0)
[    18.059] 	ModeAttributes: 0x0
[    18.059] 	WinAAttributes: 0x0
[    18.059] 	WinBAttributes: 0x0
[    18.059] 	WinGranularity: 0
[    18.059] 	WinSize: 0
[    18.059] 	WinASegment: 0x0
[    18.059] 	WinBSegment: 0x0
[    18.059] 	WinFuncPtr: 0x0
[    18.059] 	BytesPerScanline: 0
[    18.059] 	XResolution: 0
[    18.059] 	YResolution: 0
[    18.059] 	XCharSize: 0
[    18.059] 	YCharSize: 0
[    18.059] 	NumberOfPlanes: 0
[    18.059] 	BitsPerPixel: 0
[    18.059] 	NumberOfBanks: 0
[    18.059] 	MemoryModel: 0
[    18.059] 	BankSize: 0
[    18.059] 	NumberOfImages: 0
[    18.059] 	RedMaskSize: 0
[    18.059] 	RedFieldPosition: 0
[    18.059] 	GreenMaskSize: 0
[    18.059] 	GreenFieldPosition: 0
[    18.059] 	BlueMaskSize: 0
[    18.059] 	BlueFieldPosition: 0
[    18.059] 	RsvdMaskSize: 0
[    18.059] 	RsvdFieldPosition: 0
[    18.059] 	DirectColorModeInfo: 0
[    18.059] 	PhysBasePtr: 0x0
[    18.059] 	LinBytesPerScanLine: 0
[    18.059] 	BnkNumberOfImagePages: 0
[    18.059] 	LinNumberOfImagePages: 0
[    18.059] 	LinRedMaskSize: 0
[    18.059] 	LinRedFieldPosition: 0
[    18.059] 	LinGreenMaskSize: 0
[    18.059] 	LinGreenFieldPosition: 0
[    18.059] 	LinBlueMaskSize: 0
[    18.059] 	LinBlueFieldPosition: 0
[    18.059] 	LinRsvdMaskSize: 0
[    18.059] 	LinRsvdFieldPosition: 0
[    18.059] 	MaxPixelClock: 0
[    18.059] Mode: 15c (0x0)
[    18.059] 	ModeAttributes: 0x0
[    18.059] 	WinAAttributes: 0x0
[    18.059] 	WinBAttributes: 0x0
[    18.059] 	WinGranularity: 0
[    18.059] 	WinSize: 0
[    18.059] 	WinASegment: 0x0
[    18.059] 	WinBSegment: 0x0
[    18.059] 	WinFuncPtr: 0x0
[    18.059] 	BytesPerScanline: 0
[    18.059] 	XResolution: 0
[    18.059] 	YResolution: 0
[    18.059] 	XCharSize: 0
[    18.059] 	YCharSize: 0
[    18.059] 	NumberOfPlanes: 0
[    18.059] 	BitsPerPixel: 0
[    18.059] 	NumberOfBanks: 0
[    18.059] 	MemoryModel: 0
[    18.059] 	BankSize: 0
[    18.059] 	NumberOfImages: 0
[    18.059] 	RedMaskSize: 0
[    18.059] 	RedFieldPosition: 0
[    18.059] 	GreenMaskSize: 0
[    18.059] 	GreenFieldPosition: 0
[    18.059] 	BlueMaskSize: 0
[    18.059] 	BlueFieldPosition: 0
[    18.059] 	RsvdMaskSize: 0
[    18.059] 	RsvdFieldPosition: 0
[    18.059] 	DirectColorModeInfo: 0
[    18.059] 	PhysBasePtr: 0x0
[    18.059] 	LinBytesPerScanLine: 0
[    18.059] 	BnkNumberOfImagePages: 0
[    18.060] 	LinNumberOfImagePages: 0
[    18.060] 	LinRedMaskSize: 0
[    18.060] 	LinRedFieldPosition: 0
[    18.060] 	LinGreenMaskSize: 0
[    18.060] 	LinGreenFieldPosition: 0
[    18.060] 	LinBlueMaskSize: 0
[    18.060] 	LinBlueFieldPosition: 0
[    18.060] 	LinRsvdMaskSize: 0
[    18.060] 	LinRsvdFieldPosition: 0
[    18.060] 	MaxPixelClock: 0
[    18.060] Mode: 13a (0x0)
[    18.060] 	ModeAttributes: 0x0
[    18.060] 	WinAAttributes: 0x0
[    18.060] 	WinBAttributes: 0x0
[    18.060] 	WinGranularity: 0
[    18.060] 	WinSize: 0
[    18.060] 	WinASegment: 0x0
[    18.060] 	WinBSegment: 0x0
[    18.060] 	WinFuncPtr: 0x0
[    18.060] 	BytesPerScanline: 0
[    18.060] 	XResolution: 0
[    18.060] 	YResolution: 0
[    18.060] 	XCharSize: 0
[    18.060] 	YCharSize: 0
[    18.060] 	NumberOfPlanes: 0
[    18.060] 	BitsPerPixel: 0
[    18.060] 	NumberOfBanks: 0
[    18.060] 	MemoryModel: 0
[    18.060] 	BankSize: 0
[    18.060] 	NumberOfImages: 0
[    18.060] 	RedMaskSize: 0
[    18.060] 	RedFieldPosition: 0
[    18.060] 	GreenMaskSize: 0
[    18.060] 	GreenFieldPosition: 0
[    18.060] 	BlueMaskSize: 0
[    18.060] 	BlueFieldPosition: 0
[    18.060] 	RsvdMaskSize: 0
[    18.060] 	RsvdFieldPosition: 0
[    18.060] 	DirectColorModeInfo: 0
[    18.060] 	PhysBasePtr: 0x0
[    18.060] 	LinBytesPerScanLine: 0
[    18.060] 	BnkNumberOfImagePages: 0
[    18.060] 	LinNumberOfImagePages: 0
[    18.060] 	LinRedMaskSize: 0
[    18.060] 	LinRedFieldPosition: 0
[    18.060] 	LinGreenMaskSize: 0
[    18.060] 	LinGreenFieldPosition: 0
[    18.060] 	LinBlueMaskSize: 0
[    18.060] 	LinBlueFieldPosition: 0
[    18.060] 	LinRsvdMaskSize: 0
[    18.060] 	LinRsvdFieldPosition: 0
[    18.060] 	MaxPixelClock: 0
[    18.060] Mode: 14b (0x0)
[    18.060] 	ModeAttributes: 0x0
[    18.060] 	WinAAttributes: 0x0
[    18.060] 	WinBAttributes: 0x0
[    18.060] 	WinGranularity: 0
[    18.060] 	WinSize: 0
[    18.060] 	WinASegment: 0x0
[    18.060] 	WinBSegment: 0x0
[    18.060] 	WinFuncPtr: 0x0
[    18.060] 	BytesPerScanline: 0
[    18.060] 	XResolution: 0
[    18.060] 	YResolution: 0
[    18.060] 	XCharSize: 0
[    18.060] 	YCharSize: 0
[    18.060] 	NumberOfPlanes: 0
[    18.060] 	BitsPerPixel: 0
[    18.060] 	NumberOfBanks: 0
[    18.060] 	MemoryModel: 0
[    18.060] 	BankSize: 0
[    18.060] 	NumberOfImages: 0
[    18.060] 	RedMaskSize: 0
[    18.060] 	RedFieldPosition: 0
[    18.060] 	GreenMaskSize: 0
[    18.060] 	GreenFieldPosition: 0
[    18.060] 	BlueMaskSize: 0
[    18.060] 	BlueFieldPosition: 0
[    18.060] 	RsvdMaskSize: 0
[    18.060] 	RsvdFieldPosition: 0
[    18.060] 	DirectColorModeInfo: 0
[    18.060] 	PhysBasePtr: 0x0
[    18.060] 	LinBytesPerScanLine: 0
[    18.060] 	BnkNumberOfImagePages: 0
[    18.060] 	LinNumberOfImagePages: 0
[    18.060] 	LinRedMaskSize: 0
[    18.060] 	LinRedFieldPosition: 0
[    18.060] 	LinGreenMaskSize: 0
[    18.060] 	LinGreenFieldPosition: 0
[    18.060] 	LinBlueMaskSize: 0
[    18.060] 	LinBlueFieldPosition: 0
[    18.060] 	LinRsvdMaskSize: 0
[    18.060] 	LinRsvdFieldPosition: 0
[    18.060] 	MaxPixelClock: 0
[    18.060] Mode: 15a (0x0)
[    18.060] 	ModeAttributes: 0x0
[    18.060] 	WinAAttributes: 0x0
[    18.060] 	WinBAttributes: 0x0
[    18.060] 	WinGranularity: 0
[    18.060] 	WinSize: 0
[    18.060] 	WinASegment: 0x0
[    18.060] 	WinBSegment: 0x0
[    18.060] 	WinFuncPtr: 0x0
[    18.060] 	BytesPerScanline: 0
[    18.060] 	XResolution: 0
[    18.060] 	YResolution: 0
[    18.060] 	XCharSize: 0
[    18.060] 	YCharSize: 0
[    18.060] 	NumberOfPlanes: 0
[    18.060] 	BitsPerPixel: 0
[    18.060] 	NumberOfBanks: 0
[    18.060] 	MemoryModel: 0
[    18.060] 	BankSize: 0
[    18.060] 	NumberOfImages: 0
[    18.060] 	RedMaskSize: 0
[    18.060] 	RedFieldPosition: 0
[    18.060] 	GreenMaskSize: 0
[    18.060] 	GreenFieldPosition: 0
[    18.060] 	BlueMaskSize: 0
[    18.060] 	BlueFieldPosition: 0
[    18.060] 	RsvdMaskSize: 0
[    18.060] 	RsvdFieldPosition: 0
[    18.060] 	DirectColorModeInfo: 0
[    18.060] 	PhysBasePtr: 0x0
[    18.060] 	LinBytesPerScanLine: 0
[    18.060] 	BnkNumberOfImagePages: 0
[    18.060] 	LinNumberOfImagePages: 0
[    18.060] 	LinRedMaskSize: 0
[    18.060] 	LinRedFieldPosition: 0
[    18.060] 	LinGreenMaskSize: 0
[    18.060] 	LinGreenFieldPosition: 0
[    18.060] 	LinBlueMaskSize: 0
[    18.060] 	LinBlueFieldPosition: 0
[    18.060] 	LinRsvdMaskSize: 0
[    18.060] 	LinRsvdFieldPosition: 0
[    18.060] 	MaxPixelClock: 0
[    18.061] Mode: 107 (1280x1024)
[    18.061] 	ModeAttributes: 0x9b
[    18.061] 	WinAAttributes: 0x7
[    18.061] 	WinBAttributes: 0x0
[    18.061] 	WinGranularity: 64
[    18.061] 	WinSize: 64
[    18.061] 	WinASegment: 0xa000
[    18.061] 	WinBSegment: 0x0
[    18.061] 	WinFuncPtr: 0xc00079bc
[    18.061] 	BytesPerScanline: 1280
[    18.061] 	XResolution: 1280
[    18.061] 	YResolution: 1024
[    18.061] 	XCharSize: 8
[    18.061] 	YCharSize: 16
[    18.061] 	NumberOfPlanes: 1
[    18.061] 	BitsPerPixel: 8
[    18.061] 	NumberOfBanks: 1
[    18.061] 	MemoryModel: 4
[    18.061] 	BankSize: 0
[    18.061] 	NumberOfImages: 50
[    18.061] 	RedMaskSize: 0
[    18.061] 	RedFieldPosition: 0
[    18.061] 	GreenMaskSize: 0
[    18.061] 	GreenFieldPosition: 0
[    18.061] 	BlueMaskSize: 0
[    18.061] 	BlueFieldPosition: 0
[    18.061] 	RsvdMaskSize: 0
[    18.061] 	RsvdFieldPosition: 0
[    18.061] 	DirectColorModeInfo: 0
[    18.061] 	PhysBasePtr: 0xc0000000
[    18.061] 	LinBytesPerScanLine: 1280
[    18.061] 	BnkNumberOfImagePages: 50
[    18.061] 	LinNumberOfImagePages: 50
[    18.061] 	LinRedMaskSize: 0
[    18.061] 	LinRedFieldPosition: 0
[    18.061] 	LinGreenMaskSize: 0
[    18.061] 	LinGreenFieldPosition: 0
[    18.061] 	LinBlueMaskSize: 0
[    18.061] 	LinBlueFieldPosition: 0
[    18.061] 	LinRsvdMaskSize: 0
[    18.061] 	LinRsvdFieldPosition: 0
[    18.061] 	MaxPixelClock: 230000000
[    18.061] Mode: 11a (1280x1024)
[    18.061] 	ModeAttributes: 0x9b
[    18.061] 	WinAAttributes: 0x7
[    18.061] 	WinBAttributes: 0x0
[    18.061] 	WinGranularity: 64
[    18.061] 	WinSize: 64
[    18.061] 	WinASegment: 0xa000
[    18.061] 	WinBSegment: 0x0
[    18.061] 	WinFuncPtr: 0xc00079bc
[    18.061] 	BytesPerScanline: 2560
[    18.061] 	XResolution: 1280
[    18.061] 	YResolution: 1024
[    18.061] 	XCharSize: 8
[    18.061] 	YCharSize: 16
[    18.061] 	NumberOfPlanes: 1
[    18.061] 	BitsPerPixel: 16
[    18.061] 	NumberOfBanks: 1
[    18.061] 	MemoryModel: 6
[    18.061] 	BankSize: 0
[    18.061] 	NumberOfImages: 24
[    18.061] 	RedMaskSize: 5
[    18.061] 	RedFieldPosition: 11
[    18.061] 	GreenMaskSize: 6
[    18.061] 	GreenFieldPosition: 5
[    18.061] 	BlueMaskSize: 5
[    18.061] 	BlueFieldPosition: 0
[    18.061] 	RsvdMaskSize: 0
[    18.061] 	RsvdFieldPosition: 0
[    18.061] 	DirectColorModeInfo: 0
[    18.061] 	PhysBasePtr: 0xc0000000
[    18.061] 	LinBytesPerScanLine: 2560
[    18.061] 	BnkNumberOfImagePages: 24
[    18.061] 	LinNumberOfImagePages: 24
[    18.061] 	LinRedMaskSize: 5
[    18.061] 	LinRedFieldPosition: 11
[    18.061] 	LinGreenMaskSize: 6
[    18.061] 	LinGreenFieldPosition: 5
[    18.061] 	LinBlueMaskSize: 5
[    18.061] 	LinBlueFieldPosition: 0
[    18.061] 	LinRsvdMaskSize: 0
[    18.061] 	LinRsvdFieldPosition: 0
[    18.061] 	MaxPixelClock: 230000000
[    18.062] *Mode: 11b (1280x1024)
[    18.062] 	ModeAttributes: 0x9b
[    18.062] 	WinAAttributes: 0x7
[    18.062] 	WinBAttributes: 0x0
[    18.062] 	WinGranularity: 64
[    18.062] 	WinSize: 64
[    18.062] 	WinASegment: 0xa000
[    18.062] 	WinBSegment: 0x0
[    18.062] 	WinFuncPtr: 0xc00079bc
[    18.062] 	BytesPerScanline: 5120
[    18.062] 	XResolution: 1280
[    18.062] 	YResolution: 1024
[    18.062] 	XCharSize: 8
[    18.062] 	YCharSize: 16
[    18.062] 	NumberOfPlanes: 1
[    18.062] 	BitsPerPixel: 32
[    18.062] 	NumberOfBanks: 1
[    18.062] 	MemoryModel: 6
[    18.062] 	BankSize: 0
[    18.062] 	NumberOfImages: 11
[    18.062] 	RedMaskSize: 8
[    18.062] 	RedFieldPosition: 16
[    18.062] 	GreenMaskSize: 8
[    18.062] 	GreenFieldPosition: 8
[    18.062] 	BlueMaskSize: 8
[    18.062] 	BlueFieldPosition: 0
[    18.062] 	RsvdMaskSize: 8
[    18.062] 	RsvdFieldPosition: 24
[    18.062] 	DirectColorModeInfo: 0
[    18.062] 	PhysBasePtr: 0xc0000000
[    18.062] 	LinBytesPerScanLine: 5120
[    18.062] 	BnkNumberOfImagePages: 11
[    18.062] 	LinNumberOfImagePages: 11
[    18.062] 	LinRedMaskSize: 8
[    18.062] 	LinRedFieldPosition: 16
[    18.062] 	LinGreenMaskSize: 8
[    18.062] 	LinGreenFieldPosition: 8
[    18.062] 	LinBlueMaskSize: 8
[    18.062] 	LinBlueFieldPosition: 0
[    18.062] 	LinRsvdMaskSize: 8
[    18.062] 	LinRsvdFieldPosition: 24
[    18.062] 	MaxPixelClock: 230000000
[    18.062] Mode: 105 (1024x768)
[    18.062] 	ModeAttributes: 0x9b
[    18.062] 	WinAAttributes: 0x7
[    18.062] 	WinBAttributes: 0x0
[    18.062] 	WinGranularity: 64
[    18.062] 	WinSize: 64
[    18.062] 	WinASegment: 0xa000
[    18.062] 	WinBSegment: 0x0
[    18.062] 	WinFuncPtr: 0xc00079bc
[    18.062] 	BytesPerScanline: 1024
[    18.062] 	XResolution: 1024
[    18.062] 	YResolution: 768
[    18.062] 	XCharSize: 8
[    18.062] 	YCharSize: 16
[    18.062] 	NumberOfPlanes: 1
[    18.062] 	BitsPerPixel: 8
[    18.062] 	NumberOfBanks: 1
[    18.062] 	MemoryModel: 4
[    18.062] 	BankSize: 0
[    18.062] 	NumberOfImages: 84
[    18.062] 	RedMaskSize: 0
[    18.062] 	RedFieldPosition: 0
[    18.062] 	GreenMaskSize: 0
[    18.062] 	GreenFieldPosition: 0
[    18.062] 	BlueMaskSize: 0
[    18.062] 	BlueFieldPosition: 0
[    18.062] 	RsvdMaskSize: 0
[    18.062] 	RsvdFieldPosition: 0
[    18.062] 	DirectColorModeInfo: 0
[    18.062] 	PhysBasePtr: 0xc0000000
[    18.062] 	LinBytesPerScanLine: 1024
[    18.062] 	BnkNumberOfImagePages: 84
[    18.062] 	LinNumberOfImagePages: 84
[    18.062] 	LinRedMaskSize: 0
[    18.062] 	LinRedFieldPosition: 0
[    18.062] 	LinGreenMaskSize: 0
[    18.062] 	LinGreenFieldPosition: 0
[    18.062] 	LinBlueMaskSize: 0
[    18.062] 	LinBlueFieldPosition: 0
[    18.062] 	LinRsvdMaskSize: 0
[    18.062] 	LinRsvdFieldPosition: 0
[    18.062] 	MaxPixelClock: 230000000
[    18.062] Mode: 117 (1024x768)
[    18.062] 	ModeAttributes: 0x9b
[    18.062] 	WinAAttributes: 0x7
[    18.062] 	WinBAttributes: 0x0
[    18.062] 	WinGranularity: 64
[    18.062] 	WinSize: 64
[    18.062] 	WinASegment: 0xa000
[    18.062] 	WinBSegment: 0x0
[    18.062] 	WinFuncPtr: 0xc00079bc
[    18.062] 	BytesPerScanline: 2048
[    18.062] 	XResolution: 1024
[    18.062] 	YResolution: 768
[    18.062] 	XCharSize: 8
[    18.062] 	YCharSize: 16
[    18.062] 	NumberOfPlanes: 1
[    18.062] 	BitsPerPixel: 16
[    18.062] 	NumberOfBanks: 1
[    18.062] 	MemoryModel: 6
[    18.062] 	BankSize: 0
[    18.062] 	NumberOfImages: 41
[    18.062] 	RedMaskSize: 5
[    18.062] 	RedFieldPosition: 11
[    18.062] 	GreenMaskSize: 6
[    18.062] 	GreenFieldPosition: 5
[    18.062] 	BlueMaskSize: 5
[    18.062] 	BlueFieldPosition: 0
[    18.062] 	RsvdMaskSize: 0
[    18.062] 	RsvdFieldPosition: 0
[    18.062] 	DirectColorModeInfo: 0
[    18.062] 	PhysBasePtr: 0xc0000000
[    18.062] 	LinBytesPerScanLine: 2048
[    18.062] 	BnkNumberOfImagePages: 41
[    18.062] 	LinNumberOfImagePages: 41
[    18.062] 	LinRedMaskSize: 5
[    18.062] 	LinRedFieldPosition: 11
[    18.062] 	LinGreenMaskSize: 6
[    18.062] 	LinGreenFieldPosition: 5
[    18.062] 	LinBlueMaskSize: 5
[    18.062] 	LinBlueFieldPosition: 0
[    18.062] 	LinRsvdMaskSize: 0
[    18.062] 	LinRsvdFieldPosition: 0
[    18.062] 	MaxPixelClock: 230000000
[    18.063] *Mode: 118 (1024x768)
[    18.063] 	ModeAttributes: 0x9b
[    18.063] 	WinAAttributes: 0x7
[    18.063] 	WinBAttributes: 0x0
[    18.063] 	WinGranularity: 64
[    18.063] 	WinSize: 64
[    18.063] 	WinASegment: 0xa000
[    18.063] 	WinBSegment: 0x0
[    18.063] 	WinFuncPtr: 0xc00079bc
[    18.063] 	BytesPerScanline: 4096
[    18.063] 	XResolution: 1024
[    18.063] 	YResolution: 768
[    18.063] 	XCharSize: 8
[    18.063] 	YCharSize: 16
[    18.063] 	NumberOfPlanes: 1
[    18.063] 	BitsPerPixel: 32
[    18.063] 	NumberOfBanks: 1
[    18.063] 	MemoryModel: 6
[    18.063] 	BankSize: 0
[    18.063] 	NumberOfImages: 20
[    18.063] 	RedMaskSize: 8
[    18.063] 	RedFieldPosition: 16
[    18.063] 	GreenMaskSize: 8
[    18.063] 	GreenFieldPosition: 8
[    18.063] 	BlueMaskSize: 8
[    18.063] 	BlueFieldPosition: 0
[    18.063] 	RsvdMaskSize: 8
[    18.063] 	RsvdFieldPosition: 24
[    18.063] 	DirectColorModeInfo: 0
[    18.063] 	PhysBasePtr: 0xc0000000
[    18.063] 	LinBytesPerScanLine: 4096
[    18.063] 	BnkNumberOfImagePages: 20
[    18.063] 	LinNumberOfImagePages: 20
[    18.063] 	LinRedMaskSize: 8
[    18.063] 	LinRedFieldPosition: 16
[    18.063] 	LinGreenMaskSize: 8
[    18.063] 	LinGreenFieldPosition: 8
[    18.063] 	LinBlueMaskSize: 8
[    18.063] 	LinBlueFieldPosition: 0
[    18.063] 	LinRsvdMaskSize: 8
[    18.063] 	LinRsvdFieldPosition: 24
[    18.063] 	MaxPixelClock: 230000000
[    18.063] *Mode: 112 (640x480)
[    18.063] 	ModeAttributes: 0x9b
[    18.063] 	WinAAttributes: 0x7
[    18.063] 	WinBAttributes: 0x0
[    18.063] 	WinGranularity: 64
[    18.063] 	WinSize: 64
[    18.063] 	WinASegment: 0xa000
[    18.063] 	WinBSegment: 0x0
[    18.063] 	WinFuncPtr: 0xc00079bc
[    18.063] 	BytesPerScanline: 2560
[    18.063] 	XResolution: 640
[    18.063] 	YResolution: 480
[    18.063] 	XCharSize: 8
[    18.063] 	YCharSize: 16
[    18.063] 	NumberOfPlanes: 1
[    18.063] 	BitsPerPixel: 32
[    18.063] 	NumberOfBanks: 1
[    18.063] 	MemoryModel: 6
[    18.063] 	BankSize: 0
[    18.063] 	NumberOfImages: 52
[    18.063] 	RedMaskSize: 8
[    18.063] 	RedFieldPosition: 16
[    18.063] 	GreenMaskSize: 8
[    18.063] 	GreenFieldPosition: 8
[    18.063] 	BlueMaskSize: 8
[    18.063] 	BlueFieldPosition: 0
[    18.063] 	RsvdMaskSize: 8
[    18.063] 	RsvdFieldPosition: 24
[    18.063] 	DirectColorModeInfo: 0
[    18.063] 	PhysBasePtr: 0xc0000000
[    18.063] 	LinBytesPerScanLine: 2560
[    18.063] 	BnkNumberOfImagePages: 52
[    18.063] 	LinNumberOfImagePages: 52
[    18.063] 	LinRedMaskSize: 8
[    18.063] 	LinRedFieldPosition: 16
[    18.063] 	LinGreenMaskSize: 8
[    18.063] 	LinGreenFieldPosition: 8
[    18.063] 	LinBlueMaskSize: 8
[    18.063] 	LinBlueFieldPosition: 0
[    18.063] 	LinRsvdMaskSize: 8
[    18.063] 	LinRsvdFieldPosition: 24
[    18.063] 	MaxPixelClock: 230000000
[    18.064] Mode: 114 (800x600)
[    18.064] 	ModeAttributes: 0x9b
[    18.064] 	WinAAttributes: 0x7
[    18.064] 	WinBAttributes: 0x0
[    18.064] 	WinGranularity: 64
[    18.064] 	WinSize: 64
[    18.064] 	WinASegment: 0xa000
[    18.064] 	WinBSegment: 0x0
[    18.064] 	WinFuncPtr: 0xc00079bc
[    18.064] 	BytesPerScanline: 1600
[    18.064] 	XResolution: 800
[    18.064] 	YResolution: 600
[    18.064] 	XCharSize: 8
[    18.064] 	YCharSize: 16
[    18.064] 	NumberOfPlanes: 1
[    18.064] 	BitsPerPixel: 16
[    18.064] 	NumberOfBanks: 1
[    18.064] 	MemoryModel: 6
[    18.064] 	BankSize: 0
[    18.064] 	NumberOfImages: 67
[    18.064] 	RedMaskSize: 5
[    18.064] 	RedFieldPosition: 11
[    18.064] 	GreenMaskSize: 6
[    18.064] 	GreenFieldPosition: 5
[    18.064] 	BlueMaskSize: 5
[    18.064] 	BlueFieldPosition: 0
[    18.064] 	RsvdMaskSize: 0
[    18.064] 	RsvdFieldPosition: 0
[    18.064] 	DirectColorModeInfo: 0
[    18.064] 	PhysBasePtr: 0xc0000000
[    18.064] 	LinBytesPerScanLine: 1600
[    18.064] 	BnkNumberOfImagePages: 67
[    18.064] 	LinNumberOfImagePages: 67
[    18.064] 	LinRedMaskSize: 5
[    18.064] 	LinRedFieldPosition: 11
[    18.064] 	LinGreenMaskSize: 6
[    18.064] 	LinGreenFieldPosition: 5
[    18.064] 	LinBlueMaskSize: 5
[    18.064] 	LinBlueFieldPosition: 0
[    18.064] 	LinRsvdMaskSize: 0
[    18.064] 	LinRsvdFieldPosition: 0
[    18.064] 	MaxPixelClock: 230000000
[    18.064] *Mode: 115 (800x600)
[    18.064] 	ModeAttributes: 0x9b
[    18.064] 	WinAAttributes: 0x7
[    18.064] 	WinBAttributes: 0x0
[    18.064] 	WinGranularity: 64
[    18.064] 	WinSize: 64
[    18.064] 	WinASegment: 0xa000
[    18.064] 	WinBSegment: 0x0
[    18.064] 	WinFuncPtr: 0xc00079bc
[    18.064] 	BytesPerScanline: 3200
[    18.064] 	XResolution: 800
[    18.064] 	YResolution: 600
[    18.064] 	XCharSize: 8
[    18.064] 	YCharSize: 16
[    18.064] 	NumberOfPlanes: 1
[    18.064] 	BitsPerPixel: 32
[    18.064] 	NumberOfBanks: 1
[    18.064] 	MemoryModel: 6
[    18.064] 	BankSize: 0
[    18.064] 	NumberOfImages: 33
[    18.064] 	RedMaskSize: 8
[    18.064] 	RedFieldPosition: 16
[    18.064] 	GreenMaskSize: 8
[    18.064] 	GreenFieldPosition: 8
[    18.064] 	BlueMaskSize: 8
[    18.064] 	BlueFieldPosition: 0
[    18.064] 	RsvdMaskSize: 8
[    18.064] 	RsvdFieldPosition: 24
[    18.064] 	DirectColorModeInfo: 0
[    18.064] 	PhysBasePtr: 0xc0000000
[    18.064] 	LinBytesPerScanLine: 3200
[    18.064] 	BnkNumberOfImagePages: 33
[    18.064] 	LinNumberOfImagePages: 33
[    18.064] 	LinRedMaskSize: 8
[    18.064] 	LinRedFieldPosition: 16
[    18.064] 	LinGreenMaskSize: 8
[    18.064] 	LinGreenFieldPosition: 8
[    18.064] 	LinBlueMaskSize: 8
[    18.064] 	LinBlueFieldPosition: 0
[    18.064] 	LinRsvdMaskSize: 8
[    18.064] 	LinRsvdFieldPosition: 24
[    18.064] 	MaxPixelClock: 230000000
[    18.064] Mode: 101 (640x480)
[    18.064] 	ModeAttributes: 0x9b
[    18.064] 	WinAAttributes: 0x7
[    18.064] 	WinBAttributes: 0x0
[    18.064] 	WinGranularity: 64
[    18.064] 	WinSize: 64
[    18.064] 	WinASegment: 0xa000
[    18.064] 	WinBSegment: 0x0
[    18.064] 	WinFuncPtr: 0xc00079bc
[    18.064] 	BytesPerScanline: 640
[    18.064] 	XResolution: 640
[    18.064] 	YResolution: 480
[    18.064] 	XCharSize: 8
[    18.064] 	YCharSize: 16
[    18.064] 	NumberOfPlanes: 1
[    18.064] 	BitsPerPixel: 8
[    18.064] 	NumberOfBanks: 1
[    18.064] 	MemoryModel: 4
[    18.064] 	BankSize: 0
[    18.064] 	NumberOfImages: 203
[    18.064] 	RedMaskSize: 0
[    18.064] 	RedFieldPosition: 0
[    18.064] 	GreenMaskSize: 0
[    18.064] 	GreenFieldPosition: 0
[    18.064] 	BlueMaskSize: 0
[    18.064] 	BlueFieldPosition: 0
[    18.064] 	RsvdMaskSize: 0
[    18.064] 	RsvdFieldPosition: 0
[    18.064] 	DirectColorModeInfo: 0
[    18.064] 	PhysBasePtr: 0xc0000000
[    18.064] 	LinBytesPerScanLine: 640
[    18.065] 	BnkNumberOfImagePages: 203
[    18.065] 	LinNumberOfImagePages: 203
[    18.065] 	LinRedMaskSize: 0
[    18.065] 	LinRedFieldPosition: 0
[    18.065] 	LinGreenMaskSize: 0
[    18.065] 	LinGreenFieldPosition: 0
[    18.065] 	LinBlueMaskSize: 0
[    18.065] 	LinBlueFieldPosition: 0
[    18.065] 	LinRsvdMaskSize: 0
[    18.065] 	LinRsvdFieldPosition: 0
[    18.065] 	MaxPixelClock: 230000000
[    18.065] Mode: 103 (800x600)
[    18.065] 	ModeAttributes: 0x9b
[    18.065] 	WinAAttributes: 0x7
[    18.065] 	WinBAttributes: 0x0
[    18.065] 	WinGranularity: 64
[    18.065] 	WinSize: 64
[    18.065] 	WinASegment: 0xa000
[    18.065] 	WinBSegment: 0x0
[    18.065] 	WinFuncPtr: 0xc00079bc
[    18.065] 	BytesPerScanline: 832
[    18.065] 	XResolution: 800
[    18.065] 	YResolution: 600
[    18.065] 	XCharSize: 8
[    18.065] 	YCharSize: 16
[    18.065] 	NumberOfPlanes: 1
[    18.065] 	BitsPerPixel: 8
[    18.065] 	NumberOfBanks: 1
[    18.065] 	MemoryModel: 4
[    18.065] 	BankSize: 0
[    18.065] 	NumberOfImages: 126
[    18.065] 	RedMaskSize: 0
[    18.065] 	RedFieldPosition: 0
[    18.065] 	GreenMaskSize: 0
[    18.065] 	GreenFieldPosition: 0
[    18.065] 	BlueMaskSize: 0
[    18.065] 	BlueFieldPosition: 0
[    18.065] 	RsvdMaskSize: 0
[    18.065] 	RsvdFieldPosition: 0
[    18.065] 	DirectColorModeInfo: 0
[    18.065] 	PhysBasePtr: 0xc0000000
[    18.065] 	LinBytesPerScanLine: 832
[    18.065] 	BnkNumberOfImagePages: 126
[    18.065] 	LinNumberOfImagePages: 126
[    18.065] 	LinRedMaskSize: 0
[    18.065] 	LinRedFieldPosition: 0
[    18.065] 	LinGreenMaskSize: 0
[    18.065] 	LinGreenFieldPosition: 0
[    18.065] 	LinBlueMaskSize: 0
[    18.065] 	LinBlueFieldPosition: 0
[    18.065] 	LinRsvdMaskSize: 0
[    18.065] 	LinRsvdFieldPosition: 0
[    18.065] 	MaxPixelClock: 230000000
[    18.065] Mode: 111 (640x480)
[    18.065] 	ModeAttributes: 0x9b
[    18.065] 	WinAAttributes: 0x7
[    18.065] 	WinBAttributes: 0x0
[    18.065] 	WinGranularity: 64
[    18.065] 	WinSize: 64
[    18.065] 	WinASegment: 0xa000
[    18.065] 	WinBSegment: 0x0
[    18.065] 	WinFuncPtr: 0xc00079bc
[    18.065] 	BytesPerScanline: 1280
[    18.065] 	XResolution: 640
[    18.065] 	YResolution: 480
[    18.065] 	XCharSize: 8
[    18.065] 	YCharSize: 16
[    18.065] 	NumberOfPlanes: 1
[    18.065] 	BitsPerPixel: 16
[    18.065] 	NumberOfBanks: 1
[    18.065] 	MemoryModel: 6
[    18.065] 	BankSize: 0
[    18.065] 	NumberOfImages: 101
[    18.065] 	RedMaskSize: 5
[    18.065] 	RedFieldPosition: 11
[    18.065] 	GreenMaskSize: 6
[    18.065] 	GreenFieldPosition: 5
[    18.065] 	BlueMaskSize: 5
[    18.065] 	BlueFieldPosition: 0
[    18.065] 	RsvdMaskSize: 0
[    18.065] 	RsvdFieldPosition: 0
[    18.065] 	DirectColorModeInfo: 0
[    18.065] 	PhysBasePtr: 0xc0000000
[    18.065] 	LinBytesPerScanLine: 1280
[    18.065] 	BnkNumberOfImagePages: 101
[    18.065] 	LinNumberOfImagePages: 101
[    18.065] 	LinRedMaskSize: 5
[    18.065] 	LinRedFieldPosition: 11
[    18.065] 	LinGreenMaskSize: 6
[    18.065] 	LinGreenFieldPosition: 5
[    18.065] 	LinBlueMaskSize: 5
[    18.065] 	LinBlueFieldPosition: 0
[    18.065] 	LinRsvdMaskSize: 0
[    18.065] 	LinRsvdFieldPosition: 0
[    18.065] 	MaxPixelClock: 230000000
[    18.065] 
[    18.065] (II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
[    18.065] (II) VESA(0): <default monitor>: Using hsync range of 30.00-83.00 kHz
[    18.065] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-76.00 Hz
[    18.065] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[    18.065] (WW) VESA(0): Unable to estimate virtual size
[    18.065] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    18.065] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    18.065] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    18.065] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    18.065] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    18.065] (II) VESA(0): <default monitor>: Using hsync range of 30.00-83.00 kHz
[    18.065] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-76.00 Hz
[    18.065] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[    18.065] (WW) VESA(0): Unable to estimate virtual size
[    18.065] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    18.065] (**) VESA(0): *Built-in mode "1280x1024"
[    18.065] (**) VESA(0): *Built-in mode "1024x768"
[    18.065] (**) VESA(0): *Built-in mode "800x600"
[    18.065] (**) VESA(0): *Built-in mode "640x480"
[    18.065] (**) VESA(0): Display dimensions: (520, 320) mm
[    18.065] (**) VESA(0): DPI set to (62, 81)
[    18.065] (II) VESA(0): Attempting to use 75Hz refresh for mode "1280x1024" (11b)
[    18.066] (II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
[    18.066] (II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
[    18.066] (II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
[    18.067] (**) VESA(0): Using "Shadow Framebuffer"
[    18.067] (II) Loading sub module "shadow"
[    18.067] (II) LoadModule: "shadow"
[    18.067] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    18.096] (II) Module shadow: vendor="X.Org Foundation"
[    18.096] 	compiled for 1.10.4, module version = 1.1.0
[    18.096] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.096] (II) Loading sub module "fb"
[    18.096] (II) LoadModule: "fb"
[    18.096] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.096] (II) Module fb: vendor="X.Org Foundation"
[    18.096] 	compiled for 1.10.4, module version = 1.0.0
[    18.096] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.096] (II) UnloadModule: "fbdev"
[    18.096] (II) Unloading fbdev
[    18.096] (II) UnloadModule: "fbdevhw"
[    18.096] (II) Unloading fbdevhw
[    18.096] (==) Depth 24 pixmap format is 32 bpp
[    18.096] (II) Loading sub module "int10"
[    18.096] (II) LoadModule: "int10"
[    18.096] (II) Loading /usr/lib/xorg/modules/libint10.so
[    18.096] (II) Module int10: vendor="X.Org Foundation"
[    18.096] 	compiled for 1.10.4, module version = 1.0.0
[    18.096] 	ABI class: X.Org Video Driver, version 10.0
[    18.096] (II) VESA(0): initializing int10
[    18.096] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    18.097] (II) VESA(0): VESA BIOS detected
[    18.097] (II) VESA(0): VESA VBE Version 3.0
[    18.097] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[    18.097] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Desktop Graphics Chipset Accelerated VGA BIOS
[    18.097] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    18.097] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    18.097] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Desktop Graphics Controller
[    18.097] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    18.110] (II) VESA(0): virtual address = 0x7f894f628000,
	physical address = 0xc0000000, size = 67043328
[    18.114] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[    19.118] (==) VESA(0): Default visual is TrueColor
[    19.118] (==) VESA(0): Backing store disabled
[    19.119] (==) VESA(0): DPMS enabled
[    19.119] (WW) VESA(0): Option "NoLogo" is not used
[    19.119] (==) RandR enabled
[    19.119] (II) Found 2 VGA devices: arbiter wrapping enabled
[    19.119] (II) Initializing built-in extension Generic Event Extension
[    19.119] (II) Initializing built-in extension SHAPE
[    19.119] (II) Initializing built-in extension MIT-SHM
[    19.119] (II) Initializing built-in extension XInputExtension
[    19.119] (II) Initializing built-in extension XTEST
[    19.119] (II) Initializing built-in extension BIG-REQUESTS
[    19.119] (II) Initializing built-in extension SYNC
[    19.119] (II) Initializing built-in extension XKEYBOARD
[    19.119] (II) Initializing built-in extension XC-MISC
[    19.119] (II) Initializing built-in extension SECURITY
[    19.119] (II) Initializing built-in extension XINERAMA
[    19.119] (II) Initializing built-in extension XFIXES
[    19.119] (II) Initializing built-in extension RENDER
[    19.119] (II) Initializing built-in extension RANDR
[    19.119] (II) Initializing built-in extension COMPOSITE
[    19.119] (II) Initializing built-in extension DAMAGE
[    19.119] (II) Initializing built-in extension GESTURE
[    19.122] (II) AIGLX: Screen 0 is not DRI2 capable
[    19.122] (II) AIGLX: Screen 0 is not DRI capable
[    19.122] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
[    19.146] (II) AIGLX: Loaded and initialized swrast
[    19.146] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    19.152] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.157] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.157] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.157] (II) LoadModule: "evdev"
[    19.157] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.157] (II) Module evdev: vendor="X.Org Foundation"
[    19.157] 	compiled for 1.10.2, module version = 2.6.0
[    19.157] 	Module class: X.Org XInput Driver
[    19.157] 	ABI class: X.Org XInput driver, version 12.3
[    19.157] (II) Using input driver 'evdev' for 'Power Button'
[    19.157] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.158] (**) Power Button: always reports core events
[    19.158] (**) Power Button: Device: "/dev/input/event1"
[    19.158] (--) Power Button: Found keys
[    19.158] (II) Power Button: Configuring as keyboard
[    19.158] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.158] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.158] (**) Option "xkb_rules" "evdev"
[    19.158] (**) Option "xkb_model" "pc105"
[    19.158] (**) Option "xkb_layout" "gb"
[    19.159] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    19.159] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    19.159] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.159] (II) Using input driver 'evdev' for 'Video Bus'
[    19.159] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.159] (**) Video Bus: always reports core events
[    19.159] (**) Video Bus: Device: "/dev/input/event9"
[    19.159] (--) Video Bus: Found keys
[    19.159] (II) Video Bus: Configuring as keyboard
[    19.159] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event9"
[    19.159] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    19.159] (**) Option "xkb_rules" "evdev"
[    19.159] (**) Option "xkb_model" "pc105"
[    19.159] (**) Option "xkb_layout" "gb"
[    19.160] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    19.160] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.160] (II) Using input driver 'evdev' for 'Video Bus'
[    19.160] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.160] (**) Video Bus: always reports core events
[    19.160] (**) Video Bus: Device: "/dev/input/event8"
[    19.161] (--) Video Bus: Found keys
[    19.161] (II) Video Bus: Configuring as keyboard
[    19.161] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input8/event8"
[    19.161] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    19.161] (**) Option "xkb_rules" "evdev"
[    19.161] (**) Option "xkb_model" "pc105"
[    19.161] (**) Option "xkb_layout" "gb"
[    19.161] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.161] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.161] (II) Using input driver 'evdev' for 'Power Button'
[    19.161] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.161] (**) Power Button: always reports core events
[    19.161] (**) Power Button: Device: "/dev/input/event0"
[    19.161] (--) Power Button: Found keys
[    19.161] (II) Power Button: Configuring as keyboard
[    19.161] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    19.161] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.161] (**) Option "xkb_rules" "evdev"
[    19.161] (**) Option "xkb_model" "pc105"
[    19.161] (**) Option "xkb_layout" "gb"
[    19.163] (II) config/udev: Adding input device Quanta OpticalTouchScreen (/dev/input/event3)
[    19.163] (**) Quanta OpticalTouchScreen: Applying InputClass "evdev tablet catchall"
[    19.163] (II) Using input driver 'evdev' for 'Quanta OpticalTouchScreen'
[    19.163] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.163] (**) Quanta OpticalTouchScreen: always reports core events
[    19.163] (**) Quanta OpticalTouchScreen: Device: "/dev/input/event3"
[    19.163] (--) Quanta OpticalTouchScreen: Found 3 mouse buttons
[    19.163] (--) Quanta OpticalTouchScreen: Found absolute axes
[    19.163] (II) evdev-grail: failed to open grail, no gesture support
[    19.163] (--) Quanta OpticalTouchScreen: Found x and y absolute axes
[    19.163] (--) Quanta OpticalTouchScreen: Found absolute tablet.
[    19.163] (II) Quanta OpticalTouchScreen: Configuring as tablet
[    19.163] (**) Quanta OpticalTouchScreen: YAxisMapping: buttons 4 and 5
[    19.163] (**) Quanta OpticalTouchScreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.163] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input3/event3"
[    19.163] (II) XINPUT: Adding extended input device "Quanta OpticalTouchScreen" (type: TABLET)
[    19.163] (II) Quanta OpticalTouchScreen: initialized for absolute axes.
[    19.163] (**) Quanta OpticalTouchScreen: (accel) keeping acceleration scheme 1
[    19.163] (**) Quanta OpticalTouchScreen: (accel) acceleration profile 0
[    19.163] (**) Quanta OpticalTouchScreen: (accel) acceleration factor: 2.000
[    19.163] (**) Quanta OpticalTouchScreen: (accel) acceleration threshold: 4
[    19.163] (II) config/udev: Adding input device Quanta OpticalTouchScreen (/dev/input/mouse0)
[    19.163] (II) No input driver/identifier specified (ignoring)
[    19.164] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event7)
[    19.164] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    19.164] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    19.164] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.164] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    19.164] (**) Laptop_Integrated_Webcam_HD: Device: "/dev/input/event7"
[    19.164] (--) Laptop_Integrated_Webcam_HD: Found keys
[    19.164] (II) Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    19.164] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7/event7"
[    19.164] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD)
[    19.164] (**) Option "xkb_rules" "evdev"
[    19.164] (**) Option "xkb_model" "pc105"
[    19.164] (**) Option "xkb_layout" "gb"
[    19.165] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[    19.165] (II) No input driver/identifier specified (ignoring)
[    19.165] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[    19.165] (II) No input driver/identifier specified (ignoring)
[    19.166] (II) config/udev: Adding input device Dell Dell KM632 Wireless Keyboard and Mouse (/dev/input/event4)
[    19.166] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Applying InputClass "evdev keyboard catchall"
[    19.166] (II) Using input driver 'evdev' for 'Dell Dell KM632 Wireless Keyboard and Mouse'
[    19.166] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.166] (**) Dell Dell KM632 Wireless Keyboard and Mouse: always reports core events
[    19.166] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Device: "/dev/input/event4"
[    19.166] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found keys
[    19.166] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Configuring as keyboard
[    19.166] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input4/event4"
[    19.166] (II) XINPUT: Adding extended input device "Dell Dell KM632 Wireless Keyboard and Mouse" (type: KEYBOARD)
[    19.166] (**) Option "xkb_rules" "evdev"
[    19.166] (**) Option "xkb_model" "pc105"
[    19.166] (**) Option "xkb_layout" "gb"
[    19.166] (II) config/udev: Adding input device Dell Dell KM632 Wireless Keyboard and Mouse (/dev/input/event5)
[    19.166] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Applying InputClass "evdev keyboard catchall"
[    19.166] (II) Using input driver 'evdev' for 'Dell Dell KM632 Wireless Keyboard and Mouse'
[    19.166] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.166] (**) Dell Dell KM632 Wireless Keyboard and Mouse: always reports core events
[    19.166] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Device: "/dev/input/event5"
[    19.166] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found 1 mouse buttons
[    19.166] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found scroll wheel(s)
[    19.166] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found relative axes
[    19.166] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found absolute axes
[    19.166] (II) evdev-grail: failed to open grail, no gesture support
[    19.166] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found keys
[    19.166] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Configuring as mouse
[    19.166] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Configuring as keyboard
[    19.166] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Adding scrollwheel support
[    19.166] (**) Dell Dell KM632 Wireless Keyboard and Mouse: YAxisMapping: buttons 4 and 5
[    19.166] (**) Dell Dell KM632 Wireless Keyboard and Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.166] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input5/event5"
[    19.166] (II) XINPUT: Adding extended input device "Dell Dell KM632 Wireless Keyboard and Mouse" (type: KEYBOARD)
[    19.166] (**) Option "xkb_rules" "evdev"
[    19.166] (**) Option "xkb_model" "pc105"
[    19.166] (**) Option "xkb_layout" "gb"
[    19.166] (EE) Dell Dell KM632 Wireless Keyboard and Mouse: failed to initialize for relative axes.
[    19.166] (II) Dell Dell KM632 Wireless Keyboard and Mouse: initialized for absolute axes.
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) keeping acceleration scheme 1
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration profile 0
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration factor: 2.000
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration threshold: 4
[    19.167] (II) config/udev: Adding input device Dell Dell KM632 Wireless Keyboard and Mouse (/dev/input/event6)
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Applying InputClass "evdev pointer catchall"
[    19.167] (II) Using input driver 'evdev' for 'Dell Dell KM632 Wireless Keyboard and Mouse'
[    19.167] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: always reports core events
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Device: "/dev/input/event6"
[    19.167] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found 3 mouse buttons
[    19.167] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found scroll wheel(s)
[    19.167] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found relative axes
[    19.167] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found x and y relative axes
[    19.167] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Configuring as mouse
[    19.167] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Adding scrollwheel support
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: YAxisMapping: buttons 4 and 5
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.167] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.2/input/input6/event6"
[    19.167] (II) XINPUT: Adding extended input device "Dell Dell KM632 Wireless Keyboard and Mouse" (type: MOUSE)
[    19.167] (II) Dell Dell KM632 Wireless Keyboard and Mouse: initialized for relative axes.
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) keeping acceleration scheme 1
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration profile 0
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration factor: 2.000
[    19.167] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration threshold: 4
[    19.167] (II) config/udev: Adding input device Dell Dell KM632 Wireless Keyboard and Mouse (/dev/input/mouse1)
[    19.167] (II) No input driver/identifier specified (ignoring)
[    19.169] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    19.169] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.169] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.169] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.169] (**) AT Translated Set 2 keyboard: always reports core events
[    19.169] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    19.169] (--) AT Translated Set 2 keyboard: Found keys
[    19.169] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.169] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    19.169] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.169] (**) Option "xkb_rules" "evdev"
[    19.169] (**) Option "xkb_model" "pc105"
[    19.169] (**) Option "xkb_layout" "gb"
[    19.172] (II) config/udev: Adding input device Dell AIO WMI hotkeys (/dev/input/event10)
[    19.172] (**) Dell AIO WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    19.172] (II) Using input driver 'evdev' for 'Dell AIO WMI hotkeys'
[    19.172] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.172] (**) Dell AIO WMI hotkeys: always reports core events
[    19.172] (**) Dell AIO WMI hotkeys: Device: "/dev/input/event10"
[    19.172] (--) Dell AIO WMI hotkeys: Found keys
[    19.172] (II) Dell AIO WMI hotkeys: Configuring as keyboard
[    19.172] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[    19.172] (II) XINPUT: Adding extended input device "Dell AIO WMI hotkeys" (type: KEYBOARD)
[    19.172] (**) Option "xkb_rules" "evdev"
[    19.172] (**) Option "xkb_model" "pc105"
[    19.172] (**) Option "xkb_layout" "gb"

```

And here's the same file in a normal boot (the one that doesn't work):
```
[    18.946] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    18.946] X Protocol Version 11, Revision 0
[    18.946] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    18.946] Current Operating System: Linux athena 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    18.946] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=6f471731-4074-41a1-b9ab-fea2c6469ac4 ro quiet splash vt.handoff=7
[    18.946] Build Date: 19 October 2011  05:21:26AM
[    18.946] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    18.946] Current version of pixman: 0.22.2
[    18.946] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.946] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.946] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  9 21:36:41 2011
[    18.946] (==) Using config file: "/etc/X11/xorg.conf"
[    18.946] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.946] (==) No Layout section.  Using the first Screen section.
[    18.946] (==) No screen section available. Using defaults.
[    18.946] (**) |-->Screen "Default Screen Section" (0)
[    18.946] (**) |   |-->Monitor "<default monitor>"
[    18.946] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    18.946] (**) |   |-->Device "Default Device"
[    18.946] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.946] (==) Automatically adding devices
[    18.946] (==) Automatically enabling devices
[    18.946] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.946] 	Entry deleted from font path.
[    18.946] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.946] 	Entry deleted from font path.
[    18.946] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.946] 	Entry deleted from font path.
[    18.946] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.946] 	Entry deleted from font path.
[    18.946] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.946] 	Entry deleted from font path.
[    18.946] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.946] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.946] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.946] (II) Loader magic: 0x7e0220
[    18.946] (II) Module ABI versions:
[    18.946] 	X.Org ANSI C Emulation: 0.4
[    18.946] 	X.Org Video Driver: 10.0
[    18.946] 	X.Org XInput driver : 12.3
[    18.946] 	X.Org Server Extension : 5.0
[    18.947] (--) PCI:*(0:0:2:0) 8086:0102:1028:0512 rev 9, Mem @ 0xfb400000/4194304, 0xc0000000/268435456, I/O @ 0x0000f000/64
[    18.947] (--) PCI: (0:1:0:0) 10de:0df5:1028:0512 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    18.947] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.947] (II) LoadModule: "extmod"
[    18.961] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.962] (II) Module extmod: vendor="X.Org Foundation"
[    18.962] 	compiled for 1.10.4, module version = 1.0.0
[    18.962] 	Module class: X.Org Server Extension
[    18.962] 	ABI class: X.Org Server Extension, version 5.0
[    18.962] (II) Loading extension MIT-SCREEN-SAVER
[    18.962] (II) Loading extension XFree86-VidModeExtension
[    18.962] (II) Loading extension XFree86-DGA
[    18.962] (II) Loading extension DPMS
[    18.962] (II) Loading extension XVideo
[    18.962] (II) Loading extension XVideo-MotionCompensation
[    18.962] (II) Loading extension X-Resource
[    18.962] (II) LoadModule: "dbe"
[    18.962] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.962] (II) Module dbe: vendor="X.Org Foundation"
[    18.962] 	compiled for 1.10.4, module version = 1.0.0
[    18.962] 	Module class: X.Org Server Extension
[    18.962] 	ABI class: X.Org Server Extension, version 5.0
[    18.962] (II) Loading extension DOUBLE-BUFFER
[    18.962] (II) LoadModule: "glx"
[    18.962] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.962] (II) Module glx: vendor="X.Org Foundation"
[    18.962] 	compiled for 1.10.4, module version = 1.0.0
[    18.962] 	ABI class: X.Org Server Extension, version 5.0
[    18.962] (==) AIGLX enabled
[    18.962] (II) Loading extension GLX
[    18.962] (II) LoadModule: "record"
[    18.962] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.962] (II) Module record: vendor="X.Org Foundation"
[    18.962] 	compiled for 1.10.4, module version = 1.13.0
[    18.962] 	Module class: X.Org Server Extension
[    18.962] 	ABI class: X.Org Server Extension, version 5.0
[    18.962] (II) Loading extension RECORD
[    18.962] (II) LoadModule: "dri"
[    18.963] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.963] (II) Module dri: vendor="X.Org Foundation"
[    18.963] 	compiled for 1.10.4, module version = 1.0.0
[    18.963] 	ABI class: X.Org Server Extension, version 5.0
[    18.963] (II) Loading extension XFree86-DRI
[    18.963] (II) LoadModule: "dri2"
[    18.963] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.963] (II) Module dri2: vendor="X.Org Foundation"
[    18.963] 	compiled for 1.10.4, module version = 1.2.0
[    18.963] 	ABI class: X.Org Server Extension, version 5.0
[    18.963] (II) Loading extension DRI2
[    18.963] (==) Matched intel as autoconfigured driver 0
[    18.963] (==) Matched vesa as autoconfigured driver 1
[    18.963] (==) Matched fbdev as autoconfigured driver 2
[    18.963] (==) Assigned the driver to the xf86ConfigLayout
[    18.963] (II) LoadModule: "intel"
[    18.963] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.963] (II) Module intel: vendor="X.Org Foundation"
[    18.963] 	compiled for 1.10.2.902, module version = 2.15.901
[    18.963] 	Module class: X.Org Video Driver
[    18.963] 	ABI class: X.Org Video Driver, version 10.0
[    18.963] (II) LoadModule: "vesa"
[    18.963] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.963] (II) Module vesa: vendor="X.Org Foundation"
[    18.963] 	compiled for 1.10.2, module version = 2.3.0
[    18.963] 	Module class: X.Org Video Driver
[    18.963] 	ABI class: X.Org Video Driver, version 10.0
[    18.963] (II) LoadModule: "fbdev"
[    18.963] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.964] (II) Module fbdev: vendor="X.Org Foundation"
[    18.964] 	compiled for 1.10.0, module version = 0.4.2
[    18.964] 	ABI class: X.Org Video Driver, version 10.0
[    18.964] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    18.964] (II) VESA: driver for VESA chipsets: vesa
[    18.964] (II) FBDEV: driver for framebuffer: fbdev
[    18.964] (++) using VT number 7

[    18.965] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.965] (WW) Falling back to old probe method for vesa
[    18.965] (WW) Falling back to old probe method for fbdev
[    18.965] (II) Loading sub module "fbdevhw"
[    18.965] (II) LoadModule: "fbdevhw"
[    18.965] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.965] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.965] 	compiled for 1.10.4, module version = 0.0.2
[    18.965] 	ABI class: X.Org Video Driver, version 10.0
[    18.965] drmOpenDevice: node name is /dev/dri/card0
[    18.965] drmOpenDevice: open result is 12, (OK)
[    20.132] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    20.132] drmOpenDevice: node name is /dev/dri/card0
[    20.132] drmOpenDevice: open result is 12, (OK)
[    20.132] drmOpenByBusid: drmOpenMinor returns 12
[    20.132] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    20.132] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    20.132] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    20.132] (==) intel(0): RGB weight 888
[    20.132] (==) intel(0): Default visual is TrueColor
[    20.132] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Desktop (GT1)
[    20.132] (--) intel(0): Chipset: "Sandybridge Desktop (GT1)"
[    20.132] (**) intel(0): Relaxed fencing enabled
[    20.132] (**) intel(0): Wait on SwapBuffers? enabled
[    20.132] (**) intel(0): Triple buffering? enabled
[    20.132] (**) intel(0): Framebuffer tiled
[    20.132] (**) intel(0): Pixmaps tiled
[    20.132] (**) intel(0): 3D buffers tiled
[    20.132] (**) intel(0): SwapBuffers wait enabled
[    20.132] (==) intel(0): video overlay key set to 0x101fe
[    21.172] (II) intel(0): Output eDP1 has no monitor section
[    21.173] (II) intel(0): Output VGA1 has no monitor section
[    22.027] (II) intel(0): Output HDMI1 has no monitor section
[    22.076] (II) intel(0): Output DP1 has no monitor section
[    22.932] (II) intel(0): Output HDMI2 has no monitor section
[    24.820] (II) intel(0): Output HDMI3 has no monitor section
[    25.284] (II) intel(0): Output DP2 has no monitor section
[    27.420] (II) intel(0): EDID for output eDP1
[    27.420] (II) intel(0): Manufacturer: CHR  Model: 608  Serial#: 880
[    27.420] (II) intel(0): Year: 2011  Week: 21
[    27.420] (II) intel(0): EDID Version: 1.4
[    27.420] (II) intel(0): Digital Display Input
[    27.420] (II) intel(0): 8 bits per channel
[    27.420] (II) intel(0): Digital interface is DisplayPort
[    27.420] (II) intel(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    27.420] (II) intel(0): Gamma: 2.20
[    27.420] (II) intel(0): DPMS capabilities: StandBy Suspend Off
[    27.420] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.420] (II) intel(0): First detailed timing is preferred mode
[    27.420] (II) intel(0): Preferred mode is native pixel format and refresh rate
[    27.420] (II) intel(0): redX: 0.674 redY: 0.316   greenX: 0.188 greenY: 0.703
[    27.420] (II) intel(0): blueX: 0.146 blueY: 0.062   whiteX: 0.312 whiteY: 0.326
[    27.420] (II) intel(0): Manufacturer's mask: 0
[    27.420] (II) intel(0): Supported detailed timing:
[    27.420] (II) intel(0): clock: 134.6 MHz   Image Size:  509 x 286 mm
[    27.420] (II) intel(0): h_active: 1920  h_sync: 1936  h_sync_end 1968 h_blank_end 2020 h_border: 0
[    27.420] (II) intel(0): v_active: 1080  v_sync: 1085  v_sync_end 1095 v_blanking: 1111 v_border: 0
[    27.420] (II) intel(0): Established timings III: (not decoded)
[    27.420] (II) intel(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    27.420] (II) intel(0): Monitor name: 23" AIO
[    27.420] (II) intel(0): EDID (in hex):
[    27.420] (II) intel(0): 	00ffffffffffff000d12080670030000
[    27.420] (II) intel(0): 	15150104a5342078ea8042ac5130b425
[    27.420] (II) intel(0): 	10505300000001010101010101010101
[    27.420] (II) intel(0): 	0101010101019434806470381f401020
[    27.420] (II) intel(0): 	5a00fd1e1100001c000000f7000a0000
[    27.420] (II) intel(0): 	00000000000000000000000000fd0038
[    27.420] (II) intel(0): 	4c1e5311000a202020202020000000fc
[    27.420] (II) intel(0): 	003233222041494f0a202020202000d8
[    27.420] (II) intel(0): EDID vendor "CHR", prod id 1544
[    27.420] (II) intel(0): Using EDID range info for horizontal sync
[    27.420] (II) intel(0): Using EDID range info for vertical refresh
[    27.420] (II) intel(0): Printing DDC gathered Modelines:
[    27.420] (II) intel(0): Modeline "1920x1080"x0.0  134.60  1920 1936 1968 2020  1080 1085 1095 1111 -hsync +vsync (66.6 kHz)
[    27.420] (II) intel(0): Printing probed modes for output eDP1
[    27.420] (II) intel(0): Modeline "1920x1080"x60.0  134.60  1920 1936 1968 2020  1080 1085 1095 1111 -hsync +vsync (66.6 kHz)
[    27.420] (II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    27.420] (II) intel(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    27.420] (II) intel(0): EDID for output VGA1
[    28.275] (II) intel(0): EDID for output HDMI1
[    28.324] (II) intel(0): EDID for output DP1
[    28.346] (II) intel(0): EDID for output HDMI2
[    28.984] (II) intel(0): EDID for output HDMI3
[    29.860] (II) intel(0): EDID for output DP2
[    29.860] (II) intel(0): Output eDP1 connected
[    29.860] (II) intel(0): Output VGA1 disconnected
[    29.860] (II) intel(0): Output HDMI1 disconnected
[    29.860] (II) intel(0): Output DP1 disconnected
[    29.860] (II) intel(0): Output HDMI2 disconnected
[    29.860] (II) intel(0): Output HDMI3 disconnected
[    29.860] (II) intel(0): Output DP2 disconnected
[    29.860] (II) intel(0): Using exact sizes for initial modes
[    29.860] (II) intel(0): Output eDP1 using initial mode 1920x1080
[    29.860] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.860] (II) intel(0): Kernel page flipping support detected, enabling
[    29.860] (**) intel(0): Display dimensions: (520, 320) mm
[    29.860] (**) intel(0): DPI set to (93, 85)
[    29.860] (II) Loading sub module "fb"
[    29.860] (II) LoadModule: "fb"
[    29.860] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.860] (II) Module fb: vendor="X.Org Foundation"
[    29.860] 	compiled for 1.10.4, module version = 1.0.0
[    29.860] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    29.860] (II) Loading sub module "dri2"
[    29.860] (II) LoadModule: "dri2"
[    29.860] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.860] (II) Module dri2: vendor="X.Org Foundation"
[    29.860] 	compiled for 1.10.4, module version = 1.2.0
[    29.860] 	ABI class: X.Org Server Extension, version 5.0
[    29.860] (II) UnloadModule: "vesa"
[    29.860] (II) Unloading vesa
[    29.860] (II) UnloadModule: "fbdev"
[    29.860] (II) Unloading fbdev
[    29.860] (II) UnloadModule: "fbdevhw"
[    29.860] (II) Unloading fbdevhw
[    29.860] (==) Depth 24 pixmap format is 32 bpp
[    29.860] (II) intel(0): [DRI2] Setup complete
[    29.860] (II) intel(0): [DRI2]   DRI driver: i965
[    29.860] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[    29.861] (II) UXA(0): Driver registered support for the following operations:
[    29.861] (II)         solid
[    29.861] (II)         copy
[    29.861] (II)         composite (RENDER acceleration)
[    29.861] (II)         put_image
[    29.861] (II)         get_image
[    29.861] (==) intel(0): Backing store disabled
[    29.861] (==) intel(0): Silken mouse enabled
[    29.861] (II) intel(0): Initializing HW Cursor
[    31.584] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    35.744] (==) intel(0): DPMS enabled
[    35.744] (==) intel(0): Intel XvMC decoder enabled
[    35.744] (II) intel(0): Set up textured video
[    35.744] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    35.744] (II) intel(0): direct rendering: DRI2 Enabled
[    35.744] (WW) intel(0): Option "NoLogo" is not used
[    35.744] (==) intel(0): hotplug detection: "enabled"
[    35.744] (--) RandR disabled
[    35.744] (II) Initializing built-in extension Generic Event Extension
[    35.744] (II) Initializing built-in extension SHAPE
[    35.744] (II) Initializing built-in extension MIT-SHM
[    35.744] (II) Initializing built-in extension XInputExtension
[    35.744] (II) Initializing built-in extension XTEST
[    35.744] (II) Initializing built-in extension BIG-REQUESTS
[    35.744] (II) Initializing built-in extension SYNC
[    35.744] (II) Initializing built-in extension XKEYBOARD
[    35.744] (II) Initializing built-in extension XC-MISC
[    35.744] (II) Initializing built-in extension SECURITY
[    35.744] (II) Initializing built-in extension XINERAMA
[    35.744] (II) Initializing built-in extension XFIXES
[    35.744] (II) Initializing built-in extension RENDER
[    35.744] (II) Initializing built-in extension RANDR
[    35.744] (II) Initializing built-in extension COMPOSITE
[    35.744] (II) Initializing built-in extension DAMAGE
[    35.744] (II) Initializing built-in extension GESTURE
[    35.747] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[    35.749] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    35.749] (II) AIGLX: enabled GLX_INTEL_swap_event
[    35.749] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    35.749] (II) AIGLX: enabled GLX_SGI_make_current_read
[    35.749] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    35.749] (II) AIGLX: Loaded and initialized i965
[    35.749] (II) GLX: Initialized DRI2 GL provider for screen 0
[    35.750] (II) intel(0): Setting screen physical size to 508 x 285
[    35.754] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    35.758] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    35.758] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.758] (II) LoadModule: "evdev"
[    35.758] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.759] (II) Module evdev: vendor="X.Org Foundation"
[    35.759] 	compiled for 1.10.2, module version = 2.6.0
[    35.759] 	Module class: X.Org XInput Driver
[    35.759] 	ABI class: X.Org XInput driver, version 12.3
[    35.759] (II) Using input driver 'evdev' for 'Power Button'
[    35.759] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.759] (**) Power Button: always reports core events
[    35.759] (**) Power Button: Device: "/dev/input/event1"
[    35.759] (--) Power Button: Found keys
[    35.759] (II) Power Button: Configuring as keyboard
[    35.759] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    35.759] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    35.759] (**) Option "xkb_rules" "evdev"
[    35.759] (**) Option "xkb_model" "pc105"
[    35.759] (**) Option "xkb_layout" "gb"
[    35.760] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    35.761] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    35.761] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    35.761] (II) Using input driver 'evdev' for 'Video Bus'
[    35.761] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.761] (**) Video Bus: always reports core events
[    35.761] (**) Video Bus: Device: "/dev/input/event10"
[    35.761] (--) Video Bus: Found keys
[    35.761] (II) Video Bus: Configuring as keyboard
[    35.761] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10/event10"
[    35.761] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    35.761] (**) Option "xkb_rules" "evdev"
[    35.761] (**) Option "xkb_model" "pc105"
[    35.761] (**) Option "xkb_layout" "gb"
[    35.762] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    35.762] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    35.762] (II) Using input driver 'evdev' for 'Video Bus'
[    35.762] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.762] (**) Video Bus: always reports core events
[    35.762] (**) Video Bus: Device: "/dev/input/event9"
[    35.762] (--) Video Bus: Found keys
[    35.762] (II) Video Bus: Configuring as keyboard
[    35.762] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input9/event9"
[    35.762] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    35.762] (**) Option "xkb_rules" "evdev"
[    35.762] (**) Option "xkb_model" "pc105"
[    35.762] (**) Option "xkb_layout" "gb"
[    35.763] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    35.763] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    35.763] (II) Using input driver 'evdev' for 'Power Button'
[    35.763] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.763] (**) Power Button: always reports core events
[    35.763] (**) Power Button: Device: "/dev/input/event0"
[    35.763] (--) Power Button: Found keys
[    35.763] (II) Power Button: Configuring as keyboard
[    35.763] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    35.763] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    35.763] (**) Option "xkb_rules" "evdev"
[    35.763] (**) Option "xkb_model" "pc105"
[    35.763] (**) Option "xkb_layout" "gb"
[    35.764] (II) config/udev: Adding input device Quanta OpticalTouchScreen (/dev/input/event3)
[    35.764] (**) Quanta OpticalTouchScreen: Applying InputClass "evdev tablet catchall"
[    35.764] (II) Using input driver 'evdev' for 'Quanta OpticalTouchScreen'
[    35.764] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.764] (**) Quanta OpticalTouchScreen: always reports core events
[    35.764] (**) Quanta OpticalTouchScreen: Device: "/dev/input/event3"
[    35.764] (--) Quanta OpticalTouchScreen: Found 3 mouse buttons
[    35.764] (--) Quanta OpticalTouchScreen: Found absolute axes
[    35.764] (II) evdev-grail: failed to open grail, no gesture support
[    35.764] (--) Quanta OpticalTouchScreen: Found x and y absolute axes
[    35.764] (--) Quanta OpticalTouchScreen: Found absolute tablet.
[    35.764] (II) Quanta OpticalTouchScreen: Configuring as tablet
[    35.764] (**) Quanta OpticalTouchScreen: YAxisMapping: buttons 4 and 5
[    35.764] (**) Quanta OpticalTouchScreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.764] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input3/event3"
[    35.764] (II) XINPUT: Adding extended input device "Quanta OpticalTouchScreen" (type: TABLET)
[    35.764] (II) Quanta OpticalTouchScreen: initialized for absolute axes.
[    35.764] (**) Quanta OpticalTouchScreen: (accel) keeping acceleration scheme 1
[    35.764] (**) Quanta OpticalTouchScreen: (accel) acceleration profile 0
[    35.764] (**) Quanta OpticalTouchScreen: (accel) acceleration factor: 2.000
[    35.764] (**) Quanta OpticalTouchScreen: (accel) acceleration threshold: 4
[    35.765] (II) config/udev: Adding input device Quanta OpticalTouchScreen (/dev/input/mouse0)
[    35.765] (II) No input driver/identifier specified (ignoring)
[    35.765] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event7)
[    35.765] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    35.765] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    35.765] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.765] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    35.765] (**) Laptop_Integrated_Webcam_HD: Device: "/dev/input/event7"
[    35.765] (--) Laptop_Integrated_Webcam_HD: Found keys
[    35.765] (II) Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    35.765] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7/event7"
[    35.765] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD)
[    35.765] (**) Option "xkb_rules" "evdev"
[    35.766] (**) Option "xkb_model" "pc105"
[    35.766] (**) Option "xkb_layout" "gb"
[    35.766] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[    35.766] (II) No input driver/identifier specified (ignoring)
[    35.766] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[    35.766] (II) No input driver/identifier specified (ignoring)
[    35.767] (II) config/udev: Adding input device Dell Dell KM632 Wireless Keyboard and Mouse (/dev/input/event4)
[    35.767] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Applying InputClass "evdev keyboard catchall"
[    35.767] (II) Using input driver 'evdev' for 'Dell Dell KM632 Wireless Keyboard and Mouse'
[    35.767] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.767] (**) Dell Dell KM632 Wireless Keyboard and Mouse: always reports core events
[    35.767] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Device: "/dev/input/event4"
[    35.767] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found keys
[    35.767] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Configuring as keyboard
[    35.767] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input4/event4"
[    35.767] (II) XINPUT: Adding extended input device "Dell Dell KM632 Wireless Keyboard and Mouse" (type: KEYBOARD)
[    35.767] (**) Option "xkb_rules" "evdev"
[    35.767] (**) Option "xkb_model" "pc105"
[    35.767] (**) Option "xkb_layout" "gb"
[    35.768] (II) config/udev: Adding input device Dell Dell KM632 Wireless Keyboard and Mouse (/dev/input/event5)
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Applying InputClass "evdev keyboard catchall"
[    35.768] (II) Using input driver 'evdev' for 'Dell Dell KM632 Wireless Keyboard and Mouse'
[    35.768] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: always reports core events
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Device: "/dev/input/event5"
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found 1 mouse buttons
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found scroll wheel(s)
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found relative axes
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found absolute axes
[    35.768] (II) evdev-grail: failed to open grail, no gesture support
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found keys
[    35.768] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Configuring as mouse
[    35.768] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Configuring as keyboard
[    35.768] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Adding scrollwheel support
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: YAxisMapping: buttons 4 and 5
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.768] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input5/event5"
[    35.768] (II) XINPUT: Adding extended input device "Dell Dell KM632 Wireless Keyboard and Mouse" (type: KEYBOARD)
[    35.768] (**) Option "xkb_rules" "evdev"
[    35.768] (**) Option "xkb_model" "pc105"
[    35.768] (**) Option "xkb_layout" "gb"
[    35.768] (EE) Dell Dell KM632 Wireless Keyboard and Mouse: failed to initialize for relative axes.
[    35.768] (II) Dell Dell KM632 Wireless Keyboard and Mouse: initialized for absolute axes.
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) keeping acceleration scheme 1
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration profile 0
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration factor: 2.000
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration threshold: 4
[    35.768] (II) config/udev: Adding input device Dell Dell KM632 Wireless Keyboard and Mouse (/dev/input/event6)
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Applying InputClass "evdev pointer catchall"
[    35.768] (II) Using input driver 'evdev' for 'Dell Dell KM632 Wireless Keyboard and Mouse'
[    35.768] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: always reports core events
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: Device: "/dev/input/event6"
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found 3 mouse buttons
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found scroll wheel(s)
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found relative axes
[    35.768] (--) Dell Dell KM632 Wireless Keyboard and Mouse: Found x and y relative axes
[    35.768] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Configuring as mouse
[    35.768] (II) Dell Dell KM632 Wireless Keyboard and Mouse: Adding scrollwheel support
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: YAxisMapping: buttons 4 and 5
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    35.768] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.2/input/input6/event6"
[    35.768] (II) XINPUT: Adding extended input device "Dell Dell KM632 Wireless Keyboard and Mouse" (type: MOUSE)
[    35.768] (II) Dell Dell KM632 Wireless Keyboard and Mouse: initialized for relative axes.
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) keeping acceleration scheme 1
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration profile 0
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration factor: 2.000
[    35.768] (**) Dell Dell KM632 Wireless Keyboard and Mouse: (accel) acceleration threshold: 4
[    35.769] (II) config/udev: Adding input device Dell Dell KM632 Wireless Keyboard and Mouse (/dev/input/mouse1)
[    35.769] (II) No input driver/identifier specified (ignoring)
[    35.770] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    35.770] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    35.770] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    35.770] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.770] (**) AT Translated Set 2 keyboard: always reports core events
[    35.770] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    35.770] (--) AT Translated Set 2 keyboard: Found keys
[    35.770] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    35.770] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    35.770] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    35.770] (**) Option "xkb_rules" "evdev"
[    35.770] (**) Option "xkb_model" "pc105"
[    35.770] (**) Option "xkb_layout" "gb"
[    35.773] (II) config/udev: Adding input device Dell AIO WMI hotkeys (/dev/input/event8)
[    35.773] (**) Dell AIO WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    35.773] (II) Using input driver 'evdev' for 'Dell AIO WMI hotkeys'
[    35.773] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    35.773] (**) Dell AIO WMI hotkeys: always reports core events
[    35.773] (**) Dell AIO WMI hotkeys: Device: "/dev/input/event8"
[    35.773] (--) Dell AIO WMI hotkeys: Found keys
[    35.773] (II) Dell AIO WMI hotkeys: Configuring as keyboard
[    35.773] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[    35.773] (II) XINPUT: Adding extended input device "Dell AIO WMI hotkeys" (type: KEYBOARD)
[    35.773] (**) Option "xkb_rules" "evdev"
[    35.773] (**) Option "xkb_model" "pc105"
[    35.773] (**) Option "xkb_layout" "gb"
[    39.964] (II) intel(0): EDID vendor "CHR", prod id 1544
[    39.964] (II) intel(0): Using hsync ranges from config file
[    39.964] (II) intel(0): Using vrefresh ranges from config file
[    39.964] (II) intel(0): Printing DDC gathered Modelines:
[    39.964] (II) intel(0): Modeline "1920x1080"x0.0  134.60  1920 1936 1968 2020  1080 1085 1095 1111 -hsync +vsync (66.6 kHz)
[    44.124] (II) intel(0): EDID vendor "CHR", prod id 1544
[    44.124] (II) intel(0): Using hsync ranges from config file
[    44.124] (II) intel(0): Using vrefresh ranges from config file
[    44.124] (II) intel(0): Printing DDC gathered Modelines:
[    44.124] (II) intel(0): Modeline "1920x1080"x0.0  134.60  1920 1936 1968 2020  1080 1085 1095 1111 -hsync +vsync (66.6 kHz)

```


I note that fortunately the right resolution is detected 1920x1080 but I can't see anything but black screen. Also, 4 kworker processes are eating my processor away. Maybe something to do with ACPI... anyway to turn it off?

---

### Post by pmatos on 2011-11-09
Here's a further update. The black screen has nothing to do with the kworker threads eating the CPU. I manage to stop the kworker threads to eat the CPU by following the instructions in 
[http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/](http://souriguha.wordpress.com/2011/03/08/how-to-solve-problem-with-thinkpadkslowd-kworker-on-linux-kernel-2-35-2-36/)

It has something to do with an intel graphics cards.

I am now thinking that maybe the modeline is being incorrectly detected and set so I will try to set that manually.

---

### Post by pmatos on 2011-11-14
OK, there's bug in the intel driver:
[https://bugs.freedesktop.org/show_bug.cgi?id=42278](https://bugs.freedesktop.org/show_bug.cgi?id=42278)

---

### Post by Matt_Fussell on 2011-12-14
I see that the last post on this was about a month ago; have you made any headway with it since then?

I've tried the latest Nvidia drivers - unsuccesful
I tried Ironhide, though I may have set it up incorrectly
No luck with BIOS

I've got a new install and I've found a thread here:

[nVidia Optimus and Ubuntu explained [UPDATED]]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus")

It looks as though it may have a solution, though if you've knocked the bugs out, I'm all ears... well, eyes, as it were.

---

### Post by pmatos on 2011-12-14
> **Matt_Fussell said:**
> I see that the last post on this was about a month ago; have you made any headway with it since then?

I've tried the latest Nvidia drivers - unsuccesful
I tried Ironhide, though I may have set it up incorrectly
No luck with BIOS

I've got a new install and I've found a thread here:

[nVidia Optimus and Ubuntu explained [UPDATED]]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus")

It looks as though it may have a solution, though if you've knocked the bugs out, I'm all ears... well, eyes, as it were.

Unfortunately currently this is not even a problem with Optimus since you could use the intel driver and ignore the nvidia (but not the other way around). The problem is that the intel driver has a bug and won't work with the video card in the vostro 360. Until [https://bugs.freedesktop.org/show_bug.cgi?id=42278](https://bugs.freedesktop.org/show_bug.cgi?id=42278) is sorted out there's no way out. So, unless you want to join the efforts to fix the bug, all you can do is wait.

Linux works in low resolution if you use the vesa driver though so you might want to give that a try. I actually hated the low res so much that I am using windows until the bug is sorted.

---

### Post by Matt_Fussell on 2011-12-14
> **pmatos said:**
> Unfortunately currently this is not even a problem with Optimus since you could use the intel driver and ignore the nvidia (but not the other way around). The problem is that the intel driver has a bug and won't work with the video card in the vostro 360. Until [https://bugs.freedesktop.org/show_bug.cgi?id=42278](https://bugs.freedesktop.org/show_bug.cgi?id=42278) is sorted out there's no way out. So, unless you want to join the efforts to fix the bug, all you can do is wait.

Linux works in low resolution if you use the vesa driver though so you might want to give that a try. I actually hated the low res so much that I am using windows until the bug is sorted.

Unfortunately, the low-res driver won't work, as these machines are being used in a business, and subsequently must be as close to the Mac ease-of-use standard as possible; it was my hope that these machines would be a low cost alternative.  Equally unfortunate is that my coding skills are not strong at this point in life, so I doubt I could contribute much to the other project.  I suppose I am forced to wait.  Thanks for the effort.

---

### Post by pmatos on 2011-12-15
> **Matt_Fussell said:**
> Unfortunately, the low-res driver won't work, as these machines are being used in a business, and subsequently must be as close to the Mac ease-of-use standard as possible; it was my hope that these machines would be a low cost alternative.  Equally unfortunate is that my coding skills are not strong at this point in life, so I doubt I could contribute much to the other project.  I suppose I am forced to wait.  Thanks for the effort.

Same situation here. I bought it as a non-MacOsX alternative to the all-in-one from Apple and expected it to just work and I have been having crazy problems with it.. :(

You're already lucky if your Vostro doesn't make a noise whenever the brightness of display is at max. Already got a Dell eng twice to look at it and he couldn't fix it.

---

### Post by Matt_Fussell on 2011-12-15
> **pmatos said:**
> Same situation here. I bought it as a non-MacOsX alternative to the all-in-one from Apple and expected it to just work and I have been having crazy problems with it.. :(

You're already lucky if your Vostro doesn't make a noise whenever the brightness of display is at max. Already got a Dell eng twice to look at it and he couldn't fix it.

We haven't had that problem with them, but unless a driver solution rolls out in very short order we're probably not going to have them very long; I can't justify keeping equipment that doesn't work in our environment.

---

