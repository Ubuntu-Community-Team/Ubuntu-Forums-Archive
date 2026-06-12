---
title: "HELP! No wireless internet"
date: 2009-09-06
forum: General Help
---

### Post by LifeEnemy on 2009-09-06
I've had problems with my wireless connection for a long time, even before using Ubuntu, but recently it has gotten much worse, to the point that I can't connect to the internet with Ubuntu. I used to use only Vista, and I had occasion problems where the wireless connection (under "manage connections") would not respond and I had to restart the computer to connect. Now I have a dual boot with Ubuntu and Vista set up, and the problem has been getting progressively worse. In Ubuntu it used to be that I would sometimes be unable to connect and I would have to restart the computer (sometimes 3-4 times) to get it to work. Now in Vista, I can connect wirelessly, but only after I disable/enable my wireless connection (the one that used to freeze, but apparently doesn't anymore). I can connect using a cable on Ubuntu, but that is usually not a viable option. Could it be a driver issue? I've heard of ndiswrapper, could that maybe help? Or could it be that my wireless card is just going bad? Please help, without internet I can't use Ubuntu and I'm stuck here with Vista :(

EDIT: If it's important, I have also noticed that Ubuntu almost always shows a black screen with the mouse (sometimes with the 'loading' pointer icon) when loading right after I log in for about 10-20 seconds. This never happened until recently. Sometimes there are dark gray bars on the black screen corresponding to the location of the top and bottom panels of the desktop.

---

### Post by nothingspecial on 2009-09-07
Please post your wireless card

```
sudo lshw -C network
```

also post the output of ```
dmesg
```

Not all of it just anything near the end related to your wireless.

---

### Post by LifeEnemy on 2009-09-07
Here are the results:

> 
    <!--         @page { margin: 0.79in }         P { margin-bottom: 0.08in }     -->      sudo lshw -C network


  *-network               
       description: Ethernet interface
      product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:35:e8:f6
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:19:e3:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:07:f7:50:11:4b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

> 
dmesg


[    0.602197] usbcore: registered new interface driver hub
[    0.602197] usbcore: registered new device driver usb
[    0.602197] PCI: Using ACPI for IRQ routing
[    0.608011] Bluetooth: Core ver 2.13
[    0.608026] NET: Registered protocol family 31
[    0.608026] Bluetooth: HCI device and connection manager initialized
[    0.608026] Bluetooth: HCI socket layer initialized
[    0.608026] NET: Registered protocol family 8
[    0.608026] NET: Registered protocol family 20
[    0.608039] NetLabel: Initializing
[    0.608041] NetLabel:  domain hash size = 128
[    0.608043] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.608057] NetLabel:  unlabeled traffic allowed by default
[    0.608074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.608079] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.612066] AppArmor: AppArmor Filesystem Enabled
[    0.616012] Switched to high resolution mode on CPU 0
[    0.616570] Switched to high resolution mode on CPU 1
[    0.620011] pnp: PnP ACPI init
[    0.620021] ACPI: bus type pnp registered
[    0.642479] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.642484] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.642596] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.642600] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.642603] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.667876] pnp: PnP ACPI: found 13 devices
[    0.667879] ACPI: ACPI bus type pnp unregistered
[    0.667883] PnPBIOS: Disabled by ACPI PNP
[    0.667893] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    0.667897] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    0.667906] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    0.667914] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.667921] system 00:0a: ioport range 0x900-0x97f has been reserved
[    0.667924] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.667931] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.667935] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.667938] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    0.667941] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.667948] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.667951] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.667954] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.667958] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.667961] system 00:0c: iomem range 0x100000-0xbfe71fff could not be reserved
[    0.667964] system 00:0c: iomem range 0xbfe72000-0xbfefffff has been reserved
[    0.667967] system 00:0c: iomem range 0xbff00000-0xbfffffff has been reserved
[    0.667971] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
[    0.667974] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.667977] system 00:0c: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.667980] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.667983] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.667987] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.667992] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.668006] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.668010] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.668013] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.668016] system 00:0c: iomem range 0xf4000000-0xf7ffffff has been reserved
[    0.702760] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.702764] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.702769] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfeafffff
[    0.702774] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.702780] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.702784] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.702791] pci 0000:00:1c.0:   MEM window: 0xf9f00000-0xf9ffffff
[    0.702797] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.702806] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0b
[    0.702809] pci 0000:00:1c.1:   IO window: disabled
[    0.702816] pci 0000:00:1c.1:   MEM window: 0xf9e00000-0xf9efffff
[    0.702822] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.702831] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0c
[    0.702835] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.702842] pci 0000:00:1c.4:   MEM window: 0xf9c00000-0xf9dfffff
[    0.702848] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.702858] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.702860] pci 0000:00:1e.0:   IO window: disabled
[    0.702867] pci 0000:00:1e.0:   MEM window: 0xf9b00000-0xf9bfffff
[    0.702873] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.702890] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.702895] pci 0000:00:01.0: setting latency timer to 64
[    0.702905] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.702911] pci 0000:00:1c.0: setting latency timer to 64
[    0.702922] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.702928] pci 0000:00:1c.1: setting latency timer to 64
[    0.702939] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.702945] pci 0000:00:1c.4: setting latency timer to 64
[    0.702954] pci 0000:00:1e.0: setting latency timer to 64
[    0.702959] bus: 00 index 0 io port: [0x00-0xffff]
[    0.702962] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.702965] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.702967] bus: 01 index 1 mmio: [0xfa000000-0xfeafffff]
[    0.702970] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.702972] bus: 01 index 3 mmio: [0x0-0x0]
[    0.702975] bus: 09 index 0 io port: [0xd000-0xdfff]
[    0.702977] bus: 09 index 1 mmio: [0xf9f00000-0xf9ffffff]
[    0.702980] bus: 09 index 2 mmio: [0x0-0x0]
[    0.702982] bus: 09 index 3 mmio: [0x0-0x0]
[    0.702984] bus: 0b index 0 mmio: [0x0-0x0]
[    0.702986] bus: 0b index 1 mmio: [0xf9e00000-0xf9efffff]
[    0.702989] bus: 0b index 2 mmio: [0x0-0x0]
[    0.702991] bus: 0b index 3 mmio: [0x0-0x0]
[    0.702993] bus: 0c index 0 io port: [0xc000-0xcfff]
[    0.702995] bus: 0c index 1 mmio: [0xf9c00000-0xf9dfffff]
[    0.702998] bus: 0c index 2 mmio: [0xf0000000-0xf01fffff]
[    0.703000] bus: 0c index 3 mmio: [0x0-0x0]
[    0.703003] bus: 03 index 0 mmio: [0x0-0x0]
[    0.703005] bus: 03 index 1 mmio: [0xf9b00000-0xf9bfffff]
[    0.703007] bus: 03 index 2 mmio: [0x0-0x0]
[    0.703010] bus: 03 index 3 io port: [0x00-0xffff]
[    0.703012] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.703020] NET: Registered protocol family 2
[    0.716058] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.716335] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.716695] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.716886] TCP: Hash tables configured (established 131072 bind 65536)
[    0.716889] TCP reno registered
[    0.720078] NET: Registered protocol family 1
[    0.720203] checking if image is initramfs... it is
[    1.435755] Freeing initrd memory: 7309k freed
[    1.435795] Simple Boot Flag at 0x79 set to 0x1
[    1.435989] cpufreq: No nForce2 chipset.
[    1.436145] audit: initializing netlink socket (disabled)
[    1.436170] type=2000 audit(1252332118.436:1): initialized


