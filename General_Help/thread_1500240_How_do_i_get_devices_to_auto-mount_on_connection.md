---
title: "How do i get devices to auto-mount on connection?"
date: 2010-06-02
forum: General Help
---

### Post by jinba.ittai on 2010-06-02
Here is my dilemma; I have many flash drives, memory sticks, card reader, and 2 mybook 1tb so i am constanly plugging in, or unplugging devices from my machine running the latest version of ubuntu (i beleive 10.04?). I remember when i use to connect a device it would mount and work right off the bat. but now, everytime i connect anything, i have to go through Disk Utility to select the drive and mount it (also unmount before disconnect). 

Another problem is that some times disk utility doesnt like to work (as with a few other programs). This happends every now and then and im not sure if its my systems hardware or this version of ubuntu. every now and then programs like to stop responding (turn grey) and some programs like disk utility will open up, but just be blank and not show the detected devices. 


Any help would be greatly appreciated!

---

### Post by jinba.ittai on 2010-06-09
Bump?
Added more ram and the disk utility works more often but still stops responding every now and then. 

any help?

---

### Post by ibuclaw on 2010-06-09
Hi, when you next have trouble automounting a device, can you open a terminal (Applications -> Accessories -> Terminal)

And type (or paste if you wish) in:
```
dmesg
```

And post the output here in [NOPARSE]```

```[/NOPARSE] tags?

Regards.

---

### Post by paultag on 2010-06-09
> **Sandy V Jina said:**
> Bump?
Added more ram and the disk utility works more often but still stops responding every now and then. 

any help?

Perhaps post a log of dmesg and /var/log/messages?

Dude, btw, your avatar. Is that from that new movie "human centipede" ? Daaamn that's creepy.

---

### Post by jinba.ittai on 2010-06-10
> **paultag said:**
> 

Dude, btw, your avatar. Is that from that new movie "human centipede" ? Daaamn that's creepy.

Haha no, it is a creepy pic. I found it on the internet a loong time ago and went through my cache and saved it. Since then i wasnt able to find the pic so i resized and made my forum avatars.





Thanks guys, it doesnt do it as often since i added more ram, but i will remember next time it does happen to run the command and post here. (even if that might be a little while)

---

### Post by ibuclaw on 2010-06-10
> **Sandy V Jina said:**
> Haha no, it is a creepy pic. I found it on the internet a loong time ago and went through my cache and saved it. Since then i wasnt able to find the pic so i resized and made my forum avatars.





Thanks guys, it doesnt do it as often since i added more ram, but i will remember next time it does happen to run the command and post here. (even if that might be a little while)

You may want to check to see if your RAM is OK by running a memtest. IMO, if a hardware solution resolved your problem, then it's probably about time you do your annual maintenance. :)

Regards
Iain

---

