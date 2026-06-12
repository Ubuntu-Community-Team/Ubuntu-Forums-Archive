---
title: "what happened : external HFS+ disks are all in read-only mode, VLC won't play files"
date: 2009-09-13
forum: General Help
---

### Post by bjaz on 2009-09-13
hello all

I'm on a gnome running version of jaunty, and all was well, until two days ago.
for a reason i fail to understand, i'm now facing major issues with HFS+ external hdd that i used with no issues for a few months on this system :

the main issue is that all disks now mount as read-only, i really don't know why> I can't create a folder or copy a file there.

my second issue is that VLC can no longer read files, any multimedia file, from these disks. when it could before... Totem video player still works, but with VLC nothing happens. whereas it worked fine before. i've been trying to fix these issues for two days, including a couple of install re-installs of VLC, but to no avail
can anyone help ?

thanks in advance for your help

ben

---

### Post by dragos240 on 2009-09-13
Did you do anything in between the time it worked, and now?

---

### Post by bjaz on 2009-09-13
not that I can remember, no. no new applications or anything like that.
only thing i can think of is having plugged in a secondary screen, RGB, and having rebooted a couple of times. there were a couple of times when the disk wasn't unmounted properly.

the vlc bug is very strange as well. apparently others have had it, but i never did until now.

thanks

ben

---

### Post by dragos240 on 2009-09-13
> **bjaz said:**
> not that I can remember, no. no new applications or anything like that.
only thing i can think of is having plugged in a secondary screen, RGB, and having rebooted a couple of times. there were a couple of times when the disk wasn't unmounted properly.

the vlc bug is very strange as well. apparently others have had it, but i never did until now.

thanks

ben


What flavor of ubuntu are you using?

---

### Post by bjaz on 2009-09-13
intitially xubuntu Jaunty Jackalope, but replaced the xfce with the gnome environment a while back

thanks

ben

---

### Post by bjaz on 2009-09-15
any idea on how to fix this ?

i really can't find anything and all my disk, where i save the data that i'm working on, are still read only. i think i'm going to have to burn CD-R s soon

thanks

ben

---

### Post by bjaz on 2009-09-15
i forgot to add that NTFS-3g.is installed, and all was working well before. can anyone please help me out, it's really becoming problematic and i'm not finding a work around on my own

thanks in advance

ben

---

### Post by bjaz on 2009-09-15
typing demsg in a terminal gives :

