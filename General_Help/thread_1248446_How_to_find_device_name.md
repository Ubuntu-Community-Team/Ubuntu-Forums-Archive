---
title: "How to find device name"
date: 2009-08-24
forum: General Help
---

### Post by Jalke on 2009-08-24
Might seem like a simple question, but how do you find out what a device name is?  I've got a digital camera hooked up via firewire.  I need to know what the device name is (to use in VLC).  Thanks.

---

### Post by ibutho on 2009-08-24
You need to plugin the device and then go to Applications -> Accessories -> Terminal and enter the command
```
dmesg
```
There will be a series of lines that tell you that a firewire device was connected and the device name given to it.

---

### Post by Jalke on 2009-08-25
Thanks  for responding.  However, the list is rather long.  Can you tell me which entry records my video camera hooked up to the PCMCIA card firewire port?  Thanks a lot.

[    1.402787] io scheduler anticipatory registered
[    1.402790] io scheduler deadline registered
[    1.402814] io scheduler cfq registered (default)
[    1.402908] pci 0000:01:00.0: Boot video device
[    1.409412] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.409424] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.409857] ACPI: AC Adapter [AC] (on-line)
[    1.438779] ACPI: Battery Slot [BAT0] (battery present)
[    1.438860] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.438863] ACPI: Power Button (FF) [PWRF]
[    1.438917] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.439343] ACPI: Lid Switch [LID]
[    1.439396] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.439401] ACPI: Sleep Button (CM) [SLPB]
[    1.441634] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.441662] processor ACPI_CPU:00: registered as cooling_device0
[    1.441667] ACPI: Processor [CPU] (supports 8 throttling states)
[    1.447245] thermal LNXTHERM:01: registered as thermal_zone0
[    1.449557] ACPI: Thermal Zone [THM0] (27 C)
[    1.449607] isapnp: Scanning for PnP cards...
[    1.802456] isapnp: No Plug & Play device found
[    1.803839] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.804779] serial 00:0a: activated
[    1.804888] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    1.805002] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.805010] serial 0000:00:1f.6: PCI INT B disabled
[    1.805810] brd: module loaded
[    1.806182] loop: module loaded
[    1.806264] Fixed MDIO Bus: probed
[    1.806272] PPP generic driver version 2.4.2
[    1.806340] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.806375] Driver 'sd' needs updating - please use bus_type methods
[    1.806386] Driver 'sr' needs updating - please use bus_type methods
[    1.806466] ata_piix 0000:00:1f.1: version 2.12
[    1.806474] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.806913] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    1.806917] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.806965] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.807074] scsi0 : ata_piix
[    1.807299] scsi1 : ata_piix
[    1.808488] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    1.808491] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    1.972613] ata1.00: ATA-7: HTS421240H9AT00, HACIA70S, max UDMA/100
[    1.972616] ata1.00: 78140160 sectors, multi 16: LBA 
[    1.988552] ata1.00: configured for UDMA/100
[    2.152398] ata2.00: ATAPI: TOSHIBA DVD-ROM SD-R9012, 1121, max UDMA/33
[    2.168349] ata2.00: configured for UDMA/33
[    2.169111] scsi 0:0:0:0: Direct-Access     ATA      HTS421240H9AT00  HACI PQ: 0 ANSI: 5
[    2.169222] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.169242] sd 0:0:0:0: [sda] Write Protect is off
[    2.169245] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.169272] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.169345] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.169361] sd 0:0:0:0: [sda] Write Protect is off
[    2.169364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.169390] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.169394]  sda: sda1 sda2 sda3
[    2.212312] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.212366] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.217689] scsi 1:0:0:0: CD-ROM            TOSHIBA  DVD-ROM SD-R9012 1121 PQ: 0 ANSI: 5
[    2.225296] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.225300] Uniform CD-ROM driver Revision: 3.20
[    2.225404] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.225445] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.226189] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.226599] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    2.227029] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    2.227033] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    2.227065] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.227069] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.227150] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.231053] ehci_hcd 0000:00:1d.7: debug port 1
[    2.231060] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.231070] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    2.244024] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.244110] usb usb1: configuration #1 chosen from 1 choice
[    2.244143] hub 1-0:1.0: USB hub found
[    2.244152] hub 1-0:1.0: 6 ports detected
[    2.244288] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.244309] uhci_hcd: USB Universal Host Controller Interface driver
[    2.244702] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.244709] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.244716] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.244720] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.244769] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.244790] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    2.244887] usb usb2: configuration #1 chosen from 1 choice
[    2.244919] hub 2-0:1.0: USB hub found
[    2.244927] hub 2-0:1.0: 2 ports detected
[    2.245390] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    2.245806] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    2.245810] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.245816] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.245820] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.245870] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.245890] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    2.245985] usb usb3: configuration #1 chosen from 1 choice
[    2.246014] hub 3-0:1.0: USB hub found
[    2.246021] hub 3-0:1.0: 2 ports detected
[    2.246115] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.246121] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.246125] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.246171] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.246192] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    2.246278] usb usb4: configuration #1 chosen from 1 choice
[    2.246306] hub 4-0:1.0: USB hub found
[    2.246314] hub 4-0:1.0: 2 ports detected
[    2.246473] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.252759] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.252766] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.252897] mice: PS/2 mouse device common for all mice
[    2.253065] rtc_cmos 00:06: RTC can wake from S4
[    2.253126] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.253143] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    2.253229] device-mapper: uevent: version 1.0.3
[    2.253361] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.253417] device-mapper: multipath: version 1.0.5 loaded
[    2.253420] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.253531] EISA: Probing bus 0 at eisa.0
[    2.253538] Cannot allocate resource for EISA slot 1
[    2.253541] Cannot allocate resource for EISA slot 2
[    2.253544] Cannot allocate resource for EISA slot 3
[    2.253546] Cannot allocate resource for EISA slot 4
[    2.253549] Cannot allocate resource for EISA slot 5
[    2.253551] Cannot allocate resource for EISA slot 6
[    2.253554] Cannot allocate resource for EISA slot 7
[    2.253557] Cannot allocate resource for EISA slot 8
[    2.253559] EISA: Detected 0 cards.
[    2.253628] cpuidle: using governor ladder
[    2.253707] cpuidle: using governor menu
[    2.254403] TCP cubic registered
[    2.254549] NET: Registered protocol family 10
[    2.255082] lo: Disabled Privacy Extensions
[    2.255497] NET: Registered protocol family 17
[    2.255515] Bluetooth: L2CAP ver 2.11
[    2.255518] Bluetooth: L2CAP socket layer initialized
[    2.255521] Bluetooth: SCO (Voice Link) ver 0.6
[    2.255523] Bluetooth: SCO socket layer initialized
[    2.255553] Bluetooth: RFCOMM socket layer initialized
[    2.255561] Bluetooth: RFCOMM TTY layer initialized
[    2.255563] Bluetooth: RFCOMM ver 1.10
[    2.256055] IO APIC resources could be not be allocated.
[    2.256089] Using IPI No-Shortcut mode
[    2.256195] registered taskstats version 1
[    2.256333]   Magic number: 5:835:397
[    2.256385] mem random: hash matches
[    2.256440] rtc_cmos 00:06: setting system clock to 2009-08-25 20:22:00 UTC (1251231720)
[    2.256444] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.256446] EDD information not available.
[    2.256819] Freeing unused kernel memory: 532k freed
[    2.256952] Write protecting the kernel text: 4116k
[    2.256996] Write protecting the kernel read-only data: 1524k
[    2.260624] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.790340] Floppy drive(s): fd0 is 1.44M
[    2.807068] FDC 0 is a National Semiconductor PC87306
[    3.215581] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    3.215585] Copyright (c) 1999-2006 Intel Corporation.
[    3.215647] e1000 0000:02:01.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.466732] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:11:25:14:54:a4
[    3.532796] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.781725] Marking TSC unstable due to TSC halts in idle
[    4.157710] PM: Starting manual resume from disk
[    4.157715] PM: Resume from partition 8:2
[    4.157717] PM: Checking hibernation image.
[    4.157931] PM: Resume from disk failed.
[    4.213061] kjournald starting.  Commit interval 5 seconds
[    4.213073] EXT3-fs: mounted filesystem with ordered data mode.
[   12.458028] udev: starting version 141
[   12.616410] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.346939] Linux agpgart interface v0.103
[   13.371066] intel_rng: FWH not detected
[   13.473574] ieee80211_crypt: registered algorithm 'NULL'
[   13.480711] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   13.480715] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   13.481931] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   13.953893] yenta_cardbus 0000:02:00.0: CardBus bridge found [1014:0552]
[   13.953911] yenta_cardbus 0000:02:00.0: Using INTVAL to route CSC interrupts to PCI
[   13.953915] yenta_cardbus 0000:02:00.0: Routing CardBus interrupts to PCI
[   13.953920] yenta_cardbus 0000:02:00.0: TI: mfunc 0x01d21b22, devctl 0x64
[   14.006398] Non-volatile memory driver v1.2
[   14.168448] irda_init()
[   14.168465] NET: Registered protocol family 23
[   14.178063] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.185158] yenta_cardbus 0000:02:00.0: ISA IRQ mask 0x04b8, PCI irq 11
[   14.185163] yenta_cardbus 0000:02:00.0: Socket status: 30000020
[   14.185170] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   14.185175] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x8fff: clean.
[   14.186569] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   14.186573] yenta_cardbus 0000:02:00.0: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   14.187130] yenta_cardbus 0000:02:00.1: CardBus bridge found [1014:0552]
[   14.187147] yenta_cardbus 0000:02:00.1: Using INTVAL to route CSC interrupts to PCI
[   14.187149] yenta_cardbus 0000:02:00.1: Routing CardBus interrupts to PCI
[   14.187155] yenta_cardbus 0000:02:00.1: TI: mfunc 0x01d21b22, devctl 0x64
[   14.226434] parport_pc 00:0b: reported by Plug and Play ACPI
[   14.226476] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   14.240683] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input6
[   14.244337] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   14.260591] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   14.278529] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   14.316499] iTCO_vendor_support: vendor-support=0
[   14.319347] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   14.319480] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   14.319578] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.353379] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   14.353383] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   14.410564] ppdev: user-space parallel port driver
[   14.416976] yenta_cardbus 0000:02:00.1: ISA IRQ mask 0x0438, PCI irq 11
[   14.416981] yenta_cardbus 0000:02:00.1: Socket status: 30000086
[   14.416989] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   14.416994] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x8fff: clean.
[   14.418279] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   14.418283] yenta_cardbus 0000:02:00.1: pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   14.421579] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   14.423424] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   14.423489] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[   14.433794] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   14.433798] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   14.433801] thinkpad_acpi: ThinkPad BIOS 1RETDJWW (3.15 ), EC 1RHT71WW-3.04
[   14.433804] thinkpad_acpi: IBM ThinkPad T41 , model 2373S19
[   14.438150] Registered led device: tpacpi::thinklight
[   14.438430] Registered led device: tpacpi::power
[   14.438473] Registered led device: tpacpi:orange:batt
[   14.438520] Registered led device: tpacpi:green:batt
[   14.438562] Registered led device: tpacpi::dock_active
[   14.438605] Registered led device: tpacpi::bay_active
[   14.438647] Registered led device: tpacpi::dock_batt
[   14.438717] Registered led device: tpacpi::unknown_led
[   14.438762] Registered led device: tpacpi::standby
[   14.440871] input: ThinkPad Extra Buttons as /devices/virtual/input/input7
[   14.448889] nsc-ircc 00:0c: activated
[   14.448895] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   14.449062] nsc-ircc, chip->init
[   14.449070] nsc-ircc, Found chip at base=0x02e
[   14.449094] nsc-ircc, driver loaded (Dag Brattli)
[   14.660273] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
[   14.661175] IrDA: Registered device irda0
[   14.661179] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   14.820056] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   14.820103] pci 0000:03:00.0: reg 14 32bit mmio: [0x000000-0x0000ff]
[   14.820123] pci 0000:03:00.0: reg 20 io port: [0xfce0-0xfcff]
[   14.820148] pci 0000:03:00.0: supports D1 D2
[   14.820151] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[   14.820157] pci 0000:03:00.0: PME# disabled
[   14.820201] pci 0000:03:00.1: reg 14 32bit mmio: [0x000000-0x0000ff]
[   14.820221] pci 0000:03:00.1: reg 20 io port: [0xfce0-0xfcff]
[   14.820243] pci 0000:03:00.1: supports D1 D2
[   14.820245] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[   14.820250] pci 0000:03:00.1: PME# disabled
[   14.820289] pci 0000:03:00.2: reg 10 32bit mmio: [0x000000-0x0000ff]
[   14.820297] pci 0000:03:00.2: reg 14 32bit mmio: [0x000000-0x0000ff]
[   14.820335] pci 0000:03:00.2: supports D1 D2
[   14.820338] pci 0000:03:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[   14.820343] pci 0000:03:00.2: PME# disabled
[   14.820383] pci 0000:03:00.3: reg 10 32bit mmio: [0x000000-0x0007ff]
[   14.820392] pci 0000:03:00.3: reg 14 io port: [0x00-0x7f]
[   14.820434] pci 0000:03:00.3: PME# supported from D0 D3hot D3cold
[   14.820439] pci 0000:03:00.3: PME# disabled
[   14.820660] uhci_hcd 0000:03:00.0: enabling device (0000 -> 0003)
[   14.820672] uhci_hcd 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   14.820686] uhci_hcd 0000:03:00.0: UHCI Host Controller
[   14.820878] uhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 5
[   14.820913] uhci_hcd 0000:03:00.0: irq 11, io base 0x00004080
[   14.821073] usb usb5: configuration #1 chosen from 1 choice
[   14.821151] hub 5-0:1.0: USB hub found
[   14.821167] hub 5-0:1.0: 2 ports detected
[   14.821461] uhci_hcd 0000:03:00.1: enabling device (0000 -> 0003)
[   14.821470] uhci_hcd 0000:03:00.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   14.821478] uhci_hcd 0000:03:00.1: UHCI Host Controller
[   14.821853] uhci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 6
[   14.821880] uhci_hcd 0000:03:00.1: irq 11, io base 0x000040a0
[   14.822435] usb usb6: configuration #1 chosen from 1 choice
[   14.822516] hub 6-0:1.0: USB hub found
[   14.822531] hub 6-0:1.0: 2 ports detected
[   14.822839] ehci_hcd 0000:03:00.2: enabling device (0000 -> 0002)
[   14.822850] ehci_hcd 0000:03:00.2: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   14.822992] ehci_hcd 0000:03:00.2: EHCI Host Controller
[   14.823117] ehci_hcd 0000:03:00.2: new USB bus registered, assigned bus number 7
[   14.823175] ehci_hcd 0000:03:00.2: irq 11, io mem 0xc4000a00
[   14.832416] ehci_hcd 0000:03:00.2: USB 2.0 started, EHCI 1.00
[   14.832603] usb usb7: configuration #1 chosen from 1 choice
[   14.832679] hub 7-0:1.0: USB hub found
[   14.832693] hub 7-0:1.0: 4 ports detected
[   14.847903] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   14.848926] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   14.849360] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   14.849728] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   14.850249] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   14.994688] ohci1394 0000:03:00.3: enabling device (0080 -> 0083)
[   14.994704] ohci1394 0000:03:00.3: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   14.994714] ohci1394 0000:03:00.3: setting latency timer to 64
[   15.046568] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c4000000-c40007ff]  Max Packet=[2]  IR/IT contexts=[4/4]
[   15.051563] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[   15.203327] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   15.203404] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   15.211440] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   15.211446] serio: Synaptics pass-through port at isa0060/serio1/input0
[   15.248160] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   15.305090] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.306089] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.306535] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.306903] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.307424] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   16.128028] intel8x0_measure_ac97_clock: measured 55374 usecs
[   16.128031] intel8x0: clocking to 48000
[   16.264044] usb 5-2: new full speed USB device using uhci_hcd and address 2
[   16.281535] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   16.291971] lp0: using parport0 (interrupt-driven).
[   16.343626] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[4200000000c20000]
[   16.366790] Adding 1461904k swap on /dev/sda2.  Priority:-1 extents:1 across:1461904k
[   16.420600] usb 5-2: configuration #1 chosen from 1 choice
[   16.520436] usbcore: registered new interface driver usbserial
[   16.520452] USB Serial support registered for generic
[   16.520484] usbcore: registered new interface driver usbserial_generic
[   16.520486] usbserial: USB Serial Driver core
[   16.663859] USB Serial support registered for Sierra USB modem
[   16.663889] sierra 5-2:1.0: Sierra USB modem converter detected
[   16.666106] usb 5-2: Sierra USB modem converter now attached to ttyUSB0
[   16.666155] usb 5-2: Sierra USB modem converter now attached to ttyUSB1
[   16.666201] usb 5-2: Sierra USB modem converter now attached to ttyUSB2
[   16.666217] usbcore: registered new interface driver sierra
[   16.666220] sierra: v.1.3.2:USB Driver for Sierra Wireless USB modems
[   16.924175] EXT3 FS on sda1, internal journal
[   17.582958] psmouse serio2: ID: 10 00 64<5>type=1505 audit(1251188536.411:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2075
[   18.236547] type=1505 audit(1251188536.479:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2079
[   18.236749] type=1505 audit(1251188536.479:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2079
[   18.236818] type=1505 audit(1251188536.479:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2079
[   18.236874] type=1505 audit(1251188536.479:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2079
[   18.437966] type=1505 audit(1251188536.679:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2084
[   18.438308] type=1505 audit(1251188536.679:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2084
[   18.476796] type=1505 audit(1251188536.719:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2088
[   19.050128] RPC: Registered udp transport module.
[   19.050132] RPC: Registered tcp transport module.
[   19.230200] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   20.917786] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   20.944531] NFSD: starting 90-second grace period
[   21.038068] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   21.254751] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   22.826465] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.826469] Bluetooth: BNEP filters: protocol multicast
[   22.886189] Bridge firewalling registered
[   24.518645] pci 0000:01:00.0: power state changed by ACPI to D0
[   24.518659] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   24.956045] [drm] Initialized drm 1.1.0 20060810
[   25.024396] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   25.369078] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   25.369099] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   25.369137] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   25.943439] [drm] Setting GART location based on new memory map
[   25.943448] [drm] Loading R100 Microcode
[   25.943502] [drm] writeback test succeeded in 2 usecs
[   28.757011] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.812112] eth1: no IPv6 routers present
[   87.116048] Clocksource tsc unstable (delta = -189280380 ns)
[  217.536274] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[  217.812047] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[  217.812160] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[  217.885806] ieee1394: raw1394: /dev/raw1394 device initialized
[  217.942089] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.
[ 1005.200160] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 1005.200178] ieee1394: Node paused: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 1008.260057] ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 1016.832696] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 1017.672067] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 1018.192070] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 1018.751006] ohci1394: fw-host0: isochronous cycle too long
[ 1019.347736] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1019.347799] ieee1394: Node paused: ID:BUS[0-00:1023]  GUID[4200000000c20000]
[ 1019.824052] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 1019.946998] ohci1394: fw-host0: isochronous cycle too long
[ 1020.543709] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1020.643122] ohci1394: fw-host0: isochronous cycle too long
[ 1021.239813] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1021.338868] ohci1394: fw-host0: isochronous cycle too long
[ 1021.935613] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1022.034743] ohci1394: fw-host0: isochronous cycle too long
[ 1022.455240] ohci1394: fw-host0: isochronous cycle too long
[ 1023.051537] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1023.150985] ohci1394: fw-host0: isochronous cycle too long
[ 1023.524076] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 1024.320986] ohci1394: fw-host0: isochronous cycle too long
[ 1024.917422] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1025.392060] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 1025.732051] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 1026.038225] ohci1394: fw-host0: isochronous cycle too long
[ 1026.634234] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1026.733597] ohci1394: fw-host0: isochronous cycle too long
[ 1027.329647] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1027.428468] ohci1394: fw-host0: isochronous cycle too long
[ 1028.025219] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1028.500071] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 1028.628464] ohci1394: fw-host0: isochronous cycle too long
[ 1029.121172] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 1030.416734] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 1030.416844] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 1030.416861] ieee1394: Node reactivated: ID:BUS[0-01:1023]  GUID[4200000000c20000]
[ 1109.997490] PPP BSD Compression module registered
[ 1110.027377] PPP Deflate Compression module registered
[ 2648.228361] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 2648.228379] ieee1394: Node paused: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 2651.288067] ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 2685.496190] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 2685.774157] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 2685.774267] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 6006.872637] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[ 6006.872654] ieee1394: Node paused: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 6009.940065] ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 6292.804167] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[ 6293.086324] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 6293.086437] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 6294.334577] ohci1394: fw-host0: isochronous cycle too long
[ 6294.930075] ohci1394: fw-host0: AT dma reset ctx=0, aborting transmission
[ 6294.930113] ieee1394: Node paused: ID:BUS[0-01:1023]  GUID[4200000000c20000]
[ 6294.930126] ieee1394: Node paused: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 6295.406643] ieee1394: Node reactivated: ID:BUS[0-00:1023]  GUID[00804580a168e5fa]
[ 6295.406746] ieee1394: Node reactivated: ID:BUS[0-01:1023]  GUID[4200000000c20000]

---

### Post by Jalke on 2009-08-25
I tried using the /dev/raw1394 entry but this didn't appear to work (although I guess this could be because I'm new to VLC).  Would that be the entry?

---

### Post by loomsen on 2009-08-25
Hi.

there are different tools to find hardware on your pc, like 
lspci : shows information on pci devices
lsusb : ---------"---------- usb --"--
lsscsi : ...
lshw

I usually use 
lshal
if you have HAL enabled (the hardware abstraction layer)

---

