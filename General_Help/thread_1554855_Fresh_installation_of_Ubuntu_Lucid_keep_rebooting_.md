---
title: "Fresh installation of Ubuntu Lucid keep rebooting without any reason"
date: 2010-08-17
forum: General Help
---

### Post by type8code0 on 2010-08-17
Hi all,

I'm very new to Ubuntu ... I'm using windows for several years and now getting boring with it. I'm trying something new and hopefully I'll get support from the whole Ubuntu community.

Thanks

This is my first post here and also my first problem with Ubuntu.

The problem is my pc keep rebooting after a few minutes without any reason.
If you need more information, please let me know.
Thanks in advance :)

```
type8code0@desktop:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

```

lspci
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
05:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)

```


dmesg
```
[    0.206257] pci 0000:00:1f.2: reg 14 io port: [0x30e4-0x30e7]
[    0.206267] pci 0000:00:1f.2: reg 18 io port: [0x30c0-0x30c7]
[    0.206277] pci 0000:00:1f.2: reg 1c io port: [0x30e0-0x30e3]
[    0.206287] pci 0000:00:1f.2: reg 20 io port: [0x30a0-0x30af]
[    0.206322] pci 0000:00:1f.2: PME# supported from D3hot
[    0.206329] pci 0000:00:1f.2: PME# disabled
[    0.206389] pci 0000:00:1f.3: reg 20 io port: [0x3000-0x301f]
[    0.206463] pci 0000:01:00.0: reg 10 32bit mmio pref: [0x60000000-0x6fffffff]
[    0.206473] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.206483] pci 0000:01:00.0: reg 18 32bit mmio: [0x70110000-0x7011ffff]
[    0.206507] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfffe0000-0xffffffff]
[    0.206536] pci 0000:01:00.0: supports D1 D2
[    0.206580] pci 0000:01:00.1: reg 10 32bit mmio: [0x70100000-0x7010ffff]
[    0.206634] pci 0000:01:00.1: supports D1 D2
[    0.206699] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.206706] pci 0000:00:01.0: bridge 32bit mmio: [0x70100000-0x701fffff]
[    0.206714] pci 0000:00:01.0: bridge 64bit mmio pref: [0x60000000-0x6fffffff]
[    0.206780] pci 0000:00:1c.0: bridge 32bit mmio: [0x70300000-0x703fffff]
[    0.206849] pci 0000:00:1c.2: bridge 32bit mmio: [0x70400000-0x704fffff]
[    0.206915] pci 0000:00:1c.3: bridge 32bit mmio: [0x70500000-0x705fffff]
[    0.206981] pci 0000:05:08.0: reg 10 32bit mmio: [0x70000000-0x70000fff]
[    0.206993] pci 0000:05:08.0: reg 14 io port: [0x1000-0x103f]
[    0.207049] pci 0000:05:08.0: supports D1 D2
[    0.207053] pci 0000:05:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.207060] pci 0000:05:08.0: PME# disabled
[    0.207109] pci 0000:00:1e.0: transparent bridge
[    0.207115] pci 0000:00:1e.0: bridge io port: [0x1000-0x1fff]
[    0.207122] pci 0000:00:1e.0: bridge 32bit mmio: [0x70000000-0x700fffff]
[    0.207158] pci_bus 0000:00: on NUMA node 0
[    0.207165] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.207500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.207876] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.208019] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.208136] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.215024] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.215221] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.215408] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.215596] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.215784] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.215967] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.216167] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.216367] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11 12)
[    0.216592] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.216601] vgaarb: loaded
[    0.216828] SCSI subsystem initialized
[    0.216962] libata version 3.00 loaded.
[    0.217103] usbcore: registered new interface driver usbfs
[    0.217129] usbcore: registered new interface driver hub
[    0.217177] usbcore: registered new device driver usb
[    0.217431] ACPI: WMI: Mapper loaded
[    0.217436] PCI: Using ACPI for IRQ routing
[    0.217700] NetLabel: Initializing
[    0.217704] NetLabel:  domain hash size = 128
[    0.217707] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.217729] NetLabel:  unlabeled traffic allowed by default
[    0.217866] hpet clockevent registered
[    0.217872] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.217880] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.217891] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.220200] Switching to clocksource tsc
[    0.223618] AppArmor: AppArmor Filesystem Enabled
[    0.223644] pnp: PnP ACPI init
[    0.223668] ACPI: bus type pnp registered
[    0.228204] pnp: PnP ACPI: found 11 devices
[    0.228209] ACPI: ACPI bus type pnp unregistered
[    0.228215] PnPBIOS: Disabled by ACPI PNP
[    0.228234] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.228241] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.228247] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.228253] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.228259] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.228264] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.228270] system 00:01: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.228276] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[    0.228282] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.228297] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.228304] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.228310] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.263187] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    0.263275] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.263284] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.263294] pci 0000:00:01.0:   MEM window: 0x70100000-0x701fffff
[    0.263302] pci 0000:00:01.0:   PREFETCH window: 0x00000060000000-0x0000006fffffff
[    0.263311] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.263317] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff
[    0.263325] pci 0000:00:1c.0:   MEM window: 0x70300000-0x703fffff
[    0.263332] pci 0000:00:1c.0:   PREFETCH window: 0x00000070600000-0x000000707fffff
[    0.263342] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.263348] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.263356] pci 0000:00:1c.2:   MEM window: 0x70400000-0x704fffff
[    0.263363] pci 0000:00:1c.2:   PREFETCH window: 0x00000070800000-0x000000709fffff
[    0.263372] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.263378] pci 0000:00:1c.3:   IO window: 0x6000-0x6fff
[    0.263386] pci 0000:00:1c.3:   MEM window: 0x70500000-0x705fffff
[    0.263394] pci 0000:00:1c.3:   PREFETCH window: 0x00000070a00000-0x00000070bfffff
[    0.263404] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.263410] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.263418] pci 0000:00:1e.0:   MEM window: 0x70000000-0x700fffff
[    0.263424] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.263443]   alloc irq_desc for 16 on node -1
[    0.263447]   alloc kstat_irqs on node -1
[    0.263457] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.263465] pci 0000:00:01.0: setting latency timer to 64
[    0.263479]   alloc irq_desc for 17 on node -1
[    0.263483]   alloc kstat_irqs on node -1
[    0.263490] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.263497] pci 0000:00:1c.0: setting latency timer to 64
[    0.263510]   alloc irq_desc for 18 on node -1
[    0.263514]   alloc kstat_irqs on node -1
[    0.263521] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.263528] pci 0000:00:1c.2: setting latency timer to 64
[    0.263541]   alloc irq_desc for 19 on node -1
[    0.263545]   alloc kstat_irqs on node -1
[    0.263552] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.263559] pci 0000:00:1c.3: setting latency timer to 64
[    0.263571] pci 0000:00:1e.0: setting latency timer to 64
[    0.263582] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.263589] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.263596] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.263603] pci_bus 0000:01: resource 1 mem: [0x70100000-0x701fffff]
[    0.263609] pci_bus 0000:01: resource 2 pref mem [0x60000000-0x6fffffff]
[    0.263614] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.263619] pci_bus 0000:02: resource 1 mem: [0x70300000-0x703fffff]
[    0.263624] pci_bus 0000:02: resource 2 pref mem [0x70600000-0x707fffff]
[    0.263629] pci_bus 0000:03: resource 0 io:  [0x5000-0x5fff]
[    0.263634] pci_bus 0000:03: resource 1 mem: [0x70400000-0x704fffff]
[    0.263639] pci_bus 0000:03: resource 2 pref mem [0x70800000-0x709fffff]
[    0.263644] pci_bus 0000:04: resource 0 io:  [0x6000-0x6fff]
[    0.263649] pci_bus 0000:04: resource 1 mem: [0x70500000-0x705fffff]
[    0.263654] pci_bus 0000:04: resource 2 pref mem [0x70a00000-0x70bfffff]
[    0.263659] pci_bus 0000:05: resource 0 io:  [0x1000-0x1fff]
[    0.263664] pci_bus 0000:05: resource 1 mem: [0x70000000-0x700fffff]
[    0.263669] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.263673] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.263736] NET: Registered protocol family 2
[    0.263917] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.264514] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.265151] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.265461] TCP: Hash tables configured (established 131072 bind 65536)
[    0.265466] TCP reno registered
[    0.265607] NET: Registered protocol family 1
[    0.265864] pci 0000:01:00.0: Boot video device
[    0.265885] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling
[    0.266180] cpufreq-nforce2: No nForce2 chipset.
[    0.266232] Scanning for low memory corruption every 60 seconds
[    0.266433] audit: initializing netlink socket (disabled)
[    0.266447] type=2000 audit(1282075724.263:1): initialized
[    0.278684] highmem bounce pool size: 64 pages
[    0.278694] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.281692] VFS: Disk quotas dquot_6.5.2
[    0.281807] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.282979] fuse init (API version 7.13)
[    0.283163] msgmni has been set to 1703
[    0.283560] alg: No test for stdrng (krng)
[    0.283672] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.283678] io scheduler noop registered
[    0.283682] io scheduler anticipatory registered
[    0.283686] io scheduler deadline registered
[    0.283768] io scheduler cfq registered (default)
[    0.283999]   alloc irq_desc for 24 on node -1
[    0.284004]   alloc kstat_irqs on node -1
[    0.284018] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.284029] pcieport 0000:00:01.0: setting latency timer to 64
[    0.284188]   alloc irq_desc for 25 on node -1
[    0.284192]   alloc kstat_irqs on node -1
[    0.284204] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.284216] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.284395]   alloc irq_desc for 26 on node -1
[    0.284400]   alloc kstat_irqs on node -1
[    0.284412] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.284425] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.284610]   alloc irq_desc for 27 on node -1
[    0.284614]   alloc kstat_irqs on node -1
[    0.284626] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.284638] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.284793] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.284952] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.285110] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.285123] ACPI: Sleep Button [SLPB]
[    0.285231] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.285237] ACPI: Power Button [PWRF]
[    0.285704] processor LNXCPU:00: registered as cooling_device0
[    0.285850] processor LNXCPU:01: registered as cooling_device1
[    0.290977] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.291101] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.291700] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.293782] brd: module loaded
[    0.294776] loop: module loaded
[    0.294932] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.295109] ata_piix 0000:00:1f.1: version 2.13
[    0.295128] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.295186] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.295303] scsi0 : ata_piix
[    0.295437] scsi1 : ata_piix
[    0.295529] isapnp: Scanning for PnP cards...
[    0.296302] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
[    0.296308] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
[    0.296342] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.296350] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.296402] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.296468] scsi2 : ata_piix
[    0.296558] scsi3 : ata_piix
[    0.296813] ata3: SATA max UDMA/133 cmd 0x30c8 ctl 0x30e4 bmdma 0x30a0 irq 19
[    0.296819] ata4: SATA max UDMA/133 cmd 0x30c0 ctl 0x30e0 bmdma 0x30a8 irq 19
[    0.297437] Fixed MDIO Bus: probed
[    0.297500] PPP generic driver version 2.4.2
[    0.297566] tun: Universal TUN/TAP device driver, 1.6
[    0.297570] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.297716] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.297743]   alloc irq_desc for 23 on node -1
[    0.297748]   alloc kstat_irqs on node -1
[    0.297757] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.297778] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.297784] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.297838] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.297862] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.297876] ehci_hcd 0000:00:1d.7: debug port 1
[    0.301768] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.301814] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x70204000
[    0.349209] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.349419] usb usb1: configuration #1 chosen from 1 choice
[    0.349479] hub 1-0:1.0: USB hub found
[    0.349494] hub 1-0:1.0: 8 ports detected
[    0.349615] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.349648] uhci_hcd: USB Universal Host Controller Interface driver
[    0.349711] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.349724] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.349730] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.349797] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.349830] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    0.349994] usb usb2: configuration #1 chosen from 1 choice
[    0.350052] hub 2-0:1.0: USB hub found
[    0.350064] hub 2-0:1.0: 2 ports detected
[    0.350142] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.350152] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.350158] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.350227] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.350257] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    0.350419] usb usb3: configuration #1 chosen from 1 choice
[    0.350472] hub 3-0:1.0: USB hub found
[    0.350484] hub 3-0:1.0: 2 ports detected
[    0.350565] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.350578] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.350584] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.350643] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.350684] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    0.350854] usb usb4: configuration #1 chosen from 1 choice
[    0.350906] hub 4-0:1.0: USB hub found
[    0.350918] hub 4-0:1.0: 2 ports detected
[    0.351010] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.351020] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.351026] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.351088] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.351127] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00003020
[    0.351299] usb usb5: configuration #1 chosen from 1 choice
[    0.351351] hub 5-0:1.0: USB hub found
[    0.351362] hub 5-0:1.0: 2 ports detected
[    0.351546] PNP: No PS/2 controller found. Probing ports directly.
[    0.368713] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.368728] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.368902] mice: PS/2 mouse device common for all mice
[    0.369070] rtc_cmos 00:03: RTC can wake from S4
[    0.369134] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.369165] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.369364] device-mapper: uevent: version 1.0.3
[    0.375671] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.383832] device-mapper: multipath: version 1.1.0 loaded
[    0.383838] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.384042] EISA: Probing bus 0 at eisa.0
[    0.384051] Cannot allocate resource for EISA slot 1
[    0.384055] Cannot allocate resource for EISA slot 2
[    0.384059] Cannot allocate resource for EISA slot 3
[    0.384063] Cannot allocate resource for EISA slot 4
[    0.384067] Cannot allocate resource for EISA slot 5
[    0.384070] Cannot allocate resource for EISA slot 6
[    0.384081] EISA: Detected 0 cards.
[    0.397169] cpuidle: using governor ladder
[    0.397173] cpuidle: using governor menu
[    0.398001] TCP cubic registered
[    0.398236] NET: Registered protocol family 10
[    0.399057] lo: Disabled Privacy Extensions
[    0.399755] NET: Registered protocol family 17
[    0.401721] Using IPI No-Shortcut mode
[    0.401865] PM: Resume from disk failed.
[    0.401883] registered taskstats version 1
[    0.402292]   Magic number: 6:476:144
[    0.402315] block ram9: hash matches
[    0.402352] acpi device:15: hash matches
[    0.402397] rtc_cmos 00:03: setting system clock to 2010-08-17 20:08:44 UTC (1282075724)
[    0.402402] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.402405] EDD information not available.
[    0.441874] ata2: port disabled. ignoring.
[    0.490505] Freeing initrd memory: 7786k freed
[    0.559702] ata1.01: ATAPI: HL-DT-ST DVDRAM GDA-4120B, P008, max UDMA/33
[    0.575657] ata1.01: configured for UDMA/33
[    0.659506] isapnp: No Plug & Play device found
[    0.663485] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GDA-4120B P008 PQ: 0 ANSI: 5
[    0.676271] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.676276] Uniform CD-ROM driver Revision: 3.20
[    0.676419] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    0.676500] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    0.686286] ata4.00: ATA-7: ST3250820AS, 3.AAE, max UDMA/133
[    0.686291] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.752941] ata4.00: configured for UDMA/133
[    0.753064] scsi 3:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
[    0.753244] sd 3:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.753255] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    0.753355] sd 3:0:0:0: [sda] Write Protect is off
[    0.753360] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.753399] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.753599]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3
[    0.823851] sd 3:0:0:0: [sda] Attached SCSI disk
[    0.823868] Freeing unused kernel memory: 660k freed
[    0.824394] Write protecting the kernel text: 4680k
[    0.824448] Write protecting the kernel read-only data: 1840k
[    0.847773] udev: starting version 151
[    0.967397] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    1.039559] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.039565] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.039622]   alloc irq_desc for 20 on node -1
[    1.039626]   alloc kstat_irqs on node -1
[    1.039638] e100 0000:05:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.063224] e100 0000:05:08.0: PME# disabled
[    1.064195] e100: eth0: e100_probe: addr 0x70000000, irq 20, MAC addr 00:16:76:59:3b:ae
[    1.140975] usb 2-1: configuration #1 chosen from 1 choice
[    1.166888] usbcore: registered new interface driver hiddev
[    1.166962] usbcore: registered new interface driver usbhid
[    1.166967] usbhid: v2.6:USB HID core driver
[    1.182336] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    1.182738] a4tech 0003:09DA:000A.0001: input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:1d.0-1/input0
[    1.392522] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    1.520400] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    1.520407] EXT4-fs (sda6): write access will be enabled during recovery
[    1.643831] usb 4-1: configuration #1 chosen from 1 choice
[    1.694017] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input4
[    1.694123] generic-usb 0003:1241:1503.0002: input,hidraw1: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.2-1/input0
[    1.783828] input:   USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input5
[    1.783936] generic-usb 0003:1241:1503.0003: input,hidraw2: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.2-1/input1
[   11.948589] EXT4-fs (sda6): orphan cleanup on readonly fs
[   11.948601] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2623455
[   11.948686] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2623318
[   11.948716] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332391
[   11.948745] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332390
[   11.948771] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332389
[   11.948796] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332388
[   11.948821] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332387
[   11.948846] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332386
[   11.948871] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332385
[   11.948897] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332384
[   11.948925] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 131435
[   11.949379] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332382
[   11.949406] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138958
[   11.949484] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332381
[   11.949510] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332380
[   11.949542] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332343
[   11.949569] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1318016
[   11.949597] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1311267
[   11.949651] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332377
[   11.949678] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1835754
[   11.961104] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1332342
[   11.961162] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1311002
[   11.961191] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138834
[   11.961263] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138832
[   11.961289] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138829
[   11.961315] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138793
[   11.961341] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1311261
[   11.961368] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 1310769
[   11.961402] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138799
[   11.961418] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2623755
[   11.961445] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2623754
[   11.961501] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138797
[   11.961527] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138796
[   11.961541] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138794
[   11.961567] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138792
[   11.961592] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138770
[   11.961608] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138769
[   11.961634] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 138750
[   11.961651] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 2097169
[   11.961690] EXT4-fs (sda6): 39 orphan inodes deleted
[   11.961695] EXT4-fs (sda6): recovery complete
[   12.748578] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   19.250701] udev: starting version 151
[   19.289926] Adding 2561016k swap on /dev/sda7.  Priority:-1 extents:1 across:2561016k 
[   19.569790] intel_rng: Firmware space is locked read-only. If you can't or
[   19.569794] intel_rng: don't want to disable this in firmware setup, and if
[   19.569797] intel_rng: you are certain that your system has a functional
[   19.569799] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   19.573406] Linux agpgart interface v0.103
[   19.675665] lp: driver loaded but no devices found
[   19.681764] parport_pc 00:08: reported by Plug and Play ACPI
[   19.681828] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   19.764367] [drm] Initialized drm 1.1.0 20060810
[   19.800760] lp0: using parport0 (interrupt-driven).
[   19.805653] ppdev: user-space parallel port driver
[   19.834779] type=1505 audit(1282046943.929:2):  operation="profile_load" pid=560 name="/sbin/dhclient3"
[   19.835601] type=1505 audit(1282046943.929:3):  operation="profile_load" pid=560 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.836049] type=1505 audit(1282046943.933:4):  operation="profile_load" pid=560 name="/usr/lib/connman/scripts/dhclient-script"
[   19.907959] [drm] radeon defaulting to kernel modesetting.
[   19.907966] [drm] radeon kernel modesetting enabled.
[   19.908053] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.908063] radeon 0000:01:00.0: setting latency timer to 64
[   19.912208] [drm] radeon: Initializing kernel modesetting.
[   19.925983] [drm] register mmio base: 0x70110000
[   19.925988] [drm] register mmio size: 65536
[   19.928342] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   19.928365] [drm] Generation 2 PCI interface, using max accessible memory
[   19.928370] [drm] radeon: VRAM 256M
[   19.928374] [drm] radeon: VRAM from 0x00000000 to 0x0FFFFFFF
[   19.928377] [drm] radeon: GTT 512M
[   19.928381] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   19.928430]   alloc irq_desc for 28 on node -1
[   19.928434]   alloc kstat_irqs on node -1
[   19.928451] radeon 0000:01:00.0: irq 28 for MSI/MSI-X
[   19.928459] [drm] radeon: using MSI.
[   19.928491] [drm] radeon: irq initialized.
[   19.929226] [drm] Detected VRAM RAM=256M, BAR=256M
[   19.929232] [drm] RAM width 128bits DDR
[   19.929338] [TTM] Zone  kernel: Available graphics memory: 440224 kiB.
[   19.929343] [TTM] Zone highmem: Available graphics memory: 771182 kiB.
[   19.929367] [drm] radeon: 256M of VRAM memory ready
[   19.929371] [drm] radeon: 512M of GTT memory ready.
[   19.929396] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   19.930143] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   19.930199] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   19.930215] [drm] radeon: cp idle (0x10000C03)
[   19.930278] [drm] Loading R300 Microcode
[   19.930285] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   19.958004] [drm] radeon: ring at 0x0000000020000000
[   19.958031] [drm] ring test succeeded in 0 usecs
[   19.958331] [drm] radeon: ib pool ready.
[   19.958454] [drm] ib test succeeded in 0 usecs
[   19.958626] [drm] Default TV standard: NTSC
[   19.958630] [drm] 27.000000000 MHz TV ref clk
[   19.958636] [drm] DFP table revision: 4
[   19.958734] [drm] Default TV standard: NTSC
[   19.958738] [drm] 27.000000000 MHz TV ref clk
[   19.958797] [drm] Radeon Display Connectors
[   19.958801] [drm] Connector 0:
[   19.958804] [drm]   VGA
[   19.958809] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   19.958812] [drm]   Encoders:
[   19.958815] [drm]     CRT1: INTERNAL_DAC1
[   19.958819] [drm] Connector 1:
[   19.958822] [drm]   DVI-I
[   19.958825] [drm]   HPD1
[   19.958829] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   19.958833] [drm]   Encoders:
[   19.958836] [drm]     CRT2: INTERNAL_DAC2
[   19.958839] [drm]     DFP1: INTERNAL_TMDS1
[   19.958843] [drm] Connector 2:
[   19.958847] [drm]   S-video
[   19.958850] [drm]   Encoders:
[   19.958853] [drm]     TV1: INTERNAL_DAC2
[   20.104535]   alloc irq_desc for 22 on node -1
[   20.104542]   alloc kstat_irqs on node -1
[   20.104554] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.104606] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.203869] type=1505 audit(1282046944.297:5):  operation="profile_load" pid=687 name="/usr/share/gdm/guest-session/Xsession"
[   20.223117] type=1505 audit(1282046944.317:6):  operation="profile_replace" pid=691 name="/sbin/dhclient3"
[   20.223942] type=1505 audit(1282046944.317:7):  operation="profile_replace" pid=691 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.224433] type=1505 audit(1282046944.321:8):  operation="profile_replace" pid=691 name="/usr/lib/connman/scripts/dhclient-script"
[   20.238518] type=1505 audit(1282046944.333:9):  operation="profile_load" pid=692 name="/usr/bin/evince"
[   20.289278] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   20.289558] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   20.289816] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.290059] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.290302] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.290539] input: HDA Intel Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   20.290780] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   20.292930] type=1505 audit(1282046944.389:10):  operation="profile_load" pid=692 name="/usr/bin/evince-previewer"
[   20.300683] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.304154] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   20.312550] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.327828] type=1505 audit(1282046944.421:11):  operation="profile_load" pid=692 name="/usr/bin/evince-thumbnailer"
[   20.508688] [drm] fb mappable at 0x600C0000
[   20.508692] [drm] vram apper at 0x60000000
[   20.508694] [drm] size 4177920
[   20.508697] [drm] fb depth is 24
[   20.508699] [drm]    pitch is 5440
[   20.508820] fb0: radeondrmfb frame buffer device
[   20.508824] registered panic notifier
[   20.508835] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   20.512490] vga16fb: initializing
[   20.512496] vga16fb: mapped to 0xc00a0000
[   20.512503] vga16fb: not registering due to another framebuffer present
[   20.588930] Console: switching to colour frame buffer device 170x48
[   22.338477] CPU0 attaching NULL sched-domain.
[   22.338487] CPU1 attaching NULL sched-domain.
[   22.360131] CPU0 attaching sched-domain:
[   22.360139]  domain 0: span 0-1 level SIBLING
[   22.360145]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   22.360157]   domain 1: span 0-1 level MC
[   22.360162]    groups: 0-1 (cpu_power = 1178)
[   22.360174] CPU1 attaching sched-domain:
[   22.360178]  domain 0: span 0-1 level SIBLING
[   22.360183]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   22.360194]   domain 1: span 0-1 level MC
[   22.360198]    groups: 0-1 (cpu_power = 1178)
[   23.539383] CPU0 attaching NULL sched-domain.
[   23.539393] CPU1 attaching NULL sched-domain.
[   23.556662] CPU0 attaching sched-domain:
[   23.556670]  domain 0: span 0-1 level SIBLING
[   23.556675]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   23.556688]   domain 1: span 0-1 level MC
[   23.556693]    groups: 0-1 (cpu_power = 1178)
[   23.556703] CPU1 attaching sched-domain:
[   23.556707]  domain 0: span 0-1 level SIBLING
[   23.556712]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   23.556723]   domain 1: span 0-1 level MC
[   23.556727]    groups: 0-1 (cpu_power = 1178)
[   30.416006] eth0: no IPv6 routers present
type8code0@desktop:~$ 
```

---

### Post by mitsios on 2010-08-17
Try running a memtest. My desktop kept rebooting because of bad RAM.

---

### Post by type8code0 on 2010-08-17
> **mitsios said:**
> Try running a memtest. My desktop kept rebooting because of bad RAM.
Thanks for the suggestion. This is the message that I received. I guess my RAM is ok. Anything else I should try?
```
Pass successful, no errors
```

---

### Post by ercferret18 on 2010-08-17
does it go through a proper reboot, or a hard (sudden) reboot?

---

### Post by type8code0 on 2010-08-17
> **ercferret18 said:**
> does it go through a proper reboot, or a hard (sudden) reboot?
it goes to hard (sudden) reboot. As you can see in the log below, it was crashed so many times
> type8code0@desktop:~$ last
type8code0 pts/2 :0.0 Tue Aug 17 20:10 still logged in
type8code0 pts/1 :0.0 Tue Aug 17 20:10 - 20:10 (00:00)
type8code0 pts/0 :0.0 Tue Aug 17 20:10 still logged in
type8code0 tty7 :0 Tue Aug 17 20:09 still logged in
reboot system boot 2.6.32-24-generi Tue Aug 17 20:09 - 20:36 (00:27)
type8code0 pts/1 :0.0 Tue Aug 17 18:40 - crash (01:28)
type8code0 pts/0 :0.0 Tue Aug 17 18:28 - crash (01:40)
type8code0 tty7 :0 Tue Aug 17 18:27 - crash (01:41)
reboot system boot 2.6.32-24-generi Tue Aug 17 18:26 - 20:36 (02:09)
reboot system boot 2.6.32-24-generi Fri Aug 13 20:22 - 20:36 (4+00:13)
type8code0 pts/1 :0.0 Fri Aug 13 17:59 - crash (02:23)
type8code0 pts/0 :0.0 Fri Aug 13 17:58 - crash (02:23)
type8code0 tty7 :0 Fri Aug 13 17:58 - crash (02:24)
reboot system boot 2.6.32-24-generi Fri Aug 13 17:58 - 20:36 (4+02:37)
reboot system boot 2.6.32-24-generi Fri Aug 13 17:53 - 20:36 (4+02:42)
reboot system boot 2.6.32-24-generi Fri Aug 13 17:51 - 20:36 (4+02:44)
type8code0 tty7 :0 Thu Aug 12 23:09 - crash (18:42)
reboot system boot 2.6.32-24-generi Thu Aug 12 23:07 - 20:36 (4+21:28)
type8code0 pts/0 :0.0 Thu Aug 12 23:06 - 23:06 (00:00)
type8code0 tty7 :0 Thu Aug 12 23:05 - 23:07 (00:01)
reboot system boot 2.6.32-24-generi Thu Aug 12 23:05 - 23:07 (00:01)
reboot system boot 2.6.32-24-generi Thu Aug 12 23:03 - 23:07 (00:03)
type8code0 pts/0 :0.0 Thu Aug 12 18:53 - crash (04:10)
type8code0 tty7 :0 Thu Aug 12 18:52 - crash (04:11)
reboot system boot 2.6.32-24-generi Thu Aug 12 18:52 - 23:07 (04:14)
type8code0 tty8 :0 Thu Aug 12 05:58 - crash (12:54)
type8code0 tty7 :0 Thu Aug 12 05:56 - 05:57 (00:01)
reboot system boot 2.6.32-24-generi Thu Aug 12 05:53 - 23:07 (17:13)
type8code0 pts/0 :0.0 Wed Aug 11 23:26 - crash (06:27)
type8code0 pts/1 :0.0 Wed Aug 11 23:18 - crash (06:35)
type8code0 pts/1 :0.0 Wed Aug 11 22:51 - 22:51 (00:00)
type8code0 pts/0 :0.0 Wed Aug 11 22:47 - 23:18 (00:31)
type8code0 tty7 :0 Wed Aug 11 22:46 - crash (07:07)
reboot system boot 2.6.32-24-generi Wed Aug 11 22:45 - 23:07 (1+00:21)
type8code0 pts/1 :0.0 Wed Aug 11 22:36 - crash (00:09)
type8code0 pts/0 :0.0 Wed Aug 11 22:35 - crash (00:10)
type8code0 pts/0 :0.0 Wed Aug 11 22:34 - 22:35 (00:00)
type8code0 tty7 :0 Wed Aug 11 22:33 - crash (00:12)
reboot system boot 2.6.32-24-generi Wed Aug 11 22:33 - 23:07 (1+00:33)
type8code0 pts/2 :0.0 Wed Aug 11 22:24 - crash (00:09)
type8code0 pts/1 :0.0 Wed Aug 11 22:15 - crash (00:17)
type8code0 pts/0 :0.0 Wed Aug 11 22:03 - crash (00:29)
type8code0 tty7 :0 Wed Aug 11 22:03 - crash (00:29)
reboot system boot 2.6.32-24-generi Wed Aug 11 21:59 - 23:07 (1+01:07)
type8code0 pts/0 :0.0 Wed Aug 11 20:16 - crash (01:43)
type8code0 pts/0 :0.0 Wed Aug 11 18:55 - 19:12 (00:16)
type8code0 tty7 :0 Wed Aug 11 18:54 - crash (03:05)
reboot system boot 2.6.32-24-generi Wed Aug 11 18:53 - 23:07 (1+04:13)
type8code0 tty7 :0 Wed Aug 11 06:17 - down (00:10)
reboot system boot 2.6.32-24-generi Wed Aug 11 06:15 - 06:27 (00:12)
type8code0 tty7 :0 Wed Aug 11 05:36 - down (00:38)
reboot system boot 2.6.32-21-generi Wed Aug 11 05:36 - 06:15 (00:39)
reboot system boot 2.6.32-21-generi Mon Aug 9 22:57 - 23:03 (00:06)
type8code0 pts/1 :0.0 Mon Aug 9 22:37 - 22:50 (00:12)
type8code0 pts/3 :0.0 Mon Aug 9 22:25 - crash (00:32)
type8code0 pts/1 :0.0 Mon Aug 9 22:24 - 22:25 (00:00)
type8code0 pts/2 :0.0 Mon Aug 9 22:24 - 22:24 (00:00)
type8code0 pts/1 :0.0 Mon Aug 9 22:21 - 22:24 (00:03)
type8code0 pts/1 :0.0 Mon Aug 9 22:21 - 22:21 (00:00)
type8code0 pts/0 :0.0 Mon Aug 9 22:17 - crash (00:39)
type8code0 tty7 :0 Mon Aug 9 22:17 - crash (00:39)
reboot system boot 2.6.32-21-generi Mon Aug 9 22:17 - 23:03 (00:46)
type8code0 pts/0 :0.0 Mon Aug 9 22:12 - down (00:03)
type8code0 tty7 :0 Mon Aug 9 22:12 - down (00:03)
reboot system boot 2.6.32-21-generi Mon Aug 9 22:11 - 22:16 (00:04)
type8code0 pts/0 :0.0 Mon Aug 9 22:09 - down (00:02)
type8code0 tty7 :0 Mon Aug 9 22:08 - down (00:02)
reboot system boot 2.6.32-21-generi Mon Aug 9 22:08 - 22:11 (00:03)
type8code0 pts/2 :2.0 Mon Aug 9 19:33 - crash (02:34)
type8code0 pts/2 :2.0 Mon Aug 9 18:32 - 18:32 (00:00)
type8code0 pts/1 :2.0 Mon Aug 9 18:24 - crash (03:43)
type8code0 pts/0 :2.0 Mon Aug 9 07:44 - crash (14:23)
type8code0 tty8 :2 Mon Aug 9 07:43 - crash (14:25)
type0code0 pts/0 :0.0 Mon Aug 9 07:39 - 07:42 (00:02)
type8code0 pts/0 :1.0 Mon Aug 9 07:19 - 07:38 (00:18)
type8code0 tty8 :1 Mon Aug 9 07:16 - 07:38 (00:21)
type0code0 tty7 :0 Mon Aug 9 07:06 - crash (15:01)
reboot system boot 2.6.32-21-generi Mon Aug 9 07:05 - 22:11 (15:05)
reboot system boot 2.6.32-21-generi Mon Aug 9 07:03 - 07:04 (00:00)
type8code0 pts/0 :1.0 Mon Aug 9 01:23 - 01:25 (00:02)
type8code0 tty7 :1 Mon Aug 9 01:22 - down (00:03)
type0code0 tty8 :0 Mon Aug 9 01:21 - down (00:04)
type8code0 tty7 :0 Mon Aug 9 01:19 - 01:21 (00:01)
reboot system boot 2.6.32-21-generi Mon Aug 9 01:18 - 01:25 (00:06) 

---

### Post by David Batty on 2010-08-17
Is the fan working? It might be an overheating problem.

---

### Post by ercferret18 on 2010-08-17
if you also have windows installed... does windows crash periodically?

---

### Post by type8code0 on 2010-08-18
> **David Batty said:**
> Is the fan working? It might be an overheating problem.
yes, the fan is working. 
May I know what makes you think that this is fan problem? Did you found something from the log that I attached here

---

### Post by type8code0 on 2010-08-18
> **ercferret18 said:**
> if you also have windows installed... does windows crash periodically?
Yes, I have windows XP installed without any drivers. So I don't really use it. As far as I know, this windows never crash

---

### Post by David Batty on 2010-08-18
The reason why I asked about the fan is because I have noticed some users complaining that their fan didn't work using Ubuntu on a laptop. I don't think this is an issue on desktops as the fan is not reliant on the software. 
An overheating CPU can cause shutdown so your problem may be hardware related.

---

### Post by silbak04 on 2010-08-19
install lm-sensors and then run ```
sudo sensors-detect 
cat /proc/acpi/thermal_zone/THRM/temperature 
```tell me what your output is

---

### Post by type8code0 on 2010-08-21
> **silbak04 said:**
> install lm-sensors and then run ```
sudo sensors-detect 
cat /proc/acpi/thermal_zone/THRM/temperature 
```tell me what your output is
Thanks silbak04 for your advise.. below is the output
> type8code0@desktop:~$ **sudo sensors-detect **
[sudo] password for type8code0: 
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# Board: Intel Corporation D945PLRN

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC8374L Super IO Sensors'                 
    (but not activated)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter:  (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter:  (i2c-1)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x49
Probing for `National Semiconductor LM75'...                No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: SMBus I801 adapter at 3000 (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85'...                No
Probing for `National Semiconductor LM96000 or PC8374L'...  No
Probing for `Analog Devices ADM1027'...                     No
Probing for `Analog Devices ADT7460 or ADT7463'...          No
Probing for `SMSC EMC6D100 or EMC6D101'...                  No
Probing for `SMSC EMC6D102'...                              No
Probing for `SMSC EMC6D103'...                              Success!
    (confidence 7, driver `lm85')
Probing for `Winbond WPCD377I'...                           No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     No
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `Analog Devices ADT7490'...                     No
Probing for `Andigilog aSC7611'...                          No
Probing for `Andigilog aSC7621'...                          No
Probing for `National Semiconductor LM87'...                No
Probing for `Analog Devices ADM1024'...                     No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83791D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Nuvoton W83795G/ADG'...                        No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `Texas Instruments THMC51'...                   No
Probing for `ITE IT8712F'...                                No
Probing for `SMSC DME1737'...                               No
Probing for `SMSC SCH5027D-NW'...                           No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791SD'...                           No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `lm85':
  * Bus `SMBus I801 adapter at 3000'
    Busdriver `i2c_i801', I2C address 0x2e
    Chip `SMSC EMC6D103' (confidence: 7)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Adapter drivers
i2c_i801
# Chip drivers
lm85
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK

type8code0@desktop:~$ 

There is nothing inside /proc/acpi/thermal_zone/ directory
> type8code0@desktop:~$ cd /proc/acpi/thermal_zone/
type8code0@desktop:/proc/acpi/thermal_zone$ ls
type8code0@desktop:/proc/acpi/thermal_zone$ ls -al
total 0
dr-xr-xr-x  2 root root 0 2010-08-21 20:42 .
dr-xr-xr-x 10 root root 0 2010-08-21 20:40 ..
type8code0@desktop:/proc/acpi/thermal_zone$ 

> type8code0@desktop:/proc/acpi/thermal_zone$ **/etc/init.d/module-init-tools start**
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service module-init-tools start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start module-init-tools
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.54" (uid=1000 pid=1730 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
type8code0@desktop:/proc/acpi/thermal_zone$ 

---

### Post by type8code0 on 2010-08-21
> **ercferret18 said:**
> does it go through a proper reboot, or a hard (sudden) reboot?
ercferret18, sorry, actually the screen just hang & freeze. No response at all...
So I have no choice expect to press reset button on the computer

---

