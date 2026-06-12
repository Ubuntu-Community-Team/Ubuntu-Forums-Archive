---
title: "USB wifi not working in Ubuntu 10.04 LTS"
date: 2011-12-27
forum: General Help
---

### Post by vignezh on 2011-12-27
USB wifi not working. I just switched from windows to Ubuntu. Tried the latest version yesterday and the wifi worked automatically without me installing the driver. Since the comp was so slow i installed Ubuntu 10.04 lTS today but the wifi is not showing up. please help as i am new to Linux and have no clue how to install the drivers from my cd. It has a folder called Linux.:confused:

---

### Post by collisionystm on 2011-12-27
> **vignezh said:**
> USB wifi not working. I just switched from windows to Ubuntu. Tried the latest version yesterday and the wifi worked automatically without me installing the driver. Since the comp was so slow i installed Ubuntu 10.04 lTS today but the wifi is not showing up. please help as i am new to Linux and have no clue how to install the drivers from my cd. It has a folder called Linux.:confused:


What model is your usb card

Open a terminal and type

lsusb

post the output

---

### Post by vignezh on 2011-12-27
s

---

### Post by vignezh on 2011-12-27
> **collisionystm said:**
> What model is your usb card

Open a terminal and type

lsusb

post the output

Its a mini-USB adaptor bought on ebay. Worked fine with XP and Ubutu 11.10

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by collisionystm on 2011-12-27
> **vignezh said:**
> Its a mini-USB adaptor bought on ebay. Worked fine with XP and Ubutu 11.10

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I dont see it in there? Can you post the entire output or is that it?

Maybe post the output of dmesg

---

### Post by vignezh on 2011-12-27
> **collisionystm said:**
> I dont see it in there? Can you post the entire output or is that it?

Maybe post the output of dmesg

It is the second one "Realtek semiconductor corp." I am using just one USB connections at the moment and that is the wifi adaptor.

---

### Post by collisionystm on 2011-12-27
> **vignezh said:**
> It is the second one "Realtek semiconductor corp." I am using just one USB connections at the moment and that is the wifi adaptor.

okay well that does not help much, does it?

type

iwconfig

whats the output of that

---

### Post by vignezh on 2011-12-27
dmesg


