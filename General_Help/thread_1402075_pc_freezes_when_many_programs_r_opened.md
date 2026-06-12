---
title: "pc freezes when many programs r opened"
date: 2010-02-08
forum: General Help
---

### Post by mohabic on 2010-02-08
dear all

im currently using ubuntu 9.10 in 30gb partition, when i open google chrome, netbeans, pidgin messenger and mysql it causes pc o freeze, which i has to shut down pc by cutting off electricity. 

is that due to virtual memory ??
or what is the problem ?
how can it be solved ?!

thanks for help

---

### Post by Crafty Kisses on 2010-02-08
What are your system specs? Have you tried running these programs in a terminal and see if you get any errors? What is the output of the following?
```
dmesg
```

---

### Post by mohabic on 2010-02-10
> **Crafty Kisses said:**
> What are your system specs? Have you tried running these programs in a terminal and see if you get any errors? What is the output of the following?
```
dmesg
```

that is the o/p
[    0.176563] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.176566] PCI: Using configuration type 1 for base access
[    0.180021] bio: create slab <bio-0> at 0
[    0.181784] ACPI: EC: EC description table is found, configuring boot EC
[    0.191374] ACPI: Interpreter enabled
[    0.191381] ACPI: (supports S0 S1 S3 S4 S5)
[    0.191414] ACPI: Using IOAPIC for interrupt routing
[    0.192950] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.196450] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.196453] PCI: Using MMCONFIG for extended config space
[    0.207309] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.207312] ACPI: EC: driver started in poll mode
[    0.211638] ACPI Warning: Incorrect checksum in table [ATKG] - B0, should be 4A 20090521 tbutils-246
[    0.211932] ACPI: No dock devices found.
[    0.212549] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.212674] pci 0000:00:02.0: reg 10 64bit mmio: [0xfeb00000-0xfebfffff]
[    0.212685] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.212691] pci 0000:00:02.0: reg 20 io port: [0xec00-0xec07]
[    0.212748] pci 0000:00:02.1: reg 10 64bit mmio: [0xfe900000-0xfe9fffff]
[    0.212861] pci 0000:00:1a.0: reg 20 io port: [0xe000-0xe01f]
[    0.212923] pci 0000:00:1a.1: reg 20 io port: [0xdc00-0xdc1f]
[    0.212994] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfeaff400-0xfeaff7ff]
[    0.213058] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.213064] pci 0000:00:1a.7: PME# disabled
[    0.213114] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfeaf8000-0xfeafbfff]
[    0.213170] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.213175] pci 0000:00:1b.0: PME# disabled
[    0.213252] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.213257] pci 0000:00:1c.0: PME# disabled
[    0.213337] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.213342] pci 0000:00:1c.1: PME# disabled
[    0.213422] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.213427] pci 0000:00:1c.2: PME# disabled
[    0.213490] pci 0000:00:1d.0: reg 20 io port: [0xd880-0xd89f]
[    0.213553] pci 0000:00:1d.1: reg 20 io port: [0xd800-0xd81f]
[    0.213615] pci 0000:00:1d.2: reg 20 io port: [0xd480-0xd49f]
[    0.213686] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfeaff000-0xfeaff3ff]
[    0.213751] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.213756] pci 0000:00:1d.7: PME# disabled
[    0.213908] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.213913] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.213917] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0300 (mask 0003)
[    0.213924] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0250 (mask 000f)
[    0.213974] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.213982] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.213990] pci 0000:00:1f.1: reg 18 io port: [0x8f0-0x8f7]
[    0.213998] pci 0000:00:1f.1: reg 1c io port: [0x8f8-0x8fb]
[    0.214007] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.214074] pci 0000:00:1f.2: reg 10 io port: [0xe880-0xe887]
[    0.214081] pci 0000:00:1f.2: reg 14 io port: [0xe800-0xe803]
[    0.214089] pci 0000:00:1f.2: reg 18 io port: [0xe480-0xe487]
[    0.214097] pci 0000:00:1f.2: reg 1c io port: [0xe400-0xe403]
[    0.214104] pci 0000:00:1f.2: reg 20 io port: [0xe080-0xe09f]
[    0.214112] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfeaff800-0xfeafffff]
[    0.214150] pci 0000:00:1f.2: PME# supported from D3hot
[    0.214154] pci 0000:00:1f.2: PME# disabled
[    0.214342] pci 0000:00:1c.2: bridge io port: [0xb000-0xbfff]
[    0.214347] pci 0000:00:1c.2: bridge 32bit mmio: [0xfde00000-0xfe5fffff]
[    0.214355] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xbdf00000-0xbfefffff]
[    0.214410] pci 0000:05:07.0: reg 10 io port: [0xc800-0xc8ff]
[    0.214419] pci 0000:05:07.0: reg 14 32bit mmio: [0xfe6ffc00-0xfe6ffcff]
[    0.214473] pci 0000:05:07.0: supports D1 D2
[    0.214476] pci 0000:05:07.0: PME# supported from D1 D2 D3hot D3cold
[    0.214482] pci 0000:05:07.0: PME# disabled
[    0.214529] pci 0000:00:1e.0: transparent bridge
[    0.214534] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.214539] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe600000-0xfe6fffff]
[    0.214569] pci_bus 0000:00: on NUMA node 0
[    0.214575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.214820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.214901] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.215055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.236128] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    0.236308] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 12)
[    0.236485] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 12)
[    0.236660] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 12)
[    0.236836] ACPI: PCI Interrupt Link [LNKE] (IRQs *6)
[    0.237006] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    0.237181] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    0.237356] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    0.237589] SCSI subsystem initialized
[    0.237628] libata version 3.00 loaded.
[    0.237628] usbcore: registered new interface driver usbfs
[    0.237628] usbcore: registered new interface driver hub
[    0.237628] usbcore: registered new device driver usb
[    0.237628] ACPI: WMI: Mapper loaded
[    0.237628] PCI: Using ACPI for IRQ routing
[    0.248010] Bluetooth: Core ver 2.15
[    0.248026] NET: Registered protocol family 31
[    0.248026] Bluetooth: HCI device and connection manager initialized
[    0.248026] Bluetooth: HCI socket layer initialized
[    0.248026] NetLabel: Initializing
[    0.248026] NetLabel:  domain hash size = 128
[    0.248026] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.248040] NetLabel:  unlabeled traffic allowed by default
[    0.248076] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.248083] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.264021] pnp: PnP ACPI init
[    0.264048] ACPI: bus type pnp registered
[    0.267377] pnp: PnP ACPI: found 13 devices
[    0.267380] ACPI: ACPI bus type pnp unregistered
[    0.267385] PnPBIOS: Disabled by ACPI PNP
[    0.267398] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.267409] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.267413] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.267417] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.267420] system 00:08: ioport range 0x500-0x53f has been reserved
[    0.267424] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.267427] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.267431] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.267434] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.267438] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.267445] system 00:0a: ioport range 0x250-0x253 has been reserved
[    0.267449] system 00:0a: ioport range 0x256-0x25f has been reserved
[    0.267452] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.267456] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.267463] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.267470] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.267473] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.267477] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.267480] system 00:0c: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.302187] AppArmor: AppArmor Filesystem Enabled
[    0.302244] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.302246] pci 0000:00:1c.0:   IO window: disabled
[    0.302252] pci 0000:00:1c.0:   MEM window: disabled
[    0.302257] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.302262] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.302264] pci 0000:00:1c.1:   IO window: disabled
[    0.302270] pci 0000:00:1c.1:   MEM window: disabled
[    0.302275] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.302280] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.302284] pci 0000:00:1c.2:   IO window: 0xb000-0xbfff
[    0.302290] pci 0000:00:1c.2:   MEM window: 0xfde00000-0xfe5fffff
[    0.302296] pci 0000:00:1c.2:   PREFETCH window: 0x000000bdf00000-0x000000bfefffff
[    0.302304] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.302307] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.302314] pci 0000:00:1e.0:   MEM window: 0xfe600000-0xfe6fffff
[    0.302319] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.302334]   alloc irq_desc for 16 on node -1
[    0.302337]   alloc kstat_irqs on node -1
[    0.302344] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.302351] pci 0000:00:1c.0: setting latency timer to 64
[    0.302359]   alloc irq_desc for 17 on node -1
[    0.302361]   alloc kstat_irqs on node -1
[    0.302366] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.302371] pci 0000:00:1c.1: setting latency timer to 64
[    0.302379]   alloc irq_desc for 18 on node -1
[    0.302381]   alloc kstat_irqs on node -1
[    0.302386] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.302391] pci 0000:00:1c.2: setting latency timer to 64
[    0.302399] pci 0000:00:1e.0: setting latency timer to 64
[    0.302404] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.302408] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.302411] pci_bus 0000:03: resource 0 io:  [0xb000-0xbfff]
[    0.302414] pci_bus 0000:03: resource 1 mem: [0xfde00000-0xfe5fffff]
[    0.302417] pci_bus 0000:03: resource 2 pref mem [0xbdf00000-0xbfefffff]
[    0.302420] pci_bus 0000:05: resource 0 io:  [0xc000-0xcfff]
[    0.302423] pci_bus 0000:05: resource 1 mem: [0xfe600000-0xfe6fffff]
[    0.302426] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.302429] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.302475] NET: Registered protocol family 2
[    0.302596] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.302996] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.303567] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.303966] TCP: Hash tables configured (established 131072 bind 65536)
[    0.303969] TCP reno registered
[    0.304148] NET: Registered protocol family 1
[    0.304240] Trying to unpack rootfs image as initramfs...
[    0.501672] Switched to high resolution mode on CPU 1
[    0.504037] Switched to high resolution mode on CPU 0
[    0.523478] Freeing initrd memory: 7470k freed
[    0.529027] Simple Boot Flag at 0x51 set to 0x1
[    0.529250] cpufreq-nforce2: No nForce2 chipset.
[    0.529284] Scanning for low memory corruption every 60 seconds
[    0.529416] audit: initializing netlink socket (disabled)
[    0.529441] type=2000 audit(1265859012.528:1): initialized
[    0.539416] highmem bounce pool size: 64 pages
[    0.539422] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.541128] VFS: Disk quotas dquot_6.5.2
[    0.541204] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.541828] fuse init (API version 7.12)
[    0.541923] msgmni has been set to 1732
[    0.542171] alg: No test for stdrng (krng)
[    0.542187] io scheduler noop registered
[    0.542189] io scheduler anticipatory registered
[    0.542192] io scheduler deadline registered
[    0.542242] io scheduler cfq registered (default)
[    0.542256] pci 0000:00:02.0: Boot video device
[    0.616443]   alloc irq_desc for 24 on node -1
[    0.616446]   alloc kstat_irqs on node -1
[    0.616459] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.616470] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.616604]   alloc irq_desc for 25 on node -1
[    0.616606]   alloc kstat_irqs on node -1
[    0.616615] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.616625] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.616760]   alloc irq_desc for 26 on node -1
[    0.616763]   alloc kstat_irqs on node -1
[    0.616771] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.616781] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.616887] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.617294] pciehp 0000:00:1c.2:pcie04: HPC vendor_id 8086 device_id 2843 ss_vid 0 ss_did 0
[    0.617342] pciehp 0000:00:1c.2:pcie04: service driver pciehp loaded
[    0.617352] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.617582] ACPI: AC Adapter [AC0] (on-line)
[    0.617653] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.617657] ACPI: Power Button [PWRF]
[    0.617730] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.617733] ACPI: Power Button [PWRB]
[    0.617783] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.617790] ACPI: Sleep Button [SLPB]
[    0.617841] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.618032] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.625315] ACPI: Lid Switch [LID]
[    0.626314] ACPI: SSDT 3f7b83d0 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.627121] ACPI: SSDT 3f7b86b0 0060F (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.628351] Monitor-Mwait will be used to enter C-1 state
[    0.628385] Monitor-Mwait will be used to enter C-2 state
[    0.628412] Monitor-Mwait will be used to enter C-3 state
[    0.628421] Marking TSC unstable due to TSC halts in idle
[    0.628444] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.628477] processor LNXCPU:00: registered as cooling_device0
[    0.628482] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.628913] ACPI: SSDT 3f7b8300 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.629511] ACPI: SSDT 3f7b8620 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.630854] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.630882] processor LNXCPU:01: registered as cooling_device1
[    0.630887] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.636867] ACPI Warning: \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found Processor, expected Reference 20090521 nspredef-946
[    0.636877] ACPI: Expecting a [Reference] package element, found type C
[    0.636879] ACPI: Invalid passive threshold
[    0.638988] thermal LNXTHERM:01: registered as thermal_zone0
[    0.638999] ACPI: Thermal Zone [THRM] (77 C)
[    0.639071] isapnp: Scanning for PnP cards...
[    0.764526] ACPI: Battery Slot [BAT0] (battery present)
[    0.992555] isapnp: No Plug & Play device found
[    0.993930] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.995518] brd: module loaded
[    0.996042] loop: module loaded
[    0.996127] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.996215] ahci 0000:00:1f.2: version 3.0
[    0.996233]   alloc irq_desc for 20 on node -1
[    0.996235]   alloc kstat_irqs on node -1
[    0.996244] ahci 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.996277]   alloc irq_desc for 27 on node -1
[    0.996279]   alloc kstat_irqs on node -1
[    0.996289] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    0.996356] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    0.996360] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    0.996366] ahci 0000:00:1f.2: setting latency timer to 64
[    1.008095] scsi0 : ahci
[    1.008220] scsi1 : ahci
[    1.008281] scsi2 : ahci
[    1.008491] ata1: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff900 irq 27
[    1.008495] ata2: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaff980 irq 27
[    1.008499] ata3: SATA max UDMA/133 abar m2048@0xfeaff800 port 0xfeaffa00 irq 27
[    1.008567] ata_piix 0000:00:1f.1: version 2.13
[    1.008581] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.008633] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.008710] scsi3 : ata_piix
[    1.008774] scsi4 : ata_piix
[    1.010005] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.010009] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.011019] Fixed MDIO Bus: probed
[    1.011059] PPP generic driver version 2.4.2
[    1.011190] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.011213] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.011232] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.011236] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.011294] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.015199] ehci_hcd 0000:00:1a.7: debug port 1
[    1.015207] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.015224] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfeaff400
[    1.019341] ata5: port disabled. ignoring.
[    1.029011] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.029103] usb usb1: configuration #1 chosen from 1 choice
[    1.029136] hub 1-0:1.0: USB hub found
[    1.029146] hub 1-0:1.0: 4 ports detected
[    1.029213]   alloc irq_desc for 23 on node -1
[    1.029216]   alloc kstat_irqs on node -1
[    1.029223] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.029234] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.029238] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.029275] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.033173] ehci_hcd 0000:00:1d.7: debug port 1
[    1.033180] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.033197] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfeaff000
[    1.048014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.048084] usb usb2: configuration #1 chosen from 1 choice
[    1.048119] hub 2-0:1.0: USB hub found
[    1.048126] hub 2-0:1.0: 6 ports detected
[    1.048192] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.048213] uhci_hcd: USB Universal Host Controller Interface driver
[    1.048253] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.048261] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.048265] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.048308] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.048342] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e000
[    1.048430] usb usb3: configuration #1 chosen from 1 choice
[    1.048460] hub 3-0:1.0: USB hub found
[    1.048468] hub 3-0:1.0: 2 ports detected
[    1.048520]   alloc irq_desc for 21 on node -1
[    1.048522]   alloc kstat_irqs on node -1
[    1.048528] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.048534] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.048538] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.048573] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.048605] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000dc00
[    1.048697] usb usb4: configuration #1 chosen from 1 choice
[    1.048726] hub 4-0:1.0: USB hub found
[    1.048734] hub 4-0:1.0: 2 ports detected
[    1.048785] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.048792] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.048796] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.048830] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.048854] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d880
[    1.048942] usb usb5: configuration #1 chosen from 1 choice
[    1.048972] hub 5-0:1.0: USB hub found
[    1.048980] hub 5-0:1.0: 2 ports detected
[    1.049039]   alloc irq_desc for 19 on node -1
[    1.049042]   alloc kstat_irqs on node -1
[    1.049047] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.049053] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.049057] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.049095] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.049127] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[    1.049218] usb usb6: configuration #1 chosen from 1 choice
[    1.049248] hub 6-0:1.0: USB hub found
[    1.049255] hub 6-0:1.0: 2 ports detected
[    1.049306] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.049313] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.049316] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.049353] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.049377] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d480
[    1.049464] usb usb7: configuration #1 chosen from 1 choice
[    1.049494] hub 7-0:1.0: USB hub found
[    1.049501] hub 7-0:1.0: 2 ports detected
[    1.049625] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.052128] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.052774] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.052781] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.052784] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.052788] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.052791] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.052874] mice: PS/2 mouse device common for all mice
[    1.053022] rtc_cmos 00:03: RTC can wake from S4
[    1.053060] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.053087] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.053214] device-mapper: uevent: version 1.0.3
[    1.053323] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.053394] device-mapper: multipath: version 1.1.0 loaded
[    1.053397] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.053521] EISA: Probing bus 0 at eisa.0
[    1.053552] EISA: Detected 0 cards.
[    1.053712] cpuidle: using governor ladder
[    1.053851] cpuidle: using governor menu
[    1.054432] TCP cubic registered
[    1.054606] NET: Registered protocol family 10
[    1.055139] lo: Disabled Privacy Extensions
[    1.055538] NET: Registered protocol family 17
[    1.055560] Bluetooth: L2CAP ver 2.13
[    1.055562] Bluetooth: L2CAP socket layer initialized
[    1.055565] Bluetooth: SCO (Voice Link) ver 0.6
[    1.055567] Bluetooth: SCO socket layer initialized
[    1.055603] Bluetooth: RFCOMM TTY layer initialized
[    1.055607] Bluetooth: RFCOMM socket layer initialized
[    1.055609] Bluetooth: RFCOMM ver 1.11
[    1.056630] Using IPI No-Shortcut mode
[    1.056705] PM: Resume from disk failed.
[    1.056720] registered taskstats version 1
[    1.056841]   Magic number: 14:592:512
[    1.056939] rtc_cmos 00:03: setting system clock to 2010-02-11 03:30:13 UTC (1265859013)
[    1.056943] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.056945] EDD information not available.
[    1.085471] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.196893] ata4.00: ATAPI: PIONEER DVD-RW  DVR-K17A, 3.52, max UDMA/33
[    1.228960] ata4.00: configured for UDMA/33
[    1.336076] ata3: SATA link down (SStatus 0 SControl 300)
[    1.336094] ata2: SATA link down (SStatus 0 SControl 300)
[    1.341074] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.487211] usb 1-2: configuration #1 chosen from 1 choice
[    1.500035] Clocksource tsc unstable (delta = -315209894 ns)
[    1.608076] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.609138] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.609203] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    1.609207] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.880033] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    1.973047] ata1.00: ATA-8: TOSHIBA MK2046GSX, LB013M, max UDMA/100
[    1.973050] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.974482] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    1.974546] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    1.974550] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.975332] ata1.00: configured for UDMA/100
[    1.988205] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2046GS LB01 PQ: 0 ANSI: 5
[    1.988348] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.988395] sd 0:0:0:0: [sda] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.988448] sd 0:0:0:0: [sda] Write Protect is off
[    1.988452] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.988479] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.988629]  sda:
[    1.998650] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K17A 3.52 PQ: 0 ANSI: 5
[    2.030653] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.030658] Uniform CD-ROM driver Revision: 3.20
[    2.030771] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.030822] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.052659]  sda1 sda2 sda3 < sda5 sda6 sda7
[    2.109973] usb 5-1: configuration #1 chosen from 1 choice
[    2.119476]  sda8 >
[    2.119888] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.119922] Freeing unused kernel memory: 540k freed
[    2.120341] Write protecting the kernel text: 4568k
[    2.120404] Write protecting the kernel read-only data: 1836k
[    2.295739] Linux agpgart interface v0.103
[    2.299014] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    2.299409] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    2.311359] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    2.387923] [drm] Initialized drm 1.1.0 20060810
[    2.402273] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.402280] i915 0000:00:02.0: setting latency timer to 64
[    2.405250]   alloc irq_desc for 28 on node -1
[    2.405254]   alloc kstat_irqs on node -1
[    2.405267] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    2.511181] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.511222] 8139cp 0000:05:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.514151] 8139too Fast Ethernet driver 0.9.28
[    2.514216] 8139too 0000:05:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.515486] eth0: RealTek RTL8139 at 0xc800, 00:1e:8c:e9:c0:4e, IRQ 16
[    2.633892] [drm] fb0: inteldrmfb frame buffer device
[    2.634284] ACPI Warning: _BQC returned an invalid level 20090521 video-629
[    2.634419] acpi device:21: registered as cooling_device2
[    2.634562] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1e/input/input6
[    2.634602] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.634630] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.968632] [drm] LVDS-8: set mode 1280x800 e
[    3.416375] Console: switching to colour frame buffer device 160x50
[    3.759633] EXT4-fs (sda8): barriers enabled
[    3.775280] kjournald2 starting: pid 384, dev sda8:8, commit interval 5 seconds
[    3.775294] EXT4-fs (sda8): delayed allocation enabled
[    3.775298] EXT4-fs: file extents enabled
[    3.775600] EXT4-fs: mballoc enabled
[    3.775617] EXT4-fs (sda8): mounted filesystem with ordered data mode
[    4.462584] type=1505 audit(1265859016.903:2): operation="profile_load" pid=407 name=/usr/share/gdm/guest-session/Xsession
[    4.465543] type=1505 audit(1265859016.907:3): operation="profile_load" pid=408 name=/sbin/dhclient3
[    4.466395] type=1505 audit(1265859016.907:4): operation="profile_load" pid=408 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.466854] type=1505 audit(1265859016.907:5): operation="profile_load" pid=408 name=/usr/lib/connman/scripts/dhclient-script
[    4.523329] type=1505 audit(1265859016.963:6): operation="profile_load" pid=409 name=/usr/bin/evince
[    4.537241] type=1505 audit(1265859016.980:7): operation="profile_load" pid=409 name=/usr/bin/evince-previewer
[    4.545430] type=1505 audit(1265859016.988:8): operation="profile_load" pid=409 name=/usr/bin/evince-thumbnailer
[    4.570347] type=1505 audit(1265859017.012:9): operation="profile_load" pid=411 name=/usr/lib/cups/backend/cups-pdf
[   19.281406] udev: starting version 147
[   19.446877] EXT4-fs (sda8): internal journal on sda8:8
[   19.569463] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.584138] cfg80211: Calling CRDA to update world regulatory domain
[   19.591843] asus_laptop: Asus Laptop Support version 0.42
[   19.597644] asus_laptop:   T20 model detected
[   19.598554] input: Asus Laptop extra buttons as /devices/virtual/input/input7
[   19.598924] Registered led device: asus::mail
[   19.602478] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[   19.666525] lp: driver loaded but no devices found
[   19.696267] Linux video capture interface: v2.00
[   19.720504] gspca: main v2.6.0 registered
[   19.721950] gspca: probing 093a:2468
[   19.725194] pac207: Pixart Sensor ID 0x27 Chips ID 0x00
[   19.725198] pac207: Pixart PAC207BCA Image Processor and Control Chip detected (vid/pid 0x093A:0x2468)
[   19.733385] gspca: probe ok
[   19.733413] usbcore: registered new interface driver pac207
[   19.733417] pac207: registered
[   19.738960] cfg80211: World regulatory domain updated:
[   19.738964] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.738968] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.738971] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.738974] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.738977] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.738980] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.090963]   alloc irq_desc for 22 on node -1
[   20.090967]   alloc kstat_irqs on node -1
[   20.090976] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   20.091026] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.199261] eth0: link down
[   20.199513] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.269543] hda_codec: Unknown model for ALC660-VD, trying auto-probe from BIOS...
[   20.269645] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   20.373362] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x9280b1, caps: 0xa04711/0xa04000
[   20.373371] synaptics: Toshiba Satellite L40 detected, limiting rate to 40pps.
[   20.376258] __ratelimit: 9 callbacks suppressed
[   20.376262] type=1505 audit(1265851832.819:13): operation="profile_replace" pid=953 name=/usr/share/gdm/guest-session/Xsession
[   20.378556] type=1505 audit(1265851832.819:14): operation="profile_replace" pid=954 name=/sbin/dhclient3
[   20.379429] type=1505 audit(1265851832.819:15): operation="profile_replace" pid=954 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   20.379906] type=1505 audit(1265851832.819:16): operation="profile_replace" pid=954 name=/usr/lib/connman/scripts/dhclient-script
[   20.386051] type=1505 audit(1265851832.827:17): operation="profile_replace" pid=955 name=/usr/bin/evince
[   20.400602] type=1505 audit(1265851832.843:18): operation="profile_replace" pid=955 name=/usr/bin/evince-previewer
[   20.409311] type=1505 audit(1265851832.851:19): operation="profile_replace" pid=955 name=/usr/bin/evince-thumbnailer
[   20.421008] type=1505 audit(1265851832.863:20): operation="profile_replace" pid=958 name=/usr/lib/cups/backend/cups-pdf
[   20.422108] type=1505 audit(1265851832.863:21): operation="profile_replace" pid=958 name=/usr/sbin/cupsd
[   20.426966] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   20.434684] type=1505 audit(1265851832.875:22): operation="profile_replace" pid=964 name=/usr/sbin/mysqld
[   20.444342] phy0: Selected rate control algorithm 'minstrel'
[   20.445261] phy0: hwaddr 00:16:44:ae:4b:ad, RTL8187BvE V0 + rtl8225z2
[   20.486914] rtl8187: Customer ID is 0x04
[   20.486989] Registered led device: rtl8187-phy0::tx
[   20.487013] Registered led device: rtl8187-phy0::rx
[   20.487046] usbcore: registered new interface driver rtl8187
[   25.910541] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.996979] ppdev: user-space parallel port driver
[  889.862267] wlan0: authenticate with AP 00:23:cd:c6:c3:64
[  889.867262] wlan0: authenticated
[  889.867268] wlan0: associate with AP 00:23:cd:c6:c3:64
[  889.870779] wlan0: RX AssocResp from 00:23:cd:c6:c3:64 (capab=0x431 status=0 aid=1)
[  889.870783] wlan0: associated
[  889.881882] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  900.557046] wlan0: no IPv6 routers present
moha@moha:~$ 


