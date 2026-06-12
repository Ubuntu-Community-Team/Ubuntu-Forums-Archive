---
title: "PC is not waking up from hibernating"
date: 2011-12-20
forum: General Help
---

### Post by cje on 2011-12-20
I've 11.10 on a workstation. 
After some time (10-20minutes) the PC is going into hibernating or the HD is turned off. I don't know exactly what's happening. After that it's impossible to "wake it up". 

I've deactivated all power options w/o any success. 

Does anybody know what to do?

---

### Post by cje on 2011-12-23
Anyone?

---

### Post by audiomick on 2011-12-23
If we assume that computer is going into hibernation, maybe your swap is too small. If you want hibernation to work, the swap partition should be a bit bigger than the amount of RAM you have.

It puzzles me that you can't prevent the computer going to sleep. That should be possible, I am sure, but I don't have an 11.10 install to check how this is done, I am sorry.

---

### Post by bobsageek on 2011-12-23
Can you post the output from dmesg from the last time it failed to wake up to your current reboot? If it's actually going to sleep/hibernating there will be events logged there so we can know where to start?

---

### Post by pretty_whistle on 2011-12-23
There is a bug where it won't resume after suspend.  I wonder if it affects hibernate too.  If so, do this:

> Treat the screen like you're looking at as the login screen, even if you have it set to automatic login.  Now assume the cursor is in the password field and type in your password in, hit enter.That's it.

---

### Post by cje on 2011-12-25
@audiomick
thanks for your suggestion. Do you have any link with a guide to expand the swap?

@pretty_whistle
thanks for your suggestion. Unfortunately it doesn't work