[    0.781184] pci 0000:06:03.3: PME# supported from D0 D1 D2 D3hot
[    0.781191] pci 0000:06:03.3: PME# disabled
[    0.781267] pci 0000:06:08.0: reg 10 32bit mmio: [0xb0106000-0xb0106fff]
[    0.781279] pci 0000:06:08.0: reg 14 io port: [0x2000-0x203f]
[    0.781339] pci 0000:06:08.0: supports D1 D2
[    0.781342] pci 0000:06:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.781349] pci 0000:06:08.0: PME# disabled
[    0.781411] pci 0000:00:1e.0: transparent bridge
[    0.781417] pci 0000:00:1e.0: bridge io port: [0x2000-0x2fff]
[    0.781424] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.781468] bus 00 -> node 0
[    0.781477] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.781999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.787562] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.787704] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[    0.787843] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    0.787982] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.788129] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.788268] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.788408] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.788550] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.788796] ACPI: WMI: Mapper loaded
[    0.789024] SCSI subsystem initialized
[    0.789076] libata version 3.00 loaded.
[    0.789140] usbcore: registered new interface driver usbfs
[    0.789162] usbcore: registered new interface driver hub
[    0.789195] usbcore: registered new device driver usb
[    0.789341] PCI: Using ACPI for IRQ routing
[    0.789462] Bluetooth: Core ver 2.13
[    0.789462] NET: Registered protocol family 31
[    0.789462] Bluetooth: HCI device and connection manager initialized
[    0.789462] Bluetooth: HCI socket layer initialized
[    0.789462] NET: Registered protocol family 8
[    0.789462] NET: Registered protocol family 20
[    0.789462] NetLabel: Initializing
[    0.789462] NetLabel:  domain hash size = 128
[    0.789462] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.789462] NetLabel:  unlabeled traffic allowed by default
[    0.789462] hpet clockevent registered
[    0.789462] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.789462] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.789462] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.792088] AppArmor: AppArmor Filesystem Enabled
[    0.792098] pnp: PnP ACPI init
[    0.792098] ACPI: bus type pnp registered
[    0.793829] pnp: PnP ACPI: found 8 devices
[    0.793832] ACPI: ACPI bus type pnp unregistered
[    0.793836] PnPBIOS: Disabled by ACPI PNP
[    0.793849] system 00:04: ioport range 0x380-0x383 has been reserved
[    0.793853] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.793857] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.793861] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.793864] system 00:04: ioport range 0x1640-0x164f has been reserved
[    0.793869] system 00:04: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.793873] system 00:04: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.793877] system 00:04: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.793881] system 00:04: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.793884] system 00:04: iomem range 0xe0000000-0xefffffff has been reserved
[    0.829920] pci 0000:06:03.0: CardBus bridge, secondary bus 0000:07
[    0.829924] pci 0000:06:03.0:   IO window: 0x002400-0x0024ff
[    0.829931] pci 0000:06:03.0:   IO window: 0x002800-0x0028ff
[    0.829939] pci 0000:06:03.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.829946] pci 0000:06:03.0:   MEM window: 0x38000000-0x3bffffff
[    0.829954] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.829958] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.829966] pci 0000:00:1e.0:   MEM window: 0xb0100000-0xb01fffff
[    0.829972] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000033ffffff
[    0.829992] pci 0000:00:1e.0: setting latency timer to 64
[    0.830004] pci 0000:06:03.0: enabling device (0000 -> 0003)
[    0.830014] pci 0000:06:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.830027] bus: 00 index 0 io port: [0x00-0xffff]
[    0.830030] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.830033] bus: 06 index 0 io port: [0x2000-0x2fff]
[    0.830036] bus: 06 index 1 mmio: [0xb0100000-0xb01fffff]
[    0.830039] bus: 06 index 2 mmio: [0x30000000-0x33ffffff]
[    0.830042] bus: 06 index 3 io port: [0x00-0xffff]
[    0.830045] bus: 06 index 4 mmio: [0x000000-0xffffffff]
[    0.830048] bus: 07 index 0 io port: [0x2400-0x24ff]
[    0.830051] bus: 07 index 1 io port: [0x2800-0x28ff]
[    0.830054] bus: 07 index 2 mmio: [0x30000000-0x33ffffff]
[    0.830057] bus: 07 index 3 mmio: [0x38000000-0x3bffffff]
[    0.830069] NET: Registered protocol family 2
[    0.830213] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.830494] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.830606] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.830720] TCP: Hash tables configured (established 16384 bind 16384)
[    0.830726] TCP reno registered
[    0.830827] NET: Registered protocol family 1
[    0.830984] checking if image is initramfs... it is
[    1.292050] Switched to high resolution mode on CPU 0
[    1.736424] Freeing initrd memory: 7430k freed
[    1.736513] Simple Boot Flag at 0x36 set to 0x1
[    1.736555] cpufreq: No nForce2 chipset.
[    1.736772] audit: initializing netlink socket (disabled)
[    1.736800] type=2000 audit(1253009124.736:1): initialized
[    1.747140] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.748885] VFS: Disk quotas dquot_6.5.1
[    1.748969] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.749782] fuse init (API version 7.10)
[    1.749885] msgmni has been set to 976
[    1.750122] alg: No test for stdrng (krng)
[    1.750139] io scheduler noop registered
[    1.750142] io scheduler anticipatory registered
[    1.750145] io scheduler deadline registered
[    1.750166] io scheduler cfq registered (default)
[    1.750186] pci 0000:00:02.0: Boot video device
[    1.750322] pci 0000:06:08.0: Firmware left e100 interrupts enabled; disabling
[    1.753974] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.753987] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.756127] ACPI: AC Adapter [ADP1] (on-line)
[    1.772635] ACPI: Battery Slot [BAT0] (battery present)
[    1.772730] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.772733] ACPI: Power Button (FF) [PWRF]
[    1.772789] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.774002] ACPI: Lid Switch [LID0]
[    1.774063] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.774074] ACPI: Power Button (CM) [PWRB]
[    2.776168] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.776200] processor ACPI_CPU:00: registered as cooling_device0
[    2.776205] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.780850] thermal LNXTHERM:01: registered as thermal_zone0
[    2.783250] ACPI: Thermal Zone [THRM] (57 C)
[    2.783304] isapnp: Scanning for PnP cards...
[    3.137664] isapnp: No Plug & Play device found
[    3.139055] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.140318] brd: module loaded
[    3.140728] loop: module loaded
[    3.140822] Fixed MDIO Bus: probed
[    3.140830] PPP generic driver version 2.4.2
[    3.140906] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    3.140945] Driver 'sd' needs updating - please use bus_type methods
[    3.140957] Driver 'sr' needs updating - please use bus_type methods
[    3.141051] ata_piix 0000:00:1f.1: version 2.12
[    3.141073] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.141122] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.141246] scsi0 : ata_piix
[    3.141359] scsi1 : ata_piix
[    3.142232] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.142236] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    3.312631] ata1.00: ATA-6: FUJITSU MHV2060AT, 00000096, max UDMA/100
[    3.312635] ata1.00: 117210240 sectors, multi 16: LBA 
[    3.312688] ata1.01: ATAPI: HL-DT-ST DVDRAM GMA-4080N, 0S37, max UDMA/33
[    3.328585] ata1.00: configured for UDMA/100
[    3.344429] ata1.01: configured for UDMA/33
[    3.346793] ata2: port disabled. ignoring.
[    3.346955] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060A 0000 PQ: 0 ANSI: 5
[    3.347079] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    3.347102] sd 0:0:0:0: [sda] Write Protect is off
[    3.347105] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.347139] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.347219] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    3.347237] sd 0:0:0:0: [sda] Write Protect is off
[    3.347240] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.347271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.347276]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    3.487098] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.487158] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.491140] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVDRAM GMA-4080N 0S37 PQ: 0 ANSI: 5
[    3.503006] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.503011] Uniform CD-ROM driver Revision: 3.20
[    3.503121] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    3.503172] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    3.503948] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.503978] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.504020] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.504025] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.504117] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.508029] ehci_hcd 0000:00:1d.7: debug port 1
[    3.508037] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.508056] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0004000
[    3.520011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.520101] usb usb1: configuration #1 chosen from 1 choice
[    3.520137] hub 1-0:1.0: USB hub found
[    3.520154] hub 1-0:1.0: 8 ports detected
[    3.520306] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.520327] uhci_hcd: USB Universal Host Controller Interface driver
[    3.520366] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.520375] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.520379] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.520433] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.520460] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    3.520566] usb usb2: configuration #1 chosen from 1 choice
[    3.520597] hub 2-0:1.0: USB hub found
[    3.520606] hub 2-0:1.0: 2 ports detected
[    3.520705] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.520713] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.520717] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.520773] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.520809] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    3.520898] usb usb3: configuration #1 chosen from 1 choice
[    3.520929] hub 3-0:1.0: USB hub found
[    3.520937] hub 3-0:1.0: 2 ports detected
[    3.521039] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.521047] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.521051] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.521100] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.521137] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    3.521240] usb usb4: configuration #1 chosen from 1 choice
[    3.521275] hub 4-0:1.0: USB hub found
[    3.521283] hub 4-0:1.0: 2 ports detected
[    3.521379] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.521387] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.521391] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.521452] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.521488] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    3.521582] usb usb5: configuration #1 chosen from 1 choice
[    3.521613] hub 5-0:1.0: USB hub found
[    3.521621] hub 5-0:1.0: 2 ports detected
[    3.521793] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.525543] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.528983] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.528990] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.528993] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.528996] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.529000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.529199] mice: PS/2 mouse device common for all mice
[    3.529409] rtc_cmos 00:05: RTC can wake from S4
[    3.529456] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.529492] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.529579] device-mapper: uevent: version 1.0.3
[    3.529735] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.529795] device-mapper: multipath: version 1.0.5 loaded
[    3.529799] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.529900] EISA: Probing bus 0 at eisa.0
[    3.529909] Cannot allocate resource for EISA slot 1
[    3.529915] Cannot allocate resource for EISA slot 2
[    3.529948] EISA: Detected 0 cards.
[    3.530028] cpuidle: using governor ladder
[    3.530089] cpuidle: using governor menu
[    3.530727] TCP cubic registered
[    3.530870] NET: Registered protocol family 10
[    3.531390] lo: Disabled Privacy Extensions
[    3.531783] NET: Registered protocol family 17
[    3.531809] Bluetooth: L2CAP ver 2.11
[    3.531811] Bluetooth: L2CAP socket layer initialized
[    3.531814] Bluetooth: SCO (Voice Link) ver 0.6
[    3.531817] Bluetooth: SCO socket layer initialized
[    3.531856] Bluetooth: RFCOMM socket layer initialized
[    3.531873] Bluetooth: RFCOMM TTY layer initialized
[    3.531875] Bluetooth: RFCOMM ver 1.10
[    3.531931] Using IPI No-Shortcut mode
[    3.532054] registered taskstats version 1
[    3.532181]   Magic number: 9:716:72
[    3.532281] rtc_cmos 00:05: setting system clock to 2009-09-15 10:05:26 UTC (1253009126)
[    3.532285] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.532288] EDD information not available.
[    3.532670] Freeing unused kernel memory: 532k freed
[    3.532818] Write protecting the kernel text: 4116k
[    3.532881] Write protecting the kernel read-only data: 1528k
[    3.734512] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.293975] ohci1394 0000:06:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.343781] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[b0104000-b01047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.351055] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    4.351059] e100: Copyright(c) 1999-2006 Intel Corporation
[    4.355494] e100 0000:06:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.388123] e100 0000:06:08.0: PME# disabled
[    4.396125] e100: eth0: e100_probe: addr 0xb0106000, irq 20, MAC addr 00:01:4a:60:fa:c0
[    4.758218] Marking TSC unstable due to TSC halts in idle
[    4.973775] PM: Starting manual resume from disk
[    4.973781] PM: Resume from partition 8:7
[    4.973783] PM: Checking hibernation image.
[    4.974020] PM: Resume from disk failed.
[    4.976850] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.976854] EXT3-fs: write access will be enabled during recovery.
[    5.288026] Clocksource tsc unstable (delta = -415763415 ns)
[    5.624814] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460301e57dac]
[   10.546421] kjournald starting.  Commit interval 5 seconds
[   10.546442] EXT3-fs: recovery complete.
[   10.550026] EXT3-fs: mounted filesystem with ordered data mode.
[   20.713599] udev: starting version 141
[   22.551360] sony-laptop: Sony Notebook Control Driver v0.6.
[   22.552602] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/SNY5001:00/input/input5
[   22.553881] input: Sony Vaio Jogdial as /devices/virtual/input/input6
[   22.597480] intel_rng: FWH not detected
[   22.637233] Linux agpgart interface v0.103
[   22.694938] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:07/input/input7
[   22.699938] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   22.843547] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   22.862853] yenta_cardbus 0000:06:03.0: CardBus bridge found [104d:818f]
[   22.862883] yenta_cardbus 0000:06:03.0: Enabling burst memory read transactions
[   22.862891] yenta_cardbus 0000:06:03.0: Using CSCINT to route CSC interrupts to PCI
[   22.862894] yenta_cardbus 0000:06:03.0: Routing CardBus interrupts to PCI
[   22.862903] yenta_cardbus 0000:06:03.0: TI: mfunc 0x01001b22, devctl 0x64
[   22.914334] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   22.914690] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   22.918398] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   22.928358] iTCO_vendor_support: vendor-support=0
[   22.931133] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   22.931304] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   22.931317] iTCO_wdt: No card detected
[   23.095068] yenta_cardbus 0000:06:03.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   23.095075] yenta_cardbus 0000:06:03.0: Socket status: 30000811
[   23.095081] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   23.095092] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   23.095097] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   23.095371] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   23.095375] yenta_cardbus 0000:06:03.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   23.096089] tifm_7xx1 0000:06:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   23.132687] tifm_core: MMC/SD card detected in socket 0:0
[   23.343302] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.343375] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.437940] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input8
[   23.481829] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9
[   23.744048] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   23.744065] pcmcia_socket pcmcia_socket0: cs: memory probe 0xb0100000-0xb01fffff: excluding 0xb0100000-0xb010ffff
[   23.756284] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   23.838449] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   23.840880] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   23.841911] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   23.842764] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   23.843831] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   24.502262] eth1: Atmel at76c50x. Version 0.98. MAC 00:06:f4:04:8c:5b
[   24.735299] lp: driver loaded but no devices found
[   24.850935] Adding 176672k swap on /dev/sda7.  Priority:-1 extents:1 across:176672k
[   25.392915] EXT3 FS on sda6, internal journal
[   26.820532] type=1505 audit(1253001949.787:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1965
[   26.820746] type=1505 audit(1253001949.787:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1965
[   26.820830] type=1505 audit(1253001949.787:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1965
[   26.820891] type=1505 audit(1253001949.787:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1965
[   27.030737] type=1505 audit(1253001949.995:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1970
[   27.031068] type=1505 audit(1253001949.995:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1970
[   27.071819] type=1505 audit(1253001950.035:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1974
[   31.191517] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.191522] Bluetooth: BNEP filters: protocol multicast
[   31.336214] Bridge firewalling registered
[   32.580034] ppdev: user-space parallel port driver
[   36.053964] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.055092] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   36.227487] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   36.228391] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   36.290672] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   36.355475] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   36.447689] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   36.509742] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   36.571651] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   36.633924] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   36.696105] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   37.682555] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   41.135191] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.198743] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.261623] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.324134] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.388124] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.450670] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.514538] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.577028] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.639777] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.702119] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.765761] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   41.829670] atmel_cs 0.0: firmware: requesting atmel_at76c502e-wpa.bin
[   47.880130] eth1: no IPv6 routers present
[   60.468544] CPU0 attaching NULL sched-domain.
[   60.484271] CPU0 attaching NULL sched-domain.
[ 4806.317140] CPU0 attaching NULL sched-domain.
[ 4806.325638] CPU0 attaching NULL sched-domain.
[ 6337.478803] CPU0 attaching NULL sched-domain.
[ 6337.478985] CPU0 attaching NULL sched-domain.
[ 8641.077455] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 8641.860912] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[ 9366.303304] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 9368.185797] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[ 9498.296265] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 9499.442041] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[ 9679.572910] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 9679.572926] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[ 9680.918156] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[10807.348059] usb 1-5: new high speed USB device using ehci_hcd and address 2
[10807.483298] usb 1-5: configuration #1 chosen from 1 choice
[10808.136117] Initializing USB Mass Storage driver...
[10808.137740] scsi2 : SCSI emulation for USB Mass Storage devices
[10808.138228] usbcore: registered new interface driver usb-storage
[10808.138233] USB Mass Storage support registered.
[10808.140795] usb-storage: device found at 2
[10808.140800] usb-storage: waiting for device to settle before scanning
[10813.140181] usb-storage: device scan complete
[10813.140785] scsi 2:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
[10813.177590] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[10813.187553] sd 2:0:0:0: [sdb] Write Protect is off
[10813.187560] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[10813.187563] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[10813.189012] sd 2:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[10813.190230] sd 2:0:0:0: [sdb] Write Protect is off
[10813.190237] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[10813.190240] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[10813.190250]  sdb: sdb1
[10813.232859] sd 2:0:0:0: [sdb] Attached SCSI disk
[10813.232961] sd 2:0:0:0: Attached scsi generic sg2 type 0
[10815.613753] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[11733.355167] usb 1-5: USB disconnect, address 2
[19356.198070] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[19365.033523] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[24809.240054] usb 1-1: new high speed USB device using ehci_hcd and address 3
[24809.373448] usb 1-1: configuration #1 chosen from 1 choice
[24809.373692] scsi3 : SCSI emulation for USB Mass Storage devices
[24809.373919] usb-storage: device found at 3
[24809.373922] usb-storage: waiting for device to settle before scanning
[24814.397425] usb-storage: device scan complete
[24814.397985] scsi 3:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
[24814.401208] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[24814.401791] sd 3:0:0:0: [sdb] Write Protect is off
[24814.401797] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[24814.401800] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[24814.403196] sd 3:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[24814.403807] sd 3:0:0:0: [sdb] Write Protect is off
[24814.403813] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[24814.403816] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[24814.403826]  sdb: sdb1
[24814.448371] sd 3:0:0:0: [sdb] Attached SCSI disk
[24814.448482] sd 3:0:0:0: Attached scsi generic sg2 type 0
[24835.666696] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
[25504.135953] usb 1-1: USB disconnect, address 3
[26280.672040] usb 1-3: new high speed USB device using ehci_hcd and address 4
[26280.806481] usb 1-3: configuration #1 chosen from 1 choice
[26280.806863] scsi4 : SCSI emulation for USB Mass Storage devices
[26280.807420] usb-storage: device found at 4
[26280.807423] usb-storage: waiting for device to settle before scanning
[26285.812025] usb-storage: device scan complete
[26285.812642] scsi 4:0:0:0: Direct-Access     WD       3200BEV External 1.75 PQ: 0 ANSI: 4
[26285.815100] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[26285.815594] sd 4:0:0:0: [sdb] Write Protect is off
[26285.815597] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[26285.815601] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[26285.817104] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[26285.817593] sd 4:0:0:0: [sdb] Write Protect is off
[26285.817596] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[26285.817599] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[26285.817605]  sdb: sdb1
[26285.863582] sd 4:0:0:0: [sdb] Attached SCSI disk
[26285.863684] sd 4:0:0:0: Attached scsi generic sg2 type 0
[26287.264487] hfs: write access to a journaled filesystem is not supported, use the force option at your own risk, mounting read-only.
kayo@kayogoro:~$

---