### Post by jinba.ittai on 2010-06-11
```
[    0.160000] bus: 00 index 0 io port: [0, ffff]
[    0.160000] bus: 00 index 1 mmio: [a0000, bffff]
[    0.160000] bus: 00 index 2 mmio: [50000000, efffffff]
[    0.160000] bus: 00 index 3 mmio: [f0000000, fcffffffff]
[    0.160000] ACPI: bus type pci registered
[    0.160000] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.160000] PCI: MCFG area at e0000000 reserved in E820
[    0.160000] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.160000] PCI: Using configuration type 1 for base access
[    0.160000] bio: create slab <bio-0> at 0
[    0.160000] ACPI: EC: Look up EC in DSDT
[    0.160965] ACPI: Interpreter enabled
[    0.160969] ACPI: (supports S0 S3 S4 S5)
[    0.160989] ACPI: Using IOAPIC for interrupt routing
[    0.164584] ACPI: No dock devices found.
[    0.164700] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.164748] pci 0000:00:00.0: reg 18 io port: [0x4100-0x411f]
[    0.164754] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.164867] pci 0000:00:11.0: reg 10 io port: [0xfe00-0xfe07]
[    0.164875] pci 0000:00:11.0: reg 14 io port: [0xfd00-0xfd03]
[    0.164884] pci 0000:00:11.0: reg 18 io port: [0xfc00-0xfc07]
[    0.164892] pci 0000:00:11.0: reg 1c io port: [0xfb00-0xfb03]
[    0.164900] pci 0000:00:11.0: reg 20 io port: [0xfa00-0xfa0f]
[    0.164909] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f1ff]
[    0.164917] pci 0000:00:11.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
[    0.164950] pci 0000:00:11.0: supports D1 D2
[    0.165008] pci 0000:00:12.0: reg 10 io port: [0xf900-0xf907]
[    0.165017] pci 0000:00:12.0: reg 14 io port: [0xf800-0xf803]
[    0.165025] pci 0000:00:12.0: reg 18 io port: [0xf700-0xf707]
[    0.165033] pci 0000:00:12.0: reg 1c io port: [0xf600-0xf603]
[    0.165042] pci 0000:00:12.0: reg 20 io port: [0xf500-0xf50f]
[    0.165050] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe02e000-0xfe02e1ff]
[    0.165059] pci 0000:00:12.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
[    0.165091] pci 0000:00:12.0: supports D1 D2
[    0.165139] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.165245] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.165360] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.165428] pci 0000:00:13.2: supports D1 D2
[    0.165430] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.165435] pci 0000:00:13.2: PME# disabled
[    0.165490] pci 0000:00:14.0: reg 10 io port: [0x400-0x40f]
[    0.165498] pci 0000:00:14.0: reg 14 32bit mmio: [0xfe02a000-0xfe02a3ff]
[    0.165534] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.165598] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.165607] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.165615] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.165623] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.165631] pci 0000:00:14.1: reg 20 io port: [0xf300-0xf30f]
[    0.165827] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe029000-0xfe0290ff]
[    0.166000] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.166004] pci 0000:01:05.0: reg 14 io port: [0xef00-0xefff]
[    0.166008] pci 0000:01:05.0: reg 18 32bit mmio: [0xfddf0000-0xfddfffff]
[    0.166017] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.166026] pci 0000:01:05.0: supports D1 D2
[    0.166043] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.166046] pci 0000:00:01.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.166050] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.166112] pci 0000:02:02.0: reg 10 io port: [0xdf00-0xdf0f]
[    0.166122] pci 0000:02:02.0: reg 14 io port: [0xde00-0xde0f]
[    0.166133] pci 0000:02:02.0: reg 18 io port: [0xdd00-0xdd0f]
[    0.166143] pci 0000:02:02.0: reg 1c io port: [0xdc00-0xdc0f]
[    0.166153] pci 0000:02:02.0: reg 20 io port: [0xdb00-0xdb1f]
[    0.166163] pci 0000:02:02.0: reg 24 io port: [0xda00-0xdaff]
[    0.166174] pci 0000:02:02.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.166258] pci 0000:02:03.0: reg 10 io port: [0xd900-0xd9ff]
[    0.166268] pci 0000:02:03.0: reg 14 32bit mmio: [0xfdcff000-0xfdcff0ff]
[    0.166308] pci 0000:02:03.0: reg 30 32bit mmio pref: [0x000000-0x00ffff]
[    0.166337] pci 0000:02:03.0: supports D1 D2
[    0.166340] pci 0000:02:03.0: PME# supported from D1 D2 D3hot D3cold
[    0.166345] pci 0000:02:03.0: PME# disabled
[    0.166402] pci 0000:02:04.0: reg 10 32bit mmio: [0xfdcfe000-0xfdcfe7ff]
[    0.166412] pci 0000:02:04.0: reg 14 io port: [0xd800-0xd87f]
[    0.166482] pci 0000:02:04.0: supports D2
[    0.166484] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.166490] pci 0000:02:04.0: PME# disabled
[    0.166554] pci 0000:00:14.4: transparent bridge
[    0.166563] pci 0000:00:14.4: bridge io port: [0xd000-0xdfff]
[    0.166568] pci 0000:00:14.4: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.166573] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfde00000-0xfdefffff]
[    0.166589] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.166737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.166877] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.180970] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181056] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181141] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181227] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.181317] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11)
[    0.181401] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[    0.181485] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 *10 11)
[    0.181569] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11)
[    0.181689] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.181693] vgaarb: loaded
[    0.181816] SCSI subsystem initialized
[    0.181919] libata version 3.00 loaded.
[    0.182000] usbcore: registered new interface driver usbfs
[    0.182011] usbcore: registered new interface driver hub
[    0.182038] usbcore: registered new device driver usb
[    0.182167] ACPI: WMI: Mapper loaded
[    0.182169] PCI: Using ACPI for IRQ routing
[    0.182179] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.182182] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.182339] NetLabel: Initializing
[    0.182340] NetLabel:  domain hash size = 128
[    0.182342] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.182358] NetLabel:  unlabeled traffic allowed by default
[    0.184268] AppArmor: AppArmor Filesystem Enabled
[    0.184292] pnp: PnP ACPI init
[    0.184313] ACPI: bus type pnp registered
[    0.184835] pnp 00:01: io resource (0x40b-0x40b) overlaps 0000:00:14.0 BAR 0 (0x400-0x40f), disabling
[    0.186576] pnp 00:0a: mem resource (0xd0000-0xd3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.186579] pnp 00:0a: mem resource (0xd5000-0xd7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.186583] pnp 00:0a: mem resource (0xf0000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.186586] pnp 00:0a: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.186590] pnp 00:0a: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.186593] pnp 00:0a: mem resource (0x100000-0x47eeffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.186642] pnp: PnP ACPI: found 11 devices
[    0.186644] ACPI: ACPI bus type pnp unregistered
[    0.186656] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.186659] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.186661] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.186664] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.186667] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.186670] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.186678] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.186681] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.186684] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.186687] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.186694] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.186696] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.186702] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.186708] system 00:0a: iomem range 0x47f00000-0x47ffffff could not be reserved
[    0.186710] system 00:0a: iomem range 0x47ef0000-0x47efffff could not be reserved
[    0.186714] system 00:0a: iomem range 0xffff0000-0xffffffff has been reserved
[    0.186716] system 00:0a: iomem range 0x48000000-0x4fffffff has been reserved
[    0.186719] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.186722] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.186725] system 00:0a: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.191442] Switching to clocksource acpi_pm
[    0.191570] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.191572] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.191576] pci 0000:00:01.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.191579] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.191585] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.191589] pci 0000:00:14.4:   IO window: 0xd000-0xdfff
[    0.191596] pci 0000:00:14.4:   MEM window: 0xfdc00000-0xfdcfffff
[    0.191601] pci 0000:00:14.4:   PREFETCH window: 0xfde00000-0xfdefffff
[    0.191623] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.191626] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.191628] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.191631] pci_bus 0000:01: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.191633] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.191636] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.191638] pci_bus 0000:02: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.191641] pci_bus 0000:02: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.191643] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.191646] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.191689] NET: Registered protocol family 2
[    0.191820] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.192857] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.197182] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.198221] TCP: Hash tables configured (established 262144 bind 65536)
[    0.198225] TCP reno registered
[    0.198373] NET: Registered protocol family 1
[    0.198390] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.198397] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.250052] pci 0000:01:05.0: Boot video device
[    0.250449] Scanning for low memory corruption every 60 seconds
[    0.250604] audit: initializing netlink socket (disabled)
[    0.250615] type=2000 audit(1276253777.250:1): initialized
[    0.259162] Trying to unpack rootfs image as initramfs...
[    0.270455] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.271808] VFS: Disk quotas dquot_6.5.2
[    0.271870] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.280129] fuse init (API version 7.13)
[    0.280269] msgmni has been set to 2231
[    0.280549] alg: No test for stdrng (krng)
[    0.280604] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.280608] io scheduler noop registered
[    0.280610] io scheduler anticipatory registered
[    0.280612] io scheduler deadline registered
[    0.280648] io scheduler cfq registered (default)
[    0.280784] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.280810] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.280909] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.280913] ACPI: Power Button [PWRB]
[    0.280965] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.280967] ACPI: Power Button [PWRF]
[    0.281213] processor LNXCPU:00: registered as cooling_device0
[    0.284068] Linux agpgart interface v0.103
[    0.284103] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.285264] brd: module loaded
[    0.285693] loop: module loaded
[    0.285789] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.290204]   alloc irq_desc for 23 on node 0
[    0.290208]   alloc kstat_irqs on node 0
[    0.290217] pata_acpi 0000:00:11.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.290375]   alloc irq_desc for 22 on node 0
[    0.290376]   alloc kstat_irqs on node 0
[    0.290380] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.290439]   alloc irq_desc for 16 on node 0
[    0.290441]   alloc kstat_irqs on node 0
[    0.290445] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.300590] Fixed MDIO Bus: probed
[    0.300629] PPP generic driver version 2.4.2
[    0.300701] tun: Universal TUN/TAP device driver, 1.6
[    0.300703] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.300812] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.300869]   alloc irq_desc for 19 on node 0
[    0.300872]   alloc kstat_irqs on node 0
[    0.300879] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.300906] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.300939] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.301018] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02b000
[    0.320278] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.320457] usb usb1: configuration #1 chosen from 1 choice
[    0.320493] hub 1-0:1.0: USB hub found
[    0.320507] hub 1-0:1.0: 8 ports detected
[    0.320635] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.330110] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.330140] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.330233] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.330261] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02d000
[    0.394314] usb usb2: configuration #1 chosen from 1 choice
[    0.394352] hub 2-0:1.0: USB hub found
[    0.394368] hub 2-0:1.0: 4 ports detected
[    0.400201] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.400241] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.400354] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.400382] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02c000
[    0.464375] usb usb3: configuration #1 chosen from 1 choice
[    0.464409] hub 3-0:1.0: USB hub found
[    0.464425] hub 3-0:1.0: 4 ports detected
[    0.464521] uhci_hcd: USB Universal Host Controller Interface driver
[    0.464622] PNP: No PS/2 controller found. Probing ports directly.
[    0.471061] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.471075] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.471251] mice: PS/2 mouse device common for all mice
[    0.471400] rtc_cmos 00:03: RTC can wake from S4
[    0.471458] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.471486] rtc0: alarms up to one month, 242 bytes nvram
[    0.471659] device-mapper: uevent: version 1.0.3
[    0.471803] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.480186] device-mapper: multipath: version 1.1.0 loaded
[    0.480192] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.480445] cpuidle: using governor ladder
[    0.480447] cpuidle: using governor menu
[    0.480810] TCP cubic registered
[    0.480951] NET: Registered protocol family 10
[    0.481422] lo: Disabled Privacy Extensions
[    0.481695] NET: Registered protocol family 17
[    0.481733] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ processors (1 cpu cores) (version 2.20.00)
[    0.494210] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    0.496201] Freeing initrd memory: 8128k freed
[    0.504675] PM: Resume from disk failed.
[    0.504707] registered taskstats version 1
[    0.505081]   Magic number: 14:774:931
[    0.505171] rtc_cmos 00:03: setting system clock to 2010-06-11 10:56:17 UTC (1276253777)
[    0.505175] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.505176] EDD information not available.
[    0.505228] Freeing unused kernel memory: 876k freed
[    0.505975] Write protecting the kernel read-only data: 7680k
[    0.528394] udev: starting version 151
[    0.707819] Floppy drive(s): fd0 is 1.44M
[    0.710820] scsi0 : pata_atiixp
[    0.715093] scsi1 : pata_atiixp
[    0.716125] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf300 irq 14
[    0.716129] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf308 irq 15
[    0.717933] sata_sil 0000:00:11.0: version 2.4
[    0.720224] scsi2 : sata_sil
[    0.723998] FDC 0 is a post-1991 82077
[    0.737441] scsi3 : sata_sil
[    0.737615] ata3: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 23
[    0.737620] ata4: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 23
[    0.770692] scsi4 : sata_sil
[    0.770812] scsi5 : sata_sil
[    0.770935] ata5: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e080 irq 22
[    0.770939] ata6: SATA max UDMA/100 mmio m512@0xfe02e000 tf 0xfe02e0c0 irq 22
[    0.771128] sata_via 0000:02:02.0: version 2.4
[    0.771148] sata_via 0000:02:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.771198] sata_via 0000:02:02.0: routed to hard irq line 10
[    0.771335] scsi6 : sata_via
[    0.771449] scsi7 : sata_via
[    0.771536] scsi8 : sata_via
[    0.771576] ata7: SATA max UDMA/133 port i16@0xdf00 bmdma 0xdb00 irq 22
[    0.771581] ata8: SATA max UDMA/133 port i16@0xde00 bmdma 0xdb08 irq 22
[    0.771583] ata9: PATA max UDMA/133 port i16@0xdd00 bmdma 0xdb10 irq 22
[    0.840021] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    1.060604] ata2.00: ATAPI: SAMSUNG CD-ROM  SC-148C, B105, max UDMA/33
[    1.064362] usb 3-1: configuration #1 chosen from 1 choice
[    1.080616] ata2.00: configured for UDMA/33
[    1.081135] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148C   B105 PQ: 0 ANSI: 5
[    1.087099] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    1.087104] Uniform CD-ROM driver Revision: 3.20
[    1.087237] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.087304] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.087973] usbcore: registered new interface driver hiddev
[    1.088343] usbcore: registered new interface driver usbhid
[    1.088421] usbhid: v2.6:USB HID core driver
[    1.120041] ata3: SATA link down (SStatus 0 SControl 300)
[    1.131982] ata7: SATA link down (SStatus 0 SControl 310)
[    1.132043] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.185768] ata5.00: ATA-7: ST3250820AS, 3.ADG, max UDMA/133
[    1.185771] ata5.00: 488281250 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.269074] ata5.00: configured for UDMA/100
[    1.470043] ata4: SATA link down (SStatus 0 SControl 300)
[    1.470180] scsi 4:0:0:0: Direct-Access     ATA      ST3250820AS      3.AD PQ: 0 ANSI: 5
[    1.470344] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.470589] sd 4:0:0:0: [sda] 488281250 512-byte logical blocks: (250 GB/232 GiB)
[    1.470629] sd 4:0:0:0: [sda] Write Protect is off
[    1.470632] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.470652] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.470783]  sda: sda1 sda2 < sda5 >
[    1.516491] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.820044] ata6: SATA link down (SStatus 0 SControl 300)
[    2.181868] ata8: SATA link down (SStatus 0 SControl 310)
[    2.362360] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.367383] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.367805] ohci1394 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.372168] 8139too Fast Ethernet driver 0.9.28
[    2.376613] input: MLK wireless combo as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input3
[    2.376705] sunplus 0003:04FC:05D8.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK wireless combo] on usb-0000:00:13.1-1/input0
[    2.383267] sunplus 0003:04FC:05D8.0002: fixing up Sunplus Wireless Desktop report descriptor
[    2.384703] input: MLK wireless combo as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.1/input/input4
[    2.385287] sunplus 0003:04FC:05D8.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK wireless combo] on usb-0000:00:13.1-1/input1
[    2.432062] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fdcfe000-fdcfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.437965]   alloc irq_desc for 20 on node 0
[    2.437968]   alloc kstat_irqs on node 0
[    2.437977] 8139too 0000:02:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.439501] eth0: RealTek RTL8139 at 0xd900, 00:13:d3:a5:b5:d5, IRQ 20
[    2.594039] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.594045] EXT4-fs (sda1): write access will be enabled during recovery
[    3.750240] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00009ba32c]
[    4.551690] EXT4-fs (sda1): recovery complete
[    4.552252] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   15.410829] udev: starting version 151
[   15.461967] Adding 1853432k swap on /dev/sda5.  Priority:-1 extents:1 across:1853432k 
[   15.565159] lp: driver loaded but no devices found
[   15.634955] EDAC MC: Ver: 2.1.0 Jun  3 2010
[   15.639099] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.677161] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x400, revision 0
[   15.733251] parport_pc 00:08: reported by Plug and Play ACPI
[   15.733290] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   15.855740] lp0: using parport0 (interrupt-driven).
[   16.038688] [drm] Initialized drm 1.1.0 20060810
[   16.048499] type=1505 audit(1276253793.034:2):  operation="profile_load" pid=648 name="/sbin/dhclient3"
[   16.048766] type=1505 audit(1276253793.034:3):  operation="profile_load" pid=648 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.048914] type=1505 audit(1276253793.034:4):  operation="profile_load" pid=648 name="/usr/lib/connman/scripts/dhclient-script"
[   16.075125] ppdev: user-space parallel port driver
[   16.075517] EDAC amd64_edac:  Ver: 3.2.0 Jun  3 2010
[   16.080393] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   16.080400] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   16.080402]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   16.080403]  (Note that use of the override may cause unknown side effects.)
[   16.080424] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   16.189330] [drm] radeon defaulting to kernel modesetting.
[   16.189335] [drm] radeon kernel modesetting enabled.
[   16.196911]   alloc irq_desc for 17 on node 0
[   16.196915]   alloc kstat_irqs on node 0
[   16.196925] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.237968] [drm] radeon: Initializing kernel modesetting.
[   16.244469] [drm] register mmio base: 0xFDDF0000
[   16.244472] [drm] register mmio size: 65536
[   16.244947] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   16.244966] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   16.245013] [drm] Generation 2 PCI interface, using max accessible memory
[   16.245015] [drm] radeon: VRAM 128M
[   16.245017] [drm] radeon: VRAM from 0x48000000 to 0x4FFFFFFF
[   16.245019] [drm] radeon: GTT 32M
[   16.245020] [drm] radeon: GTT from 0x50000000 to 0x51FFFFFF
[   16.245061] [drm] radeon: irq initialized.
[   16.245241] [drm] Detected VRAM RAM=128M, BAR=256M
[   16.245246] [drm] RAM width 128bits DDR
[   16.249826] [TTM] Zone  kernel: Available graphics memory: 575892 kiB.
[   16.249851] [drm] radeon: 128M of VRAM memory ready
[   16.249853] [drm] radeon: 32M of GTT memory ready.
[   16.249877] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   16.250405] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[   16.250421] [drm] radeon: cp idle (0x10000C03)
[   16.250555] [drm] Loading R300 Microcode
[   16.250993] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   16.267915] [drm] radeon: ring at 0x0000000050000000
[   16.267937] [drm] ring test succeeded in 2 usecs
[   16.268079] [drm] radeon: ib pool ready.
[   16.268695] [drm] ib test succeeded in 0 usecs
[   16.268836] [drm] Radeon Display Connectors
[   16.268838] [drm] Connector 0:
[   16.268840] [drm]   VGA
[   16.268842] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   16.268844] [drm]   Encoders:
[   16.268846] [drm]     CRT1: INTERNAL_DAC2
[   16.493440] type=1505 audit(1276253793.484:5):  operation="profile_load" pid=787 name="/usr/share/gdm/guest-session/Xsession"
[   16.498649] type=1505 audit(1276253793.484:6):  operation="profile_replace" pid=788 name="/sbin/dhclient3"
[   16.498931] type=1505 audit(1276253793.484:7):  operation="profile_replace" pid=788 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.499086] type=1505 audit(1276253793.484:8):  operation="profile_replace" pid=788 name="/usr/lib/connman/scripts/dhclient-script"
[   16.500663] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   16.525222] type=1505 audit(1276253793.514:9):  operation="profile_load" pid=789 name="/usr/bin/evince"
[   16.528852] type=1505 audit(1276253793.514:10):  operation="profile_load" pid=789 name="/usr/bin/evince-previewer"
[   16.592760] type=1505 audit(1276253793.584:11):  operation="profile_load" pid=789 name="/usr/bin/evince-thumbnailer"
[   16.616662] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   16.776794] [drm] fb mappable at 0xD0040000
[   16.776797] [drm] vram apper at 0xD0000000
[   16.776799] [drm] size 5242880
[   16.776801] [drm] fb depth is 24
[   16.776802] [drm]    pitch is 5120
[   16.784747] fb0: radeondrmfb frame buffer device
[   16.784751] registered panic notifier
[   16.784758] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   16.786709] vga16fb: initializing
[   16.786714] vga16fb: mapped to 0xffff8800000a0000
[   16.786720] vga16fb: not registering due to another framebuffer present
[   16.909761] Console: switching to colour frame buffer device 160x64
[   27.250028] eth0: no IPv6 routers present
[   57.750065] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   87.061434] end_request: I/O error, dev fd0, sector 0
[  125.060888] end_request: I/O error, dev fd0, sector 0
[  163.061133] end_request: I/O error, dev fd0, sector 0
[  163.061141] __ratelimit: 9 callbacks suppressed
[  163.061144] Buffer I/O error on device fd0, logical block 0
[  201.061291] end_request: I/O error, dev fd0, sector 0
[  201.061300] Buffer I/O error on device fd0, logical block 0
[  239.061482] end_request: I/O error, dev fd0, sector 0
[  239.061491] Buffer I/O error on device fd0, logical block 0
[  277.061628] end_request: I/O error, dev fd0, sector 0
[  277.061635] Buffer I/O error on device fd0, logical block 0
[  294.100059] usb 1-5: new high speed USB device using ehci_hcd and address 3
[  294.251082] usb 1-5: configuration #1 chosen from 1 choice
[  294.319244] Initializing USB Mass Storage driver...
[  294.319389] scsi9 : SCSI emulation for USB Mass Storage devices
[  294.319566] usbcore: registered new interface driver usb-storage
[  294.319569] USB Mass Storage support registered.
[  294.326670] usb-storage: device found at 3
[  294.326674] usb-storage: waiting for device to settle before scanning
[  299.331362] usb-storage: device scan complete
[  299.331822] scsi 9:0:0:0: Direct-Access     SANYO    CG10             1.00 PQ: 0 ANSI: 2
[  299.334261] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  300.165471] sd 9:0:0:0: [sdb] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
[  300.165825] sd 9:0:0:0: [sdb] Write Protect is off
[  300.165828] sd 9:0:0:0: [sdb] Mode Sense: 18 00 00 08
[  300.165831] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  300.169581] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  300.169587]  sdb: sdb1
[  300.174581] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[  300.174587] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  315.061799] end_request: I/O error, dev fd0, sector 0
[  315.061806] Buffer I/O error on device fd0, logical block 0
[  353.060962] end_request: I/O error, dev fd0, sector 0
[  353.060973] Buffer I/O error on device fd0, logical block 0
[  391.071649] end_request: I/O error, dev fd0, sector 0
[  391.071657] Buffer I/O error on device fd0, logical block 0
david@david-desktop:~$ 

```