,locks=none
[    0.170214] vgaarb: loaded
[    0.170535] SCSI subsystem initialized
[    0.170798] libata version 3.00 loaded.
[    0.171102] usbcore: registered new interface driver usbfs
[    0.171135] usbcore: registered new interface driver hub
[    0.171298] usbcore: registered new device driver usb
[    0.171843] ACPI: WMI: Mapper loaded
[    0.171850] PCI: Using ACPI for IRQ routing
[    0.172268] NetLabel: Initializing
[    0.172276] NetLabel:  domain hash size = 128
[    0.172279] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.172309] NetLabel:  unlabeled traffic allowed by default
[    0.172465] Switching to clocksource tsc
[    0.176000] AppArmor: AppArmor Filesystem Enabled
[    0.176000] pnp: PnP ACPI init
[    0.176000] ACPI: bus type pnp registered
[    0.183523] pnp: PnP ACPI: found 15 devices
[    0.183531] ACPI: ACPI bus type pnp unregistered
[    0.183540] PnPBIOS: Disabled by ACPI PNP
[    0.183574] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[    0.183581] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.183586] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.183591] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.183597] system 00:00: iomem range 0x1fff0000-0x1fffffff could not be reserved
[    0.183602] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.183607] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.183613] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.183619] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.183624] system 00:00: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.183630] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.183635] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[    0.183652] system 00:02: ioport range 0xb78-0xb7b has been reserved
[    0.183658] system 00:02: ioport range 0xf78-0xf7b has been reserved
[    0.183662] system 00:02: ioport range 0xa78-0xa7b has been reserved
[    0.183667] system 00:02: ioport range 0xe78-0xe7b has been reserved
[    0.183672] system 00:02: ioport range 0xbbc-0xbbf has been reserved
[    0.183676] system 00:02: ioport range 0xfbc-0xfbf has been reserved
[    0.183681] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.183686] system 00:02: ioport range 0x294-0x297 has been reserved
[    0.218765] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.218771] pci 0000:00:01.0:   IO window: disabled
[    0.218778] pci 0000:00:01.0:   MEM window: 0xdc000000-0xddffffff
[    0.218784] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xd7ffffff
[    0.218793] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.218798] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.218805] pci 0000:00:1e.0:   MEM window: 0xde000000-0xdfffffff
[    0.218812] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x200fffff
[    0.218840] pci 0000:00:1e.0: setting latency timer to 64
[    0.218849] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.218853] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.218858] pci_bus 0000:01: resource 1 mem: [0xdc000000-0xddffffff]
[    0.218862] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]
[    0.218867] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.218871] pci_bus 0000:02: resource 1 mem: [0xde000000-0xdfffffff]
[    0.218875] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x200fffff]
[    0.218879] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.218884] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.218955] NET: Registered protocol family 2
[    0.219139] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.219793] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.220000] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.220359] TCP: Hash tables configured (established 16384 bind 16384)
[    0.220373] TCP reno registered
[    0.220674] NET: Registered protocol family 1
[    0.220779] pci 0000:01:00.0: Boot video device
[    0.221278] cpufreq-nforce2: No nForce2 chipset.
[    0.221342] Scanning for low memory corruption every 60 seconds
[    0.221668] audit: initializing netlink socket (disabled)
[    0.221702] type=2000 audit(1325035854.219:1): initialized
[    0.230082] Trying to unpack rootfs image as initramfs...
[    0.239809] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.246214] VFS: Disk quotas dquot_6.5.2
[    0.246403] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.248166] fuse init (API version 7.13)
[    0.248504] msgmni has been set to 978
[    0.255730] alg: No test for stdrng (krng)
[    0.255990] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.256000] io scheduler noop registered
[    0.256003] io scheduler anticipatory registered
[    0.256007] io scheduler deadline registered
[    0.256146] io scheduler cfq registered (default)
[    0.256400] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.256458] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.256655] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.256664] ACPI: Power Button [PWRB]
[    0.256781] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.256797] ACPI: Sleep Button [SLPB]
[    0.256927] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.256934] ACPI: Power Button [PWRF]
[    0.257062] fan PNP0C0B:00: registered as cooling_device0
[    0.257074] ACPI: Fan [FAN] (on)
[    0.257497] Marking TSC unstable due to TSC halts in idle
[    0.257780] processor LNXCPU:00: registered as cooling_device1
[    0.261714] Switching to clocksource acpi_pm
[    0.261985] thermal LNXTHERM:01: registered as thermal_zone0
[    0.262006] ACPI: Thermal Zone [THRM] (22 C)
[    0.268672] isapnp: Scanning for PnP cards...
[    0.280908] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.281084] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.281307] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.282022] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.282370] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.328958] brd: module loaded
[    0.330433] loop: module loaded
[    0.330735] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.331008] ata_piix 0000:00:1f.1: version 2.13
[    0.331153] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.336291] scsi0 : ata_piix
[    0.340621] scsi1 : ata_piix
[    0.342005] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.342013] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.342820] Fixed MDIO Bus: probed
[    0.342905] PPP generic driver version 2.4.2
[    0.343111] tun: Universal TUN/TAP device driver, 1.6
[    0.343117] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.343428] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.343503]   alloc irq_desc for 19 on node -1
[    0.343507]   alloc kstat_irqs on node -1
[    0.343522] ehci_hcd 0000:02:01.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.343582] ehci_hcd 0000:02:01.2: EHCI Host Controller
[    0.343745] ehci_hcd 0000:02:01.2: new USB bus registered, assigned bus number 1
[    0.364371] ehci_hcd 0000:02:01.2: irq 19, io mem 0xdf003000
[    0.376149] ehci_hcd 0000:02:01.2: USB 2.0 started, EHCI 1.00
[    0.376455] usb usb1: configuration #1 chosen from 1 choice
[    0.376531] hub 1-0:1.0: USB hub found
[    0.376566] hub 1-0:1.0: 3 ports detected
[    0.376713] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.376779]   alloc irq_desc for 17 on node -1
[    0.376783]   alloc kstat_irqs on node -1
[    0.376798] ohci_hcd 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.376838] ohci_hcd 0000:02:01.0: OHCI Host Controller
[    0.376999] ohci_hcd 0000:02:01.0: new USB bus registered, assigned bus number 2
[    0.377069] ohci_hcd 0000:02:01.0: irq 17, io mem 0xdf001000
[    0.492789] usb usb2: configuration #1 chosen from 1 choice
[    0.492888] hub 2-0:1.0: USB hub found
[    0.492921] hub 2-0:1.0: 2 ports detected
[    0.493059]   alloc irq_desc for 18 on node -1
[    0.493064]   alloc kstat_irqs on node -1
[    0.493081] ohci_hcd 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    0.493118] ohci_hcd 0000:02:01.1: OHCI Host Controller
[    0.493287] ohci_hcd 0000:02:01.1: new USB bus registered, assigned bus number 3
[    0.493356] ohci_hcd 0000:02:01.1: irq 18, io mem 0xdf002000
[    0.545091] ata1.00: ATA-6: ST340810A, 5.33, max UDMA/100
[    0.545097] ata1.00: 78165360 sectors, multi 16: LBA 
[    0.578324] ata2.00: ATAPI: HL-DT-STDVD-ROM GDR8162B, 0015, max UDMA/33
[    0.578370] ata2.01: ATAPI: HL-DT-ST GCE-8483B, 1.00, max UDMA/33
[    0.584717] ata1.00: configured for UDMA/100
[    0.592416] ata2.00: configured for UDMA/33
[    0.600581] ata2.01: configured for UDMA/33
[    0.608605] usb usb3: configuration #1 chosen from 1 choice
[    0.608695] hub 3-0:1.0: USB hub found
[    0.608733] hub 3-0:1.0: 1 port detected
[    0.608875] uhci_hcd: USB Universal Host Controller Interface driver
[    0.609008] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.609031] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    0.609037] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    0.609207] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 4
[    0.609258] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000d000
[    0.609602] usb usb4: configuration #1 chosen from 1 choice
[    0.609690] hub 4-0:1.0: USB hub found
[    0.609727] hub 4-0:1.0: 2 ports detected
[    0.609862]   alloc irq_desc for 23 on node -1
[    0.609867]   alloc kstat_irqs on node -1
[    0.609883] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    0.609900] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    0.609907] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    0.610077] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 5
[    0.610141] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000d800
[    0.610429] usb usb5: configuration #1 chosen from 1 choice
[    0.610504] hub 5-0:1.0: USB hub found
[    0.610536] hub 5-0:1.0: 2 ports detected
[    0.610784] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.620877] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.620908] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.621397] mice: PS/2 mouse device common for all mice
[    0.621927] rtc_cmos 00:04: RTC can wake from S4
[    0.622095] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.622140] rtc0: alarms up to one month, 242 bytes nvram
[    0.622463] device-mapper: uevent: version 1.0.3
[    0.622978] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.624936] device-mapper: multipath: version 1.1.0 loaded
[    0.624946] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.670284] EISA: Probing bus 0 at eisa.0
[    0.670311] Cannot allocate resource for EISA slot 4
[    0.670314] Cannot allocate resource for EISA slot 5
[    0.670330] EISA: Detected 0 cards.
[    0.673820] cpuidle: using governor ladder
[    0.673903] cpuidle: using governor menu
[    0.674609] TCP cubic registered
[    0.675004] NET: Registered protocol family 10
[    0.676624] NET: Registered protocol family 17
[    0.676808] Using IPI No-Shortcut mode
[    0.677177] PM: Resume from disk failed.
[    0.677216] registered taskstats version 1
[    0.677536]   Magic number: 7:721:509
[    0.677689] rtc_cmos 00:04: setting system clock to 2011-12-28 01:30:55 UTC (1325035855)
[    0.677697] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.677700] EDD information not available.
[    0.689308] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.939640] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    1.027845] isapnp: No Plug & Play device found
[    1.028327] scsi 0:0:0:0: Direct-Access     ATA      ST340810A        5.33 PQ: 0 ANSI: 5
[    1.028771] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.029408] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.029685] sd 0:0:0:0: [sda] Write Protect is off
[    1.029693] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.029837] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.030573]  sda:
[    1.047345] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8162B 0015 PQ: 0 ANSI: 5
[    1.056513]  sda1 sda2 <sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
[    1.059047] Uniform CD-ROM driver Revision: 3.20
[    1.059400] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.059608] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.060233] scsi 1:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8483B  1.00 PQ: 0 ANSI: 5
[    1.065814] sr1: scsi3-mmc drive: 40x/48x writer cd/rw xa/form2 cdda tray
[    1.066139] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.066388] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.089874]  sda5 >
[    1.091065] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.093757] Freeing initrd memory: 7823k freed
[    1.116306] Freeing unused kernel memory: 668k freed
[    1.118220] Write protecting the kernel text: 4684k
[    1.118259] Write protecting the kernel read-only data: 1844k
[    1.122328] usb 4-2: not running at top speed; connect to a high speed hub
[    1.148552] usb 4-2: configuration #1 chosen from 1 choice
[    1.188600] udev: starting version 151
[    1.709396] Floppy drive(s): fd0 is 1.44M
[    1.735979] FDC 0 is a post-1991 82077
[    1.902250]   alloc irq_desc for 16 on node -1
[    1.902257]   alloc kstat_irqs on node -1
[    1.902273] 3c59x 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.902306] 3c59x: Donald Becker and others.
[    1.902324] 0000:02:00.0: 3Com PCI 3c905B Cyclone 100baseTx at e0862000.
[    2.146693] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   18.791369] Adding 1489912k swap on /dev/sda5.  Priority:-1 extents:1 across:1489912k 
[   18.909846] udev: starting version 151
[   19.136667] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.216699] Linux agpgart interface v0.103
[   19.234995] intel_rng: FWH not detected
[   19.354097] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   19.380393] vga16fb: initializing
[   19.380405] vga16fb: mapped to 0xc00a0000
[   19.380589] fb0: VGA16 VGA frame buffer device
[   19.485196] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xd8000000
[   19.485487] lp: driver loaded but no devices found
[   20.539421] nvidia: module license 'NVIDIA' taints kernel.
[   20.539430] Disabling lock debugging due to kernel taint
[   20.822110] type=1505 audit(1325035875.642:2):  operation="profile_load" pid=480 name="/sbin/dhclient3"
[   20.822827] type=1505 audit(1325035875.642:3):  operation="profile_load" pid=480 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   20.823229] type=1505 audit(1325035875.642:4):  operation="profile_load" pid=480 name="/usr/lib/connman/scripts/dhclient-script"
[   21.565534] parport_pc 00:0a: reported by Plug and Play ACPI
[   21.565660] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   21.578935] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.578954] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   21.582558] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
[   21.620501] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   21.656555] lp0: using parport0 (interrupt-driven).
[   21.862665] ppdev: user-space parallel port driver
[   21.935810] psmouse serio1: ID: 10 00 64
[   21.935892] gameport: NS558 PnP Gameport is pnp00:0d/gameport0, io 0x200, speed 817kHz
[   22.175596] usb 4-2: reset full speed USB device using uhci_hcd and address 2
[   22.333452] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   22.333489] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   22.432743] Console: switching to colour frame buffer device 80x30
[   22.503306] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[   22.503818] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[   22.504540] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   22.505000] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   22.505443] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   22.505888] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   22.506250] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   22.506721] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   22.507150] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   22.507572] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   22.508091] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   22.508568] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   22.508981] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[   22.509415] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   22.509866] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   22.510346] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   22.535698] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   22.561062] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   22.586576] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[   22.612168] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   22.637822] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   22.663954] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   22.690384] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   22.716805] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   22.743215] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192cu'
[   22.841772] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   22.916123] intel8x0_measure_ac97_clock: measured 55143 usecs (2650 samples)
[   22.916130] intel8x0: clocking to 48000
[   23.389442] type=1505 audit(1325035878.210:5):  operation="profile_load" pid=668 name="/usr/share/gdm/guest-session/Xsession"
[   23.444527] type=1505 audit(1325035878.266:6):  operation="profile_replace" pid=671 name="/sbin/dhclient3"
[   23.445337] type=1505 audit(1325035878.266:7):  operation="profile_replace" pid=671 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.445779] type=1505 audit(1325035878.266:8):  operation="profile_replace" pid=671 name="/usr/lib/connman/scripts/dhclient-script"
[   23.655711] type=1505 audit(1325035878.474:9):  operation="profile_load" pid=674 name="/usr/bin/evince"
[   23.707774] type=1505 audit(1325035878.526:10):  operation="profile_load" pid=674 name="/usr/bin/evince-previewer"
[   23.743466] type=1505 audit(1325035878.562:11):  operation="profile_load" pid=674 name="/usr/bin/evince-thumbnailer"
[   23.803971] eth0:  setting full-duplex.
[   24.111024] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192cu; check system log for messages from 'loadndisdriver'
[   24.156456] usbcore: registered new interface driver ndiswrapper
[   26.278800] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   26.278824] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   26.278850] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   34.164067] eth0: no IPv6 routers present
[   45.031313] ISO 9660 Extensions: Microsoft Joliet Level 1
[   45.163345] ISOFS: changing to secondary root
[  137.710374] usbcore: deregistering interface driver ndiswrapper
[  137.713772] ndiswrapper (ntoskernel_exit:2677): object d5524820(2) was not freed, freeing it now
[  137.749847] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[  137.896116] usb 4-2: reset full speed USB device using uhci_hcd and address 2
[  138.055440] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[  138.055466] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[  138.055574] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  138.055590] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  138.055607] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  138.055623] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  138.055638] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  138.055654] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  138.055670] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  138.055686] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  138.055702] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  138.055718] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  138.055734] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  138.055749] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[  138.055765] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  138.055831] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  138.055847] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  138.055868] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  138.055901] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  138.055917] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  138.055932] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[  138.055958] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  138.055984] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  138.056096] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  138.056116] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  138.056131] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[  138.056143] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  138.056155] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  138.056167] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[  138.056174] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192cu'
[  138.062007] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192cu; check system log for messages from 'loadndisdriver'
[  138.062141] usbcore: registered new interface driver ndiswrapper
[ 2350.712366] usb 4-2: USB disconnect, address 2
[ 2350.952098] usb 4-2: new full speed USB device using uhci_hcd and address 3
[ 2351.072108] usb 4-2: device descriptor read/64, error -71
[ 2351.240127] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 2352.936098] usb 4-1: new full speed USB device using uhci_hcd and address 4
[ 2353.074175] usb 4-1: not running at top speed; connect to a high speed hub
[ 2353.102461] usb 4-1: configuration #1 chosen from 1 choice
[ 2353.272109] usb 4-1: reset full speed USB device using uhci_hcd and address 4
[ 2353.500282] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[ 2353.500305] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[ 2353.500427] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 2353.500443] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 2353.500460] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 2353.500477] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 2353.500494] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 2353.500510] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreePort'
[ 2353.500526] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[ 2353.500543] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 2353.500559] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 2353.500575] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 2353.500591] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 2353.500608] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[ 2353.500625] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 2353.500696] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 2353.500713] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 2353.500736] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 2353.500772] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 2353.500788] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 2353.500805] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[ 2353.500834] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 2353.500861] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 2353.500878] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 2353.500894] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 2353.500912] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[ 2353.500925] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 2353.500940] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 2353.500954] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[ 2353.500961] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192cu'
[ 2353.502870] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192cu; check system log for messages from 'loadndisdriver'
vignesh@vignesh-desktop:~$

