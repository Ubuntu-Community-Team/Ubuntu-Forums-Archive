---
title: "My last session was a GHOST!"
date: 2009-09-08
forum: General Help
---

### Post by lildigiman on 2009-09-08
Sorry for the catchy Title, but... Here I go.

I hadn't reboot this computer for about a week or so now, and I installed a ton of libraries and whatnot for GTKmm and C++ etc... and also did some Compiz settigns changes and some other UI changes, so then I decided to reboot just now just for fun. When I booted up, EVERYTHING was back to the way it was the previous time it had booted up. I had none of the new lirbaries or settings. I'm really confused. I'm going to reboot again too see if it does it again.

I guess I'd like to know why this happened and how to prevent it?

EDIT: The second reboot rebooted fine, but still did not bring back settings/stuff from previous boot.

---

### Post by lildigiman on 2009-09-09
Now I'm even more confused. I just restarted again just now, and it brought me back to the session I was missing, and now I don't have the most recent.

What is going on with my booting Ubuntu?

It is now asking me for Updates that I already installed earlier today before the reboot.

---

### Post by uylug on 2009-09-09
What? That is weird.
 
I don't know. Check the log for messages?
 
dmesg

---

### Post by lildigiman on 2009-09-09
Looks Normal?

> [    0.404228] Time: 20:40:44  Date: 09/09/09
[    0.404228] regulator: core version 0.5
[    0.404228] NET: Registered protocol family 16
[    0.404228] ACPI: bus type pci registered
[    0.404228] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.404228] PCI: Not using MMCONFIG.
[    0.404228] PCI: Using configuration type 1 for base access
[    0.404674] ACPI: EC: Look up EC in DSDT
[    0.418440] ACPI: Interpreter enabled
[    0.418442] ACPI: (supports S0 S1 S3 S4 S5)
[    0.418458] ACPI: Using IOAPIC for interrupt routing
[    0.418506] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.420855] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.428621] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.435761] ACPI: No dock devices found.
[    0.435817] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.435884] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.435886] pci 0000:00:01.0: PME# disabled
[    0.435943] pci 0000:00:1a.0: reg 20 io port: [0xc800-0xc81f]
[    0.435995] pci 0000:00:1a.1: reg 20 io port: [0xc880-0xc89f]
[    0.436051] pci 0000:00:1a.2: reg 20 io port: [0xcc00-0xcc1f]
[    0.436104] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe9ffc00-0xfe9fffff]
[    0.436136] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.436139] pci 0000:00:1a.7: PME# disabled
[    0.436172] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe9f8000-0xfe9fbfff]
[    0.436195] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.436198] pci 0000:00:1b.0: PME# disabled
[    0.436234] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.436236] pci 0000:00:1c.0: PME# disabled
[    0.436277] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.436279] pci 0000:00:1c.5: PME# disabled
[    0.436323] pci 0000:00:1d.0: reg 20 io port: [0xc080-0xc09f]
[    0.436374] pci 0000:00:1d.1: reg 20 io port: [0xc400-0xc41f]
[    0.436424] pci 0000:00:1d.2: reg 20 io port: [0xc480-0xc49f]
[    0.436478] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe9ff800-0xfe9ffbff]
[    0.436509] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.436513] pci 0000:00:1d.7: PME# disabled
[    0.436637] pci 0000:00:1f.2: reg 10 io port: [0xb000-0xb007]
[    0.436641] pci 0000:00:1f.2: reg 14 io port: [0xac00-0xac03]
[    0.436645] pci 0000:00:1f.2: reg 18 io port: [0xa880-0xa887]
[    0.436649] pci 0000:00:1f.2: reg 1c io port: [0xa800-0xa803]
[    0.436654] pci 0000:00:1f.2: reg 20 io port: [0xa480-0xa48f]
[    0.436658] pci 0000:00:1f.2: reg 24 io port: [0xa400-0xa40f]
[    0.436687] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe9ff400-0xfe9ff4ff]
[    0.436698] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.436732] pci 0000:00:1f.5: reg 10 io port: [0xc000-0xc007]
[    0.436736] pci 0000:00:1f.5: reg 14 io port: [0xbc00-0xbc03]
[    0.436740] pci 0000:00:1f.5: reg 18 io port: [0xb880-0xb887]
[    0.436745] pci 0000:00:1f.5: reg 1c io port: [0xb800-0xb803]
[    0.436749] pci 0000:00:1f.5: reg 20 io port: [0xb480-0xb48f]
[    0.436753] pci 0000:00:1f.5: reg 24 io port: [0xb400-0xb40f]
[    0.436790] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.436797] pci 0000:01:00.0: reg 18 64bit mmio: [0xfeae0000-0xfeaeffff]
[    0.436802] pci 0000:01:00.0: reg 20 io port: [0xd000-0xd0ff]
[    0.436809] pci 0000:01:00.0: reg 30 32bit mmio: [0xfeac0000-0xfeadffff]
[    0.436815] pci 0000:01:00.0: supports D1 D2
[    0.436841] pci 0000:01:00.1: reg 10 64bit mmio: [0xfeafc000-0xfeafffff]
[    0.436861] pci 0000:01:00.1: supports D1 D2
[    0.436897] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.436899] pci 0000:00:01.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.436902] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.436938] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.436984] pci 0000:02:00.0: reg 10 64bit mmio: [0xfebc0000-0xfebfffff]
[    0.436991] pci 0000:02:00.0: reg 18 io port: [0xec00-0xec7f]
[    0.437023] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.437027] pci 0000:02:00.0: PME# disabled
[    0.437066] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
[    0.437069] pci 0000:00:1c.5: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.437112] pci 0000:00:1e.0: transparent bridge
[    0.437132] bus 00 -> node 0
[    0.437137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.437344] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.437433] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.437574] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.437673] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.451857] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.451969] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.452085] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.452195] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.452304] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.452415] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.452524] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.452633] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.452741] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - A8, should be 9F [20080926]
[    0.452784] ACPI: WMI: Mapper loaded
[    0.452815] SCSI subsystem initialized
[    0.452815] libata version 3.00 loaded.
[    0.452815] usbcore: registered new interface driver usbfs
[    0.452815] usbcore: registered new interface driver hub
[    0.452815] usbcore: registered new device driver usb
[    0.452815] PCI: Using ACPI for IRQ routing
[    0.468010] Bluetooth: Core ver 2.13
[    0.468024] NET: Registered protocol family 31
[    0.468024] Bluetooth: HCI device and connection manager initialized
[    0.468024] Bluetooth: HCI socket layer initialized
[    0.468024] NET: Registered protocol family 8
[    0.468026] NET: Registered protocol family 20
[    0.468037] NetLabel: Initializing
[    0.468039] NetLabel:  domain hash size = 128
[    0.468040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.468055] NetLabel:  unlabeled traffic allowed by default
[    0.468089] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.468092] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.472065] AppArmor: AppArmor Filesystem Enabled
[    0.484010] pnp: PnP ACPI init
[    0.484019] ACPI: bus type pnp registered
[    0.486986] pnp: PnP ACPI: found 17 devices
[    0.486987] ACPI: ACPI bus type pnp unregistered
[    0.486994] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.486999] system 00:07: ioport range 0x290-0x29f has been reserved
[    0.487005] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.487007] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.487008] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.487010] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.487012] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.487013] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.487015] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.487019] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
[    0.487023] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.487025] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.487029] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.487033] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.487034] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.487036] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.487037] system 00:10: iomem range 0x100000-0xcfffffff could not be reserved
[    0.491658] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.491660] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.491663] pci 0000:00:01.0:   MEM window: 0xfea00000-0xfeafffff
[    0.491665] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.491669] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.491670] pci 0000:00:1c.0:   IO window: disabled
[    0.491673] pci 0000:00:1c.0:   MEM window: disabled
[    0.491676] pci 0000:00:1c.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.491680] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.491682] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
[    0.491686] pci 0000:00:1c.5:   MEM window: 0xfeb00000-0xfebfffff
[    0.491689] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.491693] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.491694] pci 0000:00:1e.0:   IO window: disabled
[    0.491697] pci 0000:00:1e.0:   MEM window: disabled
[    0.491700] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.491710] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.491712] pci 0000:00:01.0: setting latency timer to 64
[    0.491718] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.491721] pci 0000:00:1c.0: setting latency timer to 64
[    0.491726] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.491729] pci 0000:00:1c.5: setting latency timer to 64
[    0.491733] pci 0000:00:1e.0: setting latency timer to 64
[    0.491736] bus: 00 index 0 io port: [0x00-0xffff]
[    0.491737] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.491738] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.491740] bus: 01 index 1 mmio: [0xfea00000-0xfeafffff]
[    0.491741] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.491742] bus: 01 index 3 mmio: [0x0-0x0]
[    0.491743] bus: 03 index 0 mmio: [0x0-0x0]
[    0.491744] bus: 03 index 1 mmio: [0x0-0x0]
[    0.491745] bus: 03 index 2 mmio: [0xfdf00000-0xfdffffff]
[    0.491747] bus: 03 index 3 mmio: [0x0-0x0]
[    0.491748] bus: 02 index 0 io port: [0xe000-0xefff]
[    0.491749] bus: 02 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.491750] bus: 02 index 2 mmio: [0x0-0x0]
[    0.491751] bus: 02 index 3 mmio: [0x0-0x0]
[    0.491752] bus: 04 index 0 mmio: [0x0-0x0]
[    0.491753] bus: 04 index 1 mmio: [0x0-0x0]
[    0.491754] bus: 04 index 2 mmio: [0x0-0x0]
[    0.491755] bus: 04 index 3 io port: [0x00-0xffff]
[    0.491757] bus: 04 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.491763] NET: Registered protocol family 2
[    0.500649] Switched to high resolution mode on CPU 1
[    0.504005] Switched to high resolution mode on CPU 0
[    0.524059] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.524405] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.525834] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.526289] TCP: Hash tables configured (established 262144 bind 65536)
[    0.526291] TCP reno registered
[    0.536125] NET: Registered protocol family 1
[    0.536223] checking if image is initramfs... it is
[    1.068576] Freeing initrd memory: 7754k freed
[    1.071310] audit: initializing netlink socket (disabled)
[    1.071333] type=2000 audit(1252528844.068:1): initialized
[    1.077923] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.078814] VFS: Disk quotas dquot_6.5.1
[    1.078851] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.079252] fuse init (API version 7.10)
[    1.079313] msgmni has been set to 7798
[    1.079433] alg: No test for stdrng (krng)
[    1.079440] io scheduler noop registered
[    1.079442] io scheduler anticipatory registered
[    1.079443] io scheduler deadline registered
[    1.079472] io scheduler cfq registered (default)
[    1.079591] pci 0000:01:00.0: Boot video device
[    1.081556] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.081579] pcieport-driver 0000:00:01.0: found MSI capability
[    1.081595] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.081602] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.081612] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.081644] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.081670] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.081688] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.081697] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.081705] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.081713] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.081754] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.081780] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.081797] pcieport-driver 0000:00:1c.5: irq 2301 for MSI/MSI-X
[    1.081806] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.081815] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.081823] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.081870] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.082116] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.082218] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.082220] ACPI: Power Button (FF) [PWRF]
[    1.082259] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.082261] ACPI: Power Button (CM) [PWRB]
[    1.082471] processor ACPI_CPU:00: registered as cooling_device0
[    1.082499] processor ACPI_CPU:01: registered as cooling_device1
[    1.112689] Linux agpgart interface v0.103
[    1.112697] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.112778] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.113086] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.113603] brd: module loaded
[    1.113822] loop: module loaded
[    1.113868] Fixed MDIO Bus: probed
[    1.113872] PPP generic driver version 2.4.2
[    1.113912] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.113930] Driver 'sd' needs updating - please use bus_type methods
[    1.113936] Driver 'sr' needs updating - please use bus_type methods
[    1.113987] ata_piix 0000:00:1f.2: version 2.12
[    1.113999] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.114002] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.114034] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.114082] scsi0 : ata_piix
[    1.114135] scsi1 : ata_piix
[    1.115322] ata1: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 19
[    1.115326] ata2: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 19
[    1.908056] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.908067] ata1.01: SATA link down (SStatus 0 SControl 300)
[    1.916185] ata1.00: ATAPI: ASUS    DRW-2014L1T, 1.02, max UDMA/66
[    1.932191] ata1.00: configured for UDMA/66
[    2.728053] ata2.00: SATA link down (SStatus 0 SControl 300)
[    2.728064] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.762086] ata2.01: ATA-8: WDC WD5000AAJS-00YFA0, 12.01C02, max UDMA/133
[    2.762089] ata2.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.768955] ata2.01: configured for UDMA/133
[    2.769511] scsi 0:0:0:0: CD-ROM            ASUS     DRW-2014L1T      1.02 PQ: 0 ANSI: 5
[    2.772754] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.772757] Uniform CD-ROM driver Revision: 3.20
[    2.772852] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.772879] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.772924] scsi 1:0:1:0: Direct-Access     ATA      WDC WD5000AAJS-0 12.0 PQ: 0 ANSI: 5
[    2.772985] sd 1:0:1:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.772997] sd 1:0:1:0: [sda] Write Protect is off
[    2.772998] sd 1:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    2.773017] sd 1:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.773066] sd 1:0:1:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    2.773076] sd 1:0:1:0: [sda] Write Protect is off
[    2.773078] sd 1:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    2.773096] sd 1:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.773098]  sda: sda1 sda2 sda3 sda4
[    2.775183] sd 1:0:1:0: [sda] Attached SCSI disk
[    2.775208] sd 1:0:1:0: Attached scsi generic sg1 type 0
[    2.775223] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.775226] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    2.775252] ata_piix 0000:00:1f.5: setting latency timer to 64
[    2.775286] scsi2 : ata_piix
[    2.775324] scsi3 : ata_piix
[    2.776406] ata3: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb480 irq 19
[    2.776408] ata4: SATA max UDMA/133 cmd 0xb880 ctl 0xb800 bmdma 0xb488 irq 19
[    3.106553] ata3: SATA link down (SStatus 0 SControl 300)
[    3.580040] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.589009] ata4.00: ATA-8: WDC WD5000AAKS-00A7B2, 01.03B01, max UDMA/133
[    3.589012] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.605085] ata4.00: configured for UDMA/133
[    3.605166] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
[    3.605222] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.605233] sd 3:0:0:0: [sdb] Write Protect is off
[    3.605235] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.605253] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.605290] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.605301] sd 3:0:0:0: [sdb] Write Protect is off
[    3.605302] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.605321] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.605323]  sdb: sdb1 sdb2 sdb3 sdb4
[    3.621534] sd 3:0:0:0: [sdb] Attached SCSI disk
[    3.621560] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    3.621951] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.621965] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.621978] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.621980] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.622021] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.625932] ehci_hcd 0000:00:1a.7: debug port 1
[    3.625937] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.625946] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9ffc00
[    3.640508] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.640574] usb usb1: configuration #1 chosen from 1 choice
[    3.640602] hub 1-0:1.0: USB hub found
[    3.640609] hub 1-0:1.0: 6 ports detected
[    3.640688] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.640696] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.640698] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.640726] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.644638] ehci_hcd 0000:00:1d.7: debug port 1
[    3.644642] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.644651] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9ff800
[    3.660008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.660071] usb usb2: configuration #1 chosen from 1 choice
[    3.660097] hub 2-0:1.0: USB hub found
[    3.660103] hub 2-0:1.0: 6 ports detected
[    3.660173] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.660183] uhci_hcd: USB Universal Host Controller Interface driver
[    3.660199] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16



