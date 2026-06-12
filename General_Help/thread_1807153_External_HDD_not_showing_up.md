---
title: "External HDD not showing up"
date: 2011-07-18
forum: General Help
---

### Post by malel on 2011-07-18
I have just installed Ubuntu 11.04 and all's well except that my external HDD is not showing up . 
Can someone help me on how to get the HDD up as it has some important data on it.
It normally showed up automatically on other Distros

---

### Post by bhinderm on 2011-07-18
Type "sudo dmesg" a few seconds after plugging it in and post the output here. Also type "sudo fdisk -l" Not that it should matter since other distros can detect it but what filesystem is it formatted with?

---

### Post by malel on 2011-07-18
This is the result of 'dmesg'

[    0.267087] PnPBIOS: Disabled by ACPI PNP
[    0.304411] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.304417] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.304421] pci 0000:00:01.0: PCI bridge to [bus 04-04]
[    0.304425] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.304431] pci 0000:00:01.0:   bridge window [mem 0xddf00000-0xdfffffff]
[    0.304437] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.304443] pci 0000:00:1c.0: PCI bridge to [bus 03-03]
[    0.304447] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.304454] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.304460] pci 0000:00:1c.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.304467] pci 0000:00:1c.3: PCI bridge to [bus 02-02]
[    0.304472] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.304479] pci 0000:00:1c.3:   bridge window [mem 0xdde00000-0xddefffff]
[    0.304484] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    0.304491] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.304495] pci 0000:00:1e.0:   bridge window [io  0xb000-0xbfff]
[    0.304502] pci 0000:00:1e.0:   bridge window [mem 0xddd00000-0xdddfffff]
[    0.304507] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.304529] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.304534] pci 0000:00:01.0: setting latency timer to 64
[    0.304543] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.304548] pci 0000:00:1c.0: setting latency timer to 64
[    0.304560] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.304566] pci 0000:00:1c.3: setting latency timer to 64
[    0.304574] pci 0000:00:1e.0: setting latency timer to 64
[    0.304579] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.304583] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.304586] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.304589] pci_bus 0000:04: resource 1 [mem 0xddf00000-0xdfffffff]
[    0.304592] pci_bus 0000:04: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.304596] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.304599] pci_bus 0000:03: resource 1 [mem 0x40000000-0x401fffff]
[    0.304602] pci_bus 0000:03: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.304606] pci_bus 0000:02: resource 0 [io  0xc000-0xcfff]
[    0.304610] pci_bus 0000:02: resource 1 [mem 0xdde00000-0xddefffff]
[    0.304615] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    0.304618] pci_bus 0000:01: resource 1 [mem 0xddd00000-0xdddfffff]
[    0.304622] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.304625] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
[    0.304669] NET: Registered protocol family 2
[    0.304764] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.305100] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.305711] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.305982] TCP: Hash tables configured (established 131072 bind 65536)
[    0.305985] TCP reno registered
[    0.305990] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.306000] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.306093] NET: Registered protocol family 1
[    0.306237] pci 0000:04:00.0: Boot video device
[    0.306249] PCI: CLS 16 bytes, default 64
[    0.306517] cpufreq-nforce2: No nForce2 chipset.
[    0.306691] audit: initializing netlink socket (disabled)
[    0.306705] type=2000 audit(1311018755.300:1): initialized
[    0.316445] highmem bounce pool size: 64 pages
[    0.316453] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.318879] VFS: Disk quotas dquot_6.5.2
[    0.318967] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.319903] fuse init (API version 7.16)
[    0.320051] msgmni has been set to 1704
[    0.320368] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.320405] io scheduler noop registered
[    0.320408] io scheduler deadline registered
[    0.320429] io scheduler cfq registered (default)
[    0.320579] pcieport 0000:00:01.0: setting latency timer to 64
[    0.320624] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.320690] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.320736] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.320813] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.320859] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.320974] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.321008] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.321225] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.321234] ACPI: Power Button [PWRB]
[    0.321306] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.321311] ACPI: Power Button [PWRF]
[    0.321533] ACPI: acpi_idle registered with cpuidle
[    0.324198] ERST: Table is not found!
[    0.324315] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.344728] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.344877] isapnp: Scanning for PnP cards...
[    0.539580] Freeing initrd memory: 12556k freed
[    0.698014] isapnp: No Plug & Play device found
[    0.836651] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.836962] Linux agpgart interface v0.103
[    0.838920] brd: module loaded
[    0.839729] loop: module loaded
[    0.839854] i2c-core: driver [adp5520] using legacy suspend method
[    0.839857] i2c-core: driver [adp5520] using legacy resume method
[    0.839993] ata_piix 0000:00:1f.1: version 2.13
[    0.840036] ata_piix 0000:00:1f.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.840090] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.840583] scsi0 : ata_piix
[    0.840704] scsi1 : ata_piix
[    0.842477] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.842481] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.842540] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.842550] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.842607] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.843048] scsi2 : ata_piix
[    0.843143] scsi3 : ata_piix
[    0.843210] ata3: SATA max UDMA/133 cmd 0xa800 ctl 0xa400 bmdma 0x9400 irq 23
[    0.843214] ata4: SATA max UDMA/133 cmd 0xa000 ctl 0x9800 bmdma 0x9408 irq 23
[    0.843806] Fixed MDIO Bus: probed
[    0.843862] PPP generic driver version 2.4.2
[    0.843925] tun: Universal TUN/TAP device driver, 1.6
[    0.843928] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.844068] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.844095] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.844114] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.844118] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.844173] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.844223] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.844236] ehci_hcd 0000:00:1d.7: debug port 1
[    0.848110] ehci_hcd 0000:00:1d.7: cache line size of 16 is not supported
[    0.848128] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xddcffc00
[    0.864018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.864196] hub 1-0:1.0: USB hub found
[    0.864203] hub 1-0:1.0: 8 ports detected
[    0.864312] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.864332] uhci_hcd: USB Universal Host Controller Interface driver
[    0.864362] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.864369] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.864373] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.864425] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.864471] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00008000
[    0.864640] hub 2-0:1.0: USB hub found
[    0.864647] hub 2-0:1.0: 2 ports detected
[    0.864738] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.864745] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.864749] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.864799] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.868055] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00008400
[    0.868217] hub 3-0:1.0: USB hub found
[    0.868223] hub 3-0:1.0: 2 ports detected
[    0.868316] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.868323] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.868327] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.868377] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.868429] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008800
[    0.868596] hub 4-0:1.0: USB hub found
[    0.868602] hub 4-0:1.0: 2 ports detected
[    0.868689] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.868696] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.868700] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.868752] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.872052] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00009000
[    0.872221] hub 5-0:1.0: USB hub found
[    0.872226] hub 5-0:1.0: 2 ports detected
[    0.872401] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.875235] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.875243] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.875423] mousedev: PS/2 mouse device common for all mice
[    0.875604] rtc_cmos 00:03: RTC can wake from S4
[    0.876075] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.876102] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.876211] device-mapper: uevent: version 1.0.3
[    0.876319] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    0.876409] device-mapper: multipath: version 1.2.0 loaded
[    0.876413] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.876512] EISA: Probing bus 0 at eisa.0
[    0.876539] Cannot allocate resource for EISA slot 8
[    0.876541] EISA: Detected 0 cards.
[    0.876615] cpuidle: using governor ladder
[    0.876618] cpuidle: using governor menu
[    0.877004] TCP cubic registered
[    0.877177] NET: Registered protocol family 10
[    0.878015] NET: Registered protocol family 17
[    0.878035] Registering the dns_resolver key type
[    0.878085] Using IPI No-Shortcut mode
[    0.878210] PM: Hibernation image not present or could not be loaded.
[    0.878225] registered taskstats version 1
[    0.878483]   Magic number: 3:713:900
[    0.878526] acpi PNP0501:00: hash matches
[    0.878566] rtc_cmos 00:03: setting system clock to 2011-07-18 19:52:36 UTC (1311018756)
[    0.878569] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.878571] EDD information not available.
[    1.007428] ata1.00: ATAPI: PHILIPS SPD2412T, P1.3, max UDMA/33
[    1.018011] ata3.00: ATA-7: SAMSUNG HD080HJ, ZH100-33, max UDMA7
[    1.018016] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.024252] ata1.00: configured for UDMA/33
[    1.024363] ata3.00: configured for UDMA/133
[    1.025691] scsi 0:0:0:0: CD-ROM            PHILIPS  SPD2412T         P1.3 PQ: 0 ANSI: 5
[    1.030786] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.030790] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.030934] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.031018] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.031189] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD080HJ  ZH10 PQ: 0 ANSI: 5
[    1.031381] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.031474] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.031553] sd 2:0:0:0: [sda] Write Protect is off
[    1.031557] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.031591] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.058629]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.059090] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.059144] Freeing unused kernel memory: 700k freed
[    1.059583] Write protecting the kernel text: 5192k
[    1.059643] Write protecting the kernel read-only data: 2148k
[    1.087402] <30>udev[71]: starting version 167
[    1.210033] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.210062] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.210112] r8169 0000:02:00.0: setting latency timer to 64
[    1.210195] r8169 0000:02:00.0: irq 43 for MSI/MSI-X
[    1.210936] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xf8010000, 00:17:31:a3:53:e9, XID 10000000 IRQ 43
[    1.214025] Floppy drive(s): fd0 is 1.44M
[    1.222650] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.222682] 8139cp 0000:01:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.226038] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.226080] 8139too 0000:01:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    1.231838] FDC 0 is a post-1991 82077
[    1.231897] 8139too 0000:01:01.0: eth1: RealTek RTL8139 at 0xb800, 00:e0:4c:13:39:ba, IRQ 21
[    1.304018] Refined TSC clocksource calibration: 3412.073 MHz.
[    1.304026] Switching to clocksource tsc
[    1.456023] usb 1-4: new high speed USB device using ehci_hcd and address 5
[    1.575130] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    1.792019] usb 1-7: new high speed USB device using ehci_hcd and address 6
[    2.048020] usb 1-8: new high speed USB device using ehci_hcd and address 7
[    2.420020] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.591559] hub 2-1:1.0: USB hub found
[    2.592540] hub 2-1:1.0: 4 ports detected
[    2.836147] usb 2-2: new low speed USB device using uhci_hcd and address 3
[    3.260022] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    3.521540] usb 2-1.1: new full speed USB device using uhci_hcd and address 4
[    3.623566] usb 2-1.1: not running at top speed; connect to a high speed hub
[    3.725540] usb 2-1.2: new low speed USB device using uhci_hcd and address 5
[    4.420190] <30>udev[283]: starting version 167
[    4.462466] Adding 975868k swap on /dev/sda5.  Priority:-1 extents:1 across:975868k 
[    6.352006] intel_rng: FWH not detected
[    6.586138] Linux video capture interface: v2.00
[    6.811431] lp: driver loaded but no devices found
[    6.821539] leds_ss4200: no LED devices found
[    6.831927] parport_pc 00:07: reported by Plug and Play ACPI
[    6.832091] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    6.867835] ppdev: user-space parallel port driver
[    6.928975] lp0: using parport0 (interrupt-driven).
[    6.942943] usbcore: registered new interface driver uas
[    7.013403] uvcvideo: Found UVC 1.00 device Microsoft® LifeCam VX-2000 (045e:0761)
[    7.015119] input: Microsoft® LifeCam VX-2000 as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input2
[    7.015657] usbcore: registered new interface driver uvcvideo
[    7.015660] USB Video Class driver (v1.0.0)
[    7.230536] Initializing USB Mass Storage driver...
[    7.230743] scsi4 : usb-storage 1-7:1.0
[    7.231085] scsi5 : usb-storage 1-8:1.0
[    7.231423] scsi6 : usb-storage 3-1:1.2
[    7.232250] usbcore: registered new interface driver usb-storage
[    7.232254] USB Mass Storage support registered.
[    7.241788] usbcore: registered new interface driver snd-usb-audio
[    7.251622] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    7.251686] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[    7.251718] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.272788] scsi7 : usb-storage 2-1.1:1.0
[    7.273415] usbcore: registered new interface driver ums-cypress
[    7.291559] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0201
[    7.291940] usbcore: registered new interface driver usblp
[    7.521297] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input3
[    7.521694] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2/input0
[    7.536334] input: Microsoft Microsoft® Digital Media Keyboard     as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4
[    7.536607] generic-usb 0003:045E:00B4.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft® Digital Media Keyboard    ] on usb-0000:00:1d.0-1.2/input0
[    7.567865] input: Microsoft Microsoft® Digital Media Keyboard     as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input5
[    7.568135] generic-usb 0003:045E:00B4.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Digital Media Keyboard    ] on usb-0000:00:1d.0-1.2/input1
[    7.568986] usbcore: registered new interface driver usbhid
[    7.568991] usbhid: USB HID core driver
[    7.896992] nvidia: module license 'NVIDIA' taints kernel.
[    7.896997] Disabling lock debugging due to kernel taint
[    8.136669] type=1400 audit(1311018763.753:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=440 comm="apparmor_parser"
[    8.137515] type=1400 audit(1311018763.753:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=440 comm="apparmor_parser"
[    8.138048] type=1400 audit(1311018763.753:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=440 comm="apparmor_parser"
[    8.138935] type=1400 audit(1311018763.753:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=410 comm="apparmor_parser"
[    8.139770] type=1400 audit(1311018763.753:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=410 comm="apparmor_parser"
[    8.140311] type=1400 audit(1311018763.757:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[    8.141183] type=1400 audit(1311018763.757:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=541 comm="apparmor_parser"
[    8.142015] type=1400 audit(1311018763.757:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=541 comm="apparmor_parser"
[    8.142545] type=1400 audit(1311018763.757:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=541 comm="apparmor_parser"
[    8.240038] scsi 5:0:0:0: Direct-Access     Generic  IC1210        CF 1.9C PQ: 0 ANSI: 0 CCS
[    8.241206] scsi 5:0:0:1: Direct-Access     Generic  IC1210        MS 1.9C PQ: 0 ANSI: 0 CCS
[    8.242333] scsi 5:0:0:2: Direct-Access     Generic  IC1210    MMC/SD 1.9C PQ: 0 ANSI: 0 CCS
[    8.244255] scsi 5:0:0:3: Direct-Access     Generic  IC1210        SM 1.9C PQ: 0 ANSI: 0 CCS
[    8.244898] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    8.245123] sd 5:0:0:1: Attached scsi generic sg3 type 0
[    8.245332] sd 5:0:0:2: Attached scsi generic sg4 type 0
[    8.245543] sd 5:0:0:3: Attached scsi generic sg5 type 0
[    8.266449] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    8.269696] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[    8.272445] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[    8.278271] type=1400 audit(1311018763.893:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=686 comm="apparmor_parser"
[    8.285239] sd 5:0:0:3: [sde] Attached SCSI removable disk
[    8.338566] scsi 7:0:0:0: Direct-Access     ST332062 0A               0000 PQ: 0 ANSI: 0
[    8.456875] nvidia 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.456888] nvidia 0000:04:00.0: setting latency timer to 64
[    8.456896] vgaarb: device changed decodes: PCI:0000:04:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.461309] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.30  Thu Apr 14 08:47:14 PDT 2011
[    8.463793] scsi 4:0:0:0: CD-ROM            Vodafone  USB SCSI CD-ROM  USB PQ: 0 ANSI: 2
[    8.468126] scsi 6:0:0:0: Direct-Access     Brother  DCP-385C         1.00 PQ: 0 ANSI: 2
[    8.468818] sd 6:0:0:0: Attached scsi generic sg6 type 0
[    8.469296] sd 7:0:0:0: Attached scsi generic sg7 type 0
[    8.474556] sd 7:0:0:0: [sdg] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    8.478186] sr1: scsi-1 drive
[    8.478575] sr 4:0:0:0: Attached scsi CD-ROM sr1
[    8.479092] sr 4:0:0:0: Attached scsi generic sg8 type 5
[    8.479537] sd 7:0:0:0: [sdg] Write Protect is off
[    8.479542] sd 7:0:0:0: [sdg] Mode Sense: 27 00 00 00
[    8.479546] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    8.489542] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    8.502605]  sdg: sdg1
[    8.512552] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    8.512560] sd 7:0:0:0: [sdg] Attached SCSI disk
[    8.547124] sd 6:0:0:0: [sdf] Attached SCSI removable disk
[    8.913214] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    9.099107] vesafb: framebuffer at 0xe0000000, mapped to 0xf8100000, using 5120k, total 5120k
[    9.099112] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    9.099114] vesafb: scrolling: redraw
[    9.099118] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    9.099324] Console: switching to colour frame buffer device 160x64
[    9.099356] fb0: VESA VGA frame buffer device
[    9.108143] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    9.637694] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.077857] r8169 0000:02:00.0: eth0: link down
[   13.078253] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.082060] eth1: link down
[   13.082264] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   14.764575] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   18.041337] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   18.244280] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   18.348982] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   22.801822] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   22.805332] EXT4-fs (sda7): re-mounted. Opts: commit=0
[   23.396911] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   45.483839] EXT4-fs (sdg1): warning: maximal mount count reached, running e2fsck is recommended
[   45.524918] EXT4-fs (sdg1): mounted filesystem with ordered data mode. Opts: (null)
[  150.070743] usb 1-7: USB disconnect, address 6
[  182.764017] usb 1-7: new high speed USB device using ehci_hcd and address 8
[  182.911592] scsi8 : usb-storage 1-7:1.0
[  185.561249] usb 1-7: USB disconnect, address 8
[  190.812017] usb 1-7: new high speed USB device using ehci_hcd and address 9
[  191.033141] usbcore: registered new interface driver usbserial
[  191.033168] USB Serial support registered for generic
[  191.033341] usbcore: registered new interface driver usbserial_generic
[  191.033344] usbserial: USB Serial Driver core
[  191.050022] USB Serial support registered for GSM modem (1-port)
[  191.050569] option 1-7:1.0: GSM modem (1-port) converter detected
[  191.050778] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB0
[  191.050807] option 1-7:1.1: GSM modem (1-port) converter detected
[  191.050968] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB1
[  191.050994] option 1-7:1.2: GSM modem (1-port) converter detected
[  191.051144] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB2
[  191.051171] option 1-7:1.3: GSM modem (1-port) converter detected
[  191.051360] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB3
[  191.051387] option 1-7:1.4: GSM modem (1-port) converter detected
[  191.051578] usb 1-7: GSM modem (1-port) converter now attached to ttyUSB4
[  191.051967] usbcore: registered new interface driver option
[  191.051970] option: v0.7.2:USB Driver for GSM modems
[  235.728687] PPP BSD Compression module registered
[  235.750883] PPP Deflate Compression module registered
[ 4743.338678] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4743.338685] sr 0:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 4743.338691] sr 0:0:0:0: [sr0]  Add. Sense: Read of scrambled sector without authentication
[ 4743.338700] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[ 4743.338712] end_request: I/O error, dev sr0, sector 4096
[ 4743.338717] quiet_error: 45 callbacks suppressed
[ 4743.338720] Buffer I/O error on device sr0, logical block 512
[ 4743.360441] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4743.360446] sr 0:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 4743.360451] sr 0:0:0:0: [sr0]  Add. Sense: Read of scrambled sector without authentication
[ 4743.360457] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[ 4743.360469] end_request: I/O error, dev sr0, sector 4096
[ 4743.360472] Buffer I/O error on device sr0, logical block 512
[ 4743.663399] cdrom: sr0: mrw address space DMA selected
[ 4743.785932] UDF-fs: Partition marked readonly; forcing readonly mount
[ 4743.819605] UDF-fs INFO UDF: Mounting volume 'THE_SOUND_OF_MUSIC', timestamp 2001/02/27 07:15 (12d0)
[ 5176.864392] usb 2-1.1: USB disconnect, address 4
[ 5187.433176] usb 2-1.1: new full speed USB device using uhci_hcd and address 6
[ 5187.535148] usb 2-1.1: not running at top speed; connect to a high speed hub
[ 5187.559386] scsi9 : usb-storage 2-1.1:1.0
[ 5193.097057] scsi 9:0:0:0: Direct-Access     ST332062 0A               0000 PQ: 0 ANSI: 0
[ 5193.097967] sd 9:0:0:0: Attached scsi generic sg7 type 0
[ 5193.102046] sd 9:0:0:0: [sdg] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[ 5193.107043] sd 9:0:0:0: [sdg] Write Protect is off
[ 5193.107048] sd 9:0:0:0: [sdg] Mode Sense: 27 00 00 00
[ 5193.107052] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 5193.117059] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 5193.131116]  sdg: sdg1
[ 5193.141067] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 5193.141075] sd 9:0:0:0: [sdg] Attached SCSI disk
[ 5193.871357] EXT4-fs (sdg1): warning: maximal mount count reached, running e2fsck is recommended
[ 5193.909985] EXT4-fs (sdg1): recovery complete
[ 5193.909992] EXT4-fs (sdg1): mounted filesystem with ordered data mode. Opts: (null)
[ 9327.076293] end_request: I/O error, dev fd0, sector 0
[11837.136031] usb 1-8: reset high speed USB device using ehci_hcd and address 7
[13431.528118] usb 2-1.1: USB disconnect, address 6
[13438.896938] usb 2-1.1: new full speed USB device using uhci_hcd and address 7
[13438.998908] usb 2-1.1: not running at top speed; connect to a high speed hub
[13439.025115] scsi10 : usb-storage 2-1.1:1.0
[13440.029910] scsi 10:0:0:0: Direct-Access     ST332062 0A               0000 PQ: 0 ANSI: 0
[13440.032682] sd 10:0:0:0: Attached scsi generic sg7 type 0
[13440.036898] sd 10:0:0:0: [sdg] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[13440.041898] sd 10:0:0:0: [sdg] Write Protect is off
[13440.041904] sd 10:0:0:0: [sdg] Mode Sense: 27 00 00 00
[13440.041907] sd 10:0:0:0: [sdg] Assuming drive cache: write through
[13440.051893] sd 10:0:0:0: [sdg] Assuming drive cache: write through
[13440.079966]  sdg: sdg1
[13440.089892] sd 10:0:0:0: [sdg] Assuming drive cache: write through
[13440.089897] sd 10:0:0:0: [sdg] Attached SCSI disk
[13440.979211] EXT4-fs (sdg1): warning: maximal mount count reached, running e2fsck is recommended
[13441.018953] EXT4-fs (sdg1): recovery complete
[13441.018959] EXT4-fs (sdg1): mounted filesystem with ordered data mode. Opts: (null)
[13591.779782] usb 2-1.1: USB disconnect, address 7
[13625.257906] usb 2-1.1: new full speed USB device using uhci_hcd and address 8
[13625.359875] usb 2-1.1: not running at top speed; connect to a high speed hub
[13625.385113] scsi11 : usb-storage 2-1.1:1.0
[13631.793773] scsi 11:0:0:0: Direct-Access     ST332062 0A               0000 PQ: 0 ANSI: 0
[13631.794453] sd 11:0:0:0: Attached scsi generic sg7 type 0
[13631.799729] sd 11:0:0:0: [sdg] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[13631.804720] sd 11:0:0:0: [sdg] Write Protect is off
[13631.804725] sd 11:0:0:0: [sdg] Mode Sense: 27 00 00 00
[13631.804729] sd 11:0:0:0: [sdg] Assuming drive cache: write through
[13631.814714] sd 11:0:0:0: [sdg] Assuming drive cache: write through
[13631.836819]  sdg: sdg1
[13631.846724] sd 11:0:0:0: [sdg] Assuming drive cache: write through
[13631.846731] sd 11:0:0:0: [sdg] Attached SCSI disk
[13632.611034] EXT4-fs (sdg1): warning: maximal mount count reached, running e2fsck is recommended
[13632.650249] EXT4-fs (sdg1): recovery complete
[13632.650256] EXT4-fs (sdg1): mounted filesystem with ordered data mode. Opts: (null)
mal@Pentium4:~$

