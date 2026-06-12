---
title: "Maverick did crash at startup AGAIN"
date: 2011-02-10
forum: General Help
---

### Post by runeh76 on 2011-02-10
Hi guys :)

My computer have freezed three times. Last time was around 2 week ago. Just started computer and when it came to desktop, it freeze. CapsLock&ScrollLock was blinking and keyboard&mouse didnt answer.

Here is last **dmesg** (tell me what log u need to look?)

```
[    0.176080] vgaarb: loaded
[    0.176196] SCSI subsystem initialized
[    0.176258] libata version 3.00 loaded.
[    0.176298] usbcore: registered new interface driver usbfs
[    0.176308] usbcore: registered new interface driver hub
[    0.176326] usbcore: registered new device driver usb
[    0.176426] ACPI: WMI: Mapper loaded
[    0.176428] PCI: Using ACPI for IRQ routing
[    0.176431] PCI: pci_cache_line_size set to 64 bytes
[    0.176474] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.176476] reserve RAM buffer: 00000000cffc0000 - 00000000cfffffff 
[    0.176547] NetLabel: Initializing
[    0.176548] NetLabel:  domain hash size = 128
[    0.176549] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.176559] NetLabel:  unlabeled traffic allowed by default
[    0.183440] AppArmor: AppArmor Filesystem Enabled
[    0.183455] pnp: PnP ACPI init
[    0.183470] ACPI: bus type pnp registered
[    0.186961] pnp: PnP ACPI: found 13 devices
[    0.186963] ACPI: ACPI bus type pnp unregistered
[    0.186965] PnPBIOS: Disabled by ACPI PNP
[    0.186976] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.186978] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.186980] system 00:06: [io  0x2000-0x207f] has been reserved
[    0.186982] system 00:06: [io  0x2080-0x20ff] has been reserved
[    0.186984] system 00:06: [io  0x2400-0x247f] has been reserved
[    0.186986] system 00:06: [io  0x2480-0x24ff] has been reserved
[    0.186988] system 00:06: [io  0x2800-0x287f] has been reserved
[    0.186990] system 00:06: [io  0x2880-0x28ff] has been reserved
[    0.186992] system 00:06: [io  0x2c00-0x2c7f] has been reserved
[    0.186994] system 00:06: [io  0x2c80-0x2cff] has been reserved
[    0.186997] system 00:06: [mem 0x000d0000-0x000d3fff window] has been reserved
[    0.186999] system 00:06: [mem 0x000d4000-0x000d7fff window] has been reserved
[    0.187001] system 00:06: [mem 0x000de000-0x000dffff window] has been reserved
[    0.187003] system 00:06: [mem 0xfec80000-0xfd93ffff] could not be reserved
[    0.187006] system 00:06: [mem 0xfee01000-0xfeefffff] has been reserved
[    0.187010] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.187012] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.187016] system 00:0a: [io  0x0a00-0x0a0f] has been reserved
[    0.187018] system 00:0a: [io  0x0a10-0x0a1f] has been reserved
[    0.187021] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.187025] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.187027] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.187029] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.187031] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
[    0.187034] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.222716] Switching to clocksource acpi_pm
[    0.222869] pci 0000:00:08.0: PCI bridge to [bus 01-01]
[    0.222871] pci 0000:00:08.0:   bridge window [io  disabled]
[    0.222874] pci 0000:00:08.0:   bridge window [mem disabled]
[    0.222876] pci 0000:00:08.0:   bridge window [mem pref disabled]
[    0.222879] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    0.222881] pci 0000:00:0b.0:   bridge window [io  disabled]
[    0.222883] pci 0000:00:0b.0:   bridge window [mem disabled]
[    0.222885] pci 0000:00:0b.0:   bridge window [mem pref disabled]
[    0.222887] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[    0.222889] pci 0000:00:0c.0:   bridge window [io  0xd000-0xdfff]
[    0.222892] pci 0000:00:0c.0:   bridge window [mem 0xf9f00000-0xf9ffffff]
[    0.222894] pci 0000:00:0c.0:   bridge window [mem pref disabled]
[    0.222897] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[    0.222899] pci 0000:00:0d.0:   bridge window [io  0xe000-0xefff]
[    0.222901] pci 0000:00:0d.0:   bridge window [mem 0xfa000000-0xfebfffff]
[    0.222904] pci 0000:00:0d.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.222906] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[    0.222908] pci 0000:00:0e.0:   bridge window [io  disabled]
[    0.222910] pci 0000:00:0e.0:   bridge window [mem disabled]
[    0.222912] pci 0000:00:0e.0:   bridge window [mem pref disabled]
[    0.222919] pci 0000:00:08.0: setting latency timer to 64
[    0.222923] pci 0000:00:0b.0: setting latency timer to 64
[    0.222927] pci 0000:00:0c.0: setting latency timer to 64
[    0.222931] pci 0000:00:0d.0: setting latency timer to 64
[    0.222934] pci 0000:00:0e.0: setting latency timer to 64
[    0.222937] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.222939] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.222941] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.222943] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.222944] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.222946] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.222948] pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
[    0.222950] pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
[    0.222952] pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
[    0.222954] pci_bus 0000:01: resource 7 [mem 0x000d0000-0x000dffff]
[    0.222956] pci_bus 0000:01: resource 8 [mem 0xd0000000-0xdfffffff]
[    0.222957] pci_bus 0000:01: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.222959] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.222961] pci_bus 0000:03: resource 1 [mem 0xf9f00000-0xf9ffffff]
[    0.222963] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.222965] pci_bus 0000:04: resource 1 [mem 0xfa000000-0xfebfffff]
[    0.222967] pci_bus 0000:04: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.222996] NET: Registered protocol family 2
[    0.223042] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.223250] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.223759] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.223990] TCP: Hash tables configured (established 131072 bind 65536)
[    0.223990] TCP reno registered
[    0.223990] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.223990] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.223990] NET: Registered protocol family 1
[    0.242868] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.242910] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.242960] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.243011] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.243064] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.243121] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.243181] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.243196] pci 0000:04:00.0: Boot video device
[    0.243198] PCI: CLS 64 bytes, default 64
[    0.243360] cpufreq-nforce2: No nForce2 chipset.
[    0.243382] Scanning for low memory corruption every 60 seconds
[    0.243465] audit: initializing netlink socket (disabled)
[    0.243473] type=2000 audit(1297342167.239:1): initialized
[    0.250940] highmem bounce pool size: 64 pages
[    0.250943] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.251983] VFS: Disk quotas dquot_6.5.2
[    0.252027] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.252443] fuse init (API version 7.14)
[    0.252506] msgmni has been set to 1650
[    0.367430] Freeing initrd memory: 10512k freed
[    0.374092] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.374095] io scheduler noop registered
[    0.374097] io scheduler deadline registered
[    0.374107] io scheduler cfq registered (default)
[    0.374185] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.374200]   alloc irq_desc for 40 on node -1
[    0.374201]   alloc kstat_irqs on node -1
[    0.374208] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[    0.374246] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.374259]   alloc irq_desc for 41 on node -1
[    0.374260]   alloc kstat_irqs on node -1
[    0.374264] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[    0.374299] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.374311]   alloc irq_desc for 42 on node -1
[    0.374312]   alloc kstat_irqs on node -1
[    0.374315] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[    0.374347] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.374358]   alloc irq_desc for 43 on node -1
[    0.374360]   alloc kstat_irqs on node -1
[    0.374363] pcieport 0000:00:0e.0: irq 43 for MSI/MSI-X
[    0.374413] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.374432] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.374573] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.374583] ACPI: Power Button [PWRB]
[    0.374623] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.374625] ACPI: Power Button [PWRF]
[    0.374760] ACPI: acpi_idle registered with cpuidle
[    0.377234] ERST: Table is not found!
[    0.377260] isapnp: Scanning for PnP cards...
[    0.377354] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.377440] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.377648] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.378480] brd: module loaded
[    0.378856] loop: module loaded
[    0.379045] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.379324] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.379328]   alloc irq_desc for 23 on node -1
[    0.379330]   alloc kstat_irqs on node -1
[    0.379339] pata_acpi 0000:00:0a.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.379350] pata_acpi 0000:00:0a.0: setting latency timer to 64
[    0.379355] pata_acpi 0000:00:0a.0: PCI INT A disabled
[    0.379603] Fixed MDIO Bus: probed
[    0.379629] PPP generic driver version 2.4.2
[    0.379664] tun: Universal TUN/TAP device driver, 1.6
[    0.379666] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.379720] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.379977] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.379979]   alloc irq_desc for 22 on node -1
[    0.379981]   alloc kstat_irqs on node -1
[    0.379987] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    0.380031] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.380033] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.380059] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.380079] ehci_hcd 0000:00:02.1: debug port 1
[    0.380085] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.380103] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf9efec00
[    0.392017] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.392099] hub 1-0:1.0: USB hub found
[    0.392103] hub 1-0:1.0: 10 ports detected
[    0.392160] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.392420] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    0.392423]   alloc irq_desc for 21 on node -1
[    0.392424]   alloc kstat_irqs on node -1
[    0.392430] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    0.392437] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.392439] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.392465] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.392485] ohci_hcd 0000:00:02.0: irq 21, io mem 0xf9eff000
[    0.450063] hub 2-0:1.0: USB hub found
[    0.450067] hub 2-0:1.0: 10 ports detected
[    0.450119] uhci_hcd: USB Universal Host Controller Interface driver
[    0.450183] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.450185] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.450674] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.450721] mice: PS/2 mouse device common for all mice
[    0.450808] rtc_cmos 00:07: RTC can wake from S4
[    0.450838] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.450870] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    0.450946] device-mapper: uevent: version 1.0.3
[    0.451033] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.451090] device-mapper: multipath: version 1.1.1 loaded
[    0.451092] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.451177] EISA: Probing bus 0 at eisa.0
[    0.451179] EISA: Cannot allocate resource for mainboard
[    0.451181] Cannot allocate resource for EISA slot 1
[    0.451183] Cannot allocate resource for EISA slot 2
[    0.451184] Cannot allocate resource for EISA slot 3
[    0.451186] Cannot allocate resource for EISA slot 4
[    0.451188] Cannot allocate resource for EISA slot 5
[    0.451189] Cannot allocate resource for EISA slot 6
[    0.451191] Cannot allocate resource for EISA slot 7
[    0.451192] Cannot allocate resource for EISA slot 8
[    0.451194] EISA: Detected 0 cards.
[    0.451252] cpuidle: using governor ladder
[    0.451253] cpuidle: using governor menu
[    0.451464] TCP cubic registered
[    0.451559] NET: Registered protocol family 10
[    0.451831] lo: Disabled Privacy Extensions
[    0.452033] NET: Registered protocol family 17
[    0.452058] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (2 cpu cores) (version 2.20.00)
[    0.452100] powernow-k8:    0 : fid 0x17 (3100 MHz), vid 0x5
[    0.452102] powernow-k8:    1 : fid 0x16 (3000 MHz), vid 0x6
[    0.452104] powernow-k8:    2 : fid 0x14 (2800 MHz), vid 0x8
[    0.452106] powernow-k8:    3 : fid 0x12 (2600 MHz), vid 0xa
[    0.452107] powernow-k8:    4 : fid 0x10 (2400 MHz), vid 0xc
[    0.452109] powernow-k8:    5 : fid 0xe (2200 MHz), vid 0xe
[    0.452111] powernow-k8:    6 : fid 0xc (2000 MHz), vid 0x10
[    0.452112] powernow-k8:    7 : fid 0xa (1800 MHz), vid 0x10
[    0.452114] powernow-k8:    8 : fid 0x2 (1000 MHz), vid 0x12
[    0.452143] Using IPI No-Shortcut mode
[    0.452205] PM: Resume from disk failed.
[    0.452218] registered taskstats version 1
[    0.452382]   Magic number: 15:783:834
[    0.452463] rtc_cmos 00:07: setting system clock to 2011-02-10 12:49:27 UTC (1297342167)
[    0.452465] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.452467] EDD information not available.
[    0.476487] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.730097] isapnp: No Plug & Play device found
[    0.730123] Freeing unused kernel memory: 688k freed
[    0.730487] Write protecting the kernel text: 4936k
[    0.730515] Write protecting the kernel read-only data: 1976k
[    0.744198] udev[74]: starting version 163
[    0.805786] pata_amd 0000:00:09.0: version 0.4.1
[    0.805825] pata_amd 0000:00:09.0: setting latency timer to 64
[    0.808053] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    0.823657] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.823965] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 19
[    0.823970]   alloc irq_desc for 19 on node -1
[    0.823972]   alloc kstat_irqs on node -1
[    0.823981] r8169 0000:03:00.0: PCI INT A -> Link[LNEA] -> GSI 19 (level, low) -> IRQ 19
[    0.824116] scsi0 : pata_amd
[    0.827181] r8169 0000:03:00.0: setting latency timer to 64
[    0.827222]   alloc irq_desc for 44 on node -1
[    0.827224]   alloc kstat_irqs on node -1
[    0.827235] r8169 0000:03:00.0: irq 44 for MSI/MSI-X
[    0.827611] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xf8098000, 00:21:85:31:54:da, XID 18000000 IRQ 44
[    0.834509] scsi1 : pata_amd
[    0.835384] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.835386] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.839854] ahci 0000:00:0a.0: version 3.0
[    0.839868] ahci 0000:00:0a.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.839898]   alloc irq_desc for 45 on node -1
[    0.839900]   alloc kstat_irqs on node -1
[    0.839907] ahci 0000:00:0a.0: irq 45 for MSI/MSI-X
[    0.839912] ahci 0000:00:0a.0: controller can't do PMP, turning off CAP_PMP
[    0.839956] ahci 0000:00:0a.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    0.839959] ahci 0000:00:0a.0: flags: 64bit ncq sntf pm led clo pio ccc 
[    0.839962] ahci 0000:00:0a.0: setting latency timer to 64
[    0.842615] scsi2 : ahci
[    0.842699] scsi3 : ahci
[    0.842750] scsi4 : ahci
[    0.842893] scsi5 : ahci
[    0.843018] ata3: SATA max UDMA/133 abar m8192@0xf9efc000 port 0xf9efc100 irq 45
[    0.843020] ata4: SATA max UDMA/133 abar m8192@0xf9efc000 port 0xf9efc180 irq 45
[    0.843023] ata5: SATA max UDMA/133 abar m8192@0xf9efc000 port 0xf9efc200 irq 45
[    0.843025] ata6: SATA max UDMA/133 abar m8192@0xf9efc000 port 0xf9efc280 irq 45
[    0.996463] ata1.00: ATA-7: SAMSUNG SP0802N, TK100-24, max UDMA/100
[    0.996466] ata1.00: 156368016 sectors, multi 16: LBA48 
[    0.996485] ata1: nv_mode_filter: 0x3f39f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:900:0x11)
[    1.004328] ata1.00: configured for UDMA/33
[    1.004463] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0802N  TK10 PQ: 0 ANSI: 5
[    1.004607] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.004663] sd 0:0:0:0: [sda] 156368016 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.004667] ata2: port disabled. ignoring.
[    1.004697] sd 0:0:0:0: [sda] Write Protect is off
[    1.004700] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.004714] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.004857]  sda: sda1 sda2
[    1.014434] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.052044] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    1.160033] ata6: SATA link down (SStatus 0 SControl 300)
[    1.160036] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.160048] ata5: SATA link down (SStatus 0 SControl 300)
[    1.160051] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.160530] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB00, max UDMA/100
[    1.160750] ata4.00: ATA-8: WDC WD5000AACS-00G8B1, 05.04C05, max UDMA/133
[    1.160752] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.161271] ata3.00: configured for UDMA/100
[    1.162045] ata4.00: configured for UDMA/133
[    1.176559] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB00 PQ: 0 ANSI: 5
[    1.181012] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.181015] Uniform CD-ROM driver Revision: 3.20
[    1.181095] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.181149] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.181263] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 05.0 PQ: 0 ANSI: 5
[    1.181386] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.181390] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.181472] sd 3:0:0:0: [sdb] Write Protect is off
[    1.181475] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.181489] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.181591]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
[    1.219105] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.356022] usb 1-6: new high speed USB device using ehci_hcd and address 6
[    1.495394] Initializing USB Mass Storage driver...
[    1.495558] scsi6 : usb-storage 1-6:1.3
[    1.495653] usbcore: registered new interface driver usb-storage
[    1.495656] USB Mass Storage support registered.
[    1.645610] EXT3-fs (sdb2): recovery required on readonly filesystem
[    1.645613] EXT3-fs (sdb2): write access will be enabled during recovery
[    1.676595] EXT3-fs: barriers not enabled
[    1.747878] kjournald starting.  Commit interval 5 seconds
[    1.747914] EXT3-fs (sdb2): recovery complete
[    1.748226] EXT3-fs (sdb2): mounted filesystem with ordered data mode
[    1.793039] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    2.316027] usb 2-5: new low speed USB device using ohci_hcd and address 3
[    2.495426] scsi 6:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
[    2.495916] scsi 6:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
[    2.496340] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    2.498288] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    2.499784] sr1: scsi-1 drive
[    2.499841] sr 6:0:0:1: Attached scsi CD-ROM sr1
[    2.499874] sr 6:0:0:1: Attached scsi generic sg4 type 5
[   17.079838] udev[401]: starting version 163
[   17.152704] i2c i2c-0: nForce2 SMBus adapter at 0x2d00
[   17.152738] i2c i2c-1: nForce2 SMBus adapter at 0x2e00
[   17.188537] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   17.220811] Linux agpgart interface v0.103
[   17.229624] WARNING! power/level is deprecated; use power/control instead
[   17.234882] parport_pc 00:05: reported by Plug and Play ACPI
[   17.234928] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   17.257971] Adding 975868k swap on /dev/sdb5.  Priority:-1 extents:1 across:975868k 
[   17.259039] usbcore: registered new interface driver usbserial
[   17.259052] USB Serial support registered for generic
[   17.259098] usbcore: registered new interface driver usbserial_generic
[   17.259099] usbserial: USB Serial Driver core
[   17.286671] lp: driver loaded but no devices found
[   17.329599] USB Serial support registered for GSM modem (1-port)
[   17.329644] option 1-6:1.0: GSM modem (1-port) converter detected
[   17.329743] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[   17.329760] option 1-6:1.1: GSM modem (1-port) converter detected
[   17.329799] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[   17.329816] option 1-6:1.2: GSM modem (1-port) converter detected
[   17.329866] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
[   17.329890] usbcore: registered new interface driver option
[   17.329891] option: v0.7.2:USB Driver for GSM modems
[   17.341454] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1734
[   17.341685] usbcore: registered new interface driver usblp
[   17.371783] lp0: using parport0 (interrupt-driven).
[   17.371826] usbcore: registered new interface driver hiddev
[   17.371934] ppdev: user-space parallel port driver
[   17.378673] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
[   17.378762] generic-usb 0003:046D:C069.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:02.0-1/input0
[   17.378819] usbcore: registered new interface driver usbhid
[   17.378821] usbhid: USB HID core driver
[   17.417874] nvidia: module license 'NVIDIA' taints kernel.
[   17.417877] Disabling lock debugging due to kernel taint
[   17.445148] type=1400 audit(1297334984.490:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=727 comm="apparmor_parser"
[   17.445352] type=1400 audit(1297334984.490:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=727 comm="apparmor_parser"
[   17.445470] type=1400 audit(1297334984.490:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=727 comm="apparmor_parser"
[   17.446714] type=1400 audit(1297334984.490:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=739 comm="apparmor_parser"
[   17.446920] type=1400 audit(1297334984.490:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=739 comm="apparmor_parser"
[   17.447039] type=1400 audit(1297334984.490:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=739 comm="apparmor_parser"
[   17.496844] dib0700: loaded with support for 14 different device-types
[   17.499159] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.499517] input: Logitech Logitech Extreme 3D as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input4
[   17.499599] logitech 0003:046D:C215.0002: input,hidraw1: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D] on usb-0000:00:02.0-5/input0
[   17.499686] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   17.499716] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   17.501125] DVB: registering new adapter (Hauppauge Nova-T Stick)
[   17.558202] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   17.558208]   alloc irq_desc for 20 on node -1
[   17.558210]   alloc kstat_irqs on node -1
[   17.558219] HDA Intel 0000:00:07.0: PCI INT B -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   17.558222] hda_intel: Disable MSI for Nvidia chipset
[   17.558261] HDA Intel 0000:00:07.0: setting latency timer to 64
[   17.582044] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   17.583348] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   17.583351] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   17.583353] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   17.611451] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   17.729355] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   17.948598] DiB0070: successfully identified
[   17.948672] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:02.1/usb1/1-4/input/input5
[   17.948718] dvb-usb: schedule remote query interval to 50 msecs.
[   17.948721] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   17.949395] usbcore: registered new interface driver dvb_usb_dib0700
[   18.189017] hda_codec: ALC888: BIOS auto-probing.
[   18.505897] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 18
[   18.505902]   alloc irq_desc for 18 on node -1
[   18.505904]   alloc kstat_irqs on node -1
[   18.505914] nvidia 0000:04:00.0: PCI INT A -> Link[LNED] -> GSI 18 (level, low) -> IRQ 18
[   18.505921] nvidia 0000:04:00.0: setting latency timer to 64
[   18.505926] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   18.506110] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.18  Tue Jan 18 21:44:45 PST 2011
[   18.584710] EXT3-fs (sdb2): using internal journal
[  549.633357] type=1400 audit(1297335516.678:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1158 comm="apparmor_parser"
[  549.633629] type=1400 audit(1297335516.678:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1158 comm="apparmor_parser"
[  550.141698] type=1400 audit(1297335517.186:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1197 comm="apparmor_parser"
[  550.141879] type=1400 audit(1297335517.186:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1198 comm="apparmor_parser"
[  550.142089] type=1400 audit(1297335517.186:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1198 comm="apparmor_parser"
[  550.142209] type=1400 audit(1297335517.186:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1198 comm="apparmor_parser"
[  550.145166] type=1400 audit(1297335517.190:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1201 comm="apparmor_parser"
[  550.147705] type=1400 audit(1297335517.190:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1202 comm="apparmor_parser"
[  550.147991] type=1400 audit(1297335517.190:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1202 comm="apparmor_parser"
[  550.148896] type=1400 audit(1297335517.190:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1199 comm="apparmor_parser"
[  550.686896] r8169 0000:03:00.0: eth0: link down
[  550.687057] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  551.622501] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  551.622505] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[  551.622506] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[  551.622507] vboxdrv: the usage of hardware performance counters by
[  551.622508] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[  551.622510] vboxdrv: Found 2 processor cores.
[  551.623501] vboxdrv: fAsync=1 offMin=0xc5562a offMax=0xc5562a
[  551.623929] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[  551.623931] vboxdrv: Successfully loaded version 3.2.8_OSE (interface 0x00140001).
[  552.223611] usb 1-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[  561.783900] ISO 9660 Extensions: Microsoft Joliet Level 1
[  561.851783] ISOFS: changing to secondary root

```