Sorry to post the entire output from dmesg, but I couldn't figure out which parts were related to my wireless and which parts were unimportant (my knowledge of computers is very basic).

---

### Post by LifeEnemy on 2009-09-07
There is a small section missing here (all with numbers 1.44xxxx) that the forums wouldn't let me post because it said there were images in it for some reason and there were too many. I don't know. But aside from that missing portion, this is the rest of the dmesg output:


> 
[    1.450051] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.450089] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.450108] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.450122] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.450136] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.450220] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.450277] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.450314] pcieport-driver 0000:00:1c.4: irq 2300 for MSI/MSI-X
[    1.450333] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.450347] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.450361] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.450458] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.450578] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.450729] ACPI: AC Adapter [AC] (on-line)
[    1.482067] ACPI: Battery Slot [BAT0] (battery present)
[    1.482152] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.624351] ACPI: Lid Switch [LID]
[    1.624402] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.624409] ACPI: Power Button (CM) [PBTN]
[    1.624456] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.624459] ACPI: Sleep Button (CM) [SBTN]
[    1.625081] ACPI: SSDT BFE72D7A, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.625485] ACPI: SSDT BFE72710, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.625905] Monitor-Mwait will be used to enter C-1 state
[    1.625909] Monitor-Mwait will be used to enter C-2 state
[    1.625912] Monitor-Mwait will be used to enter C-3 state
[    1.625927] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.625955] processor ACPI_CPU:00: registered as cooling_device0
[    1.625960] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.626326] ACPI: SSDT BFE72F7C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.626690] ACPI: SSDT BFE72CF5, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.627158] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.627180] processor ACPI_CPU:01: registered as cooling_device1
[    1.627184] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.629635] thermal LNXTHERM:01: registered as thermal_zone0
[    1.629849] ACPI: Thermal Zone [THM] (31 C)
[    1.629916] isapnp: Scanning for PnP cards...
[    1.984146] isapnp: No Plug & Play device found
[    1.993196] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.994389] brd: module loaded
[    1.994741] loop: module loaded
[    1.994812] Fixed MDIO Bus: probed
[    1.994818] PPP generic driver version 2.4.2
[    1.994882] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.994917] Driver 'sd' needs updating - please use bus_type methods
[    1.994928] Driver 'sr' needs updating - please use bus_type methods
[    1.994972] ahci 0000:00:1f.2: version 3.0
[    1.994984] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.995029] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.995105] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.995109] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    1.995115] ahci 0000:00:1f.2: setting latency timer to 64
[    1.995306] scsi0 : ahci
[    1.995406] scsi1 : ahci
[    1.995471] scsi2 : ahci
[    1.995743] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 2299
[    1.995746] ata2: DUMMY
[    1.995750] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 2299
[    2.312023] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.313694] ata1.00: ATA-8: WDC WD3200BEKT-00F3T0, 11.01A11, max UDMA/133
[    2.313697] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    2.315445] ata1.00: configured for UDMA/133
[    2.648020] ata3: SATA link down (SStatus 0 SControl 300)
[    2.664117] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-0 11.0 PQ: 0 ANSI: 5
[    2.664219] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.664238] sd 0:0:0:0: [sda] Write Protect is off
[    2.664241] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.664270] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.664337] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.664354] sd 0:0:0:0: [sda] Write Protect is off
[    2.664356] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.664385] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.664388]  sda: sda1 sda2 sda3 sda4
[    2.712718] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.712765] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.712821] ata_piix 0000:00:1f.1: version 2.12
[    2.712828] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.712867] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.712941] scsi3 : ata_piix
[    2.713004] scsi4 : ata_piix
[    2.713738] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    2.713742] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    2.892511] ata4.00: ATAPI: TEAC   DVD+/-RW DVW28SLC, A.06, max UDMA/33
[    2.924464] ata4.00: configured for UDMA/33
[    2.936543] ata5: port disabled. ignoring.
[    2.948212] scsi 3:0:0:0: CD-ROM            TEAC     DVD+-RW DVW28SLC A.06 PQ: 0 ANSI: 5
[    2.978532] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    2.978536] Uniform CD-ROM driver Revision: 3.20
[    2.978632] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.978675] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.979461] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.979484] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.979500] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.979504] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.979565] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.983482] ehci_hcd 0000:00:1a.7: debug port 1
[    2.983490] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.983505] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.996010] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.996081] usb usb1: configuration #1 chosen from 1 choice
[    2.996111] hub 1-0:1.0: USB hub found
[    2.996119] hub 1-0:1.0: 4 ports detected
[    2.996240] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.996253] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.996257] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.996307] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.000208] ehci_hcd 0000:00:1d.7: debug port 1
[    3.000216] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.000229] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    3.016009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.016072] usb usb2: configuration #1 chosen from 1 choice
[    3.016100] hub 2-0:1.0: USB hub found
[    3.016107] hub 2-0:1.0: 6 ports detected
[    3.016216] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.016238] uhci_hcd: USB Universal Host Controller Interface driver
[    3.016259] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.016266] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.016271] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.016317] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.016346] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    3.016429] usb usb3: configuration #1 chosen from 1 choice
[    3.016457] hub 3-0:1.0: USB hub found
[    3.016465] hub 3-0:1.0: 2 ports detected
[    3.016560] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.016569] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.016573] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.016622] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.016659] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    3.016742] usb usb4: configuration #1 chosen from 1 choice
[    3.016770] hub 4-0:1.0: USB hub found
[    3.016777] hub 4-0:1.0: 2 ports detected
[    3.016870] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.016877] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.016881] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.016926] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.016954] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    3.017035] usb usb5: configuration #1 chosen
      from 1 choice
