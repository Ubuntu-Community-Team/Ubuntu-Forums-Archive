---
title: "startup takes forever"
date: 2009-08-09
forum: General Help
---

### Post by haiyun211 on 2009-08-09
Hi all,

Just today My system has been taking forever to startup  and displays all these commands on a black screen after the bar gets about half way across the screen.  I am running ubuntu 9.04 any help and advice would be appreciated.  Thanks
:(

---

### Post by Sef on 2009-08-09
What are your system specs?

---

### Post by haiyun211 on 2009-08-09
I have and intel centrino duo processor 1gb of ram a nvidia geforce go 7600 and linux kernel 2.6.28-13-generic is that what you were looking for?

---

### Post by bhaverkamp on 2009-08-09
Attach dmesg and messages logs. Should be able to see something in those logs.

---

### Post by haiyun211 on 2009-08-09
How do i get those?

---

### Post by haiyun211 on 2009-08-09
Is this what you wanted

```
[    0.534624] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.534803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.541916] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[    0.542079] ACPI: PCI Interrupt Link [LNKB] (IRQs *3)
[    0.542240] ACPI: PCI Interrupt Link [LNKC] (IRQs *3)
[    0.542400] ACPI: PCI Interrupt Link [LNKD] (IRQs *4)
[    0.542560] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    0.542719] ACPI: PCI Interrupt Link [LNKF] (IRQs 11) *0, disabled.
[    0.542881] ACPI: PCI Interrupt Link [LNKG] (IRQs *5)
[    0.543041] ACPI: PCI Interrupt Link [LNKH] (IRQs *7)
[    0.543384] ACPI: WMI: Mapper loaded
[    0.543426] SCSI subsystem initialized
[    0.543426] libata version 3.00 loaded.
[    0.543426] usbcore: registered new interface driver usbfs
[    0.543426] usbcore: registered new interface driver hub
[    0.543426] usbcore: registered new device driver usb
[    0.543426] PCI: Using ACPI for IRQ routing
[    0.548012] Bluetooth: Core ver 2.13
[    0.548028] NET: Registered protocol family 31
[    0.548028] Bluetooth: HCI device and connection manager initialized
[    0.548028] Bluetooth: HCI socket layer initialized
[    0.548028] NET: Registered protocol family 8
[    0.548030] NET: Registered protocol family 20
[    0.548043] NetLabel: Initializing
[    0.548045] NetLabel:  domain hash size = 128
[    0.548047] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.548062] NetLabel:  unlabeled traffic allowed by default
[    0.548080] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.548085] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.552068] AppArmor: AppArmor Filesystem Enabled
[    0.556014] Switched to high resolution mode on CPU 0
[    0.556568] Switched to high resolution mode on CPU 1
[    0.560012] pnp: PnP ACPI init
[    0.560021] ACPI: bus type pnp registered
[    0.565019] pnp: PnP ACPI: found 11 devices
[    0.565022] ACPI: ACPI bus type pnp unregistered
[    0.565025] PnPBIOS: Disabled by ACPI PNP
[    0.565035] system 00:00: iomem range 0xe0000000-0xefffffff has been reserved
[    0.565043] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.565046] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.565049] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.565053] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.565056] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.565059] system 00:02: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.565063] system 00:02: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.565066] system 00:02: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.565073] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.565081] system 00:06: ioport range 0x380-0x383 has been reserved
[    0.565084] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.565087] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.565090] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.565093] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.565096] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.565103] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.565106] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.599856] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff]
[    0.599859] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.599862] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.599867] pci 0000:00:01.0:   MEM window: 0xdc000000-0xddffffff
[    0.599872] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.599877] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.599882] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.599888] pci 0000:00:1c.0:   MEM window: 0xd8000000-0xd9ffffff
[    0.599894] pci 0000:00:1c.0:   PREFETCH window: 0x000000d2000000-0x000000d3ffffff
[    0.599903] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.599907] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.599914] pci 0000:00:1c.1:   MEM window: 0xd6000000-0xd7ffffff
[    0.599920] pci 0000:00:1c.1:   PREFETCH window: 0x000000d0000000-0x000000d1ffffff
[    0.599928] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.599932] pci 0000:00:1c.2:   IO window: 0x5000-0x5fff
[    0.599939] pci 0000:00:1c.2:   MEM window: 0xda000000-0xdbffffff
[    0.599945] pci 0000:00:1c.2:   PREFETCH window: 0x000000d4000000-0x000000d5ffffff
[    0.599954] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.599956] pci 0000:00:1e.0:   IO window: disabled
[    0.599963] pci 0000:00:1e.0:   MEM window: 0xde000000-0xde0fffff
[    0.599968] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.599985] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.599990] pci 0000:00:01.0: setting latency timer to 64
[    0.600000] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.600009] pci 0000:00:1c.0: setting latency timer to 64
[    0.600019] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.600025] pci 0000:00:1c.1: setting latency timer to 64
[    0.600036] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.600041] pci 0000:00:1c.2: setting latency timer to 64
[    0.600048] pci 0000:00:1e.0: enabling device (0004 -> 0006)
[    0.600055] pci 0000:00:1e.0: setting latency timer to 64
[    0.600059] bus: 00 index 0 io port: [0x00-0xffff]
[    0.600062] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.600065] bus: 01 index 0 io port: [0x2000-0x2fff]
[    0.600067] bus: 01 index 1 mmio: [0xdc000000-0xddffffff]
[    0.600070] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    0.600072] bus: 01 index 3 mmio: [0x0-0x0]
[    0.600075] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.600078] bus: 02 index 1 mmio: [0xd8000000-0xd9ffffff]
[    0.600080] bus: 02 index 2 mmio: [0xd2000000-0xd3ffffff]
[    0.600083] bus: 02 index 3 mmio: [0x0-0x0]
[    0.600085] bus: 03 index 0 io port: [0x4000-0x4fff]
[    0.600088] bus: 03 index 1 mmio: [0xd6000000-0xd7ffffff]
[    0.600090] bus: 03 index 2 mmio: [0xd0000000-0xd1ffffff]
[    0.600093] bus: 03 index 3 mmio: [0x0-0x0]
[    0.600095] bus: 05 index 0 io port: [0x5000-0x5fff]
[    0.600098] bus: 05 index 1 mmio: [0xda000000-0xdbffffff]
[    0.600100] bus: 05 index 2 mmio: [0xd4000000-0xd5ffffff]
[    0.600103] bus: 05 index 3 mmio: [0x0-0x0]
[    0.600105] bus: 07 index 0 mmio: [0x0-0x0]
[    0.600108] bus: 07 index 1 mmio: [0xde000000-0xde0fffff]
[    0.600110] bus: 07 index 2 mmio: [0x0-0x0]
[    0.600112] bus: 07 index 3 io port: [0x00-0xffff]
[    0.600115] bus: 07 index 4 mmio: [0x000000-0xffffffff]
[    0.600125] NET: Registered protocol family 2
[    0.612064] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.612347] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.612873] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.613163] TCP: Hash tables configured (established 131072 bind 65536)
[    0.613166] TCP reno registered
[    0.620099] NET: Registered protocol family 1
[    0.620239] checking if image is initramfs... it is
[    1.333298] Freeing initrd memory: 7382k freed
[    1.333342] Simple Boot Flag at 0x35 set to 0x1
[    1.333553] cpufreq: No nForce2 chipset.
[    1.333721] audit: initializing netlink socket (disabled)
[    1.333749] type=2000 audit(1249864047.332:1): initialized
[    1.342207] highmem bounce pool size: 64 pages
[    1.342213] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.343796] VFS: Disk quotas dquot_6.5.1
[    1.343863] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.344585] fuse init (API version 7.10)
[    1.344684] msgmni has been set to 1724
[    1.344900] alg: No test for stdrng (krng)
[    1.344913] io scheduler noop registered
[    1.344916] io scheduler anticipatory registered
[    1.344918] io scheduler deadline registered
[    1.344934] io scheduler cfq registered (default)
[    1.345075] pci 0000:01:00.0: Boot video device
[    1.351389] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.351430] pcieport-driver 0000:00:01.0: found MSI capability
[    1.351458] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.351469] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.351486] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.351547] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.351598] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.351632] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.351649] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.351665] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.351679] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.351757] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.351808] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.351843] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.351860] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.351874] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.351888] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.351966] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.352023] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.352058] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[    1.352075] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.352091] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.352105] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.352198] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.352645] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
[    1.352695] pciehp 0000:00:1c.0:pcie02: service driver pciehp loaded
[    1.353102] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
[    1.353145] pciehp 0000:00:1c.1:pcie02: service driver pciehp loaded
[    1.353549] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 27d4 ss_vid 0 ss_did 0
[    1.353588] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
[    1.353598] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.354371] ACPI: AC Adapter [ACAD] (off-line)
[    1.432047] ACPI: Battery Slot [BAT0] (battery present)
[    1.432137] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.432141] ACPI: Power Button (FF) [PWRF]
[    1.432191] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.432194] ACPI: Power Button (CM) [PWRB]
[    1.432245] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.432248] ACPI: Sleep Button (CM) [SLPB]
[    1.432297] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    1.432933] ACPI: Lid Switch [LID]
[    1.433587] ACPI: SSDT 3FE7C189, 0238 (r1 HP     30BD         3000 INTL 20050624)
[    1.434028] ACPI: SSDT 3FE7BC42, 04C2 (r1 HP     30BD         3001 INTL 20050624)
[    1.436801] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.436829] processor ACPI_CPU:00: registered as cooling_device0
[    1.436833] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.437243] ACPI: SSDT 3FE7C3C1, 00C8 (r1 HP     30BD         3000 INTL 20050624)
[    1.437638] ACPI: SSDT 3FE7C104, 0085 (r1 HP     30BD         3000 INTL 20050624)
[    1.438644] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.438667] processor ACPI_CPU:01: registered as cooling_device1
[    1.438671] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.448430] thermal LNXTHERM:01: registered as thermal_zone0
[    1.458071] ACPI: Thermal Zone [THR1] (0 C)
[    1.458131] isapnp: Scanning for PnP cards...
[    1.812074] isapnp: No Plug & Play device found
[    1.828272] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.829448] brd: module loaded
[    1.829814] loop: module loaded
[    1.829891] Fixed MDIO Bus: probed
[    1.829897] PPP generic driver version 2.4.2
[    1.829965] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.830000] Driver 'sd' needs updating - please use bus_type methods
[    1.830010] Driver 'sr' needs updating - please use bus_type methods
[    1.830055] ahci 0000:00:1f.2: version 3.0
[    1.830074] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.830117] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.830203] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.830207] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.830213] ahci 0000:00:1f.2: setting latency timer to 64
[    1.830429] scsi0 : ahci
[    1.830537] scsi1 : ahci
[    1.830608] scsi2 : ahci
[    1.830683] scsi3 : ahci
[    1.830791] ata1: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304500 irq 2299
[    1.830794] ata2: DUMMY
[    1.830797] ata3: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304600 irq 2299
[    1.830800] ata4: DUMMY
[    2.148027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.148641] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.148648] ata1.00: ATA-7: WDC WD1200BEVS-60LAT0, 01.06M01, max UDMA/100
[    2.148651] ata1.00: 234441648 sectors, multi 16: LBA48 
[    2.149309] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.149341] ata1.00: configured for UDMA/100
[    2.484022] ata3: SATA link down (SStatus 0 SControl 300)
[    2.500138] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
[    2.500245] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    2.500265] sd 0:0:0:0: [sda] Write Protect is off
[    2.500268] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.500299] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.500369] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    2.500386] sd 0:0:0:0: [sda] Write Protect is off
[    2.500389] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.500418] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.500423]  sda: sda1 sda2 < sda5 >
[    2.571052] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.571102] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.571162] ata_piix 0000:00:1f.1: version 2.12
[    2.571170] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.571209] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.571293] scsi4 : ata_piix
[    2.571364] scsi5 : ata_piix
[    2.571975] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    2.571978] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    2.732502] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-4084N, KQ09, max MWDMA2
[    2.748438] ata5.00: configured for MWDMA2
[    2.750762] ata6: port disabled. ignoring.
[    2.754224] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 5
[    2.765924] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.765928] Uniform CD-ROM driver Revision: 3.20
[    2.766025] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.766065] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.766825] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.766848] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.766865] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.766869] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.766938] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.770860] ehci_hcd 0000:00:1d.7: debug port 1
[    2.770868] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.770884] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xde304000
[    2.784010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.784104] usb usb1: configuration #1 chosen from 1 choice
[    2.784136] hub 1-0:1.0: USB hub found
[    2.784146] hub 1-0:1.0: 8 ports detected
[    2.784279] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.784297] uhci_hcd: USB Universal Host Controller Interface driver
[    2.784325] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.784332] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.784336] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.784385] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.784413] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    2.784498] usb usb2: configuration #1 chosen from 1 choice
[    2.784526] hub 2-0:1.0: USB hub found
[    2.784534] hub 2-0:1.0: 2 ports detected
[    2.784635] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.784642] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.784646] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.784691] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.784728] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    2.784814] usb usb3: configuration #1 chosen from 1 choice
[    2.784843] hub 3-0:1.0: USB hub found
[    2.784850] hub 3-0:1.0: 2 ports detected
[    2.784944] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.784951] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.784955] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.785001] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.785037] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    2.785122] usb usb4: configuration #1 chosen from 1 choice
[    2.785151] hub 4-0:1.0: USB hub found
[    2.785161] hub 4-0:1.0: 2 ports detected
[    2.785263] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.785270] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.785274] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.785324] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.785359] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    2.785439] usb usb5: configuration #1 chosen from 1 choice
[    2.785467] hub 5-0:1.0: USB hub found
[    2.785474] hub 5-0:1.0: 2 ports detected
[    2.785636] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.803970] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.803977] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.808046] mice: PS/2 mouse device common for all mice
[    2.828082] rtc_cmos 00:08: RTC can wake from S4
[    2.828119] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.828153] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.828222] device-mapper: uevent: version 1.0.3
[    2.828322] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.828415] device-mapper: multipath: version 1.0.5 loaded
[    2.828418] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.828511] EISA: Probing bus 0 at eisa.0
[    2.828519] Cannot allocate resource for EISA slot 1
[    2.828523] Cannot allocate resource for EISA slot 2
[    2.828526] Cannot allocate resource for EISA slot 3
[    2.828528] Cannot allocate resource for EISA slot 4
[    2.828531] Cannot allocate resource for EISA slot 5
[    2.828546] EISA: Detected 0 cards.
[    2.828688] cpuidle: using governor ladder
[    2.828826] cpuidle: using governor menu
[    2.829409] TCP cubic registered
[    2.829526] NET: Registered protocol family 10
[    2.830012] lo: Disabled Privacy Extensions
[    2.830409] NET: Registered protocol family 17
[    2.830427] Bluetooth: L2CAP ver 2.11
[    2.830429] Bluetooth: L2CAP socket layer initialized
[    2.830432] Bluetooth: SCO (Voice Link) ver 0.6
[    2.830434] Bluetooth: SCO socket layer initialized
[    2.830456] Marking TSC unstable due to TSC halts in idle
[    2.830481] Bluetooth: RFCOMM socket layer initialized
[    2.830489] Bluetooth: RFCOMM TTY layer initialized
[    2.830491] Bluetooth: RFCOMM ver 1.10
[    2.831196] Using IPI No-Shortcut mode
[    2.831272] registered taskstats version 1
[    2.831409]   Magic number: 5:684:455
[    2.831503] rtc_cmos 00:08: setting system clock to 2009-08-10 00:27:30 UTC (1249864050)
[    2.831508] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.831510] EDD information not available.
[    2.831835] Freeing unused kernel memory: 532k freed
[    2.832007] Write protecting the kernel text: 4112k
[    2.832074] Write protecting the kernel read-only data: 1524k
[    2.839567] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.101033] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    3.116054] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    3.116058] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    3.127687] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.127703] e1000e 0000:05:00.0: setting latency timer to 64
[    3.127944] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[    3.133233] ohci1394 0000:07:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.133242] ohci1394 0000:07:05.0: setting latency timer to 64
[    3.186004] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[de000000-de0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.237042] usb 1-4: configuration #1 chosen from 1 choice
[    3.301129] 0000:05:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:36:f7:2f:7c
[    3.301134] 0000:05:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.301211] 0000:05:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[    3.522580] PM: Starting manual resume from disk
[    3.522584] PM: Resume from partition 8:5
[    3.522586] PM: Checking hibernation image.
[    3.522767] PM: Resume from disk failed.
[    3.575724] kjournald starting.  Commit interval 5 seconds
[    3.575755] EXT3-fs: mounted filesystem with ordered data mode.
[    4.492563] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc000f8c8ef00]
[   10.815223] udev: starting version 141
[   11.077916] acpi device:05: registered as cooling_device2
[   11.078214] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[   11.112117] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.394926] Linux agpgart interface v0.103
[   11.505830] intel_rng: FWH not detected
[   11.530572] cfg80211: Calling CRDA to update world regulatory domain
[   11.544733] ricoh-mmc: Ricoh MMC Controller disabling driver
[   11.544736] ricoh-mmc: Copyright(c) Philip Langdale
[   11.544775] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   11.544793] ricoh-mmc: Controller is now disabled.
[   11.633331] cfg80211: World regulatory domain updated:
[   11.633336]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.633339]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.633343]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.633346]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.633349]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.633352]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.690891] sdhci: Secure Digital Host Controller Interface driver
[   11.690895] sdhci: Copyright(c) Pierre Ossman
[   11.722680] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
[   11.722694] sdhci-pci 0000:07:05.1: enabling device (0000 -> 0002)
[   11.722703] sdhci-pci 0000:07:05.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   11.722771] sdhci-pci 0000:07:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   11.722780] sdhci-pci 0000:07:05.1: setting latency timer to 64
[   11.724847] mmc0: SDHCI controller on PCI [0000:07:05.1] using DMA
[   11.886802] Linux video capture interface: v2.00
[   11.945017] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   11.999112] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1810)
[   11.999717] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   11.999982] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   11.999985] uvcvideo: Failed to initialize the device (-5).
[   12.000039] usbcore: registered new interface driver uvcvideo
[   12.000071] USB Video Class driver (v0.1.0)
[   12.015403] iTCO_vendor_support: vendor-support=0
[   12.019247] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.019449] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
[   12.019542] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.101112] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   12.241080] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   12.241085] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   12.241171] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.241187] iwl3945 0000:02:00.0: setting latency timer to 64
[   12.241240] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   12.241468] iwl3945 0000:02:00.0: irq 2297 for MSI/MSI-X
[   12.282563] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.288039] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   12.461127] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.461209] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.726730] lp: driver loaded but no devices found
[   12.829820] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   12.862342] EXT3 FS on sda1, internal journal
[   13.069723] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   13.129481] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[  195.565030] type=1505 audit(1249864243.232:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2121
[  195.621030] type=1505 audit(1249864243.288:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2125
[  195.621154] type=1505 audit(1249864243.288:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2125
[  195.621207] type=1505 audit(1249864243.288:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2125
[  195.621254] type=1505 audit(1249864243.288:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2125
[  195.782884] type=1505 audit(1249864243.448:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2130
[  195.783093] type=1505 audit(1249864243.448:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2130
[  195.839207] type=1505 audit(1249864243.504:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2134
[  195.869808] type=1505 audit(1249864243.536:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2138
[  196.086750] ip_tables: (C) 2000-2006 Netfilter Core Team
[  196.146499] nf_conntrack version 0.5.0 (16359 buckets, 65436 max)
[  196.146723] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[  196.146726] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[  196.146729] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  196.237927] ip6_tables: (C) 2000-2006 Netfilter Core Team
[  207.480848] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  207.480852] Bluetooth: BNEP filters: protocol multicast
[  207.535303] Bridge firewalling registered
[  208.664499] ppdev: user-space parallel port driver
[  212.352474] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[  212.409137] e1000e 0000:05:00.0: irq 2298 for MSI/MSI-X
[  212.410513] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  212.411898] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-1.ucode
[  212.654420] Registered led device: iwl-phy0:radio
[  212.654513] Registered led device: iwl-phy0:assoc
[  212.654553] Registered led device: iwl-phy0:RX
[  212.654591] Registered led device: iwl-phy0:TX
[  212.664482] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  221.500140] Clocksource tsc unstable (delta = -251840457 ns)
[  451.321150] wlan0: authenticate with AP 00:1e:8c:03:16:42
[  451.323168] wlan0: authenticated
[  451.323180] wlan0: associate with AP 00:1e:8c:03:16:42
[  451.325543] wlan0: RX AssocResp from 00:1e:8c:03:16:42 (capab=0x411 status=0 aid=2)
[  451.325552] wlan0: associated
[  451.329739] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  461.376122] wlan0: no IPv6 routers present
[ 3478.341151] CE: hpet increasing min_delta_ns to 15000 nsec
```

---

### Post by bhaverkamp on 2009-08-10
That looks like the dmesg log and I don't see any issues. Now attach output of 'cat /var/log/messages'

---

### Post by TheForumTroll on 2009-08-10
Hmm, there is a huge pause here:

```

[   13.129481] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[  195.565030] type=1505 audit(1249864243.232:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2121

```

---

### Post by haiyun211 on 2009-08-11
> **bhaverkamp said:**
> That looks like the dmesg log and I don't see any issues. Now attach output of 'cat /var/log/messages'

ok here is the output of the second one.

```
Aug 10 22:24:59 haiyun-laptop kernel: [    1.333333] Freeing initrd memory: 7382k freed
Aug 10 22:24:59 haiyun-laptop kernel: [    1.333376] Simple Boot Flag at 0x35 set to 0x1
Aug 10 22:24:59 haiyun-laptop kernel: [    1.333588] cpufreq: No nForce2 chipset.
Aug 10 22:24:59 haiyun-laptop kernel: [    1.333754] audit: initializing netlink socket (disabled)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.333782] type=2000 audit(1249964663.333:1): initialized
Aug 10 22:24:59 haiyun-laptop kernel: [    1.342243] highmem bounce pool size: 64 pages
Aug 10 22:24:59 haiyun-laptop kernel: [    1.342249] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Aug 10 22:24:59 haiyun-laptop kernel: [    1.343832] VFS: Disk quotas dquot_6.5.1
Aug 10 22:24:59 haiyun-laptop kernel: [    1.343900] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.344623] fuse init (API version 7.10)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.344722] msgmni has been set to 1724
Aug 10 22:24:59 haiyun-laptop kernel: [    1.344937] alg: No test for stdrng (krng)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.344950] io scheduler noop registered
Aug 10 22:24:59 haiyun-laptop kernel: [    1.344953] io scheduler anticipatory registered
Aug 10 22:24:59 haiyun-laptop kernel: [    1.344955] io scheduler deadline registered
Aug 10 22:24:59 haiyun-laptop kernel: [    1.344971] io scheduler cfq registered (default)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.351879] pcieport-driver 0000:00:01.0: found MSI capability
Aug 10 22:24:59 haiyun-laptop kernel: [    1.352051] pcieport-driver 0000:00:1c.0: found MSI capability
Aug 10 22:24:59 haiyun-laptop kernel: [    1.352262] pcieport-driver 0000:00:1c.1: found MSI capability
Aug 10 22:24:59 haiyun-laptop kernel: [    1.352471] pcieport-driver 0000:00:1c.2: found MSI capability
Aug 10 22:24:59 haiyun-laptop kernel: [    1.352643] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 10 22:24:59 haiyun-laptop kernel: [    1.353090] pciehp 0000:00:1c.0:pcie02: HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
Aug 10 22:24:59 haiyun-laptop kernel: [    1.353548] pciehp 0000:00:1c.1:pcie02: HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
Aug 10 22:24:59 haiyun-laptop kernel: [    1.353995] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 27d4 ss_vid 0 ss_did 0
Aug 10 22:24:59 haiyun-laptop kernel: [    1.354045] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Aug 10 22:24:59 haiyun-laptop kernel: [    1.354932] ACPI: AC Adapter [ACAD] (off-line)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.427542] ACPI: Battery Slot [BAT0] (battery present)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.427632] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Aug 10 22:24:59 haiyun-laptop kernel: [    1.427636] ACPI: Power Button (FF) [PWRF]
Aug 10 22:24:59 haiyun-laptop kernel: [    1.427686] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Aug 10 22:24:59 haiyun-laptop kernel: [    1.427689] ACPI: Power Button (CM) [PWRB]
Aug 10 22:24:59 haiyun-laptop kernel: [    1.427740] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Aug 10 22:24:59 haiyun-laptop kernel: [    1.427743] ACPI: Sleep Button (CM) [SLPB]
Aug 10 22:24:59 haiyun-laptop kernel: [    1.427793] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Aug 10 22:24:59 haiyun-laptop kernel: [    1.428744] ACPI: Lid Switch [LID]
Aug 10 22:24:59 haiyun-laptop kernel: [    1.429396] ACPI: SSDT 3FE7C189, 0238 (r1 HP     30BD         3000 INTL 20050624)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.429837] ACPI: SSDT 3FE7BC42, 04C2 (r1 HP     30BD         3001 INTL 20050624)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.432610] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Aug 10 22:24:59 haiyun-laptop kernel: [    1.432638] processor ACPI_CPU:00: registered as cooling_device0
Aug 10 22:24:59 haiyun-laptop kernel: [    1.432642] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.433051] ACPI: SSDT 3FE7C3C1, 00C8 (r1 HP     30BD         3000 INTL 20050624)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.433447] ACPI: SSDT 3FE7C104, 0085 (r1 HP     30BD         3000 INTL 20050624)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.434456] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Aug 10 22:24:59 haiyun-laptop kernel: [    1.434479] processor ACPI_CPU:01: registered as cooling_device1
Aug 10 22:24:59 haiyun-laptop kernel: [    1.434483] ACPI: Processor [CPU1] (supports 8 throttling states)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.443109] thermal LNXTHERM:01: registered as thermal_zone0
Aug 10 22:24:59 haiyun-laptop kernel: [    1.452399] ACPI: Thermal Zone [THR1] (0 C)
Aug 10 22:24:59 haiyun-laptop kernel: [    1.452459] isapnp: Scanning for PnP cards...
Aug 10 22:24:59 haiyun-laptop kernel: [    1.806446] isapnp: No Plug & Play device found
Aug 10 22:24:59 haiyun-laptop kernel: [    1.820273] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Aug 10 22:24:59 haiyun-laptop kernel: [    1.821450] brd: module loaded
Aug 10 22:24:59 haiyun-laptop kernel: [    1.821815] loop: module loaded
Aug 10 22:24:59 haiyun-laptop kernel: [    1.821891] Fixed MDIO Bus: probed
Aug 10 22:24:59 haiyun-laptop kernel: [    1.821897] PPP generic driver version 2.4.2
Aug 10 22:24:59 haiyun-laptop kernel: [    1.821964] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Aug 10 22:24:59 haiyun-laptop kernel: [    1.821998] Driver 'sd' needs updating - please use bus_type methods
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822009] Driver 'sr' needs updating - please use bus_type methods
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822072] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822202] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822206] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822426] scsi0 : ahci
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822534] scsi1 : ahci
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822605] scsi2 : ahci
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822680] scsi3 : ahci
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822788] ata1: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304500 irq 2299
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822791] ata2: DUMMY
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822795] ata3: SATA max UDMA/133 abar m1024@0xde304400 port 0xde304600 irq 2299
Aug 10 22:24:59 haiyun-laptop kernel: [    1.822797] ata4: DUMMY
Aug 10 22:24:59 haiyun-laptop kernel: [    2.140026] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 10 22:24:59 haiyun-laptop kernel: [    2.140640] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Aug 10 22:24:59 haiyun-laptop kernel: [    2.140646] ata1.00: ATA-7: WDC WD1200BEVS-60LAT0, 01.06M01, max UDMA/100
Aug 10 22:24:59 haiyun-laptop kernel: [    2.140649] ata1.00: 234441648 sectors, multi 16: LBA48 
Aug 10 22:24:59 haiyun-laptop kernel: [    2.141308] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Aug 10 22:24:59 haiyun-laptop kernel: [    2.141340] ata1.00: configured for UDMA/100
Aug 10 22:24:59 haiyun-laptop kernel: [    2.476022] ata3: SATA link down (SStatus 0 SControl 300)
Aug 10 22:24:59 haiyun-laptop kernel: [    2.492140] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-6 01.0 PQ: 0 ANSI: 5
Aug 10 22:24:59 haiyun-laptop kernel: [    2.492246] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
Aug 10 22:24:59 haiyun-laptop kernel: [    2.492267] sd 0:0:0:0: [sda] Write Protect is off
Aug 10 22:24:59 haiyun-laptop kernel: [    2.492300] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 10 22:24:59 haiyun-laptop kernel: [    2.492369] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
Aug 10 22:24:59 haiyun-laptop kernel: [    2.492386] sd 0:0:0:0: [sda] Write Protect is off
Aug 10 22:24:59 haiyun-laptop kernel: [    2.492419] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 10 22:24:59 haiyun-laptop kernel: [    2.492423]  sda: sda1 sda2 < sda5 >
Aug 10 22:24:59 haiyun-laptop kernel: [    2.571151] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 10 22:24:59 haiyun-laptop kernel: [    2.571201] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 10 22:24:59 haiyun-laptop kernel: [    2.571268] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 10 22:24:59 haiyun-laptop kernel: [    2.571393] scsi4 : ata_piix
Aug 10 22:24:59 haiyun-laptop kernel: [    2.571463] scsi5 : ata_piix
Aug 10 22:24:59 haiyun-laptop kernel: [    2.572090] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
Aug 10 22:24:59 haiyun-laptop kernel: [    2.572094] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
Aug 10 22:24:59 haiyun-laptop kernel: [    2.736503] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-4084N, KQ09, max MWDMA2
Aug 10 22:24:59 haiyun-laptop kernel: [    2.752439] ata5.00: configured for MWDMA2
Aug 10 22:24:59 haiyun-laptop kernel: [    2.758226] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 5
Aug 10 22:24:59 haiyun-laptop kernel: [    2.769927] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 10 22:24:59 haiyun-laptop kernel: [    2.769931] Uniform CD-ROM driver Revision: 3.20
Aug 10 22:24:59 haiyun-laptop kernel: [    2.770068] sr 4:0:0:0: Attached scsi generic sg1 type 5
Aug 10 22:24:59 haiyun-laptop kernel: [    2.770828] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Aug 10 22:24:59 haiyun-laptop kernel: [    2.770852] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 10 22:24:59 haiyun-laptop kernel: [    2.770873] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 10 22:24:59 haiyun-laptop kernel: [    2.770943] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Aug 10 22:24:59 haiyun-laptop kernel: [    2.774857] ehci_hcd 0000:00:1d.7: debug port 1
Aug 10 22:24:59 haiyun-laptop kernel: [    2.774881] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xde304000
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788106] usb usb1: configuration #1 chosen from 1 choice
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788138] hub 1-0:1.0: USB hub found
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788147] hub 1-0:1.0: 8 ports detected
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788280] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788298] uhci_hcd: USB Universal Host Controller Interface driver
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788325] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788336] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788385] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788412] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788496] usb usb2: configuration #1 chosen from 1 choice
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788524] hub 2-0:1.0: USB hub found
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788532] hub 2-0:1.0: 2 ports detected
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788633] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788644] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788689] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788725] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788811] usb usb3: configuration #1 chosen from 1 choice
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788840] hub 3-0:1.0: USB hub found
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788848] hub 3-0:1.0: 2 ports detected
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788943] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788954] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 10 22:24:59 haiyun-laptop kernel: [    2.788999] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789035] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789121] usb usb4: configuration #1 chosen from 1 choice
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789149] hub 4-0:1.0: USB hub found
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789160] hub 4-0:1.0: 2 ports detected
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789262] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789273] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789322] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789358] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789438] usb usb5: configuration #1 chosen from 1 choice
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789465] hub 5-0:1.0: USB hub found
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789473] hub 5-0:1.0: 2 ports detected
Aug 10 22:24:59 haiyun-laptop kernel: [    2.789634] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 10 22:24:59 haiyun-laptop kernel: [    2.807127] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 10 22:24:59 haiyun-laptop kernel: [    2.807134] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 10 22:24:59 haiyun-laptop kernel: [    2.808047] mice: PS/2 mouse device common for all mice
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828083] rtc_cmos 00:08: RTC can wake from S4
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828120] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828154] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828223] device-mapper: uevent: version 1.0.3
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828321] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828413] device-mapper: multipath: version 1.0.5 loaded
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828416] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828510] EISA: Probing bus 0 at eisa.0
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828518] Cannot allocate resource for EISA slot 1
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828521] Cannot allocate resource for EISA slot 2
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828524] Cannot allocate resource for EISA slot 3
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828526] Cannot allocate resource for EISA slot 4
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828529] Cannot allocate resource for EISA slot 5
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828545] EISA: Detected 0 cards.
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828687] cpuidle: using governor ladder
Aug 10 22:24:59 haiyun-laptop kernel: [    2.828825] cpuidle: using governor menu
Aug 10 22:24:59 haiyun-laptop kernel: [    2.829407] TCP cubic registered
Aug 10 22:24:59 haiyun-laptop kernel: [    2.829525] NET: Registered protocol family 10
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830011] lo: Disabled Privacy Extensions
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830408] NET: Registered protocol family 17
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830426] Bluetooth: L2CAP ver 2.11
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830428] Bluetooth: L2CAP socket layer initialized
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830432] Bluetooth: SCO (Voice Link) ver 0.6
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830434] Bluetooth: SCO socket layer initialized
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830456] Marking TSC unstable due to TSC halts in idle
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830481] Bluetooth: RFCOMM socket layer initialized
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830488] Bluetooth: RFCOMM TTY layer initialized
Aug 10 22:24:59 haiyun-laptop kernel: [    2.830491] Bluetooth: RFCOMM ver 1.10
Aug 10 22:24:59 haiyun-laptop kernel: [    2.831209] Using IPI No-Shortcut mode
Aug 10 22:24:59 haiyun-laptop kernel: [    2.831284] registered taskstats version 1
Aug 10 22:24:59 haiyun-laptop kernel: [    2.831421]   Magic number: 5:633:413
Aug 10 22:24:59 haiyun-laptop kernel: [    2.831515] rtc_cmos 00:08: setting system clock to 2009-08-11 04:24:25 UTC (1249964665)
Aug 10 22:24:59 haiyun-laptop kernel: [    2.831519] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 10 22:24:59 haiyun-laptop kernel: [    2.831521] EDD information not available.
Aug 10 22:24:59 haiyun-laptop kernel: [    2.831847] Freeing unused kernel memory: 532k freed
Aug 10 22:24:59 haiyun-laptop kernel: [    2.832017] Write protecting the kernel text: 4112k
Aug 10 22:24:59 haiyun-laptop kernel: [    2.832083] Write protecting the kernel read-only data: 1524k
Aug 10 22:24:59 haiyun-laptop kernel: [    2.839625] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Aug 10 22:24:59 haiyun-laptop kernel: [    3.095980] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Aug 10 22:24:59 haiyun-laptop kernel: [    3.095984] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Aug 10 22:24:59 haiyun-laptop kernel: [    3.096074] e1000e 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug 10 22:24:59 haiyun-laptop kernel: [    3.101035] usb 1-4: new high speed USB device using ehci_hcd and address 2
Aug 10 22:24:59 haiyun-laptop kernel: [    3.139476] ohci1394 0000:07:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 10 22:24:59 haiyun-laptop kernel: [    3.191251] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[de000000-de0007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Aug 10 22:24:59 haiyun-laptop kernel: [    3.233149] 0000:05:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:36:f7:2f:7c
Aug 10 22:24:59 haiyun-laptop kernel: [    3.233153] 0000:05:00.0: eth0: Intel(R) PRO/1000 Network Connection
Aug 10 22:24:59 haiyun-laptop kernel: [    3.233231] 0000:05:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
Aug 10 22:24:59 haiyun-laptop kernel: [    3.239913] usb 1-4: configuration #1 chosen from 1 choice
Aug 10 22:24:59 haiyun-laptop kernel: [    3.523336] PM: Starting manual resume from disk
Aug 10 22:24:59 haiyun-laptop kernel: [    3.576059] kjournald starting.  Commit interval 5 seconds
Aug 10 22:24:59 haiyun-laptop kernel: [    3.576079] EXT3-fs: mounted filesystem with ordered data mode.
Aug 10 22:24:59 haiyun-laptop kernel: [   10.726580] udev: starting version 141
Aug 10 22:24:59 haiyun-laptop kernel: [   11.313737] acpi device:05: registered as cooling_device2
Aug 10 22:24:59 haiyun-laptop kernel: [   11.313996] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
Aug 10 22:24:59 haiyun-laptop kernel: [   11.317220] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.332642] Linux video capture interface: v2.00
Aug 10 22:24:59 haiyun-laptop kernel: [   11.437297] intel_rng: FWH not detected
Aug 10 22:24:59 haiyun-laptop kernel: [   11.463923] Linux agpgart interface v0.103
Aug 10 22:24:59 haiyun-laptop kernel: [   11.516106] cfg80211: Calling CRDA to update world regulatory domain
Aug 10 22:24:59 haiyun-laptop kernel: [   11.585816] sdhci: Secure Digital Host Controller Interface driver
Aug 10 22:24:59 haiyun-laptop kernel: [   11.585819] sdhci: Copyright(c) Pierre Ossman
Aug 10 22:24:59 haiyun-laptop kernel: [   11.587739] sdhci-pci 0000:07:05.1: SDHCI controller found [1180:0822] (rev 19)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.587753] sdhci-pci 0000:07:05.1: enabling device (0000 -> 0002)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.587761] sdhci-pci 0000:07:05.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug 10 22:24:59 haiyun-laptop kernel: [   11.588805] sdhci-pci 0000:07:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
Aug 10 22:24:59 haiyun-laptop kernel: [   11.590908] mmc0: SDHCI controller on PCI [0000:07:05.1] using DMA
Aug 10 22:24:59 haiyun-laptop kernel: [   11.710858] cfg80211: World regulatory domain updated:
Aug 10 22:24:59 haiyun-laptop kernel: [   11.710862] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.710865] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.710869] ^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.710872] ^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.710875] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.710878] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.756737] ricoh-mmc: Ricoh MMC Controller disabling driver
Aug 10 22:24:59 haiyun-laptop kernel: [   11.756740] ricoh-mmc: Copyright(c) Philip Langdale
Aug 10 22:24:59 haiyun-laptop kernel: [   11.756778] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.756797] ricoh-mmc: Controller is now disabled.
Aug 10 22:24:59 haiyun-laptop kernel: [   11.785020] input: PC Speaker as /devices/platform/pcspkr/input/input7
Aug 10 22:24:59 haiyun-laptop kernel: [   11.943756] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1810)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.945950] usbcore: registered new interface driver uvcvideo
Aug 10 22:24:59 haiyun-laptop kernel: [   11.945954] USB Video Class driver (v0.1.0)
Aug 10 22:24:59 haiyun-laptop kernel: [   11.992437] iTCO_vendor_support: vendor-support=0
Aug 10 22:24:59 haiyun-laptop kernel: [   12.008124] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
Aug 10 22:24:59 haiyun-laptop kernel: [   12.008262] iTCO_wdt: Found a ICH7-M or ICH7-U TCO device (Version=2, TCOBASE=0x1060)
Aug 10 22:24:59 haiyun-laptop kernel: [   12.008333] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Aug 10 22:24:59 haiyun-laptop kernel: [   12.055280] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Aug 10 22:24:59 haiyun-laptop kernel: [   12.139186] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Aug 10 22:24:59 haiyun-laptop kernel: [   12.139190] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Aug 10 22:24:59 haiyun-laptop kernel: [   12.139267] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug 10 22:24:59 haiyun-laptop kernel: [   12.139363] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Aug 10 22:24:59 haiyun-laptop kernel: [   12.182564] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Aug 10 22:24:59 haiyun-laptop kernel: [   12.350360] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug 10 22:24:59 haiyun-laptop kernel: [   12.560406] lp: driver loaded but no devices found
Aug 10 22:24:59 haiyun-laptop kernel: [   12.662727] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
Aug 10 22:24:59 haiyun-laptop kernel: [   12.696216] EXT3 FS on sda1, internal journal
Aug 10 22:24:59 haiyun-laptop kernel: [   13.021073] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
Aug 10 22:24:59 haiyun-laptop kernel: [   13.081400] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Aug 10 22:24:59 haiyun-laptop kernel: [   35.028051] type=1505 audit(1249964697.696:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2042
Aug 10 22:24:59 haiyun-laptop kernel: [   35.083955] type=1505 audit(1249964697.748:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2046
Aug 10 22:24:59 haiyun-laptop kernel: [   35.084077] type=1505 audit(1249964697.752:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2046
Aug 10 22:24:59 haiyun-laptop kernel: [   35.084125] type=1505 audit(1249964697.752:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2046
Aug 10 22:24:59 haiyun-laptop kernel: [   35.084172] type=1505 audit(1249964697.752:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2046
Aug 10 22:24:59 haiyun-laptop kernel: [   35.245953] type=1505 audit(1249964697.912:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2051
Aug 10 22:24:59 haiyun-laptop kernel: [   35.246156] type=1505 audit(1249964697.912:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2051
Aug 10 22:24:59 haiyun-laptop kernel: [   35.291108] type=1505 audit(1249964697.956:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2055
Aug 10 22:24:59 haiyun-laptop kernel: [   35.321544] type=1505 audit(1249964697.988:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2059
Aug 10 22:24:59 haiyun-laptop kernel: [   35.538866] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 10 22:24:59 haiyun-laptop kernel: [   35.598415] nf_conntrack version 0.5.0 (16359 buckets, 65436 max)
Aug 10 22:24:59 haiyun-laptop kernel: [   35.598641] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Aug 10 22:24:59 haiyun-laptop kernel: [   35.598644] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
Aug 10 22:24:59 haiyun-laptop kernel: [   35.598647] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Aug 10 22:24:59 haiyun-laptop kernel: [   35.689857] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 10 22:25:05 haiyun-laptop kernel: [   42.920444] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Aug 10 22:25:05 haiyun-laptop kernel: [   42.920448] Bluetooth: BNEP filters: protocol multicast
Aug 10 22:25:05 haiyun-laptop kernel: [   42.976216] Bridge firewalling registered
Aug 10 22:25:07 haiyun-laptop kernel: [   44.315132] ppdev: user-space parallel port driver
Aug 10 22:25:11 haiyun-laptop kernel: [   48.406628] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 10 22:25:11 haiyun-laptop kernel: [   48.407986] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-1.ucode
Aug 10 22:25:11 haiyun-laptop kernel: [   48.795336] Registered led device: iwl-phy0:radio
Aug 10 22:25:11 haiyun-laptop kernel: [   48.795422] Registered led device: iwl-phy0:assoc
Aug 10 22:25:11 haiyun-laptop kernel: [   48.795461] Registered led device: iwl-phy0:RX
Aug 10 22:25:11 haiyun-laptop kernel: [   48.795498] Registered led device: iwl-phy0:TX
Aug 10 22:25:11 haiyun-laptop kernel: [   48.802266] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 10 22:25:17 haiyun-laptop kernel: [   54.500143] Clocksource tsc unstable (delta = -491745887 ns)
Aug 10 22:26:03 haiyun-laptop kernel: [  100.572379] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by haiyun211 on 2009-08-11
> **TheForumTroll said:**
> Hmm, there is a huge pause here:

```

[   13.129481] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[  195.565030] type=1505 audit(1249864243.232:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2121

```

Ok so do you know what might be causing this delay the delay is worse if I dont have my laptop plugged in?

---

### Post by TheForumTroll on 2009-08-11
Is it possible to disable the touchpad in the BIOS? If it is you could try that and see if it helps. I don't have a laptop so sadly I don't know much about the topic.

---

### Post by haiyun211 on 2009-08-11
Um im not sure.  How where you able to tell that there was a pause there im still way nube to this?

---

### Post by TheForumTroll on 2009-08-11
```

[   13.129481] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[  195.565030] type=1505 audit(1249864243.232:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2121

```

I'm no Linux guru so I might be way wrong here but as far as I can tell the numbers in the begining is a kernel timestamp in microseconds. If I'm correct there is a ~3minutes pause between those two lines (195 seconds = 3.25 minutes).

---

### Post by haiyun211 on 2009-08-11
Ok sounds good to me.  Ok so let me see if this sounds normal to you.  I start up and get the ubuntu splash screen and then the bar gets about half way and then stops for a about 30 seconds then starts to a black screen with all these commands that make no sense to me and then it freezes freequently and then finaly gets to the login screen.

---

### Post by TheForumTroll on 2009-08-11
Sounds like something is slow to start up. Could be the touchpad. I think that's what happens if something is really slow.

---

### Post by haiyun211 on 2009-08-11
Do you think that it could mean my touch pad is going out?  If so that sucks bad.

---

### Post by haiyun211 on 2009-08-11
Do you think that it could mean my touch pad is going out?  If so that sucks bad.

---

### Post by TheForumTroll on 2009-08-11
I would guess if it still works it is fine. Might be a driver problem tough as I said I don't have a laptop so I have no idea if I'm right or totally wrong :).

---

### Post by haiyun211 on 2009-08-11
Ok well thanks for all fo your help.

---

### Post by TheForumTroll on 2009-08-11
Have look at [this bug]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/366638"). Maybe that is it?

EDIT:Oh I just saw that you are using kernel 2.6.28-13-generic. Did you try with a new kernel? Isn't there a kernel 2.6.28-15-generic you can chose when you boot? That is if you have updated.

---

### Post by TheForumTroll on 2009-08-11
Actually I think the updated kernel is in proposed repo. You can get updates from it if you follow this guide:
[https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed")

---

### Post by haiyun211 on 2009-08-13
Well I updated the kernel and same o'l situation. I looked at the bug report and the same kind of deal but every body has different symptoms.  I mean it used to boot so fast until like a week ago.

---

### Post by haiyun211 on 2009-08-14
I tried the solution on the bug report and no go.  Any one with a solution please help this is driving me nuts the fast startup speed was one of the main reasons that I switched from windows.:(

---

### Post by haiyun211 on 2009-08-14
Bigger problem guys it did a routine drive check and it says it fails fsck of root filestatem failed and have to do manual one and won't let me in now I really don't know what to do

---