---

### Post by malel on 2011-07-18
and this is the result of 'fdisk -l'

mal@Pentium4:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011a1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          98      780288   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              98        9730    77368321    5  Extended
/dev/sda5              98         219      975872   82  Linux swap / Solaris
/dev/sda6             220        3867    29295616   83  Linux
/dev/sda7            3867        9730    47094784   83  Linux

Disk /dev/sdg: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000143f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       38913   312568641   83  Linux
mal@Pentium4:~$

---

### Post by bhinderm on 2011-07-18
Looks like it is getting detected (and mounted). Could you open Nautlius and confirm that it doesn't show up on the left pane? If it does then clicking on it should mount it on your desktop.

Next, if "mount|grep -i sdg1" doesn't show it as mounted anywhere, then you can run the following manually:

sudo mkdir /temp
sudo mount /dev/sdg1 /temp


This will mount it on /temp

---

### Post by malel on 2011-07-18
Thank you for your help . I have managed to get it on the desktop now but when I click to open it opens but says 'I do not have permissions necessary to view the contents of M2' I made a '/temp' dir in sudo, does that mean i should open it in 'sudo'

---

### Post by wildmanne39 on 2011-07-18
> **malel said:**
> Thank you for your help . I have managed to get it on the desktop now but when I click to open it opens but says 'I do not have permissions necessary to view the contents of M2' I made a '/temp' dir in sudo, does that mean i should open it in 'sudo'Hi, what you need to do is to get ownership.
```
sudo chown -R username:username /media/_media_storage
```
the last part will be your file name it will be /media/yourfilename.