Did it again this morning, really needed to move a project off my pc but cant now.... ill do a mem test when i get back home

---

### Post by dcstar on 2010-06-11
> **Sandy V Jina said:**
> Here is my dilemma; I have many flash drives, memory sticks, card reader, and 2 mybook 1tb so i am constanly plugging in, or unplugging devices from my machine running the latest version of ubuntu (i beleive 10.04?). I remember when i use to connect a device it would mount and work right off the bat. but now, everytime i connect anything, i have to go through Disk Utility to select the drive and mount it (also unmount before disconnect). 
.........
Any help would be greatly appreciated!

Automount is set on a user basis by the following gconf keys:

```
/desktop/gnome/volume_manager/automount_drives
/desktop/gnome/volume_manager/automount_media
```

Use Applications-System Tools-Configuration Editor to modify them.

---

### Post by jinba.ittai on 2010-06-11
@DCSTAR

Looking at the editor right now but have no clue how to modify the drivers to make control the auto mount...

Besides, shouldnt devices auto mount as soon as you install ubuntu? Works fine on friends laptop.

---

### Post by dino99 on 2010-06-11
i'm happy with mountmanager to deal with the partitions and devices rights

---

### Post by jinba.ittai on 2010-06-11
> **dino99 said:**
> i'm happy with mountmanager to deal with the partitions and devices rights

