---
title: "Back to my original problem... Virtual[crap]box"
date: 2010-07-27
forum: General Help
---

### Post by greenchance on 2010-07-27
Okay, I got everything unlocked, purged virtualbox, went into synaptic and started the reinstall process ALL FREAKING OVER AGAIN, and it still won't install. :mad:

I just keep getting this crap spit out at me:
```
anthony@desktop:~$ sudo apt-get install virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-3.2
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/49.4MB of archives.
After this operation, 96.7MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package virtualbox-3.2.
(Reading database ... 180331 files and directories currently installed.)
Unpacking virtualbox-3.2 (from .../virtualbox-3.2_3.2.6-63112~Ubuntu~lucid_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up virtualbox-3.2 (3.2.6-63112~Ubuntu~lucid) ...
addgroup: The group `vboxusers' already exists and is not a system group. Exiting.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
 * Starting VirtualBox kernel module                                            
 * modprobe vboxdrv failed. Please use 'dmesg' to find out why

Processing triggers for python-central ...
```

When I check dkms and gcc, they're the newest versions, and I appear to  have the proper headers as well. Is this program just garbage? It seems  to run fine for others, but I've literally spent all day staring at the  same stupid errors and gotten absolutely nowhere.
Initializing package states... Done

---

### Post by greenchance on 2010-07-27
If I type dmesg like it says, I get this:
```
[    0.295816] pci 0000:04:01.0: PME# supported from D3hot D3cold
[    0.295830] pci 0000:04:01.0: PME# disabled
[    0.295949] pci 0000:00:1e.0: transparent bridge
[    0.295963] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.295977] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.296069] pci_bus 0000:00: on NUMA node 0
[    0.296084] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.296587] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.296789] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.297104] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.297301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.327207] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.327584] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.327955] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.328350] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.328717] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.329098] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.329474] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.329851] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.330237] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.330257] vgaarb: loaded
[    0.330672] SCSI subsystem initialized
[    0.330920] libata version 3.00 loaded.
[    0.331177] usbcore: registered new interface driver usbfs
[    0.331233] usbcore: registered new interface driver hub
[    0.331336] usbcore: registered new device driver usb
[    0.331795] ACPI: WMI: Mapper loaded
[    0.331801] PCI: Using ACPI for IRQ routing
[    0.332332] NetLabel: Initializing
[    0.332338] NetLabel:  domain hash size = 128
[    0.332343] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.332387] NetLabel:  unlabeled traffic allowed by default
[    0.332586] hpet clockevent registered
[    0.332599] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.332614] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.332633] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.336534] Switching to clocksource tsc
[    0.342825] AppArmor: AppArmor Filesystem Enabled
[    0.342859] pnp: PnP ACPI init
[    0.342888] ACPI: bus type pnp registered
[    0.356728] pnp: PnP ACPI: found 17 devices
[    0.356737] ACPI: ACPI bus type pnp unregistered
[    0.356748] PnPBIOS: Disabled by ACPI PNP
[    0.356791] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.356820] system 00:08: ioport range 0x290-0x297 has been reserved
[    0.356848] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.356858] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.356868] system 00:09: ioport range 0x480-0x4bf has been reserved
[    0.356878] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.356887] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.356907] system 00:0b: iomem range 0xffc00000-0xfff7ffff has been reserved
[    0.356935] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.356945] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.356969] system 00:0f: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.356994] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.357004] system 00:10: iomem range 0xc0000-0xcffff could not be reserved
[    0.357014] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.357023] system 00:10: iomem range 0x100000-0x3fffffff could not be reserved
[    0.392350] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.392363] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.392378] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.392389] pci 0000:00:01.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.392407] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.392417] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.392432] pci 0000:00:1c.0:   MEM window: 0xfea00000-0xfeafffff
[    0.392446] pci 0000:00:1c.0:   PREFETCH window: 0x000000fc000000-0x000000fdffffff
[    0.392466] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.392475] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.392490] pci 0000:00:1c.1:   MEM window: 0xfe900000-0xfe9fffff
[    0.392501] pci 0000:00:1c.1:   PREFETCH window: 0x00000040000000-0x000000401fffff
[    0.392520] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.392530] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.392545] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.392555] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.392594]   alloc irq_desc for 16 on node -1
[    0.392603]   alloc kstat_irqs on node -1
[    0.392618] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.392633] pci 0000:00:01.0: setting latency timer to 64
[    0.392657] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.392672] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.392686] pci 0000:00:1c.0: setting latency timer to 64
[    0.392707] pci 0000:00:1c.1: enabling device (0106 -> 0107)
[    0.392717]   alloc irq_desc for 17 on node -1
[    0.392725]   alloc kstat_irqs on node -1
[    0.392736] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.392750] pci 0000:00:1c.1: setting latency timer to 64
[    0.392770] pci 0000:00:1e.0: setting latency timer to 64
[    0.392784] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.392794] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.392807] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.392814] pci_bus 0000:01: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.392823] pci_bus 0000:01: resource 2 pref mem [0xe8000000-0xefffffff]
[    0.392833] pci_bus 0000:03: resource 0 io:  [0x1000-0x1fff]
[    0.392843] pci_bus 0000:03: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.392852] pci_bus 0000:03: resource 2 pref mem [0xfc000000-0xfdffffff]
[    0.392862] pci_bus 0000:02: resource 0 io:  [0x2000-0x2fff]
[    0.392867] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.392876] pci_bus 0000:02: resource 2 pref mem [0x40000000-0x401fffff]
[    0.392885] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.392891] pci_bus 0000:04: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.392900] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.392909] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.393025] NET: Registered protocol family 2
[    0.393359] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.394428] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.395873] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.396598] TCP: Hash tables configured (established 131072 bind 65536)
[    0.396604] TCP reno registered
[    0.396842] NET: Registered protocol family 1
[    0.397108] pci 0000:01:00.0: Boot video device
[    0.397661] cpufreq-nforce2: No nForce2 chipset.
[    0.397763] Scanning for low memory corruption every 60 seconds
[    0.398107] audit: initializing netlink socket (disabled)
[    0.398140] type=2000 audit(1280265834.394:1): initialized
[    0.420875] highmem bounce pool size: 64 pages
[    0.420895] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.426081] VFS: Disk quotas dquot_6.5.2
[    0.426316] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.428420] fuse init (API version 7.13)
[    0.428732] msgmni has been set to 1716
[    0.429443] alg: No test for stdrng (krng)
[    0.429640] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.429650] io scheduler noop registered
[    0.429656] io scheduler anticipatory registered
[    0.429664] io scheduler deadline registered
[    0.429810] io scheduler cfq registered (default)
[    0.430298]   alloc irq_desc for 24 on node -1
[    0.430307]   alloc kstat_irqs on node -1
[    0.430332] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.430355] pcieport 0000:00:01.0: setting latency timer to 64
[    0.430672]   alloc irq_desc for 25 on node -1
[    0.430678]   alloc kstat_irqs on node -1
[    0.430702] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.430726] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.431090]   alloc irq_desc for 26 on node -1
[    0.431096]   alloc kstat_irqs on node -1
[    0.431119] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.431144] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.431436] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.431717] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.432060] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.432074] ACPI: Power Button [PWRB]
[    0.432239] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.432249] ACPI: Power Button [PWRF]
[    0.434326] ACPI: SSDT 3ffb00f0 00214 (v01    AMI   CPU1PM 00000001 INTL 20051117)
[    0.435309] processor LNXCPU:00: registered as cooling_device0
[    0.436405] ACPI: SSDT 3ffb0310 00143 (v01    AMI   CPU2PM 00000001 INTL 20051117)
[    0.437309] processor LNXCPU:01: registered as cooling_device1
[    0.451100] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.451349] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.452716] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.455129] isapnp: Scanning for PnP cards...
[    0.456431] brd: module loaded
[    0.458109] loop: module loaded
[    0.458402] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.458686] ata_piix 0000:00:1f.1: version 2.13
[    0.458721]   alloc irq_desc for 18 on node -1
[    0.458730]   alloc kstat_irqs on node -1
[    0.458750] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.458862] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.459061] scsi0 : ata_piix
[    0.459316] scsi1 : ata_piix
[    0.464444] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.464454] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.464522]   alloc irq_desc for 19 on node -1
[    0.464532]   alloc kstat_irqs on node -1
[    0.464550] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.464565] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.464671] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.464814] scsi2 : ata_piix
[    0.464994] scsi3 : ata_piix
[    0.469641] ata3: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 19
[    0.469651] ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 19
[    0.470971] Fixed MDIO Bus: probed
[    0.471110] PPP generic driver version 2.4.2
[    0.471251] tun: Universal TUN/TAP device driver, 1.6
[    0.471257] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.471559] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.471614]   alloc irq_desc for 23 on node -1
[    0.471624]   alloc kstat_irqs on node -1
[    0.471642] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.471681] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.471692] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.471808] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.471863] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.471892] ehci_hcd 0000:00:1d.7: debug port 1
[    0.475798] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.475836] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe7fbc00
[    0.505250] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.505604] usb usb1: configuration #1 chosen from 1 choice
[    0.505711] hub 1-0:1.0: USB hub found
[    0.505740] hub 1-0:1.0: 8 ports detected
[    0.505978] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.506037] uhci_hcd: USB Universal Host Controller Interface driver
[    0.506142] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.506195] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.506209] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.506329] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.506390] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c480
[    0.506685] usb usb2: configuration #1 chosen from 1 choice
[    0.506787] hub 2-0:1.0: USB hub found
[    0.506811] hub 2-0:1.0: 2 ports detected
[    0.506961] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.506980] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.506990] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.507097] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.507152] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c800
[    0.507457] usb usb3: configuration #1 chosen from 1 choice
[    0.507554] hub 3-0:1.0: USB hub found
[    0.507578] hub 3-0:1.0: 2 ports detected
[    0.507714] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.507734] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.507743] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.507874] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.507950] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c880
[    0.508246] usb usb4: configuration #1 chosen from 1 choice
[    0.508338] hub 4-0:1.0: USB hub found
[    0.508361] hub 4-0:1.0: 2 ports detected
[    0.508504] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.508523] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.508533] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.508635] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.508709] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000cc00
[    0.508990] usb usb5: configuration #1 chosen from 1 choice
[    0.509082] hub 5-0:1.0: USB hub found
[    0.509103] hub 5-0:1.0: 2 ports detected
[    0.509436] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.509445] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.510384] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.519289] mice: PS/2 mouse device common for all mice
[    0.519696] rtc_cmos 00:03: RTC can wake from S4
[    0.519828] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.519898] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.520270] device-mapper: uevent: version 1.0.3
[    0.520588] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.548556] device-mapper: multipath: version 1.1.0 loaded
[    0.548567] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.549061] EISA: Probing bus 0 at eisa.0
[    0.549081] Cannot allocate resource for EISA slot 1
[    0.549087] Cannot allocate resource for EISA slot 2
[    0.549142] EISA: Detected 0 cards.
[    0.724596] cpuidle: using governor ladder
[    0.724602] cpuidle: using governor menu
[    0.726248] TCP cubic registered
[    0.726729] NET: Registered protocol family 10
[    0.728363] lo: Disabled Privacy Extensions
[    0.729533] NET: Registered protocol family 17
[    0.731085] Using IPI No-Shortcut mode
[    0.731400] PM: Resume from disk failed.
[    0.731439] registered taskstats version 1
[    0.732431]   Magic number: 2:88:400
[    0.732649] rtc_cmos 00:03: setting system clock to 2010-07-27 21:23:55 UTC (1280265835)
[    0.732663] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.732668] EDD information not available.
[    0.739538] ata1.00: ATAPI: TSSTcorpDVD-ROM TS-H352C, DE02, max UDMA/33
[    0.739659] ata1.01: ATAPI: ASUS    DRW-1608P3S, 1.24, max UDMA/66
[    0.771118] ata1.00: configured for UDMA/33
[    0.786934] ata1.01: configured for UDMA/66
[    0.820646] isapnp: No Plug & Play device found
[    0.821571] ata4.00: ATA-7: WDC WD2500JS-75NCB3, 10.02E04, max UDMA/133
[    0.821584] ata4.00: 488281250 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.822278] scsi 0:0:0:0: CD-ROM            TSSTcorp DVD-ROM TS-H352C DE02 PQ: 0 ANSI: 5
[    0.831128] ata4.00: configured for UDMA/133
[    0.833621] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    0.833634] Uniform CD-ROM driver Revision: 3.20
[    0.833961] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.834140] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.840956] scsi 0:0:1:0: CD-ROM            ASUS     DRW-1608P3S      1.24 PQ: 0 ANSI: 5
[    0.860511] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.860795] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    0.860945] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    0.873037] Freeing initrd memory: 7783k freed
[    1.228047] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.397787] usb 2-1: configuration #1 chosen from 1 choice
[    1.640163] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    1.803632] usb 2-2: configuration #1 chosen from 1 choice
[    1.810525] hub 2-2:1.0: USB hub found
[    1.811467] hub 2-2:1.0: 4 ports detected
[    2.056042] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.224391] usb 3-1: configuration #1 chosen from 1 choice
[    2.301456] usb 2-2.1: new low speed USB device using uhci_hcd and address 4
[    2.443640] usb 2-2.1: configuration #1 chosen from 1 choice
[    2.553446] usb 2-2.4: new full speed USB device using uhci_hcd and address 5
[    2.657441] usb 2-2.4: not running at top speed; connect to a high speed hub
[    2.691620] usb 2-2.4: configuration #1 chosen from 1 choice
[    5.756035] ata3: link is slow to respond, please be patient (ready=0)
[   10.572012] ata3: SRST failed (errno=-16)
[   15.768013] ata3: link is slow to respond, please be patient (ready=0)
[   20.584013] ata3: SRST failed (errno=-16)
[   25.780013] ata3: link is slow to respond, please be patient (ready=0)
[   55.628013] ata3: SRST failed (errno=-16)
[   60.656013] ata3: SRST failed (errno=-16)
[   60.656018] ata3: reset failed, giving up
[   60.656165] scsi 3:0:0:0: Direct-Access     ATA      WDC WD2500JS-75N 10.0 PQ: 0 ANSI: 5
[   60.656325] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   60.656350] sd 3:0:0:0: [sda] 488281250 512-byte logical blocks: (250 GB/232 GiB)
[   60.656431] sd 3:0:0:0: [sda] Write Protect is off
[   60.656435] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   60.656471] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   60.656663]  sda: sda1 sda2 < sda5 >
[   60.696540] sd 3:0:0:0: [sda] Attached SCSI disk
[   60.696557] Freeing unused kernel memory: 660k freed
[   60.697019] Write protecting the kernel text: 4680k
[   60.697071] Write protecting the kernel read-only data: 1840k
[   60.719475] udev: starting version 151
[   60.831516] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   60.831529] atl1 0000:02:00.0: setting latency timer to 64
[   60.831554] atl1 0000:02:00.0: version 2.1.3
[   60.873448] Floppy drive(s): fd0 is 1.44M
[   60.879262] usbcore: registered new interface driver hiddev
[   60.884605] Initializing USB Mass Storage driver...
[   60.884772] scsi4 : SCSI emulation for USB Mass Storage devices
[   60.884970] usbcore: registered new interface driver usb-storage
[   60.884974] USB Mass Storage support registered.
[   60.885093] usb-storage: device found at 5
[   60.885096] usb-storage: waiting for device to settle before scanning
[   60.892403] FDC 0 is a post-1991 82077
[   60.892648] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[   60.892780] generic-usb 0003:0461:4D15.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-1/input0
[   60.913334] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input4
[   60.913417] generic-usb 0003:049F:000E.0002: input,hidraw1: USB HID v1.00 Keyboard [Compaq Compaq Internet Keyboard] on usb-0000:00:1d.0-2.1/input0
[   61.035976] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2.1/2-2.1:1.1/input/input5
[   61.036161] generic-usb 0003:049F:000E.0003: input,hiddev96,hidraw2: USB HID v1.00 Device [Compaq Compaq Internet Keyboard] on usb-0000:00:1d.0-2.1/input1
[   61.036195] usbcore: registered new interface driver usbhid
[   61.036199] usbhid: v2.6:USB HID core driver
[   61.083724] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   62.449874] Adding 3002360k swap on /dev/sda5.  Priority:-1 extents:1 across:3002360k 
[   62.797340] udev: starting version 151
[   63.678911] lirc_dev: IR Remote Control driver registered, major 61 
[   63.753587] type=1505 audit(1280265898.519:2):  operation="profile_load" pid=465 name="/sbin/dhclient3"
[   63.754228] type=1505 audit(1280265898.519:3):  operation="profile_load" pid=465 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   63.754572] type=1505 audit(1280265898.519:4):  operation="profile_load" pid=465 name="/usr/lib/connman/scripts/dhclient-script"
[   64.000077] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   64.000082] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   64.007711] lp: driver loaded but no devices found
[   64.018725] parport_pc 00:07: reported by Plug and Play ACPI
[   64.018838] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   64.112036] usb 2-1: reset full speed USB device using uhci_hcd and address 2
[   64.116314] lp0: using parport0 (interrupt-driven).
[   64.181805] ppdev: user-space parallel port driver
[   64.216795] Linux agpgart interface v0.103
[   64.259946] lirc_dev: lirc_register_driver: sample_rate: 0
[   64.260396] [drm] Initialized drm 1.1.0 20060810
[   64.264785] lirc_mceusb[2]: Philips eHome Infrared Transceiver on usb2:2
[   64.264849] usbcore: registered new interface driver lirc_mceusb
[   64.268610] intel_rng: FWH not detected
[   64.412681] [drm] radeon defaulting to kernel modesetting.
[   64.412685] [drm] radeon kernel modesetting enabled.
[   64.412740] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   64.412747] radeon 0000:01:00.0: setting latency timer to 64
[   64.414485] [drm] radeon: Initializing kernel modesetting.
[   64.414651] [drm] register mmio base: 0xFE8E0000
[   64.414655] [drm] register mmio size: 65536
[   64.416879] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   64.416894] [drm] Generation 2 PCI interface, using max accessible memory
[   64.416897] [drm] radeon: VRAM 128M
[   64.416900] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   64.416902] [drm] radeon: GTT 512M
[   64.416904] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   64.416942]   alloc irq_desc for 27 on node -1
[   64.416945]   alloc kstat_irqs on node -1
[   64.416959] radeon 0000:01:00.0: irq 27 for MSI/MSI-X
[   64.416966] [drm] radeon: using MSI.
[   64.416991] [drm] radeon: irq initialized.
[   64.417751] [drm] Detected VRAM RAM=128M, BAR=128M
[   64.417756] [drm] RAM width 128bits DDR
[   64.418023] [TTM] Zone  kernel: Available graphics memory: 443536 kiB.
[   64.418027] [TTM] Zone highmem: Available graphics memory: 512980 kiB.
[   64.418045] [drm] radeon: 128M of VRAM memory ready
[   64.418048] [drm] radeon: 512M of GTT memory ready.
[   64.418071] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   64.418702] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   64.418740] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   64.418753] [drm] radeon: cp idle (0x10000C03)
[   64.418811] [drm] Loading R300 Microcode
[   64.418924] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   64.550273] [drm] radeon: ring at 0x0000000020000000
[   64.550296] [drm] ring test succeeded in 1 usecs
[   64.551006] [drm] radeon: ib pool ready.
[   64.551093] [drm] ib test succeeded in 0 usecs
[   64.551411] [drm] Default TV standard: NTSC
[   64.551414] [drm] 27.000000000 MHz TV ref clk
[   64.551418] [drm] DFP table revision: 4
[   64.551741] [drm] Default TV standard: NTSC
[   64.551744] [drm] 27.000000000 MHz TV ref clk
[   64.551894] [drm] Radeon Display Connectors
[   64.551897] [drm] Connector 0:
[   64.551899] [drm]   VGA
[   64.551902] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   64.551904] [drm]   Encoders:
[   64.551906] [drm]     CRT1: INTERNAL_DAC1
[   64.551909] [drm] Connector 1:
[   64.551910] [drm]   DVI-I
[   64.551912] [drm]   HPD1
[   64.551915] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   64.551917] [drm]   Encoders:
[   64.551919] [drm]     CRT2: INTERNAL_DAC2
[   64.551921] [drm]     DFP1: INTERNAL_TMDS1
[   64.551923] [drm] Connector 2:
[   64.551924] [drm]   S-video
[   64.551926] [drm]   Encoders:
[   64.551928] [drm]     TV1: INTERNAL_DAC2
[   64.783351] [drm] fb mappable at 0xE80C0000
[   64.783355] [drm] vram apper at 0xE8000000
[   64.783358] [drm] size 5242880
[   64.783360] [drm] fb depth is 24
[   64.783362] [drm]    pitch is 5120
[   64.783533] fb0: radeondrmfb frame buffer device
[   64.783537] registered panic notifier
[   64.783543] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   65.089201] vga16fb: initializing
[   65.089206] vga16fb: mapped to 0xc00a0000
[   65.089212] vga16fb: not registering due to another framebuffer present
[   65.358632] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   65.358663] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   65.498573] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   65.529513] Console: switching to colour frame buffer device 160x64
[   65.885795] usb-storage: device scan complete
[   65.888783] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[   65.890344] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   65.896763] sd 4:0:0:0: [sdb] 3966976 512-byte logical blocks: (2.03 GB/1.89 GiB)
[   65.899753] sd 4:0:0:0: [sdb] Write Protect is off
[   65.899758] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   65.899762] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   65.914753] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   65.914810]  sdb:
[   65.930403] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   65.930475] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   68.520399] type=1505 audit(1280265903.287:5):  operation="profile_load" pid=793 name="/usr/share/gdm/guest-session/Xsession"
[   68.522699] type=1505 audit(1280265903.287:6):  operation="profile_replace" pid=794 name="/sbin/dhclient3"
[   68.523357] type=1505 audit(1280265903.287:7):  operation="profile_replace" pid=794 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   68.523721] type=1505 audit(1280265903.287:8):  operation="profile_replace" pid=794 name="/usr/lib/connman/scripts/dhclient-script"
[   68.548713] type=1505 audit(1280265903.315:9):  operation="profile_load" pid=795 name="/usr/bin/evince"
[   68.561846] type=1505 audit(1280265903.327:10):  operation="profile_load" pid=795 name="/usr/bin/evince-previewer"
[   68.566977] type=1505 audit(1280265903.331:11):  operation="profile_load" pid=795 name="/usr/bin/evince-thumbnailer"
[   68.681390]   alloc irq_desc for 28 on node -1
[   68.681394]   alloc kstat_irqs on node -1
[   68.681411] atl1 0000:02:00.0: irq 28 for MSI/MSI-X
[   68.681507] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[   73.469009] CPU0 attaching NULL sched-domain.
[   73.469016] CPU1 attaching NULL sched-domain.
[   73.496105] CPU0 attaching sched-domain:
[   73.496110]  domain 0: span 0-1 level CPU
[   73.496114]   groups: 0 1
[   73.496122] CPU1 attaching sched-domain:
[   73.496125]  domain 0: span 0-1 level CPU
[   73.496128]   groups: 1 0
[   76.164369] CPU0 attaching NULL sched-domain.
[   76.164376] CPU1 attaching NULL sched-domain.
[   76.184941] CPU0 attaching sched-domain:
[   76.184946]  domain 0: span 0-1 level CPU
[   76.184950]   groups: 0 1
[   76.184958] CPU1 attaching sched-domain:
[   76.184961]  domain 0: span 0-1 level CPU
[   76.184964]   groups: 1 0
[   79.596009] eth0: no IPv6 routers present

```

---

### Post by greenchance on 2010-07-27
Okay, now I can run it and make a system, but when I try to open said system, I get:

```
 p, li { white-space: pre-wrap; }  ernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000FF]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

```

Except that, as I said DKMS is installed and is the newest version!

I attempt to run the vboxdrv setup as root, and I get:
```
anthony@desktop:~$ gksudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
anthony@desktop:~$ 

```

So it seems I'm getting closer, but I'm still quite stuck.

---

### Post by spcwingo on 2010-07-27
You do have the package build-essential installed, correct?  If not it's just a:

```
sudo apt-get install build-essential
```

away!  :)

---

