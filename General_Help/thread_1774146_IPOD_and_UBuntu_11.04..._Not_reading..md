---
title: "IPOD and UBuntu 11.04... Not reading."
date: 2011-06-02
forum: General Help
---

### Post by berberry08 on 2011-06-02
Hi all,

I can't get Banshee or my system to recconize my IPOD. I believe its a 6Gen 8Gig. This is the log I got:
[    0.816809] system 00:01: [io  0xff2c-0xff2f] has been reserved
[    0.816818] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.816825] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.816833] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.816840] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.816847] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.816855] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.816863] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.816872] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.816904] pnp 00:02: [io  0x0000-0x001f]
[    0.816910] pnp 00:02: [io  0x0081-0x0091]
[    0.816915] pnp 00:02: [io  0x0093-0x009f]
[    0.816921] pnp 00:02: [io  0x00c0-0x00df]
[    0.816926] pnp 00:02: [dma 4]
[    0.817001] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.817068] pnp 00:03: [io  0x0070-0x0077]
[    0.817153] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.817320] pnp 00:04: [irq 0 disabled]
[    0.817342] pnp 00:04: [irq 8]
[    0.817352] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.817430] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.817462] pnp 00:05: [io  0x00f0]
[    0.817474] pnp 00:05: [irq 13]
[    0.817555] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.817586] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.817661] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.817746] pnp 00:07: [io  0x0060]
[    0.817752] pnp 00:07: [io  0x0064]
[    0.817764] pnp 00:07: [irq 1]
[    0.817843] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.817960] pnp 00:08: [irq 12]
[    0.818053] pnp 00:08: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
[    0.818396] pnp: PnP ACPI: found 9 devices
[    0.818401] ACPI: ACPI bus type pnp unregistered
[    0.818408] PnPBIOS: Disabled by ACPI PNP
[    0.858027] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.858038] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.858049] pci 0000:00:1c.0:   bridge window [mem 0x57000000-0x57ffffff]
[    0.858060] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
[    0.858073] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.858081] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.858092] pci 0000:00:1c.1:   bridge window [mem 0x56000000-0x56ffffff]
[    0.858102] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
[    0.858115] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.858120] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.858130] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.858138] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.858184] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.858195] pci 0000:00:1c.0: setting latency timer to 64
[    0.858218] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.858227] pci 0000:00:1c.1: setting latency timer to 64
[    0.858241] pci 0000:00:1e.0: setting latency timer to 64
[    0.858251] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.858257] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.858263] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.858270] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
[    0.858276] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.858282] pci_bus 0000:01: resource 1 [mem 0x57000000-0x57ffffff]
[    0.858289] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
[    0.858296] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.858302] pci_bus 0000:02: resource 1 [mem 0x56000000-0x56ffffff]
[    0.858309] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
[    0.858316] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.858322] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.858328] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.858335] pci_bus 0000:05: resource 7 [mem 0x40000000-0xfebfffff]
[    0.858415] NET: Registered protocol family 2
[    0.858562] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.859117] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.860090] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.860514] TCP: Hash tables configured (established 131072 bind 65536)
[    0.860520] TCP reno registered
[    0.860529] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.860548] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.860780] NET: Registered protocol family 1
[    0.860819] pci 0000:00:02.0: Boot video device
[    0.861087] PCI: CLS 64 bytes, default 64
[    0.861139] Simple Boot Flag at 0x44 set to 0x1
[    0.861608] cpufreq-nforce2: No nForce2 chipset.
[    0.861929] audit: initializing netlink socket (disabled)
[    0.861951] type=2000 audit(1307066810.856:1): initialized
[    0.880806] highmem bounce pool size: 64 pages
[    0.880819] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.885342] VFS: Disk quotas dquot_6.5.2
[    0.885488] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.887254] fuse init (API version 7.16)
[    0.887494] msgmni has been set to 1729
[    0.888121] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.888199] io scheduler noop registered
[    0.888207] io scheduler deadline registered
[    0.888259] io scheduler cfq registered (default)
[    0.888512] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.888595] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.888728] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.888801] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.888995] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.889061] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.889187] intel_idle: MWAIT substates: 0x20220
[    0.889205] intel_idle: v0.4 model 0x1C
[    0.889211] intel_idle: lapic_timer_reliable_states 0x2
[    0.889225] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    1.088057] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.288089] ACPI: AC Adapter [AC] (off-line)
[    1.288320] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.288332] ACPI: Power Button [PWRB]
[    1.288443] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.288453] ACPI: Sleep Button [SLPB]
[    1.288567] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.288612] ACPI: Lid Switch [LID0]
[    1.288746] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.288755] ACPI: Power Button [PWRF]
[    1.288900] ACPI: Fan [FAN] (on)
[    1.289172] ACPI: acpi_idle yielding to intel_idle
[    1.423748] thermal LNXTHERM:00: registered as thermal_zone0
[    1.423756] ACPI: Thermal Zone [THRM] (46 C)
[    1.423848] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.423994] ERST: Table is not found!
[    1.424182] isapnp: Scanning for PnP cards...
[    1.424273] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.552054] ACPI: Battery Slot [BAT0] (battery absent)
[    1.778040] isapnp: No Plug & Play device found
[    1.784317] Linux agpgart interface v0.103
[    1.784496] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.784767] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.785089] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.785330] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    1.788578] brd: module loaded
[    1.790131] loop: module loaded
[    1.790380] i2c-core: driver [adp5520] using legacy suspend method
[    1.790386] i2c-core: driver [adp5520] using legacy resume method
[    1.791590] Fixed MDIO Bus: probed
[    1.791698] PPP generic driver version 2.4.2
[    1.791809] tun: Universal TUN/TAP device driver, 1.6
[    1.791814] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.792077] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.792124] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.792158] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.792167] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.792271] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.792371] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.792391] ehci_hcd 0000:00:1d.7: debug port 1
[    1.796296] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.796331] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58204400
[    1.812032] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.812340] hub 1-0:1.0: USB hub found
[    1.812351] hub 1-0:1.0: 8 ports detected
[    1.812526] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.812564] uhci_hcd: USB Universal Host Controller Interface driver
[    1.812640] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.812655] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.812663] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.812766] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.812856] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
[    1.813163] hub 2-0:1.0: USB hub found
[    1.813174] hub 2-0:1.0: 2 ports detected
[    1.813322] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.813336] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.813343] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.813442] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.813540] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
[    1.813847] hub 3-0:1.0: USB hub found
[    1.813858] hub 3-0:1.0: 2 ports detected
[    1.814014] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.814028] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.814035] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.814147] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.816129] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    1.816452] hub 4-0:1.0: USB hub found
[    1.816463] hub 4-0:1.0: 2 ports detected
[    1.816624] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.816640] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.816647] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.816746] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.816845] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
[    1.817150] hub 5-0:1.0: USB hub found
[    1.817161] hub 5-0:1.0: 2 ports detected
[    1.817428] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.831223] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.831239] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.831586] mousedev: PS/2 mouse device common for all mice
[    1.832082] rtc_cmos 00:03: RTC can wake from S4
[    1.832240] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.832282] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.832520] device-mapper: uevent: version 1.0.3
[    1.832731] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.832909] device-mapper: multipath: version 1.2.0 loaded
[    1.832918] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.833129] EISA: Probing bus 0 at eisa.0
[    1.833136] EISA: Cannot allocate resource for mainboard
[    1.833142] Cannot allocate resource for EISA slot 1
[    1.833148] Cannot allocate resource for EISA slot 2
[    1.833153] Cannot allocate resource for EISA slot 3
[    1.833159] Cannot allocate resource for EISA slot 4
[    1.833164] Cannot allocate resource for EISA slot 5
[    1.833170] Cannot allocate resource for EISA slot 6
[    1.833175] Cannot allocate resource for EISA slot 7
[    1.833181] Cannot allocate resource for EISA slot 8
[    1.833185] EISA: Detected 0 cards.
[    1.833490] cpuidle: using governor ladder
[    1.833757] cpuidle: using governor menu
[    1.834373] TCP cubic registered
[    1.834719] NET: Registered protocol family 10
[    1.836082] NET: Registered protocol family 17
[    1.836153] Registering the dns_resolver key type
[    1.837091] Using IPI No-Shortcut mode
[    1.837399] PM: Hibernation image not present or could not be loaded.
[    1.837424] registered taskstats version 1
[    1.837862]   Magic number: 15:496:105
[    1.837880] usbmon usbmon1: hash matches
[    1.838006] rtc_cmos 00:03: setting system clock to 2011-06-03 02:06:52 UTC (1307066812)
[    1.838014] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.838018] EDD information not available.
[    1.838259] Freeing unused kernel memory: 700k freed
[    1.838690] Write protecting the kernel text: 5192k
[    1.838778] Write protecting the kernel read-only data: 2148k
[    1.844828] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.897608] <30>udev[63]: starting version 167
[    2.236134] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    2.508820] atl1c 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.508847] atl1c 0000:01:00.0: setting latency timer to 64
[    2.550917] ahci 0000:00:1f.2: version 3.0
[    2.550953] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.551066] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    2.551157] ahci: SSS flag set, parallel bus scan disabled
[    2.551218] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    2.551231] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    2.551246] ahci 0000:00:1f.2: setting latency timer to 64
[    2.560755] scsi0 : ahci
[    2.564165] scsi1 : ahci
[    2.565141] scsi2 : ahci
[    2.569542] scsi3 : ahci
[    2.570308] ata1: SATA max UDMA/133 abar m1024@0x58204000 port 0x58204100 irq 42
[    2.570323] ata2: SATA max UDMA/133 abar m1024@0x58204000 port 0x58204180 irq 42
[    2.570331] ata3: DUMMY
[    2.570337] ata4: DUMMY
[    2.617885] atl1c 0000:01:00.0: version 1.0.1.0-NAPI
[    2.732133] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.984732] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
[    2.985186] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    2.990896] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input6
[    2.991414] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    2.991968] usbcore: registered new interface driver usbhid
[    2.991977] usbhid: USB HID core driver
[    3.060156] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.061009] ata1.00: unexpected _GTF length (4)
[    3.061392] ata1.00: ATA-8: Hitachi HTS545016B9A300, PBBOC60F, max UDMA/133
[    3.061400] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.062371] ata1.00: unexpected _GTF length (4)
[    3.062752] ata1.00: configured for UDMA/133
[    3.063035] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54501 PBBO PQ: 0 ANSI: 5
[    3.063618] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.063737] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    3.063972] sd 0:0:0:0: [sda] Write Protect is off
[    3.063982] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.064126] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.113270]  sda: sda1 sda2 < sda5 >
[    3.114194] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.380151] ata2: SATA link down (SStatus 0 SControl 300)
[    3.781379] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.453253] Adding 1036284k swap on /dev/sda5.  Priority:-1 extents:1 across:1036284k 
[    7.139489] <30>udev[265]: starting version 167
[    7.141824] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.458846] lp: driver loaded but no devices found
[    9.198126] cfg80211: Calling CRDA to update world regulatory domain
[    9.415201] [drm] Initialized drm 1.1.0 20060810
[    9.452367] type=1400 audit(1307066820.110:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=520 comm="apparmor_parser"
[    9.453151] type=1400 audit(1307066820.110:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=520 comm="apparmor_parser"
[    9.453668] type=1400 audit(1307066820.110:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=520 comm="apparmor_parser"
[    9.455178] type=1400 audit(1307066820.110:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=478 comm="apparmor_parser"
[    9.456342] type=1400 audit(1307066820.114:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=478 comm="apparmor_parser"
[    9.457116] type=1400 audit(1307066820.114:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=478 comm="apparmor_parser"
[    9.532077] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.532092] i915 0000:00:02.0: setting latency timer to 64
[    9.589671] Linux video capture interface: v2.00
[    9.609911] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[    9.609923] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.609928] [drm] Driver supports precise vblank timestamp query.
[    9.696414] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.696805] [drm] initialized overlay support
[    9.955155] uvcvideo: Found UVC 1.00 device Webcam (04f2:b19d)
[    9.958121] input: Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7
[    9.958394] usbcore: registered new interface driver uvcvideo
[    9.958402] USB Video Class driver (v1.0.0)
[    9.980553] Console: switching to colour frame buffer device 128x37
[    9.980634] fb0: inteldrmfb frame buffer device
[    9.980640] drm: registered panic notifier
[   10.221363] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   10.294807] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   10.300370] acpi device:25: registered as cooling_device3
[   10.300941] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   10.301162] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   10.301633] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.567005] cfg80211: World regulatory domain updated:
[   10.567013] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.567022] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.567028] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.567035] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.567042] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.567048] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.716157] fixme: max PWM is zero.
[   11.057436] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.057461] ath9k 0000:02:00.0: setting latency timer to 64
[   11.109137] ath: EEPROM regdomain: 0x65
[   11.109144] ath: EEPROM indicates we should expect a direct regpair map
[   11.109152] ath: Country alpha2 being used: 00
[   11.109156] ath: Regpair used: 0x65
[   11.109164] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   11.109171] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109177] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   11.109184] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109190] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   11.109197] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109202] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   11.109209] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109215] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   11.109222] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109228] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   11.109235] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109240] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   11.109247] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109253] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   11.109260] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109266] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   11.109273] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109278] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   11.109285] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109291] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   11.109298] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109304] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   11.109311] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109316] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   11.109323] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   11.109329] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   11.111324] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   12.107638] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.107773] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   12.107838] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.163600] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.165703] Registered led device: ath9k-phy0::radio
[   13.165795] Registered led device: ath9k-phy0::assoc
[   13.165964] Registered led device: ath9k-phy0::tx
[   13.166140] Registered led device: ath9k-phy0::rx
[   13.166165] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf86a0000, irq=17
[   13.350872] hda_codec: ALC272X: BIOS auto-probing.
[   13.362707] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.363104] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.634819] type=1400 audit(1307066827.291:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=739 comm="apparmor_parser"
[   16.635850] type=1400 audit(1307066827.291:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=739 comm="apparmor_parser"
[   16.636595] type=1400 audit(1307066827.295:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=739 comm="apparmor_parser"
[   16.779197] ppdev: user-space parallel port driver
[   16.896430] type=1400 audit(1307066827.555:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=738 comm="apparmor_parser"
[   17.148602] type=1400 audit(1307066827.807:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=753 comm="apparmor_parser"
[   17.148628] type=1400 audit(1307066827.807:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=760 comm="apparmor_parser"
[   17.150137] type=1400 audit(1307066827.807:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=760 comm="apparmor_parser"
[   17.150161] type=1400 audit(1307066827.807:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=753 comm="apparmor_parser"
[   17.184285] type=1400 audit(1307066827.843:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=764 comm="apparmor_parser"
[   17.211504] type=1400 audit(1307066827.867:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=740 comm="apparmor_parser"
[   19.727924] atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
[   19.789150] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.143608] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.934031] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[   38.054537] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   59.487788] wlan0: authenticate with 00:24:d2:39:a9:19 (try 1)
[   59.491224] wlan0: authenticated
[   59.513818] wlan0: associate with 00:24:d2:39:a9:19 (try 1)
[   59.516411] wlan0: RX AssocResp from 00:24:d2:39:a9:19 (capab=0x431 status=0 aid=1)
[   59.516422] wlan0: associated
[   59.517267] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.664039] wlan0: no IPv6 routers present
[  683.856172] usb 1-1: new high speed USB device using ehci_hcd and address 4
[  684.086021] usbcore: registered new interface driver uas
[  684.105028] Initializing USB Mass Storage driver...
[  684.105496] scsi4 : usb-storage 1-1:1.0
[  684.107144] usbcore: registered new interface driver usb-storage
[  684.107154] USB Mass Storage support registered.
[  685.124397] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  685.126807] sd 4:0:0:0: Attached scsi generic sg1 type 0
[  685.134118] sd 4:0:0:0: [sdb] Spinning up disk....ready
[  687.081032] sd 4:0:0:0: [sdb] 1941441 4096-byte logical blocks: (7.95 GB/7.40 GiB)
[  687.082101] sd 4:0:0:0: [sdb] Write Protect is off
[  687.082122] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[  687.083272] sd 4:0:0:0: [sdb] No Caching mode page present
[  687.083292] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  687.086775] sd 4:0:0:0: [sdb] 1941441 4096-byte logical blocks: (7.95 GB/7.40 GiB)
[  687.088639] sd 4:0:0:0: [sdb] No Caching mode page present
[  687.088658] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  687.090602]  sdb: sdb1
[  687.097172] sd 4:0:0:0: [sdb] 1941441 4096-byte logical blocks: (7.95 GB/7.40 GiB)
[  687.099124] sd 4:0:0:0: [sdb] No Caching mode page present
[  687.099144] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  687.099160] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  944.858445] usb 1-1: USB disconnect, address 4
[ 1027.536097] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1027.697313] scsi5 : usb-storage 1-1:1.0
[ 1028.711861] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1028.715255] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 1028.716941] sd 5:0:0:0: [sdc] Spinning up disk....ready
[ 1030.769074] sd 5:0:0:0: [sdc] 1941441 4096-byte logical blocks: (7.95 GB/7.40 GiB)
[ 1030.769676] sd 5:0:0:0: [sdc] Write Protect is off
[ 1030.769691] sd 5:0:0:0: [sdc] Mode Sense: 68 00 00 08
[ 1030.770667] sd 5:0:0:0: [sdc] No Caching mode page present
[ 1030.770681] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1030.774692] sd 5:0:0:0: [sdc] 1941441 4096-byte logical blocks: (7.95 GB/7.40 GiB)
[ 1030.776437] sd 5:0:0:0: [sdc] No Caching mode page present
[ 1030.776452] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1030.777879]  sdc: sdc1
[ 1030.785214] sd 5:0:0:0: [sdc] 1941441 4096-byte logical blocks: (7.95 GB/7.40 GiB)
[ 1030.787214] sd 5:0:0:0: [sdc] No Caching mode page present
[ 1030.787236] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 1030.787254] sd 5:0:0:0: [sdc] Attached SCSI removable disk