[    3.017062] hub 5-0:1.0: USB hub found
[    3.017069] hub 5-0:1.0: 2 ports detected
[    3.017162] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.017171] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.017175] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.017224] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.017253] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    3.017331] usb usb6: configuration #1 chosen from 1 choice
[    3.017359] hub 6-0:1.0: USB hub found
[    3.017366] hub 6-0:1.0: 2 ports detected
[    3.017470] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    3.017478] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.017482] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.017526] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.017554] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    3.017636] usb usb7: configuration #1 chosen from 1 choice
[    3.017663] hub 7-0:1.0: USB hub found
[    3.017670] hub 7-0:1.0: 2 ports detected
[    3.017836] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.032785] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.032791] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.037041] mice: PS/2 mouse device common for all mice
  [    3.053073] rtc_cmos 00:04: RTC can wake from S4
[    3.053110] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.053147] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.053213] device-mapper: uevent: version 1.0.3
[    3.053307] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    3.053388] device-mapper: multipath: version 1.0.5 loaded
[    3.053391] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.053471] EISA: Probing bus 0 at eisa.0
[    3.053480] Cannot allocate resource for EISA slot 1
[    3.053512] EISA: Detected 0 cards.
[    3.053642] cpuidle: using governor ladder
[    3.053778] cpuidle: using governor menu
[    3.054357] TCP cubic registered
[    3.054468] NET: Registered protocol family 10
[    3.054951] lo: Disabled Privacy Extensions
[    3.055339] NET: Registered protocol family 17
[    3.055357] Bluetooth: L2CAP ver 2.11
[    3.055359] Bluetooth: L2CAP socket layer initialized
[    3.055362] Bluetooth: SCO (Voice Link) ver 0.6
[    3.055364] Bluetooth: SCO socket layer initialized
[    3.055398] Bluetooth: RFCOMM socket layer initialized
[    3.055405] Bluetooth: RFCOMM TTY layer initialized
[    3.055407] Bluetooth: RFCOMM ver 1.10
[    3.055696] Marking TSC unstable due to TSC halts in idle
[    3.056041] Using IPI No-Shortcut mode
[    3.056115] registered taskstats version 1
[    3.056255]   Magic number: 9:987:29
[    3.056354] rtc_cmos 00:04: setting system clock to 2009-09-07 14:02:00 UTC (1252332120)
[    3.056358] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.056360] EDD information not available.
[    3.056654] Freeing unused kernel memory: 532k freed
[    3.056837] Write protecting the kernel text: 4116k
[    3.056907] Write protecting the kernel read-only data: 1528k
[    3.076498] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4 
  [    3.315415] sky2 driver version 1.22
