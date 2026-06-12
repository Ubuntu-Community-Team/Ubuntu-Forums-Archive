---
title: "Memory stick not recognized"
date: 2011-05-26
forum: General Help
---

### Post by sofasurfer on 2011-05-26
Its a "Geek Squad" memory stick from Best Buy. There has been a couple of other times (recently) that it was not recognozed but after a couple of attempt it loaded. But today it is not showing up at all.
Any ideas?

---

### Post by wojox on 2011-05-26
What does this output when run in the terminal:

```
dmesg | tail
```

---

### Post by sofasurfer on 2011-05-26
$ dmesg | tail
[  957.019329] scsi 7:0:0:0: Direct-Access     M-Sys    Pan UCL   Mode   3.00 PQ: 0 ANSI: 0 CCS
[  957.019985] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  957.043354] sd 7:0:0:0: [sdc] 32768 512-byte logical blocks: (16.7 MB/16.0 MiB)
[  957.048336] sd 7:0:0:0: [sdc] Write Protect is off
[  957.048342] sd 7:0:0:0: [sdc] Mode Sense: 45 00 00 08
[  957.048344] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  957.072355] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  957.072364]  sdc: unknown partition table
[  957.122500] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  957.122506] sd 7:0:0:0: [sdc] Attached SCSI removable disk

---

### Post by sofasurfer on 2011-05-26
I left my stick in the usn port for an hour and the light on it operates all the time but the stick is never recognized. Did the stick go bad?

---

### Post by wojox on 2011-05-27
When you open Disk Utility does it recognize it in there?

---

### Post by sofasurfer on 2011-05-27
Do you mean "udisks"? Can you explain how to work it?
My pc still shows nothing of my mem stick. I took it to work where I have used it before and the Windoz pc said something like "do you want to reformat"? I put it in a cars usb port where it should have played music and the message was "no files available". Brought it back home and my pc say NOTHING. So I can not even try to reformat on my pc.

---

### Post by sofasurfer on 2011-05-27
Here is my dmesg. I don't understand this stuff but I am led to beleive that this should tell me something. I see a line in it that makes me wonder. It repeats many times and says, "0.634262] usb usb2: configuration #1 chosen from 1 choice"

