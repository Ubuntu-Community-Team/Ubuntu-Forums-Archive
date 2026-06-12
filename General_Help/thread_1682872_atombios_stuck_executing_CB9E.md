---
title: "atombios stuck executing CB9E"
date: 2011-02-06
forum: General Help
---

### Post by rimez on 2011-02-06
I have a very strange issue. Whenever I logout of my Gnome session I am taken to a console where I see an error message that keeps repeating ([see image here]("http://goo.gl/U2R0y") [http://goo.gl/U2R0y](http://goo.gl/U2R0y) [IMG]http://goo.gl/U2R0y[/IMG] ): The key thing is says is: "atombios stuck executing CB9E". 
After about 30-45 seconds of watching the text, it goes back into GDM where I can log in normally. 

I'm using Ubuntu 10.10 Maverick Meerkat 64bit
My laptop is an Acer Aspire TimelineX 3820TG
The Video Card (which I suspect the issue is coming from) is an ATI Mobility Radeon HD 5650. 

Does anyone have a clue as to what the issue could be? If so, I would appreciate any advice on how to get rid of it.

---

### Post by rimez on 2011-02-07
Here's a dmesg dump (after logging out of Gnome desktop):

```

[    0.000000]   #31 [0001d3d280 - 0001d3d2e8]         BOOTMEM
[    0.000000]   #32 [0001d3d300 - 0001d3d368]         BOOTMEM
[    0.000000]   #33 [0001d3d380 - 0001d3d3e8]         BOOTMEM
[    0.000000]   #34 [0001d3d400 - 0001d3d468]         BOOTMEM
[    0.000000]   #35 [0001d3d480 - 0001d3d4e8]         BOOTMEM
[    0.000000]   #36 [0001d3d500 - 0001d3d568]         BOOTMEM
[    0.000000]   #37 [0001d3d580 - 0001d3d5e8]         BOOTMEM
[    0.000000]   #38 [0001d3d600 - 0001d3d668]         BOOTMEM
[    0.000000]   #39 [0001d3d680 - 0001d3d6e8]         BOOTMEM
[    0.000000]   #40 [0001d3d700 - 0001d3d768]         BOOTMEM
[    0.000000]   #41 [0001d3d780 - 0001d3d7e8]         BOOTMEM
[    0.000000]   #42 [0001d3d800 - 0001d3d868]         BOOTMEM
[    0.000000]   #43 [0001d3d880 - 0001d3d8e8]         BOOTMEM
[    0.000000]   #44 [0001d3d900 - 0001d3d968]         BOOTMEM
[    0.000000]   #45 [0001d3d980 - 0001d3d9e8]         BOOTMEM
[    0.000000]   #46 [0001d3da00 - 0001d3da68]         BOOTMEM
[    0.000000]   #47 [0001d3da80 - 0001d3dae8]         BOOTMEM
[    0.000000]   #48 [0001d3db00 - 0001d3db68]         BOOTMEM
[    0.000000]   #49 [0001d3db80 - 0001d3dbe8]         BOOTMEM
[    0.000000]   #50 [0001d3dc00 - 0001d3dc68]         BOOTMEM
[    0.000000]   #51 [0001d3dc80 - 0001d3dce8]         BOOTMEM
[    0.000000]   #52 [0001d3dd00 - 0001d3dd68]         BOOTMEM
[    0.000000]   #53 [0001d3dd80 - 0001d3dde8]         BOOTMEM
[    0.000000]   #54 [0001d3de00 - 0001d3de68]         BOOTMEM
[    0.000000]   #55 [0001d3de80 - 0001d3dea0]         BOOTMEM
[    0.000000]   #56 [0001d3dec0 - 0001d3dee0]         BOOTMEM
[    0.000000]   #57 [0001d3df00 - 0001d3df20]         BOOTMEM
[    0.000000]   #58 [0001d3df40 - 0001d3df60]         BOOTMEM
[    0.000000]   #59 [0001d3df80 - 0001d3dfa0]         BOOTMEM
[    0.000000]   #60 [0001d3dfc0 - 0001d3dfe0]         BOOTMEM
[    0.000000]   #61 [0001d3f000 - 0001d3f020]         BOOTMEM
[    0.000000]   #62 [0001d3f040 - 0001d3f060]         BOOTMEM
[    0.000000]   #63 [0001d3f080 - 0001d3f108]         BOOTMEM
[    0.000000]   #64 [0001d3f140 - 0001d3f1c8]         BOOTMEM
[    0.000000]   #65 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #66 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #67 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #68 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #69 [0001d41200 - 0001d41208]         BOOTMEM
[    0.000000]   #70 [0001d41240 - 0001d41248]         BOOTMEM
[    0.000000]   #71 [0001d41280 - 0001d41290]         BOOTMEM
[    0.000000]   #72 [0001d412c0 - 0001d412e0]         BOOTMEM
[    0.000000]   #73 [0001d41300 - 0001d41430]         BOOTMEM
[    0.000000]   #74 [0001d41440 - 0001d41490]         BOOTMEM
[    0.000000]   #75 [0001d414c0 - 0001d41510]         BOOTMEM
[    0.000000]   #76 [0001d41540 - 0001d49540]         BOOTMEM
[    0.000000]   #77 [0001f9e000 - 0005f9e000]         BOOTMEM
[    0.000000]   #78 [0001d49540 - 0001d69540]         BOOTMEM
[    0.000000]   #79 [0001d69540 - 0001da9540]         BOOTMEM
[    0.000000]   #80 [000001b800 - 0000023800]         BOOTMEM
[    0.000000] Memory: 3708568k/5636096k available (5711k kernel code, 1781384k absent, 146144k reserved, 5379k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:712
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 39321600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2527.035 MHz processor.
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5054.07 BogoMIPS (lpj=25270350)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000029] Security Framework initialized
[    0.000044] AppArmor: AppArmor initialized
[    0.000045] Yama: becoming mindful.
[    0.000394] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.001356] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.001762] Mount-cache hash table entries: 256
[    0.001861] Initializing cgroup subsys ns
[    0.001865] Initializing cgroup subsys cpuacct
[    0.001868] Initializing cgroup subsys memory
[    0.001873] Initializing cgroup subsys devices
[    0.001875] Initializing cgroup subsys freezer
[    0.001877] Initializing cgroup subsys net_cls
[    0.001897] CPU: Physical Processor ID: 0
[    0.001898] CPU: Processor Core ID: 0
[    0.001903] mce: CPU supports 9 MCE banks
[    0.001913] CPU0: Thermal monitoring enabled (TM1)
[    0.001921] using mwait in idle threads.
[    0.001923] Performance Events: PEBS fmt1+, Westmere events, Intel PMU driver.
[    0.001929] ... version:                3
[    0.001930] ... bit width:              48
[    0.001931] ... generic registers:      4
[    0.001932] ... value mask:             0000ffffffffffff
[    0.001933] ... max period:             000000007fffffff
[    0.001934] ... fixed-purpose events:   3
[    0.001935] ... event mask:             000000070000000f
[    0.003785] ACPI: Core revision 20100428
[    0.032716] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032720] ftrace: allocating 22678 entries in 89 pages
[    0.039218] Setting APIC routing to flat
[    0.039551] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.139510] CPU0: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz stepping 05
[    0.259419] Booting Node   0, Processors  #1 #2 #3 Ok.
[    0.799061] Brought up 4 CPUs
[    0.799064] Total of 4 processors activated (20215.99 BogoMIPS).
[    0.800761] devtmpfs: initialized
[    0.801591] regulator: core version 0.5
[    0.801615] Time: 10:29:36  Date: 02/07/11
[    0.801642] NET: Registered protocol family 16
[    0.801724] Trying to unpack rootfs image as initramfs...
[    0.801734] ACPI: bus type pci registered
[    0.801804] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.801807] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.854370] PCI: Using configuration type 1 for base access
[    0.855066] bio: create slab <bio-0> at 0
[    0.856928] ACPI: EC: Look up EC in DSDT
[    0.872106] ACPI: BIOS _OSI(Linux) query honored via cmdline
[    0.873378] ACPI: SSDT 000000009371a918 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.873857] ACPI: Dynamic OEM Table Load:
[    0.873859] ACPI: SSDT (null) 00432 (v01  PmRef  Cpu0Ist 00003000 INTL 20060912)
[    0.874269] ACPI: SSDT 0000000093718018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.874742] ACPI: Dynamic OEM Table Load:
[    0.874744] ACPI: SSDT (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20060912)
[    0.875320] ACPI: SSDT 0000000093719a98 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.875863] ACPI: Dynamic OEM Table Load:
[    0.875865] ACPI: SSDT (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20060912)
[    0.876060] ACPI: SSDT 0000000093717d98 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.876565] ACPI: Dynamic OEM Table Load:
[    0.876567] ACPI: SSDT (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20060912)
[    0.902124] ACPI: Interpreter enabled
[    0.902128] ACPI: (supports S0 S3 S4 S5)
[    0.902151] ACPI: Using IOAPIC for interrupt routing
[    0.918782] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.919318] ACPI: No dock devices found.
[    0.919321] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.920202] \_SB_.PCI0:_OSC invalid UUID
[    0.920204] _OSC request data:1 8 1f 
[    0.920207] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.921507] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.921510] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.921512] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.921514] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.921515] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.921517] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.921520] pci_root PNP0A08:00: host bridge window [mem 0xa0000000-0xfeafffff]
[    0.921578] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.921580] pci 0000:00:01.0: PME# disabled
[    0.921598] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.921602] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.921605] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
[    0.921670] pci 0000:00:16.0: reg 10: [mem 0xf0804000-0xf080400f 64bit]
[    0.921723] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.921726] pci 0000:00:16.0: PME# disabled
[    0.921767] pci 0000:00:1a.0: reg 10: [mem 0xf0806000-0xf08063ff]
[    0.921813] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.921816] pci 0000:00:1a.0: PME# disabled
[    0.921844] pci 0000:00:1b.0: reg 10: [mem 0xf0800000-0xf0803fff 64bit]
[    0.921878] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.921881] pci 0000:00:1b.0: PME# disabled
[    0.921937] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.921940] pci 0000:00:1c.0: PME# disabled
[    0.921993] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.921996] pci 0000:00:1c.1: PME# disabled
[    0.922035] pci 0000:00:1d.0: reg 10: [mem 0xf0807000-0xf08073ff]
[    0.922081] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.922084] pci 0000:00:1d.0: PME# disabled
[    0.922224] pci 0000:00:1f.2: reg 10: [io  0x1818-0x181f]
[    0.922229] pci 0000:00:1f.2: reg 14: [io  0x180c-0x180f]
[    0.922233] pci 0000:00:1f.2: reg 18: [io  0x1810-0x1817]
[    0.922237] pci 0000:00:1f.2: reg 1c: [io  0x1808-0x180b]
[    0.922242] pci 0000:00:1f.2: reg 20: [io  0x1820-0x183f]
[    0.922246] pci 0000:00:1f.2: reg 24: [mem 0xf0808000-0xf08087ff]
[    0.922271] pci 0000:00:1f.2: PME# supported from D3hot
[    0.922274] pci 0000:00:1f.2: PME# disabled
[    0.922296] pci 0000:00:1f.3: reg 10: [mem 0xf0809000-0xf08090ff 64bit]
[    0.922307] pci 0000:00:1f.3: reg 20: [io  0x1840-0x185f]
[    0.922347] pci 0000:00:1f.6: reg 10: [mem 0xf080a000-0xf080afff 64bit]
[    0.922427] pci 0000:02:00.0: reg 10: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.922434] pci 0000:02:00.0: reg 18: [mem 0xafee0000-0xafefffff 64bit]
[    0.922438] pci 0000:02:00.0: reg 20: [io  0x2000-0x20ff]
[    0.922445] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.922460] pci 0000:02:00.0: supports D1 D2
[    0.922483] pci 0000:02:00.1: reg 10: [mem 0xafedc000-0xafedffff 64bit]
[    0.922511] pci 0000:02:00.1: supports D1 D2
[    0.922538] pci 0000:00:01.0: PCI bridge to [bus 02-02]
[    0.922540] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.922542] pci 0000:00:01.0:   bridge window [mem 0xafe00000-0xafefffff]
[    0.922545] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.922608] pci 0000:03:00.0: reg 10: [mem 0xf0400000-0xf043ffff 64bit]
[    0.922615] pci 0000:03:00.0: reg 18: [io  0x3000-0x307f]
[    0.922671] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.922675] pci 0000:03:00.0: PME# disabled
[    0.939078] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    0.939084] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.939087] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.939092] pci 0000:00:1c.0:   bridge window [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.939163] pci 0000:05:00.0: reg 10: [mem 0xf0500000-0xf050ffff 64bit]
[    0.939223] pci 0000:05:00.0: supports D1
[    0.939225] pci 0000:05:00.0: PME# supported from D0 D1 D3hot
[    0.939229] pci 0000:05:00.0: PME# disabled
[    0.959062] pci 0000:00:1c.1: PCI bridge to [bus 05-05]
[    0.959067] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.959071] pci 0000:00:1c.1:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.959075] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.959132] pci 0000:00:1e.0: PCI bridge to [bus 0f-0f] (subtractive decode)
[    0.959135] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.959138] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.959143] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.959145] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.959147] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.959149] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.959151] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.959153] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.959154] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.959156] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xfeafffff] (subtractive decode)
[    0.959188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.959469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.959626] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.959844] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.959984] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.960269] \_SB_.PCI0:_OSC invalid UUID
[    0.960270] _OSC request data:1 1f 1f 
[    0.973494] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.973992] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.974119] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.974244] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.974369] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.974493] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.974620] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.974745] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.974869] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.974927] HEST: Table is not found!
[    0.974997] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.975005] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.975009] vgaarb: loaded
[    0.975115] SCSI subsystem initialized
[    0.975219] libata version 3.00 loaded.
[    0.975264] usbcore: registered new interface driver usbfs
[    0.975273] usbcore: registered new interface driver hub
[    0.975299] usbcore: registered new device driver usb
[    0.975617] ACPI: WMI: Mapper loaded
[    0.975619] PCI: Using ACPI for IRQ routing
[    0.975621] PCI: pci_cache_line_size set to 64 bytes
[    0.975685] reserve RAM buffer: 000000000009c400 - 000000000009ffff 
[    0.975688] reserve RAM buffer: 000000009327c000 - 0000000093ffffff 
[    0.975691] reserve RAM buffer: 00000000933e4000 - 0000000093ffffff 
[    0.975693] reserve RAM buffer: 000000009346f000 - 0000000093ffffff 
[    0.975696] reserve RAM buffer: 0000000093717000 - 0000000093ffffff 
[    0.975698] reserve RAM buffer: 000000009376c000 - 0000000093ffffff 
[    0.975700] reserve RAM buffer: 00000000937dd000 - 0000000093ffffff 
[    0.975702] reserve RAM buffer: 0000000093800000 - 0000000093ffffff 
[    0.975776] NetLabel: Initializing
[    0.975777] NetLabel:  domain hash size = 128
[    0.975778] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.975791] NetLabel:  unlabeled traffic allowed by default
[    0.975818] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.975823] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.977837] Switching to clocksource tsc
[    0.984407] AppArmor: AppArmor Filesystem Enabled
[    0.984424] pnp: PnP ACPI init
[    0.984441] ACPI: bus type pnp registered
[    0.987183] pnp: PnP ACPI: found 11 devices
[    0.987185] ACPI: ACPI bus type pnp unregistered
[    0.987197] system 00:05: [io  0x0500-0x050f] has been reserved
[    0.987199] system 00:05: [io  0xffff] has been reserved
[    0.987201] system 00:05: [io  0xffff] has been reserved
[    0.987203] system 00:05: [io  0x0400-0x047f] has been reserved
[    0.987204] system 00:05: [io  0x1180-0x11ff] has been reserved
[    0.987206] system 00:05: [io  0xfe00] has been reserved
[    0.987208] system 00:05: [mem 0xff800000-0xff800fff] has been reserved
[    0.987212] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.987214] system 00:09: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.987216] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.987218] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.987220] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.987222] system 00:09: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.987224] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.987226] system 00:09: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.987228] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.987230] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.987232] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.992732] pci 0000:00:1c.1: BAR 15: assigned [mem 0xa0000000-0xa01fffff 64bit pref]
[    0.992736] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.992739] pci 0000:02:00.0: BAR 6: assigned [mem 0xafe00000-0xafe1ffff pref]
[    0.992741] pci 0000:00:01.0: PCI bridge to [bus 02-02]
[    0.992744] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.992746] pci 0000:00:01.0:   bridge window [mem 0xafe00000-0xafefffff]
[    0.992749] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.992752] pci 0000:00:1c.0: PCI bridge to [bus 03-04]
[    0.992755] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.992758] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.992761] pci 0000:00:1c.0:   bridge window [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.992767] pci 0000:00:1c.1: PCI bridge to [bus 05-05]
[    0.992769] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.992772] pci 0000:00:1c.1:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.992776] pci 0000:00:1c.1:   bridge window [mem 0xa0000000-0xa01fffff 64bit pref]
[    0.992780] pci 0000:00:1e.0: PCI bridge to [bus 0f-0f]
[    0.992781] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.992785] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.992788] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.992799]   alloc irq_desc for 16 on node -1
[    0.992801]   alloc kstat_irqs on node -1
[    0.992807] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.992810] pci 0000:00:01.0: setting latency timer to 64
[    0.992817] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.992820] pci 0000:00:1c.0: setting latency timer to 64
[    0.992826]   alloc irq_desc for 17 on node -1
[    0.992827]   alloc kstat_irqs on node -1
[    0.992830] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.992833] pci 0000:00:1c.1: setting latency timer to 64
[    0.992838] pci 0000:00:1e.0: setting latency timer to 64
[    0.992842] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.992843] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.992845] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.992846] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.992848] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.992849] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.992851] pci_bus 0000:00: resource 10 [mem 0xa0000000-0xfeafffff]
[    0.992853] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.992854] pci_bus 0000:02: resource 1 [mem 0xafe00000-0xafefffff]
[    0.992856] pci_bus 0000:02: resource 2 [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.992857] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.992859] pci_bus 0000:03: resource 1 [mem 0xf0400000-0xf04fffff]
[    0.992860] pci_bus 0000:03: resource 2 [mem 0xf0a00000-0xf0bfffff 64bit pref]
[    0.992862] pci_bus 0000:05: resource 0 [io  0x4000-0x4fff]
[    0.992864] pci_bus 0000:05: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.992865] pci_bus 0000:05: resource 2 [mem 0xa0000000-0xa01fffff 64bit pref]
[    0.992867] pci_bus 0000:0f: resource 4 [io  0x0000-0x0cf7]
[    0.992869] pci_bus 0000:0f: resource 5 [io  0x0d00-0xffff]
[    0.992870] pci_bus 0000:0f: resource 6 [mem 0x000a0000-0x000bffff]
[    0.992872] pci_bus 0000:0f: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.992873] pci_bus 0000:0f: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.992875] pci_bus 0000:0f: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.992876] pci_bus 0000:0f: resource 10 [mem 0xa0000000-0xfeafffff]
[    0.992909] NET: Registered protocol family 2
[    0.993036] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.993916] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.995660] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.995870] TCP: Hash tables configured (established 524288 bind 65536)
[    0.995872] TCP reno registered
[    0.995881] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.995904] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.996002] NET: Registered protocol family 1
[    0.996021] pci 0000:00:02.0: Boot video device
[    0.996112] PCI: CLS 64 bytes, default 64
[    0.996114] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.996116] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
[    0.996118] software IO TLB at phys 0x1f9e000 - 0x5f9e000
[    0.996147] Simple Boot Flag at 0x3e set to 0x1
[    0.996375] Scanning for low memory corruption every 60 seconds
[    0.996477] audit: initializing netlink socket (disabled)
[    0.996485] type=2000 audit(1297074575.840:1): initialized
[    0.998180] Freeing initrd memory: 10740k freed
[    1.008274] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.009350] VFS: Disk quotas dquot_6.5.2
[    1.009392] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.009837] fuse init (API version 7.14)
[    1.009900] msgmni has been set to 7264
[    1.011604] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.011606] io scheduler noop registered
[    1.011608] io scheduler deadline registered
[    1.011636] io scheduler cfq registered (default)
[    1.011722] pcieport 0000:00:01.0: setting latency timer to 64
[    1.011740]   alloc irq_desc for 40 on node -1
[    1.011742]   alloc kstat_irqs on node -1
[    1.011750] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.011792] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.011817]   alloc irq_desc for 41 on node -1
[    1.011818]   alloc kstat_irqs on node -1
[    1.011823] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.011875] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.011900]   alloc irq_desc for 42 on node -1
[    1.011901]   alloc kstat_irqs on node -1
[    1.011906] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.011967] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.012121] \_SB_.PCI0:_OSC invalid UUID
[    1.012122] _OSC request data:1 0 1f 
[    1.012224] \_SB_.PCI0:_OSC invalid UUID
[    1.012226] _OSC request data:1 0 1f 
[    1.012334] \_SB_.PCI0:_OSC invalid UUID
[    1.012335] _OSC request data:1 0 1f 
[    1.012433] \_SB_.PCI0:_OSC invalid UUID
[    1.012434] _OSC request data:1 0 1f 
[    1.012450] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.012507] intel_idle: MWAIT substates: 0x1120
[    1.012508] intel_idle: v0.4 model 0x25
[    1.012509] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.013889] ACPI: AC Adapter [ADP1] (on-line)
[    1.013965] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.015046] ACPI: Lid Switch [LID0]
[    1.015075] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.015079] ACPI: Sleep Button [SLPB]
[    1.015106] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.015108] ACPI: Power Button [PWRF]
[    1.015608] ACPI: acpi_idle yielding to intel_idle
[    1.039042] thermal LNXTHERM:01: registered as thermal_zone0
[    1.039047] ACPI: Thermal Zone [TZS0] (62 C)
[    1.045265] thermal LNXTHERM:02: registered as thermal_zone1
[    1.045270] ACPI: Thermal Zone [TZS1] (35 C)
[    1.045348] ERST: Table is not found!
[    1.046946] Linux agpgart interface v0.103
[    1.046961] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.047855] brd: module loaded
[    1.048176] loop: module loaded
[    1.048475] Fixed MDIO Bus: probed
[    1.048500] PPP generic driver version 2.4.2
[    1.048524] tun: Universal TUN/TAP device driver, 1.6
[    1.048525] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.048572] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.048591] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.048608] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.048611] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.048636] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.048659] ehci_hcd 0000:00:1a.0: debug port 2
[    1.052612] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.052626] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf0806000
[    1.068916] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.069032] hub 1-0:1.0: USB hub found
[    1.069036] hub 1-0:1.0: 3 ports detected
[    1.069083]   alloc irq_desc for 23 on node -1
[    1.069084]   alloc kstat_irqs on node -1
[    1.069089] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.069099] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.069102] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.069125] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.069145] ehci_hcd 0000:00:1d.0: debug port 2
[    1.073088] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.073101] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf0807000
[    1.088902] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.089038] hub 2-0:1.0: USB hub found
[    1.089042] hub 2-0:1.0: 3 ports detected
[    1.089098] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.089110] uhci_hcd: USB Universal Host Controller Interface driver
[    1.089194] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.111440] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.111445] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.111489] mice: PS/2 mouse device common for all mice
[    1.111565] rtc_cmos 00:06: RTC can wake from S4
[    1.111592] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.111618] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.111684] device-mapper: uevent: version 1.0.3
[    1.111746] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.111831] device-mapper: multipath: version 1.1.1 loaded
[    1.111834] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.112064] cpuidle: using governor ladder
[    1.112584] cpuidle: using governor menu
[    1.112778] TCP cubic registered
[    1.112863] NET: Registered protocol family 10
[    1.113097] lo: Disabled Privacy Extensions
[    1.113235] NET: Registered protocol family 17
[    1.114787] PM: Resume from disk failed.
[    1.114798] registered taskstats version 1
[    1.115053]   Magic number: 15:484:476
[    1.115169] rtc_cmos 00:06: setting system clock to 2011-02-07 10:29:36 UTC (1297074576)
[    1.115173] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.115174] EDD information not available.
[    1.115281] Freeing unused kernel memory: 908k freed
[    1.115444] Write protecting the kernel read-only data: 10240k
[    1.115651] Freeing unused kernel memory: 412k freed
[    1.115862] Freeing unused kernel memory: 1644k freed
[    1.128853] udev[98]: starting version 163
[    1.141943] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.156811] atl1c 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.156825] atl1c 0000:03:00.0: setting latency timer to 64
[    1.169234] ahci 0000:00:1f.2: version 3.0
[    1.169254]   alloc irq_desc for 19 on node -1
[    1.169257]   alloc kstat_irqs on node -1
[    1.169267] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.169326]   alloc irq_desc for 43 on node -1
[    1.169328]   alloc kstat_irqs on node -1
[    1.169337] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    1.169367] ahci: SSS flag set, parallel bus scan disabled
[    1.169389] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    1.169394] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems apst 
[    1.169399] ahci 0000:00:1f.2: setting latency timer to 64
[    1.175021] scsi0 : ahci
[    1.190064] scsi1 : ahci
[    1.210294] scsi2 : ahci
[    1.213149] scsi3 : ahci
[    1.213234] ata1: SATA max UDMA/133 abar m2048@0xf0808000 port 0xf0808100 irq 43
[    1.213237] ata2: DUMMY
[    1.213239] ata3: DUMMY
[    1.213240] ata4: DUMMY
[    1.237497] ACPI: Battery Slot [BAT0] (battery present)
[    1.329640] atl1c 0000:03:00.0: version 1.0.0.2-NAPI
[    1.397788] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.548403] hub 1-1:1.0: USB hub found
[    1.548605] hub 1-1:1.0: 6 ports detected
[    1.561470] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.563722] ata1.00: ATA-8: WDC WD6400BEVT-22A0RT0, 01.01A01, max UDMA/133
[    1.563728] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.566238] ata1.00: configured for UDMA/133
[    1.581583] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400BEVT-2 01.0 PQ: 0 ANSI: 5
[    1.581743] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.581769] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.581818] sd 0:0:0:0: [sda] Write Protect is off
[    1.581821] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.581847] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.582096]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.660616] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.677652] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.822117] hub 2-1:1.0: USB hub found
[    1.822189] hub 2-1:1.0: 8 ports detected
[    2.110077] usb 2-1.2: new low speed USB device using ehci_hcd and address 3
[    2.235529] usbcore: registered new interface driver hiddev
[    2.238884] input: DELL DELL USB Laser Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4
[    2.238957] generic-usb 0003:046D:C063.0001: input,hidraw0: USB HID v1.10 Mouse [DELL DELL USB Laser Mouse] on usb-0000:00:1d.0-1.2/input0
[    2.238969] usbcore: registered new interface driver usbhid
[    2.238970] usbhid: USB HID core driver
[    2.285339] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.307492] usb 2-1.5: new high speed USB device using ehci_hcd and address 4
[   13.474504] udev[449]: starting version 163
[   13.491865] Adding 10903548k swap on /dev/sda6.  Priority:-1 extents:1 across:10903548k 
[   13.492291] lp: driver loaded but no devices found
[   13.611610] intel ips 0000:00:1f.6: Warning: CPU TDP doesn't match expected value (found 25, expected 35)
[   13.611636]   alloc irq_desc for 18 on node -1
[   13.611638]   alloc kstat_irqs on node -1
[   13.611649] intel ips 0000:00:1f.6: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.611822] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
[   13.627973] acer-wmi: Acer Laptop ACPI-WMI Extras
[   13.628196] acer-wmi: Unable to detect available WMID devices
[   13.644128] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 65535
[   13.644360] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[   13.645698] agpgart-intel 0000:00:00.0: detected 131068K stolen memory, trimming to 32768K
[   13.722691] [drm] Initialized drm 1.1.0 20060810
[   13.747517] cfg80211: Calling CRDA to update world regulatory domain
[   13.755462] cfg80211: World regulatory domain updated:
[   13.755467]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.755471]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.755473]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.755476]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.755478]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.755480]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.757527] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   13.809572] ath9k 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.809583] ath9k 0000:05:00.0: setting latency timer to 64
[   13.826106] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.826110] i915 0000:00:02.0: setting latency timer to 64
[   13.828672] Linux video capture interface: v2.00
[   13.835203] type=1400 audit(1297070989.222:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=832 comm="apparmor_parser"
[   13.835698] type=1400 audit(1297070989.222:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=832 comm="apparmor_parser"
[   13.835968] type=1400 audit(1297070989.222:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=832 comm="apparmor_parser"
[   13.837175] type=1400 audit(1297070989.222:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=800 comm="apparmor_parser"
[   13.837663] type=1400 audit(1297070989.222:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=800 comm="apparmor_parser"
[   13.837671] uvcvideo: Found UVC 1.00 device 1.3M WebCam (0402:9665)
[   13.838078] type=1400 audit(1297070989.222:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=800 comm="apparmor_parser"
[   13.844625] input: 1.3M WebCam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input5
[   13.844998] usbcore: registered new interface driver uvcvideo
[   13.845002] USB Video Class driver (v0.1.0)
[   13.896083] [drm] radeon defaulting to kernel modesetting.
[   13.896087] [drm] radeon kernel modesetting enabled.
[   13.896128] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[   13.896180] radeon 0000:02:00.0: enabling device (0104 -> 0107)
[   13.896189] radeon 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.896195] radeon 0000:02:00.0: setting latency timer to 64
[   13.897958] [drm] initializing kernel modesetting (REDWOOD 0x1002:0x68C1).
[   13.899220] ath: EEPROM regdomain: 0x65
[   13.899223] ath: EEPROM indicates we should expect a direct regpair map
[   13.899227] ath: Country alpha2 being used: 00
[   13.899228] ath: Regpair used: 0x65
[   13.900033] [drm] register mmio base: 0xAFEE0000
[   13.900036] [drm] register mmio size: 131072
[   13.920058] [drm] detected 127M stolen memory, trimming to 32M
[   13.920134]   alloc irq_desc for 44 on node -1
[   13.920136]   alloc kstat_irqs on node -1
[   13.920147] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   13.920159] [drm] set up 32M of stolen space
[   13.920488] vga_switcheroo: enabled
[   13.921312] radeon atpx: version is 1
[   13.923736] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.924324] Registered led device: ath9k-phy0::radio
[   13.924339] Registered led device: ath9k-phy0::assoc
[   13.924353] Registered led device: ath9k-phy0::tx
[   13.924368] Registered led device: ath9k-phy0::rx
[   13.924375] phy0: Atheros AR9287 Rev:2 mem=0xffffc900119a0000, irq=17
[   13.992428] ATOM BIOS: MADISON
[   13.992443] [drm] Clocks initialized !
[   13.992457] radeon 0000:02:00.0: VRAM: 1024M 0x00000000 - 0x3FFFFFFF (256M used)
[   13.992460] radeon 0000:02:00.0: GTT: 512M 0x40000000 - 0x5FFFFFFF
[   13.992480] mtrr: no more MTRRs available
[   13.992481] [drm] Detected VRAM RAM=1024M, BAR=256M
[   13.992483] [drm] RAM width 128bits DDR
[   13.992534] [TTM] Zone  kernel: Available graphics memory: 1861136 kiB.
[   13.992536] [TTM] Initializing pool allocator.
[   13.992556] [drm] radeon: 256M of VRAM memory ready
[   13.992557] [drm] radeon: 512M of GTT memory ready.
[   13.992597]   alloc irq_desc for 45 on node -1
[   13.992598]   alloc kstat_irqs on node -1
[   13.992608] radeon 0000:02:00.0: irq 45 for MSI/MSI-X
[   13.992612] radeon 0000:02:00.0: radeon: using MSI.
[   13.992646] [drm] radeon: irq initialized.
[   13.992648] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   13.993180] [drm] Loading REDWOOD Microcode
[   14.029049] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[   14.029055] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   14.151212] [drm] ring test succeeded in 1 usecs
[   14.151317] [drm] radeon: ib pool ready.
[   14.151392] [drm] ib test succeeded in 0 usecs
[   14.152137] [drm] Radeon Display Connectors
[   14.152139] [drm] Connector 0:
[   14.152141] [drm]   LVDS
[   14.152143] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[   14.152145] [drm]   Encoders:
[   14.152147] [drm]     LCD1: INTERNAL_UNIPHY
[   14.152148] [drm] Connector 1:
[   14.152150] [drm]   HDMI-A
[   14.152151] [drm]   HPD1
[   14.152153] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   14.152154] [drm]   Encoders:
[   14.152156] [drm]     DFP1: INTERNAL_UNIPHY1
[   14.152157] [drm] Connector 2:
[   14.152159] [drm]   VGA
[   14.152161] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   14.152162] [drm]   Encoders:
[   14.152164] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   14.189509] Skipping EDID probe due to cached edid
[   14.245173] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   14.336724] Console: switching to colour frame buffer device 160x48
[   14.338784] fb0: inteldrmfb frame buffer device
[   14.338785] drm: registered panic notifier
[   14.338788] Slow work thread pool: Starting up
[   14.338839] Slow work thread pool: Ready
[   14.372228] acpi device:02: registered as cooling_device4
[   14.372574] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input7
[   14.372674] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   14.397436] acpi device:07: registered as cooling_device5
[   14.398048] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   14.398096] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.398163] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.398209]   alloc irq_desc for 22 on node -1
[   14.398211]   alloc kstat_irqs on node -1
[   14.398218] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.398290]   alloc irq_desc for 46 on node -1
[   14.398291]   alloc kstat_irqs on node -1
[   14.398301] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   14.398329] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.500468] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   14.521496] hda_codec: ALC271X: BIOS auto-probing.
[   14.521847] hda_codec: connection list not available for 0x24
[   14.533069] Skipping EDID probe due to cached edid
[   14.624379] [drm] Internal thermal controller without fan control
[   14.624402] [drm] radeon: power management initialized
[   15.214486]   alloc irq_desc for 47 on node -1
[   15.214490]   alloc kstat_irqs on node -1
[   15.214506] atl1c 0000:03:00.0: irq 47 for MSI/MSI-X
[   15.214603] atl1c 0000:03:00.0: atl1c: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[   15.217138] type=1400 audit(1297070990.602:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1268 comm="apparmor_parser"
[   15.217455] type=1400 audit(1297070990.602:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1269 comm="apparmor_parser"
[   15.218012] type=1400 audit(1297070990.602:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1269 comm="apparmor_parser"
[   15.218253] type=1400 audit(1297070990.602:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1269 comm="apparmor_parser"
[   15.302295] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.364288] [drm] fb mappable at 0xB0140000
[   15.364290] [drm] vram apper at 0xB0000000
[   15.364291] [drm] size 4325376
[   15.364292] [drm] fb depth is 24
[   15.364293] [drm]    pitch is 5632
[   15.364371] fb1: radeondrmfb frame buffer device
[   15.364378] [drm] Initialized radeon 2.5.0 20080528 for 0000:02:00.0 on minor 1
[   15.364424] HDA Intel 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.364473]   alloc irq_desc for 48 on node -1
[   15.364475]   alloc kstat_irqs on node -1
[   15.364486] HDA Intel 0000:02:00.1: irq 48 for MSI/MSI-X
[   15.364511] HDA Intel 0000:02:00.1: setting latency timer to 64
[   15.788186] Skipping EDID probe due to cached edid
[   15.808287] vboxdrv: Found 4 processor cores.
[   15.808355] VBoxDrv: dbg - g_abExecMemory=ffffffffa04915e0
[   15.808386] vboxdrv: fAsync=0 offMin=0x1f8 offMax=0xd50
[   15.808434] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   15.808436] vboxdrv: Successfully loaded version 4.0.2 (interface 0x00160000).
[   15.905660] Skipping EDID probe due to cached edid
[   15.979313] ppdev: user-space parallel port driver
[   16.425951] acpi_call: Module loaded successfully
[   17.040763] acpi_call: Calling \_SB.PCI0.P0P1.VGA._OFF
[   17.040772] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   17.041701] acpi_call: Calling \_SB.PCI0.P0P2.VGA._OFF
[   17.041706] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   17.042600] acpi_call: Calling \_SB_.PCI0.OVGA.ATPX
[   17.042607] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   17.043428] acpi_call: Calling \_SB_.PCI0.OVGA.XTPX
[   17.043433] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   17.044164] acpi_call: Calling \_SB.PCI0.P0P3.PEGP._OFF
[   17.044169] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   17.044861] acpi_call: Calling \_SB.PCI0.P0P2.PEGP._OFF
[   17.045473] acpi_call: Call successful: 0x1
[   18.093089] Skipping EDID probe due to cached edid
[   18.210045] Skipping EDID probe due to cached edid
[   18.644599] Skipping EDID probe due to cached edid
[   18.761657] Skipping EDID probe due to cached edid
[   20.063043] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   20.623621] radeon: switched off
[   25.845479] Skipping EDID probe due to cached edid
[   25.962432] Skipping EDID probe due to cached edid
[   26.079402] Skipping EDID probe due to cached edid
[   26.196925] eth0: no IPv6 routers present
[   27.874580] Skipping EDID probe due to cached edid
[   28.603233] wlan0: authenticate with 00:1a:30:b9:da:70 (try 1)
[   28.605235] wlan0: authenticated
[   28.605265] wlan0: associate with 00:1a:30:b9:da:70 (try 1)
[   28.608145] wlan0: RX AssocResp from 00:1a:30:b9:da:70 (capab=0x421 status=0 aid=30)
[   28.608151] wlan0: associated
[   28.608582] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.608655] cfg80211: Calling CRDA for country: SK
[   28.611706] cfg80211: Received country IE:
[   28.611709] cfg80211: Regulatory domain: SK
[   28.611710]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.611712]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 2300 mBm)
[   28.611713] cfg80211: CRDA thinks this should applied:
[   28.611714] cfg80211: Regulatory domain: SK
[   28.611715]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.611717]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   28.611718]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   28.611720]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   28.611721]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   28.611723] cfg80211: We intersect both of these and get:
[   28.611724] cfg80211: Regulatory domain: 98
[   28.611724]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.611726]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   28.611732] cfg80211: Current regulatory domain updated by AP to: SK
[   28.611733]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.611735]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.789948] Skipping EDID probe due to cached edid
[   39.177457] wlan0: no IPv6 routers present
[   80.400372] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  136.637554] wlan0: deauthenticating from 00:1a:30:b9:da:70 by local choice (reason=3)
[  136.718068] cfg80211: All devices are disconnected, going to restore regulatory settings
[  136.718078] cfg80211: Restoring regulatory settings
[  136.718084] cfg80211: Calling CRDA to update world regulatory domain
[  136.722757] cfg80211: World regulatory domain updated:
[  136.722761]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  136.722766]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  136.722770]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  136.722774]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  136.722778]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  136.722782]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  136.753176] wlan0: authenticate with 00:1a:30:8d:bc:b0 (try 1)
[  136.755164] wlan0: authenticated
[  136.755193] wlan0: associate with 00:1a:30:8d:bc:b0 (try 1)
[  136.770454] wlan0: RX AssocResp from 00:1a:30:8d:bc:b0 (capab=0x421 status=0 aid=3)
[  136.770459] wlan0: associated
[  136.771135] cfg80211: Calling CRDA for country: SK
[  136.775795] cfg80211: Received country IE:
[  136.775799] cfg80211: Regulatory domain: SK
[  136.775802]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  136.775807]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 2300 mBm)
[  136.775810] cfg80211: CRDA thinks this should applied:
[  136.775812] cfg80211: Regulatory domain: SK
[  136.775814]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  136.775818]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  136.775822]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  136.775825]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  136.775829]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  136.775831] cfg80211: We intersect both of these and get:
[  136.775834] cfg80211: Regulatory domain: 98
[  136.775836]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  136.775840]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  136.775847] cfg80211: Current regulatory domain updated by AP to: SK
[  136.775850]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  136.775854]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  216.614455] wlan0: deauthenticating from 00:1a:30:8d:bc:b0 by local choice (reason=3)
[  216.654700] cfg80211: All devices are disconnected, going to restore regulatory settings
[  216.654708] cfg80211: Restoring regulatory settings
[  216.654711] cfg80211: Calling CRDA to update world regulatory domain
[  216.690243] wlan0: authenticate with 00:1a:30:b9:da:70 (try 1)
[  216.697103] wlan0: authenticated
[  216.697123] wlan0: associate with 00:1a:30:b9:da:70 (try 1)
[  216.715065] wlan0: RX AssocResp from 00:1a:30:b9:da:70 (capab=0x421 status=0 aid=30)
[  216.715069] wlan0: associated
[  216.715562] cfg80211: Calling CRDA for country: SK
[  216.767743] cfg80211: Received country IE:
[  216.767746] cfg80211: Regulatory domain: SK
[  216.767747]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  216.767749]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 2300 mBm)
[  216.767751] cfg80211: CRDA thinks this should applied:
[  216.767752] cfg80211: Regulatory domain: SK
[  216.767752]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  216.767754]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  216.767756]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  216.767757]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  216.767759]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  216.767760] cfg80211: We intersect both of these and get:
[  216.767761] cfg80211: Regulatory domain: 98
[  216.767762]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  216.767763]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  216.767769] cfg80211: Current regulatory domain updated by AP to: SK
[  216.767770]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  216.767772]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  316.528181] wlan0: deauthenticating from 00:1a:30:b9:da:70 by local choice (reason=3)
[  316.608727] cfg80211: All devices are disconnected, going to restore regulatory settings
[  316.608736] cfg80211: Restoring regulatory settings
[  316.608742] cfg80211: Calling CRDA to update world regulatory domain
[  316.637734] cfg80211: World regulatory domain updated:
[  316.637737]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  316.637740]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  316.637743]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  316.637745]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  316.637747]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  316.637749]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  316.643930] wlan0: authenticate with 00:1a:30:8d:bc:b0 (try 1)
[  316.645927] wlan0: authenticated
[  316.645957] wlan0: associate with 00:1a:30:8d:bc:b0 (try 1)
[  316.661847] wlan0: RX AssocResp from 00:1a:30:8d:bc:b0 (capab=0x421 status=0 aid=3)
[  316.661851] wlan0: associated
[  316.662554] cfg80211: Calling CRDA for country: SK
[  316.667165] cfg80211: Received country IE:
[  316.667170] cfg80211: Regulatory domain: SK
[  316.667172]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  316.667177]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 2300 mBm)
[  316.667180] cfg80211: CRDA thinks this should applied:
[  316.667182] cfg80211: Regulatory domain: SK
[  316.667184]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  316.667188]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  316.667192]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  316.667195]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  316.667199]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  316.667201] cfg80211: We intersect both of these and get:
[  316.667204] cfg80211: Regulatory domain: 98
[  316.667206]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  316.667210]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  316.667217] cfg80211: Current regulatory domain updated by AP to: SK
[  316.667220]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  316.667224]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  409.986798] lo: Disabled Privacy Extensions
[  436.463669] wlan0: deauthenticating from 00:1a:30:8d:bc:b0 by local choice (reason=3)
[  436.544053] cfg80211: All devices are disconnected, going to restore regulatory settings
[  436.544060] cfg80211: Restoring regulatory settings
[  436.544065] cfg80211: Calling CRDA to update world regulatory domain
[  436.547254] cfg80211: World regulatory domain updated:
[  436.547257]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  436.547259]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  436.547261]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  436.547262]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  436.547264]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  436.547266]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  436.579124] wlan0: authenticate with 00:1a:30:b9:da:70 (try 1)
[  436.583092] wlan0: authenticated
[  436.583123] wlan0: associate with 00:1a:30:b9:da:70 (try 1)
[  436.598468] wlan0: RX AssocResp from 00:1a:30:b9:da:70 (capab=0x421 status=0 aid=30)
[  436.598472] wlan0: associated
[  436.599142] cfg80211: Calling CRDA for country: SK
[  436.603633] cfg80211: Received country IE:
[  436.603638] cfg80211: Regulatory domain: SK
[  436.603641]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  436.603645]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 2300 mBm)
[  436.603648] cfg80211: CRDA thinks this should applied:
[  436.603651] cfg80211: Regulatory domain: SK
[  436.603653]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  436.603656]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  436.603660]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  436.603664]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  436.603667]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  436.603670] cfg80211: We intersect both of these and get:
[  436.603672] cfg80211: Regulatory domain: 98
[  436.603674]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  436.603678]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  436.603686] cfg80211: Current regulatory domain updated by AP to: SK
[  436.603689]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  436.603693]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  853.748992] wlan0: deauthenticating from 00:1a:30:b9:da:70 by local choice (reason=3)
[  853.799669] cfg80211: All devices are disconnected, going to restore regulatory settings
[  853.799678] cfg80211: Restoring regulatory settings
[  853.799684] cfg80211: Calling CRDA to update world regulatory domain
[  853.902987] cfg80211: World regulatory domain updated:
[  853.902991]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  853.902994]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  853.902996]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  853.902998]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  853.903000]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  853.903001]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  855.391735] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  855.391779] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  856.421182] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  856.421265] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  856.421353] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing C246 (len 871, WS 0, PS 0) @ 0xC2A3
[  857.639319] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  857.639397] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CFC0 (len 72, WS 0, PS 0) @ 0xCFEF
[  858.648732] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  858.648816] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  859.858082] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  859.858158] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  861.064931] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  861.065009] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  862.275529] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  862.275607] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  863.483629] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  863.483707] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  864.694229] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  864.694310] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  865.902328] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  865.902405] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  867.112927] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  867.113004] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  868.321023] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  868.321117] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  869.530374] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  869.530451] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  870.740972] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  870.741050] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  871.949072] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  871.949147] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  873.159677] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  873.163046] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  874.367771] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  874.371243] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  875.587162] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  875.590631] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  876.796522] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  876.800075] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  878.007061] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  878.010754] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  879.215162] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  879.218954] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  880.427010] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  880.430815] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  881.633858] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  881.637735] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  882.844457] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  882.848396] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  884.052556] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  884.056381] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  885.264405] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  885.268389] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  886.471254] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  886.475232] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  887.680602] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  887.684614] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  888.889952] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  888.893946] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  890.100550] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  890.104439] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  891.308650] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  891.312639] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  892.519248] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  892.523256] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  893.727348] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  893.731358] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  895.397700] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  895.397708] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  896.605799] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  896.605807] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  897.816397] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  897.816404] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  899.024496] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  899.024504] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  900.235095] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  900.235102] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  901.443194] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  901.443202] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  902.653793] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  902.653800] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  903.861894] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  903.861901] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  905.073741] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  905.073749] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  906.280591] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  906.280598] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  907.491189] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  907.491196] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  908.699288] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  908.699295] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  909.909886] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  909.909894] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  911.117986] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  911.117993] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  912.328585] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  912.328592] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  913.536684] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  913.536691] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  914.747282] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  914.747290] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  915.955383] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  915.955391] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  917.165981] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  917.165989] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  918.375330] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  918.375337] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  919.583429] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  919.583436] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  920.794027] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  920.794034] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  922.002127] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  922.002134] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  923.212725] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  923.212733] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  924.420825] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 1sec aborting
[  924.420832] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing CB9E (len 62, WS 0, PS 0) @ 0xCBBA
[  924.731208] Skipping EDID probe due to cached edid
[  924.847649] Skipping EDID probe due to cached edid
[  927.954123] Skipping EDID probe due to cached edid
[  928.070973] Skipping EDID probe due to cached edid
[  928.204638] Skipping EDID probe due to cached edid
[  928.321100] Skipping EDID probe due to cached edid
[  936.809171] Skipping EDID probe due to cached edid
[  936.942815] Skipping EDID probe due to cached edid
[  937.060314] Skipping EDID probe due to cached edid
[  943.161998] Skipping EDID probe due to cached edid
[  943.718079] wlan0: authenticate with 00:1a:30:b9:da:70 (try 1)
[  943.720035] wlan0: authenticated
[  943.720056] wlan0: associate with 00:1a:30:b9:da:70 (try 1)
[  943.730933] wlan0: RX AssocResp from 00:1a:30:b9:da:70 (capab=0x421 status=0 aid=30)
[  943.730935] wlan0: associated
[  943.731482] cfg80211: Calling CRDA for country: SK
[  943.734207] cfg80211: Received country IE:
[  943.734210] cfg80211: Regulatory domain: SK
[  943.734211]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  943.734213]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (10000 mBi, 2300 mBm)
[  943.734215] cfg80211: CRDA thinks this should applied:
[  943.734216] cfg80211: Regulatory domain: SK
[  943.734216]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  943.734218]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  943.734220]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  943.734221]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  943.734223]     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  943.734224] cfg80211: We intersect both of these and get:
[  943.734225] cfg80211: Regulatory domain: 98
[  943.734226]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  943.734228]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  943.734233] cfg80211: Current regulatory domain updated by AP to: SK
[  943.734234]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  943.734235]     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  943.750074] Skipping EDID probe due to cached edid
```

EDIT: I can't believe no one has had this issue before :(  Please, can anyone help?

---

### Post by vedovatti on 2011-03-27
Hi


I have exactly the same problem. I have a hybrid card  ATI RADEON 545O,seems like a problem with the driver. Ubuntu 10.10, HP touchmart tm2.

Did submit a bug?

---

### Post by vedovatti on 2011-03-27
Hi


I have exactly the same problem. I have a hybrid card  ATI RADEON 545O,seems like a problem with the driver. Ubuntu 10.10, HP touchmart tm2.

Did submit a bug? check this one bug report 647665 in launchpad.net?

---

### Post by rimez on 2011-03-29
Wow. i just realized that I *did not* create a bug (could have sworn I did) :redface:

The mentioned bug does look like the same thing but the message is slightly different. 

[here's the link]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/647665") for those interested.

---

### Post by vedovatti on 2011-03-31
Hi there! again.

I suspect that the bug it could be from the Intel driver. I have a script to change between the ATI and Intel hybrid cards. When I use just the intel it gave me the this bug. But when I use only ATI works ok.

I have to say that both drivers have troubles the Intel have this problem with the atombios etc., and the brigtness isn't well calibrated and sometimes the monitor start without backlit but the ATI has the problem that the brightness cannot be regulated at all, spend double of energy (not really ecologic, and no good for battery).

I hope that it will be solve on the next ubuntu release 11.04. Another solution could be using the PPA Ubuntu X swat upstream. It has the most stable advanced drivers. I haven't tried but if this problem keeps on I will tried next week and let you know. (by the way I don't use the property ATI drivers, in my hybrid card it just destroy the ubuntu installation.

cheers

---

### Post by vedovatti on 2011-03-31
Hi,

I tried the PPA, didn't. So I guess we have to wait until natty.

Cheers

---

### Post by vedovatti on 2011-04-04
Hi there,

I just got the confirmation that the bug has been solved in Ubuntu 11.04

Check [https://bugs.launchpad.net/bugs/647665](https://bugs.launchpad.net/bugs/647665)

Bye

---

### Post by Capirex on 2011-04-06
Hi. I have the acer 4820. I use this script to switch between my cards [http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
I had this problem, but in the comments i found the solution: its because the ATI is powered off.
> I would suggest you to put the shutdown code as a script in runlevels 0 (halt) and 6 (reboot). This is how I did that:

$ sudo "echo ON > /sys/kernel/debug/vgaswitcheroo/switch" > /etc/init.d/hybrid_graphics_on
$ sudo ln /etc/init.d/hybrid_graphics_on /etc/rc0.d/S01hybrid-on
$ sudo ln /etc/init.d/hybrid_graphics_on /etc/rc6.d/S01hybrid-on

This way, you can shutdown / reboot as always and the system will invoke the necessary script to power on both graphic cards. Edit: the comment is by josean1968.
This works for me, but only for reboot and halt, not for restarting X. So i added the commands
```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```to /etc/dgm/PreSession/Defaults and
```
echo ON > /sys/kernel/debug/vgaswitcheroo/switch 
```to /etc/dgm/PostSession/Defaults

Bye

---

### Post by vedovatti on 2011-04-07
Hi there!
I use the same script. It really works!

I will try your solution. In fact, I think it will work because in your example applied to my GPU it will avoid the disadvantages of both GPU.

Anyway, it seems that it has been both drivers have been really improved on the next kernel of Ubuntu 11.04. And at least this bug is corrected.

Another solution it would be to try the ubuntu edgers ppa. The experimental drivers for the video cards. I haven't tried, I am just afraid that I won't see any more my system.

Cheers

---

