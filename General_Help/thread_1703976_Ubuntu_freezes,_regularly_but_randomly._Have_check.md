---
title: "Ubuntu freezes, regularly but randomly. Have checked logs and googled. Please help."
date: 2011-03-10
forum: General Help
---

### Post by migel_wimtore on 2011-03-10
Okay, i know. Freezes are really hard to define as they can be caused by any number of issues, and could even be specific to my setup. 

That said im going mad. I used to use ubuntu powerpc on an old ibook and that never ever crashed. 

However i have been running ubuntu on a (almost as old) dell inspiron 1300 with a pentium m 2.10 Ghz laptop for a while now and it freezes (no input, mouse or keyboard, no sysrq alt gr REISUB, no ctrl alt backspace, no changing terminal, nothing), and it is driving me mad. 

Mad mad.

Not good mad.

Bad mad.

I know, no one will be able to tell me the prob as such, right? But, can someone help me to diagnose it. 

Please.

Every time i get a crash, which appears to be quite random, happens mostly when using firefox 4, but happened when i used chromium to test whether it was firefox, i have to hard reset my machine (is that actually bad for the drive, by the way, or is that an old wives?). Not sure if it would happen without a browser open at all as that is 97% of what i use computer for.

Perhaps will leave on with no app running everyday while i go to work for a month, or until i sort this out, to check.

It seems to happen when the computer has been on for a while, a couple off hours or more, though has happened sooner, once (as far as i can remember), but this was after being recently rebooted following a previous crash.

Happens when flash is playing, or is not, when cpu load is high or is not (mostly when relatively low, though i tend to just read web pages, so...). Happens with compiz running or not, happens in ubuntu desktop and in openbox.

Seems to happen randomly as far as i can tell, anywhere between twice a day (up to 10 hours of on time per day) to once a week, or less (rarely).

I have been looking in /var/log/messages and /var/log/syslog and var/log/kern.log and pretty much everywhere in System Log Viewer and also reading through dmesg output.

The problem is i dont know if i would be able to identify the problem if i saw it.