well i didnt try to use terminal to run these programs, how can i ?

Thanks a lot for ur response :D

---

### Post by x33a on 2010-02-10
How much ram do you have? 

Run memtest86+ for checking memory corruption.

---

### Post by sgosnell on 2010-02-10
Do you have a swap partition, and is it active?  Running that many programs will almost certainly require more RAM than you have, so the OS will have to swap between disk and RAM, and if you don't have the swap space, it has no way to do that, and thus everything freezes.

---

### Post by mohabic on 2010-02-20
> **sgosnell said:**
> Do you have a swap partition, and is it active?  Running that many programs will almost certainly require more RAM than you have, so the OS will have to swap between disk and RAM, and if you don't have the swap space, it has no way to do that, and thus everything freezes.

I have 1G of RAM. and well, i know nothing about the swap process, how to settle it in my pc ?
<very sorry for being late>
Thanks

---

### Post by x33a on 2010-02-20
> **mohabic said:**
> I have 1G of RAM. and well, i know nothing about the swap process, how to settle it in my pc ?
<very sorry for being late>
Thanks

Did you check the RAM using memtest 86+, it is available in the boot options (grub), when the computer starts.

also, open a terminal and post the output of
```
df -h
sudo fdisk -l
```

---

### Post by sgosnell on 2010-02-20
Type 'free' in a terminal, without the quotes of course, and post the output.  That will tell you how much RAM is in use, and how much is free, and will also show whether you have a swap partition, how big it is, and how much is in use.