Sorry, I'm very new to this and have been on this forum for hours trying to find help! I want my music!!

---

### Post by berberry08 on 2011-06-02
Bunp.... I know I'm a newbie! I need help!

---

### Post by Ditchdoc7893 on 2011-06-02
I'm not exactly sure about anything 11.04 as I don't have it running on any of my machines. However, as a general help response, my questions would be do you have any of the music on the iPod backed up anywhere else?, and have you considered using nautilus to see if you can copy and paste them to your HD, or at least on a minimum be able to access the files?  BTW, friendly feedback, be careful about bumping unless you haven't rec'd a response within 24 hrs.  It doesn't bother me, but some folks get their panties in a wad about it.  :)

---

### Post by berberry08 on 2011-06-02
So sorry! I just got this OS a week ago and LOVE how eAnverything else works but I keep on having problems making my IPOD synch. There really wasn't many walktrhoughs on how to manually do it. I am used to troubleshooting and getting the answers quickly.... again, I apologise!

All my mp3's are backed up.

---

### Post by Rodney9 on 2011-06-03
Try GTKPOD, it is in the Software Center.

---

### Post by moboticdes on 2011-06-03
> **Rodney9 said:**
> Try GTKPOD, it is in the Software Center.

I'm sorry I'm posting this on multiple posts but I want to clear this once and for all:

As of June 2011 Banshee, Amarok and GtkPod cannot sync library with generation 6th 7th or 8 ipods!
Banshee can mostly only play the music already in the ipod!
For some compatible ipod players see this compatibility list: [http://wiki.songbirdnest.com/Docs/IPod_Device_Support](http://wiki.songbirdnest.com/Docs/IPod_Device_Support)

You won't get any better than that. THAT'S WHY YOU SHOULD AVOID APPLE  STUFF EVEN MORE THAN WINDOWS ONE! THEY HAVE NOT YET LEARNED TO PLAY  ALONG WITH OTHERS...

Now to the solution, forget banshee gtkpod or amarok or rhythmbox as  they all don't support syncing, forget about using wine to install  iTunes and sync as wine doesn't support usb tethering.
The only working solution is:

1. install windows xp in virtualbox
2. activate usb detection
3. install iTunes and sync from there.

I know it sucks using an entire virtual machine for such a stupid job  but again thank those people who dont want to make life easier but only  to earn some big money with their proprietary software! 
Hope this has finally cleared the state of things and wont make you waste any more time trying to sync under linux.

---

