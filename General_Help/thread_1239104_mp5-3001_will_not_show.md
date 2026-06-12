---
title: "mp5-3001 will not show"
date: 2009-08-13
forum: General Help
---

### Post by muhammadg on 2009-08-13
i have a mp5-3001 and the device says its mounted but ubuntu dose no show any thing 
so i typed in the terminal **dmesg **and this is what i got 

[    0.658420] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 07
[    0.660002] Brought up 1 CPUs
[    0.660002] Total of 1 processors activated (3985.46 BogoMIPS).
[    0.660002] CPU0 attaching NULL sched-domain.
[    0.660002] net_namespace: 776 bytes
[    0.660002] Booting paravirtualized kernel on bare hardware
[    0.660002] Time:  5:46:12  Date: 08/13/09
[    0.660002] regulator: core version 0.5
[    0.660002] NET: Registered protocol family 16
[    0.660002] EISA bus registered
[    0.660002] ACPI: bus type pci registered
[    0.684286] PCI: PCI BIOS revision 2.10 entry at 0xfbdf8, last bus=1
[    0.684290] PCI: Using configuration type 1 for base access
[    0.686357] ACPI: EC: Look up EC in DSDT
[    0.715651] ACPI: Interpreter enabled
[    0.715661] ACPI: (supports S0 S1 S3 S4 S5)
[    0.715693] ACPI: Using IOAPIC for interrupt routing
[    0.748669] ACPI: No dock devices found.
[    0.748686] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.748755] pci 0000:00:00.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.748840] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.748850] pci 0000:00:02.0: reg 14 32bit mmio: [0xff680000-0xff6fffff]
[    0.748973] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.749034] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.749095] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.749165] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa00800-0xffa00bff]
[    0.749217] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.749224] pci 0000:00:1d.7: PME# disabled
[    0.749280] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.749282] * this clock source is slow. If you are sure your timer does not have
[    0.749284] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.749331] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.749340] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.749346] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.749371] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.749379] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.749388] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.749396] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.749405] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.749414] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.749473] pci 0000:00:1f.3: reg 20 io port: [0xdc80-0xdc9f]
[    0.749528] pci 0000:00:1f.5: reg 10 io port: [0xd800-0xd8ff]
[    0.749536] pci 0000:00:1f.5: reg 14 io port: [0xdc40-0xdc7f]
[    0.749545] pci 0000:00:1f.5: reg 18 32bit mmio: [0xffa00400-0xffa005ff]
[    0.749554] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xffa00000-0xffa000ff]
[    0.749581] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.749587] pci 0000:00:1f.5: PME# disabled
[    0.749667] pci 0000:01:0c.0: reg 10 32bit mmio: [0xff8e0000-0xff8fffff]
[    0.749681] pci 0000:01:0c.0: reg 18 io port: [0xecc0-0xecff]
[    0.749715] pci 0000:01:0c.0: PME# supported from D0 D3hot D3cold
[    0.749721] pci 0000:01:0c.0: PME# disabled
[    0.749760] pci 0000:00:1e.0: transparent bridge
[    0.749766] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.749773] pci 0000:00:1e.0: bridge 32bit mmio: [0xff800000-0xff9fffff]
[    0.749787] bus 00 -> node 0
[    0.749797] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.750425] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.850841] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.851199] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.851554] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.852052] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.852404] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.852759] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.853113] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.853472] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.853701] ACPI: WMI: Mapper loaded
[    0.854044] SCSI subsystem initialized
[    0.854114] libata version 3.00 loaded.
[    0.854198] usbcore: registered new interface driver usbfs
[    0.854229] usbcore: registered new interface driver hub
[    0.854272] usbcore: registered new device driver usb
[    0.854462] PCI: Using ACPI for IRQ routing
[    0.854590] Bluetooth: Core ver 2.13
[    0.854590] NET: Registered protocol family 31
[    0.854590] Bluetooth: HCI device and connection manager initialized
[    0.854590] Bluetooth: HCI socket layer initialized
[    0.854590] NET: Registered protocol family 8
[    0.854590] NET: Registered protocol family 20
[    0.854590] NetLabel: Initializing
[    0.854590] NetLabel:  domain hash size = 128
[    0.854590] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.854590] NetLabel:  unlabeled traffic allowed by default
[    0.854590] AppArmor: AppArmor Filesystem Enabled
[    0.854590] pnp: PnP ACPI init
[    0.854590] ACPI: bus type pnp registered
[    0.878691] pnp 00:0b: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.878697] pnp 00:0b: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.879527] pnp: PnP ACPI: found 12 devices
[    0.879531] ACPI: ACPI bus type pnp unregistered
[    0.879538] PnPBIOS: Disabled by ACPI PNP
[    0.879554] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.879559] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.879564] system 00:00: iomem range 0x1000000-0xfe70fff could not be reserved
[    0.879569] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.879573] system 00:00: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.879577] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.879581] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.879585] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    0.879601] system 00:0b: ioport range 0xc00-0xc7f has been reserved
[    0.914480] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.914486] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.914493] pci 0000:00:1e.0:   MEM window: 0xff800000-0xff9fffff
[    0.914500] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.914518] pci 0000:00:1e.0: setting latency timer to 64
[    0.914524] bus: 00 index 0 io port: [0x00-0xffff]
[    0.914529] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.914532] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.914535] bus: 01 index 1 mmio: [0xff800000-0xff9fffff]
[    0.914538] bus: 01 index 2 mmio: [0x0-0x0]
[    0.914541] bus: 01 index 3 io port: [0x00-0xffff]
[    0.914544] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.914563] NET: Registered protocol family 2
[    0.914773] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.915110] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.915177] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.915239] TCP: Hash tables configured (established 8192 bind 8192)
[    0.915243] TCP reno registered
[    0.915390] NET: Registered protocol family 1
[    0.915595] checking if image is initramfs... it is
[    1.415797] Switched to high resolution mode on CPU 0
[    1.778477] Freeing initrd memory: 7381k freed
[    1.778566] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    1.778569] Simple Boot Flag at 0x7a set to 0x1
[    1.778619] cpufreq: No nForce2 chipset.
[    1.778905] audit: initializing netlink socket (disabled)
[    1.778947] type=2000 audit(1250142372.776:1): initialized
[    1.788674] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.790508] VFS: Disk quotas dquot_6.5.1
[    1.790595] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.791555] fuse init (API version 7.10)
[    1.791682] msgmni has been set to 485
[    1.792035] alg: No test for stdrng (krng)
[    1.792056] io scheduler noop registered
[    1.792060] io scheduler anticipatory registered
[    1.792063] io scheduler deadline registered
[    1.792098] io scheduler cfq registered (default)
[    1.792125] pci 0000:00:02.0: Boot video device
[    1.815163] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.815178] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.815360] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.815364] ACPI: Power Button (FF) [PWRF]
[    1.815430] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.815439] ACPI: Power Button (CM) [VBTN]
[    1.815720] processor ACPI_CPU:00: registered as cooling_device0
[    1.837125] isapnp: Scanning for PnP cards...
[    2.191150] isapnp: No Plug & Play device found
[    2.193227] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.193338] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.193853] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.195052] brd: module loaded
[    2.195597] loop: module loaded
[    2.195729] Fixed MDIO Bus: probed
[    2.195741] PPP generic driver version 2.4.2
[    2.195832] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.195886] Driver 'sd' needs updating - please use bus_type methods
[    2.195901] Driver 'sr' needs updating - please use bus_type methods
[    2.196050] ata_piix 0000:00:1f.1: version 2.12
[    2.196066] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    2.196088] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.196179] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.196368] scsi0 : ata_piix
[    2.196552] scsi1 : ata_piix
[    2.196608] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.196612] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.360503] ata1.00: ATA-7: Maxtor 6E040L0, NAR61590, max UDMA/133
[    2.360507] ata1.00: 80293248 sectors, multi 8: LBA 
[    2.376448] ata1.00: configured for UDMA/100
[    2.540380] ata2.00: ATAPI: _NEC DVD_RW ND-2500A, 1.06, max UDMA/33
[    2.556362] ata2.00: configured for UDMA/33
[    2.556794] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6E040L0   NAR6 PQ: 0 ANSI: 5
[    2.556961] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
[    2.556987] sd 0:0:0:0: [sda] Write Protect is off
[    2.556991] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.557033] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.557142] sd 0:0:0:0: [sda] 80293248 512-byte hardware sectors: (41.1 GB/38.2 GiB)
[    2.557165] sd 0:0:0:0: [sda] Write Protect is off
[    2.557169] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.557208] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.557214]  sda: sda1 sda2 < sda5 >
[    2.602481] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.602570] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.604120] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-2500A  1.06 PQ: 0 ANSI: 5
[    2.605394] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.605400] Uniform CD-ROM driver Revision: 3.20
[    2.605562] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.605630] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.606467] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.606511] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.606548] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.606554] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.606664] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.610600] ehci_hcd 0000:00:1d.7: debug port 1
[    2.610610] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.610633] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa00800
[    2.624013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.624120] usb usb1: configuration #1 chosen from 1 choice
[    2.624164] hub 1-0:1.0: USB hub found
[    2.624179] hub 1-0:1.0: 6 ports detected
[    2.624351] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.624379] uhci_hcd: USB Universal Host Controller Interface driver
[    2.624444] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.624457] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.624462] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.624535] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.624571] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    2.624692] usb usb2: configuration #1 chosen from 1 choice
[    2.624734] hub 2-0:1.0: USB hub found
[    2.624749] hub 2-0:1.0: 2 ports detected
[    2.624876] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.624885] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.624890] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.624962] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.624995] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    2.625106] usb usb3: configuration #1 chosen from 1 choice
[    2.625144] hub 3-0:1.0: USB hub found
[    2.625158] hub 3-0:1.0: 2 ports detected
[    2.625286] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.625295] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.625300] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.625366] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.625400] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    2.625517] usb usb4: configuration #1 chosen from 1 choice
[    2.625555] hub 4-0:1.0: USB hub found
[    2.625570] hub 4-0:1.0: 2 ports detected
[    2.625780] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.628362] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.628373] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.628560] mice: PS/2 mouse device common for all mice
[    2.628759] rtc_cmos 00:05: RTC can wake from S4
[    2.628830] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.628858] rtc0: alarms up to one day, 242 bytes nvram
[    2.628979] device-mapper: uevent: version 1.0.3
[    2.629176] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.629259] device-mapper: multipath: version 1.0.5 loaded
[    2.629263] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.629417] EISA: Probing bus 0 at eisa.0
[    2.629459] EISA: Detected 0 cards.
[    2.629505] cpuidle: using governor ladder
[    2.629509] cpuidle: using governor menu
[    2.630305] TCP cubic registered
[    2.630419] NET: Registered protocol family 10
[    2.631073] lo: Disabled Privacy Extensions
[    2.631537] NET: Registered protocol family 17
[    2.631601] Bluetooth: L2CAP ver 2.11
[    2.631604] Bluetooth: L2CAP socket layer initialized
[    2.631608] Bluetooth: SCO (Voice Link) ver 0.6
[    2.631611] Bluetooth: SCO socket layer initialized
[    2.631678] Bluetooth: RFCOMM socket layer initialized
[    2.631693] Bluetooth: RFCOMM TTY layer initialized
[    2.631696] Bluetooth: RFCOMM ver 1.10
[    2.631773] Using IPI No-Shortcut mode
[    2.631939] registered taskstats version 1
[    2.632171]   Magic number: 5:751:769
[    2.632231] mem kmsg: hash matches
[    2.632283] rtc_cmos 00:05: setting system clock to 2009-08-13 05:46:14 UTC (1250142374)
[    2.632288] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.632291] EDD information not available.
[    2.633244] Freeing unused kernel memory: 532k freed
[    2.633400] Write protecting the kernel text: 4116k
[    2.633454] Write protecting the kernel read-only data: 1524k
[    2.675388] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.256210] Floppy drive(s): fd0 is 1.44M
[    3.274167] FDC 0 is a post-1991 82077
[    3.620280] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    3.620285] Copyright (c) 1999-2006 Intel Corporation.
[    3.620360] e1000 0000:01:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.895073] e1000: 0000:01:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:08:74:37:b7:56
[    4.162596] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    5.788718] PM: Starting manual resume from disk
[    5.788724] PM: Resume from partition 8:5
[    5.788727] PM: Checking hibernation image.
[    5.789072] PM: Resume from disk failed.
[    5.812749] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.812756] EXT3-fs: write access will be enabled during recovery.
[    5.988033] kjournald starting.  Commit interval 5 seconds
[    5.988060] EXT3-fs: recovery complete.
[    5.988513] EXT3-fs: mounted filesystem with ordered data mode.
[   13.902621] udev: starting version 141
[   14.212097] Linux agpgart interface v0.103
[   14.217870] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   14.218100] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[   14.220828] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   14.349212] parport_pc 00:0a: reported by Plug and Play ACPI
[   14.349267] parport0: PC-style at 0x378 (0x77:cool:, irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   14.752208] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.779740] intel_rng: FWH not detected
[   14.986525] iTCO_vendor_support: vendor-support=0
[   14.989188] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   14.989356] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   14.989367] iTCO_wdt: No card detected
[   15.295662] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   15.423395] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   15.809033] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.809264] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.863926] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.912816] psmouse serio1: ID: 10 00 64<6>intel8x0_measure_ac97_clock: measured 54820 usecs
[   16.228051] intel8x0: clocking to 48000
[   16.722294] ppdev: user-space parallel port driver
[   16.945876] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   17.876191] lp0: using parport0 (interrupt-driven).
[   18.772427] Adding 706820k swap on /dev/sda5.  Priority:-1 extents:1 across:706820k
[   19.676018] EXT3 FS on sda1, internal journal
[ 22.948853] type=1505 audit(1250142394.815:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1836
[   23.118077] type=1505 audit(1250142394.983:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1840
[   23.118406] type=1505 audit(1250142394.983:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1840
[ 23.118510] type=1505 audit(1250142394.983:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1840
[ 23.118584] type=1505 audit(1250142394.983:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1840
[ 23.568575] type=1505 audit(1250142395.435:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1845
[   23.569014] type=1505 audit(1250142395.435::cool:: operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1845
[   23.692341] type=1505 audit(1250142395.559:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1849
[   31.102973] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   31.102979] vboxdrv: Successfully done.
[   31.102982] vboxdrv: Found 1 processor cores.
[   31.103168] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.103172] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   33.005496] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.005502] Bluetooth: BNEP filters: protocol multicast
[   33.029678] Bridge firewalling registered
[   35.246496] [drm] Initialized drm 1.1.0 20060810
[   35.258424] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   35.258435] pci 0000:00:02.0: setting latency timer to 64
[   35.258705] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   35.338053] [drm:i915_setparam] *ERROR* unknown parameter 4
[   35.338103] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   36.487717] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   38.134705] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.136405] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   38.145429] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   48.340033] eth0: no IPv6 routers present
[   65.006586] UDF-fs: No VRS found
[   65.068559] ISO 9660 Extensions: Microsoft Joliet Level 3
[   65.121596] ISOFS: changing to secondary root
[ 183.709215] update-manager[3304]: segfault at 5bae000 ip b6bb37bf sp bfafae60 error 4 in libapt-pkg-libc6.9-6.so.4.7.0[b6b7d000+bf000]
[  184.392033] usb 1-2: new high speed USB device using ehci_hcd and address 2
[  184.525196] usb 1-2: configuration #1 chosen from 1 choice
[  186.094063] Initializing USB Mass Storage driver...
[  186.096759] scsi2 : SCSI emulation for USB Mass Storage devices
[  186.097221] usbcore: registered new interface driver usb-storage
[  186.097228] USB Mass Storage support registered.
[  186.101031] usb-storage: device found at 2
[  186.101037] usb-storage: waiting for device to settle before scanning
[  191.100221] usb-storage: device scan complete
[  191.100799] scsi 2:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[  191.101156] scsi 2:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[  191.105791] sd 2:0:0:0: [sdb] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[  191.216052] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[  191.408521] sd 2:0:0:0: [sdb] Write Protect is off
[  191.408529] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  191.408534] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  191.408982] sd 2:0:0:0: [sdb] READ CAPACITY failed
[  191.408986] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  191.408992] sd 2:0:0:0: [sdb] Sense not available.
[  191.409059] sd 2:0:0:0: [sdb] Write Protect is off
[  191.409063] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  191.409066] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  191.409376] sd 2:0:0:0: [sdb] READ CAPACITY failed
[  191.409379] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  191.409384] sd 2:0:0:0: [sdb] Sense not available.
[  191.409449] sd 2:0:0:0: [sdb] Write Protect is off
[  191.409453] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  191.409456] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  191.411718] usb 1-2: USB disconnect, address 2
[  191.416146] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  191.416264] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  191.416500] sd 2:0:0:1: [sdc] READ CAPACITY failed
[  191.416504] sd 2:0:0:1: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  191.416510] sd 2:0:0:1: [sdc] Sense not available.
[  191.416533] sd 2:0:0:1: [sdc] Write Protect is off
[  191.416536] sd 2:0:0:1: [sdc] Mode Sense: 00 00 00 00
[  191.416540] sd 2:0:0:1: [sdc] Assuming drive cache: write through
[  191.416665] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[  191.416750] sd 2:0:0:1: Attached scsi generic sg3 type 0
[  303.056044] usb 1-2: new high speed USB device using ehci_hcd and address 3
[  303.189192] usb 1-2: configuration #1 chosen from 1 choice
[  303.189404] scsi3 : SCSI emulation for USB Mass Storage devices
[  303.189740] usb-storage: device found at 3
[  303.189744] usb-storage: waiting for device to settle before scanning
[  308.188319] usb-storage: device scan complete
[  308.188777] scsi 3:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[  308.189140] scsi 3:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[  308.193648] sd 3:0:0:0: [sdb] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[  308.248656] sd 3:0:0:0: [sdb] Write Protect is off
[  308.248664] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  308.248669] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  308.249113] sd 3:0:0:0: [sdb] READ CAPACITY failed
[  308.249117] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  308.249123] sd 3:0:0:0: [sdb] Sense not available.
[  308.249189] sd 3:0:0:0: [sdb] Write Protect is off
[  308.249193] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  308.249196] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  308.249507] sd 3:0:0:0: [sdb] READ CAPACITY failed
[  308.249510] sd 3:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  308.249515] sd 3:0:0:0: [sdb] Sense not available.
[  308.249580] sd 3:0:0:0: [sdb] Write Protect is off
[  308.249584] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  308.249587] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  308.249772] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  308.249897] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  308.250232] sd 3:0:0:1: [sdc] READ CAPACITY failed
[  308.250236] sd 3:0:0:1: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  308.250241] sd 3:0:0:1: [sdc] Sense not available.
[  308.250297] sd 3:0:0:1: [sdc] Write Protect is off
[  308.250301] sd 3:0:0:1: [sdc] Mode Sense: 00 00 00 00
[  308.250305] sd 3:0:0:1: [sdc] Assuming drive cache: write through
[  308.250408] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[  308.250484] sd 3:0:0:1: Attached scsi generic sg3 type 0
[  308.250560] usb 1-2: USB disconnect, address 3
[ 9493.323357] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 9497.411393] [drm:i915_getparam] *ERROR* Unknown parameter 6
[10097.115608] [drm:i915_getparam] *ERROR* Unknown parameter 6
[10697.123048] [drm:i915_getparam] *ERROR* Unknown parameter 6
[11049.752056] usb 1-2: new high speed USB device using ehci_hcd and address 4
[11049.885267] usb 1-2: configuration #1 chosen from 1 choice
[11049.887220] scsi4 : SCSI emulation for USB Mass Storage devices
[11049.887638] usb-storage: device found at 4
[11049.887642] usb-storage: waiting for device to settle before scanning
[11054.884509] usb-storage: device scan complete
[11054.885092] scsi 4:0:0:0: Direct-Access     RockChip USBDISK  User    1.00 PQ: 0 ANSI: 0
[11054.885653] scsi 4:0:0:1: Direct-Access     RockChip USBDISK    SD    1.00 PQ: 0 ANSI: 0
[11054.892457] sd 4:0:0:0: [sdb] 15953920 512-byte hardware sectors: (8.16 GB/7.60 GiB)
[11054.992197] sd 4:0:0:0: [sdb] Write Protect is off
[11054.992205] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[11054.992209] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[11054.992670] sd 4:0:0:0: [sdb] READ CAPACITY failed
[11054.992673] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[11054.992680] sd 4:0:0:0: [sdb] Sense not available.
[11054.992749] sd 4:0:0:0: [sdb] Write Protect is off
[11054.992752] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[11054.992756] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[11054.993080] sd 4:0:0:0: [sdb] READ CAPACITY failed
[11054.993084] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[11054.993089] sd 4:0:0:0: [sdb] Sense not available.
[11054.993157] sd 4:0:0:0: [sdb] Write Protect is off
[11054.993161] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[11054.993164] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[11054.993352] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[11054.993477] sd 4:0:0:0: Attached scsi generic sg2 type 0
[11054.993818] sd 4:0:0:1: [sdc] READ CAPACITY failed
[11054.993822] sd 4:0:0:1: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[11054.993828] sd 4:0:0:1: [sdc] Sense not available.
[11054.993884] sd 4:0:0:1: [sdc] Write Protect is off
[11054.993887] sd 4:0:0:1: [sdc] Mode Sense: 00 00 00 00
[11054.993891] sd 4:0:0:1: [sdc] Assuming drive cache: write through
[11054.993995] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[11054.994075] sd 4:0:0:1: Attached scsi generic sg3 type 0
[11054.994161] usb 1-2: USB disconnect, address 4

---

### Post by P4man on 2009-08-13
think it just mounts it like a external drive?
can you post output of:
```
lsusb
```

and
```

sudo fdisk -l
```

---

### Post by muhammadg on 2009-08-13
_lsusb _

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
_sudo fdisk -l_

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b2e9b2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4910    39439543+  83  Linux
/dev/sda2            4911        4998      706860    5  Extended
/dev/sda5            4911        4998      706828+  82  Linux swap / Solaris

---

### Post by P4man on 2009-08-13
was that player plugged in while you ran those commands?
If so, its not recognized in any way.. not sure if there is much you can do.

---

### Post by muhammadg on 2009-08-13
yes it was  but read the dmesg it wont read but it can scan

---

### Post by P4man on 2009-08-13
Im not sure, but those messages you see in dmesg may well relate to the SD card socket, which I suspect is empty. You could try inserting an SD card, and its possible ubuntu will pick that up, but it doesn't look like you'll be able to access the internal drive of the device.

---

### Post by muhammadg on 2009-08-13
i tought needed a TF SD card

---