---

### Post by mohabic on 2010-02-21
moha@moha:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8              28G   18G  8.2G  69% /
udev                  498M  280K  497M   1% /dev
none                  498M  1.5M  496M   1% /dev/shm
none                  498M  196K  497M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw


moha@moha:~$ sudo fdisk -l
[sudo] password for moha: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c0808e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        6509    50746518+   7  HPFS/NTFS
/dev/sda3            6510       24322   143076352+   f  W95 Ext'd (LBA)
/dev/sda5            6510        8468    15727616    7  HPFS/NTFS
/dev/sda6            8468       12748    34376953+   7  HPFS/NTFS
/dev/sda7           16395       24322    63671296    7  HPFS/NTFS
/dev/sda8           12749       16394    29286463+  83  Linux

Partition table entries are not in disk order



moha@moha:~$ free
             total       used       free     shared    buffers     cached
Mem:       1018060     779424     238636          0      63572     399144
-/+ buffers/cache:     316708     701352
Swap:            0          0          0
moha@moha:~$

---

### Post by x33a on 2010-02-21
You don't have any swap. you'll need to create one, and see if solves the problem.

use a live disk to resize your linux partition by about 2 GB, then add format that space to a swap. Then you'll have to enter the swap partition into your /etc/fstab file.

Please, post the output of 
```
cat /etc/fstab
```