---

### Post by vignezh on 2011-12-27
> **collisionystm said:**
> okay well that does not help much, does it?

type

iwconfig

whats the output of that

Sorry heres "iwconfig"


lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by collisionystm on 2011-12-27
so you installed ndiswrapper

remove that and reboot your system with the card unplugged. plug it in

post last few lines of dmesg

---

### Post by vignezh on 2011-12-27
> **collisionystm said:**
> so you installed ndiswrapper

remove that and reboot your system with the card unplugged. plug it in

post last few lines of dmesg

Hi I had to remove 3 things in total related to ndiswrapper and i did exactly what you said, heres the last few lines of dmesg


=643 name="/usr/bin/evince-thumbnailer"
[   23.693233] eth0:  setting full-duplex.
[   25.558877] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   25.558903] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   25.558929] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   34.296058] eth0: no IPv6 routers present
[   42.059108] ISO 9660 Extensions: Microsoft Joliet Level 1
[   42.156552] ISOFS: changing to secondary root
[   70.168102] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   70.307276] usb 4-1: not running at top speed; connect to a high speed hub
[   70.337234] usb 4-1: configuration #1 chosen from 1 choice
[   70.441404] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   70.451889] usbcore: registered new interface driver ndiswrapper

---

### Post by collisionystm on 2011-12-27
is there any more information for this usb card?

make, model? anything printed on it?

---