It would be great to get this solved! Whats going on?
Thank you :)

---

### Post by P4man on 2011-02-10
Try ruling out a hardware issue first. In the grub menu, select memtest86 and let it run overnight. It should produce zero errors. If it throws errors, you probably have a memory module that is failing.

Also check your harddisk. In system > administration > disk utility, select your drive and check the SMART status.

Also, have a look in your bios, if you have a "PC Health" page, check if temperatures are okay and if the positive voltages are within ~5% of their nominal values (eg, +12v  is not measures as +10.5v). If voltages are further off and/or fluctuate, you may need a new powersupply.

Lastly, ensure your fans are clean and all spinning.

---

### Post by runeh76 on 2011-02-10
Thx for the quick reply  :)


I did check BIOS and here's result:

CPU Vcore 1.440v
3.3v      3.264v
5v        5.003v
12v       11.880v
5v SB     5.045v
(Power supply 500W)

Temperatures:
Graphic card  52C
CPU           40C
System        30C

Fans OK (I have 2 extra-fans for the ventilation) and i also clean box inside, once per month.
MemTest OK (0errors)
After freeze i had to shutdown computer from front-panel power-button. Next boot ended to disk-check and founded problems from _/Home_ and fixed them.

Also **fsck** runs quite often, dont know does this matter..

