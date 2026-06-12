---
title: "Splash to Terminal Login to GUI Login"
date: 2011-01-10
forum: General Help
---

### Post by PresidentWolf on 2011-01-10
Hi Everyone,

I have been visiting these forums for a while now and want to first thank everyone for the great advice and fixes. 

I recently did a fresh install of Ubuntu 10.10 64-bit. After installing the ATI drivers, I had to tweak GRUB to get the nice splash screen back during boot. Then, I installed drivers for my TV Tuner (Hauppauge 2250). The card works fine. However, my boot now goes splash screen to a terminal login for around 10 sec where system messages also show up to the GUI Login screen. I was wondering if there was anyway to return to a normal boot. 

Thanks for any help you can provide! Let me know if any additional information is neeeded.

Wolf

---

### Post by PresidentWolf on 2011-01-11
Bump.

I thought I would clarify about the system messages. I see messages about the downloading of firmware for my TV tuner card. Its not an error message. 

Thanks
Wolf

---

### Post by PresidentWolf on 2011-01-12
Bump...

Is there a way to make the splash screen last longer?

PresidentWolf

---

### Post by PresidentWolf on 2011-01-13
I thought it had something to do with the tweaks I made to the splash screen because I was using a resolution not supported by my graphics card. I have fixed that, but the problem still persists. 

Below is my dmesg output:

[    1.832666] pci_bus 0000:07: resource 2 [mem 0xc0400000-0xc05fffff 64bit pref]
[    1.832668] pci_bus 0000:06: resource 0 [io  0x3000-0x3fff]
[    1.832669] pci_bus 0000:06: resource 1 [mem 0xfb400000-0xfbbfffff]
[    1.832671] pci_bus 0000:06: resource 2 [mem 0xc0600000-0xc07fffff 64bit pref]
[    1.832672] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
[    1.832674] pci_bus 0000:05: resource 1 [mem 0xfb300000-0xfb3fffff]
[    1.832676] pci_bus 0000:05: resource 2 [mem 0xc0800000-0xc09fffff 64bit pref]
[    1.832677] pci_bus 0000:09: resource 0 [io  0xe000-0xefff]
[    1.832679] pci_bus 0000:09: resource 1 [mem 0xfbe00000-0xfbefffff]
[    1.832680] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
[    1.832682] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
[    1.832683] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
[    1.832685] pci_bus 0000:09: resource 7 [mem 0x000d0000-0x000dffff]
[    1.832686] pci_bus 0000:09: resource 8 [mem 0xc0000000-0xdfffffff]
[    1.832688] pci_bus 0000:09: resource 9 [mem 0xf0000000-0xfed8ffff]
[    1.832710] NET: Registered protocol family 2
[    1.832899] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.833827] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.835057] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.835188] TCP: Hash tables configured (established 524288 bind 65536)
[    1.835190] TCP reno registered
[    1.835202] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.835235] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.835338] NET: Registered protocol family 1
[    1.835522] pci 0000:03:00.0: Boot video device
[    1.835535] PCI: CLS 256 bytes, default 64
[    1.835537] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.835539] Placing 64MB software IO TLB between ffff880001ffe000 - ffff880005ffe000
[    1.835541] software IO TLB at phys 0x1ffe000 - 0x5ffe000
[    1.835907] Scanning for low memory corruption every 60 seconds
[    1.835995] audit: initializing netlink socket (disabled)
[    1.836001] type=2000 audit(1294950937.580:1): initialized
[    1.848116] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.849235] VFS: Disk quotas dquot_6.5.2
[    1.849283] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.849714] fuse init (API version 7.14)
[    1.849777] msgmni has been set to 11910
[    1.850099] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.850102] io scheduler noop registered
[    1.850103] io scheduler deadline registered
[    1.850131] io scheduler cfq registered (default)
[    1.850215] pcieport 0000:00:01.0: setting latency timer to 64
[    1.850241]   alloc irq_desc for 64 on node -1
[    1.850242]   alloc kstat_irqs on node -1
[    1.850253] pcieport 0000:00:01.0: irq 64 for MSI/MSI-X
[    1.850307] pcieport 0000:00:02.0: setting latency timer to 64
[    1.850330]   alloc irq_desc for 65 on node -1
[    1.850331]   alloc kstat_irqs on node -1
[    1.850336] pcieport 0000:00:02.0: irq 65 for MSI/MSI-X
[    1.850385] pcieport 0000:00:03.0: setting latency timer to 64
[    1.850408]   alloc irq_desc for 66 on node -1
[    1.850409]   alloc kstat_irqs on node -1
[    1.850414] pcieport 0000:00:03.0: irq 66 for MSI/MSI-X
[    1.850463] pcieport 0000:00:07.0: setting latency timer to 64
[    1.850486]   alloc irq_desc for 67 on node -1
[    1.850487]   alloc kstat_irqs on node -1
[    1.850492] pcieport 0000:00:07.0: irq 67 for MSI/MSI-X
[    1.850545] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.850572]   alloc irq_desc for 68 on node -1
[    1.850573]   alloc kstat_irqs on node -1
[    1.850578] pcieport 0000:00:1c.0: irq 68 for MSI/MSI-X
[    1.850639] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.850666]   alloc irq_desc for 69 on node -1
[    1.850667]   alloc kstat_irqs on node -1
[    1.850672] pcieport 0000:00:1c.2: irq 69 for MSI/MSI-X
[    1.850731] pcieport 0000:00:1c.4: setting latency timer to 64
[    1.850758]   alloc irq_desc for 70 on node -1
[    1.850759]   alloc kstat_irqs on node -1
[    1.850764] pcieport 0000:00:1c.4: irq 70 for MSI/MSI-X
[    1.850826] pcieport 0000:00:1c.5: setting latency timer to 64
[    1.850853]   alloc irq_desc for 71 on node -1
[    1.850854]   alloc kstat_irqs on node -1
[    1.850859] pcieport 0000:00:1c.5: irq 71 for MSI/MSI-X
[    1.850926] aer 0000:00:01.0:pcie02: AER service couldn't init device: no _OSC support
[    1.850931] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
[    1.850935] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    1.850938] aer 0000:00:07.0:pcie02: AER service couldn't init device: no _OSC support
[    1.850951] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.851036] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.851088] intel_idle: MWAIT substates: 0x1120
[    1.851090] intel_idle: v0.4 model 0x1A
[    1.851091] intel_idle: lapic_timer_reliable_states 0x2
[    1.851183] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.851186] ACPI: Power Button [PWRB]
[    1.851217] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.851219] ACPI: Power Button [PWRF]
[    1.851503] ACPI: acpi_idle yielding to intel_idle
[    1.853739] ERST: Table is not found!
[    1.853886] Linux agpgart interface v0.103
[    1.853903] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.854832] brd: module loaded
[    1.855174] loop: module loaded
[    1.855282] ata_piix 0000:00:1f.2: version 2.13
[    1.855294]   alloc irq_desc for 20 on node -1
[    1.855295]   alloc kstat_irqs on node -1
[    1.855299] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.855303] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.855330] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.855375] scsi0 : ata_piix
[    1.855429] scsi1 : ata_piix
[    1.856599] ata1: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7480 irq 20
[    1.856604] ata2: SATA max UDMA/133 cmd 0x7880 ctl 0x7800 bmdma 0x7488 irq 20
[    1.856622] ata_piix 0000:00:1f.5: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.856627] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.856658] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.856688] scsi2 : ata_piix
[    1.856727] scsi3 : ata_piix
[    1.857629] ata3: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 20
[    1.857632] ata4: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 20
[    1.857844] Fixed MDIO Bus: probed
[    1.857863] PPP generic driver version 2.4.2
[    1.857887] tun: Universal TUN/TAP device driver, 1.6
[    1.857888] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.857936] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.857950] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.857964] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.857967] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.857996] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.858017] ehci_hcd 0000:00:1a.7: debug port 1
[    1.861910] ehci_hcd 0000:00:1a.7: cache line size of 256 is not supported
[    1.861922] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfafff000
[    1.864862] Freeing initrd memory: 16376k freed
[    1.879786] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.879927] hub 1-0:1.0: USB hub found
[    1.879930] hub 1-0:1.0: 6 ports detected
[    1.879998]   alloc irq_desc for 23 on node -1
[    1.879999]   alloc kstat_irqs on node -1
[    1.880005] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.880025] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.880028] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.880053] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.880074] ehci_hcd 0000:00:1d.7: debug port 1
[    1.883966] ehci_hcd 0000:00:1d.7: cache line size of 256 is not supported
[    1.883980] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfaffe000
[    1.899778] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.899886] hub 2-0:1.0: USB hub found
[    1.899889] hub 2-0:1.0: 6 ports detected
[    1.899942] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.899952] uhci_hcd: USB Universal Host Controller Interface driver
[    1.900003] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.900008] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.900010] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.900034] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.900062] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00009800
[    1.900136] hub 3-0:1.0: USB hub found
[    1.900139] hub 3-0:1.0: 2 ports detected
[    1.900182]   alloc irq_desc for 21 on node -1
[    1.900183]   alloc kstat_irqs on node -1
[    1.900187] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.900191] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.900194] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.900215] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.900242] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00009880
[    1.900318] hub 4-0:1.0: USB hub found
[    1.900320] hub 4-0:1.0: 2 ports detected
[    1.900362]   alloc irq_desc for 19 on node -1
[    1.900363]   alloc kstat_irqs on node -1
[    1.900367] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.900371] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.900373] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.900397] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.900424] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00009c00
[    1.900502] hub 5-0:1.0: USB hub found
[    1.900505] hub 5-0:1.0: 2 ports detected
[    1.900547] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.900552] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.900554] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.900576] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.900596] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009080
[    1.900671] hub 6-0:1.0: USB hub found
[    1.900676] hub 6-0:1.0: 2 ports detected
[    1.900722] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.900726] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.900728] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.900750] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.900771] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009400
[    1.900845] hub 7-0:1.0: USB hub found
[    1.900848] hub 7-0:1.0: 2 ports detected
[    1.900890] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.900895] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.900897] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.900918] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.900939] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009480
[    1.901013] hub 8-0:1.0: USB hub found
[    1.901015] hub 8-0:1.0: 2 ports detected
[    1.901097] PNP: No PS/2 controller found. Probing ports directly.
[    1.903640] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.903645] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.903696] mice: PS/2 mouse device common for all mice
[    1.903766] rtc_cmos 00:03: RTC can wake from S4
[    1.903791] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.903814] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.903883] device-mapper: uevent: version 1.0.3
[    1.903959] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.904073] device-mapper: multipath: version 1.1.1 loaded
[    1.904077] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.904452] cpuidle: using governor ladder
[    1.904674] cpuidle: using governor menu
[    1.904881] TCP cubic registered
[    1.904968] NET: Registered protocol family 10
[    1.905252] lo: Disabled Privacy Extensions
[    1.905394] NET: Registered protocol family 17
[    1.908211] PM: Resume from disk failed.
[    1.908219] registered taskstats version 1
[    1.908610]   Magic number: 11:97:599
[    1.908624] serial8250 serial8250: hash matches
[    1.908780] rtc_cmos 00:03: setting system clock to 2011-01-13 20:35:38 UTC (1294950938)
[    1.908784] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.908787] EDD information not available.
[    2.198564] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.209543] ata3: SATA link down (SStatus 0 SControl 300)
[    2.220413] ata4: SATA link down (SStatus 0 SControl 300)
[    2.588408] usb 2-5: new high speed USB device using ehci_hcd and address 2
[    2.708476] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.708496] ata2.00: SATA link down (SStatus 0 SControl 300)
[    2.708499] ata1.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.708518] ata2.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.748762] ata1.00: ATA-8: ST31500541AS, CC34, max UDMA/133
[    2.748767] ata1.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.748794] ata1.01: ATAPI: ATAPI   iHAS124   Y, BL0V, max UDMA/100
[    2.766040] ata2.01: ATA-8: ST31500341AS, CC1H, max UDMA/133
[    2.766044] ata2.01: 2930277168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.788846] ata1.00: configured for UDMA/133
[    2.828505] ata1.01: configured for UDMA/100
[    2.829287] scsi 0:0:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    2.829433] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.829482] sd 0:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.830895] scsi 0:0:1:0: CD-ROM            ATAPI    iHAS124   Y      BL0V PQ: 0 ANSI: 5
[    2.832393] sd 0:0:0:0: [sda] Write Protect is off
[    2.832397] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.835251] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.835945] ata2.01: configured for UDMA/133
[    2.836099] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.836103] Uniform CD-ROM driver Revision: 3.20
[    2.836203] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.836257] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.836265]  sda:
[    2.836465] scsi 1:0:1:0: Direct-Access     ATA      ST31500341AS     CC1H PQ: 0 ANSI: 5
[    2.836610] sd 1:0:1:0: Attached scsi generic sg2 type 0
[    2.836662] sd 1:0:1:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.836787] sd 1:0:1:0: [sdb] Write Protect is off
[    2.836791] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.836845] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.837063]  sdb: sdb1
[    2.842242] sd 1:0:1:0: [sdb] Attached SCSI disk
[    2.860264]  sda1 sda2
[    2.860745] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.860760] Freeing unused kernel memory: 908k freed
[    2.860897] Write protecting the kernel read-only data: 10240k
[    2.861924] Freeing unused kernel memory: 412k freed
[    2.862458] Freeing unused kernel memory: 1644k freed
[    2.881271] udev[156]: starting version 163
[    2.903116] ahci 0000:01:00.0: version 3.0
[    2.903134]   alloc irq_desc for 28 on node -1
[    2.903136]   alloc kstat_irqs on node -1
[    2.903145] ahci 0000:01:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    2.903198]   alloc irq_desc for 72 on node -1
[    2.903200]   alloc kstat_irqs on node -1
[    2.903208] ahci 0000:01:00.0: irq 72 for MSI/MSI-X
[    2.903250] ahci 0000:01:00.0: AHCI 0001.0000 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    2.903255] ahci 0000:01:00.0: flags: 64bit ncq sntf led only pmp fbs pio slum part sxs 
[    2.903260] ahci 0000:01:00.0: setting latency timer to 64
[    2.903265] ahci 0000:01:00.0: The port is not capable of FBS
[    2.903303] ahci 0000:01:00.0: The port is not capable of FBS
[    2.907117] sky2: driver version 1.28
[    2.907151] sky2 0000:07:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.907162] sky2 0000:07:00.0: setting latency timer to 64
[    2.907195] sky2 0000:07:00.0: Yukon-2 EC Ultra chip revision 3
[    2.907279]   alloc irq_desc for 73 on node -1
[    2.907282]   alloc kstat_irqs on node -1
[    2.907295] sky2 0000:07:00.0: irq 73 for MSI/MSI-X
[    2.910642] sky2 0000:07:00.0: eth0: addr 48:5b:39:31:cb:23
[    2.910666] sky2 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.910677] sky2 0000:05:00.0: setting latency timer to 64
[    2.910711] sky2 0000:05:00.0: Yukon-2 EC Ultra chip revision 3
[    2.910795]   alloc irq_desc for 74 on node -1
[    2.910797]   alloc kstat_irqs on node -1
[    2.910809] sky2 0000:05:00.0: irq 74 for MSI/MSI-X
[    2.911366] sky2 0000:05:00.0: eth1: addr 48:5b:39:31:c3:39
[    2.912246] scsi4 : ahci
[    2.912334] scsi5 : ahci
[    2.912383] ata5: SATA max UDMA/133 abar m2048@0xfb0ff800 port 0xfb0ff900 irq 72
[    2.912387] ata6: SATA max UDMA/133 irq_stat 0x80400040, connection status changed irq 72
[    2.918285] Initializing USB Mass Storage driver...
[    2.918357] scsi6 : usb-storage 1-1:1.0
[    2.918443] usb-storage 2-5:1.0: Quirks match for vid 152d pid 2329: 8020
[    2.918460] scsi7 : usb-storage 2-5:1.0
[    2.918512] usbcore: registered new interface driver usb-storage
[    2.918513] USB Mass Storage support registered.
[    3.138293] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    3.259255] ata5: SATA link down (SStatus 0 SControl 370)
[    3.383644] usbcore: registered new interface driver hiddev
[    3.398159] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input2
[    3.398218] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1a.2-1/input0
[    3.442050] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.1/input/input3
[    3.442186] generic-usb 0003:046D:C312.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1a.2-1/input1
[    3.442200] usbcore: registered new interface driver usbhid
[    3.442202] usbhid: USB HID core driver
[    3.598156] usb 5-2: new low speed USB device using uhci_hcd and address 3
[    3.791029] input: USB Laser Wheel Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input4
[    3.791126] generic-usb 0003:1BCF:000A.0003: input,hiddev97,hidraw2: USB HID v1.11 Mouse [USB Laser Wheel Mouse] on usb-0000:00:1a.2-2/input0
[    3.858146] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 370)
[    3.860684] ata6.00: ATA-8: WDC WD1002FAEX-00Z3A0, 05.01D05, max UDMA/133
[    3.860689] ata6.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    3.862760] ata6.00: configured for UDMA/133
[    3.862869] scsi 5:0:0:0: Direct-Access     ATA      WDC WD1002FAEX-0 05.0 PQ: 0 ANSI: 5
[    3.863020] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    3.863085] sd 5:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.863167] sd 5:0:0:0: [sdc] Write Protect is off
[    3.863171] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.863206] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.863351]  sdc: sdc1 sdc2 < sdc5 sdc6 >
[    3.910454] sd 5:0:0:0: [sdc] Attached SCSI disk
[    3.912020] firewire_ohci 0000:09:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.921119] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    3.921150] scsi 7:0:0:0: Direct-Access     WDC WD10 EACS-22D6B0           PQ: 0 ANSI: 2 CCS
[    3.921617] sd 7:0:0:0: Attached scsi generic sg4 type 0
[    3.921674] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    3.922104] sd 7:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.922172] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    3.922730] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    3.922847] sd 7:0:0:0: [sdd] Write Protect is off
[    3.922850] sd 7:0:0:0: [sdd] Mode Sense: 34 00 00 00
[    3.922852] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    3.923091] sd 6:0:0:0: Attached scsi generic sg5 type 0
[    3.923208] sd 6:0:0:1: Attached scsi generic sg6 type 0
[    3.923353] sd 6:0:0:2: Attached scsi generic sg7 type 0
[    3.923502] sd 6:0:0:3: Attached scsi generic sg8 type 0
[    3.924352] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    3.924356]  sdd:
[    3.926661] sd 6:0:0:0: [sde] Attached SCSI removable disk
[    3.927499] sd 6:0:0:1: [sdf] Attached SCSI removable disk
[    3.928158] sd 6:0:0:2: [sdg] Attached SCSI removable disk
[    3.928785] sd 6:0:0:3: [sdh] Attached SCSI removable disk
[    3.935638]  sdd1
[    3.937263] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[    3.937266] sd 7:0:0:0: [sdd] Attached SCSI disk
[    4.077979] usb 8-2: new full speed USB device using uhci_hcd and address 2
[    4.079614] firewire_ohci: Added fw-ohci device 0000:09:02.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
[    4.447298] uvesafb: (C) 1988-2005, ATI Technologies Inc. , CYPRESS, 01.00, OEM: ATI ATOMBIOS, VBE v3.0
[    4.471699] uvesafb: VBIOS/hardware supports DDC2 transfers
[    4.522564] uvesafb: monitor limits: vf = 75 Hz, hf = 81 kHz, clk = 170 MHz
[    4.522674] uvesafb: scrolling: redraw
[    4.524115] mtrr: type mismatch for d0000000,800000 old: write-back new: write-combining
[    4.524117] mtrr: type mismatch for d0000000,400000 old: write-back new: write-combining
[    4.524119] mtrr: type mismatch for d0000000,200000 old: write-back new: write-combining
[    4.524122] mtrr: type mismatch for d0000000,100000 old: write-back new: write-combining
[    4.524124] mtrr: type mismatch for d0000000,80000 old: write-back new: write-combining
[    4.524126] mtrr: type mismatch for d0000000,40000 old: write-back new: write-combining
[    4.524128] mtrr: type mismatch for d0000000,20000 old: write-back new: write-combining
[    4.524130] mtrr: type mismatch for d0000000,10000 old: write-back new: write-combining
[    4.524132] mtrr: type mismatch for d0000000,8000 old: write-back new: write-combining
[    4.524134] mtrr: type mismatch for d0000000,4000 old: write-back new: write-combining
[    4.524136] mtrr: type mismatch for d0000000,2000 old: write-back new: write-combining
[    4.524138] mtrr: type mismatch for d0000000,1000 old: write-back new: write-combining
[    4.526418] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[    4.548009] firewire_core: created device fw0: GUID 001e8c0000d33180, S400
[    4.655174] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[    4.907869] Console: switching to colour frame buffer device 128x48
[    4.908108] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[    5.157948] uvesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011800000, using 11550k, total 16384k
[    5.157950] fb0: VESA VGA frame buffer device
[    5.162009] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[    5.649712] EXT4-fs (sdc5): mounted filesystem with ordered data mode. Opts: (null)
[   13.212909] udev[530]: starting version 163
[   13.220663] lp: driver loaded but no devices found
[   13.230856]   alloc irq_desc for 29 on node -1
[   13.230859]   alloc kstat_irqs on node -1
[   13.230868] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
[   13.230905] xhci_hcd 0000:02:00.0: setting latency timer to 64
[   13.230908] xhci_hcd 0000:02:00.0: xHCI Host Controller
[   13.231006] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[   13.231131] xhci_hcd 0000:02:00.0: irq 29, io mem 0xfb1fe000
[   13.231619] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   13.231622] Disabling lock debugging due to kernel taint
[   13.233191] Adding 11717628k swap on /dev/sdc6.  Priority:-1 extents:1 across:11717628k 
[   13.238878] usb usb9: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[   13.238982] xHCI xhci_add_endpoint called for root hub
[   13.238985] xHCI xhci_check_bandwidth called for root hub
[   13.239016] hub 9-0:1.0: USB hub found
[   13.239021] hub 9-0:1.0: 4 ports detected
[   13.244190] EDAC MC: Ver: 2.1.0 Dec  2 2010
[   13.255890] PCI: Discovered peer bus ff
[   13.257167] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:ff:03.0
[   13.257192] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:ff:03.0' (POLLED)
[   13.257196] EDAC i7core: Driver loaded.
[   13.296967] IR NEC protocol handler initialized
[   13.302469] [fglrx] Maximum main memory to use for locked dma buffers: 5776 MBytes.
[   13.302534] saa7164 driver loaded
[   13.302575] [fglrx]   vendor: 1002 device: 6898 count: 1
[   13.302580] saa7164 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.303323] [fglrx] ioport: bar 4, base 0xb000, size: 0x100
[   13.303334]   alloc irq_desc for 24 on node -1
[   13.303337]   alloc kstat_irqs on node -1
[   13.303345] pci 0000:03:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   13.303349] pci 0000:03:00.0: setting latency timer to 64
[   13.304006] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   13.304013] saa7164[0]/0: found at 0000:06:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb800000
[   13.304020] saa7164 0000:06:00.0: setting latency timer to 64
[   13.304123] [fglrx] Kernel PAT support is enabled
[   13.304144] [fglrx] module loaded - fglrx 8.78.30 [Sep 20 2010] with 1 minors
[   13.316046] IR RC5(x) protocol handler initialized
[   13.319235] IR RC6 protocol handler initialized
[   13.321176] IR JVC protocol handler initialized
[   13.322749] IR Sony protocol handler initialized
[   13.325580] lirc_dev: IR Remote Control driver registered, major 248 
[   13.327115] IR LIRC bridge handler initialized
[   13.335933] Registered IR keymap rc-rc6-mce
[   13.335995] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0011) as /devices/virtual/rc/rc0/input5
[   13.336029] rc0: Media Center Ed. eHome Infrared Remote Transceiver (1784:0011) as /devices/virtual/rc/rc0
[   13.336050] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[   13.336064] mceusb 8-2:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver on usb8:2
[   13.336079] usbcore: registered new interface driver mceusb
[   13.349407] type=1400 audit(1294968949.938:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=761 comm="apparmor_parser"
[   13.349562] type=1400 audit(1294968949.938:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=804 comm="apparmor_parser"
[   13.349677] type=1400 audit(1294968949.938:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=793 comm="apparmor_parser"
[   13.349800] type=1400 audit(1294968949.938:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=761 comm="apparmor_parser"
[   13.350013] type=1400 audit(1294968949.938:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=761 comm="apparmor_parser"
[   13.350045] type=1400 audit(1294968949.938:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=804 comm="apparmor_parser"
[   13.350064] type=1400 audit(1294968949.938:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=793 comm="apparmor_parser"
[   13.350276] type=1400 audit(1294968949.938:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=793 comm="apparmor_parser"
[   13.350315] type=1400 audit(1294968949.938:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=804 comm="apparmor_parser"
[   13.362783]   alloc irq_desc for 22 on node -1
[   13.362785]   alloc kstat_irqs on node -1
[   13.362791] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.362836]   alloc irq_desc for 75 on node -1
[   13.362837]   alloc kstat_irqs on node -1
[   13.362845] HDA Intel 0000:00:1b.0: irq 75 for MSI/MSI-X
[   13.362864] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.462585] hda_codec: ALC889: BIOS auto-probing.
[   13.470336]   alloc irq_desc for 34 on node -1
[   13.470339]   alloc kstat_irqs on node -1
[   13.470346] HDA Intel 0000:03:00.1: PCI INT B -> GSI 34 (level, low) -> IRQ 34
[   13.470401]   alloc irq_desc for 76 on node -1
[   13.470403]   alloc kstat_irqs on node -1
[   13.470410] HDA Intel 0000:03:00.1: irq 76 for MSI/MSI-X
[   13.470428] HDA Intel 0000:03:00.1: setting latency timer to 64
[   13.496851] saa7164_downloadfirmware() no first image
[   13.496861] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
[   13.534116] saa7164_downloadfirmware() firmware read 3978608 bytes.
[   13.534118] saa7164_downloadfirmware() firmware loaded.
[   13.534120] Firmware file header part 1:
[   13.534122]  .FirmwareSize = 0x0
[   13.534123]  .BSLSize = 0x0
[   13.534125]  .Reserved = 0x3cb57
[   13.534126]  .Version = 0x3
[   13.534127] saa7164_downloadfirmware() SecBootLoader.FileSize = 3978608
[   13.534133] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   13.534135] saa7164_downloadfirmware() BSLSize = 0x0
[   13.534137] saa7164_downloadfirmware() Reserved = 0x0
[   13.534138] saa7164_downloadfirmware() Version = 0x51cc1
[   13.709509] EXT4-fs (sdc5): re-mounted. Opts: errors=remount-ro
[   14.270161] type=1400 audit(1294968950.858:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1192 comm="apparmor_parser"
[   14.282846] sky2 0000:07:00.0: eth0: enabling interface
[   14.283371] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.287479] sky2 0000:05:00.0: eth1: enabling interface
[   14.288009] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   15.468837] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   15.468839] vboxdrv: Successfully done.
[   15.468841] vboxdrv: Found 8 processor cores.
[   15.468886] VBoxDrv: dbg - g_abExecMemory=ffffffffa04c7d60
[   15.469040] vboxdrv: fAsync=0 offMin=0x210 offMax=0x18fb9
[   15.469080] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   15.469082] vboxdrv: Successfully loaded version 3.2.8_OSE (interface 0x00140001).
[   15.804382] EXT4-fs (sdc5): re-mounted. Opts: errors=remount-ro,commit=0
[   15.965658] sky2 0000:07:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   15.966174] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.739187] uvesafb: mode switch failed (eax=0x34f, err=0). Trying again with default timings.
[   20.765683] saa7164_downloadimage() Image downloaded, booting...
[   20.874510] saa7164_downloadimage() Image booted successfully.
[   20.874524] starting firmware download(2)
[   23.216284] saa7164_downloadimage() Image downloaded, booting...
[   24.645368] saa7164_downloadimage() Image booted successfully.
[   24.645383] firmware download complete.
[   24.686007] tveeprom 0-0000: Hauppauge model 88061, rev C4F2, serial# 7229733
[   24.686011] tveeprom 0-0000: MAC address is 00:0d:fe:6e:51:25
[   24.686014] tveeprom 0-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   24.686018] tveeprom 0-0000: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   24.686021] tveeprom 0-0000: audio processor is SAA7164 (idx 43)
[   24.686024] tveeprom 0-0000: decoder processor is SAA7164 (idx 40)
[   24.686026] tveeprom 0-0000: has radio, has IR receiver, has no IR transmitter
[   24.686029] saa7164[0]: Hauppauge eeprom: model=88061
[   25.011434] tda18271 1-0060: creating new instance
[   25.015702] TDA18271HD/C2 detected @ 1-0060
[   25.361382] DVB: registering new adapter (saa7164)
[   25.361385] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   25.644926] tda18271 2-0060: creating new instance
[   25.649182] TDA18271HD/C2 detected @ 2-0060
[   25.990180] tda18271: performing RF tracking filter calibration
[   26.005691] eth0: no IPv6 routers present
[   28.625309] tda18271: RF tracking filter calibration complete
[   28.625424] DVB: registering new adapter (saa7164)
[   28.625426] DVB: registering adapter 1 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   28.663392] audit_printk_skb: 27 callbacks suppressed
[   28.663394] type=1400 audit(1294968965.243:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1552 comm="apparmor_parser"
[   28.663916] type=1400 audit(1294968965.243:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1552 comm="apparmor_parser"
[   28.700750] ppdev: user-space parallel port driver
[   29.076725]   alloc irq_desc for 77 on node -1
[   29.076727]   alloc kstat_irqs on node -1
[   29.076735] fglrx_pci 0000:03:00.0: irq 77 for MSI/MSI-X
[   29.077418] [fglrx] Firegl kernel thread PID: 1652
[   29.077655] [fglrx] IRQ 77 Enabled
[   29.303837] [fglrx] Gart USWC size:1280 M.
[   29.303839] [fglrx] Gart cacheable size:508 M.
[   29.303843] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   29.303845] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
[   29.303846] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
[   31.285084] EXT4-fs (sdc5): re-mounted. Opts: errors=remount-ro,commit=0
[   31.458746] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   48.767326] Intel AES-NI instructions are not detected.
[   48.833655] padlock: VIA PadLock not detected.

When I reach the terminal login, I see the following two system messages appear:

[   20.874524] starting firmware download(2)
[   23.216284] saa7164_downloadimage() Image downloaded, booting..

After that it goes to the GUI Login. Thoughts?

---