Anyways this is the output of dmesg after rebooting from a crash, just now, and being driven over the edge (like an independently minded lemming by his pushy father), and realising i cant do this, alone:
```

[    0.146643] pci 0000:00:02.0: reg 1c: [mem 0xdfec0000-0xdfefffff]
[    0.146676] pci 0000:00:02.1: reg 10: [mem 0xdff80000-0xdfffffff]
[    0.146778] pci 0000:00:1b.0: reg 10: [mem 0xdfebc000-0xdfebffff 64bit]
[    0.146838] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.146843] pci 0000:00:1b.0: PME# disabled
[    0.146938] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.146943] pci 0000:00:1c.0: PME# disabled
[    0.147042] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.147047] pci 0000:00:1c.3: PME# disabled
[    0.147110] pci 0000:00:1d.0: reg 20: [io  0xbf80-0xbf9f]
[    0.147172] pci 0000:00:1d.1: reg 20: [io  0xbf60-0xbf7f]
[    0.147234] pci 0000:00:1d.2: reg 20: [io  0xbf40-0xbf5f]
[    0.147296] pci 0000:00:1d.3: reg 20: [io  0xbf20-0xbf3f]
[    0.147354] pci 0000:00:1d.7: reg 10: [mem 0xb0000000-0xb00003ff]
[    0.147416] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.147422] pci 0000:00:1d.7: PME# disabled
[    0.147573] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.147580] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.147586] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.147591] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0900-097f
[    0.147623] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.147631] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.147639] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.147647] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.147655] pci 0000:00:1f.1: reg 20: [io  0xbfa0-0xbfaf]
[    0.147745] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.147751] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.147757] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.147765] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.147824] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]
[    0.147829] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.147834] pci 0000:00:1c.3:   bridge window [mem 0xdfc00000-0xdfdfffff]
[    0.147842] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.147901] pci 0000:02:00.0: reg 10: [mem 0xdfbfc000-0xdfbfdfff]
[    0.147957] pci 0000:02:00.0: supports D1 D2
[    0.147960] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.147965] pci 0000:02:00.0: PME# disabled
[    0.148006] pci 0000:02:03.0: reg 10: [mem 0xdfbfe000-0xdfbfffff]
[    0.148101] pci 0000:00:1e.0: PCI bridge to [bus 02-02] (subtractive decode)
[    0.148107] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.148112] pci 0000:00:1e.0:   bridge window [mem 0xdfb00000-0xdfbfffff]
[    0.148120] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.148123] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.148126] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.148147] pci_bus 0000:00: on NUMA node 0
[    0.148152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.148494] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.148615] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.148701] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.157283] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.157411] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.157537] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.157667] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 *7 9 10 11)
[    0.157774] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.157884] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.157996] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.158052] HEST: Table is not found!
[    0.158128] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.158136] vgaarb: loaded
[    0.158294] SCSI subsystem initialized
[    0.158347] libata version 3.00 loaded.
[    0.158403] usbcore: registered new interface driver usbfs
[    0.158419] usbcore: registered new interface driver hub
[    0.158445] usbcore: registered new device driver usb
[    0.158567] ACPI: WMI: Mapper loaded
[    0.158569] PCI: Using ACPI for IRQ routing
[    0.158573] PCI: pci_cache_line_size set to 64 bytes
[    0.158635] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.158638] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.158641] reserve RAM buffer: 000000007f7d3800 - 000000007fffffff 
[    0.158746] NetLabel: Initializing
[    0.158748] NetLabel:  domain hash size = 128
[    0.158749] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.158764] NetLabel:  unlabeled traffic allowed by default
[    0.158902] hpet clockevent registered
[    0.158907] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.158915] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.158919] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.164016] Switching to clocksource tsc
[    0.175287] AppArmor: AppArmor Filesystem Enabled
[    0.175320] pnp: PnP ACPI init
[    0.175350] ACPI: bus type pnp registered
[    0.204857] pnp 00:02: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.204861] pnp 00:02: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.204930] pnp 00:03: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.204934] pnp 00:03: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.204938] pnp 00:03: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.205785] pnp: PnP ACPI: found 11 devices
[    0.205788] ACPI: ACPI bus type pnp unregistered
[    0.205793] PnPBIOS: Disabled by ACPI PNP
[    0.205808] system 00:00: [mem 0x00000000-0x0009fbff] could not be reserved
[    0.205811] system 00:00: [mem 0x0009fc00-0x0009ffff] could not be reserved
[    0.205815] system 00:00: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.205818] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.205821] system 00:00: [mem 0x00100000-0x7f7d37ff] could not be reserved
[    0.205824] system 00:00: [mem 0x7f7d3800-0x7f7fffff] has been reserved
[    0.205827] system 00:00: [mem 0x7f800000-0x7fffffff] has been reserved
[    0.205830] system 00:00: [mem 0xfeda0000-0xfedfffff] has been reserved
[    0.205833] system 00:00: [mem 0xffb00000-0xffffffff] has been reserved
[    0.205837] system 00:00: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.205840] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.205843] system 00:00: [mem 0xfed20000-0xfed9ffff] has been reserved
[    0.205846] system 00:00: [mem 0xf0000000-0xf0003fff] has been reserved
[    0.205849] system 00:00: [mem 0xf0004000-0xf0004fff] has been reserved
[    0.205852] system 00:00: [mem 0xf0005000-0xf0005fff] has been reserved
[    0.205855] system 00:00: [mem 0xf0006000-0xf0006fff] has been reserved
[    0.205858] system 00:00: [mem 0xf0008000-0xf000bfff] has been reserved
[    0.205861] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.205868] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.205874] system 00:03: [io  0xf400-0xf4fe] has been reserved
[    0.205877] system 00:03: [io  0x1080-0x10bf] has been reserved
[    0.205880] system 00:03: [io  0x10c0-0x10df] has been reserved
[    0.205883] system 00:03: [io  0x10e0-0x10ff] has been reserved
[    0.205889] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.205892] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.205895] system 00:08: [io  0x0920-0x092f] has been reserved
[    0.205898] system 00:08: [io  0x0930-0x093f] has been reserved
[    0.205900] system 00:08: [io  0x0940-0x097f] has been reserved
[    0.242024] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.242028] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.242032] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.242035] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.242039] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.242046] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.242052] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.242060] pci 0000:00:1c.3: PCI bridge to [bus 0c-0d]
[    0.242064] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.242071] pci 0000:00:1c.3:   bridge window [mem 0xdfc00000-0xdfdfffff]
[    0.242076] pci 0000:00:1c.3:   bridge window [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.242085] pci 0000:00:1e.0: PCI bridge to [bus 02-02]
[    0.242086] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.242093] pci 0000:00:1e.0:   bridge window [mem 0xdfb00000-0xdfbfffff]
[    0.242098] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.242122]   alloc irq_desc for 16 on node -1
[    0.242124]   alloc kstat_irqs on node -1
[    0.242132] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.242139] pci 0000:00:1c.0: setting latency timer to 64
[    0.242149]   alloc irq_desc for 19 on node -1
[    0.242151]   alloc kstat_irqs on node -1
[    0.242155] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.242160] pci 0000:00:1c.3: setting latency timer to 64
[    0.242169] pci 0000:00:1e.0: setting latency timer to 64
[    0.242174] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.242176] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.242179] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.242182] pci_bus 0000:0b: resource 1 [mem 0x80000000-0x801fffff]
[    0.242184] pci_bus 0000:0b: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.242187] pci_bus 0000:0c: resource 0 [io  0xd000-0xdfff]
[    0.242190] pci_bus 0000:0c: resource 1 [mem 0xdfc00000-0xdfdfffff]
[    0.242192] pci_bus 0000:0c: resource 2 [mem 0xd0000000-0xd01fffff 64bit pref]
[    0.242195] pci_bus 0000:02: resource 1 [mem 0xdfb00000-0xdfbfffff]
[    0.242198] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.242200] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.242251] NET: Registered protocol family 2
[    0.242331] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.242615] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.243824] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.244585] TCP: Hash tables configured (established 131072 bind 65536)
[    0.244590] TCP reno registered
[    0.244598] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.244625] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.244800] NET: Registered protocol family 1
[    0.244829] pci 0000:00:02.0: Boot video device
[    0.244958] PCI: CLS 64 bytes, default 64
[    0.245203] cpufreq-nforce2: No nForce2 chipset.
[    0.245246] Scanning for low memory corruption every 60 seconds
[    0.245461] audit: initializing netlink socket (disabled)
[    0.245479] type=2000 audit(1299731227.240:1): initialized
[    0.256508] Trying to unpack rootfs image as initramfs...
[    0.268291] highmem bounce pool size: 64 pages
[    0.268298] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.280014] VFS: Disk quotas dquot_6.5.2
[    0.280105] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.280818] fuse init (API version 7.14)
[    0.280916] msgmni has been set to 1683
[    0.568685] Freeing initrd memory: 10524k freed
[    0.582838] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.582844] io scheduler noop registered
[    0.582846] io scheduler deadline registered
[    0.582867] io scheduler cfq registered (default)
[    0.582999] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.583049]   alloc irq_desc for 40 on node -1
[    0.583051]   alloc kstat_irqs on node -1
[    0.583065] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.583177] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.583221]   alloc irq_desc for 41 on node -1
[    0.583222]   alloc kstat_irqs on node -1
[    0.583231] pcieport 0000:00:1c.3: irq 41 for MSI/MSI-X
[    0.583349] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.583429] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.583932] ACPI: AC Adapter [AC] (on-line)
[    0.584039] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.584384] ACPI: Lid Switch [LID]
[    0.584439] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.584445] ACPI: Power Button [PBTN]
[    0.584492] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.584496] ACPI: Sleep Button [SBTN]
[    0.584700] ACPI: acpi_idle registered with cpuidle
[    0.584924] Marking TSC unstable due to TSC halts in idle
[    0.589002] Switching to clocksource hpet
[    0.590297] thermal LNXTHERM:01: registered as thermal_zone0
[    0.590305] ACPI: Thermal Zone [THM] (60 C)
[    0.590380] ACPI: Battery Slot [BAT0] (battery absent)
[    0.590417] ERST: Table is not found!
[    0.590455] isapnp: Scanning for PnP cards...
[    0.639690] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.641199] brd: module loaded
[    0.641754] loop: module loaded
[    0.641945] ata_piix 0000:00:1f.1: version 2.13
[    0.641963] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.642009] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.642180] scsi0 : ata_piix
[    0.642262] scsi1 : ata_piix
[    0.642931] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.642934] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.643281] Fixed MDIO Bus: probed
[    0.643315] PPP generic driver version 2.4.2
[    0.643365] tun: Universal TUN/TAP device driver, 1.6
[    0.643367] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.643442] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.643463] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.643482] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.643487] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.643526] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.643560] ehci_hcd 0000:00:1d.7: debug port 1
[    0.647437] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.647456] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xb0000000
[    0.651826] ata2: port disabled. ignoring.
[    0.695415] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.695542] hub 1-0:1.0: USB hub found
[    0.695547] hub 1-0:1.0: 8 ports detected
[    0.695626] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.695639] uhci_hcd: USB Universal Host Controller Interface driver
[    0.695669] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.695676] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.695680] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.695711] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.695738] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    0.695858] hub 2-0:1.0: USB hub found
[    0.695863] hub 2-0:1.0: 2 ports detected
[    0.695921]   alloc irq_desc for 17 on node -1
[    0.695923]   alloc kstat_irqs on node -1
[    0.695930] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.695937] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.695941] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.695970] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.739591] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    0.739706] hub 3-0:1.0: USB hub found
[    0.739710] hub 3-0:1.0: 2 ports detected
[    0.739767]   alloc irq_desc for 18 on node -1
[    0.739769]   alloc kstat_irqs on node -1
[    0.739774] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.739780] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.739784] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.739824] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.739860] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    0.739988] hub 4-0:1.0: USB hub found
[    0.739992] hub 4-0:1.0: 2 ports detected
[    0.740063] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.740069] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.740073] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.740114] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.740152] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    0.740263] hub 5-0:1.0: USB hub found
[    0.740267] hub 5-0:1.0: 2 ports detected
[    0.740387] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.740619] i8042.c: Warning: Keylock active.
[    0.741778] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.741785] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.741890] mice: PS/2 mouse device common for all mice
[    0.742042] rtc_cmos 00:06: RTC can wake from S4
[    0.742085] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.742136] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.742301] device-mapper: uevent: version 1.0.3
[    0.742418] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.742469] device-mapper: multipath: version 1.1.1 loaded
[    0.742472] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.830266] EISA: Probing bus 0 at eisa.0
[    0.830274] Cannot allocate resource for EISA slot 1
[    0.830276] Cannot allocate resource for EISA slot 2
[    0.830300] EISA: Detected 0 cards.
[    0.830388] cpuidle: using governor ladder
[    0.830455] cpuidle: using governor menu
[    0.830738] TCP cubic registered
[    0.830874] NET: Registered protocol family 10
[    0.831246] lo: Disabled Privacy Extensions
[    0.831453] NET: Registered protocol family 17
[    0.831970] Using IPI No-Shortcut mode
[    0.832062] PM: Resume from disk failed.
[    0.832077] registered taskstats version 1
[    0.832274]   Magic number: 3:80:464
[    0.832383] rtc_cmos 00:06: setting system clock to 2011-03-10 04:27:08 UTC (1299731228)
[    0.832386] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.832388] EDD information not available.
[    0.919621] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.964016] isapnp: No Plug & Play device found
[    0.966743] ata1.00: ATA-8: SAMSUNG HM160HC, LQ100-10, max UDMA/100
[    0.966746] ata1.00: 312581808 sectors, multi 8: LBA48 
[    0.966782] ata1.01: ATAPI: _NEC DVD+/-RW ND-6650A, 102C, max UDMA/33
[    0.982593] ata1.00: configured for UDMA/100
[    0.996523] ata1.01: configured for UDMA/33
[    0.997980] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HC  LQ10 PQ: 0 ANSI: 5
[    0.998109] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.999649] scsi 0:0:1:0: CD-ROM            _NEC     DVD+-RW ND-6650A 102C PQ: 0 ANSI: 5
[    0.999838] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.002596] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.002599] Uniform CD-ROM driver Revision: 3.20
[    1.002694] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.002737] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.002790] sd 0:0:0:0: [sda] Write Protect is off
[    1.002793] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.002815] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.002960]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.084569] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.084586] Freeing unused kernel memory: 688k freed
[    1.085034] Write protecting the kernel text: 4936k
[    1.085070] Write protecting the kernel read-only data: 1980k
[    1.099789] udev[67]: starting version 163
[    1.367654] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.384056] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.384064] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.384071] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.384078] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.424101] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    1.427827] b44 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.444046] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.444055] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.444062] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.484214] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[    1.484368] b44: b44.c:v2.0
[    1.504853] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:a8:c5:3e
[    1.688140] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    1.688146] EXT4-fs (sda5): write access will be enabled during recovery
[    2.281754] EXT4-fs (sda5): recovery complete
[    2.284400] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   17.628887] udev[335]: starting version 163
[   17.701781] Adding 255996k swap on /dev/sda7.  Priority:-1 extents:1 across:255996k 
[   17.854298] intel_rng: FWH not detected
[   17.946226] lp: driver loaded but no devices found
[   18.055113] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.073202] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input4
[   18.073267] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   18.073296] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   18.106137] Linux agpgart interface v0.103
[   18.160326] coretemp: CPU (model=0xd) has no thermal sensor.
[   18.186381] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   18.187213] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   18.389551] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   18.396319] cfg80211: Calling CRDA to update world regulatory domain
[   18.406323] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   18.441890] cfg80211: World regulatory domain updated:
[   18.441894]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.441897]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.441900]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.441903]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.441906]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.441909]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.497546] [drm] Initialized drm 1.1.0 20060810
[   18.513298] type=1400 audit(1299731246.178:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=610 comm="apparmor_parser"
[   18.513913] type=1400 audit(1299731246.178:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=610 comm="apparmor_parser"
[   18.514257] type=1400 audit(1299731246.178:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=610 comm="apparmor_parser"
[   18.618035] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   18.662919] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.662927] i915 0000:00:02.0: setting latency timer to 64
[   18.673604] [drm] set up 7M of stolen space
[   18.790367] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   18.790941] [drm] initialized overlay support
[   19.287534] dell-wmi-aio: No known WMI GUID found
[   19.295372] phy0: Selected rate control algorithm 'minstrel'
[   19.295989] Registered led device: b43-phy0::tx
[   19.296046] Registered led device: b43-phy0::rx
[   19.296064] Registered led device: b43-phy0::radio
[   19.296147] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   19.331729] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   19.384239] Skipping EDID probe due to cached edid
[   20.085990] Console: switching to colour frame buffer device 160x50
[   20.090347] fb0: inteldrmfb frame buffer device
[   20.090349] drm: registered panic notifier
[   20.090452] Slow work thread pool: Starting up
[   20.090513] Slow work thread pool: Ready
[   20.090523] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.090704] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.090754]   alloc irq_desc for 42 on node -1
[   20.090756]   alloc kstat_irqs on node -1
[   20.090771] HDA Intel 0000:00:1b.0: irq 42 for MSI/MSI-X
[   20.090810] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.164819] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   20.165084] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   20.345326] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x200000/0x0
[   20.381964] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   49.888138] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   49.888204] ata1.00: failed command: READ DMA
[   49.888243] ata1.00: cmd c8/00:08:68:56:4d/00:00:00:00:00/e3 tag 0 dma 4096 in
[   49.888244]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[   49.888353] ata1.00: status: { DRDY }
[   54.928162] ata1: link is slow to respond, please be patient (ready=0)
[   59.912166] ata1: device not ready (errno=-16), forcing hardreset
[   59.912250] ata1: soft resetting link
[   60.102589] ata1.00: configured for UDMA/100
[   60.116522] ata1.01: configured for UDMA/33
[   60.119312] ata1.00: device reported invalid CHS sector 0
[   60.119321] ata1: EH complete
[   65.522209] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   69.196531] type=1400 audit(1299731296.862:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=914 comm="apparmor_parser"
[   69.197290] type=1400 audit(1299731296.862:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=914 comm="apparmor_parser"
[   69.263165] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   69.286631] ppdev: user-space parallel port driver
[   69.353016] type=1400 audit(1299731297.018:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1019 comm="apparmor_parser"
[   69.366734] type=1400 audit(1299731297.030:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1022 comm="apparmor_parser"
[   69.367345] type=1400 audit(1299731297.030:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1022 comm="apparmor_parser"
[   69.367680] type=1400 audit(1299731297.030:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1022 comm="apparmor_parser"
[   69.382138] type=1400 audit(1299731297.046:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1026 comm="apparmor_parser"
[   69.390121] type=1400 audit(1299731297.054:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1026 comm="apparmor_parser"
[   69.395093] type=1400 audit(1299731297.058:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1026 comm="apparmor_parser"
[   69.405286] type=1400 audit(1299731297.070:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1029 comm="apparmor_parser"
[   69.624037] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   69.674672] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.703587] b43-phy0: Radio hardware status changed to DISABLED
[   69.716353] Skipping EDID probe due to cached edid
[   70.216309] Skipping EDID probe due to cached edid
[   71.266038] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   71.269561] EXT4-fs (sda1): re-mounted. Opts: commit=0
[   72.756746] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   72.816200] b44 ssb1:0: eth0: Link is up at 100 Mbps, full duplex
[   72.816204] b44 ssb1:0: eth0: Flow control is off for TX and off for RX
[   72.816521] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   72.968248] Skipping EDID probe due to cached edid
[   73.468223] Skipping EDID probe due to cached edid
[   73.972229] Skipping EDID probe due to cached edid
[   74.460197] Skipping EDID probe due to cached edid
[   83.664095] eth0: no IPv6 routers present

```
Because, i dont no what im looking for.