If you hover your mouse over the drive in file manager it will show /media/something and that is what you put on the end of yours.

---

### Post by malel on 2011-07-18
Thanks for help . Using your suggestion this what I got 

mal@Pentium4:~$ sudo chown -R mal:mal /media/M2
[sudo] password for mal: 
chown: changing ownership of `/media/M2': Input/output error
mal@Pentium4:~$

---

### Post by wildmanne39 on 2011-07-18
> **malel said:**
> Thanks for help . Using your suggestion this what I got 

mal@Pentium4:~$ sudo chown -R mal:mal /media/M2
[sudo] password for mal: 
chown: changing ownership of `/media/M2': Input/output error
mal@Pentium4:~$Hi, what format is the partition in? like ntfs or ext4.

---

### Post by malel on 2011-07-18
it says ext3/ext4

---

### Post by wildmanne39 on 2011-07-19
> **malel said:**
> it says ext3/ext4Hi, thats the right format that command should have worked usually if you see an input/output error it is a disk problem. Try to run a disk check on it by opening disk utility and click smart data to see information about your disk.

---

### Post by malel on 2011-07-19
Than you very much for your help. What I have done is  re format the drive after opening it with Gparted and then carried out 'chmod' and it is working as it should now. I had previously formatted it in Fedora but I have no idea why it wouldn't work in Ubuntu until I did a reformat. All's well now . Thanks again

---

### Post by wildmanne39 on 2011-07-19
> **malel said:**
> Than you very much for your help. What I have done is  re format the drive after opening it with Gparted and then carried out 'chmod' and it is working as it should now. I had previously formatted it in Fedora but I have no idea why it wouldn't work in Ubuntu until I did a reformat. All's well now . Thanks againHi, your welcome! would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

