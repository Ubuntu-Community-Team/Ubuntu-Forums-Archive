---
title: "USB Mic not recognized. Doesn't show up when i plug it in."
date: 2012-07-05
forum: General Help
---

### Post by Naitogunjin on 2012-07-05
Hello everyone.

I bought a USB Mic adapter cable which allows you to plug your dynamic mic straight into your computer via USB. I got it really cheap online and there isn't really even a name on it.

I've tried it on windows and it works fine. It shows up as being a C-Media USB Headset even though it's a mic. 

When I try and plug it in my lubuntu 12.04 system nothing happens. I've tried dmesg in terminal and it shows up as C-Media USB Headset as well. 

Here is what dmesg brings up:

```
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f3c0a000 soft=f3c0c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2992.349 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.69 BogoMIPS (lpj=11969396)
[    0.004011] pid_max: default: 32768 minimum: 301
[    0.004046] Security Framework initialized
[    0.004069] AppArmor: AppArmor initialized
[    0.004072] Yama: becoming mindful.
[    0.004154] Mount-cache hash table entries: 512
[    0.004362] Initializing cgroup subsys cpuacct
[    0.004372] Initializing cgroup subsys memory
[    0.004384] Initializing cgroup subsys devices
[    0.004387] Initializing cgroup subsys freezer
[    0.004390] Initializing cgroup subsys blkio
[    0.004401] Initializing cgroup subsys perf_event
[    0.004444] CPU: Physical Processor ID: 0
[    0.004447] CPU: Processor Core ID: 0
[    0.004451] mce: CPU supports 4 MCE banks
[    0.004464] CPU0: Thermal monitoring enabled (TM1)
[    0.004470] using mwait in idle threads.
[    0.004769] SMP alternatives: switching to UP code
[    0.019128] ACPI: Core revision 20110623
[    0.050758] ftrace: allocating 25884 entries in 51 pages
[    0.052067] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052439] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.094398] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 0a
[    0.096005] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.096005] ... version:                0
[    0.096005] ... bit width:              40
[    0.096005] ... generic registers:      18
[    0.096005] ... value mask:             000000ffffffffff
[    0.096005] ... max period:             0000007fffffffff
[    0.096005] ... fixed-purpose events:   0
[    0.096005] ... event mask:             000000000003ffff
[    0.096005] NMI watchdog enabled, takes one hw-pmu counter.
[    0.096005] Brought up 1 CPUs
[    0.096005] Total of 1 processors activated (5984.69 BogoMIPS).
[    0.096005] devtmpfs: initialized
[    0.096005] EVM: security.selinux
[    0.096005] EVM: security.SMACK64
[    0.096005] EVM: security.capability
[    0.096005] PM: Registering ACPI NVS region at bf688c00 (8192 bytes)
[    0.096005] print_constraints: dummy: 
[    0.096005] RTC time: 21:11:19, date: 07/05/12
[    0.096005] NET: Registered protocol family 16
[    0.096005] EISA bus registered
[    0.096005] ACPI: bus type pci registered
[    0.096005] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.096005] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.096005] PCI: Using MMCONFIG for extended config space
[    0.096005] PCI: Using configuration type 1 for base access
[    0.097576] bio: create slab <bio-0> at 0
[    0.097712] ACPI: Added _OSI(Module Device)
[    0.097716] ACPI: Added _OSI(Processor Device)
[    0.097719] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.097722] ACPI: Added _OSI(Processor Aggregator Device)
[    0.098337] ACPI: EC: Look up EC in DSDT
[    0.108208] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.117172] ACPI: Interpreter enabled
[    0.117192] ACPI: (supports S0 S1 S3 S4 S5)
[    0.117224] ACPI: Using IOAPIC for interrupt routing
[    0.163259] ACPI: No dock devices found.
[    0.163263] HEST: Table not found.
[    0.163270] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.167116] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.174432] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.174437] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.174441] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.174445] pci_root PNP0A03:00: host bridge window [mem 0xbf700000-0xdfffffff] (ignored)
[    0.174449] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
[    0.174464] pci 0000:00:00.0: [8086:2580] type 0 class 0x000600
[    0.174521] pci 0000:00:02.0: [8086:2582] type 0 class 0x000300
[    0.174535] pci 0000:00:02.0: reg 10: [mem 0xdff80000-0xdfffffff]
[    0.174543] pci 0000:00:02.0: reg 14: [io  0xecd8-0xecdf]
[    0.174551] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
[    0.174559] pci 0000:00:02.0: reg 1c: [mem 0xdff40000-0xdff7ffff]
[    0.174634] pci 0000:00:1b.0: [8086:2668] type 0 class 0x000403
[    0.174653] pci 0000:00:1b.0: reg 10: [mem 0xdff3c000-0xdff3ffff 64bit]
[    0.174731] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.174736] pci 0000:00:1b.0: PME# disabled
[    0.174761] pci 0000:00:1c.0: [8086:2660] type 1 class 0x000604
[    0.174842] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.174847] pci 0000:00:1c.0: PME# disabled
[    0.174873] pci 0000:00:1c.1: [8086:2662] type 1 class 0x000604
[    0.174952] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.174957] pci 0000:00:1c.1: PME# disabled
[    0.174985] pci 0000:00:1d.0: [8086:2658] type 0 class 0x000c03
[    0.175031] pci 0000:00:1d.0: reg 20: [io  0xff80-0xff9f]
[    0.175068] pci 0000:00:1d.1: [8086:2659] type 0 class 0x000c03
[    0.175113] pci 0000:00:1d.1: reg 20: [io  0xff60-0xff7f]
[    0.175149] pci 0000:00:1d.2: [8086:265a] type 0 class 0x000c03
[    0.175194] pci 0000:00:1d.2: reg 20: [io  0xff40-0xff5f]
[    0.175230] pci 0000:00:1d.3: [8086:265b] type 0 class 0x000c03
[    0.175275] pci 0000:00:1d.3: reg 20: [io  0xff20-0xff3f]
[    0.175321] pci 0000:00:1d.7: [8086:265c] type 0 class 0x000c03
[    0.175344] pci 0000:00:1d.7: reg 10: [mem 0xffa80800-0xffa80bff]
[    0.175434] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.175440] pci 0000:00:1d.7: PME# disabled
[    0.175460] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.175529] pci 0000:00:1f.0: [8086:2640] type 0 class 0x000601
[    0.175614] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0c00-0c7f
[    0.175619] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 00e0-00ef
[    0.175638] pci 0000:00:1f.1: [8086:266f] type 0 class 0x000101
[    0.175654] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.175665] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.175676] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.175686] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.175697] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.175738] pci 0000:00:1f.2: [8086:2651] type 0 class 0x000101
[    0.175755] pci 0000:00:1f.2: reg 10: [io  0xfe00-0xfe07]
[    0.175765] pci 0000:00:1f.2: reg 14: [io  0xfe10-0xfe13]
[    0.175775] pci 0000:00:1f.2: reg 18: [io  0xfe20-0xfe27]
[    0.175784] pci 0000:00:1f.2: reg 1c: [io  0xfe30-0xfe33]
[    0.175794] pci 0000:00:1f.2: reg 20: [io  0xfea0-0xfeaf]
[    0.175835] pci 0000:00:1f.2: PME# supported from D3hot
[    0.175840] pci 0000:00:1f.2: PME# disabled
[    0.176025] pci 0000:00:1f.3: [8086:266a] type 0 class 0x000c05
[    0.176082] pci 0000:00:1f.3: reg 20: [io  0xece0-0xecff]
[    0.176167] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.176176] pci 0000:00:1c.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.176226] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.176234] pci 0000:00:1c.1:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.176275] pci 0000:03:01.0: [14f1:2f20] type 0 class 0x000780
[    0.176295] pci 0000:03:01.0: reg 10: [mem 0xdfcf0000-0xdfcfffff]
[    0.176307] pci 0000:03:01.0: reg 14: [io  0xdcb8-0xdcbf]
[    0.176381] pci 0000:03:01.0: PME# supported from D3hot D3cold
[    0.176386] pci 0000:03:01.0: PME# disabled
[    0.176413] pci 0000:03:08.0: [8086:1064] type 0 class 0x000200
[    0.176433] pci 0000:03:08.0: reg 10: [mem 0xdfcef000-0xdfceffff]
[    0.176445] pci 0000:03:08.0: reg 14: [io  0xdcc0-0xdcff]
[    0.176518] pci 0000:03:08.0: supports D1 D2
[    0.176521] pci 0000:03:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.176526] pci 0000:03:08.0: PME# disabled
[    0.176565] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.176571] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.176576] pci 0000:00:1e.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.176583] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.176588] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.176606] pci_bus 0000:00: on NUMA node 0
[    0.176612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.176950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.177279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.177471] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[    0.177687]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.177692]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.177695] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.560968] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.561310] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.561651] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.561985] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.562327] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.562666] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.563005] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.563344] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.563555] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.563565] vgaarb: loaded
[    0.563567] vgaarb: bridge control possible 0000:00:02.0
[    0.563765] i2c-core: driver [aat2870] using legacy suspend method
[    0.563768] i2c-core: driver [aat2870] using legacy resume method
[    0.563897] SCSI subsystem initialized
[    0.563953] libata version 3.00 loaded.
[    0.564070] usbcore: registered new interface driver usbfs
[    0.564089] usbcore: registered new interface driver hub
[    0.564126] usbcore: registered new device driver usb
[    0.564281] PCI: Using ACPI for IRQ routing
[    0.571341] PCI: pci_cache_line_size set to 64 bytes
[    0.571409] reserve RAM buffer: 00000000bf688c00 - 00000000bfffffff 
[    0.571556] NetLabel: Initializing
[    0.571560] NetLabel:  domain hash size = 128
[    0.571562] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.571576] NetLabel:  unlabeled traffic allowed by default
[    0.571645] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.571652] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.571658] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.576091] Switching to clocksource hpet
[    0.584616] AppArmor: AppArmor Filesystem Enabled
[    0.584654] pnp: PnP ACPI init
[    0.584678] ACPI: bus type pnp registered
[    0.588464] pnp 00:00: [bus 00-ff]
[    0.588469] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.588473] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.588476] pnp 00:00: [io  0x0d00-0xffff window]
[    0.588480] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.588483] pnp 00:00: [mem 0x00000000 window]
[    0.588486] pnp 00:00: [mem 0xbf700000-0xdfffffff window]
[    0.588489] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.588543] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.590594] pnp 00:01: [io  0x0060]
[    0.590598] pnp 00:01: [io  0x0064]
[    0.590601] pnp 00:01: [io  0x0062-0x0063]
[    0.590603] pnp 00:01: [io  0x0065-0x006f]
[    0.590606] pnp 00:01: [io  0x00e0-0x00ef]
[    0.590609] pnp 00:01: [io  0x0800-0x085f]
[    0.590612] pnp 00:01: [io  0x0c00-0x0c7f]
[    0.590614] pnp 00:01: [io  0x0860-0x08ff]
[    0.590686] system 00:01: [io  0x0800-0x085f] has been reserved
[    0.590691] system 00:01: [io  0x0c00-0x0c7f] has been reserved
[    0.590694] system 00:01: [io  0x0860-0x08ff] has been reserved
[    0.590700] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.590824] pnp 00:02: [io  0x0080-0x009f]
[    0.590828] pnp 00:02: [io  0x0000-0x001f]
[    0.590830] pnp 00:02: [io  0x00c0-0x00df]
[    0.590834] pnp 00:02: [dma 4]
[    0.590872] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.590972] pnp 00:03: [io  0x00f0-0x00ff]
[    0.590987] pnp 00:03: [irq 13]
[    0.591028] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.591126] pnp 00:04: [io  0x0061]
[    0.591167] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.591266] pnp 00:05: [io  0x0070-0x007f]
[    0.591273] pnp 00:05: [irq 8]
[    0.591313] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.598930] pnp 00:06: [io  0x0378-0x037f]
[    0.598934] pnp 00:06: [io  0x0778-0x077f]
[    0.598942] pnp 00:06: [irq 7]
[    0.598945] pnp 00:06: [dma 0 disabled]
[    0.599479] pnp 00:06: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.601924] pnp 00:07: [io  0x03f8-0x03ff]
[    0.601932] pnp 00:07: [irq 4]
[    0.602139] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.612518] pnp 00:08: [mem 0x00000000-0x0009ffff]
[    0.612522] pnp 00:08: [mem 0x00100000-0x00ffffff]
[    0.612525] pnp 00:08: [mem 0x01000000-0xbf688bff]
[    0.612528] pnp 00:08: [mem 0x000c0000-0x000fffff]
[    0.612531] pnp 00:08: [mem 0xfec00000-0xfecfffff]
[    0.612534] pnp 00:08: [mem 0xfee00000-0xfeefffff]
[    0.612537] pnp 00:08: [mem 0xfed20000-0xfed9ffff]
[    0.612540] pnp 00:08: [mem 0xffb00000-0xffbfffff]
[    0.612543] pnp 00:08: [mem 0xffc00000-0xffffffff]
[    0.612607] system 00:08: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.612613] system 00:08: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.612616] system 00:08: [mem 0x01000000-0xbf688bff] could not be reserved
[    0.612620] system 00:08: [mem 0x000c0000-0x000fffff] could not be reserved
[    0.612624] system 00:08: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.612628] system 00:08: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.612631] system 00:08: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.612635] system 00:08: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.612639] system 00:08: [mem 0xffc00000-0xffffffff] has been reserved
[    0.612644] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.613771] pnp 00:09: [mem 0xe0000000-0xefffffff]
[    0.613775] pnp 00:09: [mem 0xfeda0000-0xfedacfff]
[    0.613778] pnp 00:09: [io  0x0100-0x01fe]
[    0.613780] pnp 00:09: [io  0x0200-0x0277]
[    0.613783] pnp 00:09: [io  0x0280-0x02e7]
[    0.613786] pnp 00:09: [io  0x02e8-0x02ef]
[    0.613789] pnp 00:09: [io  0x02f0-0x02f7]
[    0.613791] pnp 00:09: [io  0x02f8-0x02ff]
[    0.613794] pnp 00:09: [io  0x0300-0x0377]
[    0.613797] pnp 00:09: [io  0x0380-0x03bb]
[    0.613799] pnp 00:09: [io  0x03c0-0x03e7]
[    0.613802] pnp 00:09: [io  0x03f6-0x03f7]
[    0.613805] pnp 00:09: [io  0x0400-0x04cf]
[    0.613808] pnp 00:09: [io  0x04d2-0x057f]
[    0.613810] pnp 00:09: [io  0x0580-0x0677]
[    0.613813] pnp 00:09: [io  0x0680-0x0777]
[    0.613816] pnp 00:09: [io  0x0780-0x07bb]
[    0.613818] pnp 00:09: [io  0x07c0-0x07ff]
[    0.613821] pnp 00:09: [io  0x08e0-0x08ff]
[    0.613824] pnp 00:09: [io  0x0900-0x09fe]
[    0.613827] pnp 00:09: [io  0x0a00-0x0afe]
[    0.613829] pnp 00:09: [io  0x0b00-0x0bfe]
[    0.613832] pnp 00:09: [io  0x0c80-0x0caf]
[    0.613835] pnp 00:09: [io  0x0cb0-0x0cbf]
[    0.613837] pnp 00:09: [io  0x0cc0-0x0cf7]
[    0.613844] pnp 00:09: [io  0x0d00-0x0dfe]
[    0.613847] pnp 00:09: [io  0x0e00-0x0efe]
[    0.613850] pnp 00:09: [io  0x0f00-0x0ffe]
[    0.613853] pnp 00:09: [io  0x2000-0x20fe]
[    0.613855] pnp 00:09: [io  0x2100-0x21fe]
[    0.613858] pnp 00:09: [io  0x2200-0x22fe]
[    0.613861] pnp 00:09: [io  0x2300-0x23fe]
[    0.613863] pnp 00:09: [io  0x2400-0x24fe]
[    0.613866] pnp 00:09: [io  0x2500-0x25fe]
[    0.613869] pnp 00:09: [io  0x2600-0x26fe]
[    0.613871] pnp 00:09: [io  0x2700-0x27fe]
[    0.613874] pnp 00:09: [io  0x2800-0x28fe]
[    0.613877] pnp 00:09: [io  0x2900-0x29fe]
[    0.613880] pnp 00:09: [io  0x2a00-0x2afe]
[    0.613882] pnp 00:09: [io  0x2b00-0x2bfe]
[    0.613885] pnp 00:09: [io  0x2c00-0x2cfe]
[    0.613888] pnp 00:09: [io  0x2d00-0x2dfe]
[    0.613890] pnp 00:09: [io  0x2e00-0x2efe]
[    0.613893] pnp 00:09: [io  0x2f00-0x2ffe]
[    0.613896] pnp 00:09: [io  0x5000-0x50fe]
[    0.613898] pnp 00:09: [io  0x5100-0x51fe]
[    0.613901] pnp 00:09: [io  0x5200-0x52fe]
[    0.613904] pnp 00:09: [io  0x5300-0x53fe]
[    0.613906] pnp 00:09: [io  0x5400-0x54fe]
[    0.613909] pnp 00:09: [io  0x5500-0x55fe]
[    0.613912] pnp 00:09: [io  0x5600-0x56fe]
[    0.613914] pnp 00:09: [io  0x5700-0x57fe]
[    0.613917] pnp 00:09: [io  0x5800-0x58fe]
[    0.613920] pnp 00:09: [io  0x5900-0x59fe]
[    0.613923] pnp 00:09: [io  0x5a00-0x5afe]
[    0.613925] pnp 00:09: [io  0x5b00-0x5bfe]
[    0.613928] pnp 00:09: [io  0x5c00-0x5cfe]
[    0.613931] pnp 00:09: [io  0x5d00-0x5dfe]
[    0.613933] pnp 00:09: [io  0x5e00-0x5efe]
[    0.613936] pnp 00:09: [io  0x5f00-0x5ffe]
[    0.613939] pnp 00:09: [io  0x6000-0x60fe]
[    0.613941] pnp 00:09: [io  0x6100-0x61fe]
[    0.613944] pnp 00:09: [io  0x6200-0x62fe]
[    0.613947] pnp 00:09: [io  0x6300-0x63fe]
[    0.613949] pnp 00:09: [io  0x6400-0x64fe]
[    0.613952] pnp 00:09: [io  0x6500-0x65fe]
[    0.613955] pnp 00:09: [io  0x6600-0x66fe]
[    0.613957] pnp 00:09: [io  0x6700-0x67fe]
[    0.613960] pnp 00:09: [io  0x6800-0x68fe]
[    0.613963] pnp 00:09: [io  0x6900-0x69fe]
[    0.613965] pnp 00:09: [io  0x6a00-0x6afe]
[    0.613968] pnp 00:09: [io  0x6b00-0x6bfe]
[    0.613971] pnp 00:09: [io  0x6c00-0x6cfe]
[    0.613973] pnp 00:09: [io  0x6d00-0x6dfe]
[    0.613976] pnp 00:09: [io  0x6e00-0x6efe]
[    0.613979] pnp 00:09: [io  0x6f00-0x6ffe]
[    0.613981] pnp 00:09: [io  0xa000-0xa0fe]
[    0.613984] pnp 00:09: [io  0xa100-0xa1fe]
[    0.613987] pnp 00:09: [io  0xa200-0xa2fe]
[    0.613990] pnp 00:09: [io  0xa300-0xa3fe]
[    0.613992] pnp 00:09: [io  0xa400-0xa4fe]
[    0.613995] pnp 00:09: [io  0xa500-0xa5fe]
[    0.613998] pnp 00:09: [io  0xa600-0xa6fe]
[    0.614000] pnp 00:09: [io  0xa700-0xa7fe]
[    0.614003] pnp 00:09: [io  0xa800-0xa8fe]
[    0.614006] pnp 00:09: [io  0xa900-0xa9fe]
[    0.614008] pnp 00:09: [io  0xaa00-0xaafe]
[    0.614011] pnp 00:09: [io  0xab00-0xabfe]
[    0.614014] pnp 00:09: [io  0xac00-0xacfe]
[    0.614018] pnp 00:09: [io  0xad00-0xadfe]
[    0.614021] pnp 00:09: [io  0xae00-0xaefe]
[    0.614024] pnp 00:09: [io  0xaf00-0xaffe]
[    0.614266] system 00:09: [io  0x0100-0x01fe] could not be reserved
[    0.614270] system 00:09: [io  0x0200-0x0277] has been reserved
[    0.614274] system 00:09: [io  0x0280-0x02e7] has been reserved
[    0.614277] system 00:09: [io  0x02e8-0x02ef] has been reserved
[    0.614281] system 00:09: [io  0x02f0-0x02f7] has been reserved
[    0.614285] system 00:09: [io  0x02f8-0x02ff] has been reserved
[    0.614288] system 00:09: [io  0x0300-0x0377] could not be reserved
[    0.614292] system 00:09: [io  0x0380-0x03bb] has been reserved
[    0.614295] system 00:09: [io  0x03c0-0x03e7] has been reserved
[    0.614299] system 00:09: [io  0x03f6-0x03f7] could not be reserved
[    0.614303] system 00:09: [io  0x0400-0x04cf] has been reserved
[    0.614306] system 00:09: [io  0x04d2-0x057f] has been reserved
[    0.614310] system 00:09: [io  0x0580-0x0677] has been reserved
[    0.614313] system 00:09: [io  0x0680-0x0777] has been reserved
[    0.614317] system 00:09: [io  0x0780-0x07bb] has been reserved
[    0.614324] system 00:09: [io  0x07c0-0x07ff] has been reserved
[    0.614328] system 00:09: [io  0x08e0-0x08ff] has been reserved
[    0.614331] system 00:09: [io  0x0900-0x09fe] has been reserved
[    0.614335] system 00:09: [io  0x0a00-0x0afe] has been reserved
[    0.614338] system 00:09: [io  0x0b00-0x0bfe] has been reserved
[    0.614342] system 00:09: [io  0x0c80-0x0caf] has been reserved
[    0.614345] system 00:09: [io  0x0cb0-0x0cbf] has been reserved
[    0.614349] system 00:09: [io  0x0cc0-0x0cf7] has been reserved
[    0.614353] system 00:09: [io  0x0d00-0x0dfe] has been reserved
[    0.614356] system 00:09: [io  0x0e00-0x0efe] has been reserved
[    0.614360] system 00:09: [io  0x0f00-0x0ffe] has been reserved
[    0.614364] system 00:09: [io  0x2000-0x20fe] has been reserved
[    0.614367] system 00:09: [io  0x2100-0x21fe] has been reserved
[    0.614371] system 00:09: [io  0x2200-0x22fe] has been reserved
[    0.614375] system 00:09: [io  0x2300-0x23fe] has been reserved
[    0.614378] system 00:09: [io  0x2400-0x24fe] has been reserved
[    0.614382] system 00:09: [io  0x2500-0x25fe] has been reserved
[    0.614386] system 00:09: [io  0x2600-0x26fe] has been reserved
[    0.614389] system 00:09: [io  0x2700-0x27fe] has been reserved
[    0.614393] system 00:09: [io  0x2800-0x28fe] has been reserved
[    0.614397] system 00:09: [io  0x2900-0x29fe] has been reserved
[    0.614400] system 00:09: [io  0x2a00-0x2afe] has been reserved
[    0.614404] system 00:09: [io  0x2b00-0x2bfe] has been reserved
[    0.614408] system 00:09: [io  0x2c00-0x2cfe] has been reserved
[    0.614411] system 00:09: [io  0x2d00-0x2dfe] has been reserved
[    0.614415] system 00:09: [io  0x2e00-0x2efe] has been reserved
[    0.614419] system 00:09: [io  0x2f00-0x2ffe] has been reserved
[    0.614422] system 00:09: [io  0x5000-0x50fe] has been reserved
[    0.614426] system 00:09: [io  0x5100-0x51fe] has been reserved
[    0.614430] system 00:09: [io  0x5200-0x52fe] has been reserved
[    0.614434] system 00:09: [io  0x5300-0x53fe] has been reserved
[    0.614437] system 00:09: [io  0x5400-0x54fe] has been reserved
[    0.614441] system 00:09: [io  0x5500-0x55fe] has been reserved
[    0.614445] system 00:09: [io  0x5600-0x56fe] has been reserved
[    0.614449] system 00:09: [io  0x5700-0x57fe] has been reserved
[    0.614452] system 00:09: [io  0x5800-0x58fe] has been reserved
[    0.614456] system 00:09: [io  0x5900-0x59fe] has been reserved
[    0.614460] system 00:09: [io  0x5a00-0x5afe] has been reserved
[    0.614464] system 00:09: [io  0x5b00-0x5bfe] has been reserved
[    0.614467] system 00:09: [io  0x5c00-0x5cfe] has been reserved
[    0.614471] system 00:09: [io  0x5d00-0x5dfe] has been reserved
[    0.614475] system 00:09: [io  0x5e00-0x5efe] has been reserved
[    0.614479] system 00:09: [io  0x5f00-0x5ffe] has been reserved
[    0.614482] system 00:09: [io  0x6000-0x60fe] has been reserved
[    0.614486] system 00:09: [io  0x6100-0x61fe] has been reserved
[    0.614492] system 00:09: [io  0x6200-0x62fe] has been reserved
[    0.614496] system 00:09: [io  0x6300-0x63fe] has been reserved
[    0.614500] system 00:09: [io  0x6400-0x64fe] has been reserved
[    0.614504] system 00:09: [io  0x6500-0x65fe] has been reserved
[    0.614508] system 00:09: [io  0x6600-0x66fe] has been reserved
[    0.614512] system 00:09: [io  0x6700-0x67fe] has been reserved
[    0.614515] system 00:09: [io  0x6800-0x68fe] has been reserved
[    0.614519] system 00:09: [io  0x6900-0x69fe] has been reserved
[    0.614523] system 00:09: [io  0x6a00-0x6afe] has been reserved
[    0.614527] system 00:09: [io  0x6b00-0x6bfe] has been reserved
[    0.614531] system 00:09: [io  0x6c00-0x6cfe] has been reserved
[    0.614535] system 00:09: [io  0x6d00-0x6dfe] has been reserved
[    0.614538] system 00:09: [io  0x6e00-0x6efe] has been reserved
[    0.614542] system 00:09: [io  0x6f00-0x6ffe] has been reserved
[    0.614546] system 00:09: [io  0xa000-0xa0fe] has been reserved
[    0.614550] system 00:09: [io  0xa100-0xa1fe] has been reserved
[    0.614554] system 00:09: [io  0xa200-0xa2fe] has been reserved
[    0.614558] system 00:09: [io  0xa300-0xa3fe] has been reserved
[    0.614562] system 00:09: [io  0xa400-0xa4fe] has been reserved
[    0.614566] system 00:09: [io  0xa500-0xa5fe] has been reserved
[    0.614570] system 00:09: [io  0xa600-0xa6fe] has been reserved
[    0.614574] system 00:09: [io  0xa700-0xa7fe] has been reserved
[    0.614578] system 00:09: [io  0xa800-0xa8fe] has been reserved
[    0.614582] system 00:09: [io  0xa900-0xa9fe] has been reserved
[    0.614586] system 00:09: [io  0xaa00-0xaafe] has been reserved
[    0.614590] system 00:09: [io  0xab00-0xabfe] has been reserved
[    0.614594] system 00:09: [io  0xac00-0xacfe] has been reserved
[    0.614598] system 00:09: [io  0xad00-0xadfe] has been reserved
[    0.614602] system 00:09: [io  0xae00-0xaefe] has been reserved
[    0.614606] system 00:09: [io  0xaf00-0xaffe] has been reserved
[    0.614611] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.614614] system 00:09: [mem 0xfeda0000-0xfedacfff] has been reserved
[    0.614620] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.614629] pnp: PnP ACPI: found 10 devices
[    0.614632] ACPI: ACPI bus type pnp unregistered
[    0.614637] PnPBIOS: Disabled by ACPI PNP
[    0.652337] PCI: max bus depth: 1 pci_try_num: 2
[    0.652373] pci 0000:00:1c.0: BAR 15: assigned [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.652379] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.652383] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.652387] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.652393] pci 0000:00:1c.0:   bridge window [mem 0xdfe00000-0xdfefffff]
[    0.652399] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.652406] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.652412] pci 0000:00:1c.1:   bridge window [mem 0xdfd00000-0xdfdfffff]
[    0.652422] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.652426] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.652432] pci 0000:00:1e.0:   bridge window [mem 0xdfc00000-0xdfcfffff]
[    0.652458] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.652465] pci 0000:00:1c.0: setting latency timer to 64
[    0.652479] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.652484] pci 0000:00:1c.1: setting latency timer to 64
[    0.652492] pci 0000:00:1e.0: setting latency timer to 64
[    0.652498] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.652501] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.652504] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.652507] pci_bus 0000:01: resource 1 [mem 0xdfe00000-0xdfefffff]
[    0.652511] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.652514] pci_bus 0000:02: resource 1 [mem 0xdfd00000-0xdfdfffff]
[    0.652518] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.652521] pci_bus 0000:03: resource 1 [mem 0xdfc00000-0xdfcfffff]
[    0.652524] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.652527] pci_bus 0000:03: resource 5 [mem 0x00000000-0xffffffff]
[    0.652574] NET: Registered protocol family 2
[    0.652675] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.652964] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.653457] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.653706] TCP: Hash tables configured (established 131072 bind 65536)
[    0.653709] TCP reno registered
[    0.653712] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.653722] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.653827] NET: Registered protocol family 1
[    0.653847] pci 0000:00:02.0: Boot video device
[    0.653876] pci 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.653896] pci 0000:00:1d.0: PCI INT A disabled
[    0.653911] pci 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.653929] pci 0000:00:1d.1: PCI INT B disabled
[    0.653944] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.653962] pci 0000:00:1d.2: PCI INT C disabled
[    0.653977] pci 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.653995] pci 0000:00:1d.3: PCI INT D disabled
[    0.654005] pci 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.654033] pci 0000:00:1d.7: PCI INT A disabled
[    0.654065] pci 0000:03:08.0: Firmware left e100 interrupts enabled; disabling
[    0.654073] PCI: CLS 64 bytes, default 64
[    0.654133] Simple Boot Flag at 0x7a set to 0x1
[    0.654527] audit: initializing netlink socket (disabled)
[    0.654539] type=2000 audit(1341522679.648:1): initialized
[    0.680768] Trying to unpack rootfs image as initramfs...
[    0.724189] highmem bounce pool size: 64 pages
[    0.724197] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.748459] VFS: Disk quotas dquot_6.5.2
[    0.748550] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.749393] fuse init (API version 7.17)
[    0.749538] msgmni has been set to 1654
[    0.764344] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.764388] io scheduler noop registered
[    0.764391] io scheduler deadline registered
[    0.764403] io scheduler cfq registered (default)
[    0.764571] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.764623] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.764707] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.764752] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.764860] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.764900] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.765117] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.765126] ACPI: Power Button [VBTN]
[    0.765204] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.765209] ACPI: Power Button [PWRF]
[    0.833030] ERST: Table is not found!
[    0.833034] GHES: HEST is not enabled!
[    0.836448] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.856872] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.856910] isapnp: Scanning for PnP cards...
[    0.949326] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.968453] Linux agpgart interface v0.103
[    0.968532] agpgart-intel 0000:00:00.0: Intel 915G Chipset
[    0.968644] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.969053] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.972286] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.974540] brd: module loaded
[    0.980788] loop: module loaded
[    0.981013] ata_piix 0000:00:1f.1: version 2.13
[    0.981030] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.981078] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.025004] scsi0 : ata_piix
[    1.025114] scsi1 : ata_piix
[    1.025183] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.025187] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.025240] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    1.025247] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.028375] ata2: port disabled--ignoring
[    1.195680] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.204377] ata1.00: ATAPI: SONY    DVD RW DW-U18A, UYS1, max UDMA/33
[    1.212544] scsi2 : ata_piix
[    1.216025] scsi3 : ata_piix
[    1.216102] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    1.216107] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    1.216753] Fixed MDIO Bus: probed
[    1.216793] tun: Universal TUN/TAP device driver, 1.6
[    1.216796] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.216893] PPP generic driver version 2.4.2
[    1.217039] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.217064] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.217088] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.217093] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.217155] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.217191] ehci_hcd 0000:00:1d.7: debug port 1
[    1.221088] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.221268] ata1.00: configured for UDMA/33
[    1.221473] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[    1.236053] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.236272] hub 1-0:1.0: USB hub found
[    1.236280] hub 1-0:1.0: 8 ports detected
[    1.236398] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.236421] uhci_hcd: USB Universal Host Controller Interface driver
[    1.236455] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.236470] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.236475] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.236544] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.236573] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    1.236754] hub 2-0:1.0: USB hub found
[    1.236761] hub 2-0:1.0: 2 ports detected
[    1.236848] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.236858] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.236862] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.236924] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.236963] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    1.237139] hub 3-0:1.0: USB hub found
[    1.237146] hub 3-0:1.0: 2 ports detected
[    1.237233] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.237243] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.237247] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.237308] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.237344] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    1.237523] hub 4-0:1.0: USB hub found
[    1.237529] hub 4-0:1.0: 2 ports detected
[    1.237624] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.237634] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.237638] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.237699] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.237735] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    1.237918] hub 5-0:1.0: USB hub found
[    1.237925] hub 5-0:1.0: 2 ports detected
[    1.238087] usbcore: registered new interface driver libusual
[    1.238155] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.284314] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.284324] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.288293] mousedev: PS/2 mouse device common for all mice
[    1.288504] rtc_cmos 00:05: RTC can wake from S4
[    1.288629] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.288658] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    1.288762] device-mapper: uevent: version 1.0.3
[    1.288870] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.288919] EISA: Probing bus 0 at eisa.0
[    1.288923] EISA: Cannot allocate resource for mainboard
[    1.288926] Cannot allocate resource for EISA slot 1
[    1.288929] Cannot allocate resource for EISA slot 2
[    1.288939] Cannot allocate resource for EISA slot 5
[    1.288941] Cannot allocate resource for EISA slot 6
[    1.288951] EISA: Detected 0 cards.
[    1.288962] cpufreq-nforce2: No nForce2 chipset.
[    1.288967] cpuidle: using governor ladder
[    1.288969] cpuidle: using governor menu
[    1.288971] EFI Variables Facility v0.08 2004-May-17
[    1.289285] TCP cubic registered
[    1.289466] NET: Registered protocol family 10
[    1.290192] NET: Registered protocol family 17
[    1.290199] Registering the dns_resolver key type
[    1.290225] Using IPI No-Shortcut mode
[    1.290360] PM: Hibernation image not present or could not be loaded.
[    1.290377] registered taskstats version 1
[    1.425035] ata3.00: ATA-6: WDC WD1600JD-00HBB0, 08.02D08, max UDMA/133
[    1.425041] ata3.00: 312581808 sectors, multi 8: LBA48 
[    1.471821] isapnp: No Plug & Play device found
[    1.512703] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DW-U18A   UYS1 PQ: 0 ANSI: 5
[    1.513846] ata3.00: configured for UDMA/133
[    1.515472] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.515477] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.515656] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.515839] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.516053] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600JD-00H 08.0 PQ: 0 ANSI: 5
[    1.516305] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.516415] sd 2:0:0:0: [sda] Write Protect is off
[    1.516420] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.516456] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.516855] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.561635]  sda: sda1 sda2 < sda5 >
[    1.562148] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.566404] Freeing initrd memory: 13796k freed
[    1.582393]   Magic number: 4:226:196
[    1.582496] rtc_cmos 00:05: setting system clock to 2012-07-05 21:11:21 UTC (1341522681)
[    1.582522] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.582525] EDD information not available.
[    1.652023] Refined TSC clocksource calibration: 2992.499 MHz.
[    1.652031] Switching to clocksource tsc
[    1.728026] usb 1-5: new high-speed USB device number 4 using ehci_hcd
[    2.212017] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    2.632041] usb 2-2: new low-speed USB device number 3 using uhci_hcd
[    3.056018] usb 4-2: new full-speed USB device number 2 using uhci_hcd
[    5.412099] Freeing unused kernel memory: 712k freed
[    5.412474] Write protecting the kernel text: 5616k
[    5.412513] Write protecting the kernel read-only data: 2324k
[    5.437896] udevd[88]: starting version 175
[    5.638525] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input2
[    5.638704] generic-usb 0003:045E:0040.0003: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2/input0
[    5.642467] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.3/input/input3
[    5.642591] generic-usb 0003:0D8C:000C.0004: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.2-2/input3
[    5.642617] usbcore: registered new interface driver usbhid
[    5.642620] usbhid: USB HID core driver
[    5.657817] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    5.657822] e100: Copyright(c) 1999-2006 Intel Corporation
[    5.657875] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.688830] e100 0000:03:08.0: PME# disabled
[    5.691870] e100 0000:03:08.0: eth0: addr 0xdfcef000, irq 20, MAC addr 00:16:76:63:cf:55
[    5.785615] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[    5.786219] logitech 0003:046D:C517.0001: input,hidraw2: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
[    5.815628] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    5.818299] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input5
[    5.820082] logitech 0003:046D:C517.0002: input,hiddev0,hidraw3: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
[    5.891440] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    5.891446] EXT4-fs (sda1): write access will be enabled during recovery
[    7.975379] EXT4-fs (sda1): orphan cleanup on readonly fs
[    7.975392] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6163309
[    7.975500] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6820994
[    7.975525] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6820985
[    7.975546] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817293
[    7.975568] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817215
[    7.975589] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817190
[    7.975609] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817180
[    7.975629] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817172
[    7.975649] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817110
[    7.975670] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817109
[    7.975689] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817108
[    7.975709] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817049
[    7.975730] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6817041
[    7.975750] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6816812
[    7.975771] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6816611
[    7.975791] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6816591
[    7.975813] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2623824
[    7.986144] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6816142
[    7.986312] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6816584
[    7.986333] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6161111
[    7.986354] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 6163297
[    7.986417] EXT4-fs (sda1): 21 orphan inodes deleted
[    7.986421] EXT4-fs (sda1): recovery complete
[    8.383421] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   16.932710] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.968889] udevd[298]: starting version 175
[   17.041583] Adding 3133436k swap on /dev/sda5.  Priority:-1 extents:1 across:3133436k 
[   17.052696] lp: driver loaded but no devices found
[   17.214284] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.532498] ppdev: user-space parallel port driver
[   17.558936] parport_pc 00:06: reported by Plug and Play ACPI
[   17.558994] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   17.560990] Bluetooth: Core ver 2.16
[   17.561015] NET: Registered protocol family 31
[   17.561018] Bluetooth: HCI device and connection manager initialized
[   17.561022] Bluetooth: HCI socket layer initialized
[   17.561024] Bluetooth: L2CAP socket layer initialized
[   17.561033] Bluetooth: SCO socket layer initialized
[   17.583045] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.583051] Bluetooth: BNEP filters: protocol multicast
[   17.585400] [drm] Initialized drm 1.1.0 20060810
[   17.651383] intel_rng: Firmware space is locked read-only. If you can't or
[   17.651385] intel_rng: don't want to disable this in firmware setup, and if
[   17.651387] intel_rng: you are certain that your system has a functional
[   17.651389] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   17.656416] lp0: using parport0 (interrupt-driven).
[   17.756846] type=1400 audit(1341522697.672:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=554 comm="apparmor_parser"
[   17.757520] type=1400 audit(1341522697.672:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=554 comm="apparmor_parser"
[   17.859081] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.859090] i915 0000:00:02.0: setting latency timer to 64
[   17.911351] type=1400 audit(1341522697.824:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=598 comm="apparmor_parser"
[   17.915622] type=1400 audit(1341522697.828:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=598 comm="apparmor_parser"
[   17.915930] type=1400 audit(1341522697.828:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=598 comm="apparmor_parser"
[   17.928252] type=1400 audit(1341522697.844:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=599 comm="apparmor_parser"
[   18.117612] usbcore: registered new interface driver cdc_ether
[   18.174729] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.174734] [drm] Driver supports precise vblank timestamp query.
[   18.174798] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   18.281636] usbcore: registered new interface driver rndis_host
[   18.298049] cfg80211: Calling CRDA to update world regulatory domain
[   18.314900] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.402072] usbcore: registered new interface driver snd-usb-audio
[   18.465681] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.465686] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465689] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.465692] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465695] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.465698] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465700] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.465703] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465706] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.465709] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465712] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.465715] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465717] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.465720] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465723] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.465726] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465729] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.465732] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465734] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.465738] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465740] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.465743] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   18.465746] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.465749] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   18.465751] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.465755] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   18.465757] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   18.465760] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   18.516554] rndis_wlan 1-5:1.0: wlan0: register 'rndis_wlan' at usb-0000:00:1d.7-5, Wireless RNDIS device, BCM4320a based, 00:0f:66:ec:3c:57
[   18.521504] usbcore: registered new interface driver rndis_wlan
[   18.524373] init: failsafe main process (693) killed by TERM signal
[   18.755454] type=1400 audit(1341522698.668:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=791 comm="apparmor_parser"
[   18.788377] type=1400 audit(1341522698.704:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=792 comm="apparmor_parser"
[   18.790259] type=1400 audit(1341522698.704:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=792 comm="apparmor_parser"
[   18.790570] type=1400 audit(1341522698.704:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=792 comm="apparmor_parser"
[   18.814819] [drm] initialized overlay support
[   19.020539] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.020983] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.053964] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.055359] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.183740] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   19.183746] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183750] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   19.183753] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183756] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   19.183760] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183763] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   19.183767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183770] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   19.183773] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183776] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   19.183780] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183783] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   19.183787] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183790] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   19.183793] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183796] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   19.183800] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183803] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   19.183806] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183809] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   19.183813] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183816] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   19.183819] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.183822] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   19.183826] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.183829] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   19.183833] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.183837] cfg80211: World regulatory domain updated:
[   19.183839] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.183843] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183846] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.183850] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.183853] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.183856] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.292723] init: alsa-restore main process (849) terminated with status 99
[   19.391023] fbcon: inteldrmfb (fb0) is primary device
[   19.392321] Console: switching to colour frame buffer device 160x64
[   19.392362] fb0: inteldrmfb frame buffer device
[   19.392364] drm: registered panic notifier
[   19.392413] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.392461] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.392529] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   19.392562] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   19.573702] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   19.574154] vboxdrv: Found 1 processor cores.
[   19.575253] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.575258] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   19.580672] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.580987] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.584296] input: HDA Intel Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   19.680906] vboxpci: IOMMU not found (not registered)
[   20.500132] init: plymouth-stop pre-start process (1031) terminated with status 1
[   22.816545] rndis_wlan 1-5:1.0: wlan0: media connect
[   22.936489] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.888011] wlan0: no IPv6 routers present
[  130.957414] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  649.756043] usb 4-2: reset full-speed USB device number 2 using uhci_hcd
[  649.908564] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.3/input/input10
[  649.911995] generic-usb 0003:0D8C:000C.0005: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.2-2/input3
[ 2369.808085] usb 4-2: reset full-speed USB device number 2 using uhci_hcd
[ 2369.959997] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.3/input/input11
[ 2369.960420] generic-usb 0003:0D8C:000C.0006: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.2-2/input3
[ 3158.068048] usb 4-2: reset full-speed USB device number 2 using uhci_hcd
[ 3158.219966] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.3/input/input12
[ 3158.220296] generic-usb 0003:0D8C:000C.0007: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.2-2/input3
[ 4303.464067] usb 4-2: USB disconnect, device number 2
[ 4333.504023] usb 4-2: new full-speed USB device number 3 using uhci_hcd
[ 4333.733168] input: C-Media USB Headphone Set   as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.3/input/input13
[ 4333.733300] generic-usb 0003:0D8C:000C.0008: input,hidraw1: USB HID v1.00 Device [C-Media USB Headphone Set  ] on usb-0000:00:1d.2-2/input3
```


If anyone knows how to get this working then please let me know. Thanks

---

### Post by Naitogunjin on 2012-07-05
Sorry for so much code.

It starts talking about C-Media at the end of the code.

;)

---