[    3.315472] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.315490] sky2 0000:09:00.0: setting latency timer to 64
[    3.315533] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    3.315761] sky2 0000:09:00.0: irq 2298 for MSI/MSI-X
[    3.316580] sky2 eth0: addr 00:1d:09:35:e8:f6
[    3.316683] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.459805] ohci1394 0000:03:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.510649] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f9bff800-f9bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.534492] usb 1-1: configuration #1 chosen from 1 choice
[    3.831269] PM: Starting manual resume from disk
[    3.831273] PM: Resume from partition 8:3
[    3.831275] PM: Checking hibernation image.
[    3.831399] PM: Resume from disk failed.
[    3.850802] kjournald starting.  Commit interval 5 seconds
[    3.850812] EXT3-fs: mounted filesystem with ordered data mode.
[    3.955569] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.128539] usb 3-2: configuration #1 chosen from 1 choice
[    4.800244] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc000242375a1]
[    8.448866] udev: starting version 141
[    8.582385] Linux agpgart interface v0.103
[    8.664088] cfg80211: Calling CRDA to update world regulatory domain
[    8.702992] iTCO_vendor_support: vendor-support=0
[    8.728853] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.729178] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[    8.729279] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    8.758135] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    8.929732] sdhci: Secure Digital Host Controller Interface driver
[    8.929736] sdhci: Copyright(c) Pierre Ossman
[    8.931271] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 22)
[    8.931295] sdhci-pci 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    8.933464] mmc0: SDHCI controller on PCI [0000:03:09.1] using DMA
[    8.936040] ricoh-mmc: Ricoh MMC Controller disabling driver
[    8.936043] ricoh-mmc: Copyright(c) Philip Langdale
[    8.936071] ricoh-mmc: Ricoh MMC controller found at 0000:03:09.2 [1180:0843] (rev 12)
[    8.936093] ricoh-mmc: Controller is now disabled.
[    8.954365] Linux video capture interface: v2.00
[    8.969106] cfg80211: World regulatory domain updated:
[    8.969110]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.969114]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.969116]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.969119]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.969121]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.969124]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.057975] acpi device:32: registered as cooling_device2
[    9.058706] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input6
[    9.060040] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.065483] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    9.065486] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    9.065601] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.065616] iwl3945 0000:0b:00.0: setting latency timer to 64
[    9.065667] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    9.067479] iwl3945 0000:0b:00.0: irq 2297 for MSI/MSI-X
[    9.123706] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.124129] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    9.126345] phy0: Selected rate control algorithm 'iwl-3945-rs'
[    9.180399] nvidia: module license 'NVIDIA' taints kernel.
[    9.251436] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    9.251785] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[    9.252491] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input7
[    9.342136] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.342252] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.393239] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.445323] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.445334] nvidia 0000:01:00.0: setting latency timer to 64
[    9.445544] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    9.447885] usbcore: registered new interface driver uvcvideo
[    9.447915] USB Video Class driver (v0.1.0)
[    9.799374] lp: driver loaded but no devices found
[    9.957550] Adding 4996204k swap on /dev/sda3.  Priority:-1 extents:1 across:4996204k
[   10.100092] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8
[   10.134414] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   10.501993] EXT3 FS on sda2, internal journal
[   11.016069] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x215ba000
[   11.297338] kjournald starting.  Commit interval 5 seconds
[   11.297689] EXT3 FS on sda4, internal journal
[   11.297699] EXT3-fs: mounted filesystem with ordered data mode.
[   11.649537] type=1505 audit(1252346529.092:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2161
[   11.702742] type=1505 audit(1252346529.144:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2165
[   11.702853] type=1505 audit(1252346529.144:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2165
[   11.702901] type=1505 audit(1252346529.144:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2165
[   11.702942] type=1505 audit(1252346529.144:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2165
[   11.742366] type=1505 audit(1252346529.183:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2170
[   11.888719] type=1505 audit(1252346529.331:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2174
[   11.888906] type=1505 audit(1252346529.331:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2174
[   11.920346] type=1505 audit(1252346529.363:10): operation="profile_load" name="/usr/sbin/tcpdump"    
    name2="default" pid=2178
[   16.309202] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   16.309206] vboxdrv: Successfully done.
[   16.309208] vboxdrv: Found 2 processor cores.
[   16.309537] vboxdrv: fAsync=0 offMin=0x1ae offMax=0x9b0
[   16.310391] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   16.310394] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   17.678284] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.678287] Bluetooth: BNEP filters: protocol multicast
[   17.694439] Bridge firewalling registered
[   19.218837] ppdev: user-space parallel port driver
[   22.561824] sky2 eth0: enabling interface
[   22.562036] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.562773] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   22.665486] iwl3945: MAC is in deep sleep!
[   22.665490] iwl3945: Unable to int nic
[   22.666894] iwl3945: MAC is in deep sleep!
[   22.666899] iwl3945: Unable to int nic
[   82.500065] Clocksource tsc unstable (delta = -122841499 ns)
 

---

### Post by nothingspecial on 2009-09-08
This card  has been causing problems in 8.10 and 9.04. It used to work before that using a different kernel module (driver).

Some people have had success installing the linux-backports-modules-jaunty package. Search for it in synaptic package manager.

Some people have had success installing wicd. Again search for it in synaptic package manager.

If neither of those work then we`ll have to try something else.

---

### Post by P4man on 2009-09-08
a quick workaround, rather than rebooting, try running this in a terminal:

```
sudo rmmod iwl3945; sudo modprobe iwl3945
```

---

### Post by LifeEnemy on 2009-09-08
I downloaded both of those from synaptic and it seems to have worked. On a side note, I tried booting up the previous kernel and that did work. Go figure. Also, I tried that suggested 'workaround,' but when I typed in the second line it said something about a config file, and ignoring it in a later release. Is that bad at all?

---

### Post by chinoy on 2009-09-09
when you first load off the CD you get a generic kernel
Everything works with that except your Express Card Slot
So you then download the laptop remix kernel
then your wifi crashes.
Its a good idea not to remove your earlier kernels.

Ive tried everything nothing seems to work except when i tried to install wicd it removed my network manager so now I cant even browse in the other kernels.

Its a royal mess and its hiting laptop owners the most.
Best bet reinstall with the CD and use Desktop kernel for x86

---

### Post by LifeEnemy on 2009-09-20
So the two packages I downloaded last week worked for the most part, but sometimes I would still have to restart my computer once to make it work. Now the problem has come back with a vengeance, I just had to restart FOUR times to connect. This is getting ridiculous. I'm thinking of taking my laptop to the tech guys on campus, or calling Dell to see if the problem is the hardware.

---

### Post by nothingspecial on 2009-09-20
There are 2 things I`ve never been able to get to work in linux.

One is this stupid little key chain that is supposed to display photos in a slide show.

The other is this wireless card with the iwl3945 module. The really annoying thing is that it used to perfectly well in Ubuntu 7.10. Then a new module was introduced that has never worked properly. I used the old one for a while but since it`s not been actively developed for a couple of years using it now is a major security risk.

Luckily I have a usb wireless thingy.

Sorry, I can`t be of more help, but if you do fix it, let me know.

---

### Post by LifeEnemy on 2009-09-20
So would that mean that the problem is something with the wireless card and/or Dell/whoever? Is it something that can be fixed by the Ubuntu developers, or no?

---

### Post by nothingspecial on 2009-09-20
There`s nothing wrong with the wireless card, and yes it will get fixed eventually - it always does.

From my understanding, the people working on the card (I think it`s intell, I can`t be bothered to look right now, believe me I have looked into this exhaustively), say it`s the linux/gnome developers problem and they say it`s theirs.

So untill these 2 get together and sort it, we are where we are.

This is from what I`ve read in my endeavours to get this working propperly. There may be a fix that I`ve missed somewhere. Keep looking if you want. Like I said, I've got a spare dongle thingy and better things to do.

Sorry.

---

### Post by LifeEnemy on 2009-09-20
Well, that sucks. Unfortunately developers battling over something like this just hurts the end user. I'll just have to look for some kind of solution I guess. The thing that gets me is that my wireless card had troubles before Ubuntu, and it still has some problems in Vista (dual-boot). They are usually much worse in Ubuntu, though. But that's because I don't know how to disable/enable the wirelsss connection like in vista.

---

### Post by LifeEnemy on 2009-10-05
Question: i think I mentioned earlier that using the previous kernel version seemed to help the wireless problem. If needed, could I just use that kernel for the majority of the time? Are there any potential problems that could come from not using the newest kernel all the time?

---

### Post by nothingspecial on 2009-10-05
> **LifeEnemy said:**
>  But that's because I don't know how to disable/enable the wirelsss connection like in vista.

```
sudo ifconfig wlan0 down
```

```
sudo ifconfig wlano up
```

As to the question about latest kernels - Ubuntu keeps the old ones around precisely for these sorts of issues.

If you`re worried, you can check what changes have been made in the new kernel but in most cases you should be fine.

See [[COLOR="Magenta"]here[/COLOR]]("http://kernelnewbies.org/LinuxChanges") for details.

---

### Post by LifeEnemy on 2009-10-09
Thanks for the info. I'll use the older kernel if the problem gets bad again (it's not too bad right now). I tried those terminal commands, but they didn't fix it. When the problem was active, I got an error about not finding the device or something. When the wireless was working correctly, I also tried those commands, and setting the device to "down" it disconnected but still could find networks. When I have trouble none of the networks nearby show up.

---