Are you referring to the KVPM KDE Volume Partition manage?

---

### Post by dino99 on 2010-06-11
> **Sandy V Jina said:**
> Are you referring to the KVPM KDE Volume Partition manage?

mountmanager is used with gnome (based on qt)

but see here:

[http://kde-apps.org/content/show.php/MountManager?content=76502](http://kde-apps.org/content/show.php/MountManager?content=76502)

---

### Post by jinba.ittai on 2010-06-11
> **dino99 said:**
> mountmanager is used with gnome (based on qt)

but see here:

[http://kde-apps.org/content/show.php/MountManager?content=76502](http://kde-apps.org/content/show.php/MountManager?content=76502)

i386 =[ im on amd64

---

### Post by jinba.ittai on 2010-06-12
Bump? still nothing is mounting automatically.

---

### Post by sighthnd on 2010-06-22
> **dcstar said:**
> Automount is set on a user basis by the following gconf keys:

```
/desktop/gnome/volume_manager/automount_drives
/desktop/gnome/volume_manager/automount_media
```Use Applications-System Tools-Configuration Editor to modify them.

What would be the equivalent for KDE?

---

### Post by last1home on 2010-06-26
[http://ubuntuforums.org/showthread.php?t=1503850](http://ubuntuforums.org/showthread.php?t=1503850)  read the whole thread ... last1home

---

### Post by elitenoobboy on 2010-08-12
> **dcstar said:**
> Automount is set on a user basis by the following gconf keys:

```
/desktop/gnome/volume_manager/automount_drives
/desktop/gnome/volume_manager/automount_media
```

Use Applications-System Tools-Configuration Editor to modify them.
If there is no volume_manager folder already present, would you just create it?

---