However, thing is, as far as i can see that starts after fresh boot, but i could be wrong.

See readouts about "stolen memory" and "Skipping EDID probe due to cached edid" in some of the logs, these flag themselves to my untrained eye, but i dont think they are the cause. Plus they occur, at times, in log no where near crashes too.

Sorry for long post, but trying to provide details, you know the drill.

What shall i do?

How common is this behaviour in 10.10.

I thought linux was famous for being rock solid, i havnt turned my computer of since the son of our father's comeback tour or non-bland-generic-rehashed-mashup-wax-work-istoppedcaringaboutpeoplebecaseofshitlikethis pop songs were in the charts or whichever came first stable. So, what the friggidy friggin **** is wrong with ubuntu these days? 

This does not happen with an arch (gnome and openbox) or debian setup, on the same machine. But, ubuntu looks so pretty. As the caustic, famine stricken appearance of all system fonts in arch and debian are so depressing, no matter the subpixel smoothing or particular font choice i make, esp. firefox (which follows its own damn rules) and im too half stupid, half crazed to fix it (any tips in that regard by the way?) after iv wasted half a day (okay more) fiddling with the application and panel icons, as im so compu-vain, that there is barely time to fiddle with myself.

My priorities are ****** and im going mad.

Please help, ubuntu community, for i love you.

