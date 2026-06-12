---
title: "Dmesg..........Question"
date: 2010-07-22
forum: General Help
---

### Post by jkid on 2010-07-22
iwould like to know what the output at the end.....is im a little worry about it...



```
[    0.585886] bus: 07 index 2 mmio: [0x50000000-0x53ffffff]
[    0.585889] bus: 07 index 3 mmio: [0x58000000-0x5bffffff]
[    0.585897] NET: Registered protocol family 2
[    0.586011] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.586266] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.586951] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.587374] TCP: Hash tables configured (established 131072 bind 65536)
[    0.587377] TCP reno registered
[    0.587522] NET: Registered protocol family 1
[    0.587665] checking if image is initramfs... it is
[    1.047940] Switched to high resolution mode on CPU 0
[    1.283693] Freeing initrd memory: 7372k freed
[    1.283755] Simple Boot Flag at 0x36 set to 0x1
[    1.283790] cpufreq: No nForce2 chipset.
[    1.283967] audit: initializing netlink socket (disabled)
[    1.283989] type=2000 audit(1279805488.280:1): initialized
[    1.292436] highmem bounce pool size: 64 pages
[    1.292445] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.293847] VFS: Disk quotas dquot_6.5.1
[    1.293907] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.294553] fuse init (API version 7.10)
[    1.294642] msgmni has been set to 1724
[    1.294825] alg: No test for stdrng (krng)
[    1.294837] io scheduler noop registered
[    1.294839] io scheduler anticipatory registered
[    1.294842] io scheduler deadline registered
[    1.294857] io scheduler cfq registered (default)
[    1.294872] pci 0000:00:02.0: Boot video device
[    1.298995] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.299044] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.299082] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.299098] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.299114] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.299131] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.299215] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.299260] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.300865] ACPI: AC Adapter [AC] (off-line)
[    1.341935] ACPI: Battery Slot [BAT0] (battery present)
[    1.342012] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.342015] ACPI: Power Button (FF) [PWRF]
[    1.342060] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.346906] ACPI: Lid Switch [LID0]
[    1.346959] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.346962] ACPI: Sleep Button (CM) [SLPB]
[    1.347006] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.347009] ACPI: Power Button (CM) [PWB]
[    1.347374] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    1.347400] processor ACPI_CPU:00: registered as cooling_device0
[    1.371307] thermal LNXTHERM:01: registered as thermal_zone0
[    1.377210] ACPI: Thermal Zone [THR0] (55 C)
[    1.386296] thermal LNXTHERM:02: registered as thermal_zone1
[    1.392073] ACPI: Thermal Zone [THR1] (32 C)
[    1.392115] isapnp: Scanning for PnP cards...
[    1.746352] isapnp: No Plug & Play device found
[    1.747471] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.747830] serial 0000:00:1e.3: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.747837] serial 0000:00:1e.3: PCI INT B disabled
[    1.748540] brd: module loaded
[    1.748859] loop: module loaded
[    1.748937] Fixed MDIO Bus: probed
[    1.748944] PPP generic driver version 2.4.2
[    1.749001] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.749029] Driver 'sd' needs updating - please use bus_type methods
[    1.749038] Driver 'sr' needs updating - please use bus_type methods
[    1.749113] ata_piix 0000:00:1f.1: version 2.12
[    1.749123] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.749164] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.749257] scsi0 : ata_piix
[    1.749337] scsi1 : ata_piix
[    1.750017] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.750021] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.920622] ata1.00: ATA-5: HITACHI_DK23FB-40, 00M1A0C1, max UDMA/100
[    1.920625] ata1.00: 78140160 sectors, multi 16: LBA 
[    1.920668] ata1.01: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CC15, max MWDMA2
[    1.936506] ata1.00: configured for UDMA/100
[    1.952358] ata1.01: configured for MWDMA2
[    1.954663] ata2: port disabled. ignoring.
[    1.954786] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FB-4 00M1 PQ: 0 ANSI: 5
[    1.954884] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    1.954902] sd 0:0:0:0: [sda] Write Protect is off
[    1.954905] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.954931] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.954989] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    1.955004] sd 0:0:0:0: [sda] Write Protect is off
[    1.955006] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.955031] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.955034]  sda: sda1 sda2 < sda5 sda6 >
[    2.014994] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.015036] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.018961] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CC15 PQ: 0 ANSI: 5
[    2.030489] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.030493] Uniform CD-ROM driver Revision: 3.20
[    2.030573] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.030613] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    2.031242] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.031263] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.031286] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.031290] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.031359] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.035288] ehci_hcd 0000:00:1d.7: debug port 1
[    2.035295] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.035310] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0040000
[    2.048007] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.048077] usb usb1: configuration #1 chosen from 1 choice
[    2.048108] hub 1-0:1.0: USB hub found
[    2.048116] hub 1-0:1.0: 8 ports detected
[    2.048244] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.048260] uhci_hcd: USB Universal Host Controller Interface driver
[    2.048281] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.048287] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.048291] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.048330] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.048354] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    2.048430] usb usb2: configuration #1 chosen from 1 choice
[    2.048454] hub 2-0:1.0: USB hub found
[    2.048462] hub 2-0:1.0: 2 ports detected
[    2.048542] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.048550] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.048554] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.048596] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.048629] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    2.048701] usb usb3: configuration #1 chosen from 1 choice
[    2.048725] hub 3-0:1.0: USB hub found
[    2.048731] hub 3-0:1.0: 2 ports detected
[    2.048811] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.048818] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.048821] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.048860] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.048894] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.048965] usb usb4: configuration #1 chosen from 1 choice
[    2.048994] hub 4-0:1.0: USB hub found
[    2.049000] hub 4-0:1.0: 2 ports detected
[    2.049079] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.049087] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.049091] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.049138] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.049171] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    2.049256] usb usb5: configuration #1 chosen from 1 choice
[    2.049281] hub 5-0:1.0: USB hub found
[    2.049287] hub 5-0:1.0: 2 ports detected
[    2.049425] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.055357] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.058795] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.058801] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.058803] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.058806] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.058808] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.058966] mice: PS/2 mouse device common for all mice
[    2.059159] rtc_cmos 00:05: RTC can wake from S4
[    2.059201] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.059235] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.059293] device-mapper: uevent: version 1.0.3
[    2.059400] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.059446] device-mapper: multipath: version 1.0.5 loaded
[    2.059449] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.059522] EISA: Probing bus 0 at eisa.0
[    2.059530] Cannot allocate resource for EISA slot 1
[    2.059533] Cannot allocate resource for EISA slot 2
[    2.059535] Cannot allocate resource for EISA slot 3
[    2.059561] EISA: Detected 0 cards.
[    2.059635] cpuidle: using governor ladder
[    2.059714] cpuidle: using governor menu
[    2.060227] TCP cubic registered
[    2.060328] NET: Registered protocol family 10
[    2.060738] lo: Disabled Privacy Extensions
[    2.061054] NET: Registered protocol family 17
[    2.061075] Bluetooth: L2CAP ver 2.11
[    2.061077] Bluetooth: L2CAP socket layer initialized
[    2.061080] Bluetooth: SCO (Voice Link) ver 0.6
[    2.061082] Bluetooth: SCO socket layer initialized
[    2.061106] Bluetooth: RFCOMM socket layer initialized
[    2.061114] Bluetooth: RFCOMM TTY layer initialized
[    2.061115] Bluetooth: RFCOMM ver 1.10
[    2.061383] Using IPI No-Shortcut mode
[    2.061454] registered taskstats version 1
[    2.061590]   Magic number: 2:515:534
[    2.061602] bdi 1:12: hash matches
[    2.061669] rtc_cmos 00:05: setting system clock to 2010-07-22 13:31:29 UTC (1279805489)
[    2.061672] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.061674] EDD information not available.
[    2.061957] Freeing unused kernel memory: 532k freed
[    2.062074] Write protecting the kernel text: 4120k
[    2.062115] Write protecting the kernel read-only data: 1524k
[    2.098070] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.528498] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    2.728718] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    2.734105] ohci1394 0000:06:06.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    2.783926] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[b0108000-b01087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.790702] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.795320] 8139cp 0000:06:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.798407] 8139too Fast Ethernet driver 0.9.28
[    2.798451] 8139too 0000:06:07.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.799971] eth0: RealTek RTL8139 at 0x3000, 00:0a:e4:dc:b9:d9, IRQ 20
[    2.799973] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    2.928556] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    3.037069] Marking TSC unstable due to TSC halts in idle
[    3.128831] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[    3.129063] PM: Starting manual resume from disk
[    3.129066] PM: Resume from partition 8:6
[    3.129068] PM: Checking hibernation image.
[    3.129247] PM: Resume from disk failed.
[    3.164625] kjournald starting.  Commit interval 5 seconds
[    3.164635] EXT3-fs: mounted filesystem with ordered data mode.
[    3.544024] Clocksource tsc unstable (delta = -440590134 ns)
[    9.646951] udev: starting version 141
[   10.076468] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6
[   10.079779] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.371129] Linux agpgart interface v0.103
[   10.378454] intel_rng: FWH not detected
[   10.403808] ieee80211_crypt: registered algorithm 'NULL'
[   10.415926] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   10.415929] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   10.510604] sdhci: Secure Digital Host Controller Interface driver
[   10.510607] sdhci: Copyright(c) Pierre Ossman
[   10.512598] sdhci-pci 0000:06:06.4: SDHCI controller found [104c:8034] (rev 0)
[   10.512620] sdhci-pci 0000:06:06.4: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.512759] mmc0: SDHCI controller on PCI [0000:06:06.4] using PIO
[   10.512831] mmc1: SDHCI controller on PCI [0000:06:06.4] using PIO
[   10.512905] mmc2: SDHCI controller on PCI [0000:06:06.4] using PIO
[   10.904011] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   10.904529] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   10.907622] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   10.967461] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   10.967464] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   10.967675] ipw2200 0000:06:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   10.969998] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   10.970050] ipw2200 0000:06:05.0: firmware: requesting ipw2200-bss.fw
[   10.980950] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   11.249454] ipw2200: Radio Frequency Kill Switch is On:
[   11.249456] Kill switch must be turned off for wireless networking to work.
[   11.250030] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   11.254634] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   11.254669] tifm_7xx1 0000:06:06.3: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.287860] iTCO_vendor_support: vendor-support=0
[   11.289794] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   11.289926] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   11.290013] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   11.309788] yenta_cardbus 0000:06:06.0: CardBus bridge found [103c:309d]
[   11.309814] yenta_cardbus 0000:06:06.0: Enabling burst memory read transactions
[   11.309821] yenta_cardbus 0000:06:06.0: Using CSCINT to route CSC interrupts to PCI
[   11.309824] yenta_cardbus 0000:06:06.0: Routing CardBus interrupts to PCI
[   11.309831] yenta_cardbus 0000:06:06.0: TI: mfunc 0x01aa1b02, devctl 0x64
[   11.451209] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
[   11.481352] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.481452] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   11.541236] yenta_cardbus 0000:06:06.0: ISA IRQ mask 0x0cf8, PCI irq 22
[   11.541241] yenta_cardbus 0000:06:06.0: Socket status: 30000006
[   11.541245] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   11.541252] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   11.541257] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   11.541486] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   11.541490] yenta_cardbus 0000:06:06.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   11.737732] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.872926] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   11.875295] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   11.876327] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   11.877168] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   11.878191] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   12.345051] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   12.369425] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   12.404028] intel8x0_measure_ac97_clock: measured 55470 usecs
[   12.404032] intel8x0: clocking to 48000
[   12.611067] lp: driver loaded but no devices found
[   12.672354] Adding 6466120k swap on /dev/sda6.  Priority:-1 extents:1 across:6466120k
[   12.693523] EXT3 FS on sda5, internal journal
[   13.164200] type=1505 audit(1279819900.602:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1913
[   13.219693] type=1505 audit(1279819900.654:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1917
[   13.219817] type=1505 audit(1279819900.654:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1917
[   13.219868] type=1505 audit(1279819900.654:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1917
[   13.219914] type=1505 audit(1279819900.654:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1917
[   13.383493] type=1505 audit(1279819900.818:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1922
[   13.383744] type=1505 audit(1279819900.818:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1922
[   13.415143] type=1505 audit(1279819900.850:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1926
[   15.709955] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.709959] Bluetooth: BNEP filters: protocol multicast
[   15.721189] Bridge firewalling registered
[   17.488024] ppdev: user-space parallel port driver
[   18.509919] [drm] Initialized drm 1.1.0 20060810
[   18.518026] pci 0000:00:02.0: power state changed by ACPI to D0
[   18.518037] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.518043] pci 0000:00:02.0: setting latency timer to 64
[   18.518226] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   18.520364] [drm:i915_setparam] *ERROR* unknown parameter 4
[   18.520391] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   20.271447] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   20.564949] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   20.566307] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.148081] eth0: no IPv6 routers present
[   38.183287] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   49.561706] CPU0 attaching NULL sched-domain.
[   49.561787] CPU0 attaching NULL sched-domain.
[   54.411384] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   54.411395] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[   54.411396]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   54.411398]          res 7f/7f:7f:7f:7f:7f/00:00:00:00:00/7f Emask 0x2 (HSM violation)
[   54.411401] ata1.01: status: { DRDY DF DRQ ERR }
[   54.411435] ata1: soft resetting link
[   54.588529] ata1.00: configured for UDMA/100
[   54.604378] ata1.01: configured for MWDMA2
[   54.713780] ata1: EH complete
[   54.825258] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[   54.831727] sd 0:0:0:0: [sda] Write Protect is off
[   54.831730] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.861764] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.884023] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[   54.884128] sd 0:0:0:0: [sda] Write Protect is off
[   54.884131] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   54.896364] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  926.073215] ACPI: EC: GPE storm detected, transactions will use polling mode
[ 1427.312185] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 1520.000080] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1520.000098] ata1.00: cmd ca/00:18:53:70:9d/00:00:00:00:00/e3 tag 0 dma 12288 out
[ 1520.000102]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 1520.000109] ata1.00: status: { DRDY }
[ 1520.000152] ata1: soft resetting link
[ 1520.180788] ata1.00: configured for UDMA/100
[ 1520.196589] ata1.01: configured for MWDMA2
[ 1520.203092] ata1: EH complete
[ 1520.210610] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 1520.214368] sd 0:0:0:0: [sda] Write Protect is off
[ 1520.214375] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1520.221705] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1520.226918] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 1520.227911] sd 0:0:0:0: [sda] Write Protect is off
[ 1520.227917] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1520.236264] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2642.920987] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2642.921007] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 2642.921010]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 2642.921013]          res 7f/7f:7f:7f:7f:7f/00:00:00:00:00/7f Emask 0x2 (HSM violation)
[ 2642.921021] ata1.01: status: { DRDY DF DRQ ERR }
[ 2642.921065] ata1: soft resetting link
[ 2643.100613] ata1.00: configured for UDMA/100
[ 2643.116447] ata1.01: configured for MWDMA2
[ 2643.223176] ata1: EH complete
[ 2643.334634] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 2643.447541] sd 0:0:0:0: [sda] Write Protect is off
[ 2643.447550] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2643.665667] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2643.781071] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 2643.781820] sd 0:0:0:0: [sda] Write Protect is off
[ 2643.781826] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2643.781887] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2747.143636] CPU0 attaching NULL sched-domain.
[ 2747.143769] CPU0 attaching NULL sched-domain.
[ 3039.059400] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3039.059421] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 3039.059424]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3039.059427]          res 7f/7f:7f:7f:7f:7f/00:00:00:00:00/7f Emask 0x2 (HSM violation)
[ 3039.059435] ata1.01: status: { DRDY DF DRQ ERR }
[ 3039.059478] ata1: soft resetting link
[ 3039.236735] ata1.00: configured for UDMA/100
[ 3039.252446] ata1.01: configured for MWDMA2
[ 3039.361585] ata1: EH complete
[ 3039.473200] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 3039.583198] sd 0:0:0:0: [sda] Write Protect is off
[ 3039.583207] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3039.802879] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3039.812964] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 3039.813404] sd 0:0:0:0: [sda] Write Protect is off
[ 3039.813410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3039.814515] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4704.576423] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 4704.576428] ata1.01: ST_FIRST: DRQ=1 with device error, dev_stat 0x7F
[ 4704.576437] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 4704.576438]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4704.576440]          res 7f/7f:7f:7f:7f:7f/00:00:00:00:00/7f Emask 0x2 (HSM violation)
[ 4704.576444] ata1.01: status: { DRDY DF DRQ ERR }
[ 4704.576477] ata1: soft resetting link
[ 4704.765133] ata1.00: configured for UDMA/100
[ 4704.780511] ata1.01: configured for MWDMA2
[ 4704.889450] ata1: EH complete
[ 4705.000901] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 4705.117644] sd 0:0:0:0: [sda] Write Protect is off
[ 4705.117653] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4705.330869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4705.551199] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 4705.557687] sd 0:0:0:0: [sda] Write Protect is off
[ 4705.557695] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 4705.559318] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5954.587325] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 5954.587334] ata1.01: ST_FIRST: DRQ=1 with device error, dev_stat 0x7F
[ 5954.587351] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 5954.587354]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 5954.587357]          res 7f/7f:7f:7f:7f:7f/00:00:00:00:00/7f Emask 0x2 (HSM violation)
[ 5954.587365] ata1.01: status: { DRDY DF DRQ ERR }
[ 5954.587407] ata1: soft resetting link
[ 5954.784944] ata1.00: configured for UDMA/100
[ 5954.800446] ata1.01: configured for MWDMA2
[ 5954.909159] ata1: EH complete
[ 5955.020886] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 5955.130792] sd 0:0:0:0: [sda] Write Protect is off
[ 5955.130801] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5955.350440] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 5955.585941] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 5955.592625] sd 0:0:0:0: [sda] Write Protect is off
[ 5955.592633] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 5955.593459] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7448.910824] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 7448.910835] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 7448.910837]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 7448.910838]          res 7f/7f:7f:7f:7f:7f/00:00:00:00:00/7f Emask 0x2 (HSM violation)
[ 7448.910842] ata1.01: status: { DRDY DF DRQ ERR }
[ 7448.910877] ata1: soft resetting link
[ 7449.088579] ata1.00: configured for UDMA/100
[ 7449.104457] ata1.01: configured for MWDMA2
[ 7449.213031] ata1: EH complete
[ 7449.324501] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 7449.434403] sd 0:0:0:0: [sda] Write Protect is off
[ 7449.434410] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 7449.654229] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 7449.770759] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[ 7449.771452] sd 0:0:0:0: [sda] Write Protect is off
[ 7449.771458] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 7449.771518] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

---

### Post by jkid on 2010-07-25
bump!!

---

### Post by AlphaLexman on 2010-07-25
What part are you worried about, I did not see anything unusual?

---