---

### Post by lildigiman on 2009-09-09
The rest - 

> 
[    3.660204] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.660206] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.660235] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.660260] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c800
[    3.660310] usb usb3: configuration #1 chosen from 1 choice
[    3.660328] hub 3-0:1.0: USB hub found
[    3.660333] hub 3-0:1.0: 2 ports detected
[    3.660390] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.660394] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.660396] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.660426] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.660450] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c880
[    3.660499] usb usb4: configuration #1 chosen from 1 choice
[    3.660519] hub 4-0:1.0: USB hub found
[    3.660523] hub 4-0:1.0: 2 ports detected
[    3.660578] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.660583] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.660585] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.660611] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.660630] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000cc00
[    3.660679] usb usb5: configuration #1 chosen from 1 choice
[    3.660695] hub 5-0:1.0: USB hub found
[    3.660699] hub 5-0:1.0: 2 ports detected
[    3.660761] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.660766] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.660768] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.660794] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.660813] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c080
[    3.660863] usb usb6: configuration #1 chosen from 1 choice
[    3.660879] hub 6-0:1.0: USB hub found
[    3.660884] hub 6-0:1.0: 2 ports detected
[    3.660939] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.660943] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.660945] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.660979] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.660998] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c400
[    3.661047] usb usb7: configuration #1 chosen from 1 choice
[    3.661065] hub 7-0:1.0: USB hub found
[    3.661069] hub 7-0:1.0: 2 ports detected
[    3.661126] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.661130] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.661133] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.661161] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.661179] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
[    3.661231] usb usb8: configuration #1 chosen from 1 choice
[    3.661247] hub 8-0:1.0: USB hub found
[    3.661251] hub 8-0:1.0: 2 ports detected
[    3.661344] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    3.661345] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    3.661804] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.672538] mice: PS/2 mouse device common for all mice
[    3.708557] rtc_cmos 00:03: RTC can wake from S4
[    3.708590] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.708618] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.708660] device-mapper: uevent: version 1.0.3
[    3.708720] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.708769] device-mapper: multipath: version 1.0.5 loaded
[    3.708771] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.708837] cpuidle: using governor ladder
[    3.708838] cpuidle: using governor menu
[    3.709124] TCP cubic registered
[    3.709171] NET: Registered protocol family 10
[    3.709448] lo: Disabled Privacy Extensions
[    3.709643] NET: Registered protocol family 17
[    3.709656] Bluetooth: L2CAP ver 2.11
[    3.709657] Bluetooth: L2CAP socket layer initialized
[    3.709659] Bluetooth: SCO (Voice Link) ver 0.6
[    3.709660] Bluetooth: SCO socket layer initialized
[    3.709677] Bluetooth: RFCOMM socket layer initialized
[    3.709681] Bluetooth: RFCOMM TTY layer initialized
[    3.709682] Bluetooth: RFCOMM ver 1.10
[    3.709767] registered taskstats version 1
[    3.709854]   Magic number: 9:947:699
[    3.709917] rtc_cmos 00:03: setting system clock to 2009-09-09 20:40:47 UTC (1252528847)
[    3.709919] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.709920] EDD information not available.
[    3.709949] Freeing unused kernel memory: 532k freed
[    3.710089] Write protecting the kernel read-only data: 6688k
[    3.738991] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.833020] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.833033] ATL1E 0000:02:00.0: setting latency timer to 64
[    3.871510] Floppy drive(s): fd0 is 1.44M
[    3.892190] FDC 0 is a post-1991 82077
[    4.360517] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    4.399861] kjournald starting.  Commit interval 5 seconds
[    4.399867] EXT3-fs: mounted filesystem with ordered data mode.
[    4.537491] usb 4-2: configuration #1 chosen from 1 choice
[    4.780022] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    4.967821] usb 6-1: configuration #1 chosen from 1 choice
[    7.791999] udev: starting version 141
[    7.942654] usbcore: registered new interface driver hiddev
[    7.960838] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    7.976151] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input5
[    7.988598] iTCO_vendor_support: vendor-support=0
[    7.990275] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    7.990385] iTCO_wdt: Found a ICH10 TCO device (Version=2, TCOBASE=0x0860)
[    7.990456] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    8.012117] generic-usb 0003:045E:008C.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A] on usb-0000:00:1d.0-1/input0
[    8.012136] usbcore: registered new interface driver usbhid
[    8.012155] usbhid: v2.6:USB HID core driver
[    8.168562] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    8.182896] [fglrx] Maximum main memory to use for locked dma buffers: 3738 MBytes.
[    8.182996] [fglrx]   vendor: 1002 device: 9505 count: 1
[    8.183231] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[    8.183241] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.183245] pci 0000:01:00.0: setting latency timer to 64
[    8.184786] [fglrx] Driver built-in PAT support is enabled successfully
[    8.184822] [fglrx] module loaded - fglrx 8.60.40 [Mar 14 2009] with 1 minors
[    8.566992] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.567078] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.630139] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    8.630177] HDA Intel 0000:01:00.1: setting latency timer to 64
[    8.792540] lp: driver loaded but no devices found
[    9.404807] EXT3 FS on sdb2, internal journal
[   10.386350] type=1505 audit(1252543254.174:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2085
[   10.414086] type=1505 audit(1252543254.202:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2089
[   10.414165] type=1505 audit(1252543254.202:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2089
[   10.414195] type=1505 audit(1252543254.202:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2089
[   10.414223] type=1505 audit(1252543254.202:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2089
[   10.436875] type=1505 audit(1252543254.226:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2094
[   10.513813] type=1505 audit(1252543254.302:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2098
[   10.513931] type=1505 audit(1252543254.302:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2098
[   10.531316] type=1505 audit(1252543254.318:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2102
[   14.612115] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   14.612118] vboxdrv: Successfully done.
[   14.612119] vboxdrv: Found 2 processor cores.
[   14.612176] VBoxDrv: dbg - g_abExecMemory=ffffffffa0463b40
[   14.612193] vboxdrv: fAsync=0 offMin=0x18f offMax=0x880
[   14.612230] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   14.612231] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   14.816327] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0602980
[   16.145984] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.145986] Bluetooth: BNEP filters: protocol multicast
[   16.158638] Bridge firewalling registered
[   17.482460] ppdev: user-space parallel port driver
[   21.212901] ATL1E 0000:02:00.0: irq 2300 for MSI/MSI-X
[   21.213024] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   21.213479] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.213962] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.567072] fglrx_pci 0000:01:00.0: irq 2299 for MSI/MSI-X
[   22.575607] [fglrx] Firegl kernel thread PID: 3448
[   22.607239] [fglrx] Gart USWC size:1885 M.
[   22.607242] [fglrx] Gart cacheable size:60 M.
[   22.607246] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.607247] [fglrx] Reserved FB block: Unshared offset:fc27000, size:3d9000 
[   22.607249] [fglrx] Reserved FB block: Unshared offset:1fffc000, size:4000 
[   31.372005] eth0: no IPv6 routers present

---

### Post by PukingPenguin on 2009-09-09
Perhaps if you posted whatever information the system gave you that lead you to believe that the libraries and/or whatever were not really installed....
Otherwise, it sounds like it calls for speculation.

---

### Post by lildigiman on 2009-09-09
In terminal I downloaded them again - and it didn't complain, the Terminal always says if something is already installed.

I used Sudo apt-get install libraryXYZ etc...

Also using Netbeans/the terminal for compiling said that they couldnt find the header files from the specific libraries.

Also my Firefox sessions are different. So I could boot one time, and get a Session of Firefox from two boots ago, or get the one from the last boot. It seems somewhat random...?

---