---

### Post by ikt on 2011-03-10
Are you able to paste in:

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

The full output of syslog after a freeze?

And to the best of your ability point out around what time the freeze happened, that would help me a lot :)

---

### Post by migel_wimtore on 2011-03-10
Well, i did it.

Heres the url:

[http://paste.ubuntu.com/578203/](http://paste.ubuntu.com/578203/).

Cheers.

---

### Post by migel_wimtore on 2011-03-10
On perusal im not sure if that will help us, as i think it must have happened before the 04:28:16 readouts, as that seems to be the startup (or not?), and prior to that there isnt a message for 6 mins.

Or perhaps you will see some other clue. If not, thanks for the offer anyways.

Is it possible that the system could freeze without leaving any trace?

---

### Post by migel_wimtore on 2011-03-11
Just had another crash.

Lame.

This is output of syslog, 5 minutes after crash:

[http://paste.ubuntu.com/579061/](http://paste.ubuntu.com/579061/).

Cheers.

---

### Post by s3a on 2011-03-11
How about using a different video card driver?

---

### Post by migel_wimtore on 2011-03-11
Hi S3A, thanks for the reply. 

How exactly would i do this?

I have checked my xorg.conf.failsafe and it simply says i have "vesa" as my driver.

When i run "lspci -v | less", it reports:

VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])