```

[    0.198561] NetLabel:  domain hash size = 128
[    0.198563] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.198579] NetLabel:  unlabeled traffic allowed by default
[    0.200334] AppArmor: AppArmor Filesystem Enabled
[    0.200355] pnp: PnP ACPI init
[    0.200372] ACPI: bus type pnp registered
[    0.203236] pnp: PnP ACPI: found 13 devices
[    0.203238] ACPI: ACPI bus type pnp unregistered
[    0.203249] system 00:01: ioport range 0x4100-0x411f has been reserved
[    0.203252] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.203255] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.203257] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.203260] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.203262] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.203265] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.203268] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.203270] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.203273] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
[    0.203276] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
[    0.203282] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.203288] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.203291] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.203294] system 00:01: ioport range 0xb10-0xb1f has been reserved
[    0.203303] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.203306] system 00:06: ioport range 0x220-0x225 has been reserved
[    0.203313] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.203318] system 00:0c: iomem range 0xce200-0xcffff has been reserved
[    0.203321] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.203324] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.203326] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.203329] system 00:0c: iomem range 0x3fef0000-0x3ffeffff could not be reserved
[    0.203333] system 00:0c: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.203335] system 00:0c: iomem range 0x3fee0000-0x3fefffff could not be reserved
[    0.203338] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.203341] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.203344] system 00:0c: iomem range 0x100000-0x3fedffff could not be reserved
[    0.203347] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.203350] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.203353] system 00:0c: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.208029] Switching to clocksource acpi_pm
[    0.208154] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.208156] pci 0000:00:02.0:   IO window: 0xd000-0xdfff
[    0.208160] pci 0000:00:02.0:   MEM window: 0xfa000000-0xfcffffff
[    0.208163] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.208171] pci 0000:00:07.0: PCI bridge, secondary bus 0000:02
[    0.208174] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.208177] pci 0000:00:07.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.208180] pci 0000:00:07.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.208185] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.208188] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.208194] pci 0000:00:14.4:   MEM window: 0xf0000000-0xf7ffffff
[    0.208199] pci 0000:00:14.4:   PREFETCH window: 0xfdf00000-0xfdffffff
[    0.208214] pci 0000:00:02.0: setting latency timer to 64
[    0.208220] pci 0000:00:07.0: setting latency timer to 64
[    0.208229] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.208231] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.208234] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.208236] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfcffffff]
[    0.208239] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.208241] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.208244] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.208246] pci_bus 0000:02: resource 2 pref mem [0xfde00000-0xfdefffff]
[    0.208249] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.208251] pci_bus 0000:03: resource 1 mem: [0xf0000000-0xf7ffffff]
[    0.208253] pci_bus 0000:03: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.208256] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.208258] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.208298] NET: Registered protocol family 2
[    0.208414] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.208994] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.209989] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.209989] TCP: Hash tables configured (established 131072 bind 65536)
[    0.209989] TCP reno registered
[    0.209989] NET: Registered protocol family 1
[    0.460059] pci 0000:01:00.0: Boot video device
[    0.460284] Trying to unpack rootfs image as initramfs...
[    0.490515] Scanning for low memory corruption every 60 seconds
[    0.490649] audit: initializing netlink socket (disabled)
[    0.490662] type=2000 audit(1306518957.490:1): initialized
[    0.510448] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.511896] VFS: Disk quotas dquot_6.5.2
[    0.511953] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.512639] fuse init (API version 7.13)
[    0.512729] msgmni has been set to 1979
[    0.520227] alg: No test for stdrng (krng)
[    0.520340] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.520343] io scheduler noop registered
[    0.520345] io scheduler anticipatory registered
[    0.520347] io scheduler deadline registered
[    0.520380] io scheduler cfq registered (default)
[    0.520541]   alloc irq_desc for 24 on node 0
[    0.520543]   alloc kstat_irqs on node 0
[    0.520552] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.520559] pcieport 0000:00:02.0: setting latency timer to 64
[    0.520672]   alloc irq_desc for 25 on node 0
[    0.520673]   alloc kstat_irqs on node 0
[    0.520678] pcieport 0000:00:07.0: irq 25 for MSI/MSI-X
[    0.520683] pcieport 0000:00:07.0: setting latency timer to 64
[    0.520745] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.520768] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.520859] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.520863] ACPI: Power Button [PWRB]
[    0.520916] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.520918] ACPI: Power Button [PWRF]
[    0.520964] fan PNP0C0B:00: registered as cooling_device0
[    0.520971] ACPI: Fan [FAN] (on)
[    0.521223] processor LNXCPU:00: registered as cooling_device1
[    0.523456] ACPI Warning for \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference (20090903/nspredef-1012)
[    0.523464] ACPI: Expecting a [Reference] package element, found type 0
[    0.523466] ACPI: Invalid passive threshold
[    0.523741] thermal LNXTHERM:01: registered as thermal_zone0
[    0.523748] ACPI: Thermal Zone [THRM] (40 C)
[    0.525039] Linux agpgart interface v0.103
[    0.525076] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.525201] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.525504] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.526503] brd: module loaded
[    0.526959] loop: module loaded
[    0.527052] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.530292]   alloc irq_desc for 16 on node 0
[    0.530296]   alloc kstat_irqs on node 0
[    0.530309] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.530756] Fixed MDIO Bus: probed
[    0.530795] PPP generic driver version 2.4.2
[    0.530849] tun: Universal TUN/TAP device driver, 1.6
[    0.530851] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.530942] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.540254]   alloc irq_desc for 19 on node 0
[    0.540259]   alloc kstat_irqs on node 0
[    0.540272] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.540295] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.540370] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.540406] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.540421] ehci_hcd 0000:00:13.5: debug port 1
[    0.540459] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
[    0.560052] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.560186] usb usb1: configuration #1 chosen from 1 choice
[    0.560215] hub 1-0:1.0: USB hub found
[    0.560226] hub 1-0:1.0: 10 ports detected
[    0.560337] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.570279] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.570305] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.570383] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.570427] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[    0.634262] usb usb2: configuration #1 chosen from 1 choice
[    0.634294] hub 2-0:1.0: USB hub found
[    0.634308] hub 2-0:1.0: 2 ports detected
[    0.640233]   alloc irq_desc for 17 on node 0
[    0.640237]   alloc kstat_irqs on node 0
[    0.640250] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.640275] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.640352] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.640393] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
[    0.683596] Freeing initrd memory: 8141k freed
[    0.704244] usb usb3: configuration #1 chosen from 1 choice
[    0.704274] hub 3-0:1.0: USB hub found
[    0.704288] hub 3-0:1.0: 2 ports detected
[    0.704422]   alloc irq_desc for 18 on node 0
[    0.704424]   alloc kstat_irqs on node 0
[    0.704436] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.704458] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.704500] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.704541] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[    0.764103] usb usb4: configuration #1 chosen from 1 choice
[    0.764126] hub 4-0:1.0: USB hub found
[    0.764137] hub 4-0:1.0: 2 ports detected
[    0.764213] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.764224] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.764258] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.764278] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
[    0.824101] usb usb5: configuration #1 chosen from 1 choice
[    0.824125] hub 5-0:1.0: USB hub found
[    0.824136] hub 5-0:1.0: 2 ports detected
[    0.824207] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.824220] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.824269] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.824286] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
[    0.884095] usb usb6: configuration #1 chosen from 1 choice
[    0.884122] hub 6-0:1.0: USB hub found
[    0.884131] hub 6-0:1.0: 2 ports detected
[    0.884185] uhci_hcd: USB Universal Host Controller Interface driver
[    0.884272] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.884676] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.884682] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.884767] mice: PS/2 mouse device common for all mice
[    0.884861] rtc_cmos 00:03: RTC can wake from S4
[    0.884906] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.884937] rtc0: alarms up to one month, 242 bytes nvram
[    0.885069] device-mapper: uevent: version 1.0.3
[    0.885212] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.885265] device-mapper: multipath: version 1.1.0 loaded
[    0.885268] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.885402] cpuidle: using governor ladder
[    0.885404] cpuidle: using governor menu
[    0.885762] TCP cubic registered
[    0.885918] NET: Registered protocol family 10
[    0.886381] lo: Disabled Privacy Extensions
[    0.886641] NET: Registered protocol family 17
[    0.886676] powernow-k8: Found 1 AMD Sempron(tm) Processor LE-1250 processors (1 cpu cores) (version 2.20.00)
[    0.886727] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
[    0.886729] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
[    0.886731] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
[    0.886733] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    0.886856] PM: Resume from disk failed.
[    0.886881] registered taskstats version 1
[    0.887405]   Magic number: 11:716:947
[    0.887439] tty tty4: hash matches
[    0.887500] rtc_cmos 00:03: setting system clock to 2011-05-27 17:55:58 UTC (1306518958)
[    0.887502] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.887504] EDD information not available.
[    0.887563] Freeing unused kernel memory: 884k freed
[    0.888082] Write protecting the kernel read-only data: 7704k
[    0.901200] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.910865] udev: starting version 151
[    1.129017] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.129042] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.129089] r8169 0000:02:00.0: setting latency timer to 64
[    1.129138]   alloc irq_desc for 26 on node 0
[    1.129140]   alloc kstat_irqs on node 0
[    1.129153] r8169 0000:02:00.0: irq 26 for MSI/MSI-X
[    1.129855] eth0: RTL8168b/8111b at 0xffffc9001053c000, 00:22:15:ca:94:63, XID 18000000 IRQ 26
[    1.132051] scsi0 : pata_atiixp
[    1.132240] scsi1 : pata_atiixp
[    1.132795] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
[    1.132798] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
[    1.133159] ahci 0000:00:12.0: version 3.0
[    1.133176]   alloc irq_desc for 22 on node 0
[    1.133178]   alloc kstat_irqs on node 0
[    1.133189] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.133215] ahci 0000:00:12.0: ASUS M2A-VM: enabling 64bit DMA
[    1.133316] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.133320] ahci 0000:00:12.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.133773] scsi2 : ahci
[    1.133985] scsi3 : ahci
[    1.134078] scsi4 : ahci
[    1.134167] scsi5 : ahci
[    1.134295] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.134299] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.134303] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.134307] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    1.340476] ata1.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[    1.340481] ata1.00: ATA-8: WDC WD3200AAJB-22WGA0, 00.02C01, max UDMA/100
[    1.340484] ata1.00: 625142448 sectors, multi 1: LBA48 
[    1.340505] ata1.00: limited to UDMA/33 due to 40-wire cable
[    1.380648] ata1.00: configured for UDMA/33
[    1.380761] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJB-2 00.0 PQ: 0 ANSI: 5
[    1.380924] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.381261] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.381309] sd 0:0:0:0: [sda] Write Protect is off
[    1.381312] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.381337] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.381474]  sda: sda1 < sda5 > sda2
[    1.408176] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.480038] ata5: SATA link down (SStatus 0 SControl 300)
[    1.480068] ata3: SATA link down (SStatus 0 SControl 300)
[    1.660021] ata4: softreset failed (device not ready)
[    1.660024] ata4: applying SB600 PMP SRST workaround and retrying
[    1.660040] ata6: softreset failed (device not ready)
[    1.660043] ata6: applying SB600 PMP SRST workaround and retrying
[    1.840031] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.840055] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.852546] ata4.00: ATAPI: PHILIPS SPD2513P, MP03, max UDMA/100
[    1.852564] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.860644] ata6.00: ATA-7: WDC WD2500YS-01SHB1, 20.06C06, max UDMA/133
[    1.860647] ata6.00: 490234752 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.860665] ata6.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.861488] ata6.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.861491] ata6.00: configured for UDMA/133
[    1.865481] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.865483] ata4.00: configured for UDMA/100
[    1.881086] scsi 3:0:0:0: CD-ROM            PHILIPS  SPD2513P         MP03 PQ: 0 ANSI: 5
[    1.886396] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.886399] Uniform CD-ROM driver Revision: 3.20
[    1.886507] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.886565] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    1.886828] scsi 5:0:0:0: Direct-Access     ATA      WDC WD2500YS-01S 20.0 PQ: 0 ANSI: 5
[    1.887002] sd 5:0:0:0: [sdb] 490234752 512-byte logical blocks: (251 GB/233 GiB)
[    1.887046] sd 5:0:0:0: [sdb] Write Protect is off
[    1.887048] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.887072] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.887198]  sdb:
[    1.887332] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    1.893387]  sdb1 sdb2 < sdb5 sdb6 >
[    1.919276] sd 5:0:0:0: [sdb] Attached SCSI disk
[    2.229058] EXT4-fs (sdb5): mounted filesystem with ordered data mode
[   13.432582] udev: starting version 151
[   13.492356] Adding 2993144k swap on /dev/sdb6.  Priority:-1 extents:1 across:2993144k 
[   13.575564] lp: driver loaded but no devices found
[   13.591402] vga16fb: initializing
[   13.591407] vga16fb: mapped to 0xffff8800000a0000
[   13.591475] fb0: VGA16 VGA frame buffer device
[   13.617726] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.947031] type=1505 audit(1306533371.552:2):  operation="profile_load" pid=597 name="/sbin/dhclient3"
[   13.947299] type=1505 audit(1306533371.552:3):  operation="profile_load" pid=597 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.947455] type=1505 audit(1306533371.552:4):  operation="profile_load" pid=597 name="/usr/lib/connman/scripts/dhclient-script"
[   14.022874] nvidia: module license 'NVIDIA' taints kernel.
[   14.022879] Disabling lock debugging due to kernel taint
[   14.516053] parport_pc 00:08: reported by Plug and Play ACPI
[   14.516087] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   14.773236] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   14.790312] EDAC MC: Ver: 2.1.0 Apr  8 2011
[   14.810262] lp0: using parport0 (interrupt-driven).
[   14.835137] cfg80211: Calling CRDA to update world regulatory domain
[   14.864592] EDAC amd64_edac:  Ver: 3.2.0 Apr  8 2011
[   14.880496] ppdev: user-space parallel port driver
[   14.891142] cfg80211: World regulatory domain updated:
[   14.891145] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.891148] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.891151] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.891153] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.891155] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.891157] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.895588] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   14.895595] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   14.895596]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   14.895598]  (Note that use of the override may cause unknown side effects.)
[   14.895622] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   15.072947] type=1505 audit(1306533372.682:5):  operation="profile_load" pid=774 name="/usr/share/gdm/guest-session/Xsession"
[   15.085674] type=1505 audit(1306533372.692:6):  operation="profile_replace" pid=775 name="/sbin/dhclient3"
[   15.085970] type=1505 audit(1306533372.692:7):  operation="profile_replace" pid=775 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.086134] type=1505 audit(1306533372.692:8):  operation="profile_replace" pid=775 name="/usr/lib/connman/scripts/dhclient-script"
[   15.093282] Linux video capture interface: v2.00
[   15.163326] type=1505 audit(1306533372.772:9):  operation="profile_load" pid=780 name="/usr/bin/evince"
[   15.166659] logips2pp: Detected unknown logitech mouse model 127
[   15.191762] type=1505 audit(1306533372.802:10):  operation="profile_load" pid=780 name="/usr/bin/evince-previewer"
[   15.199697] cx18:  Start initialization, version 1.2.0
[   15.200170] cx18-0: Initializing card 0
[   15.200174] cx18-0: Autodetected Hauppauge card
[   15.210282] r8169: eth0: link down
[   15.210497] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.213653] type=1505 audit(1306533372.822:11):  operation="profile_load" pid=780 name="/usr/bin/evince-thumbnailer"
[   15.223171]   alloc irq_desc for 20 on node 0
[   15.223173]   alloc kstat_irqs on node 0
[   15.223186] cx18 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   15.224487] cx18-0: cx23418 revision 01010000 (B)
[   15.433268] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.507355] Console: switching to colour frame buffer device 80x30
[   15.582389] tveeprom 1-0050: Hauppauge model 74041, rev C5B2, serial# 3013423
[   15.582394] tveeprom 1-0050: MAC address is 00-0D-FE-2D-FB-2F
[   15.582397] tveeprom 1-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   15.582400] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   15.582402] tveeprom 1-0050: audio processor is CX23418 (idx 38)
[   15.582405] tveeprom 1-0050: decoder processor is CX23418 (idx 31)
[   15.582407] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[   15.582410] cx18-0: Autodetected Hauppauge HVR-1600
[   15.582412] cx18-0: Simultaneous Digital and Analog TV capture supported
[   15.582786] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.582793] nvidia 0000:01:00.0: setting latency timer to 64
[   15.583525] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.22  Wed Nov 11 05:08:25 PST 2009
[   15.680812] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   15.708808] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[   15.918506] IRQ 20/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   15.930316] tuner 2-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   15.934219] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   15.947431] tuner-simple 2-0061: creating new instance
[   15.947436] tuner-simple 2-0061: type set to 50 (TCL 2002N)
[   15.949034] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   15.949038] DVB: registering new adapter (cx18)
[   16.131069] MXL5005S: Attached at address 0x63
[   16.131075] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   16.131199] cx18-0: DVB Frontend registered
[   16.131201] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   16.131244] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   16.131272] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   16.131298] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   16.131301] cx18-0: Initialized card: Hauppauge HVR-1600
[   16.131627] cx18:  End initialization
[   16.146286]   alloc irq_desc for 21 on node 0
[   16.146290]   alloc kstat_irqs on node 0
[   16.146303] rt61pci 0000:03:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.154754] cx18 0000:03:05.0: firmware: requesting v4l-cx23418-cpu.fw
[   16.359287] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   16.369669] phy0: Selected rate control algorithm 'minstrel'
[   16.370447] Registered led device: rt61pci-phy0::radio
[   16.370463] Registered led device: rt61pci-phy0::assoc
[   16.388922] rt61pci 0000:03:06.0: firmware: requesting rt2561s.bin
[   16.480342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.693645] cx18 0000:03:05.0: firmware: requesting v4l-cx23418-apu.fw
[   16.844883] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   16.898917] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   17.110097] cx18 0000:03:05.0: firmware: requesting v4l-cx23418-cpu.fw
[   17.452398] cx18 0000:03:05.0: firmware: requesting v4l-cx23418-apu.fw
[   17.881752] cx18 0000:03:05.0: firmware: requesting v4l-cx23418-dig.fw
[   18.081178] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   18.113007] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   31.040093] wlan0: deauthenticating from 00:17:3f:f1:1a:2c by local choice (reason=3)
[   31.040804] wlan0: direct probe to AP 00:17:3f:f1:1a:2c (try 1)
[   31.240033] wlan0: direct probe to AP 00:17:3f:f1:1a:2c (try 2)
[   31.440033] wlan0: direct probe to AP 00:17:3f:f1:1a:2c (try 3)
[   31.640041] wlan0: direct probe to AP 00:17:3f:f1:1a:2c timed out
[   42.500062] wlan0: direct probe to AP 00:17:3f:f1:1a:2c (try 1)
[   42.503337] wlan0: direct probe responded
[   42.503344] wlan0: authenticate with AP 00:17:3f:f1:1a:2c (try 1)
[   42.505300] wlan0: authenticated
[   42.505330] wlan0: associate with AP 00:17:3f:f1:1a:2c (try 1)
[   42.507777] wlan0: RX AssocResp from 00:17:3f:f1:1a:2c (capab=0x431 status=0 aid=1)
[   42.507782] wlan0: associated
[   42.508354] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.834859] Intel AES-NI instructions are not detected.
[   42.857764] padlock: VIA PadLock not detected.
[   53.420028] wlan0: no IPv6 routers present
[   77.650046] Clocksource tsc unstable (delta = -229130880 ns)
[   95.790078] usb 4-1: new full speed USB device using ohci_hcd and address 2
[   95.984550] usb 4-1: configuration #1 chosen from 1 choice
[   96.088694] Initializing USB Mass Storage driver...
[   96.088949] scsi6 : SCSI emulation for USB Mass Storage devices
[   96.089270] usbcore: registered new interface driver usb-storage
[   96.089276] USB Mass Storage support registered.
[   96.101377] usb-storage: device found at 2
[   96.101384] usb-storage: waiting for device to settle before scanning
[  101.106109] usb-storage: device scan complete
[  101.111332] scsi 6:0:0:0: Direct-Access     M-Sys    Pan UCL   Mode   3.00 PQ: 0 ANSI: 0 CCS
[  101.111778] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  101.132331] sd 6:0:0:0: [sdc] 32768 512-byte logical blocks: (16.7 MB/16.0 MiB)
[  101.138288] sd 6:0:0:0: [sdc] Write Protect is off
[  101.138291] sd 6:0:0:0: [sdc] Mode Sense: 45 00 00 08
[  101.138294] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  101.162312] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  101.162320]  sdc: unknown partition table
[  101.210321] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  101.210329] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  102.298456] usb 4-1: USB disconnect, address 2
[  102.790086] usb 4-1: new full speed USB device using ohci_hcd and address 3
[  103.004531] usb 4-1: configuration #1 chosen from 1 choice
[  103.029149] scsi7 : SCSI emulation for USB Mass Storage devices
[  103.033910] usb-storage: device found at 3
[  103.033916] usb-storage: waiting for device to settle before scanning
[  108.030405] usb-storage: device scan complete
[  108.036350] scsi 7:0:0:0: Direct-Access     M-Sys    Pan UCL   Mode   3.00 PQ: 0 ANSI: 0 CCS
[  108.041545] sd 7:0:0:0: Attached scsi generic sg3 type 0
[  108.056047] sd 7:0:0:0: [sdc] 32768 512-byte logical blocks: (16.7 MB/16.0 MiB)
[  108.061136] sd 7:0:0:0: [sdc] Write Protect is off
[  108.061148] sd 7:0:0:0: [sdc] Mode Sense: 45 00 00 08
[  108.061153] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  108.087337] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  108.087352]  sdc: unknown partition table
[  108.138361] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[  108.138374] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by wojox on 2011-05-27
No it's called palimpsest. The icon says Disk Utility. Alt_F2 and type palimpsest.

---

### Post by sofasurfer on 2011-05-27
When I put the stick in, palimpsest shows that a usb item exists but the fields for the make, model, driver, etc are all blank. I have pretty much concluded that the stick has died. I read that they do wear out after 10,000-100,000 re-writes. I'm probably no where near that but it has been used a lot for the past 3 or 4 years. Paid $15 for it (2gig). I see Office Max and Walmart both have a 8 gig for $13...Wintec and Verbatum.
You know of any better deals out there?

---