---

### Post by P4man on 2011-02-10
That all looks perfectly healthy, and how about the harddisk? Especially you say it does fsck a lot.. it basically never does on mine (or if it does, its so fast I dont see it).

---

### Post by runeh76 on 2011-02-10
Dah! sry man..i knew that i didnt remember all!

Hard-disk Smart-status is Green  OK.

---

### Post by P4man on 2011-02-10
Well, in a way thats unfortunate, because troubleshooting intermittent and non repeatable kernel panics can be bloody hard. So much easier to replace a defective piece of hardware. 

Do you have any other useful datapoints? Do you dualboot windows, ever have issues there? When did this start happening? Any pattern you can make out ?

---

### Post by runeh76 on 2011-02-10
I have Dual-boot with Win XP. Never had problems there, when im playing "heavy"-games.
I havent log in windows long time.

Problem started around month ago..cant realize why though.
I think this problem is readable in logs, but i dont know which one?

---

### Post by P4man on 2011-02-10
dmesg is the kernel log. You can view older one;s by opening system > administration > log file viewer.

NExt time you have a kernel panic/freeze, look at your watch, note the exact time. Then after rebooting you can go through all the timestamped logs and see if you can find something that happened just before, but I dont think kernel panics are actually logged.

Did you do an update or upgrade before this happened? Have you tried booting older kernels? Have you tried updating your bios?

---

### Post by runeh76 on 2011-02-10
No i didnt do nothing else, than just started my computer and it came to the desktop and freeze.

Havent upgraded BIOS, havent tried older kernels.

---

### Post by runeh76 on 2011-02-10
Well here is exactly that time kernel log:


