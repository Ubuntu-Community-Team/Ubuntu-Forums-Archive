---
title: "Automount USB drives."
date: 2010-06-06
forum: General Help
---

### Post by warfacegod on 2010-06-06
Suffice it to say, I'm an idjit and can't figure out how to get my USB drives to automount.

(warfacegod hangs head in shame that his divine powers didn't provide him the answer to this newb question)

---

### Post by Leppie on 2010-06-06
are these pendrives?
if so, try putting yourself in the fuse group:
```
sudo adduser wfg fuse
```

---

### Post by warfacegod on 2010-06-06
2 4GB jump drives and 1 1TB external HDD.

I'll see if adding myself to fuse works.

---

### Post by Leppie on 2010-06-06
while you're at it, also check the "Access external storage devices automatically" option in the users and groups panel.

---

### Post by warfacegod on 2010-06-06
> **Leppie said:**
> while you're at it, also check the "Access external storage devices automatically" option in the users and groups panel.

That was already checked. Adding myself to fuse didn't work nor did adding myself to root.

---

### Post by Leppie on 2010-06-06
what does dmesg say?

---

### Post by warfacegod on 2010-06-06
This?

```
[    0.242770] PCI: Using ACPI for IRQ routing
[    0.242770] Expanded resource reserved due to conflict with Adapter ROM
[    0.252015] Bluetooth: Core ver 2.15
[    0.252043] NET: Registered protocol family 31
[    0.252043] Bluetooth: HCI device and connection manager initialized
[    0.252043] Bluetooth: HCI socket layer initialized
[    0.252043] NetLabel: Initializing
[    0.252043] NetLabel:  domain hash size = 128
[    0.252043] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.252055] NetLabel:  unlabeled traffic allowed by default
[    0.252184] hpet clockevent registered
[    0.252188] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.252195] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.252203] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.268019] pnp: PnP ACPI init
[    0.268045] ACPI: bus type pnp registered
[    0.292091] pnp: PnP ACPI: found 10 devices
[    0.292095] ACPI: ACPI bus type pnp unregistered
[    0.292100] PnPBIOS: Disabled by ACPI PNP
[    0.292117] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.292122] system 00:01: ioport range 0x1180-0x11bf has been reserved
[    0.292126] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.292131] system 00:01: ioport range 0xfe00-0xfe00 has been reserved
[    0.292135] system 00:01: ioport range 0x200-0x20f has been reserved
[    0.292141] system 00:01: iomem range 0xfecf0000-0xfecfffff could not be reserved
[    0.292146] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.326870] AppArmor: AppArmor Filesystem Enabled
[    0.326927] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.326930] pci 0000:00:01.0:   IO window: disabled
[    0.326937] pci 0000:00:01.0:   MEM window: 0xc1000000-0xc1ffffff
[    0.326943] pci 0000:00:01.0:   PREFETCH window: 0xe0000000-0xefffffff
[    0.326961] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    0.326964] pci 0000:02:04.0:   IO window: 0x003400-0x0034ff
[    0.326970] pci 0000:02:04.0:   IO window: 0x003800-0x0038ff
[    0.326976] pci 0000:02:04.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.326982] pci 0000:02:04.0:   MEM window: 0x8c000000-0x8fffffff
[    0.326988] pci 0000:02:04.1: CardBus bridge, secondary bus 0000:07
[    0.326991] pci 0000:02:04.1:   IO window: 0x003c00-0x003cff
[    0.326997] pci 0000:02:04.1:   IO window: 0x001400-0x0014ff
[    0.327003] pci 0000:02:04.1:   PREFETCH window: 0x84000000-0x87ffffff
[    0.327009] pci 0000:02:04.1:   MEM window: 0x90000000-0x93ffffff
[    0.327015] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.327019] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.327026] pci 0000:00:1e.0:   MEM window: 0xc2000000-0xc20fffff
[    0.327032] pci 0000:00:1e.0:   PREFETCH window: 0x80000000-0x87ffffff
[    0.327050] pci 0000:00:1e.0: setting latency timer to 64
[    0.327061] pci 0000:02:04.0: enabling device (0000 -> 0003)
[    0.327069]   alloc irq_desc for 16 on node -1
[    0.327072]   alloc kstat_irqs on node -1
[    0.327079] pci 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.327092] pci 0000:02:04.1: enabling device (0000 -> 0003)
[    0.327097]   alloc irq_desc for 17 on node -1
[    0.327100]   alloc kstat_irqs on node -1
[    0.327105] pci 0000:02:04.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.327115] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.327119] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.327123] pci_bus 0000:01: resource 1 mem: [0xc1000000-0xc1ffffff]
[    0.327126] pci_bus 0000:01: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.327130] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.327133] pci_bus 0000:02: resource 1 mem: [0xc2000000-0xc20fffff]
[    0.327137] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x87ffffff]
[    0.327141] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.327144] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.327148] pci_bus 0000:03: resource 0 io:  [0x3400-0x34ff]
[    0.327151] pci_bus 0000:03: resource 1 io:  [0x3800-0x38ff]
[    0.327155] pci_bus 0000:03: resource 2 pref mem [0x80000000-0x83ffffff]
[    0.327158] pci_bus 0000:03: resource 3 mem: [0x8c000000-0x8fffffff]
[    0.327162] pci_bus 0000:07: resource 0 io:  [0x3c00-0x3cff]
[    0.327166] pci_bus 0000:07: resource 1 io:  [0x1400-0x14ff]
[    0.327169] pci_bus 0000:07: resource 2 pref mem [0x84000000-0x87ffffff]
[    0.327173] pci_bus 0000:07: resource 3 mem: [0x90000000-0x93ffffff]
[    0.327229] NET: Registered protocol family 2
[    0.327368] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.327851] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.328474] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.328855] TCP: Hash tables configured (established 131072 bind 65536)
[    0.328861] TCP reno registered
[    0.329003] NET: Registered protocol family 1
[    0.329102] Trying to unpack rootfs image as initramfs...
[    0.588284] Freeing initrd memory: 8196k freed
[    0.596710] cpufreq-nforce2: No nForce2 chipset.
[    0.596749] Scanning for low memory corruption every 60 seconds
[    0.596891] audit: initializing netlink socket (disabled)
[    0.596909] type=2000 audit(1275838467.596:1): initialized
[    0.605152] highmem bounce pool size: 64 pages
[    0.605160] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.607261] VFS: Disk quotas dquot_6.5.2
[    0.607355] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.608171] fuse init (API version 7.12)
[    0.608287] msgmni has been set to 1705
[    0.608623] alg: No test for stdrng (krng)
[    0.608646] io scheduler noop registered
[    0.608649] io scheduler anticipatory registered
[    0.608652] io scheduler deadline registered
[    0.608719] io scheduler cfq registered (default)
[    0.608844] pci 0000:01:00.0: Boot video device
[    0.609006] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.609042] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.609283] ACPI: AC Adapter [ACAD] (on-line)
[    0.609371] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.609376] ACPI: Power Button [PWRF]
[    0.609441] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.609489] ACPI: Lid Switch [LID]
[    0.609550] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.609555] ACPI: Power Button [PWRB]
[    0.609859] processor LNXCPU:00: registered as cooling_device0
[    0.609917] processor LNXCPU:01: registered as cooling_device1
[    0.633477] isapnp: Scanning for PnP cards...
[    0.676599] ACPI: Battery Slot [BAT1] (battery present)
[    0.752829] Switched to high resolution mode on CPU 1
[    0.756057] Switched to high resolution mode on CPU 0
[    0.987232] isapnp: No Plug & Play device found
[    0.988804] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.989231] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.989239] serial 0000:00:1f.6: PCI INT B disabled
[    0.990605] brd: module loaded
[    0.991265] loop: module loaded
[    0.991385] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.991547] ata_piix 0000:00:1f.1: version 2.13
[    0.991560] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.991569]   alloc irq_desc for 18 on node -1
[    0.991572]   alloc kstat_irqs on node -1
[    0.991582] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.991636] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.991772] scsi0 : ata_piix
[    0.991904] scsi1 : ata_piix
[    0.993103] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1880 irq 14
[    0.993107] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1888 irq 15
[    0.994538] Fixed MDIO Bus: probed
[    0.994591] PPP generic driver version 2.4.2
[    0.994740] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.994771]   alloc irq_desc for 23 on node -1
[    0.994775]   alloc kstat_irqs on node -1
[    0.994784] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.994806] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.994811] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.994856] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.998769] ehci_hcd 0000:00:1d.7: debug port 1
[    0.998777] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.998796] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xc0000000
[    1.012016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.012126] usb usb1: configuration #1 chosen from 1 choice
[    1.012168] hub 1-0:1.0: USB hub found
[    1.012180] hub 1-0:1.0: 8 ports detected
[    1.012277] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.012304] uhci_hcd: USB Universal Host Controller Interface driver
[    1.012352] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.012361] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.012366] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.012413] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.012447] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001800
[    1.012552] usb usb2: configuration #1 chosen from 1 choice
[    1.012590] hub 2-0:1.0: USB hub found
[    1.012600] hub 2-0:1.0: 2 ports detected
[    1.012661]   alloc irq_desc for 19 on node -1
[    1.012665]   alloc kstat_irqs on node -1
[    1.012672] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.012679] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.012684] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.012729] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.012760] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    1.012860] usb usb3: configuration #1 chosen from 1 choice
[    1.012900] hub 3-0:1.0: USB hub found
[    1.012909] hub 3-0:1.0: 2 ports detected
[    1.012971] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.012978] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.012983] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.013056] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.013088] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    1.013207] usb usb4: configuration #1 chosen from 1 choice
[    1.013245] hub 4-0:1.0: USB hub found
[    1.013256] hub 4-0:1.0: 2 ports detected
[    1.013318] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.013326] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.013330] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.013375] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.013399] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    1.013502] usb usb5: configuration #1 chosen from 1 choice
[    1.013538] hub 5-0:1.0: USB hub found
[    1.013549] hub 5-0:1.0: 2 ports detected
[    1.013679] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.022327] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.029687] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.029698] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.029706] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.029710] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.029714] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.029795] mice: PS/2 mouse device common for all mice
[    1.029935] rtc_cmos 00:04: RTC can wake from S4
[    1.029984] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.030009] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.030161] device-mapper: uevent: version 1.0.3
[    1.030323] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.030447] device-mapper: multipath: version 1.1.0 loaded
[    1.030452] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.030637] EISA: Probing bus 0 at eisa.0
[    1.030645] Cannot allocate resource for EISA slot 1
[    1.030649] Cannot allocate resource for EISA slot 2
[    1.030652] Cannot allocate resource for EISA slot 3
[    1.030677] EISA: Detected 0 cards.
[    1.030819] cpuidle: using governor ladder
[    1.030823] cpuidle: using governor menu
[    1.031600] TCP cubic registered
[    1.031782] NET: Registered protocol family 10
[    1.032471] lo: Disabled Privacy Extensions
[    1.033017] NET: Registered protocol family 17
[    1.033050] Bluetooth: L2CAP ver 2.13
[    1.033053] Bluetooth: L2CAP socket layer initialized
[    1.033057] Bluetooth: SCO (Voice Link) ver 0.6
[    1.033060] Bluetooth: SCO socket layer initialized
[    1.033116] Bluetooth: RFCOMM TTY layer initialized
[    1.033125] Bluetooth: RFCOMM socket layer initialized
[    1.033129] Bluetooth: RFCOMM ver 1.11
[    1.033179] Using IPI No-Shortcut mode
[    1.033282] PM: Resume from disk failed.
[    1.033300] registered taskstats version 1
[    1.033475]   Magic number: 14:70:588
[    1.033562] rtc_cmos 00:04: setting system clock to 2010-06-06 15:34:28 UTC (1275838468)
[    1.033567] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.033569] EDD information not available.
[    1.053389] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.156642] ata2.00: ATAPI: MATSHITADVD-RAM UJ-811, H100, max UDMA/33
[    1.172295] ata2.00: configured for UDMA/33
[    1.213625] ata1.00: ATA-8: WDC WD2500BEVE-00WZT0, 01.01A01, max UDMA/100
[    1.213632] ata1.00: 488397168 sectors, multi 16: LBA48 
[    1.228595] ata1.00: configured for UDMA/100
[    1.228728] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVE-0 01.0 PQ: 0 ANSI: 5
[    1.228907] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.228993] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.229136] sd 0:0:0:0: [sda] Write Protect is off
[    1.229140] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.229176] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.229366]  sda:
[    1.231078] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-811   H100 PQ: 0 ANSI: 5
[    1.233374]  sda1 sda2 sda3
[    1.233760] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.263286] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.263292] Uniform CD-ROM driver Revision: 3.20
[    1.263406] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.263482] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.263524] Freeing unused kernel memory: 544k freed
[    1.264173] Write protecting the kernel text: 4584k
[    1.264245] Write protecting the kernel read-only data: 1844k
[    1.325054] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    1.405506] ramzswap: disk size set to 515304 kB
[    1.449074] Linux agpgart interface v0.103
[    1.474261] usb 1-5: configuration #1 chosen from 1 choice
[    1.475394] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[    1.557883] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.578051] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/device:02/input/input5
[    1.578142] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.638451] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.638509] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.645892] FDC 0 is a post-1991 82077
[    1.665486] 8139too Fast Ethernet driver 0.9.28
[    1.665563] 8139too 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.667354] eth0: RealTek RTL8139 at 0x3000, 00:02:3f:81:cf:2e, IRQ 17
[    1.678446] Adding 515300k swap on /dev/ramzswap0.  Priority:100 extents:1 across:515300k SSD
[    1.694902] ohci1394 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.704172] Initializing USB Mass Storage driver...
[    1.704366] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.704563] usb-storage: device found at 2
[    1.704568] usb-storage: waiting for device to settle before scanning
[    1.704589] usbcore: registered new interface driver usb-storage
[    1.704596] USB Mass Storage support registered.
[    1.749044] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[c2014000-c20147ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.208236] vesafb: framebuffer at 0xe0000000, mapped to 0xf8300000, using 3072k, total 3072k
[    2.208241] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    2.208244] vesafb: scrolling: redraw
[    2.208250] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    2.208337] fb0: VESA VGA frame buffer device
[    2.217518] Console: switching to colour frame buffer device 128x48
[    2.664838] xor: automatically using best checksumming function: pIII_sse
[    2.684009]    pIII_sse  :  3554.000 MB/sec
[    2.684013] xor: using function: pIII_sse (3554.000 MB/sec)
[    2.687488] device-mapper: dm-raid45: initialized v0.2594b
[    3.029249] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f3739004358]
[    3.045079] EXT4-fs (sda1): barriers enabled
[    3.053379] kjournald2 starting: pid 390, dev sda1:8, commit interval 5 seconds
[    3.053465] EXT4-fs (sda1): delayed allocation enabled
[    3.053471] EXT4-fs: file extents enabled
[    3.054308] EXT4-fs: mballoc enabled
[    3.054329] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.704236] usb-storage: device scan complete
[    6.704707] scsi 2:0:0:0: Direct-Access              Gigaware         8.02 PQ: 0 ANSI: 0 CCS
[    6.705382] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.706058] sd 2:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[    6.706553] sd 2:0:0:0: [sdb] Write Protect is off
[    6.706557] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    6.706561] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.708427] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.708432]  sdb: sdb1
[    6.710801] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.710806] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    7.812023] usb 1-7: new high speed USB device using ehci_hcd and address 3
[    7.964422] usb 1-7: configuration #1 chosen from 1 choice
[    7.966060] scsi3 : SCSI emulation for USB Mass Storage devices
[    7.966171] usb-storage: device found at 3
[    7.966175] usb-storage: waiting for device to settle before scanning
[   12.964267] usb-storage: device scan complete
[   12.968228] scsi 3:0:0:0: Direct-Access     ST310005 20AS                  PQ: 0 ANSI: 2
[   12.968909] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   12.969834] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   12.972083] sd 3:0:0:0: [sdc] Write Protect is off
[   12.972088] sd 3:0:0:0: [sdc] Mode Sense: 38 00 00 00
[   12.972092] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   12.975331] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   12.975336]  sdc: sdc1
[   12.999462] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   12.999468] sd 3:0:0:0: [sdc] Attached SCSI disk
[   13.389427] udev: starting version 147
[   13.428222] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.442504] lp: driver loaded but no devices found
[   13.495624] intel_rng: FWH not detected
[   13.703575] nvidia: module license 'NVIDIA' taints kernel.
[   13.703582] Disabling lock debugging due to kernel taint
[   13.782518] EXT4-fs (sda1): internal journal on sda1:8
[   14.065296] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   14.065312] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.065622] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009
[   14.086589] parport_pc 00:09: reported by Plug and Play ACPI
[   14.086622] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   14.120660] yenta_cardbus 0000:02:04.0: CardBus bridge found [1179:0001]
[   14.143855] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.166204] ppdev: user-space parallel port driver
[   14.169247] cfg80211: Calling CRDA to update world regulatory domain
[   14.169847] lp0: using parport0 (interrupt-driven).
[   14.205823] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   14.206714] sr: Sense Key : Hardware Error [current] 
[   14.206722] sr: Add. Sense: Head select fault
[   14.252713] yenta_cardbus 0000:02:04.0: ISA IRQ mask 0x0c38, PCI irq 16
[   14.252721] yenta_cardbus 0000:02:04.0: Socket status: 30000007
[   14.252729] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   14.252747] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   14.252755] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   14.253227] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0xc2000000 - 0xc20fffff
[   14.253237] yenta_cardbus 0000:02:04.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[   14.255367] yenta_cardbus 0000:02:04.1: CardBus bridge found [1179:0001]
[   14.297074] cfg80211: World regulatory domain updated:
[   14.297082] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.297088] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.297094] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.297100] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.297105] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.297111] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.364624] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   14.365521] sr: Sense Key : Hardware Error [current] 
[   14.365529] sr: Add. Sense: Head select fault
[   14.376637] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.376683] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.381622] yenta_cardbus 0000:02:04.1: ISA IRQ mask 0x0c38, PCI irq 17
[   14.381628] yenta_cardbus 0000:02:04.1: Socket status: 30000087
[   14.381634] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   14.381647] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   14.381652] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x3fff: clean.
[   14.381986] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge Memory window: 0xc2000000 - 0xc20fffff
[   14.381991] yenta_cardbus 0000:02:04.1: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x87ffffff
[   14.382508] ath5k 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.382583] ath5k 0000:02:02.0: registered as 'phy0'
[   14.603386] ath: EEPROM regdomain: 0x64
[   14.603391] ath: EEPROM indicates we should expect a direct regpair map
[   14.603396] ath: Country alpha2 being used: 00
[   14.603399] ath: Regpair used: 0x64
[   14.604466] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input6
[   14.630196] phy0: Selected rate control algorithm 'minstrel'
[   14.631433] Registered led device: ath5k-phy0::rx
[   14.631474] Registered led device: ath5k-phy0::tx
[   14.631481] ath5k phy0: Atheros AR5211 chip found (MAC: 0x42, PHY: 0x30)
[   14.631487] ath5k phy0: RF5111 5GHz radio found (0x17)
[   14.631492] ath5k phy0: RF2111 2GHz radio found (0x23)
[   14.633982] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input7
[   14.724034] intel8x0_measure_ac97_clock: measured 53361 usecs (2570 samples)
[   14.724039] intel8x0: clocking to 48000
[   14.891021] EXT4-fs (sda2): barriers enabled
[   14.913434] kjournald2 starting: pid 862, dev sda2:8, commit interval 5 seconds
[   14.946546] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   14.949518] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   14.950302] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   14.950961] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   14.951853] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   14.952939] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   14.955363] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   14.956168] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   14.956820] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   14.957818] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.958730] EXT4-fs (sda2): internal journal on sda2:8
[   14.958741] EXT4-fs (sda2): delayed allocation enabled
[   14.958749] EXT4-fs: file extents enabled
[   14.968914] EXT4-fs: mballoc enabled
[   14.968946] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   15.168645] eth0: link down
[   15.168946] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.256446] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.561778] type=1505 audit(1275838483.027:2): operation="profile_load" pid=1052 name=/sbin/dhclient3
[   15.562548] type=1505 audit(1275838483.027:3): operation="profile_load" pid=1052 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.562961] type=1505 audit(1275838483.027:4): operation="profile_load" pid=1052 name=/usr/lib/connman/scripts/dhclient-script
[   15.576395] type=1505 audit(1275838483.039:5): operation="profile_load" pid=1061 name=/usr/bin/evince
[   15.588469] type=1505 audit(1275838483.051:6): operation="profile_load" pid=1061 name=/usr/bin/evince-previewer
[   15.595191] type=1505 audit(1275838483.059:7): operation="profile_load" pid=1061 name=/usr/bin/evince-thumbnailer
[   15.648302] type=1505 audit(1275838483.111:8): operation="profile_load" pid=1063 name=/usr/lib/cups/backend/cups-pdf
[   15.649280] type=1505 audit(1275838483.115:9): operation="profile_load" pid=1063 name=/usr/sbin/cupsd
[   15.653943] type=1505 audit(1275838483.119:10): operation="profile_load" pid=1068 name=/usr/sbin/tcpdump
[   15.876265] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
[   15.876298] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
[   15.876371] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   16.844057] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   16.844099] sr: Sense Key : Hardware Error [current] 
[   16.844110] sr: Add. Sense: Head select fault
[   16.957822] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   16.957852] sr: Sense Key : Hardware Error [current] 
[   16.957861] sr: Add. Sense: Head select fault
[   16.957872] cdrom: This disc doesn't have any tracks I recognize!
[   17.016195] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   17.016226] sr: Sense Key : Hardware Error [current] 
[   17.016235] sr: Add. Sense: Head select fault
[   17.108731] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   17.108765] sr: Sense Key : Hardware Error [current] 
[   17.108776] sr: Add. Sense: Head select fault
[   18.124387] CPU0 attaching NULL sched-domain.
[   18.124396] CPU1 attaching NULL sched-domain.
[   18.140097] CPU0 attaching sched-domain:
[   18.140103]  domain 0: span 0-1 level SIBLING
[   18.140107]   groups: 0 1
[   18.140117] CPU1 attaching sched-domain:
[   18.140120]  domain 0: span 0-1 level SIBLING
[   18.140124]   groups: 1 0
[   31.574501] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   31.581087] ACPI: EC: GPE storm detected, transactions will use polling mode
[   39.845047] wlan0: direct probe to AP 00:18:f8:d5:28:e1 try 1
[   40.052227] wlan0: direct probe to AP 00:18:f8:d5:28:e1 try 2
[   40.259332] wlan0: direct probe to AP 00:18:f8:d5:28:e1 try 3
[   40.262519] wlan0 direct probe responded
[   40.262526] wlan0: authenticate with AP 00:18:f8:d5:28:e1
[   40.276034] wlan0: authenticated
[   40.276042] wlan0: associate with AP 00:18:f8:d5:28:e1
[   40.280442] wlan0: RX AssocResp from 00:18:f8:d5:28:e1 (capab=0x401 status=0 aid=2)
[   40.280449] wlan0: associated
[   40.281307] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   51.088011] wlan0: no IPv6 routers present

```

---

### Post by Leppie on 2010-06-06
hmmm...
your dmesg says there's a 4gb usb drive (sdb1) and a 1tb usb drive (sdc1) mounted:
```

[    6.704707] scsi 2:0:0:0: Direct-Access              Gigaware         8.02 PQ: 0 ANSI: 0 CCS
[    6.705382] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.706058] sd 2:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[    6.706553] sd 2:0:0:0: [sdb] Write Protect is off
[    6.706557] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[    6.706561] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.708427] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    6.708432]  sdb: sdb1


``````
[    7.966171] usb-storage: device found at 3
[    7.966175] usb-storage: waiting for device to settle before scanning
[   12.964267] usb-storage: device scan complete
[   12.968228] scsi 3:0:0:0: Direct-Access     ST310005 20AS                  PQ: 0 ANSI: 2
[   12.968909] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   12.969834] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[   12.972083] sd 3:0:0:0: [sdc] Write Protect is off
[   12.972088] sd 3:0:0:0: [sdc] Mode Sense: 38 00 00 00
[   12.972092] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   12.975331] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   12.975336]  sdc: sdc1

```

---

### Post by warfacegod on 2010-06-06
Gparted and Palimpset both say that they are not mounted. Palimpset is able to mount them, Gparted is not. (Finally a useful aspect of Palimpset.)

Tried rebooting with both mounted and still no honey.

---

### Post by Leppie on 2010-06-06
could you post your fstab?

---

### Post by warfacegod on 2010-06-06
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ed41f203-6d06-43b0-88e9-eb1c9be66855 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=ab836dc2-dd09-4060-a6bc-4f0d6ec0fd0c /home           ext4    defaults        0       2
```

---

### Post by Leppie on 2010-06-06
wow, your system is getting more obscure every time...
do you only have 1 useraccount on this system? try creating a new account and add the right privileges and see what happens.

---

### Post by warfacegod on 2010-06-06
> **Leppie said:**
> wow, your system is getting more obscure every time...
do you only have 1 useraccount on this system? try creating a new account and add the right privileges and see what happens.

Yep, one user. Already tried that. No honey. Deleted second user.

---

### Post by warfacegod on 2010-06-06
Is there any reason I can't manually add the UUID's the the fstab? that would make the drives automount wouldn't it?

---

### Post by Leppie on 2010-06-06
> **warfacegod said:**
> Is there any reason I can't manually add the UUID's the the fstab?
no, there's not...

> **warfacegod said:**
> that would make the drives automount wouldn't it?
kind of, but i think it would also slow down your boot process...

---

### Post by warfacegod on 2010-06-06
> **Leppie said:**
> no, there's not...

Great, how do I do that?


> **Leppie said:**
> kind of, but i think it would also slow down your boot process...

Not if they aren't plugged in or turned on as the case maybe.

---

### Post by Leppie on 2010-06-06
> **warfacegod said:**
> Great, how do I do that?
to get the uuid of the partition(s):
```
ls -al /dev/disk/by-uuid/
```an entry in fstab could be something like this:
```
UUID=559E-EA87 /media/pendrive           vfat    defaults        0       0
```

do you by any chance have the package "usbmount" installed? seen some other posts claiming this causes issues...

---

### Post by warfacegod on 2010-06-06
No usbmount installed and editing the fstab didn't work.

---

### Post by warfacegod on 2010-06-06
After editing the fstab, Palimpset will no longer mount the drives. It gives this error message:

```
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 18 in /etc/fstab is bad
mount: only root can mount /dev/sdb1 on /media/04CD-C734
```

---

### Post by Leppie on 2010-06-06
try modifying the entry like this:
```
UUID=04CD-C734 /media/pendrive           vfat    rw,umask=007,gid=46    0       0
```

---

### Post by warfacegod on 2010-06-06
> **Leppie said:**
> try modifying the entry like this:
```
UUID=04CD-C734 /media/pendrive           vfat    rw,umask=007,gid=46    0       0
```

No love on this one either.

---

### Post by warfacegod on 2010-06-06
Fresh install. Problem solved.

Obviously not a great fix but it's better than nothing.

(Props (again) go to Leppie for lending a hand as I have (again) slammed my face into the wall of newbism.)

---

### Post by Leppie on 2010-06-06
i'm sorry it didn't work hoss...
but then again, i know you love reinstalling and messing all up again ;)

---

### Post by warfacegod on 2010-06-06
> **Leppie said:**
> i'm sorry it didn't work hoss...
but then again, i know you love reinstalling and messing all up again ;)

Even my main partition doesn't always escape my divine formatting wrath. My experiment partition never does. It's about to get Elive.

---

### Post by Leppie on 2010-06-06
elive is quite nice, just that enlightenment seems to be in eternal development.

---

### Post by warfacegod on 2010-06-08
It's got a fantastic Live environment but the installer insists on this very MS like "give us money" code thing. Major deal breaker.

---

### Post by Leppie on 2010-06-08
> **king john said:**
> I'd expect if I attach a vfat drive that it will automount, but all I  see is the USB activity.  I do a  'mount -t vfat /dev/sda1  /mnt/usbdrive' and it mounts but will not mount automatically.  The same  goes for a NTFS formatted drive, which is even more touchy,  because  half the time it refuses to mount (usually with a 'superblock' error).
do you always use the mechanisms to safely unmount the drives? i only have these issues when i do not unmount correctly (windows or linux).

---

