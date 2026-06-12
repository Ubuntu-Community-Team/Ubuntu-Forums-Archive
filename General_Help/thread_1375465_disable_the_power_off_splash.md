---
title: "disable the power off splash"
date: 2010-01-07
forum: General Help
---

### Post by ant2ne on 2010-01-07
9.04 - My system is hanging at power off and restart.  forcing me to hit the power button. All I see is this progress bar that stops progressing. What I'd like to see is text fly by so I can get an idea of where it is hanging at. 

dmesg isn't helping much.

> [    0.688846] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[    0.689032] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[    0.689217] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[    0.689401] ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0
[    0.689586] ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0, disabled.
[    0.689781] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.689965] ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.
[    0.690150] ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.
[    0.690335] ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.
[    0.690520] ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0
[    0.690705] ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.
[    0.690893] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0
[    0.691077] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0
[    0.691263] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[    0.691382] ACPI: WMI: Mapper loaded
[    0.691420] SCSI subsystem initialized
[    0.691420] libata version 3.00 loaded.
[    0.691420] usbcore: registered new interface driver usbfs
[    0.691420] usbcore: registered new interface driver hub
[    0.691420] usbcore: registered new device driver usb
[    0.691420] PCI: Using ACPI for IRQ routing
[    0.704012] Bluetooth: Core ver 2.13
[    0.704029] NET: Registered protocol family 31
[    0.704029] Bluetooth: HCI device and connection manager initialized
[    0.704029] Bluetooth: HCI socket layer initialized
[    0.704029] NET: Registered protocol family 8
[    0.704029] NET: Registered protocol family 20
[    0.704038] NetLabel: Initializing
[    0.704040] NetLabel:  domain hash size = 128
[    0.704041] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.704055] NetLabel:  unlabeled traffic allowed by default
[    0.704101] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.704106] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.716063] AppArmor: AppArmor Filesystem Enabled
[    0.720010] Switched to high resolution mode on CPU 0
[    0.720534] Switched to high resolution mode on CPU 3
[    0.721639] Switched to high resolution mode on CPU 2
[    0.721686] Switched to high resolution mode on CPU 1
[    0.728022] pnp: PnP ACPI init
[    0.728032] ACPI: bus type pnp registered
[    0.731225] pnp: PnP ACPI: found 11 devices
[    0.731226] ACPI: ACPI bus type pnp unregistered
[    0.731233] system 00:00: ioport range 0x1000-0x107f has been reserved
[    0.731235] system 00:00: ioport range 0x1080-0x10ff has been reserved
[    0.731236] system 00:00: ioport range 0x1400-0x147f has been reserved
[    0.731238] system 00:00: ioport range 0x1480-0x14ff has been reserved
[    0.731240] system 00:00: ioport range 0x1800-0x187f has been reserved
[    0.731242] system 00:00: ioport range 0x1880-0x18ff has been reserved
[    0.731246] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.731248] system 00:02: ioport range 0x295-0x314 has been reserved
[    0.731250] system 00:02: ioport range 0x880-0x88f has been reserved
[    0.731255] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.731260] system 00:0a: iomem range 0xd0000-0xd3fff has been reserved
[    0.731261] system 00:0a: iomem range 0xd5800-0xd7fff has been reserved
[    0.731263] system 00:0a: iomem range 0xf0000-0xfbfff could not be reserved
[    0.731265] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.731267] system 00:0a: iomem range 0x9fef0000-0x9fefffff could not be reserved
[    0.731269] system 00:0a: iomem range 0xffff0000-0xffffffff has been reserved
[    0.731271] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.731272] system 00:0a: iomem range 0x100000-0x9feeffff could not be reserved
[    0.731274] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.731276] system 00:0a: iomem range 0xd0000000-0xdfffffff has been reserved
[    0.731278] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.731280] system 00:0a: iomem range 0xfeff0000-0xfeff0000 has been reserved
[    0.735932] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.735933] pci 0000:00:03.0:   IO window: disabled
[    0.735936] pci 0000:00:03.0:   MEM window: 0xcc000000-0xceffffff
[    0.735939] pci 0000:00:03.0:   PREFETCH window: 0x000000a0000000-0x000000bfffffff
[    0.735943] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:02
[    0.735944] pci 0000:00:0f.0:   IO window: disabled
[    0.735947] pci 0000:00:0f.0:   MEM window: 0xcfe00000-0xcfefffff
[    0.735949] pci 0000:00:0f.0:   PREFETCH window: 0x000000cfd00000-0x000000cfdfffff
[    0.735958] pci 0000:00:03.0: setting latency timer to 64
[    0.735962] pci 0000:00:0f.0: setting latency timer to 64
[    0.735965] bus: 00 index 0 io port: [0x00-0xffff]
[    0.735966] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.735968] bus: 01 index 0 mmio: [0x0-0x0]
[    0.735969] bus: 01 index 1 mmio: [0xcc000000-0xceffffff]
[    0.735971] bus: 01 index 2 mmio: [0xa0000000-0xbfffffff]
[    0.735972] bus: 01 index 3 mmio: [0x0-0x0]
[    0.735973] bus: 02 index 0 mmio: [0x0-0x0]
[    0.735974] bus: 02 index 1 mmio: [0xcfe00000-0xcfefffff]
[    0.735976] bus: 02 index 2 mmio: [0xcfd00000-0xcfdfffff]
[    0.735977] bus: 02 index 3 io port: [0x00-0xffff]
[    0.735978] bus: 02 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.735985] NET: Registered protocol family 2
[    0.772087] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.772773] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.774276] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.774724] TCP: Hash tables configured (established 262144 bind 65536)
[    0.774726] TCP reno registered
[    0.784146] NET: Registered protocol family 1
[    0.784264] checking if image is initramfs... it is
[    1.342772] Freeing initrd memory: 7774k freed
[    1.346052] audit: initializing netlink socket (disabled)
[    1.346078] type=2000 audit(1262922704.344:1): initialized
[    1.353300] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.354395] VFS: Disk quotas dquot_6.5.1
[    1.354435] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.354898] fuse init (API version 7.10)
[    1.354964] msgmni has been set to 15750
[    1.355139] alg: No test for stdrng (krng)
[    1.355148] io scheduler noop registered
[    1.355149] io scheduler anticipatory registered
[    1.355151] io scheduler deadline registered
[    1.355185] io scheduler cfq registered (default)
[    1.355330] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0e.1: Disabling HT MSI mapping<6>pci 0000:00:0e.2: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:0f.1: Disabling HT MSI mapping<6>pci 0000:00:12.0: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
[    1.374330] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.374361] pcieport-driver 0000:00:03.0: found MSI capability
[    1.374380] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
[    1.374387] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.374398] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.374442] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.374450] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.374576] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.374578] ACPI: Power Button (FF) [PWRF]
[    1.374610] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.374612] ACPI: Power Button (CM) [PWRB]
[    1.374941] processor ACPI_CPU:00: registered as cooling_device0
[    1.374944] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.374975] processor ACPI_CPU:01: registered as cooling_device1
[    1.375003] processor ACPI_CPU:02: registered as cooling_device2
[    1.375031] processor ACPI_CPU:03: registered as cooling_device3
[    1.404233] Linux agpgart interface v0.103
[    1.404240] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.404984] brd: module loaded
[    1.405238] loop: module loaded
[    1.405287] Fixed MDIO Bus: probed
[    1.405292] PPP generic driver version 2.4.2
[    1.405332] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.405351] Driver 'sd' needs updating - please use bus_type methods
[    1.405358] Driver 'sr' needs updating - please use bus_type methods
[    1.405517] sata_nv 0000:00:0e.0: version 3.5
[    1.405801] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 23
[    1.405807] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 23 (level, low) -> IRQ 23
[    1.405808] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.406041] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.406183] scsi0 : sata_nv
[    1.406263] scsi1 : sata_nv
[    1.406399] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    1.406402] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    2.138415] ata1: SATA link down (SStatus 0 SControl 300)
[    3.016053] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.024354] ata2.00: ATA-7: Hitachi HDS721075KLA330, GK8OA70M, max UDMA/133
[    3.024357] ata2.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.040357] ata2.00: configured for UDMA/133
[    3.040456] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDS72107 GK8O PQ: 0 ANSI: 5
[    3.040557] sd 1:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    3.040577] sd 1:0:0:0: [sda] Write Protect is off
[    3.040578] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040597] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.040640] sd 1:0:0:0: [sda] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    3.040651] sd 1:0:0:0: [sda] Write Protect is off
[    3.040653] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.040671] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.040673]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.087276] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.087307] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    3.087597] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 22
[    3.087601] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 22 (level, low) -> IRQ 22
[    3.087603] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    3.087630] sata_nv 0000:00:0e.1: setting latency timer to 64
[    3.087744] scsi2 : sata_nv
[    3.087810] scsi3 : sata_nv
[    3.087944] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[    3.087946] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[    3.964038] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.988153] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L05, max UDMA/100
[    4.020168] ata3.00: configured for UDMA/100
[    4.754414] ata4: SATA link down (SStatus 0 SControl 300)
[    4.755576] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L05 PQ: 0 ANSI: 5
[    4.760994] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.760998] Uniform CD-ROM driver Revision: 3.20
[    4.761088] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.761127] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    4.761424] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 21
[    4.761428] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    4.761430] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    4.761457] sata_nv 0000:00:0e.2: setting latency timer to 64
[    4.761552] scsi4 : sata_nv
[    4.761597] scsi5 : sata_nv
[    4.761723] ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 21
[    4.761726] ata6: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 21
[    5.494409] ata5: SATA link down (SStatus 0 SControl 300)
[    6.372039] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.380337] ata6.00: ATA-7: Hitachi HDS721075KLA330, GK8OA70M, max UDMA/133
[    6.380340] ata6.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.396350] ata6.00: configured for UDMA/133
[    6.396423] scsi 5:0:0:0: Direct-Access     ATA      Hitachi HDS72107 GK8O PQ: 0 ANSI: 5
[    6.396517] sd 5:0:0:0: [sdb] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    6.396534] sd 5:0:0:0: [sdb] Write Protect is off
[    6.396536] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.396564] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.396606] sd 5:0:0:0: [sdb] 1465149168 512-byte hardware sectors: (750 GB/698 GiB)
[    6.396617] sd 5:0:0:0: [sdb] Write Protect is off
[    6.396618] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.396636] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.396639]  sdb: sdb1
[    6.402427] sd 5:0:0:0: [sdb] Attached SCSI disk
[    6.402476] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    6.402544] pata_amd 0000:00:0d.0: version 0.3.10
[    6.402569] pata_amd 0000:00:0d.0: setting latency timer to 64
[    6.402648] scsi6 : pata_amd
[    6.402713] scsi7 : pata_amd
[    6.403174] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[    6.403176] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[    6.567030] ata8: port disabled. ignoring.
[    6.567381] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.567666] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 20
[    6.567670] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[AUS2] -> GSI 20 (level, low) -> IRQ 20
[    6.567678] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    6.567681] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    6.567722] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    6.567745] ehci_hcd 0000:00:0b.1: debug port 1
[    6.567749] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    6.567762] ehci_hcd 0000:00:0b.1: irq 20, io mem 0xcfffe000
[    6.576016] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    6.576090] usb usb1: configuration #1 chosen from 1 choice
[    6.576118] hub 1-0:1.0: USB hub found
[    6.576125] hub 1-0:1.0: 10 ports detected
[    6.576228] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.576511] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[    6.576514] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[AUBA] -> GSI 23 (level, low) -> IRQ 23
[    6.576521] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    6.576523] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    6.576562] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    6.576571] ohci_hcd 0000:00:0b.0: irq 23, io mem 0xcffff000
[    6.634039] usb usb2: configuration #1 chosen from 1 choice
[    6.634056] hub 2-0:1.0: USB hub found
[    6.634063] hub 2-0:1.0: 10 ports detected
[    6.634134] uhci_hcd: USB Universal Host Controller Interface driver
[    6.634189] PNP: No PS/2 controller found. Probing ports directly.
[    6.636993] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.636998] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.648051] mice: PS/2 mouse device common for all mice
[    6.684083] rtc_cmos 00:05: RTC can wake from S4
[    6.684121] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    6.684152] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    6.684218] device-mapper: uevent: version 1.0.3
[    6.684278] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    6.684380] device-mapper: multipath: version 1.0.5 loaded
[    6.684382] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.684496] cpuidle: using governor ladder
[    6.684497] cpuidle: using governor menu
[    6.684814] TCP cubic registered
[    6.684862] NET: Registered protocol family 10
[    6.685159] lo: Disabled Privacy Extensions
[    6.685369] NET: Registered protocol family 17
[    6.685382] Bluetooth: L2CAP ver 2.11
[    6.685383] Bluetooth: L2CAP socket layer initialized
[    6.685385] Bluetooth: SCO (Voice Link) ver 0.6
[    6.685386] Bluetooth: SCO socket layer initialized
[    6.685434] Bluetooth: RFCOMM socket layer initialized
[    6.685441] Bluetooth: RFCOMM TTY layer initialized
[    6.685443] Bluetooth: RFCOMM ver 1.10
[    6.685578] registered taskstats version 1
[    6.685703]   Magic number: 10:223:866
[    6.685784] rtc_cmos 00:05: setting system clock to 2010-01-08 03:51:50 UTC (1262922710)
[    6.685791] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.685792] EDD information not available.
[    6.685821] Freeing unused kernel memory: 536k freed
[    6.685998] Write protecting the kernel read-only data: 6688k
[    6.849436] FDC 0 is a post-1991 82077
[    6.877162] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    6.877541] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[    6.877544] forcedeth 0000:00:12.0: PCI INT A -> Link[AMA1] -> GSI 22 (level, low) -> IRQ 22
[    6.877548] forcedeth 0000:00:12.0: setting latency timer to 64
[    6.877586] nv_probe: set workaround bit for reversed mac addr
[    6.879265] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    6.879273] ohci1394 0000:02:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    6.879278] ohci1394 0000:02:07.0: setting latency timer to 64
[    6.929188] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[cfeff000-cfeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.116164] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    7.250370] usb 1-5: configuration #1 chosen from 1 choice
[    7.250643] hub 1-5:1.0: USB hub found
[    7.250939] hub 1-5:1.0: 4 ports detected
[    7.398161] forcedeth 0000:00:12.0: ifname eth0, PHY OUI 0x5043 @ 2, addr 00:04:4b:03:de:f6
[    7.398165] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    7.500712] PM: Starting manual resume from disk
[    7.500716] PM: Resume from partition 8:1
[    7.500717] PM: Checking hibernation image.
[    7.500924] PM: Resume from disk failed.
[    7.504941] EXT4-fs: INFO: recovery required on readonly filesystem.
[    7.504943] EXT4-fs: write access will be enabled during recovery.
[    7.516195] EXT4-fs: barriers enabled
[    7.557093] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    7.768336] usb 2-3: configuration #1 chosen from 1 choice
[    7.774150] hub 2-3:1.0: USB hub found
[    7.777164] hub 2-3:1.0: 3 ports detected
[    8.096050] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    8.212200] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0d60cee600044b03]
[    8.299181] usb 2-4: configuration #1 chosen from 1 choice
[    8.377108] usb 2-3.1: new low speed USB device using ohci_hcd and address 4
[    8.490187] usb 2-3.1: configuration #1 chosen from 1 choice
[    8.500164] usbcore: registered new interface driver hiddev
[    8.512389] input: Dell Dell Multimedia Pro Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3.1/2-3.1:1.0/input/input3
[    8.536146] generic-usb 0003:413C:2011.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell Multimedia Pro Keyboard] on usb-0000:00:0b.0-3.1/input0
[    8.549175] input: Dell Dell Multimedia Pro Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3.1/2-3.1:1.1/input/input4
[    8.572101] generic-usb 0003:413C:2011.0002: input,hidraw1: USB HID v1.10 Device [Dell Dell Multimedia Pro Keyboard] on usb-0000:00:0b.0-3.1/input1
[    8.572129] usbcore: registered new interface driver usbhid
[    8.572132] usbhid: v2.6:USB HID core driver
[    8.585115] usb 2-3.2: new low speed USB device using ohci_hcd and address 5
[    8.693198] usb 2-3.2: configuration #1 chosen from 1 choice
[    8.703746] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3.2/2-3.2:1.0/input/input5
[    8.732091] generic-usb 0003:045E:0053.0003: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0b.0-3.2/input0
[    8.889487] kjournald2 starting.  Commit interval 5 seconds
[    8.889512] EXT4-fs: delayed allocation enabled
[    8.889516] EXT4-fs: file extents enabled
[    8.896667] EXT4-fs: mballoc enabled
[    8.896668] EXT4-fs: recovery complete.
[    8.897186] EXT4-fs: mounted filesystem with ordered data mode.
[   12.111603] udev: starting version 141
[   12.835834] nvidia: module license 'NVIDIA' taints kernel.
[   12.873579] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
[   12.873610] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000
[   12.900733] Linux video capture interface: v2.00
[   12.920750] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   12.996263] gspca: main v2.3.0 registered
[   13.006203] gspca: probing 046d:08d9
[   13.034489] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.062341] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ff000000-0x00000000ffffffff - kernel bug?
[   13.062352] resource map sanity check conflict: 0xff000000 0xffffffff 0xffff0000 0xffffffff pnp 00:0a
[   13.062358] ------------[ cut here ]------------
[   13.062360] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
[   13.062361] Modules linked in: ck804xrom(+) snd videobuf_core ip_tables mtd psmouse btcx_risc gspca_zc3xx(+) gspca_main chipreg x_tables soundcore snd_page_alloc serio_raw tveeprom pcspkr(+) compat_ioctl32 videodev v4l1_compat i2c_nforce2 map_funcs nvidia(P+) joydev usbhid ohci1394 forcedeth ieee1394 floppy fbcon tileblit font bitblit softcursor
[   13.062379] Pid: 1060, comm: modprobe Tainted: P           2.6.28-17-generic #58-Ubuntu
[   13.062380] Call Trace:
[   13.062385]  [<ffffffff80250bef>] warn_on_slowpath+0x5f/0x90
[   13.062389]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
[   13.062391]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
[   13.062393]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
[   13.062397]  [<ffffffffa09452db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[   13.062399]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
[   13.062402]  [<ffffffffa09452db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[   13.062405]  [<ffffffffa094b041>] init_ck804xrom+0x41/0x59 [ck804xrom]
[   13.062408]  [<ffffffffa094b000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
[   13.062411]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
[   13.062415]  [<ffffffff8041cb29>] ? rb_insert_color+0x109/0x140
[   13.062418]  [<ffffffff80242572>] ? enqueue_entity+0x122/0x2b0
[   13.062421]  [<ffffffff802488cb>] ? enqueue_task_fair+0x7b/0x80
[   13.062423]  [<ffffffff8023e349>] ? wakeup_preempt_entity+0x59/0x60
[   13.062425]  [<ffffffff802494b8>] ? check_preempt_wakeup+0x1d8/0x250
[   13.062427]  [<ffffffff8024a5ac>] ? try_to_wake_up+0x12c/0x2e0
[   13.062431]  [<ffffffff8027f31d>] sys_init_module+0xad/0x1e0
[   13.062434]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[   13.062436] ---[ end trace ff9e329946473302 ]---
[   13.088226] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   13.088232] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[   13.088237] nvidia 0000:01:00.0: setting latency timer to 64
[   13.088421] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[   13.144926] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   13.145136] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   13.145138] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   13.145139] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   13.174891] bttv: driver version 0.9.17 loaded
[   13.174894] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   13.175065] bttv: Bt8xx card found (0).
[   13.175413] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   13.175420] bttv 0000:02:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   13.175433] bttv0: Bt878 (rev 17) at 0000:02:0a.0, irq: 18, latency: 16, mmio: 0xcfdff000
[   13.175534] bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
[   13.175536] bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
[   13.175577] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   13.175621] bttv0: tuner type=19
[   13.175623] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   13.176339] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   13.195055] Found: SST 49LF040B
[   13.195057] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank
[   13.208763] using fwh lock/unlock method
[   13.208765] number of JEDEC chips: 1
[   13.208767] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
[   13.243395] All bytes are equal. It is not a TEA5767
[   13.243448] tuner' 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   13.271966] tuner-simple 2-0060: creating new instance
[   13.271968] tuner-simple 2-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[   13.281921] bttv0: registered device video0
[   13.281944] bttv0: registered device vbi0
[   13.281965] bttv0: PLL: 28636363 => 35468950 .. ok
[   13.343492] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   13.343497] HDA Intel 0000:00:0f.1: PCI INT B -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   13.343544] HDA Intel 0000:00:0f.1: setting latency timer to 64
[   13.732020] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   14.891373] zc3xx: probe 2wr ov vga 0x0000
[   14.963375] zc3xx: probe sensor -> 11
[   14.963377] zc3xx: Find Sensor HV7131R(c)
[   14.978481] gspca: probe ok
[   14.978494] gspca: probing 046d:08d9
[   14.978504] gspca: probing 046d:08d9
[   14.978530] usbcore: registered new interface driver zc3xx
[   14.978560] zc3xx: registered
[   15.124817] usbcore: registered new interface driver snd-usb-audio
[   15.248157] lp: driver loaded but no devices found
[   15.444424] w83627ehf: Found W83627DHG chip at 0x290
[   15.460557] coretemp coretemp.0: Using relative temperature scale!
[   15.460591] coretemp coretemp.1: Using relative temperature scale!
[   15.460625] coretemp coretemp.2: Using relative temperature scale!
[   15.460654] coretemp coretemp.3: Using relative temperature scale!
[   15.548461] Adding 9767480k swap on /dev/sda1.  Priority:-1 extents:1 across:9767480k
[   16.078213] EXT4 FS on sda2, internal journal on sda2:8
[   59.096864] kjournald starting.  Commit interval 5 seconds
[   59.097154] EXT3 FS on sdb1, internal journal
[   59.097161] EXT3-fs: mounted filesystem with ordered data mode.
[   59.138725] kjournald starting.  Commit interval 5 seconds
[   59.138993] EXT3 FS on sda6, internal journal
[   59.138998] EXT3-fs: mounted filesystem with ordered data mode.
[   59.153943] kjournald starting.  Commit interval 5 seconds
[   59.154149] EXT3 FS on sda5, internal journal
[   59.154153] EXT3-fs: mounted filesystem with ordered data mode.
[   59.381213] type=1505 audit(1262922763.195:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3168
[   59.412293] type=1505 audit(1262922763.223:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=3172
[   59.412369] type=1505 audit(1262922763.223:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=3172
[   59.412399] type=1505 audit(1262922763.223:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=3172
[   59.412429] type=1505 audit(1262922763.223:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=3172
[   59.497518] type=1505 audit(1262922763.311:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3177
[   59.497646] type=1505 audit(1262922763.311:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3177
[   59.517603] type=1505 audit(1262922763.331:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=3181
[   62.345349] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   62.345353] vboxdrv: Successfully done.
[   62.345354] vboxdrv: Found 4 processor cores.
[   62.345409] VBoxDrv: dbg - g_abExecMemory=ffffffffa0bc7b40
[   62.345469] vboxdrv: fAsync=0 offMin=0x453 offMax=0x1ca7
[   62.345681] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   62.345682] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   62.550753] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0d66980
[   63.089527] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   63.089529] Bluetooth: BNEP filters: protocol multicast
[   63.102841] Bridge firewalling registered
[   63.482871] ppdev: user-space parallel port driver
[   67.187655] forcedeth 0000:00:12.0: irq 2302 for MSI/MSI-X
[   78.020056] eth0: no IPv6 routers present
[   90.997461] warning: `VBoxHeadless' uses 32-bit capabilities (legacy support

---

### Post by s.fox on 2010-01-08
Hello,

Can you try shutting down by opening a terminal and using

```

sudo shutdown -h now

```

Do you still encounter the problem shutting down in this manner?  I know this is not a long term fix.  

I have also seen some people report hanging was resolved by removing splash by editing /boot/grub/menu.lst 

-Silver Fox

---

