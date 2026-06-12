---
title: "What is causing my freezes on 10.10?"
date: 2010-11-11
forum: General Help
---

### Post by waloshin on 2010-11-11
```
Nov 11 14:24:10 ubuntu kernel: [    0.164555] CPU0: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
Nov 11 14:24:10 ubuntu kernel: [    0.170000] Booting processor 1 APIC 0x2 ip 0x6000
Nov 11 14:24:10 ubuntu kernel: [    0.020000] Initializing CPU#1
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 24K
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: L2 cache: 512K
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU 1/0x2 -> Node 0
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: Physical Processor ID: 0
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: Processor Core ID: 1
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU1: Thermal monitoring enabled (TM2)
Nov 11 14:24:10 ubuntu kernel: [    0.320139] CPU1: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
Nov 11 14:24:10 ubuntu kernel: [    0.320156] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 11 14:24:10 ubuntu kernel: [    0.330230] Booting processor 2 APIC 0x1 ip 0x6000
Nov 11 14:24:10 ubuntu kernel: [    0.020000] Initializing CPU#2
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 24K
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: L2 cache: 512K
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU 2/0x1 -> Node 0
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: Physical Processor ID: 0
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: Processor Core ID: 0
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU2: Thermal monitoring enabled (TM2)
Nov 11 14:24:10 ubuntu kernel: [    0.490105] CPU2: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
Nov 11 14:24:10 ubuntu kernel: [    0.490122] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Nov 11 14:24:10 ubuntu kernel: [    0.500282] Booting processor 3 APIC 0x3 ip 0x6000
Nov 11 14:24:10 ubuntu kernel: [    0.020000] Initializing CPU#3
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 24K
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: L2 cache: 512K
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU 3/0x3 -> Node 0
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: Physical Processor ID: 0
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU: Processor Core ID: 1
Nov 11 14:24:10 ubuntu kernel: [    0.020000] CPU3: Thermal monitoring enabled (TM2)
Nov 11 14:24:10 ubuntu kernel: [    0.660106] CPU3: Intel(R) Atom(TM) CPU  330   @ 1.60GHz stepping 02
Nov 11 14:24:10 ubuntu kernel: [    0.660122] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Nov 11 14:24:10 ubuntu kernel: [    0.670032] Brought up 4 CPUs
Nov 11 14:24:10 ubuntu kernel: [    0.670040] Total of 4 processors activated (12767.89 BogoMIPS).
Nov 11 14:24:10 ubuntu kernel: [    0.671686] CPU0 attaching sched-domain:
Nov 11 14:24:10 ubuntu kernel: [    0.671696]  domain 0: span 0,2 level SIBLING
Nov 11 14:24:10 ubuntu kernel: [    0.671702]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
Nov 11 14:24:10 ubuntu kernel: [    0.671715]   domain 1: span 0,2 level MC
Nov 11 14:24:10 ubuntu kernel: [    0.671721]    groups: 0,2 (cpu_power = 1178)
Nov 11 14:24:10 ubuntu kernel: [    0.671730]    domain 2: span 0-3 level CPU
Nov 11 14:24:10 ubuntu kernel: [    0.671736]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
Nov 11 14:24:10 ubuntu kernel: [    0.671754] CPU1 attaching sched-domain:
Nov 11 14:24:10 ubuntu kernel: [    0.671759]  domain 0: span 1,3 level SIBLING
Nov 11 14:24:10 ubuntu kernel: [    0.671765]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
Nov 11 14:24:10 ubuntu kernel: [    0.671777]   domain 1: span 1,3 level MC
Nov 11 14:24:10 ubuntu kernel: [    0.671783]    groups: 1,3 (cpu_power = 1178)
Nov 11 14:24:10 ubuntu kernel: [    0.671792]    domain 2: span 0-3 level CPU
Nov 11 14:24:10 ubuntu kernel: [    0.671797]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
Nov 11 14:24:10 ubuntu kernel: [    0.671812] CPU2 attaching sched-domain:
Nov 11 14:24:10 ubuntu kernel: [    0.671817]  domain 0: span 0,2 level SIBLING
Nov 11 14:24:10 ubuntu kernel: [    0.671822]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
Nov 11 14:24:10 ubuntu kernel: [    0.671834]   domain 1: span 0,2 level MC
Nov 11 14:24:10 ubuntu kernel: [    0.671840]    groups: 0,2 (cpu_power = 1178)
Nov 11 14:24:10 ubuntu kernel: [    0.671849]    domain 2: span 0-3 level CPU
Nov 11 14:24:10 ubuntu kernel: [    0.671854]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
Nov 11 14:24:10 ubuntu kernel: [    0.671868] CPU3 attaching sched-domain:
Nov 11 14:24:10 ubuntu kernel: [    0.671873]  domain 0: span 1,3 level SIBLING
Nov 11 14:24:10 ubuntu kernel: [    0.671879]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
Nov 11 14:24:10 ubuntu kernel: [    0.671891]   domain 1: span 1,3 level MC
Nov 11 14:24:10 ubuntu kernel: [    0.671896]    groups: 1,3 (cpu_power = 1178)
Nov 11 14:24:10 ubuntu kernel: [    0.671906]    domain 2: span 0-3 level CPU
Nov 11 14:24:10 ubuntu kernel: [    0.671911]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
Nov 11 14:24:10 ubuntu kernel: [    0.672344] devtmpfs: initialized
Nov 11 14:24:10 ubuntu kernel: [    0.680987] regulator: core version 0.5
Nov 11 14:24:10 ubuntu kernel: [    0.680987] Time: 20:23:58  Date: 11/11/10
Nov 11 14:24:10 ubuntu kernel: [    0.680987] NET: Registered protocol family 16
Nov 11 14:24:10 ubuntu kernel: [    0.680987] ACPI: bus type pci registered
Nov 11 14:24:10 ubuntu kernel: [    0.680987] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub with MMCONFIG support.
Nov 11 14:24:10 ubuntu kernel: [    0.680987] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
Nov 11 14:24:10 ubuntu kernel: [    0.680987] PCI: Not using MMCONFIG.
Nov 11 14:24:10 ubuntu kernel: [    0.680987] PCI: Using configuration type 1 for base access
Nov 11 14:24:10 ubuntu kernel: [    0.682713] Trying to unpack rootfs image as initramfs...
Nov 11 14:24:10 ubuntu kernel: [    0.682747] bio: create slab <bio-0> at 0
Nov 11 14:24:10 ubuntu kernel: [    0.682747] ACPI: EC: Look up EC in DSDT
Nov 11 14:24:10 ubuntu kernel: [    0.686252] ACPI: Executed 1 blocks of module-level executable AML code
Nov 11 14:24:10 ubuntu kernel: [    0.704132] ACPI: Interpreter enabled
Nov 11 14:24:10 ubuntu kernel: [    0.704145] ACPI: (supports S0 S3 S4 S5)
Nov 11 14:24:10 ubuntu kernel: [    0.704197] ACPI: Using IOAPIC for interrupt routing
Nov 11 14:24:10 ubuntu kernel: [    0.722370] ACPI Warning: Incorrect checksum in table [OEMB] - 07, should be 06 (20090903/tbutils-314)
Nov 11 14:24:10 ubuntu kernel: [    0.722649] ACPI: No dock devices found.
Nov 11 14:24:10 ubuntu kernel: [    0.722953] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 11 14:24:10 ubuntu kernel: [    0.723125] pci 0000:00:02.0: reg 10 32bit mmio: [0xfea80000-0xfeafffff]
Nov 11 14:24:10 ubuntu kernel: [    0.723136] pci 0000:00:02.0: reg 14 io port: [0xdc00-0xdc07]
Nov 11 14:24:10 ubuntu kernel: [    0.723146] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
Nov 11 14:24:10 ubuntu kernel: [    0.723155] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfea40000-0xfea7ffff]
Nov 11 14:24:10 ubuntu kernel: [    0.723260] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfea38000-0xfea3bfff]
Nov 11 14:24:10 ubuntu kernel: [    0.723317] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Nov 11 14:24:10 ubuntu kernel: [    0.723326] pci 0000:00:1b.0: PME# disabled
Nov 11 14:24:10 ubuntu kernel: [    0.723406] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Nov 11 14:24:10 ubuntu kernel: [    0.723414] pci 0000:00:1c.0: PME# disabled
Nov 11 14:24:10 ubuntu kernel: [    0.723496] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Nov 11 14:24:10 ubuntu kernel: [    0.723503] pci 0000:00:1c.1: PME# disabled
Nov 11 14:24:10 ubuntu kernel: [    0.723569] pci 0000:00:1d.0: reg 20 io port: [0xd880-0xd89f]
Nov 11 14:24:10 ubuntu kernel: [    0.723639] pci 0000:00:1d.1: reg 20 io port: [0xd800-0xd81f]
Nov 11 14:24:10 ubuntu kernel: [    0.723706] pci 0000:00:1d.2: reg 20 io port: [0xd480-0xd49f]
Nov 11 14:24:10 ubuntu kernel: [    0.723783] pci 0000:00:1d.3: reg 20 io port: [0xd400-0xd41f]
Nov 11 14:24:10 ubuntu kernel: [    0.723855] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfea37c00-0xfea37fff]
Nov 11 14:24:10 ubuntu kernel: [    0.723919] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Nov 11 14:24:10 ubuntu kernel: [    0.723927] pci 0000:00:1d.7: PME# disabled
Nov 11 14:24:10 ubuntu kernel: [    0.724087] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Nov 11 14:24:10 ubuntu kernel: [    0.724096] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
Nov 11 14:24:10 ubuntu kernel: [    0.724104] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
Nov 11 14:24:10 ubuntu kernel: [    0.724162] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
Nov 11 14:24:10 ubuntu kernel: [    0.724174] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
Nov 11 14:24:10 ubuntu kernel: [    0.724187] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
Nov 11 14:24:10 ubuntu kernel: [    0.724199] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
Nov 11 14:24:10 ubuntu kernel: [    0.724210] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
Nov 11 14:24:10 ubuntu kernel: [    0.724267] pci 0000:00:1f.2: reg 10 io port: [0xd080-0xd087]
Nov 11 14:24:10 ubuntu kernel: [    0.724278] pci 0000:00:1f.2: reg 14 io port: [0xd000-0xd003]
Nov 11 14:24:10 ubuntu kernel: [    0.724288] pci 0000:00:1f.2: reg 18 io port: [0xcc00-0xcc07]
Nov 11 14:24:10 ubuntu kernel: [    0.724299] pci 0000:00:1f.2: reg 1c io port: [0xc880-0xc883]
Nov 11 14:24:10 ubuntu kernel: [    0.724309] pci 0000:00:1f.2: reg 20 io port: [0xc800-0xc80f]
Nov 11 14:24:10 ubuntu kernel: [    0.724342] pci 0000:00:1f.2: PME# supported from D3hot
Nov 11 14:24:10 ubuntu kernel: [    0.724350] pci 0000:00:1f.2: PME# disabled
Nov 11 14:24:10 ubuntu kernel: [    0.724408] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
Nov 11 14:24:10 ubuntu kernel: [    0.724566] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
Nov 11 14:24:10 ubuntu kernel: [    0.724595] pci 0000:02:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
Nov 11 14:24:10 ubuntu kernel: [    0.724624] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebc0000-0xfebdffff]
Nov 11 14:24:10 ubuntu kernel: [    0.724682] pci 0000:02:00.0: supports D1 D2
Nov 11 14:24:10 ubuntu kernel: [    0.724687] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
Nov 11 14:24:10 ubuntu kernel: [    0.724696] pci 0000:02:00.0: PME# disabled
Nov 11 14:24:10 ubuntu kernel: [    0.724758] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
Nov 11 14:24:10 ubuntu kernel: [    0.724766] pci 0000:00:1c.1: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
Nov 11 14:24:10 ubuntu kernel: [    0.724843] pci 0000:00:1e.0: transparent bridge
Nov 11 14:24:10 ubuntu kernel: [    0.724884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 11 14:24:10 ubuntu kernel: [    0.725174] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Nov 11 14:24:10 ubuntu kernel: [    0.725361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Nov 11 14:24:10 ubuntu kernel: [    0.725564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
Nov 11 14:24:10 ubuntu kernel: [    0.746774] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Nov 11 14:24:10 ubuntu kernel: [    0.747030] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Nov 11 14:24:10 ubuntu kernel: [    0.747278] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Nov 11 14:24:10 ubuntu kernel: [    0.747525] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Nov 11 14:24:10 ubuntu kernel: [    0.747775] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 11 14:24:10 ubuntu kernel: [    0.748026] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 11 14:24:10 ubuntu kernel: [    0.748272] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Nov 11 14:24:10 ubuntu kernel: [    0.748522] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Nov 11 14:24:10 ubuntu kernel: [    0.748834] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Nov 11 14:24:10 ubuntu kernel: [    0.748859] vgaarb: loaded
Nov 11 14:24:10 ubuntu kernel: [    0.749137] SCSI subsystem initialized
Nov 11 14:24:10 ubuntu kernel: [    0.749187] libata version 3.00 loaded.
Nov 11 14:24:10 ubuntu kernel: [    0.749187] usbcore: registered new interface driver usbfs
Nov 11 14:24:10 ubuntu kernel: [    0.749187] usbcore: registered new interface driver hub
Nov 11 14:24:10 ubuntu kernel: [    0.749187] usbcore: registered new device driver usb
Nov 11 14:24:10 ubuntu kernel: [    0.750144] ACPI: WMI: Mapper loaded
Nov 11 14:24:10 ubuntu kernel: [    0.750149] PCI: Using ACPI for IRQ routing
Nov 11 14:24:10 ubuntu kernel: [    0.750481] NetLabel: Initializing
Nov 11 14:24:10 ubuntu kernel: [    0.750487] NetLabel:  domain hash size = 128
Nov 11 14:24:10 ubuntu kernel: [    0.750491] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 11 14:24:10 ubuntu kernel: [    0.750519] NetLabel:  unlabeled traffic allowed by default
Nov 11 14:24:10 ubuntu kernel: [    0.750629] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Nov 11 14:24:10 ubuntu kernel: [    0.750642] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Nov 11 14:24:10 ubuntu kernel: [    0.780601] Switching to clocksource tsc
Nov 11 14:24:10 ubuntu kernel: [    0.784937] AppArmor: AppArmor Filesystem Enabled
Nov 11 14:24:10 ubuntu kernel: [    0.784988] pnp: PnP ACPI init
Nov 11 14:24:10 ubuntu kernel: [    0.785044] ACPI: bus type pnp registered
Nov 11 14:24:10 ubuntu kernel: [    0.792998] pnp: PnP ACPI: found 17 devices
Nov 11 14:24:10 ubuntu kernel: [    0.793006] ACPI: ACPI bus type pnp unregistered
Nov 11 14:24:10 ubuntu kernel: [    0.793038] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793061] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793069] system 00:06: ioport range 0x800-0x87f has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793076] system 00:06: ioport range 0x480-0x4bf has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793084] system 00:06: iomem range 0xfed1c000-0xfed1ffff has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793092] system 00:06: iomem range 0xfed20000-0xfed8ffff has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793108] system 00:09: iomem range 0xffc00000-0xfff7ffff has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793132] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793139] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793158] system 00:0d: ioport range 0xa00-0xa0f has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793165] system 00:0d: ioport range 0xa10-0xa1f has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793172] system 00:0d: ioport range 0xa20-0xa2f has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793180] system 00:0d: ioport range 0xa30-0xa3f has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793196] system 00:0f: iomem range 0xe0000000-0xe3ffffff has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793213] system 00:10: iomem range 0x0-0x9ffff could not be reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793221] system 00:10: iomem range 0xc0000-0xcffff has been reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793228] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
Nov 11 14:24:10 ubuntu kernel: [    0.793236] system 00:10: iomem range 0x100000-0x7f7fffff could not be reserved
Nov 11 14:24:10 ubuntu kernel: [    0.798304] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
Nov 11 14:24:10 ubuntu kernel: [    0.798313] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Nov 11 14:24:10 ubuntu kernel: [    0.798323] pci 0000:00:1c.0:   MEM window: 0x80000000-0x801fffff
Nov 11 14:24:10 ubuntu kernel: [    0.798333] pci 0000:00:1c.0:   PREFETCH window: 0x00000080200000-0x000000803fffff
Nov 11 14:24:10 ubuntu kernel: [    0.798345] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
Nov 11 14:24:10 ubuntu kernel: [    0.798352] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
Nov 11 14:24:10 ubuntu kernel: [    0.798361] pci 0000:00:1c.1:   MEM window: 0xfeb00000-0xfebfffff
Nov 11 14:24:10 ubuntu kernel: [    0.798370] pci 0000:00:1c.1:   PREFETCH window: 0x00000080400000-0x000000805fffff
Nov 11 14:24:10 ubuntu kernel: [    0.798381] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
Nov 11 14:24:10 ubuntu kernel: [    0.798386] pci 0000:00:1e.0:   IO window: disabled
Nov 11 14:24:10 ubuntu kernel: [    0.798394] pci 0000:00:1e.0:   MEM window: disabled
Nov 11 14:24:10 ubuntu kernel: [    0.798401] pci 0000:00:1e.0:   PREFETCH window: disabled
Nov 11 14:24:10 ubuntu kernel: [    0.798424] pci 0000:00:1c.0: enabling device (0104 -> 0107)
Nov 11 14:24:10 ubuntu kernel: [    0.798437]   alloc irq_desc for 16 on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.798442]   alloc kstat_irqs on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.798491] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 11 14:24:10 ubuntu kernel: [    0.798501] pci 0000:00:1c.0: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.798517]   alloc irq_desc for 17 on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.798522]   alloc kstat_irqs on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.798532] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Nov 11 14:24:10 ubuntu kernel: [    0.798541] pci 0000:00:1c.1: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.798555] pci 0000:00:1e.0: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.798564] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Nov 11 14:24:10 ubuntu kernel: [    0.798571] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Nov 11 14:24:10 ubuntu kernel: [    0.798578] pci_bus 0000:01: resource 0 io:  [0x1000-0x1fff]
Nov 11 14:24:10 ubuntu kernel: [    0.798584] pci_bus 0000:01: resource 1 mem: [0x80000000-0x801fffff]
Nov 11 14:24:10 ubuntu kernel: [    0.798591] pci_bus 0000:01: resource 2 pref mem [0x80200000-0x803fffff]
Nov 11 14:24:10 ubuntu kernel: [    0.798597] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
Nov 11 14:24:10 ubuntu kernel: [    0.798603] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
Nov 11 14:24:10 ubuntu kernel: [    0.798610] pci_bus 0000:02: resource 2 pref mem [0x80400000-0x805fffff]
Nov 11 14:24:10 ubuntu kernel: [    0.798617] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
Nov 11 14:24:10 ubuntu kernel: [    0.798624] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
Nov 11 14:24:10 ubuntu kernel: [    0.798726] NET: Registered protocol family 2
Nov 11 14:24:10 ubuntu kernel: [    0.799093] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Nov 11 14:24:10 ubuntu kernel: [    0.801290] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Nov 11 14:24:10 ubuntu kernel: [    0.805398] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 11 14:24:10 ubuntu kernel: [    0.806368] TCP: Hash tables configured (established 262144 bind 65536)
Nov 11 14:24:10 ubuntu kernel: [    0.806376] TCP reno registered
Nov 11 14:24:10 ubuntu kernel: [    0.806660] NET: Registered protocol family 1
Nov 11 14:24:10 ubuntu kernel: [    0.806719] pci 0000:00:02.0: Boot video device
Nov 11 14:24:10 ubuntu kernel: [    0.807672] Scanning for low memory corruption every 60 seconds
Nov 11 14:24:10 ubuntu kernel: [    0.807996] audit: initializing netlink socket (disabled)
Nov 11 14:24:10 ubuntu kernel: [    0.808032] type=2000 audit(1289507037.798:1): initialized
Nov 11 14:24:10 ubuntu kernel: [    0.824906] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Nov 11 14:24:10 ubuntu kernel: [    0.828871] VFS: Disk quotas dquot_6.5.2
Nov 11 14:24:10 ubuntu kernel: [    0.829037] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 11 14:24:10 ubuntu kernel: [    0.830764] fuse init (API version 7.13)
Nov 11 14:24:10 ubuntu kernel: [    0.831001] msgmni has been set to 3984
Nov 11 14:24:10 ubuntu gdm-binary[829]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 11 14:24:10 ubuntu kernel: [    0.831785] alg: No test for stdrng (krng)
Nov 11 14:24:10 ubuntu kernel: [    0.831970] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Nov 11 14:24:10 ubuntu kernel: [    0.831978] io scheduler noop registered
Nov 11 14:24:10 ubuntu kernel: [    0.831983] io scheduler anticipatory registered
Nov 11 14:24:10 ubuntu kernel: [    0.831988] io scheduler deadline registered (default)
Nov 11 14:24:10 ubuntu kernel: [    0.832090] io scheduler cfq registered
Nov 11 14:24:10 ubuntu kernel: [    0.832364]   alloc irq_desc for 24 on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.832369]   alloc kstat_irqs on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.832389] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
Nov 11 14:24:10 ubuntu kernel: [    0.832404] pcieport 0000:00:1c.0: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.832576]   alloc irq_desc for 25 on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.832581]   alloc kstat_irqs on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.832595] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
Nov 11 14:24:10 ubuntu kernel: [    0.832608] pcieport 0000:00:1c.1: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.832760] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 11 14:24:10 ubuntu kernel: [    0.832944] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 11 14:24:10 ubuntu kernel: [    0.833196] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Nov 11 14:24:10 ubuntu kernel: [    0.833205] ACPI: Power Button [PWRB]
Nov 11 14:24:10 ubuntu kernel: [    0.833318] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Nov 11 14:24:10 ubuntu kernel: [    0.833325] ACPI: Power Button [PWRF]
Nov 11 14:24:10 ubuntu kernel: [    0.834000] processor LNXCPU:00: registered as cooling_device0
Nov 11 14:24:10 ubuntu kernel: [    0.834097] processor LNXCPU:01: registered as cooling_device1
Nov 11 14:24:10 ubuntu kernel: [    0.834190] processor LNXCPU:02: registered as cooling_device2
Nov 11 14:24:10 ubuntu kernel: [    0.834296] processor LNXCPU:03: registered as cooling_device3
Nov 11 14:24:10 ubuntu kernel: [    0.840864] thermal LNXTHERM:01: registered as thermal_zone0
Nov 11 14:24:10 ubuntu kernel: [    0.840883] ACPI: Thermal Zone [THRM] (40 C)
Nov 11 14:24:10 ubuntu kernel: [    0.845057] Linux agpgart interface v0.103
Nov 11 14:24:10 ubuntu kernel: [    0.845146] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 11 14:24:10 ubuntu kernel: [    0.845305] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 11 14:24:10 ubuntu kernel: [    0.846044] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 11 14:24:10 ubuntu kernel: [    0.848920] brd: module loaded
Nov 11 14:24:10 ubuntu kernel: [    0.850238] loop: module loaded
Nov 11 14:24:10 ubuntu kernel: [    0.850531] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Nov 11 14:24:10 ubuntu kernel: [    0.850851] ata_piix 0000:00:1f.1: version 2.13
Nov 11 14:24:10 ubuntu kernel: [    0.850883]   alloc irq_desc for 18 on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.850889]   alloc kstat_irqs on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.850905] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Nov 11 14:24:10 ubuntu kernel: [    0.850978] ata_piix 0000:00:1f.1: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.851179] scsi0 : ata_piix
Nov 11 14:24:10 ubuntu kernel: [    0.851420] scsi1 : ata_piix
Nov 11 14:24:10 ubuntu kernel: [    0.854638] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Nov 11 14:24:10 ubuntu kernel: [    0.854647] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Nov 11 14:24:10 ubuntu kernel: [    0.854733]   alloc irq_desc for 19 on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.854740]   alloc kstat_irqs on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.854756] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 11 14:24:10 ubuntu kernel: [    0.854768] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Nov 11 14:24:10 ubuntu kernel: [    0.854842] ata_piix 0000:00:1f.2: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.855058] scsi2 : ata_piix
Nov 11 14:24:10 ubuntu kernel: [    0.855300] scsi3 : ata_piix
Nov 11 14:24:10 ubuntu kernel: [    0.858896] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
Nov 11 14:24:10 ubuntu kernel: [    0.858906] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
Nov 11 14:24:10 ubuntu kernel: [    0.859806] Fixed MDIO Bus: probed
Nov 11 14:24:10 ubuntu kernel: [    0.859895] PPP generic driver version 2.4.2
Nov 11 14:24:10 ubuntu kernel: [    0.860045] tun: Universal TUN/TAP device driver, 1.6
Nov 11 14:24:10 ubuntu kernel: [    0.860051] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Nov 11 14:24:10 ubuntu kernel: [    0.860310] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 11 14:24:10 ubuntu kernel: [    0.860364]   alloc irq_desc for 23 on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.860370]   alloc kstat_irqs on node -1
Nov 11 14:24:10 ubuntu kernel: [    0.860386] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 11 14:24:10 ubuntu kernel: [    0.860421] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.860429] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Nov 11 14:24:10 ubuntu kernel: [    0.860526] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Nov 11 14:24:10 ubuntu kernel: [    0.860567] ehci_hcd 0000:00:1d.7: using broken periodic workaround
Nov 11 14:24:10 ubuntu kernel: [    0.860585] ehci_hcd 0000:00:1d.7: debug port 1
Nov 11 14:24:10 ubuntu kernel: [    0.864474] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Nov 11 14:24:10 ubuntu kernel: [    0.864516] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfea37c00
Nov 11 14:24:10 ubuntu kernel: [    0.878509] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Nov 11 14:24:10 ubuntu kernel: [    0.878823] usb usb1: configuration #1 chosen from 1 choice
Nov 11 14:24:10 ubuntu kernel: [    0.878898] hub 1-0:1.0: USB hub found
Nov 11 14:24:10 ubuntu kernel: [    0.878918] hub 1-0:1.0: 8 ports detected
Nov 11 14:24:10 ubuntu kernel: [    0.879071] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 11 14:24:10 ubuntu kernel: [    0.879108] uhci_hcd: USB Universal Host Controller Interface driver
Nov 11 14:24:10 ubuntu kernel: [    0.879185] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Nov 11 14:24:10 ubuntu kernel: [    0.879202] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.879210] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Nov 11 14:24:10 ubuntu kernel: [    0.879340] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Nov 11 14:24:10 ubuntu kernel: [    0.879384] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
Nov 11 14:24:10 ubuntu kernel: [    0.879611] usb usb2: configuration #1 chosen from 1 choice
Nov 11 14:24:10 ubuntu kernel: [    0.879684] hub 2-0:1.0: USB hub found
Nov 11 14:24:10 ubuntu kernel: [    0.879701] hub 2-0:1.0: 2 ports detected
Nov 11 14:24:10 ubuntu kernel: [    0.879807] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Nov 11 14:24:10 ubuntu kernel: [    0.879820] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.879827] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Nov 11 14:24:10 ubuntu kernel: [    0.879919] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Nov 11 14:24:10 ubuntu kernel: [    0.879957] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
Nov 11 14:24:10 ubuntu kernel: [    0.880184] usb usb3: configuration #1 chosen from 1 choice
Nov 11 14:24:10 ubuntu kernel: [    0.880253] hub 3-0:1.0: USB hub found
Nov 11 14:24:10 ubuntu kernel: [    0.880270] hub 3-0:1.0: 2 ports detected
Nov 11 14:24:10 ubuntu kernel: [    0.880379] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Nov 11 14:24:10 ubuntu kernel: [    0.880392] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.880399] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Nov 11 14:24:10 ubuntu kernel: [    0.880494] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Nov 11 14:24:10 ubuntu kernel: [    0.880557] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
Nov 11 14:24:10 ubuntu kernel: [    0.880809] usb usb4: configuration #1 chosen from 1 choice
Nov 11 14:24:10 ubuntu kernel: [    0.880878] hub 4-0:1.0: USB hub found
Nov 11 14:24:10 ubuntu kernel: [    0.880898] hub 4-0:1.0: 2 ports detected
Nov 11 14:24:10 ubuntu kernel: [    0.881011] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Nov 11 14:24:10 ubuntu kernel: [    0.881026] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    0.881033] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Nov 11 14:24:10 ubuntu kernel: [    0.881141] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Nov 11 14:24:10 ubuntu kernel: [    0.881193] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d400
Nov 11 14:24:10 ubuntu kernel: [    0.881418] usb usb5: configuration #1 chosen from 1 choice
Nov 11 14:24:10 ubuntu kernel: [    0.881487] hub 5-0:1.0: USB hub found
Nov 11 14:24:10 ubuntu kernel: [    0.881504] hub 5-0:1.0: 2 ports detected
Nov 11 14:24:10 ubuntu kernel: [    0.881731] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Nov 11 14:24:10 ubuntu kernel: [    0.882141] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 11 14:24:10 ubuntu kernel: [    0.882163] serio: i8042 AUX port at 0x60,0x64 irq 12
Nov 11 14:24:10 ubuntu kernel: [    0.882449] mice: PS/2 mouse device common for all mice
Nov 11 14:24:10 ubuntu kernel: [    0.882722] rtc_cmos 00:03: RTC can wake from S4
Nov 11 14:24:10 ubuntu kernel: [    0.882830] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Nov 11 14:24:10 ubuntu kernel: [    0.882870] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Nov 11 14:24:10 ubuntu kernel: [    0.883215] device-mapper: uevent: version 1.0.3
Nov 11 14:24:10 ubuntu kernel: [    0.883529] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Nov 11 14:24:10 ubuntu kernel: [    0.883912] device-mapper: multipath: version 1.1.0 loaded
Nov 11 14:24:10 ubuntu kernel: [    0.883922] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 11 14:24:10 ubuntu kernel: [    0.884657] cpuidle: using governor ladder
Nov 11 14:24:10 ubuntu kernel: [    0.884663] cpuidle: using governor menu
Nov 11 14:24:10 ubuntu kernel: [    0.885565] TCP cubic registered
Nov 11 14:24:10 ubuntu kernel: [    0.885906] NET: Registered protocol family 10
Nov 11 14:24:10 ubuntu kernel: [    0.887158] lo: Disabled Privacy Extensions
Nov 11 14:24:10 ubuntu kernel: [    0.887921] NET: Registered protocol family 17
Nov 11 14:24:10 ubuntu kernel: [    0.888301] PM: Resume from disk failed.
Nov 11 14:24:10 ubuntu kernel: [    0.888331] registered taskstats version 1
Nov 11 14:24:10 ubuntu kernel: [    0.888892]   Magic number: 2:801:396
Nov 11 14:24:10 ubuntu kernel: [    0.889075] rtc_cmos 00:03: setting system clock to 2010-11-11 20:23:58 UTC (1289507038)
Nov 11 14:24:10 ubuntu kernel: [    0.889083] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 11 14:24:10 ubuntu kernel: [    0.889087] EDD information not available.
Nov 11 14:24:10 ubuntu kernel: [    0.908454] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Nov 11 14:24:10 ubuntu kernel: [    1.063056] ata4.00: ATA-8: WDC WD1600AAJS-00B4A0, 01.03A01, max UDMA/133
Nov 11 14:24:10 ubuntu kernel: [    1.063065] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
Nov 11 14:24:10 ubuntu kernel: [    1.081103] ata4.00: configured for UDMA/133
Nov 11 14:24:10 ubuntu kernel: [    1.081351] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 01.0 PQ: 0 ANSI: 5
Nov 11 14:24:10 ubuntu kernel: [    1.081679] sd 3:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Nov 11 14:24:10 ubuntu kernel: [    1.081758] sd 3:0:0:0: Attached scsi generic sg0 type 0
Nov 11 14:24:10 ubuntu kernel: [    1.081901] sd 3:0:0:0: [sda] Write Protect is off
Nov 11 14:24:10 ubuntu kernel: [    1.081911] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 11 14:24:10 ubuntu kernel: [    1.082012] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 11 14:24:10 ubuntu kernel: [    1.082425]  sda:
Nov 11 14:24:10 ubuntu kernel: [    1.085206] Freeing initrd memory: 8059k freed
Nov 11 14:24:10 ubuntu kernel: [    1.132380]  sda1 sda2 sda3 sda4
Nov 11 14:24:10 ubuntu kernel: [    1.133297] sd 3:0:0:0: [sda] Attached SCSI disk
Nov 11 14:24:10 ubuntu kernel: [    1.133347] Freeing unused kernel memory: 800k freed
Nov 11 14:24:10 ubuntu kernel: [    1.133889] Write protecting the kernel read-only data: 7804k
Nov 11 14:24:10 ubuntu kernel: [    1.177274] udev: starting version 151
Nov 11 14:24:10 ubuntu kernel: [    1.210232] usb 1-5: new high speed USB device using ehci_hcd and address 2
Nov 11 14:24:10 ubuntu kernel: [    1.312040] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 11 14:24:10 ubuntu kernel: [    1.312113] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 11 14:24:10 ubuntu kernel: [    1.312204] r8169 0000:02:00.0: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [    1.312299]   alloc irq_desc for 26 on node -1
Nov 11 14:24:10 ubuntu kernel: [    1.312307]   alloc kstat_irqs on node -1
Nov 11 14:24:10 ubuntu kernel: [    1.312339] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
Nov 11 14:24:10 ubuntu kernel: [    1.314417] eth0: RTL8101e at 0xffffc900008c2000, 90:fb:a6:21:02:6c, XID 94200000 IRQ 26
Nov 11 14:24:10 ubuntu kernel: [    1.527587] usb 1-5: configuration #1 chosen from 1 choice
Nov 11 14:24:10 ubuntu kernel: [    1.849758] EXT4-fs (sda4): INFO: recovery required on readonly filesystem
Nov 11 14:24:10 ubuntu kernel: [    1.849768] EXT4-fs (sda4): write access will be enabled during recovery
Nov 11 14:24:10 ubuntu kernel: [    2.067880] EXT4-fs (sda4): orphan cleanup on readonly fs
Nov 11 14:24:10 ubuntu kernel: [    2.067912] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 2367623
Nov 11 14:24:10 ubuntu kernel: [    2.067993] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 2367569
Nov 11 14:24:10 ubuntu kernel: [    2.068028] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 2367470
Nov 11 14:24:10 ubuntu kernel: [    2.068134] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 2367442
Nov 11 14:24:10 ubuntu kernel: [    2.068164] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 2367370
Nov 11 14:24:10 ubuntu kernel: [    2.068214] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 2367268
Nov 11 14:24:10 ubuntu kernel: [    2.068265] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 2365850
Nov 11 14:24:10 ubuntu kernel: [    2.068294] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 2360858
Nov 11 14:24:10 ubuntu kernel: [    2.068344] EXT4-fs (sda4): ext4_orphan_cleanup: deleting unreferenced inode 4718645
Nov 11 14:24:10 ubuntu kernel: [    2.068419] EXT4-fs (sda4): 9 orphan inodes deleted
Nov 11 14:24:10 ubuntu kernel: [    2.068427] EXT4-fs (sda4): recovery complete
Nov 11 14:24:10 ubuntu kernel: [    2.436787] EXT4-fs (sda4): mounted filesystem with ordered data mode
Nov 11 14:24:10 ubuntu kernel: [   11.235429] Adding 4002808k swap on /dev/sda1.  Priority:-1 extents:1 across:4002808k 
Nov 11 14:24:10 ubuntu kernel: [   11.258431] udev: starting version 151
Nov 11 14:24:10 ubuntu kernel: [   11.358630] lp: driver loaded but no devices found
Nov 11 14:24:10 ubuntu kernel: [   11.373829] agpgart-intel 0000:00:00.0: Intel 945G Chipset
Nov 11 14:24:10 ubuntu kernel: [   11.374206] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
Nov 11 14:24:10 ubuntu kernel: [   11.378820] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Nov 11 14:24:10 ubuntu kernel: [   11.522732] [drm] Initialized drm 1.1.0 20060810
Nov 11 14:24:10 ubuntu kernel: [   11.706230] intel_rng: FWH not detected
Nov 11 14:24:10 ubuntu kernel: [   11.775369] Linux video capture interface: v2.00
Nov 11 14:24:10 ubuntu kernel: [   11.823283] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0807)
Nov 11 14:24:10 ubuntu kernel: [   11.891181] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 11 14:24:10 ubuntu kernel: [   11.891198] i915 0000:00:02.0: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [   11.921281] input: UVC Camera (046d:0807) as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input4
Nov 11 14:24:10 ubuntu kernel: [   11.921484] usbcore: registered new interface driver uvcvideo
Nov 11 14:24:10 ubuntu kernel: [   11.921495] USB Video Class driver (v0.1.0)
Nov 11 14:24:10 ubuntu kernel: [   11.924341] [drm] set up 7M of stolen space
Nov 11 14:24:10 ubuntu kernel: [   11.925852] [drm] initialized overlay support
Nov 11 14:24:10 ubuntu kernel: [   11.953399] type=1505 audit(1289507049.560:2):  operation="profile_load" pid=584 name="/sbin/dhclient3"
Nov 11 14:24:10 ubuntu kernel: [   11.954183] type=1505 audit(1289507049.560:3):  operation="profile_load" pid=584 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Nov 11 14:24:10 ubuntu kernel: [   11.954636] type=1505 audit(1289507049.560:4):  operation="profile_load" pid=584 name="/usr/lib/connman/scripts/dhclient-script"
Nov 11 14:24:10 ubuntu kernel: [   11.966369] r8169: eth0: link up
Nov 11 14:24:10 ubuntu kernel: [   11.966385] r8169: eth0: link up
Nov 11 14:24:10 ubuntu kernel: [   12.127329] fb0: inteldrmfb frame buffer device
Nov 11 14:24:10 ubuntu kernel: [   12.127337] registered panic notifier
Nov 11 14:24:10 ubuntu kernel: [   12.127358] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Nov 11 14:24:10 ubuntu kernel: [   12.129081] EXT4-fs (sda3): mounted filesystem with ordered data mode
Nov 11 14:24:10 ubuntu kernel: [   12.129512] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 11 14:24:10 ubuntu kernel: [   12.129588] HDA Intel 0000:00:1b.0: setting latency timer to 64
Nov 11 14:24:10 ubuntu kernel: [   12.133661] vga16fb: initializing
Nov 11 14:24:10 ubuntu avahi-daemon[845]: Found user 'avahi' (UID 109) and group 'avahi' (GID 119).
Nov 11 14:24:10 ubuntu avahi-daemon[845]: Successfully dropped root privileges.
Nov 11 14:24:10 ubuntu kernel: [   12.133673] vga16fb: mapped to 0xffff8800000a0000
Nov 11 14:24:10 ubuntu kernel: [   12.133686] vga16fb: not registering due to another framebuffer present
Nov 11 14:24:10 ubuntu kernel: [   12.268873] hda_codec: ALC662 rev1: BIOS auto-probing.
Nov 11 14:24:10 ubuntu kernel: [   12.271186] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
Nov 11 14:24:10 ubuntu kernel: [   12.286867] Console: switching to colour frame buffer device 160x64
Nov 11 14:24:10 ubuntu kernel: [   12.325137] usbcore: registered new interface driver snd-usb-audio
Nov 11 14:24:10 ubuntu kernel: [   12.524798] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Nov 11 14:24:10 ubuntu kernel: [   12.620486] EXT4-fs (sda2): mounted filesystem with ordered data mode
Nov 11 14:24:10 ubuntu avahi-daemon[845]: avahi-daemon 0.6.25 starting up.
Nov 11 14:24:10 ubuntu avahi-daemon[845]: Successfully called chroot().
Nov 11 14:24:10 ubuntu avahi-daemon[845]: Successfully dropped remaining capabilities.
Nov 11 14:24:10 ubuntu NetworkManager: <info>  starting...
Nov 11 14:24:10 ubuntu NetworkManager: <info>  Trying to start the modem-manager...
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: init!
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Nov 11 14:24:10 ubuntu NetworkManager:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
Nov 11 14:24:10 ubuntu kernel: [   12.936529] type=1505 audit(1289507050.540:5):  operation="profile_load" pid=853 name="/usr/share/gdm/guest-session/Xsession"
Nov 11 14:24:10 ubuntu avahi-daemon[845]: No service file found in /etc/avahi/services.
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Gobi
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Nokia
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Ericsson MBM
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin ZTE
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin AnyData
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Option High-Speed
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Novatel
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Huawei
Nov 11 14:24:10 ubuntu avahi-daemon[845]: Network interface enumeration completed.
Nov 11 14:24:10 ubuntu avahi-daemon[845]: Registering new address record for fe80::92fb:a6ff:fe21:26c on eth0.*.
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Option
Nov 11 14:24:10 ubuntu avahi-daemon[845]: Server startup complete. Host name is ubuntu.local. Local service cookie is 3233795836.
Nov 11 14:24:10 ubuntu avahi-daemon[845]: Registering HINFO record with values 'X86_64'/'LINUX'.
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: autoconnect
Nov 11 14:24:10 ubuntu NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth0, iface: eth0)
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Longcheer
Nov 11 14:24:10 ubuntu NetworkManager:    SCPluginIfupdown: locking wired connection setting
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin MotoC
Nov 11 14:24:10 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 1
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: (33640736) ... get_connections.
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: (33640736) ... get_connections (managed=false): return empty list.
Nov 11 14:24:10 ubuntu NetworkManager:    Ifupdown: get unmanaged devices count: 1
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 11 14:24:10 ubuntu NetworkManager:    SCPlugin-Ifupdown: end _init.
Nov 11 14:24:10 ubuntu NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Generic
Nov 11 14:24:10 ubuntu modem-manager: Loaded plugin Sierra
Nov 11 14:24:10 ubuntu NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 11 14:24:10 ubuntu kernel: [   12.966198] type=1505 audit(1289507050.570:6):  operation="profile_replace" pid=929 name="/sbin/dhclient3"
Nov 11 14:24:10 ubuntu kernel: [   12.967002] type=1505 audit(1289507050.570:7):  operation="profile_replace" pid=929 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Nov 11 14:24:10 ubuntu kernel: [   12.967497] type=1505 audit(1289507050.570:8):  operation="profile_replace" pid=929 name="/usr/lib/connman/scripts/dhclient-script"
Nov 11 14:24:10 ubuntu kernel: [   12.985759] type=1505 audit(1289507050.590:9):  operation="profile_load" pid=934 name="/usr/bin/evince"
Nov 11 14:24:10 ubuntu NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Nov 11 14:24:10 ubuntu NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Nov 11 14:24:10 ubuntu NetworkManager: <info>  (eth0): carrier is ON
Nov 11 14:24:10 ubuntu NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Nov 11 14:24:10 ubuntu NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 11 14:24:10 ubuntu kernel: [   13.010871] type=1505 audit(1289507050.620:10):  operation="profile_load" pid=934 name="/usr/bin/evince-previewer"
Nov 11 14:24:10 ubuntu gdm-binary[829]: WARNING: Unable to find users: no seat-id found
Nov 11 14:24:10 ubuntu NetworkManager: <info>  modem-manager is now available
Nov 11 14:24:10 ubuntu NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov 11 14:24:10 ubuntu NetworkManager: <info>  Trying to start the supplicant...
Nov 11 14:24:10 ubuntu kernel: [   13.021894] type=1505 audit(1289507050.630:11):  operation="profile_load" pid=934 name="/usr/bin/evince-thumbnailer"
Nov 11 14:24:10 ubuntu gdm-simple-slave[940]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 11 14:24:10 ubuntu init: plymouth main process (294) killed by SEGV signal
Nov 11 14:24:10 ubuntu init: apport pre-start process (1028) terminated with status 1
Nov 11 14:24:10 ubuntu cron[1039]: (CRON) INFO (pidfile fd = 3)
Nov 11 14:24:10 ubuntu acpid: starting up with proc fs
Nov 11 14:24:10 ubuntu cron[1063]: (CRON) STARTUP (fork ok)
Nov 11 14:24:10 ubuntu anacron[1059]: Anacron 2.3 started on 2010-11-11
Nov 11 14:24:10 ubuntu acpid: 36 rules loaded
Nov 11 14:24:10 ubuntu acpid: waiting for events: event logging is off
Nov 11 14:24:10 ubuntu acpid: client connected from 990[0:0]
Nov 11 14:24:10 ubuntu acpid: 1 client rule loaded
Nov 11 14:24:10 ubuntu cron[1063]: (CRON) INFO (Running @reboot jobs)
Nov 11 14:24:10 ubuntu init: apport post-stop process (1061) terminated with status 1
Nov 11 14:24:11 ubuntu anacron[1059]: Will run job `cron.weekly' in 10 min.
Nov 11 14:24:11 ubuntu anacron[1059]: Will run job `cron.monthly' in 15 min.
Nov 11 14:24:11 ubuntu anacron[1059]: Jobs will be executed sequentially
Nov 11 14:24:11 ubuntu dhclient: DHCPREQUEST of 192.168.2.8 on eth0 to 255.255.255.255 port 67
Nov 11 14:24:11 ubuntu dhclient: DHCPACK of 192.168.2.8 from 192.168.2.1
Nov 11 14:24:11 ubuntu avahi-daemon[845]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.8.
Nov 11 14:24:11 ubuntu avahi-daemon[845]: New relevant interface eth0.IPv4 for mDNS.
Nov 11 14:24:11 ubuntu avahi-daemon[845]: Registering new address record for 192.168.2.8 on eth0.IPv4.
Nov 11 14:24:11 ubuntu kernel: [   13.481827] r8169: WARNING! Changing of MTU on this NIC may lead to frame reception errors!
Nov 11 14:24:11 ubuntu dhclient: bound to 192.168.2.8 -- renewal in 2147483648 seconds.
Nov 11 14:24:13 ubuntu amavis[1046]: starting.  /usr/sbin/amavisd-new at ubuntu.Survivorfun amavisd-new-2.6.4 (20090625), Unicode aware
Nov 11 14:24:13 ubuntu amavis[1046]: Perl version               5.010001
Nov 11 14:24:13 ubuntu amavis[1178]: Net::Server: Group Not Defined.  Defaulting to EGID '116 116'
Nov 11 14:24:13 ubuntu amavis[1178]: Net::Server: User Not Defined.  Defaulting to EUID '107'
Nov 11 14:24:13 ubuntu gdm-session-worker[1197]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 11 14:24:13 ubuntu amavis[1178]: Module Amavis::Conf        2.207
Nov 11 14:24:13 ubuntu amavis[1178]: Module Archive::Zip        1.30
Nov 11 14:24:13 ubuntu amavis[1178]: Module BerkeleyDB          0.39
Nov 11 14:24:13 ubuntu amavis[1178]: Module Compress::Zlib      2.02
Nov 11 14:24:13 ubuntu amavis[1178]: Module Convert::TNEF       0.17
Nov 11 14:24:13 ubuntu amavis[1178]: Module Convert::UUlib      1.12
Nov 11 14:24:13 ubuntu amavis[1178]: Module Crypt::OpenSSL::RSA 0.25
Nov 11 14:24:13 ubuntu amavis[1178]: Module Digest::MD5         2.39
Nov 11 14:24:13 ubuntu amavis[1178]: Module Digest::SHA         5.47
Nov 11 14:24:13 ubuntu amavis[1178]: Module IO::Socket::INET6   2.54
Nov 11 14:24:13 ubuntu amavis[1178]: Module MIME::Entity        5.427
Nov 11 14:24:13 ubuntu amavis[1178]: Module MIME::Parser        5.427
Nov 11 14:24:13 ubuntu amavis[1178]: Module MIME::Tools         5.427
Nov 11 14:24:13 ubuntu amavis[1178]: Module Mail::DKIM::Signer  0.38
Nov 11 14:24:13 ubuntu amavis[1178]: Module Mail::DKIM::Verifier 0.38
Nov 11 14:24:13 ubuntu amavis[1178]: Module Mail::Header        2.05
Nov 11 14:24:13 ubuntu amavis[1178]: Module Mail::Internet      2.05
Nov 11 14:24:13 ubuntu amavis[1178]: Module Net::DNS            0.65
Nov 11 14:24:13 ubuntu amavis[1178]: Module Net::Server         0.97
Nov 11 14:24:13 ubuntu amavis[1178]: Module Socket6             0.23
Nov 11 14:24:13 ubuntu amavis[1178]: Module Time::HiRes         1.9719
Nov 11 14:24:13 ubuntu amavis[1178]: Module Unix::Syslog        1.1
Nov 11 14:24:13 ubuntu rtkit-daemon[1231]: Sucessfully called chroot.
Nov 11 14:24:13 ubuntu amavis[1178]: Amavis::DB code      loaded
Nov 11 14:24:13 ubuntu amavis[1178]: Amavis::Cache code   loaded
Nov 11 14:24:13 ubuntu amavis[1178]: SQL base code        NOT loaded
Nov 11 14:24:13 ubuntu rtkit-daemon[1231]: Sucessfully dropped privileges.
Nov 11 14:24:13 ubuntu amavis[1178]: SQL::Log code        NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: SQL::Quarantine      NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: Lookup::SQL code     NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: Lookup::LDAP code    NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: AM.PDP-in proto code loaded
Nov 11 14:24:13 ubuntu rtkit-daemon[1231]: Sucessfully limited resources.
Nov 11 14:24:13 ubuntu amavis[1178]: SMTP-in proto code   loaded
Nov 11 14:24:13 ubuntu amavis[1178]: Courier proto code   NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: SMTP-out proto code  loaded
Nov 11 14:24:13 ubuntu amavis[1178]: Pipe-out proto code  NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: BSMTP-out proto code NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: Local-out proto code loaded
Nov 11 14:24:13 ubuntu amavis[1178]: OS_Fingerprint code  NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: ANTI-VIRUS code      NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: ANTI-SPAM code       NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: ANTI-SPAM-EXT code   NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: ANTI-SPAM-C code     NOT loaded
Nov 11 14:24:13 ubuntu amavis[1178]: ANTI-SPAM-SA code    NOT loaded
Nov 11 14:24:13 ubuntu rtkit-daemon[1231]: Running.
Nov 11 14:24:13 ubuntu amavis[1178]: Unpackers code       loaded
Nov 11 14:24:13 ubuntu amavis[1178]: DKIM code            loaded
Nov 11 14:24:13 ubuntu amavis[1178]: Tools code           NOT loaded
Nov 11 14:24:13 ubuntu rtkit-daemon[1231]: Watchdog thread running.
Nov 11 14:24:13 ubuntu amavis[1178]: Found $file            at /usr/bin/file
Nov 11 14:24:13 ubuntu amavis[1178]: No $altermime,         not using it
Nov 11 14:24:13 ubuntu amavis[1178]: Internal decoder for .mail
Nov 11 14:24:13 ubuntu amavis[1178]: No decoder for       .F   
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .Z    at /bin/uncompress
Nov 11 14:24:13 ubuntu amavis[1178]: Internal decoder for .gz  
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .bz2  at /bin/bzip2 -d
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .lzo  at /usr/bin/lzop -d
Nov 11 14:24:13 ubuntu rtkit-daemon[1231]: Canary thread running.
Nov 11 14:24:13 ubuntu amavis[1178]: No decoder for       .rpm  tried: rpm2cpio.pl, rpm2cpio
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .cpio at /usr/bin/pax
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .tar  at /usr/bin/pax
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .deb  at /usr/bin/ar
Nov 11 14:24:13 ubuntu amavis[1178]: Internal decoder for .zip 
Nov 11 14:24:13 ubuntu amavis[1178]: No decoder for       .7z   tried: 7zr, 7za, 7z
Nov 11 14:24:13 ubuntu amavis[1178]: No decoder for       .rar  tried: unrar-free
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .arj  at /usr/bin/arj
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .arc  at /usr/bin/nomarch
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .zoo  at /usr/bin/zoo
Nov 11 14:24:13 ubuntu amavis[1178]: No decoder for       .lha 
Nov 11 14:24:13 ubuntu amavis[1178]: No decoder for       .doc  tried: ripole
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .cab  at /usr/bin/cabextract
Nov 11 14:24:13 ubuntu amavis[1178]: No decoder for       .tnef
Nov 11 14:24:13 ubuntu amavis[1178]: Internal decoder for .tnef
Nov 11 14:24:13 ubuntu amavis[1178]: Found decoder for    .exe  at /usr/bin/arj
Nov 11 14:24:13 ubuntu init: ssh main process (806) terminated with status 255
Nov 11 14:24:13 ubuntu amavis[1178]: Creating db in /var/lib/amavis/db/; BerkeleyDB 0.39, libdb 4.8
Nov 11 14:24:13 ubuntu polkitd[1243]: started daemon version 0.96 using authority implementation `local' version `0.96'
Nov 11 14:24:13 ubuntu init: Failed to spawn vsftpd main process: unable to execute: No such file or directory
Nov 11 14:24:13 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1223 of process 1223 (n/a) owned by '119' high priority at nice level -11.
Nov 11 14:24:13 ubuntu rtkit-daemon[1231]: Supervising 1 threads of 1 processes of 1 users.
Nov 11 14:24:14 ubuntu kernel: [   16.514011] CPU0 attaching NULL sched-domain.
Nov 11 14:24:14 ubuntu kernel: [   16.514042] CPU1 attaching NULL sched-domain.
Nov 11 14:24:14 ubuntu kernel: [   16.514053] CPU2 attaching NULL sched-domain.
Nov 11 14:24:14 ubuntu kernel: [   16.514063] CPU3 attaching NULL sched-domain.
Nov 11 14:24:14 ubuntu kernel: [   16.600362] CPU0 attaching sched-domain:
Nov 11 14:24:14 ubuntu kernel: [   16.600373]  domain 0: span 0,2 level SIBLING
Nov 11 14:24:14 ubuntu kernel: [   16.600380]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
Nov 11 14:24:14 ubuntu kernel: [   16.600394]   domain 1: span 0,2 level MC
Nov 11 14:24:14 ubuntu kernel: [   16.600399]    groups: 0,2 (cpu_power = 1178)
Nov 11 14:24:14 ubuntu kernel: [   16.600409]    domain 2: span 0-3 level CPU
Nov 11 14:24:14 ubuntu kernel: [   16.600415]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
Nov 11 14:24:14 ubuntu kernel: [   16.600433] CPU1 attaching sched-domain:
Nov 11 14:24:14 ubuntu kernel: [   16.600439]  domain 0: span 1,3 level SIBLING
Nov 11 14:24:14 ubuntu kernel: [   16.600444]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
Nov 11 14:24:14 ubuntu kernel: [   16.600457]   domain 1: span 1,3 level MC
Nov 11 14:24:14 ubuntu kernel: [   16.600462]    groups: 1,3 (cpu_power = 1178)
Nov 11 14:24:14 ubuntu kernel: [   16.600472]    domain 2: span 0-3 level CPU
Nov 11 14:24:14 ubuntu kernel: [   16.600477]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
Nov 11 14:24:14 ubuntu kernel: [   16.600492] CPU2 attaching sched-domain:
Nov 11 14:24:14 ubuntu kernel: [   16.600497]  domain 0: span 0,2 level SIBLING
Nov 11 14:24:14 ubuntu kernel: [   16.600503]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
Nov 11 14:24:14 ubuntu kernel: [   16.600515]   domain 1: span 0,2 level MC
Nov 11 14:24:14 ubuntu kernel: [   16.600520]    groups: 0,2 (cpu_power = 1178)
Nov 11 14:24:14 ubuntu kernel: [   16.600530]    domain 2: span 0-3 level CPU
Nov 11 14:24:14 ubuntu kernel: [   16.600535]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
Nov 11 14:24:14 ubuntu kernel: [   16.600549] CPU3 attaching sched-domain:
Nov 11 14:24:14 ubuntu kernel: [   16.600555]  domain 0: span 1,3 level SIBLING
Nov 11 14:24:14 ubuntu kernel: [   16.600560]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
Nov 11 14:24:14 ubuntu kernel: [   16.600572]   domain 1: span 1,3 level MC
Nov 11 14:24:14 ubuntu kernel: [   16.600578]    groups: 1,3 (cpu_power = 1178)
Nov 11 14:24:14 ubuntu kernel: [   16.600587]    domain 2: span 0-3 level CPU
Nov 11 14:24:14 ubuntu kernel: [   16.600593]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
Nov 11 14:24:14 ubuntu gdm-simple-greeter[1176]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Nov 11 14:24:14 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1524 of process 1223 (n/a) owned by '119' RT at priority 5.
Nov 11 14:24:14 ubuntu rtkit-daemon[1231]: Supervising 2 threads of 1 processes of 1 users.
Nov 11 14:24:14 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1532 of process 1223 (n/a) owned by '119' RT at priority 5.
Nov 11 14:24:14 ubuntu rtkit-daemon[1231]: Supervising 3 threads of 1 processes of 1 users.
Nov 11 14:24:14 ubuntu acpid: client connected from 1538[113:121]
Nov 11 14:24:14 ubuntu acpid: 1 client rule loaded
Nov 11 14:24:14 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1539 of process 1223 (n/a) owned by '119' RT at priority 5.
Nov 11 14:24:14 ubuntu rtkit-daemon[1231]: Supervising 4 threads of 1 processes of 1 users.
Nov 11 14:24:16 ubuntu gdm-session-worker[1197]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Nov 11 14:24:19 ubuntu kernel: [   22.361289] eth0: no IPv6 routers present
Nov 11 14:24:22 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1633 of process 1633 (n/a) owned by '1000' high priority at nice level -11.
Nov 11 14:24:22 ubuntu rtkit-daemon[1231]: Supervising 5 threads of 2 processes of 2 users.
Nov 11 14:24:22 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 11 14:24:22 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 11 14:24:22 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1655 of process 1633 (n/a) owned by '1000' RT at priority 5.
Nov 11 14:24:22 ubuntu rtkit-daemon[1231]: Supervising 6 threads of 2 processes of 2 users.
Nov 11 14:24:23 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1656 of process 1633 (n/a) owned by '1000' RT at priority 5.
Nov 11 14:24:23 ubuntu rtkit-daemon[1231]: Supervising 7 threads of 2 processes of 2 users.
Nov 11 14:24:23 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1659 of process 1633 (n/a) owned by '1000' RT at priority 5.
Nov 11 14:24:23 ubuntu rtkit-daemon[1231]: Supervising 8 threads of 2 processes of 2 users.
Nov 11 14:24:23 ubuntu rtkit-daemon[1231]: Sucessfully made thread 1663 of process 1663 (n/a) owned by '1000' high priority at nice level -11.
Nov 11 14:24:23 ubuntu rtkit-daemon[1231]: Supervising 9 threads of 3 processes of 2 users.
Nov 11 14:24:23 ubuntu pulseaudio[1663]: pid.c: Daemon already running.
Nov 11 14:24:29 ubuntu ntpdate[1226]: adjust time server 91.189.94.4 offset 0.199642 sec
Nov 11 14:24:40 ubuntu NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 11 14:24:47 ubuntu kernel: [   49.920244] ppdev: user-space parallel port driver
Nov 11 14:24:51 ubuntu init: plymouth-stop pre-start process (2246) terminated with status 1
Nov 11 14:25:30 ubuntu AptDaemon: INFO: Initializing daemon
Nov 11 14:30:31 ubuntu AptDaemon: INFO: Quiting due to inactivity
Nov 11 14:30:31 ubuntu AptDaemon: INFO: Shutdown was requested
Nov 11 14:34:10 ubuntu anacron[1059]: Job `cron.weekly' started
Nov 11 14:34:10 ubuntu anacron[2379]: Updated timestamp for job `cron.weekly' to 2010-11-11
Nov 11 14:34:24 ubuntu kernel: [  626.995722] lo: Disabled Privacy Extensions
Nov 11 14:36:44 ubuntu anacron[1059]: Job `cron.weekly' terminated
```

Also what does this mean:

Init: plymouth main spalsh process (96) killed by SEGV signal
init: Plymouth-splash main process (134) terminated with status 2

---

### Post by cucu007 on 2010-11-11
Is this a clean system or an upgraded. Are you getting the freeze in the console/shell or while using the window manager. Looks like something is failing as gdm loads, have you updated your video drivers and patch whatever window manager u using. Can you tell us about when this started happening in order to further troubleshoot. Thank you.

---

### Post by waloshin on 2010-11-11
Was running server 10.10 then installed the desktop version through apt-get, it seems to freeze with google chrome.

---

### Post by cucu007 on 2010-11-11
You probably be better ff doing a clean install of the desktop since the server version may have left some strip elements within the upgrade. Always run either or do not try migrating from one to another, that's my two cents. You can always look at the logs and see if you see anything suspicious.

---