Which seems appropriate.

When i followed the instructions listed here:

[http://ubuntuforums.org/showthread.php?t=234231](http://ubuntuforums.org/showthread.php?t=234231)

it did not offer me any choices, but went straghit back to the command line prompt.

When i installed Arch i was able to select driver "xf86-video-intel" from a long list.

Thanks.

---

### Post by PeonDevelopments on 2011-03-18
I *think* I've had this problem before as well, on an Alienware M17 laptop.

I had Ubuntu 8.10 installed on it, then wiped it off in order to install Gentoo. That's when it started to act up, randomly freezing. Now, it wasn't Gentoo's fault that this started happening. 

I reinstalled Ubuntu 8.10 and found out that the laptop would rarely if ever freeze when powersavings were set to "performance", even when on battery. Otherwise, it would freeze up quite frequently.
I had to sell it eventually and put back the original OEM Vista installation. Guess what? This started to freeze up too. 

The problem may have been a driver issue, but that is unlikely.
Your problem sounds like a hardware issue.

It could either be

a) Your laptop video card is overheating. Unlikely, but Apple laptops do tend to get pretty heated and intel cards don't generally have the performance of ATI and nVidia.

Most likely it's
b) Your hard drive. I carried my laptop to and from school for a long time. It could have been bumped at any time, damaging the hard drive.
My suggestion is that you either install Ubuntu on an external drive if possible and test to see if it starts to freeze up on you.
If that isn't possible, for now, use a livecd to browse the internet and do your work. You can always mount your harddrive like a usb device if you need to load or save anything. (Nautilus should have an entry for it)
Better yet, use a live-usb stick. Then when you have access to another laptop hard drive or an external, test first then change the hard drive if it's successful. 
And I hope you are.