```
Feb 10 10:08:14 Masiina kernel: Kernel logging (proc) stopped.
Feb 10 12:08:44 Masiina kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb 10 12:08:44 Masiina rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1130" x-info="http://www.rsyslog.com"] (re)start
Feb 10 12:08:44 Masiina rsyslogd: rsyslogd's groupid changed to 103
Feb 10 12:08:44 Masiina rsyslogd: rsyslogd's userid changed to 101
Feb 10 12:08:44 Masiina kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 10 12:08:44 Masiina kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 10 12:08:44 Masiina kernel: [    0.000000] Linux version 2.6.35-26-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #46-Ubuntu SMP Sun Jan 30 08:10:51 UTC 2011 (Ubuntu 2.6.35-26.46-generic 2.6.35.10)
Feb 10 12:08:44 Masiina kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffc0000 (usable)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 00000000cffc0000 - 00000000cffce000 (ACPI data)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 00000000cffce000 - 00000000cfff0000 (ACPI NVS)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfffe000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Feb 10 12:08:44 Masiina kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Feb 10 12:08:44 Masiina kernel: [    0.000000] DMI present.
Feb 10 12:08:44 Masiina kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Feb 10 12:08:44 Masiina kernel: [    0.000000] last_pfn = 0xcffc0 max_arch_pfn = 0x100000
Feb 10 12:08:44 Masiina kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 10 12:08:44 Masiina kernel: [    0.000000] Scanning 0 areas for low memory corruption
Feb 10 12:08:44 Masiina kernel: [    0.000000] modified physical RAM map:
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 0000000000100000 - 00000000cffc0000 (usable)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 00000000cffc0000 - 00000000cffce000 (ACPI data)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 00000000cffce000 - 00000000cfff0000 (ACPI NVS)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 00000000cfff0000 - 00000000cfffe000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Feb 10 12:08:44 Masiina kernel: [    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
Feb 10 12:08:44 Masiina kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Feb 10 12:08:44 Masiina kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Feb 10 12:08:44 Masiina kernel: [    0.000000] RAMDISK: 375ac000 - 37ff0000
Feb 10 12:08:44 Masiina kernel: [    0.000000] Allocated new RAMDISK: 009a7000 - 013ea9e2
Feb 10 12:08:44 Masiina kernel: [    0.000000] Move RAMDISK from 00000000375ac000 - 0000000037fef9e1 to 009a7000 - 013ea9e1
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: RSDP 000f9810 00014 (v00 ACPIAM)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: RSDT cffc0000 00038 (v01 031108 RSDT1839 20080311 MSFT 00000097)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: FACP cffc0200 00084 (v01 031108 FACP1839 20080311 MSFT 00000097)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: DSDT cffc0440 04B9F (v01  1ADKU 1ADKU004 00000004 INTL 20051117)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: FACS cffce000 00040
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: APIC cffc0390 00070 (v01 031108 APIC1839 20080311 MSFT 00000097)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: MCFG cffc0400 0003C (v01 031108 OEMMCFG  20080311 MSFT 00000097)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: OEMB cffce040 00071 (v01 031108 OEMB1839 20080311 MSFT 00000097)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: SSDT cffc4fe0 00350 (v01 A M I  POWERNOW 00000001 AMD  00000001)
Feb 10 12:08:44 Masiina kernel: [    0.000000] 2439MB HIGHMEM available.
Feb 10 12:08:44 Masiina kernel: [    0.000000] 887MB LOWMEM available.
Feb 10 12:08:44 Masiina kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Feb 10 12:08:44 Masiina kernel: [    0.000000]   low ram: 0 - 377fe000
Feb 10 12:08:44 Masiina kernel: [    0.000000] Zone PFN ranges:
Feb 10 12:08:44 Masiina kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Feb 10 12:08:44 Masiina kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Feb 10 12:08:44 Masiina kernel: [    0.000000]   HighMem  0x000377fe -> 0x000cffc0
Feb 10 12:08:44 Masiina kernel: [    0.000000] Movable zone start PFN for each node
Feb 10 12:08:44 Masiina kernel: [    0.000000] early_node_map[2] active PFN ranges
Feb 10 12:08:44 Masiina kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Feb 10 12:08:44 Masiina kernel: [    0.000000]     0: 0x00000100 -> 0x000cffc0
Feb 10 12:08:44 Masiina kernel: [    0.000000] Using APIC driver default
Feb 10 12:08:44 Masiina kernel: [    0.000000] Nvidia board detected. Ignoring ACPI timer override.
Feb 10 12:08:44 Masiina kernel: [    0.000000] If you got timer trouble try acpi_use_timer_override
Feb 10 12:08:44 Masiina kernel: [    0.000000] Detected use of extended apic ids on hypertransport bus
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x2008
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Feb 10 12:08:44 Masiina kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Feb 10 12:08:44 Masiina kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Feb 10 12:08:44 Masiina kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 10 12:08:44 Masiina kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Feb 10 12:08:44 Masiina kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Feb 10 12:08:44 Masiina kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Feb 10 12:08:44 Masiina kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Feb 10 12:08:44 Masiina kernel: [    0.000000] Allocating PCI resources starting at cfffe000 (gap: cfffe000:2ec02000)
Feb 10 12:08:44 Masiina kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 10 12:08:44 Masiina kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Feb 10 12:08:44 Masiina kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36416 r0 d20928 u2097152
Feb 10 12:08:44 Masiina kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
Feb 10 12:08:44 Masiina kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Feb 10 12:08:44 Masiina kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845135
Feb 10 12:08:44 Masiina kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-26-generic root=UUID=4f919ebd-7e14-4ce6-95fb-69c83614f7cb ro quiet splash
Feb 10 12:08:44 Masiina kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.000000] Enabling fast FPU save and restore... done.
Feb 10 12:08:44 Masiina kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Feb 10 12:08:44 Masiina kernel: [    0.000000] Initializing CPU#0
Feb 10 12:08:44 Masiina kernel: [    0.000000] allocated 17037760 bytes of page_cgroup
Feb 10 12:08:44 Masiina kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Feb 10 12:08:44 Masiina kernel: [    0.000000] Subtract (49 early reservations)
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #3 [00009a3000 - 00009a6158]             BRK
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #6 [000009fc00 - 00000fd030]   BIOS reserved
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #7 [00000fd174 - 00000ff780]   BIOS reserved
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #8 [00000fd030 - 00000fd174]    MP-table mpc
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #12 [00009a7000 - 00013eb000]     NEW RAMDISK
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #13 [00013eb000 - 00013ec000]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #14 [00013ec000 - 0002dec000]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #15 [0002dec000 - 0002dec004]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #16 [0002dec040 - 0002dec100]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #17 [0002dec100 - 0002dec154]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #18 [0002dec180 - 0002def180]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #19 [0002def180 - 0002def268]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #20 [0002def280 - 0002dfb280]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #21 [0002dfb280 - 0002dfb2a7]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #22 [0002dfb2c0 - 0002dfb410]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #23 [0002dfb440 - 0002dfb480]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #24 [0002dfb480 - 0002dfb4c0]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #25 [0002dfb4c0 - 0002dfb500]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #26 [0002dfb500 - 0002dfb540]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #27 [0002dfb540 - 0002dfb580]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #28 [0002dfb580 - 0002dfb5c0]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #29 [0002dfb5c0 - 0002dfb600]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #30 [0002dfb600 - 0002dfb640]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #31 [0002dfb640 - 0002dfb680]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #32 [0002dfb680 - 0002dfb6c0]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #33 [0002dfb6c0 - 0002dfb700]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #34 [0002dfb700 - 0002dfb710]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #35 [0002dfb740 - 0002dfb7aa]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #36 [0002dfb7c0 - 0002dfb82a]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #37 [0003000000 - 000300e000]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #38 [0003200000 - 000320e000]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #39 [0002dfd840 - 0002dfd844]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #40 [0002dfd880 - 0002dfd884]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #41 [0002dfd8c0 - 0002dfd8c8]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #42 [0002dfd900 - 0002dfd908]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #43 [0002dfd940 - 0002dfd9e8]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #44 [0002dfda00 - 0002dfda68]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #45 [0002dfda80 - 0002e01a80]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #46 [0002e01a80 - 0002e81a80]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #47 [0002e81a80 - 0002ec1a80]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000]   #48 [000320e000 - 000424d9c0]         BOOTMEM
Feb 10 12:08:44 Masiina kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000cffc0)
Feb 10 12:08:44 Masiina kernel: [    0.000000] Memory: 3343536k/3407616k available (4934k kernel code, 63628k reserved, 2331k data, 688k init, 2498312k highmem)
Feb 10 12:08:44 Masiina kernel: [    0.000000] virtual kernel memory layout:
Feb 10 12:08:44 Masiina kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Feb 10 12:08:44 Masiina kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Feb 10 12:08:44 Masiina kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Feb 10 12:08:44 Masiina kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Feb 10 12:08:44 Masiina kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
Feb 10 12:08:44 Masiina kernel: [    0.000000]       .data : 0xc05d181e - 0xc08187a8   (2331 kB)
Feb 10 12:08:44 Masiina kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d181e   (4934 kB)
Feb 10 12:08:44 Masiina kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Feb 10 12:08:44 Masiina kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Feb 10 12:08:44 Masiina kernel: [    0.000000] Hierarchical RCU implementation.
Feb 10 12:08:44 Masiina kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Feb 10 12:08:44 Masiina kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Feb 10 12:08:44 Masiina kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Feb 10 12:08:44 Masiina kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512
Feb 10 12:08:44 Masiina kernel: [    0.000000] Console: colour VGA+ 80x25
Feb 10 12:08:44 Masiina kernel: [    0.000000] console [tty0] enabled
Feb 10 12:08:44 Masiina kernel: [    0.000000] Fast TSC calibration using PIT
Feb 10 12:08:44 Masiina kernel: [    0.000000] Detected 3084.458 MHz processor.
Feb 10 12:08:44 Masiina kernel: [    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6168.91 BogoMIPS (lpj=12337832)
Feb 10 12:08:44 Masiina kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Feb 10 12:08:44 Masiina kernel: [    0.004025] Security Framework initialized
Feb 10 12:08:44 Masiina kernel: [    0.004043] AppArmor: AppArmor initialized
Feb 10 12:08:44 Masiina kernel: [    0.004045] Yama: becoming mindful.
Feb 10 12:08:44 Masiina kernel: [    0.004092] Mount-cache hash table entries: 512
Feb 10 12:08:44 Masiina kernel: [    0.004201] Initializing cgroup subsys ns
Feb 10 12:08:44 Masiina kernel: [    0.004205] Initializing cgroup subsys cpuacct
Feb 10 12:08:44 Masiina kernel: [    0.004209] Initializing cgroup subsys memory
Feb 10 12:08:44 Masiina kernel: [    0.004216] Initializing cgroup subsys devices
Feb 10 12:08:44 Masiina kernel: [    0.004218] Initializing cgroup subsys freezer
Feb 10 12:08:44 Masiina kernel: [    0.004221] Initializing cgroup subsys net_cls
Feb 10 12:08:44 Masiina kernel: [    0.004241] CPU: Physical Processor ID: 0
Feb 10 12:08:44 Masiina kernel: [    0.004243] CPU: Processor Core ID: 0
Feb 10 12:08:44 Masiina kernel: [    0.004245] mce: CPU supports 5 MCE banks
Feb 10 12:08:44 Masiina kernel: [    0.004253] using C1E aware idle routine
Feb 10 12:08:44 Masiina kernel: [    0.004259] Performance Events: AMD PMU driver.
Feb 10 12:08:44 Masiina kernel: [    0.004265] ... version:                0
Feb 10 12:08:44 Masiina kernel: [    0.004267] ... bit width:              48
Feb 10 12:08:44 Masiina kernel: [    0.004269] ... generic registers:      4
Feb 10 12:08:44 Masiina kernel: [    0.004271] ... value mask:             0000ffffffffffff
Feb 10 12:08:44 Masiina kernel: [    0.004273] ... max period:             00007fffffffffff
Feb 10 12:08:44 Masiina kernel: [    0.004275] ... fixed-purpose events:   0
Feb 10 12:08:44 Masiina kernel: [    0.004276] ... event mask:             000000000000000f
Feb 10 12:08:44 Masiina kernel: [    0.006179] ACPI: Core revision 20100428
Feb 10 12:08:44 Masiina kernel: [    0.012596] ftrace: converting mcount calls to 0f 1f 44 00 00
Feb 10 12:08:44 Masiina kernel: [    0.012601] ftrace: allocating 21755 entries in 43 pages
Feb 10 12:08:44 Masiina kernel: [    0.016063] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Feb 10 12:08:44 Masiina kernel: [    0.016513] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
Feb 10 12:08:44 Masiina kernel: [    0.057494] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 02
Feb 10 12:08:44 Masiina kernel: [    0.060000] Booting Node   0, Processors  #1 Ok.
Feb 10 12:08:44 Masiina kernel: [    0.008000] Initializing CPU#1
Feb 10 12:08:44 Masiina kernel: [    0.144115] Brought up 2 CPUs
Feb 10 12:08:44 Masiina kernel: [    0.144118] Total of 2 processors activated (12337.89 BogoMIPS).
Feb 10 12:08:44 Masiina kernel: [    0.144330] devtmpfs: initialized
Feb 10 12:08:44 Masiina kernel: [    0.144709] regulator: core version 0.5
Feb 10 12:08:44 Masiina kernel: [    0.144743] Time: 12:08:25  Date: 02/10/11
Feb 10 12:08:44 Masiina kernel: [    0.144778] NET: Registered protocol family 16
Feb 10 12:08:44 Masiina kernel: [    0.144876] EISA bus registered
Feb 10 12:08:44 Masiina kernel: [    0.144884] TOM: 00000000d0000000 aka 3328M
Feb 10 12:08:44 Masiina kernel: [    0.144893] TOM2: 0000000130000000 aka 4864M
Feb 10 12:08:44 Masiina kernel: [    0.144906] ACPI: bus type pci registered
Feb 10 12:08:44 Masiina kernel: [    0.144961] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Feb 10 12:08:44 Masiina kernel: [    0.144964] PCI: not using MMCONFIG
Feb 10 12:08:44 Masiina kernel: [    0.145487] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Feb 10 12:08:44 Masiina kernel: [    0.145489] PCI: Using configuration type 1 for base access
Feb 10 12:08:44 Masiina kernel: [    0.146191] Trying to unpack rootfs image as initramfs...
Feb 10 12:08:44 Masiina kernel: [    0.146191] bio: create slab <bio-0> at 0
Feb 10 12:08:44 Masiina kernel: [    0.148770] ACPI: Executed 1 blocks of module-level executable AML code
Feb 10 12:08:44 Masiina kernel: [    0.153347] ACPI: Interpreter enabled
Feb 10 12:08:44 Masiina kernel: [    0.153350] ACPI: (supports S0 S1 S4 S5)
Feb 10 12:08:44 Masiina kernel: [    0.153363] ACPI: Using IOAPIC for interrupt routing
Feb 10 12:08:44 Masiina kernel: [    0.153396] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Feb 10 12:08:44 Masiina kernel: [    0.154803] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Feb 10 12:08:44 Masiina kernel: [    0.154805] PCI: Using MMCONFIG for extended config space
Feb 10 12:08:44 Masiina kernel: [    0.160480] ACPI Warning: Incorrect checksum in table [OEMB] - 0xD0, should be 0xCB (20100428/tbutils-314)
Feb 10 12:08:44 Masiina kernel: [    0.160565] ACPI: No dock devices found.
Feb 10 12:08:44 Masiina kernel: [    0.160568] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Feb 10 12:08:44 Masiina kernel: [    0.160821] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Feb 10 12:08:44 Masiina kernel: [    0.161036] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
Feb 10 12:08:44 Masiina kernel: [    0.161038] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
Feb 10 12:08:44 Masiina kernel: [    0.161040] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
Feb 10 12:08:44 Masiina kernel: [    0.161042] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
Feb 10 12:08:44 Masiina kernel: [    0.161044] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xdfffffff]
Feb 10 12:08:44 Masiina kernel: [    0.161046] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
Feb 10 12:08:44 Masiina kernel: [    0.161703] pci 0000:00:08.0: PCI bridge to [bus 01-01] (subtractive decode)
Feb 10 12:08:44 Masiina kernel: [    0.161741] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
Feb 10 12:08:44 Masiina kernel: [    0.161864] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Feb 10 12:08:44 Masiina kernel: [    0.161871] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
Feb 10 12:08:44 Masiina kernel: [    0.168009] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
Feb 10 12:08:44 Masiina kernel: [    0.168034] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
Feb 10 12:08:44 Masiina kernel: [    0.173289] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.173448] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.173604] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.173757] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.173917] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
Feb 10 12:08:44 Masiina kernel: [    0.174068] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.174220] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.174376] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *10
Feb 10 12:08:44 Masiina kernel: [    0.174531] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
Feb 10 12:08:44 Masiina kernel: [    0.174686] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
Feb 10 12:08:44 Masiina kernel: [    0.174838] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.174993] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
Feb 10 12:08:44 Masiina kernel: [    0.175157] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
Feb 10 12:08:44 Masiina kernel: [    0.175315] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.175471] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
Feb 10 12:08:44 Masiina kernel: [    0.175653] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.175808] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.175961] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *0, disabled.
Feb 10 12:08:44 Masiina kernel: [    0.176007] HEST: Table is not found!
Feb 10 12:08:44 Masiina kernel: [    0.176073] vgaarb: device added: PCI:0000:04:00.0,decodes=io+mem,owns=io+mem,locks=none
Feb 10 12:08:44 Masiina kernel: [    0.176075] vgaarb: loaded
Feb 10 12:08:44 Masiina kernel: [    0.176193] SCSI subsystem initialized
Feb 10 12:08:44 Masiina kernel: [    0.176297] usbcore: registered new interface driver usbfs
Feb 10 12:08:44 Masiina kernel: [    0.176306] usbcore: registered new interface driver hub
Feb 10 12:08:44 Masiina kernel: [    0.176323] usbcore: registered new device driver usb
Feb 10 12:08:44 Masiina kernel: [    0.176427] ACPI: WMI: Mapper loaded
Feb 10 12:08:44 Masiina kernel: [    0.176428] PCI: Using ACPI for IRQ routing
Feb 10 12:08:44 Masiina kernel: [    0.176548] NetLabel: Initializing
Feb 10 12:08:44 Masiina kernel: [    0.176550] NetLabel:  domain hash size = 128
Feb 10 12:08:44 Masiina kernel: [    0.176551] NetLabel:  protocols = UNLABELED CIPSOv4
Feb 10 12:08:44 Masiina kernel: [    0.176560] NetLabel:  unlabeled traffic allowed by default
Feb 10 12:08:44 Masiina kernel: [    0.183471] AppArmor: AppArmor Filesystem Enabled
Feb 10 12:08:44 Masiina kernel: [    0.183488] pnp: PnP ACPI init
Feb 10 12:08:44 Masiina kernel: [    0.183502] ACPI: bus type pnp registered
Feb 10 12:08:44 Masiina kernel: [    0.186988] pnp: PnP ACPI: found 13 devices
Feb 10 12:08:44 Masiina kernel: [    0.186989] ACPI: ACPI bus type pnp unregistered
Feb 10 12:08:44 Masiina kernel: [    0.186992] PnPBIOS: Disabled by ACPI PNP
Feb 10 12:08:44 Masiina kernel: [    0.187002] system 00:06: [io  0x04d0-0x04d1] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187004] system 00:06: [io  0x0800-0x080f] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187006] system 00:06: [io  0x2000-0x207f] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187008] system 00:06: [io  0x2080-0x20ff] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187011] system 00:06: [io  0x2400-0x247f] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187013] system 00:06: [io  0x2480-0x24ff] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187015] system 00:06: [io  0x2800-0x287f] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187017] system 00:06: [io  0x2880-0x28ff] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187019] system 00:06: [io  0x2c00-0x2c7f] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187021] system 00:06: [io  0x2c80-0x2cff] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187023] system 00:06: [mem 0x000d0000-0x000d3fff window] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187025] system 00:06: [mem 0x000d4000-0x000d7fff window] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187028] system 00:06: [mem 0x000de000-0x000dffff window] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187030] system 00:06: [mem 0xfec80000-0xfd93ffff] could not be reserved
Feb 10 12:08:44 Masiina kernel: [    0.187032] system 00:06: [mem 0xfee01000-0xfeefffff] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187037] system 00:08: [mem 0xfec00000-0xfec00fff] could not be reserved
Feb 10 12:08:44 Masiina kernel: [    0.187039] system 00:08: [mem 0xfee00000-0xfee00fff] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187042] system 00:0a: [io  0x0a00-0x0a0f] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187044] system 00:0a: [io  0x0a10-0x0a1f] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187048] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
Feb 10 12:08:44 Masiina kernel: [    0.187052] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
Feb 10 12:08:44 Masiina kernel: [    0.187054] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
Feb 10 12:08:44 Masiina kernel: [    0.187056] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
Feb 10 12:08:44 Masiina kernel: [    0.187058] system 00:0c: [mem 0x00100000-0xcfffffff] could not be reserved
Feb 10 12:08:44 Masiina kernel: [    0.187060] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
Feb 10 12:08:44 Masiina kernel: [    0.222677] Switching to clocksource acpi_pm
Feb 10 12:08:44 Masiina kernel: [    0.222891] pci 0000:00:08.0: PCI bridge to [bus 01-01]
Feb 10 12:08:44 Masiina kernel: [    0.222893] pci 0000:00:08.0:   bridge window [io  disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222896] pci 0000:00:08.0:   bridge window [mem disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222898] pci 0000:00:08.0:   bridge window [mem pref disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222902] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
Feb 10 12:08:44 Masiina kernel: [    0.222903] pci 0000:00:0b.0:   bridge window [io  disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222905] pci 0000:00:0b.0:   bridge window [mem disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222907] pci 0000:00:0b.0:   bridge window [mem pref disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222910] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
Feb 10 12:08:44 Masiina kernel: [    0.222912] pci 0000:00:0c.0:   bridge window [io  0xd000-0xdfff]
Feb 10 12:08:44 Masiina kernel: [    0.222914] pci 0000:00:0c.0:   bridge window [mem 0xf9f00000-0xf9ffffff]
Feb 10 12:08:44 Masiina kernel: [    0.222916] pci 0000:00:0c.0:   bridge window [mem pref disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222919] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
Feb 10 12:08:44 Masiina kernel: [    0.222921] pci 0000:00:0d.0:   bridge window [io  0xe000-0xefff]
Feb 10 12:08:44 Masiina kernel: [    0.222923] pci 0000:00:0d.0:   bridge window [mem 0xfa000000-0xfebfffff]
Feb 10 12:08:44 Masiina kernel: [    0.222926] pci 0000:00:0d.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Feb 10 12:08:44 Masiina kernel: [    0.222929] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
Feb 10 12:08:44 Masiina kernel: [    0.222930] pci 0000:00:0e.0:   bridge window [io  disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222932] pci 0000:00:0e.0:   bridge window [mem disabled]
Feb 10 12:08:44 Masiina kernel: [    0.222934] pci 0000:00:0e.0:   bridge window [mem pref disabled]
Feb 10 12:08:44 Masiina kernel: [    0.223018] NET: Registered protocol family 2
Feb 10 12:08:44 Masiina kernel: [    0.223063] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.223272] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.223781] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.223990] TCP: Hash tables configured (established 131072 bind 65536)
Feb 10 12:08:44 Masiina kernel: [    0.223990] TCP reno registered
Feb 10 12:08:44 Masiina kernel: [    0.223990] UDP hash table entries: 512 (order: 2, 16384 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.223990] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.223990] NET: Registered protocol family 1
Feb 10 12:08:44 Masiina kernel: [    0.242894] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 10 12:08:44 Masiina kernel: [    0.242937] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 10 12:08:44 Masiina kernel: [    0.242987] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 10 12:08:44 Masiina kernel: [    0.243037] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 10 12:08:44 Masiina kernel: [    0.243091] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 10 12:08:44 Masiina kernel: [    0.243147] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 10 12:08:44 Masiina kernel: [    0.243207] pci 0000:00:00.0: Found enabled HT MSI Mapping
Feb 10 12:08:44 Masiina kernel: [    0.243386] cpufreq-nforce2: No nForce2 chipset.
Feb 10 12:08:44 Masiina kernel: [    0.243408] Scanning for low memory corruption every 60 seconds
Feb 10 12:08:44 Masiina kernel: [    0.243491] audit: initializing netlink socket (disabled)
Feb 10 12:08:44 Masiina kernel: [    0.243498] type=2000 audit(1297339704.239:1): initialized
Feb 10 12:08:44 Masiina kernel: [    0.250965] highmem bounce pool size: 64 pages
Feb 10 12:08:44 Masiina kernel: [    0.250969] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Feb 10 12:08:44 Masiina kernel: [    0.252017] VFS: Disk quotas dquot_6.5.2
Feb 10 12:08:44 Masiina kernel: [    0.252061] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 10 12:08:44 Masiina kernel: [    0.252477] fuse init (API version 7.14)
Feb 10 12:08:44 Masiina kernel: [    0.252541] msgmni has been set to 1650
Feb 10 12:08:44 Masiina kernel: [    0.367465] Freeing initrd memory: 10512k freed
Feb 10 12:08:44 Masiina kernel: [    0.374122] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Feb 10 12:08:44 Masiina kernel: [    0.374126] io scheduler noop registered
Feb 10 12:08:44 Masiina kernel: [    0.374127] io scheduler deadline registered
Feb 10 12:08:44 Masiina kernel: [    0.374137] io scheduler cfq registered (default)
Feb 10 12:08:44 Masiina kernel: [    0.374444] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 10 12:08:44 Masiina kernel: [    0.374462] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 10 12:08:44 Masiina kernel: [    0.374604] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Feb 10 12:08:44 Masiina kernel: [    0.374614] ACPI: Power Button [PWRB]
Feb 10 12:08:44 Masiina kernel: [    0.374654] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Feb 10 12:08:44 Masiina kernel: [    0.374657] ACPI: Power Button [PWRF]
Feb 10 12:08:44 Masiina kernel: [    0.377284] ERST: Table is not found!
Feb 10 12:08:44 Masiina kernel: [    0.377308] isapnp: Scanning for PnP cards...
Feb 10 12:08:44 Masiina kernel: [    0.377404] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb 10 12:08:44 Masiina kernel: [    0.377490] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 10 12:08:44 Masiina kernel: [    0.377698] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 10 12:08:44 Masiina kernel: [    0.378530] brd: module loaded
Feb 10 12:08:44 Masiina kernel: [    0.378903] loop: module loaded
Feb 10 12:08:44 Masiina kernel: [    0.379372] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
Feb 10 12:08:44 Masiina kernel: [    0.379387] pata_acpi 0000:00:0a.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
Feb 10 12:08:44 Masiina kernel: [    0.379403] pata_acpi 0000:00:0a.0: PCI INT A disabled
Feb 10 12:08:44 Masiina kernel: [    0.379651] Fixed MDIO Bus: probed
Feb 10 12:08:44 Masiina kernel: [    0.379677] PPP generic driver version 2.4.2
Feb 10 12:08:44 Masiina kernel: [    0.379711] tun: Universal TUN/TAP device driver, 1.6
Feb 10 12:08:44 Masiina kernel: [    0.379713] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Feb 10 12:08:44 Masiina kernel: [    0.379766] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 10 12:08:44 Masiina kernel: [    0.380055] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
Feb 10 12:08:44 Masiina kernel: [    0.380064] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
Feb 10 12:08:44 Masiina kernel: [    0.380078] ehci_hcd 0000:00:02.1: EHCI Host Controller
Feb 10 12:08:44 Masiina kernel: [    0.380104] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
Feb 10 12:08:44 Masiina kernel: [    0.380123] ehci_hcd 0000:00:02.1: debug port 1
Feb 10 12:08:44 Masiina kernel: [    0.380148] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf9efec00
Feb 10 12:08:44 Masiina kernel: [    0.392017] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
Feb 10 12:08:44 Masiina kernel: [    0.392100] hub 1-0:1.0: USB hub found
Feb 10 12:08:44 Masiina kernel: [    0.392104] hub 1-0:1.0: 10 ports detected
Feb 10 12:08:44 Masiina kernel: [    0.392160] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Feb 10 12:08:44 Masiina kernel: [    0.392412] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
Feb 10 12:08:44 Masiina kernel: [    0.392422] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
Feb 10 12:08:44 Masiina kernel: [    0.392431] ohci_hcd 0000:00:02.0: OHCI Host Controller
Feb 10 12:08:44 Masiina kernel: [    0.392457] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
Feb 10 12:08:44 Masiina kernel: [    0.392478] ohci_hcd 0000:00:02.0: irq 21, io mem 0xf9eff000
Feb 10 12:08:44 Masiina kernel: [    0.450063] hub 2-0:1.0: USB hub found
Feb 10 12:08:44 Masiina kernel: [    0.450067] hub 2-0:1.0: 10 ports detected
Feb 10 12:08:44 Masiina kernel: [    0.450118] uhci_hcd: USB Universal Host Controller Interface driver
Feb 10 12:08:44 Masiina kernel: [    0.450182] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Feb 10 12:08:44 Masiina kernel: [    0.450184] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Feb 10 12:08:44 Masiina kernel: [    0.450879] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 10 12:08:44 Masiina kernel: [    0.450927] mice: PS/2 mouse device common for all mice
Feb 10 12:08:44 Masiina kernel: [    0.451013] rtc_cmos 00:07: RTC can wake from S4
Feb 10 12:08:44 Masiina kernel: [    0.451043] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Feb 10 12:08:44 Masiina kernel: [    0.451075] rtc0: alarms up to one year, y3k, 114 bytes nvram
Feb 10 12:08:44 Masiina kernel: [    0.451150] device-mapper: uevent: version 1.0.3
Feb 10 12:08:44 Masiina kernel: [    0.451237] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Feb 10 12:08:44 Masiina kernel: [    0.451294] device-mapper: multipath: version 1.1.1 loaded
Feb 10 12:08:44 Masiina kernel: [    0.451296] device-mapper: multipath round-robin: version 1.0.0 loaded
Feb 10 12:08:44 Masiina kernel: [    0.451380] EISA: Probing bus 0 at eisa.0
Feb 10 12:08:44 Masiina kernel: [    0.451382] EISA: Cannot allocate resource for mainboard
Feb 10 12:08:44 Masiina kernel: [    0.451384] Cannot allocate resource for EISA slot 1
Feb 10 12:08:44 Masiina kernel: [    0.451386] Cannot allocate resource for EISA slot 2
Feb 10 12:08:44 Masiina kernel: [    0.451387] Cannot allocate resource for EISA slot 3
Feb 10 12:08:44 Masiina kernel: [    0.451389] Cannot allocate resource for EISA slot 4
Feb 10 12:08:44 Masiina kernel: [    0.451391] Cannot allocate resource for EISA slot 5
Feb 10 12:08:44 Masiina kernel: [    0.451392] Cannot allocate resource for EISA slot 6
Feb 10 12:08:44 Masiina kernel: [    0.451394] Cannot allocate resource for EISA slot 7
Feb 10 12:08:44 Masiina kernel: [    0.451395] Cannot allocate resource for EISA slot 8
Feb 10 12:08:44 Masiina kernel: [    0.451397] EISA: Detected 0 cards.
Feb 10 12:08:44 Masiina kernel: [    0.451456] cpuidle: using governor ladder
Feb 10 12:08:44 Masiina kernel: [    0.451457] cpuidle: using governor menu
Feb 10 12:08:44 Masiina kernel: [    0.451667] TCP cubic registered
Feb 10 12:08:44 Masiina kernel: [    0.451763] NET: Registered protocol family 10
Feb 10 12:08:44 Masiina kernel: [    0.452062] lo: Disabled Privacy Extensions
Feb 10 12:08:44 Masiina kernel: [    0.452235] NET: Registered protocol family 17
Feb 10 12:08:44 Masiina kernel: [    0.452260] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ (2 cpu cores) (version 2.20.00)
Feb 10 12:08:44 Masiina kernel: [    0.452301] powernow-k8:    0 : fid 0x17 (3100 MHz), vid 0x5
Feb 10 12:08:44 Masiina kernel: [    0.452303] powernow-k8:    1 : fid 0x16 (3000 MHz), vid 0x6
Feb 10 12:08:44 Masiina kernel: [    0.452305] powernow-k8:    2 : fid 0x14 (2800 MHz), vid 0x8
Feb 10 12:08:44 Masiina kernel: [    0.452307] powernow-k8:    3 : fid 0x12 (2600 MHz), vid 0xa
Feb 10 12:08:44 Masiina kernel: [    0.452308] powernow-k8:    4 : fid 0x10 (2400 MHz), vid 0xc
Feb 10 12:08:44 Masiina kernel: [    0.452310] powernow-k8:    5 : fid 0xe (2200 MHz), vid 0xe
Feb 10 12:08:44 Masiina kernel: [    0.452312] powernow-k8:    6 : fid 0xc (2000 MHz), vid 0x10
Feb 10 12:08:44 Masiina kernel: [    0.452313] powernow-k8:    7 : fid 0xa (1800 MHz), vid 0x10
Feb 10 12:08:44 Masiina kernel: [    0.452315] powernow-k8:    8 : fid 0x2 (1000 MHz), vid 0x12
Feb 10 12:08:44 Masiina kernel: [    0.452344] Using IPI No-Shortcut mode
Feb 10 12:08:44 Masiina kernel: [    0.452419] registered taskstats version 1
Feb 10 12:08:44 Masiina kernel: [    0.452583]   Magic number: 15:62:127
Feb 10 12:08:44 Masiina kernel: [    0.452625] acpi device:02: hash matches
Feb 10 12:08:44 Masiina kernel: [    0.452668] rtc_cmos 00:07: setting system clock to 2011-02-10 12:08:25 UTC (1297339705)
Feb 10 12:08:44 Masiina kernel: [    0.452670] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Feb 10 12:08:44 Masiina kernel: [    0.452671] EDD information not available.
Feb 10 12:08:44 Masiina kernel: [    0.475770] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
Feb 10 12:08:44 Masiina kernel: [    0.730120] isapnp: No Plug & Play device found
Feb 10 12:08:44 Masiina kernel: [    0.730147] Freeing unused kernel memory: 688k freed
Feb 10 12:08:44 Masiina kernel: [    0.730511] Write protecting the kernel text: 4936k
Feb 10 12:08:44 Masiina kernel: [    0.730539] Write protecting the kernel read-only data: 1976k
Feb 10 12:08:44 Masiina kernel: [    0.744297] udev[74]: starting version 163
Feb 10 12:08:44 Masiina kernel: [    0.808055] usb 1-2: new high speed USB device using ehci_hcd and address 3
Feb 10 12:08:44 Masiina kernel: [    0.816915] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb 10 12:08:44 Masiina kernel: [    0.817215] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 19
Feb 10 12:08:44 Masiina kernel: [    0.817230] r8169 0000:03:00.0: PCI INT A -> Link[LNEA] -> GSI 19 (level, low) -> IRQ 19
Feb 10 12:08:44 Masiina kernel: [    0.817674] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xf8098000, 00:21:85:31:54:da, XID 18000000 IRQ 44
Feb 10 12:08:44 Masiina kernel: [    0.836722] scsi0 : pata_amd
Feb 10 12:08:44 Masiina kernel: [    0.841722] scsi1 : pata_amd
Feb 10 12:08:44 Masiina kernel: [    0.842562] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Feb 10 12:08:44 Masiina kernel: [    0.842564] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Feb 10 12:08:44 Masiina kernel: [    0.842737] ahci 0000:00:0a.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
Feb 10 12:08:44 Masiina kernel: [    0.842780] ahci 0000:00:0a.0: controller can't do PMP, turning off CAP_PMP
Feb 10 12:08:44 Masiina kernel: [    0.842821] ahci 0000:00:0a.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Feb 10 12:08:44 Masiina kernel: [    0.842824] ahci 0000:00:0a.0: flags: 64bit ncq sntf pm led clo pio ccc 
Feb 10 12:08:44 Masiina kernel: [    0.843211] scsi2 : ahci
Feb 10 12:08:44 Masiina kernel: [    0.843271] scsi3 : ahci
Feb 10 12:08:44 Masiina kernel: [    0.843319] scsi4 : ahci
Feb 10 12:08:44 Masiina kernel: [    0.843384] scsi5 : ahci
Feb 10 12:08:44 Masiina kernel: [    0.843473] ata3: SATA max UDMA/133 abar m8192@0xf9efc000 port 0xf9efc100 irq 45
Feb 10 12:08:44 Masiina kernel: [    0.843475] ata4: SATA max UDMA/133 abar m8192@0xf9efc000 port 0xf9efc180 irq 45
Feb 10 12:08:44 Masiina kernel: [    0.843478] ata5: SATA max UDMA/133 abar m8192@0xf9efc000 port 0xf9efc200 irq 45
Feb 10 12:08:44 Masiina kernel: [    0.843480] ata6: SATA max UDMA/133 abar m8192@0xf9efc000 port 0xf9efc280 irq 45
Feb 10 12:08:44 Masiina kernel: [    1.004403] ata1.00: ATA-7: SAMSUNG SP0802N, TK100-24, max UDMA/100
Feb 10 12:08:44 Masiina kernel: [    1.004406] ata1.00: 156368016 sectors, multi 16: LBA48 
Feb 10 12:08:44 Masiina kernel: [    1.012328] ata1.00: configured for UDMA/33
Feb 10 12:08:44 Masiina kernel: [    1.012464] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0802N  TK10 PQ: 0 ANSI: 5
Feb 10 12:08:44 Masiina kernel: [    1.012602] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb 10 12:08:44 Masiina kernel: [    1.012661] sd 0:0:0:0: [sda] 156368016 512-byte logical blocks: (80.0 GB/74.5 GiB)
Feb 10 12:08:44 Masiina kernel: [    1.012703] sd 0:0:0:0: [sda] Write Protect is off
Feb 10 12:08:44 Masiina kernel: [    1.012720] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 10 12:08:44 Masiina kernel: [    1.012864]  sda: sda1 sda2
Feb 10 12:08:44 Masiina kernel: [    1.016973] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 10 12:08:44 Masiina kernel: [    1.052045] usb 1-4: new high speed USB device using ehci_hcd and address 4
Feb 10 12:08:44 Masiina kernel: [    1.160033] ata6: SATA link down (SStatus 0 SControl 300)
Feb 10 12:08:44 Masiina kernel: [    1.160036] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 10 12:08:44 Masiina kernel: [    1.160048] ata5: SATA link down (SStatus 0 SControl 300)
Feb 10 12:08:44 Masiina kernel: [    1.160051] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 10 12:08:44 Masiina kernel: [    1.160537] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB00, max UDMA/100
Feb 10 12:08:44 Masiina kernel: [    1.160733] ata4.00: ATA-8: WDC WD5000AACS-00G8B1, 05.04C05, max UDMA/133
Feb 10 12:08:44 Masiina kernel: [    1.160736] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Feb 10 12:08:44 Masiina kernel: [    1.161273] ata3.00: configured for UDMA/100
Feb 10 12:08:44 Masiina kernel: [    1.161513] ata4.00: configured for UDMA/133
Feb 10 12:08:44 Masiina kernel: [    1.176581] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB00 PQ: 0 ANSI: 5
Feb 10 12:08:44 Masiina kernel: [    1.180869] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Feb 10 12:08:44 Masiina kernel: [    1.180871] Uniform CD-ROM driver Revision: 3.20
Feb 10 12:08:44 Masiina kernel: [    1.181016] sr 2:0:0:0: Attached scsi generic sg1 type 5
Feb 10 12:08:44 Masiina kernel: [    1.181121] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 05.0 PQ: 0 ANSI: 5
Feb 10 12:08:44 Masiina kernel: [    1.181244] sd 3:0:0:0: Attached scsi generic sg2 type 0
Feb 10 12:08:44 Masiina kernel: [    1.181269] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Feb 10 12:08:44 Masiina kernel: [    1.181327] sd 3:0:0:0: [sdb] Write Protect is off
Feb 10 12:08:44 Masiina kernel: [    1.181344] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 10 12:08:44 Masiina kernel: [    1.181450]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
Feb 10 12:08:44 Masiina kernel: [    1.216902] sd 3:0:0:0: [sdb] Attached SCSI disk
Feb 10 12:08:44 Masiina kernel: [    1.356025] usb 1-6: new high speed USB device using ehci_hcd and address 6
Feb 10 12:08:44 Masiina kernel: [    1.501077] Initializing USB Mass Storage driver...
Feb 10 12:08:44 Masiina kernel: [    1.501206] scsi6 : usb-storage 1-6:1.3
Feb 10 12:08:44 Masiina kernel: [    1.501303] usbcore: registered new interface driver usb-storage
Feb 10 12:08:44 Masiina kernel: [    1.501304] USB Mass Storage support registered.
Feb 10 12:08:44 Masiina kernel: [    1.518819] EXT3-fs: barriers not enabled
Feb 10 12:08:44 Masiina kernel: [    1.525209] kjournald starting.  Commit interval 5 seconds
Feb 10 12:08:44 Masiina kernel: [    1.525245] EXT3-fs (sdb2): mounted filesystem with ordered data mode
Feb 10 12:08:44 Masiina kernel: [    1.797021] usb 2-1: new low speed USB device using ohci_hcd and address 2
Feb 10 12:08:44 Masiina kernel: [    2.321024] usb 2-5: new low speed USB device using ohci_hcd and address 3
Feb 10 12:08:44 Masiina kernel: [    2.502472] scsi 6:0:0:0: Direct-Access     ZTE      MMC Storage      2.31 PQ: 0 ANSI: 2
Feb 10 12:08:44 Masiina kernel: [    2.503085] scsi 6:0:0:1: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Feb 10 12:08:44 Masiina kernel: [    2.503494] sd 6:0:0:0: Attached scsi generic sg3 type 0
Feb 10 12:08:44 Masiina kernel: [    2.505582] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Feb 10 12:08:44 Masiina kernel: [    2.507955] sr1: scsi-1 drive
Feb 10 12:08:44 Masiina kernel: [    2.508070] sr 6:0:0:1: Attached scsi generic sg4 type 5
Feb 10 12:08:44 Masiina kernel: [   17.014530] udev[404]: starting version 163
Feb 10 12:08:44 Masiina kernel: [   17.051867] i2c i2c-0: nForce2 SMBus adapter at 0x2d00
Feb 10 12:08:44 Masiina kernel: [   17.051950] i2c i2c-1: nForce2 SMBus adapter at 0x2e00
Feb 10 12:08:44 Masiina kernel: [   17.059696] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
Feb 10 12:08:44 Masiina kernel: [   17.083712] lp: driver loaded but no devices found
Feb 10 12:08:44 Masiina kernel: [   17.181429] Linux agpgart interface v0.103
Feb 10 12:08:44 Masiina kernel: [   17.188699] Adding 975868k swap on /dev/sdb5.  Priority:-1 extents:1 across:975868k 
Feb 10 12:08:44 Masiina kernel: [   17.211432] usbcore: registered new interface driver usbserial
Feb 10 12:08:44 Masiina kernel: [   17.211443] USB Serial support registered for generic
Feb 10 12:08:44 Masiina kernel: [   17.211490] usbcore: registered new interface driver usbserial_generic
Feb 10 12:08:44 Masiina kernel: [   17.211491] usbserial: USB Serial Driver core
Feb 10 12:08:44 Masiina kernel: [   17.224850] WARNING! power/level is deprecated; use power/control instead
Feb 10 12:08:44 Masiina kernel: [   17.275447] parport_pc 00:05: reported by Plug and Play ACPI
Feb 10 12:08:44 Masiina kernel: [   17.275492] parport0: PC-style at 0x378, irq 7 [PCSPP]
Feb 10 12:08:44 Masiina kernel: [   17.295246] USB Serial support registered for GSM modem (1-port)
Feb 10 12:08:44 Masiina kernel: [   17.295333] option 1-6:1.0: GSM modem (1-port) converter detected
Feb 10 12:08:44 Masiina kernel: [   17.295624] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Feb 10 12:08:44 Masiina kernel: [   17.295643] option 1-6:1.1: GSM modem (1-port) converter detected
Feb 10 12:08:44 Masiina kernel: [   17.295789] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
Feb 10 12:08:44 Masiina kernel: [   17.295804] option 1-6:1.2: GSM modem (1-port) converter detected
Feb 10 12:08:44 Masiina kernel: [   17.295944] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
Feb 10 12:08:44 Masiina kernel: [   17.296208] usbcore: registered new interface driver option
Feb 10 12:08:44 Masiina kernel: [   17.296210] option: v0.7.2:USB Driver for GSM modems
Feb 10 12:08:44 Masiina kernel: [   17.300968] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1734
Feb 10 12:08:44 Masiina kernel: [   17.301166] usbcore: registered new interface driver usblp
Feb 10 12:08:44 Masiina kernel: [   17.312311] usbcore: registered new interface driver hiddev
Feb 10 12:08:44 Masiina kernel: [   17.333987] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
Feb 10 12:08:44 Masiina kernel: [   17.334097] generic-usb 0003:046D:C069.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:02.0-1/input0
Feb 10 12:08:44 Masiina kernel: [   17.334158] usbcore: registered new interface driver usbhid
Feb 10 12:08:44 Masiina kernel: [   17.334160] usbhid: USB HID core driver
Feb 10 12:08:44 Masiina kernel: [   17.342964] type=1400 audit(1297332522.386:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=704 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   17.343165] type=1400 audit(1297332522.386:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=704 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   17.343283] type=1400 audit(1297332522.386:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=704 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   17.345146] type=1400 audit(1297332522.390:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=703 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   17.345349] type=1400 audit(1297332522.390:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=703 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   17.345465] type=1400 audit(1297332522.390:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=703 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   17.346502] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 10 12:08:44 Masiina kernel: [   17.356692] ppdev: user-space parallel port driver
Feb 10 12:08:44 Masiina kernel: [   17.358092] nvidia: module license 'NVIDIA' taints kernel.
Feb 10 12:08:44 Masiina kernel: [   17.358096] Disabling lock debugging due to kernel taint
Feb 10 12:08:44 Masiina kernel: [   17.386828] input: Logitech Logitech Extreme 3D as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input4
Feb 10 12:08:44 Masiina kernel: [   17.386899] logitech 0003:046D:C215.0002: input,hidraw1: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D] on usb-0000:00:02.0-5/input0
Feb 10 12:08:44 Masiina kernel: [   17.433448] lp0: using parport0 (interrupt-driven).
Feb 10 12:08:44 Masiina kernel: [   17.471978] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Feb 10 12:08:44 Masiina kernel: [   17.473298] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Feb 10 12:08:44 Masiina kernel: [   17.473301] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Feb 10 12:08:44 Masiina kernel: [   17.473303] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Feb 10 12:08:44 Masiina kernel: [   17.524489] ip6_tables: (C) 2000-2006 Netfilter Core Team
Feb 10 12:08:44 Masiina kernel: [   17.546110] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
Feb 10 12:08:44 Masiina kernel: [   17.546127] HDA Intel 0000:00:07.0: PCI INT B -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
Feb 10 12:08:44 Masiina kernel: [   17.546129] hda_intel: Disable MSI for Nvidia chipset
Feb 10 12:08:44 Masiina kernel: [   17.645501] dib0700: loaded with support for 14 different device-types
Feb 10 12:08:44 Masiina kernel: [   17.646543] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
Feb 10 12:08:44 Masiina kernel: [   17.647288] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Feb 10 12:08:44 Masiina kernel: [   17.647588] DVB: registering new adapter (Hauppauge Nova-T Stick)
Feb 10 12:08:44 Masiina kernel: [   17.864771] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
Feb 10 12:08:44 Masiina kernel: [   18.083270] DiB0070: successfully identified
Feb 10 12:08:44 Masiina kernel: [   18.083769] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:02.1/usb1/1-4/input/input5
Feb 10 12:08:44 Masiina kernel: [   18.083891] dvb-usb: schedule remote query interval to 50 msecs.
Feb 10 12:08:44 Masiina kernel: [   18.083895] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
Feb 10 12:08:44 Masiina kernel: [   18.084170] usbcore: registered new interface driver dvb_usb_dib0700
Feb 10 12:08:44 Masiina kernel: [   18.168021] hda_codec: ALC888: BIOS auto-probing.
Feb 10 12:08:44 Masiina kernel: [   18.450289] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 18
Feb 10 12:08:44 Masiina kernel: [   18.450305] nvidia 0000:04:00.0: PCI INT A -> Link[LNED] -> GSI 18 (level, low) -> IRQ 18
Feb 10 12:08:44 Masiina kernel: [   18.450315] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Feb 10 12:08:44 Masiina kernel: [   18.450497] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.18  Tue Jan 18 21:44:45 PST 2011
Feb 10 12:08:44 Masiina kernel: [   18.540452] EXT3-fs (sdb2): using internal journal
Feb 10 12:08:44 Masiina kernel: [   19.685062] type=1400 audit(1297332524.730:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1162 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   19.685333] type=1400 audit(1297332524.730:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1162 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   19.715105] r8169 0000:03:00.0: eth0: link down
Feb 10 12:08:44 Masiina kernel: [   19.715265] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 10 12:08:44 Masiina kernel: [   19.741488] type=1400 audit(1297332524.786:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1262 comm="apparmor_parser"
Feb 10 12:08:44 Masiina kernel: [   19.741693] type=1400 audit(1297332524.786:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1262 comm="apparmor_parser"
Feb 10 12:08:45 Masiina inputlircd: Started
Feb 10 12:08:45 Masiina runvdr: stopping after fatal fail (vdr: can't access video directory /tv/Videot/vdr)
Feb 10 12:08:45 Masiina kernel: [   20.127493] vboxdrv: fAsync=1 offMin=0x14d3 offMax=0x14d3
Feb 10 12:08:45 Masiina kernel: [   20.127899] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
Feb 10 12:08:46 Masiina kernel: [   21.282231] usb 1-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Feb 10 12:09:09 Masiina moblock: * Merged ranges: 171402
Feb 10 12:09:09 Masiina moblock: * Skipped useless ranges: 474126
Feb 10 12:09:09 Masiina kernel: [   44.703322] Netfilter messages via NETLINK v0.30.
Feb 10 12:09:09 Masiina moblock: NFQUEUE: binding to queue '92'
Feb 10 12:09:17 Masiina pppd[2119]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Feb 10 12:09:17 Masiina pppd[2119]: pppd 2.4.5 started by root, uid 0
Feb 10 12:09:17 Masiina pppd[2119]: Using interface ppp0
Feb 10 12:09:17 Masiina pppd[2119]: Connect: ppp0 <--> /dev/ttyUSB2
Feb 10 12:09:17 Masiina pppd[2119]: PAP authentication succeeded
Feb 10 12:09:20 Masiina pppd[2119]: Could not determine remote IP address: defaulting to 10.64.64.64

Feb 10 12:09:37 Masiina kernel: Kernel logging (proc) stopped.
Feb 10 12:09:37 Masiina rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1130" x-info="http://www.rsyslog.com"] exiting on signal 15.
Feb 10 12:47:32 Masiina kernel: imklog 4.2.0, log source = /proc/kmsg started.
```

---