@bobsageek
I'm not sure if this is of any help. As the computer is going into hibernate it has to be restarted. Anyway, this is the dmesg just after restart:
```

[    0.294824] PCI: pci_cache_line_size set to 64 bytes
[    0.294891] reserve RAM buffer: 000000003fe70000 - 000000003fffffff 
[    0.295072] NetLabel: Initializing
[    0.295077] NetLabel:  domain hash size = 128
[    0.295079] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.295096] NetLabel:  unlabeled traffic allowed by default
[    0.295285] hpet clockevent registered
[    0.295292] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.295300] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.295308] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.300101] Switching to clocksource hpet
[    0.303959] Switched to NOHz mode on CPU #0
[    0.310139] AppArmor: AppArmor Filesystem Enabled
[    0.310190] pnp: PnP ACPI init
[    0.310217] ACPI: bus type pnp registered
[    0.313951] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.313957] pnp 00:00: [mem 0x00100000-0x00ffffff]
[    0.313960] pnp 00:00: [mem 0x01000000-0x3fe6ffff]
[    0.313964] pnp 00:00: [mem 0x000c0000-0x000fffff]
[    0.313967] pnp 00:00: [mem 0xfec00000-0xfec0ffff]
[    0.313971] pnp 00:00: [mem 0xfee00000-0xfee0ffff]
[    0.313974] pnp 00:00: [mem 0xfed20000-0xfed8ffff]
[    0.313977] pnp 00:00: [mem 0xfecf0000-0xfecf0fff]
[    0.313981] pnp 00:00: [mem 0xffb00000-0xffbfffff]
[    0.313984] pnp 00:00: [mem 0xffc00000-0xffffffff]
[    0.314081] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.314087] system 00:00: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.314092] system 00:00: [mem 0x01000000-0x3fe6ffff] could not be reserved
[    0.314096] system 00:00: [mem 0x000c0000-0x000fffff] could not be reserved
[    0.314101] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.314106] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.314110] system 00:00: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.314114] system 00:00: [mem 0xfecf0000-0xfecf0fff] has been reserved
[    0.314119] system 00:00: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.314123] system 00:00: [mem 0xffc00000-0xffffffff] has been reserved
[    0.314130] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.315725] pnp 00:01: [bus 00-ff]
[    0.315731] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.315735] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.315738] pnp 00:01: [io  0x0d00-0xffff window]
[    0.315742] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.315746] pnp 00:01: [mem 0x000c0000-0x00000000 window]
[    0.315750] pnp 00:01: [mem 0x80000000-0xfebfffff window]
[    0.315812] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.319068] pnp 00:02: [io  0x0080-0x009f]
[    0.319073] pnp 00:02: [io  0x0000-0x001f]
[    0.319076] pnp 00:02: [io  0x00c0-0x00df]
[    0.319080] pnp 00:02: [dma 4]
[    0.319133] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.319239] pnp 00:03: [io  0x00f0-0x00ff]
[    0.319260] pnp 00:03: [irq 13]
[    0.319310] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.319415] pnp 00:04: [io  0x0061]
[    0.319459] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.319565] pnp 00:05: [io  0x0070-0x007f]
[    0.319575] pnp 00:05: [irq 8]
[    0.319622] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.321805] pnp 00:06: [io  0x0060]
[    0.321810] pnp 00:06: [io  0x0064]
[    0.321820] pnp 00:06: [irq 1]
[    0.321884] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.325810] pnp 00:07: [io  0x03f8-0x03ff]
[    0.325821] pnp 00:07: [irq 4]
[    0.326056] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.329434] pnp 00:08: [io  0x0378-0x037f]
[    0.329439] pnp 00:08: [io  0x0778-0x077f]
[    0.329450] pnp 00:08: [irq 7]
[    0.329454] pnp 00:08: [dma 0 disabled]
[    0.329985] pnp 00:08: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.331773] pnp 00:09: [io  0x0062-0x0063]
[    0.331778] pnp 00:09: [io  0x0065-0x006f]
[    0.331782] pnp 00:09: [io  0x00e0-0x00ef]
[    0.331785] pnp 00:09: [io  0x0800-0x085f]
[    0.331788] pnp 00:09: [io  0x0c00-0x0c7f]
[    0.331791] pnp 00:09: [io  0x0860-0x08ff]
[    0.331872] system 00:09: [io  0x0800-0x085f] has been reserved
[    0.331878] system 00:09: [io  0x0c00-0x0c7f] has been reserved
[    0.331882] system 00:09: [io  0x0860-0x08ff] has been reserved
[    0.331889] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.332659] pnp: PnP ACPI: found 10 devices
[    0.332664] ACPI: ACPI bus type pnp unregistered
[    0.332671] PnPBIOS: Disabled by ACPI PNP
[    0.370352] PCI: max bus depth: 1 pci_try_num: 2
[    0.370373] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.370379] pci 0000:00:1e.0:   bridge window [io  0xd000-0xdfff]
[    0.370387] pci 0000:00:1e.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.370393] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.370414] pci 0000:00:1e.0: setting latency timer to 64
[    0.370420] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.370424] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.370428] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.370432] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.370435] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.370439] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
[    0.370509] NET: Registered protocol family 2
[    0.370618] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.370996] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.371650] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.371983] TCP: Hash tables configured (established 131072 bind 65536)
[    0.371988] TCP reno registered
[    0.371997] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.372057] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.372241] NET: Registered protocol family 1
[    0.372273] pci 0000:00:02.0: Boot video device
[    0.372382] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    0.372391] PCI: CLS 64 bytes, default 64
[    0.372478] Simple Boot Flag at 0x7a set to 0x1
[    0.372907] audit: initializing netlink socket (disabled)
[    0.372925] type=2000 audit(1324831984.368:1): initialized
[    0.402601] Trying to unpack rootfs image as initramfs...
[    0.444610] highmem bounce pool size: 64 pages
[    0.444621] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.456267] VFS: Disk quotas dquot_6.5.2
[    0.456387] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.464526] fuse init (API version 7.16)
[    0.464750] msgmni has been set to 1704
[    0.472499] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.472573] io scheduler noop registered
[    0.472577] io scheduler deadline registered
[    0.472620] io scheduler cfq registered (default)
[    0.472836] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.472886] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.473114] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.473125] ACPI: Power Button [VBTN]
[    0.473205] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.473211] ACPI: Power Button [PWRF]
[    0.473250] ACPI: acpi_idle registered with cpuidle
[    0.509772] ERST: Table is not found!
[    0.512436] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.532824] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.532878] isapnp: Scanning for PnP cards...
[    0.626911] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.648864] Linux agpgart interface v0.103
[    0.648955] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    0.648992] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.649131] agpgart-intel 0000:00:00.0: detected 1024K stolen memory
[    0.649306] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[    0.651404] brd: module loaded
[    0.700543] loop: module loaded
[    0.700802] ata_piix 0000:00:1f.1: version 2.13
[    0.700840] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.700899] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.701382] scsi0 : ata_piix
[    0.704243] scsi1 : ata_piix
[    0.704352] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.704357] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.705029] Fixed MDIO Bus: probed
[    0.705076] PPP generic driver version 2.4.2
[    0.705189] tun: Universal TUN/TAP device driver, 1.6
[    0.705193] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.705376] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.705431] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.705458] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.705464] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.705549] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.705594] ehci_hcd 0000:00:1d.7: debug port 1
[    0.709492] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.712180] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[    0.732195] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.732487] hub 1-0:1.0: USB hub found
[    0.732497] hub 1-0:1.0: 8 ports detected
[    0.732623] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.732650] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732734] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.732749] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.732754] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.732853] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.732912] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    0.733146] hub 2-0:1.0: USB hub found
[    0.733155] hub 2-0:1.0: 2 ports detected
[    0.733269] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.733282] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.733287] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.733375] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.733423] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    0.733651] hub 3-0:1.0: USB hub found
[    0.733660] hub 3-0:1.0: 2 ports detected
[    0.733758] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.733769] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.733774] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.733870] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    0.733906] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
[    0.734139] hub 4-0:1.0: USB hub found
[    0.734149] hub 4-0:1.0: 2 ports detected
[    0.734310] i8042: PNP: PS/2 Controller [PNP0303:KBD] at 0x60,0x64 irq 1
[    0.734314] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.735163] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.740356] mousedev: PS/2 mouse device common for all mice
[    0.740650] rtc_cmos 00:05: RTC can wake from S4
[    0.740793] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.740827] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    0.741030] device-mapper: uevent: version 1.0.3
[    0.741215] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.741289] EISA: Probing bus 0 at eisa.0
[    0.741331] EISA: Detected 0 cards.
[    0.741345] cpufreq-nforce2: No nForce2 chipset.
[    0.741350] cpuidle: using governor ladder
[    0.741353] cpuidle: using governor menu
[    0.741355] EFI Variables Facility v0.08 2004-May-17
[    0.741784] TCP cubic registered
[    0.742059] NET: Registered protocol family 10
[    0.742966] NET: Registered protocol family 17
[    0.743009] Registering the dns_resolver key type
[    0.743047] Using IPI No-Shortcut mode
[COLOR="Red"][    0.743248] PM: Hibernation image not present or could not be loaded.[/COLOR]
[    0.743268] registered taskstats version 1
[    0.764106] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.908450] ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX310EE, SDK3, max UDMA/33
[    1.017569] ata1.00: ATA-7: SAMSUNG SP0802N/P, TK300-08, max UDMA/100
[    1.017576] ata1.00: 156250000 sectors, multi 8: LBA48 
[    1.032534] ata2.00: configured for UDMA/33
[    1.040527] ata1.00: configured for UDMA/100
[    1.091699] usb 1-2: new high speed USB device number 2 using ehci_hcd
[    1.151873] isapnp: No Plug & Play device found
[    1.152106] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0802N/ TK30 PQ: 0 ANSI: 5
[    1.152417] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.152747] sd 0:0:0:0: [sda] 156250000 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.152855] sd 0:0:0:0: [sda] Write Protect is off
[    1.152861] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.152905] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.154104] scsi 1:0:0:0: CD-ROM            SONY     CDRWDVD CRX310EE SDK3 PQ: 0 ANSI: 5
[    1.157525] sr0: scsi3-mmc drive: 0x/48x writer cd/rw xa/form2 cdda tray
[    1.157533] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.157753] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.157887] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.197446]  sda: sda1 sda2 < sda5 >
[    1.198050] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.339809] Freeing initrd memory: 13328k freed
[    1.365421]   Magic number: 7:951:894
[    1.365532] rtc_cmos 00:05: setting system clock to 2011-12-25 16:53:05 UTC (1324831985)
[    1.365561] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.365564] EDD information not available.
[    1.365745] Freeing unused kernel memory: 696k freed
[    1.366342] Write protecting the kernel text: 5336k
[    1.366387] Write protecting the kernel read-only data: 2192k
[    1.372087] Refined TSC clocksource calibration: 2526.999 MHz.
[    1.372097] Switching to clocksource tsc
[    1.409395] udevd[81]: starting version 173
[    1.777252] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.777258] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.777325] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.845967] e100 0000:01:08.0: PME# disabled
[    1.847913] e100 0000:01:08.0: eth0: addr 0xfeaff000, irq 20, MAC addr 00:13:20:de:44:14
[    1.880086] usb 3-1: new full speed USB device number 2 using uhci_hcd
[    2.060250] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.060258] EXT4-fs (sda1): write access will be enabled during recovery
[    2.304036] usb 3-2: new low speed USB device number 3 using uhci_hcd
[    2.504261] input: Dell Dell USB Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
[    2.505192] generic-usb 0003:413C:3200.0001: input,hidraw0: USB HID v1.10 Mouse [Dell Dell USB Mouse] on usb-0000:00:1d.1-2/input0
[    2.505625] usbcore: registered new interface driver usbhid
[    2.505631] usbhid: USB HID core driver
[    4.854352] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.854376] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525528
[    4.854422] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525067
[    4.854578] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 132376
[    4.875414] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 139917
[    4.875547] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 145314
[    4.875695] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525748
[    4.875750] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 172206
[    4.906342] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 157499
[    4.937323] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 189299
[    4.943720] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 115
[    4.943845] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 55
[    4.956472] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262284
[    4.956622] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262276
[    4.956655] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262267
[    4.956681] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 262265
[    4.968759] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660066
[    4.968808] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660065
[    4.968838] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660064
[    4.968864] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660058
[    4.968887] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660055
[    4.968909] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660054
[    4.978868] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660052
[    4.978899] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660050
[    4.978922] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660049
[    4.978947] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660048
[    4.978973] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660047
[    4.978996] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660045
[    4.979025] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660043
[    4.979048] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660041
[    4.979071] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660038
[    4.979094] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660037
[    4.979116] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660036
[    4.979138] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 660033
[    4.979163] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 133600
[    4.979223] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 133547
[    4.979278] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 133544
[    4.979305] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 133531
[    4.979336] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 133501
[    4.979363] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 133474
[    4.979394] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 526344
[    4.988987] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525375
[    4.989037] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525081
[    4.989062] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525069
[    4.996265] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524947
[    4.996499] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524830
[    4.996539] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 133216
[    4.996565] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 132801
[    4.996589] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525068
[    4.996611] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525063
[    4.996634] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525066
[    4.996657] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524943
[    4.996680] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525065
[    4.996702] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525064
[    4.996725] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525040
[    4.996748] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525056
[    4.996773] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525004
[    4.996796] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524999
[    4.996818] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524998
[    4.996840] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524988
[    4.996868] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524915
[    4.996891] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524925
[    4.996914] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524987
[    4.996936] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524816
[    4.996962] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524895
[    4.996987] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524800
[    5.019209] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 524471
[    5.023885] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525858
[    5.023939] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 525403
[    5.024131] EXT4-fs (sda1): 68 orphan inodes deleted
[    5.024135] EXT4-fs (sda1): recovery complete
[    5.136576] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   20.976990] udevd[277]: starting version 173
[   21.060086] lp: driver loaded but no devices found
[   21.077136] Adding 1485976k swap on /dev/sda5.  Priority:-1 extents:1 across:1485976k 
[   21.330574] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   21.863247] [drm] Initialized drm 1.1.0 20060810
[   21.867872] type=1400 audit(1324828405.996:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=465 comm="apparmor_parser"
[   21.868597] type=1400 audit(1324828406.000:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=465 comm="apparmor_parser"
[   21.868981] type=1400 audit(1324828406.000:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=465 comm="apparmor_parser"
[   22.093909] parport_pc 00:08: reported by Plug and Play ACPI
[   22.093963] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   22.101133] intel_rng: Firmware space is locked read-only. If you can't or
[   22.101138] intel_rng: don't want to disable this in firmware setup, and if
[   22.101140] intel_rng: you are certain that your system has a functional
[   22.101142] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   22.115034] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.184354] lp0: using parport0 (interrupt-driven).
[   22.277272] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.280172] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   22.280644] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.459925] Linux video capture interface: v2.00
[   22.491204] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0804)
[   22.495036] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.495048] i915 0000:00:02.0: setting latency timer to 64
[   22.610965] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   22.610972] [drm] Driver supports precise vblank timestamp query.
[   22.611036] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   22.778422] input: UVC Camera (046d:0804) as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input4
[   22.778760] usbcore: registered new interface driver uvcvideo
[   22.778766] USB Video Class driver (v1.1.0)
[   22.831765] [drm] initialized overlay support
[   23.109060] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   23.415429] init: failsafe main process (651) killed by TERM signal
[   23.679339] type=1400 audit(1324828407.808:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=721 comm="apparmor_parser"
[   23.727616] type=1400 audit(1324828407.856:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=722 comm="apparmor_parser"
[   23.738232] type=1400 audit(1324828407.868:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=727 comm="apparmor_parser"
[   23.746777] type=1400 audit(1324828407.876:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=727 comm="apparmor_parser"
[   23.747185] type=1400 audit(1324828407.876:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=727 comm="apparmor_parser"
[   23.791335] type=1400 audit(1324828407.920:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=728 comm="apparmor_parser"
[   23.827207] type=1400 audit(1324828407.956:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=728 comm="apparmor_parser"
[   23.859279] usbcore: registered new interface driver snd-usb-audio
[   24.150292] ppdev: user-space parallel port driver
[   24.407688] init: apport pre-start process (841) terminated with status 1
[   24.518341] init: apport post-stop process (885) terminated with status 1
[   24.601121] Bluetooth: Core ver 2.16
[   24.603882] NET: Registered protocol family 31
[   24.603887] Bluetooth: HCI device and connection manager initialized
[   24.603892] Bluetooth: HCI socket layer initialized
[   24.603895] Bluetooth: L2CAP socket layer initialized
[   24.607553] Bluetooth: SCO socket layer initialized
[   24.667558] Bluetooth: RFCOMM TTY layer initialized
[   24.667569] Bluetooth: RFCOMM socket layer initialized
[   24.667572] Bluetooth: RFCOMM ver 1.11
[   24.809062] fbcon: inteldrmfb (fb0) is primary device
[   24.812577] Console: switching to colour frame buffer device 210x65
[   24.812639] fb0: inteldrmfb frame buffer device
[   24.812642] drm: registered panic notifier
[   24.812708] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.812807] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   24.812859] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   24.903152] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.903159] Bluetooth: BNEP filters: protocol multicast
[   25.020693] init: gdm main process (974) killed by TERM signal
[   25.300032] intel8x0_measure_ac97_clock: measured 52502 usecs (2530 samples)
[   25.300039] intel8x0: clocking to 48000
[   26.569288] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   26.854829] init: plymouth-stop pre-start process (1165) terminated with status 1
[   29.748533] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   33.248012] eth0: no IPv6 routers present
[ 2838.263310] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[ 2838.264015] render error detected, EIR: 0x00000010
[ 2838.264015] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
[ 2838.264015] render error detected, EIR: 0x00000010

```