---

### Post by SecretCode on 2010-02-21
> **mohabic said:**
> ```
moha@moha:~$ free
             total       used       free     shared    buffers     cached
Mem:       1018060     779424     238636          0      63572     399144
-/+ buffers/cache:     316708     701352
Swap:            0          0          0
```

You definitely need a swap partition - or file - swap file would be easier because you won't have to resize existing partitions.

Be aware that the system will still slow down when you use up real RAM. I don't know for certain, but I think netbeans can use a lot of RAM and chrome and mysql could use a fair amount. You might also want to consider upgrading to 2GB of RAM!

---

### Post by mohabic on 2010-02-21
> **x33a said:**
> You don't have any swap. you'll need to create one, and see if solves the problem.

use a live disk to resize your linux partition by about 2 GB, then add format that space to a swap. Then you'll have to enter the swap partition into your /etc/fstab file.

Please, post the output of 
```
cat /etc/fstab
```

moha@moha:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=cdb1c6ac-a2cc-4a36-803c-24b2a8732300 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
moha@moha:~$

---

### Post by mohabic on 2010-02-21
well, let's say that i want to build 2G swap memory without partitioning, (i have some sensitivity to that) what commands should i feed my terminal with ?

---

### Post by SecretCode on 2010-02-22
See here: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

Follow those 4 steps, substituting _bs=1M count=2048_ instead of _bs=1M count=512_. Also it doesn't really matter what you name the file.

But it's worth reading the rest of the page too - good background information.

---

### Post by mohabic on 2010-02-22
> **SecretCode said:**
> See here: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

Follow those 4 steps, substituting _bs=1M count=2048_ instead of _bs=1M count=512_. Also it doesn't really matter what you name the file.

But it's worth reading the rest of the page too - good background information.

Thank you so much for ur help :D
im really thankful

---

### Post by x33a on 2010-02-22
Please mark the thread solved.

---

### Post by mohabic on 2010-02-23
> **x33a said:**
> Please mark the thread solved.

Thank you for advice :D
Done . . .

---

