---
title: "(sda) Assuming drive cache: write through"
date: 2009-09-29
forum: General Help
---

### Post by FLinux on 2009-09-29
Good day.

I have run into a problem yesterday.  I was reading up on how to mount my USB flash drive in the Ubuntu terminal to install packages from it.  After doing so I returned to the GDM display manager and then turn off the pc without un-mounting the flashdrive in the terminal.

Now when I log into Ubuntu and connect the flashdrive the the pc Ubuntu doesn't see it at all.  In the past I could even see my Windows Vista partition and when I clicked on it, it was mounted by Ubuntu and I could axcces the files from the Linux desktop.  I can't even use the cd-rom at this stage.

Can anyone help, please.

Here is an output from dmesh:

[html][    0.004241] CPU: Physical Processor ID: 0
[    0.004242] CPU: Processor Core ID: 0
[    0.004246] using mwait in idle threads.
[    0.004257] Checking 'hlt' instruction... OK.
[    0.023243] ACPI: Core revision 20080926
[    0.023910] ACPI: Checking initramfs for custom DSDT
[    0.293975] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.333670] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 01
[    0.336001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6384.52 BogoMIPS (lpj=12769055)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.420390] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 01
[    0.420416] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.424061] Brought up 2 CPUs
[    0.424067] Total of 2 processors activated (12769.11 BogoMIPS).
[    0.424121] CPU0 attaching sched-domain:
[    0.424125]  domain 0: span 0-1 level SIBLING
[    0.424128]   groups: 0 1
[    0.424135] CPU1 attaching sched-domain:
[    0.424137]  domain 0: span 0-1 level SIBLING
[    0.424140]   groups: 1 0
[    0.424226] net_namespace: 776 bytes
[    0.424232] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.424236] Booting paravirtualized kernel on bare hardware
[    0.424441] Time: 12:31:10  Date: 09/29/09
[    0.424441] regulator: core version 0.5
[    0.424441] NET: Registered protocol family 16
[    0.424441] EISA bus registered
[    0.424441] ACPI: bus type pci registered
[    0.424441] PCI: MCFG configuration 0: base d0000000 segment 0 buses 0 - 255
[    0.424441] PCI: MCFG area at d0000000 reserved in E820
[    0.424441] PCI: Using MMCONFIG for extended config space
[    0.424441] PCI: Using configuration type 1 for base access
[    0.425489] ACPI: EC: Look up EC in DSDT
[    0.430958] ACPI: Interpreter enabled
[    0.430966] ACPI: (supports S0 S1 S3 S4 S5)
[    0.430991] ACPI: Using IOAPIC for interrupt routing
[    0.435945] ACPI: No dock devices found.
[    0.435961] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.436071] pci 0000:00:02.0: reg 10 32bit mmio: [0xcfe00000-0xcfe7ffff]
[    0.436078] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.436083] pci 0000:00:02.0: reg 18 32bit mmio: [0xe0000000-0xefffffff]
[    0.436089] pci 0000:00:02.0: reg 1c 32bit mmio: [0xcff00000-0xcff3ffff]
[    0.436124] pci 0000:00:02.1: reg 10 32bit mmio: [0xcfe80000-0xcfefffff]
[    0.436227] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.436232] pci 0000:00:1c.0: PME# disabled
[    0.436285] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.436289] pci 0000:00:1c.1: PME# disabled
[    0.436343] pci 0000:00:1d.0: reg 20 io port: [0x1440-0x145f]
[    0.436393] pci 0000:00:1d.1: reg 20 io port: [0x1460-0x147f]
[    0.436444] pci 0000:00:1d.2: reg 20 io port: [0x1480-0x149f]
[    0.436497] pci 0000:00:1d.3: reg 20 io port: [0x14a0-0x14bf]
[    0.436555] pci 0000:00:1d.7: reg 10 32bit mmio: [0xcff40000-0xcff403ff]
[    0.436596] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.436601] pci 0000:00:1d.7: PME# disabled
[    0.436676] pci 0000:00:1e.2: reg 10 io port: [0x1000-0x10ff]
[    0.436683] pci 0000:00:1e.2: reg 14 io port: [0x1400-0x143f]
[    0.436690] pci 0000:00:1e.2: reg 18 32bit mmio: [0xcff40400-0xcff405ff]
[    0.436696] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xcff40600-0xcff406ff]
[    0.436719] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.436723] pci 0000:00:1e.2: PME# disabled
[    0.436800] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.436806] pci 0000:00:1f.0: quirk: region f800-f87f claimed by ICH6 ACPI/GPIO/TCO
[    0.436811] pci 0000:00:1f.0: quirk: region fa00-fa3f claimed by ICH6 GPIO
[    0.436832] pci 0000:00:1f.1: reg 10 io port: [0x1808-0x180f]
[    0.436839] pci 0000:00:1f.1: reg 14 io port: [0x1828-0x182b]
[    0.436846] pci 0000:00:1f.1: reg 18 io port: [0x1810-0x1817]
[    0.436853] pci 0000:00:1f.1: reg 1c io port: [0x182c-0x182f]
[    0.436861] pci 0000:00:1f.1: reg 20 io port: [0x14e0-0x14ef]
[    0.436902] pci 0000:00:1f.2: reg 10 io port: [0x1818-0x181f]
[    0.436909] pci 0000:00:1f.2: reg 14 io port: [0x1830-0x1833]
[    0.436915] pci 0000:00:1f.2: reg 18 io port: [0x1820-0x1827]
[    0.436922] pci 0000:00:1f.2: reg 1c io port: [0x1834-0x1837]
[    0.436928] pci 0000:00:1f.2: reg 20 io port: [0x14f0-0x14ff]
[    0.436947] pci 0000:00:1f.2: PME# supported from D3hot
[    0.436951] pci 0000:00:1f.2: PME# disabled
[    0.437074] pci 0000:40:00.0: reg 10 64bit mmio: [0xf0400000-0xf040ffff]
[    0.437121] pci 0000:40:00.0: PME# supported from D3hot D3cold
[    0.437126] pci 0000:40:00.0: PME# disabled
[    0.437177] pci 0000:00:1c.1: bridge 32bit mmio: [0xf0200000-0xf04fffff]
[    0.437233] pci 0000:00:1e.0: transparent bridge
[    0.437259] bus 00 -> node 0
[    0.437266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.437668] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX1._PRT]
[    0.437821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX2._PRT]
[    0.437978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.450111] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.450249] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.450383] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.450518] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.450651] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.450784] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.450918] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.451052] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.451258] ACPI: WMI: Mapper loaded
[    0.451321] SCSI subsystem initialized
[    0.451321] libata version 3.00 loaded.
[    0.451321] usbcore: registered new interface driver usbfs
[    0.451321] usbcore: registered new interface driver hub
[    0.451321] usbcore: registered new device driver usb
[    0.451321] PCI: Using ACPI for IRQ routing
[    0.456015] Bluetooth: Core ver 2.13
[    0.456037] NET: Registered protocol family 31
[    0.456037] Bluetooth: HCI device and connection manager initialized
[    0.456037] Bluetooth: HCI socket layer initialized
[    0.456037] NET: Registered protocol family 8
[    0.456038] NET: Registered protocol family 20
[    0.456052] NetLabel: Initializing
[    0.456055] NetLabel:  domain hash size = 128
[    0.456056] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.456074] NetLabel:  unlabeled traffic allowed by default
[    0.456168] hpet clockevent registered
[    0.456171] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.456177] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.456183] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.460095] AppArmor: AppArmor Filesystem Enabled
[    0.468015] pnp: PnP ACPI init
[    0.468029] ACPI: bus type pnp registered
[    0.470722] pnp 00:0c: io resource (0xf800-0xf81f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.470728] pnp 00:0c: io resource (0xf820-0xf83f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.470731] pnp 00:0c: io resource (0xf840-0xf85f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.470734] pnp 00:0c: io resource (0xf860-0xf87f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.471865] pnp: PnP ACPI: found 15 devices
[    0.471868] ACPI: ACPI bus type pnp unregistered
[    0.471872] PnPBIOS: Disabled by ACPI PNP
[    0.471892] system 00:0c: ioport range 0x400-0x41f has been reserved
[    0.471895] system 00:0c: ioport range 0x420-0x43f has been reserved
[    0.471898] system 00:0c: ioport range 0x440-0x45f has been reserved
[    0.471901] system 00:0c: ioport range 0x460-0x47f has been reserved
[    0.471904] system 00:0c: ioport range 0x480-0x48f has been reserved
[    0.471907] system 00:0c: ioport range 0xfa00-0xfa3f has been reserved
[    0.471910] system 00:0c: ioport range 0xfc00-0xfc7f has been reserved
[    0.471913] system 00:0c: ioport range 0xfc80-0xfcff has been reserved
[    0.471915] system 00:0c: ioport range 0xfe00-0xfe7f has been reserved
[    0.471918] system 00:0c: ioport range 0xfe80-0xfeff has been reserved
[    0.471925] system 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[    0.471933] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.471936] system 00:0e: iomem range 0x100000-0x1fffffff could not be reserved
[    0.471939] system 00:0e: iomem range 0xe8000-0xfffff could not be reserved
[    0.471942] system 00:0e: iomem range 0xfec01000-0xffffffff has been reserved
[    0.471945] system 00:0e: iomem range 0xd0000000-0xdfffffff has been reserved
[    0.471948] system 00:0e: iomem range 0xcd800-0xe7fff has been reserved
[    0.506687] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:20
[    0.506690] pci 0000:00:1c.0:   IO window: disabled
[    0.506695] pci 0000:00:1c.0:   MEM window: disabled
[    0.506699] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.506706] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:40
[    0.506708] pci 0000:00:1c.1:   IO window: disabled
[    0.506714] pci 0000:00:1c.1:   MEM window: 0xf0200000-0xf04fffff
[    0.506718] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.506725] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.506727] pci 0000:00:1e.0:   IO window: disabled
[    0.506732] pci 0000:00:1e.0:   MEM window: disabled
[    0.506736] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.506752] pci 0000:00:1c.0: setting latency timer to 64
[    0.506767] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.506771] pci 0000:00:1c.1: setting latency timer to 64
[    0.506779] pci 0000:00:1e.0: setting latency timer to 64
[    0.506783] bus: 00 index 0 io port: [0x00-0xffff]
[    0.506786] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.506788] bus: 20 index 0 mmio: [0x0-0x0]
[    0.506790] bus: 20 index 1 mmio: [0x0-0x0]
[    0.506792] bus: 20 index 2 mmio: [0x0-0x0]
[    0.506794] bus: 20 index 3 mmio: [0x0-0x0]
[    0.506796] bus: 40 index 0 mmio: [0x0-0x0]
[    0.506798] bus: 40 index 1 mmio: [0xf0200000-0xf04fffff]
[    0.506800] bus: 40 index 2 mmio: [0x0-0x0]
[    0.506802] bus: 40 index 3 mmio: [0x0-0x0]
[    0.506805] bus: 05 index 0 mmio: [0x0-0x0]
[    0.506806] bus: 05 index 1 mmio: [0x0-0x0]
[    0.506808] bus: 05 index 2 mmio: [0x0-0x0]
[    0.506811] bus: 05 index 3 io port: [0x00-0xffff]
[    0.506813] bus: 05 index 4 mmio: [0x000000-0xffffffff]
[    0.506822] NET: Registered protocol family 2
[    0.520088] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.520362] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.520436] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.520504] TCP: Hash tables configured (established 16384 bind 16384)
[    0.520507] TCP reno registered
[    0.528107] NET: Registered protocol family 1
[    0.528258] checking if image is initramfs... it is
[    0.956493] Switched to high resolution mode on CPU 1
[    0.960011] Switched to high resolution mode on CPU 0
[    1.084093] Freeing initrd memory: 7383k freed
[    1.084331] cpufreq: No nForce2 chipset.
[    1.084497] audit: initializing netlink socket (disabled)
[    1.084530] type=2000 audit(1254227471.081:1): initialized
[    1.091938] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.093434] VFS: Disk quotas dquot_6.5.1
[    1.093505] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.094242] fuse init (API version 7.10)
[    1.094343] msgmni has been set to 977
[    1.094558] alg: No test for stdrng (krng)
[    1.094584] io scheduler noop registered
[    1.094589] io scheduler anticipatory registered
[    1.094592] io scheduler deadline registered
[    1.094617] io scheduler cfq registered (default)
[    1.094633] pci 0000:00:02.0: Boot video device
[    1.094760] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    1.094905] ACPI Warning (nspredef-0252): \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, expected 4 [20080926]
[    1.095922] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    1.097122] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.097161] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.097192] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.097205] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.097223] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.097240] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.097306] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.097343] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.097370] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.097382] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.097398] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.097414] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.097491] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.097507] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    1.097784] ACPI Warning (nseval-0168): Insufficient arguments - method [_OSC] needs 5, found 4 [20080926]
[    1.098046] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.098197] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.098201] ACPI: Power Button (FF) [PWRF]
[    1.098268] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.098276] ACPI: Power Button (CM) [PBTN]
[    1.098576] processor ACPI_CPU:00: registered as cooling_device0
[    1.098581] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.098669] processor ACPI_CPU:01: registered as cooling_device1
[    1.098675] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.100755] isapnp: Scanning for PnP cards...
[    1.452385] isapnp: No Plug & Play device found
[    1.461175] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.461280] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.461689] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.462664] brd: module loaded
[    1.463064] loop: module loaded
[    1.463151] Fixed MDIO Bus: probed
[    1.463157] PPP generic driver version 2.4.2
[    1.463227] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.463267] Driver 'sd' needs updating - please use bus_type methods
[    1.463279] Driver 'sr' needs updating - please use bus_type methods
[    1.463360] ata_piix 0000:00:1f.1: version 2.12
[    1.463374] ata_piix 0000:00:1f.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.463421] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.463527] scsi0 : ata_piix
[    1.463650] scsi1 : ata_piix
[    1.463790] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x14e0 irq 14
[    1.463793] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x14e8 irq 15
[    1.632357] ata1.01: ATAPI: HL-DT-ST CD-ROM GCR-8483B, 1.02, max MWDMA2
[    1.648302] ata1.01: configured for MWDMA2
[    1.818299] scsi 0:0:1:0: CD-ROM            HL-DT-ST CD-ROM GCR-8483B 1.02 PQ: 0 ANSI: 5
[    1.834648] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.834652] Uniform CD-ROM driver Revision: 3.20
[    1.834777] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.834837] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    1.834866] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.834871] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.988021] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.988117] scsi2 : ata_piix
[    1.988198] scsi3 : ata_piix
[    1.988331] ata3: SATA max UDMA/133 cmd 0x1818 ctl 0x1830 bmdma 0x14f0 irq 19
[    1.988335] ata4: SATA max UDMA/133 cmd 0x1820 ctl 0x1834 bmdma 0x14f8 irq 19
[    2.152217] ata3.00: ATA-8: WDC WD3200AAJS-65VWA0, 12.01B02, max UDMA/133
[    2.152221] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.168238] ata3.00: configured for UDMA/133
[    2.334226] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-6 12.0 PQ: 0 ANSI: 5
[    2.334345] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.334366] sd 2:0:0:0: [sda] Write Protect is off
[    2.334370] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.334403] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.334478] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.334497] sd 2:0:0:0: [sda] Write Protect is off
[    2.334500] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.334533] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.334538]  sda: sda1 sda2 sda3
[    2.368720] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.368774] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.369539] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.369567] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.369595] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.369599] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.369673] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.373597] ehci_hcd 0000:00:1d.7: debug port 1
[    2.373604] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.373622] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xcff40000
[    2.388017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.388126] usb usb1: configuration #1 chosen from 1 choice
[    2.388160] hub 1-0:1.0: USB hub found
[    2.388168] hub 1-0:1.0: 8 ports detected
[    2.388308] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.388328] uhci_hcd: USB Universal Host Controller Interface driver
[    2.388368] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.388376] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.388379] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.388435] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.388459] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001440
[    2.388546] usb usb2: configuration #1 chosen from 1 choice
[    2.388578] hub 2-0:1.0: USB hub found
[    2.388587] hub 2-0:1.0: 2 ports detected
[    2.388699] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.388706] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.388709] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.388760] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.388791] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001460
[    2.388872] usb usb3: configuration #1 chosen from 1 choice
[    2.388903] hub 3-0:1.0: USB hub found
[    2.388911] hub 3-0:1.0: 2 ports detected
[    2.389012] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.389018] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.389022] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.389079] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.389110] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001480
[    2.389191] usb usb4: configuration #1 chosen from 1 choice
[    2.389221] hub 4-0:1.0: USB hub found
[    2.389229] hub 4-0:1.0: 2 ports detected
[    2.389331] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
[    2.389338] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.389341] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.389394] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.389423] uhci_hcd 0000:00:1d.3: irq 22, io base 0x000014a0
[    2.389506] usb usb5: configuration #1 chosen from 1 choice
[    2.389540] hub 5-0:1.0: USB hub found
[    2.389549] hub 5-0:1.0: 2 ports detected
[    2.389725] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    2.392035] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.392046] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.396063] mice: PS/2 mouse device common for all mice
[    2.408098] rtc_cmos 00:03: RTC can wake from S4
[    2.408139] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.408166] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.408256] device-mapper: uevent: version 1.0.3
[    2.408378] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.408495] device-mapper: multipath: version 1.0.5 loaded
[    2.408500] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.408603] EISA: Probing bus 0 at eisa.0
[    2.408611] Cannot allocate resource for EISA slot 1
[    2.408635] EISA: Detected 0 cards.
[    2.408704] cpuidle: using governor ladder
[    2.408708] cpuidle: using governor menu
[    2.409345] TCP cubic registered
[    2.409432] NET: Registered protocol family 10
[    2.409950] lo: Disabled Privacy Extensions
[    2.410341] NET: Registered protocol family 17
[    2.410365] Bluetooth: L2CAP ver 2.11
[    2.410367] Bluetooth: L2CAP socket layer initialized
[    2.410370] Bluetooth: SCO (Voice Link) ver 0.6
[    2.410372] Bluetooth: SCO socket layer initialized
[    2.410419] Bluetooth: RFCOMM socket layer initialized
[    2.410430] Bluetooth: RFCOMM TTY layer initialized
[    2.410433] Bluetooth: RFCOMM ver 1.10
[    2.410496] Using IPI No-Shortcut mode
[    2.410595] registered taskstats version 1
[    2.410710]   Magic number: 9:946:532
[    2.410729] bdi 1:10: hash matches
[    2.410800] rtc_cmos 00:03: setting system clock to 2009-09-29 12:31:12 UTC (1254227472)
[    2.410804] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.410806] EDD information not available.
[    2.411255] Freeing unused kernel memory: 532k freed
[    2.411408] Write protecting the kernel text: 4120k
[    2.411464] Write protecting the kernel read-only data: 1524k
[    2.646119] tg3.c:v3.94 (August 14, 2008)
[    2.646144] tg3 0000:40:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.646157] tg3 0000:40:00.0: setting latency timer to 64
[    2.693546] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:13:21:00:29:7b
[    2.693554] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    2.693559] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.773205] Floppy drive(s): fd0 is 1.44M
[    2.791148] FDC 0 is a post-1991 82077
[    2.941517] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    3.121187] usb 4-1: configuration #1 chosen from 1 choice
[    3.130423] usbcore: registered new interface driver hiddev
[    3.143377] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input3
[    3.143669] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.2-1/input0
[    3.143692] usbcore: registered new interface driver usbhid
[    3.143696] usbhid: v2.6:USB HID core driver
[    3.206180] PM: Starting manual resume from disk
[    3.206185] PM: Resume from partition 8:2
[    3.206187] PM: Checking hibernation image.
[    3.206384] PM: Resume from disk failed.
[    3.224554] kjournald starting.  Commit interval 5 seconds
[    3.224569] EXT3-fs: mounted filesystem with ordered data mode.
[    3.364035] usb 4-2: new low speed USB device using uhci_hcd and address 3
[    3.540151] usb 4-2: configuration #1 chosen from 1 choice
[    3.558394] input: CHICONY HP Basic USB Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4
[    3.558666] generic-usb 0003:03F0:0024.0002: input,hidraw1: USB HID v1.10 Keyboard [CHICONY HP Basic USB Keyboard] on usb-0000:00:1d.2-2/input0
[    7.974558] udev: starting version 141
[    8.031379] udev: renamed network interface eth0 to eth1
[    8.137928] Linux agpgart interface v0.103
[    8.168792] agpgart-intel 0000:00:00.0: Intel 915G Chipset
[    8.169277] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    8.171798] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    8.213783] parport_pc 00:07: reported by Plug and Play ACPI
[    8.213848] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    8.420309] intel_rng: Firmware space is locked read-only. If you can't or
[    8.420314] intel_rng: don't want to disable this in firmware setup, and if
[    8.420316] intel_rng: you are certain that your system has a functional
[    8.420319] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    8.495283] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    8.804381] ppdev: user-space parallel port driver
[    8.822941] iTCO_vendor_support: vendor-support=0
[    8.825105] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.825401] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0xf860)
[    8.826421] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    8.946389] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    8.946470] Intel ICH 0000:00:1e.2: setting latency timer to 64
[    9.368016] intel8x0_measure_ac97_clock: measured 54805 usecs
[    9.368020] intel8x0: clocking to 48000
[    9.537297] lp0: using parport0 (interrupt-driven).
[    9.626504] Adding 489972k swap on /dev/sda2.  Priority:-1 extents:1 across:489972k
[   10.170271] EXT3 FS on sda3, internal journal
[   11.205840] type=1505 audit(1254220281.293:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1953
[   11.254305] type=1505 audit(1254220281.341:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1957
[   11.254463] type=1505 audit(1254220281.341:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1957
[   11.254511] type=1505 audit(1254220281.341:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1957
[   11.254554] type=1505 audit(1254220281.341:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1957
[   11.389812] type=1505 audit(1254220281.477:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1962
[   11.390045] type=1505 audit(1254220281.477:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1962
[   11.419743] type=1505 audit(1254220281.505:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1966
[   17.641116] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   17.641122] vboxdrv: Successfully done.
[   17.641126] vboxdrv: Found 2 processor cores.
[   17.641233] vboxdrv: fAsync=0 offMin=0x358 offMax=0x13d8
[   17.641323] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   17.641327] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   18.769878] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.769885] Bluetooth: BNEP filters: protocol multicast
[   18.789697] Bridge firewalling registered
[   24.081690] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   65.778119] mtrr: no MTRR for e0000000,7b0000 found
[   80.779455] glxinfo[3627]: segfault at 0 ip 0804ad46 sp bfb54a80 error 4 in glxinfo[8048000+5000]
[   80.814958] glxinfo[3630]: segfault at 0 ip 0804ad46 sp bfed25f0 error 4 in glxinfo[8048000+5000]
[   85.316030] end_request: I/O error, dev fd0, sector 0
[   85.340031] end_request: I/O error, dev fd0, sector 0
[  182.696015] usb 1-7: new high speed USB device using ehci_hcd and address 4
[  183.398420] usb 1-7: configuration #1 chosen from 1 choice
[  183.464230] Initializing USB Mass Storage driver...
[  183.464613] scsi4 : SCSI emulation for USB Mass Storage devices
[  183.465021] usb-storage: device found at 4
[  183.465025] usb-storage: waiting for device to settle before scanning
[  183.465044] usbcore: registered new interface driver usb-storage
[  183.465052] USB Mass Storage support registered.
[  188.464147] usb-storage: device scan complete
[  188.474491] scsi 4:0:0:0: Direct-Access     JetFlash TS4GJFV30        8.07 PQ: 0 ANSI: 2
[  188.476974] sd 4:0:0:0: [sdb] 7987198 512-byte hardware sectors: (4.08 GB/3.80 GiB)
[  188.478229] sd 4:0:0:0: [sdb] Write Protect is off
[  188.478235] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  188.478240] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  188.485233] sd 4:0:0:0: [sdb] 7987198 512-byte hardware sectors: (4.08 GB/3.80 GiB)
[  188.485717] sd 4:0:0:0: [sdb] Write Protect is off
[  188.485723] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  188.485728] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  188.485737]  sdb: sdb1
[  188.486718] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  188.486855] sd 4:0:0:0: Attached scsi generic sg2 type 0
franco@franco-desktop:~$[/html]May it be a problem within /etc/fstab or /etc/mtab ?

I don't have a clue what to do so any help will be appreciated.

Thank You

---

### Post by sisco311 on 2009-09-29
any error message, when you try to mount it?

```
sudo mount -t auto -o umask=002,uid=$(id -u) /dev/sdb1 /mnt
```

---

### Post by FLinux on 2009-09-30
I've used the command;
 
sudo mount -t auto -o umask=002,uid=$(id -u) /dev/sdb1 /mnt
 
The flash drive is then mounted, but I can only [COLOR=black][FONT=Verdana]access [/FONT][/COLOR]it from the terminal. I can also mount my windows partition in this manner, but then access is also only through the terminal.
 
Usually I when I connected the flash drive an icon appeared on the desktop and a window open showing the contents of the flash drive. Wel this doesn't happen anymore. It seem as if Ubuntu doesn't see the flash drive. That is why I can only access it through the terminal.
 
When I am in the terminal and I connect the flash drive the following pop onto the screen:
 
(sda)Assuming drive cache:write through
 
Sorry I still am clueless about what to do.

---