---

### Post by audiomick on 2011-12-25
> **cje said:**
> @audiomick
thanks for your suggestion. Do you have any link with a guide to expand the swap?

Before we get on to that, how big is your swap, and how much RAM do you have?

On way to find out is to look at the "resources" tab of the system monitor.

---

### Post by bobsageek on 2011-12-26
> **cje said:**
> @audiomick
thanks for your suggestion. Do you have any link with a guide to expand the swap?

@pretty_whistle
thanks for your suggestion. Unfortunately it doesn't work

@bobsageek
I'm not sure if this is of any help. As the computer is going into hibernate it has to be restarted. Anyway, this is the dmesg just after restart:
```

[B][COLOR="Red"]
[ 2838.263310] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
[ 2838.264015] render error detected, EIR: 0x00000010
[ 2838.264015] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
[ 2838.264015] render error detected, EIR: 0x00000010[/COLOR][/B]

```

[COLOR="Black"][/COLOR]

This might be your issue, video driver is erroring out on wake. Now at least you know where the error is likely coming from. I'm tied up now but I'll try and look into this, but hopefully a smart person will mosey by and see this and help.

Searching bugs in Launchpad [refers to this bug,]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/702090") might be worth reading through those solutions.

---

### Post by cje on 2012-01-03
> **audiomick said:**
> Before we get on to that, how big is your swap, and how much RAM do you have?

On way to find out is to look at the "resources" tab of the system monitor.

Dear audiomick
Thanks for your reply.
The SWAP is 2,5MB (0,2%)

---

### Post by cje on 2012-01-03
> **bobsageek said:**
> [COLOR="Black"][/COLOR]

This might be your issue, video driver is erroring out on wake. Now at least you know where the error is likely coming from. I'm tied up now but I'll try and look into this, but hopefully a smart person will mosey by and see this and help.

Searching bugs in Launchpad [refers to this bug,]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/702090") might be worth reading through those solutions.

Thanks for your suggestion bobsageek
I believe you're into something. Do you know if there are sufficient support on this Graphic card:
Intel® 865G x86/MMX/SSE2

---

