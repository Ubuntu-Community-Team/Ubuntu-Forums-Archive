---
title: "weired problem"
date: 2010-02-13
forum: General Help
---

### Post by sn0m on 2010-02-13
bought a new wd sata hard disk to replace the old one.
Starting up karmic on disk mode, everything ok, started g parted, divided disk in swap, ext4, ntfs partition then tried to install, when it comes to prepare partition the table is empty.......
What is going on here, checked disk with check disk utility and made sure that all partitions are bootable, still no luck?
Anybody has the same problem and how to sort it out?
reg
Sokol

---

### Post by ajgreeny on 2010-02-13
Sorry, but I don't fully understand what you did and what exactly you are trying to achieve, so can you say in more detail.

For example, what do you mean by
> Starting up karmic on disk mode, everything ok, started g parted, divided disk in swap, ext4, ntfs partition then tried to install, when it comes to prepare partition the table is empty
Also why an ntfs partition?  If you will have windows, you should install that first for an easier install plan.

Secondly, did you actually format those partitions in gparted, or just plan them out?

Finally, if you are installing ubuntu on the new disk, you can make all the partitions for that during the install by choosing the manual option at partitioning stage; you do not need to make them first in gparted.

---

### Post by sn0m on 2010-02-13
ajgreeny
thanks for your reply.
I have installed windows seven in the ntfs partition so that I don't have to do MBR all over again.
The problem is that I cant get partition editor when installing ubuntu, so I fired up live cd session and could see my hard disk clearly in gparted and disk utility which reports healthy disk.So i used gparted to partition disk in swap, ext4, ntfs 
Now when attempting to install ubuntu, in step 4/7 the system scans partitions and then brings up an empty partition table.
It must be a bug cas I tried a live cd from fedora and it could bring up all the partitions ready to install....picture for reference
I'm not very lucky am I?
Regards
Sokol

---

### Post by sn0m on 2010-02-13
this is what i get from dmesg