Cheers,

---

### Post by migel_wimtore on 2011-03-18
Hi Peondev. Thank for the response. 

I had come to believe it might be a driver issue as i had tried disabling various autostart apps, and i couldnt narrow it down to any particular process. I dont think it was a hardware issue either. At first, i was convinced it was, so i actually bought a new HD, imagine how gutted i was the first time ubuntu freezed-up.

Anyways, i have moved to debian, using openbox now. And so far (touch wood) no crashes. Though, the random freezes i was experiencing in ubuntu were so unpredictable that sometimes nearly a week could go by without a crash.

Your suggestion that it might be a CPU performance issue was an interesting one, as i previously had a 1.6ghz celeron m, which did not support scaling and i, dont think i experienced crashes with that. However, if i scale the new pentium m up in performance it makes the fan run full all the time, annoying. I used to run i8kmon to control fan speed but the new CPU overrides it in BIOS, or something.

Anyways, i dont think its a heat issue, at least my laptop never feels overly warm and hardware sensors never report heats over 55 decrees Celsius. That said however, it did tend to happen when the laptop had been on for a while, so that would lend credence to that theory.

Anyways, i am on debian now. I think it suits my need more anyways, i was only running in openbox with ubuntu, and i dont think i will have any need for the upcoming Unity interface, though i was curous about waylen.

Thanks though my (wo)man.

---