[    0.475804] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.475806] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.475808] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.475810] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.475812] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.475814] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.475817] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.475821] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.475823] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.475825] system 00:02: ioport range 0x290-0x294 has been reserved
[    0.475830] system 00:0b: iomem range 0xe0000000-0xe1ffffff has been reserved
[    0.475837] system 00:0c: iomem range 0xd0000-0xd3fff has been reserved
[    0.475840] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.475842] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.475844] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.475846] system 00:0c: iomem range 0xbfef0000-0xbfefffff could not be reserved
[    0.475848] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.475852] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.475854] system 00:0c: iomem range 0x100000-0xbfeeffff could not be reserved
[    0.475856] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.475858] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.480501] AppArmor: AppArmor Filesystem Enabled
[    0.480555] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.480557] pci 0000:00:08.0:   IO window: disabled
[    0.480560] pci 0000:00:08.0:   MEM window: 0xe7000000-0xe70fffff
[    0.480562] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.480567] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
[    0.480572] pci 0000:00:10.0:   IO window: 0xa000-0xafff
[    0.480581] pci 0000:00:10.0:   MEM window: 0xe2000000-0xe5ffffff
[    0.480588] pci 0000:00:10.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.480601] pci 0000:00:14.0: PCI bridge, secondary bus 0000:03
[    0.480605] pci 0000:00:14.0:   IO window: 0xb000-0xbfff
[    0.480614] pci 0000:00:14.0:   MEM window: 0xe6000000-0xe6ffffff
[    0.480621] pci 0000:00:14.0:   PREFETCH window: 0x000000e7100000-0x000000e71fffff
[    0.480637] pci 0000:00:08.0: setting latency timer to 64
[    0.480912] ACPI: PCI Interrupt Link [AE0A] enabled at IRQ 16
[    0.480914]   alloc irq_desc for 16 on node 0
[    0.480916]   alloc kstat_irqs on node 0
[    0.480920] pci 0000:00:10.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    0.480927] pci 0000:00:10.0: setting latency timer to 64
[    0.481194] ACPI: PCI Interrupt Link [AE4A] enabled at IRQ 16
[    0.481196] pci 0000:00:14.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    0.481204] pci 0000:00:14.0: setting latency timer to 64
[    0.481209] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.481211] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.481213] pci_bus 0000:01: resource 1 mem: [0xe7000000-0xe70fffff]
[    0.481215] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.481217] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.481219] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff]
[    0.481221] pci_bus 0000:02: resource 1 mem: [0xe2000000-0xe5ffffff]
[    0.481223] pci_bus 0000:02: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.481224] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
[    0.481226] pci_bus 0000:03: resource 1 mem: [0xe6000000-0xe6ffffff]
[    0.481228] pci_bus 0000:03: resource 2 pref mem [0xe7100000-0xe71fffff]
[    0.481255] NET: Registered protocol family 2
[    0.481380] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.482575] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.485410] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.485868] TCP: Hash tables configured (established 524288 bind 65536)
[    0.485870] TCP reno registered
[    0.485950] NET: Registered protocol family 1
[    0.486003] Trying to unpack rootfs image as initramfs...
[    1.523347] Freeing initrd memory: 5699k freed
[    1.525802] Scanning for low memory corruption every 60 seconds
[    1.525900] audit: initializing netlink socket (disabled)
[    1.525912] type=2000 audit(1266072822.520:1): initialized
[    1.532355] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.533358] VFS: Disk quotas dquot_6.5.2
[    1.533397] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.533828] fuse init (API version 7.12)
[    1.533882] msgmni has been set to 7927
[    1.534064] alg: No test for stdrng (krng)
[    1.534080] io scheduler noop registered
[    1.534082] io scheduler anticipatory registered
[    1.534083] io scheduler deadline registered
[    1.534110] io scheduler cfq registered (default)
[    1.583752] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.583852] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.583977] pci 0000:02:00.0: Boot video device
[    1.584270]   alloc irq_desc for 24 on node 0
[    1.584271]   alloc kstat_irqs on node 0
[    1.584290] pcieport-driver 0000:00:10.0: irq 24 for MSI/MSI-X
[    1.584309] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.584701]   alloc irq_desc for 25 on node 0
[    1.584702]   alloc kstat_irqs on node 0
[    1.584717] pcieport-driver 0000:00:14.0: irq 25 for MSI/MSI-X
[    1.584735] pcieport-driver 0000:00:14.0: setting latency timer to 64
[    1.584888] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.584905] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.585007] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.585010] ACPI: Power Button [PWRF]
[    1.585045] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.585047] ACPI: Power Button [PWRB]
[    1.585486] processor LNXCPU:00: registered as cooling_device0
[    1.585508] processor LNXCPU:01: registered as cooling_device1
[    1.591979] Linux agpgart interface v0.103
[    1.591986] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.592077] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.592288] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.592945] brd: module loaded
[    1.593248] loop: module loaded
[    1.593297] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.593389] ahci 0000:00:09.0: version 3.0
[    1.593695] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.593698]   alloc irq_desc for 23 on node 0
[    1.593699]   alloc kstat_irqs on node 0
[    1.593705] ahci 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.593732]   alloc irq_desc for 26 on node 0
[    1.593733]   alloc kstat_irqs on node 0
[    1.593738] ahci 0000:00:09.0: irq 26 for MSI/MSI-X
[    1.593802] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.593805] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.593807] ahci 0000:00:09.0: setting latency timer to 64
[    1.594217] scsi0 : ahci
[    1.594316] scsi1 : ahci
[    1.594362] scsi2 : ahci
[    1.594407] scsi3 : ahci
[    1.594450] scsi4 : ahci
[    1.594498] scsi5 : ahci
[    1.594613] ata1: SATA max UDMA/133 abar m8192@0xe7204000 port 0xe7204100 irq 26
[    1.594616] ata2: SATA max UDMA/133 abar m8192@0xe7204000 port 0xe7204180 irq 26
[    1.594618] ata3: SATA max UDMA/133 abar m8192@0xe7204000 port 0xe7204200 irq 26
[    1.594620] ata4: SATA max UDMA/133 abar m8192@0xe7204000 port 0xe7204280 irq 26
[    1.594622] ata5: SATA max UDMA/133 abar m8192@0xe7204000 port 0xe7204300 irq 26
[    1.594624] ata6: SATA max UDMA/133 abar m8192@0xe7204000 port 0xe7204380 irq 26
[    1.594831] pata_amd 0000:00:06.0: version 0.4.1
[    1.594862] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.594928] scsi6 : pata_amd
[    1.594974] scsi7 : pata_amd
[    1.595560] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.595562] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.596020] Fixed MDIO Bus: probed
[    1.596046] PPP generic driver version 2.4.2
[    1.596123] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.596453] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    1.596456]   alloc irq_desc for 22 on node 0
[    1.596457]   alloc kstat_irqs on node 0
[    1.596462] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    1.596475] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.596477] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.596520] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.596544] ehci_hcd 0000:00:02.1: debug port 1
[    1.596548] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.596560] ehci_hcd 0000:00:02.1: irq 22, io mem 0xe720b000
[    1.610011] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.610068] usb usb1: configuration #1 chosen from 1 choice
[    1.610091] hub 1-0:1.0: USB hub found
[    1.610097] hub 1-0:1.0: 6 ports detected
[    1.610349] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    1.610466] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    1.610468]   alloc irq_desc for 21 on node 0
[    1.610470]   alloc kstat_irqs on node 0
[    1.610473] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    1.610481] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.610483] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.610512] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.610532] ehci_hcd 0000:00:04.1: debug port 1
[    1.610535] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.610545] ehci_hcd 0000:00:04.1: irq 21, io mem 0xe7209000
[    1.630010] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.630051] usb usb2: configuration #1 chosen from 1 choice
[    1.630069] hub 2-0:1.0: USB hub found
[    1.630073] hub 2-0:1.0: 6 ports detected
[    1.630122] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.630439] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    1.630441]   alloc irq_desc for 20 on node 0
[    1.630442]   alloc kstat_irqs on node 0
[    1.630445] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    1.630452] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.630454] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.630476] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.630492] ohci_hcd 0000:00:02.0: irq 20, io mem 0xe720a000
[    1.692054] usb usb3: configuration #1 chosen from 1 choice
[    1.692071] hub 3-0:1.0: USB hub found
[    1.692078] hub 3-0:1.0: 6 ports detected
[    1.692442] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    1.692445] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    1.692451] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.692453] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.692477] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.692494] ohci_hcd 0000:00:04.0: irq 23, io mem 0xe720c000
[    1.752222] usb usb4: configuration #1 chosen from 1 choice
[    1.752243] hub 4-0:1.0: USB hub found
[    1.752249] hub 4-0:1.0: 6 ports detected
[    1.752296] uhci_hcd: USB Universal Host Controller Interface driver
[    1.752375] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.752376] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.752746] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.752750] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.752809] mice: PS/2 mouse device common for all mice
[    1.752877] rtc_cmos 00:05: RTC can wake from S4
[    1.752905] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.752952] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.753032] device-mapper: uevent: version 1.0.3
[    1.753103] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.753170] device-mapper: multipath: version 1.1.0 loaded
[    1.753173] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.753317] cpuidle: using governor ladder
[    1.753318] cpuidle: using governor menu
[    1.753618] TCP cubic registered
[    1.753706] NET: Registered protocol family 10
[    1.754015] lo: Disabled Privacy Extensions
[    1.754208] NET: Registered protocol family 17
[    1.754222] Bluetooth: L2CAP ver 2.13
[    1.754223] Bluetooth: L2CAP socket layer initialized
[    1.754226] Bluetooth: SCO (Voice Link) ver 0.6
[    1.754227] Bluetooth: SCO socket layer initialized
[    1.754254] Bluetooth: RFCOMM TTY layer initialized
[    1.754256] Bluetooth: RFCOMM socket layer initialized
[    1.754257] Bluetooth: RFCOMM ver 1.11
[    1.754278] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ processors (2 cpu cores) (version 2.20.00)
[    1.754326] powernow-k8:    0 : fid 0x16 (3000 MHz), vid 0x8
[    1.754328] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0xa
[    1.754330] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xc
[    1.754331] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xe
[    1.754333] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0x10
[    1.754334] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x10
[    1.754336] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x10
[    1.754337] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12
[    1.754431] PM: Resume from disk failed.
[    1.754440] registered taskstats version 1
[    1.754545]   Magic number: 14:773:889
[    1.754659] rtc_cmos 00:05: setting system clock to 2010-02-13 14:53:43 UTC (1266072823)
[    1.754661] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.754662] EDD information not available.
[    1.770353] ata7.00: ATAPI: HL-DT-STDVD-RAM GH22LP20, 1.03, max UDMA/66
[    1.770371] ata7: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    1.810302] ata7.00: configured for UDMA/66
[    1.940019] ata3: SATA link down (SStatus 0 SControl 300)
[    1.940031] ata4: SATA link down (SStatus 0 SControl 300)
[    1.940041] ata5: SATA link down (SStatus 0 SControl 300)
[    1.940051] ata6: SATA link down (SStatus 0 SControl 300)
[    1.940061] ata2: SATA link down (SStatus 0 SControl 300)
[    2.010015] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    2.120015] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.121892] ata1.00: HPA unlocked: 976771055 -> 976773168, native 976773168
[    2.121896] ata1.00: ATA-8: WDC WD5000AAKS-00V1A0, 05.01D05, max UDMA/133
[    2.121898] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.123901] ata1.00: configured for UDMA/133
[    2.123977] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 05.0 PQ: 0 ANSI: 5
[    2.124067] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.124096] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.124127] sd 0:0:0:0: [sda] Write Protect is off
[    2.124129] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.124144] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.124235]  sda:
[    2.125359] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22LP20 1.03 PQ: 0 ANSI: 5
[    2.126903] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.126906] Uniform CD-ROM driver Revision: 3.20
[    2.126959] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    2.126990] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    2.127017] ata8: port disabled. ignoring.
[    2.134945]  sda1 sda2 sda3
[    2.135316] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.135331] Freeing unused kernel memory: 660k freed
[    2.135585] Write protecting the kernel read-only data: 7580k
[    2.164750] usb 2-4: configuration #1 chosen from 1 choice
[    2.251984] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.252009] r8169 0000:03:00.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    2.252054] r8169 0000:03:00.0: setting latency timer to 64
[    2.252085]   alloc irq_desc for 27 on node 0
[    2.252086]   alloc kstat_irqs on node 0
[    2.252096] r8169 0000:03:00.0: irq 27 for MSI/MSI-X
[    2.252537] eth0: RTL8168c/8111c at 0xffffc90000662000, 00:24:1d:6c:16:4a, XID 3c4000c0 IRQ 27
[    2.259278] Floppy drive(s): fd0 is 1.44M
[    2.275874] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    2.275879]   alloc irq_desc for 19 on node 0
[    2.275881]   alloc kstat_irqs on node 0
[    2.275887] ohci1394 0000:01:0e.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    2.282703] usb 2-5: new high speed USB device using ehci_hcd and address 4
[    2.287613] FDC 0 is a post-1991 82077
[    2.330065] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[e700c000-e700c7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.445261] usb 2-5: configuration #1 chosen from 1 choice
[    2.451444] Initializing USB Mass Storage driver...
[    2.451589] scsi8 : SCSI emulation for USB Mass Storage devices
[    2.451694] usb-storage: device found at 4
[    2.451696] usb-storage: waiting for device to settle before scanning
[    2.451701] usbcore: registered new interface driver usb-storage
[    2.451703] USB Mass Storage support registered.
[    2.621263] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    2.865258] usb 4-1: configuration #1 chosen from 1 choice
[    2.890055] usbcore: registered new interface driver hiddev
[    2.900446] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0/input/input3
[    2.900495] generic-usb 0003:045E:00DD.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:04.0-1/input0
[    2.918275] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.1/input/input4
[    2.918308] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:04.0-1/input1
[    2.918318] usbcore: registered new interface driver usbhid
[    2.918320] usbhid: v2.6:USB HID core driver
[    3.324488] xor: automatically using best checksumming function: generic_sse
[    3.370019]    generic_sse:  9383.600 MB/sec
[    3.370021] xor: using function: generic_sse (9383.600 MB/sec)
[    3.371737] device-mapper: dm-raid45: initialized v0.2594b
[    3.450869] EXT4-fs (sda2): barriers enabled
[    3.458740] kjournald2 starting: pid 516, dev sda2:8, commit interval 5 seconds
[    3.458756] EXT4-fs (sda2): delayed allocation enabled
[    3.458759] EXT4-fs: file extents enabled
[    3.460905] EXT4-fs: mballoc enabled
[    3.460917] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    3.473982] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[    3.473984] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[    3.473986] EXT4-fs: mballoc: 0 generated and it took 0
[    3.473988] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[    3.690181] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[006e03b700001d7d]
[    4.608545] ISO 9660 Extensions: Microsoft Joliet Level 3
[    4.638472] ISO 9660 Extensions: RRIP_1991A
[    4.874695] aufs 2-standalone.tree-30-20090727
[    5.058129] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    7.450242] usb-storage: device scan complete
[    7.456960] scsi 8:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    7.463952] scsi 8:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[    7.471078] scsi 8:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    7.478076] scsi 8:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[    7.478423] sd 8:0:0:0: Attached scsi generic sg2 type 0
[    7.478498] sd 8:0:0:1: Attached scsi generic sg3 type 0
[    7.478567] sd 8:0:0:2: Attached scsi generic sg4 type 0
[    7.478636] sd 8:0:0:3: Attached scsi generic sg5 type 0
[    7.497575] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[    7.498322] sd 8:0:0:1: [sdc] Attached SCSI removable disk
[    7.499942] sd 8:0:0:3: [sde] Attached SCSI removable disk
[    7.500694] sd 8:0:0:2: [sdd] Attached SCSI removable disk
[   56.801375] udev: starting version 147
[   59.026639] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   59.285732] EDAC MC: Ver: 2.1.0 Oct 16 2009
[   59.618411] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   59.618429] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   59.778328] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[   59.778452] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   59.778456] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   59.778459] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   59.778460]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   59.778461]     Might be a BIOS bug, if BIOS says ECC is enabled
[   59.778461]     Use of the override can cause unknown side effects.
[   59.778773] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   60.087073] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   60.490053] cfg80211: Calling CRDA to update world regulatory domain
[   62.300577] ip_tables: (C) 2000-2006 Netfilter Core Team
[   64.067255] rt61pci 0000:01:09.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   64.873871] phy0: Selected rate control algorithm 'minstrel'
[   64.874411] Registered led device: rt61pci-phy0::radio
[   64.874426] Registered led device: rt61pci-phy0::assoc
[   65.163674] cfg80211: World regulatory domain updated:
[   65.163677] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   65.163680] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.163682] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   65.163684] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   65.163685] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.163687] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.612323] rt61pci 0000:01:09.0: firmware: requesting rt2561s.bin
[   67.368933] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   67.368938] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   67.368984] HDA Intel 0000:00:07.0: setting latency timer to 64
[   67.441817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   67.443048] r8169: eth0: link down
[   67.443511] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.821343] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   68.860065] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input6
[   72.472262] lp: driver loaded but no devices found
[   72.687557] usplash:437 freeing invalid memtype ffffffffe3000000-ffffffffe3e00000
[   72.801413] ppdev: user-space parallel port driver
[   81.727774] CPU0 attaching NULL sched-domain.
[   81.727779] CPU1 attaching NULL sched-domain.
[   81.760093] CPU0 attaching sched-domain:
[   81.760096]  domain 0: span 0-1 level MC
[   81.760098]   groups: 0 1
[   81.760101]   domain 1: span 0-1 level CPU
[   81.760103]    groups: 0-1 (__cpu_power = 2048)
[   81.760106] CPU1 attaching sched-domain:
[   81.760108]  domain 0: span 0-1 level MC
[   81.760109]   groups: 1 0
[   81.760112]   domain 1: span 0-1 level CPU
[   81.760113]    groups: 0-1 (__cpu_power = 2048)
[  123.093529] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  123.095764] SGI XFS Quota Management subsystem
[  123.185084] JFS: nTxBlock = 8192, nTxLock = 65536
[  123.257482] NTFS driver 2.1.29 [Flags: R/O MODULE].
[  123.439202] QNX4 filesystem 0.2.3 registered.
[  142.000025] Clocksource tsc unstable (delta = -72831877 ns)
[  148.099650] end_request: I/O error, dev fd0, sector 0
[  160.178459] end_request: I/O error, dev fd0, sector 0
[  207.088415] end_request: I/O error, dev fd0, sector 0
[  219.169006] end_request: I/O error, dev fd0, sector 0
[  454.148747] end_request: I/O error, dev fd0, sector 0
[  466.228664] end_request: I/O error, dev fd0, sector 0
[ 1117.800002] end_request: I/O error, dev fd0, sector 0
[ 1129.882165] end_request: I/O error, dev fd0, sector 0
[ 1147.703955] mtrr: no MTRR for d0000000,ff00000 found
[ 1155.148527] CPU0 attaching NULL sched-domain.
[ 1155.148539] CPU1 attaching NULL sched-domain.
[ 1155.190164] CPU0 attaching sched-domain:
[ 1155.190172]  domain 0: span 0-1 level MC
[ 1155.190178]   groups: 0 1
[ 1155.190187] CPU1 attaching sched-domain:
[ 1155.190192]  domain 0: span 0-1 level MC
[ 1155.190197]   groups: 1 0
[ 1243.566228] sd 8:0:0:2: [sdd] 15728640 512-byte logical blocks: (8.05 GB/7.50 GiB)
[ 1243.568710] sd 8:0:0:2: [sdd] Assuming drive cache: write through
[ 1243.572713] sd 8:0:0:2: [sdd] Assuming drive cache: write through
[ 1243.572721]  sdd: sdd1
[ 1434.158712] end_request: I/O error, dev fd0, sector 0
[ 1446.240128] end_request: I/O error, dev fd0, sector 0
[ 1535.535979] sd 8:0:0:2: [sdd] 15728640 512-byte logical blocks: (8.05 GB/7.50 GiB)
[ 1535.538719] sd 8:0:0:2: [sdd] Assuming drive cache: write through
[ 1535.544709] sd 8:0:0:2: [sdd] Assuming drive cache: write through
[ 1535.544717]  sdd: sdd1
[ 2155.808452] end_request: I/O error, dev fd0, sector 0
[ 2167.890517] end_request: I/O error, dev fd0, sector 0
[ 2293.388648] end_request: I/O error, dev fd0, sector 0
[ 2305.468605] end_request: I/O error, dev fd0, sector 0
[ 2366.790087] wlan0: authenticate with AP 00:19:5b:7a:4d:21
[ 2366.791659] wlan0: authenticated
[ 2366.791668] wlan0: associate with AP 00:19:5b:7a:4d:21
[ 2366.794830] wlan0: RX AssocResp from 00:19:5b:7a:4d:21 (capab=0x431 status=0 aid=87)
[ 2366.794836] wlan0: associated
[ 2366.796750] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2367.544510] cfg80211: Calling CRDA for country: US
[ 2367.549222] cfg80211: Received country IE:
[ 2367.549230] cfg80211: Regulatory domain: US
[ 2367.549234] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2367.549240] 	(2402000 KHz - 2477000 KHz @ 40000 KHz), (10000 mBi, 10000 mBm)
[ 2367.549245] cfg80211: CRDA thinks this should applied:
[ 2367.549249] cfg80211: Regulatory domain: US
[ 2367.549252] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2367.549257] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2367.549263] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 2367.549268] 	(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2367.549274] 	(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2367.549279] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 2367.549283] cfg80211: We intersect both of these and get:
[ 2367.549286] cfg80211: Regulatory domain: 98
[ 2367.549289] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2367.549295] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2367.549305] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[ 2367.549310] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[ 2367.549315] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[ 2367.549322] cfg80211: Current regulatory domain updated by AP to: US
[ 2367.549325] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2367.549331] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2377.241269] wlan0: no IPv6 routers present
[ 2523.139085] end_request: I/O error, dev fd0, sector 0
[ 2535.229085] end_request: I/O error, dev fd0, sector 0
ubuntu@ubuntu:~$

---

### Post by sn0m on 2010-02-13
this is fdisk

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047ae9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         973     7815591   82  Linux swap / Solaris
/dev/sda2             974        3405    19535040   83  Linux
/dev/sda3   *        3406       15563    97659135    7  HPFS/NTFS

---

### Post by sn0m on 2010-02-13
It might be that there are some remnants of raid configuration on hdd. When tried to install motherboard went onto raid form and i twinked with it for a while.
Disk is in ide mode now.
Do you guys know how to wipe raid config or wipe any 1 and 0 from hard disk?
regards
Koli

---

### Post by sn0m on 2010-02-14
I manage to get through.
I had to go back and mess with raid utility in motherboard and manage to delete raid configuration on the disk. (I initially played with raid but then mounted it in ide format.)
From then on everything went fine.
It is strange that neither nuke boot or shred facility didn't erase raid configuration.
Also ubuntu should check automatically that the disk is mounted in ide format and has got raid set up in it and erase it, (just re-write config zone with zeros or something). Wintoss (those games he)  was able to do it and ubuntu can do better.
Thanks to everyone that helped me.
Regards
Sokol

---

