---
title: "automount doesn't work anymore"
date: 2009-08-16
forum: General Help
---

### Post by cedric_libre on 2009-08-16
Hi,
 I am using Hardy .
 Up to one or two weeks ago, automount worked perfectly for the 2 labelled usb external hard drives, that got mounted according to their label under /media directory at boot time .
 For some strange reason, it doesn't work anymore .
 I just can tell I used a few times gparted, and that I disconnected one of the usb drives to plug it on another PC .
 The two drives are still listed in /dev directory, but I'd like to get them at boot time mounted according to their label .
 Any help would be greatly appreciated
 Thanks

---

### Post by scaramanzia on 2009-08-16
OK. Let's see your kernel trace with dmesg. This way we can check if usb kernel modules are working right.

---

### Post by cedric_libre on 2009-08-17
Hi, 
Thanks for your help ,

here is dmesg output :

 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002fff3000 - 0000000030000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196592
[    0.000000]   HighMem    196592 ->   196592
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196592
[    0.000000] On node 0 totalpages: 196592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7610 checksum 0
[    0.000000] ACPI: RSDP 000F7610, 0014 (r0 VIA694)
[    0.000000] ACPI: RSDT 2FFF3000, 0028 (r1 VIA694 MSI ACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 2FFF3040, 0074 (r1 VIA694 MSI ACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 2FFF30C0, 259F (r1 VIA694 AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 2FFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cfff0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 195057
[    0.000000] Kernel command line: root=UUID=37ba40a3-57bc-47ce-a0f5-42c321947450 ro
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0160e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1195.229 MHz processor.
[   42.052137] Console: colour VGA+ 80x25
[   42.052144] console [tty0] enabled
[   42.055696] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   42.058166] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   42.105017] Memory: 766724k/786368k available (2177k kernel code, 19008k reserved, 1006k data, 368k init, 0k highmem)
[   42.105096] virtual kernel memory layout:
[   42.105099]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   42.105101]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   42.105103]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   42.105105]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   42.105108]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   42.105110]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   42.105112]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   42.105506] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   42.105678] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   42.185702] Calibrating delay using timer specific routine.. 2393.11 BogoMIPS (lpj=4786220)
[   42.185849] Security Framework initialized
[   42.185909] SELinux:  Disabled at boot.
[   42.185991] AppArmor: AppArmor initialized
[   42.186048] Failure registering capabilities with primary security module.
[   42.186116] Mount-cache hash table entries: 512
[   42.186384] Initializing cgroup subsys ns
[   42.186439] Initializing cgroup subsys cpuacct
[   42.186504] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   42.186520] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   42.186576] CPU: L2 Cache: 256K (64 bytes/line)
[   42.186629] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   42.186648] Compat vDSO mapped to ffffe000.
[   42.186717] Checking 'hlt' instruction... OK.
[   42.201802] SMP alternatives: switching to UP code
[   42.203672] Freeing SMP alternatives: 11k freed
[   42.203965] Early unpacking initramfs... done
[   42.826224] ACPI: Core revision 20070126
[   42.826423] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   42.828011] ACPI: setting ELCR to 0800 (from 0e00)
[   42.829866] CPU0: AMD Athlon(tm) Processor stepping 02
[   42.829995] SMP motherboard not detected.
[   42.830046] Local APIC not detected. Using dummy APIC emulation.
[   42.830201] Brought up 1 CPUs
[   42.830299] CPU0 attaching sched-domain:
[   42.830304]  domain 0: span 01
[   42.830307]   groups: 01
[   42.830726] net_namespace: 64 bytes
[   42.830790] Booting paravirtualized kernel on bare hardware
[   42.831625] Time: 14:50:06  Date: 08/17/09
[   42.831736] NET: Registered protocol family 16
[   42.832175] EISA bus registered
[   42.832243] ACPI: bus type pci registered
[   42.863897] PCI: PCI BIOS revision 2.10 entry at 0xfb160, last bus=1
[   42.863952] PCI: Using configuration type 1
[   42.864023] Setting up standard PCI resources
[   42.872545] ACPI: EC: Look up EC in DSDT
[   42.876068] ACPI: Interpreter enabled
[   42.876127] ACPI: (supports S0 S1 S4 S5)
[   42.876334] ACPI: Using PIC for interrupt routing
[   42.881736] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   42.881931] Disabling VIA memory write queue (PCI ID 0305, rev 03): [55] 8d & 1f -> 0d
[   42.882233] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   42.882288] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   42.882846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   42.907037] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
[   42.907785] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   42.908492] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   42.909216] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   42.909912] Linux Plug and Play Support v0.97 (c) Adam Belay
[   42.910025] pnp: PnP ACPI init
[   42.910086] ACPI: bus type pnp registered
[   42.913744] pnp: PnP ACPI: found 11 devices
[   42.913799] ACPI: ACPI bus type pnp unregistered
[   42.913854] PnPBIOS: Disabled by ACPI PNP
[   42.914369] PCI: Using ACPI for IRQ routing
[   42.914423] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   42.957088] NET: Registered protocol family 8
[   42.957140] NET: Registered protocol family 20
[   42.957338] AppArmor: AppArmor Filesystem Enabled
[   42.961065] Time: tsc clocksource has been installed.
[   42.969133] system 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   42.969190] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   42.969246] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   42.969302] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   42.969358] system 00:00: iomem range 0x2fff0000-0x2fffffff could not be reserved
[   42.969421] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   42.969483] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   42.969538] system 00:00: iomem range 0x100000-0x2ffeffff could not be reserved
[   42.969601] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[   42.969665] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   43.000505] PCI: Bridge: 0000:00:01.0
[   43.000558]   IO window: disabled.
[   43.000610]   MEM window: dc000000-ddffffff
[   43.000662]   PREFETCH window: d0000000-d7ffffff
[   43.000732] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   43.000753] NET: Registered protocol family 2
[   43.037187] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   43.037944] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   43.042667] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   43.045103] TCP: Hash tables configured (established 131072 bind 65536)
[   43.045164] TCP reno registered
[   43.057318] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   43.579676]  it is
[   44.226727] Freeing initrd memory: 7921k freed
[   44.228048] audit: initializing netlink socket (disabled)
[   44.228129] audit(1250520607.128:1): initialized
[   44.231995] VFS: Disk quotas dquot_6.5.1
[   44.232193] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   44.232551] io scheduler noop registered
[   44.232603] io scheduler anticipatory registered
[   44.232653] io scheduler deadline registered
[   44.232719] io scheduler cfq registered (default)
[   44.232797] Applying VIA southbridge workaround.
[   44.232851] PCI: VIA PCI bridge detected. Disabling DAC.
[   44.232905] PCI: Disabling Via external APIC routing
[   44.233045] Boot video device is 0000:01:00.0
[   44.233568] isapnp: Scanning for PnP cards...
[   44.587631] isapnp: No Plug & Play device found
[   44.641370] Real Time Clock Driver v1.12ac
[   44.641601] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   44.641879] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   44.642154] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   44.643268] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   44.643964] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   44.645493] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   44.645687] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   44.646032] PNP: No PS/2 controller found. Probing ports directly.
[   44.646506] serio: i8042 KBD port at 0x60,0x64 irq 1
[   44.646564] serio: i8042 AUX port at 0x60,0x64 irq 12
[   44.651780] mice: PS/2 mouse device common for all mice
[   44.652055] EISA: Probing bus 0 at eisa.0
[   44.652132] Cannot allocate resource for EISA slot 4
[   44.652184] Cannot allocate resource for EISA slot 5
[   44.652238] Cannot allocate resource for EISA slot 6
[   44.652299] EISA: Detected 0 cards.
[   44.652351] cpuidle: using governor ladder
[   44.652400] cpuidle: using governor menu
[   44.652727] NET: Registered protocol family 1
[   44.652833] Using IPI No-Shortcut mode
[   44.652942] registered taskstats version 1
[   44.653185]   Magic number: 5:561:839
[   44.653432]   hash matches device ptyu5
[   44.653581] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   44.653635] EDD information not available.
[   44.654584] Freeing unused kernel memory: 368k freed
[   45.027700] fuse init (API version 7.9)
[   45.065357] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   45.065533] ACPI: Processor [CPU0] (supports 2 throttling states)
[   45.098442] device-mapper: uevent: version 1.0.3
[   45.098603] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   45.735780] SCSI subsystem initialized
[   45.838464] libata version 3.00 loaded.
[   45.878544] pata_via 0000:00:07.1: version 0.3.3
[   45.894392] scsi0 : pata_via
[   45.917119] scsi1 : pata_via
[   45.917290] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xc000 irq 14
[   45.917348] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xc008 irq 15
[   46.110317] usbcore: registered new interface driver usbfs
[   46.110424] usbcore: registered new interface driver hub
[   46.128188] ata1.00: ATA-7: MAXTOR STM3160215A, 3.AAD, max UDMA/100
[   46.128259] ata1.00: 312581808 sectors, multi 0: LBA48 
[   46.128686] ata1.01: ATA-6: HDS722580VLAT20, V32OA6EA, max UDMA/100
[   46.128742] ata1.01: 160836480 sectors, multi 0: LBA48 
[   46.128810] ata1.00: limited to UDMA/33 due to 40-wire cable
[   46.128863] ata1.01: limited to UDMA/33 due to 40-wire cable
[   46.129559] usbcore: registered new device driver usb
[   46.155332] USB Universal Host Controller Interface driver v3.0
[   46.195294] ata1.00: configured for UDMA/33
[   46.218758] ata1.01: configured for UDMA/33
[   46.235201] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   46.374317] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM316021 3.AA PQ: 0 ANSI: 5
[   46.374599] scsi 0:0:1:0: Direct-Access     ATA      HDS722580VLAT20  V32O PQ: 0 ANSI: 5
[   46.378562] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   46.378630] PCI: setting IRQ 10 as level-triggered
[   46.378637] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   46.378776] PCI: VIA VLink IRQ fixup for 0000:00:07.2, from 9 to 10
[   46.378858] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   46.379331] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   46.379428] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000c400
[   46.379745] usb usb1: configuration #1 chosen from 1 choice
[   46.379838] hub 1-0:1.0: USB hub found
[   46.379896] hub 1-0:1.0: 2 ports detected
[   46.457992] Floppy drive(s): fd0 is 1.44M
[   46.477689] FDC 0 is a post-1991 82077
[   46.482105] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   46.482260] PCI: VIA VLink IRQ fixup for 0000:00:07.3, from 9 to 10
[   46.482343] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   46.482440] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   46.482529] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000c800
[   46.482799] usb usb2: configuration #1 chosen from 1 choice
[   46.482891] hub 2-0:1.0: USB hub found
[   46.482949] hub 2-0:1.0: 2 ports detected
[   46.586548] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   46.586617] PCI: setting IRQ 11 as level-triggered
[   46.586622] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   46.586771] uhci_hcd 0000:00:08.0: UHCI Host Controller
[   46.586870] uhci_hcd 0000:00:08.0: new USB bus registered, assigned bus number 3
[   46.586962] uhci_hcd 0000:00:08.0: irq 11, io base 0x0000dc00
[   46.587230] usb usb3: configuration #1 chosen from 1 choice
[   46.587323] hub 3-0:1.0: USB hub found
[   46.587382] hub 3-0:1.0: 2 ports detected
[   46.690467] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   46.690538] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   46.690691] uhci_hcd 0000:00:08.1: UHCI Host Controller
[   46.690794] uhci_hcd 0000:00:08.1: new USB bus registered, assigned bus number 4
[   46.690886] uhci_hcd 0000:00:08.1: irq 10, io base 0x0000e000
[   46.691144] usb usb4: configuration #1 chosen from 1 choice
[   46.691237] hub 4-0:1.0: USB hub found
[   46.691295] hub 4-0:1.0: 2 ports detected
[   46.794569] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   46.794639] ACPI: PCI Interrupt 0000:00:08.2[C] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   46.794795] ehci_hcd 0000:00:08.2: EHCI Host Controller
[   46.794901] ehci_hcd 0000:00:08.2: new USB bus registered, assigned bus number 5
[   46.795034] ehci_hcd 0000:00:08.2: irq 11, io mem 0xdf114000
[   46.849602] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   46.861525] ehci_hcd 0000:00:08.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   46.861881] usb usb5: configuration #1 chosen from 1 choice
[   46.861989] hub 5-0:1.0: USB hub found
[   46.862051] hub 5-0:1.0: 4 ports detected
[   46.965818] 8139cp 0000:00:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   46.965897] 8139cp 0000:00:0a.0: Try the "8139too" driver instead.
[   46.973679] 8139too Fast Ethernet driver 0.9.28
[   46.973860] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   46.974615] eth0: RealTek RTL8139 at 0xe800, 00:08:a1:88:10:f8, IRQ 11
[   46.974673] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   47.035103] usb 1-2: configuration #1 chosen from 1 choice
[   47.537096] Driver 'sd' needs updating - please use bus_type methods
[   47.537334] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   47.537416] sd 0:0:0:0: [sda] Write Protect is off
[   47.537470] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.537504] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.537656] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   47.538503] sd 0:0:0:0: [sda] Write Protect is off
[   47.538563] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   47.538628] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.538697]  sda: sda1 sda2 < sda5 > sda3
[   47.597305] sd 0:0:0:0: [sda] Attached SCSI disk
[   47.597512] sd 0:0:1:0: [sdb] 160836480 512-byte hardware sectors (82348 MB)
[   47.597591] sd 0:0:1:0: [sdb] Write Protect is off
[   47.597647] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   47.597680] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.597824] sd 0:0:1:0: [sdb] 160836480 512-byte hardware sectors (82348 MB)
[   47.597896] sd 0:0:1:0: [sdb] Write Protect is off
[   47.597949] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   47.597979] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   47.598047]  sdb: sdb1 sdb2 sdb3
[   47.609996] sd 0:0:1:0: [sdb] Attached SCSI disk
[   47.633832] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   47.633932] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   48.048413] usb 5-2: new high speed USB device using ehci_hcd and address 2
[   48.181679] usb 5-2: configuration #1 chosen from 1 choice
[   48.421863] usb 5-3: new high speed USB device using ehci_hcd and address 3
[   48.573021] usb 5-3: configuration #1 chosen from 1 choice
[   48.575194] usbcore: registered new interface driver hiddev
[   48.589756] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0/input/input1
[   48.600250] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:07.2-2
[   48.631123] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.1/input/input2
[   48.656012] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:07.2-2
[   48.656316] usbcore: registered new interface driver usbhid
[   48.656382] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   48.662622] usbcore: registered new interface driver libusual
[   48.676939] Initializing USB Mass Storage driver...
[   48.707893] scsi2 : SCSI emulation for USB Mass Storage devices
[   48.715875] usb-storage: device found at 2
[   48.715884] usb-storage: waiting for device to settle before scanning
[   48.738444] scsi3 : SCSI emulation for USB Mass Storage devices
[   48.751889] usbcore: registered new interface driver usb-storage
[   48.751981] USB Mass Storage support registered.
[   48.752341] usb-storage: device found at 3
[   48.752346] usb-storage: waiting for device to settle before scanning
[   48.953754] Attempting manual resume
[   48.953821] swsusp: Resume From Partition 8:3
[   48.953824] PM: Checking swsusp image.
[   48.968047] PM: Resume from disk failed.
[   49.042828] kjournald starting.  Commit interval 5 seconds
[   49.042923] EXT3-fs: mounted filesystem with ordered data mode.
[   53.711450] usb-storage: device scan complete
[   53.712042] scsi 2:0:0:0: Direct-Access     TOSHIBA  MK3255GSX        9.03 PQ: 0 ANSI: 2 CCS
[   53.713615] sd 2:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   53.714618] sd 2:0:0:0: [sdc] Write Protect is off
[   53.714683] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   53.714687] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   53.715863] sd 2:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   53.716863] sd 2:0:0:0: [sdc] Write Protect is off
[   53.716925] sd 2:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   53.716929] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[   53.717016]  sdc:<7>usb-storage: device scan complete
[   53.748145] scsi 3:0:0:0: Direct-Access     WDC WD32 00BEVT-00ZAT0         PQ: 0 ANSI: 2 CCS
[   54.074434]  sdc1 sdc2
[   54.074770] sd 2:0:0:0: [sdc] Attached SCSI disk
[   54.074953] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   54.076071] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
[   54.077069] sd 3:0:0:0: [sdd] Write Protect is off
[   54.077132] sd 3:0:0:0: [sdd] Mode Sense: 34 00 00 00
[   54.077137] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[   54.078940] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors (320073 MB)
[   54.079940] sd 3:0:0:0: [sdd] Write Protect is off
[   54.080003] sd 3:0:0:0: [sdd] Mode Sense: 34 00 00 00
[   54.080006] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[   54.080094]  sdd: sdd1 sdd2 sdd3
[   54.366816] sd 3:0:0:0: [sdd] Attached SCSI disk
[   54.366953] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   59.202201] Linux agpgart interface v0.102
[   59.314330] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   59.320070] agpgart: AGP aperture is 64M @ 0xd8000000
[   59.510596] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.583283] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   59.796228] parport_pc: VIA 686A/8231 detected
[   59.796237] parport_pc: probing current configuration
[   59.796261] parport_pc: Current parallel port base: 0x378
[   59.796323] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   59.896663] parport_pc: VIA parallel port: io=0x378, irq=7
[   60.438866] input: Power Button (FF) as /devices/virtual/input/input3
[   60.449037] ACPI: Power Button (FF) [PWRF]
[   60.449332] input: Power Button (CM) as /devices/virtual/input/input4
[   60.460961] ACPI: Power Button (CM) [PWRB]
[   60.461175] input: Sleep Button (CM) as /devices/virtual/input/input5
[   60.472977] ACPI: Sleep Button (CM) [SLPB]
[   62.771037] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   62.851518] phy0: Selected rate control algorithm 'simple'
[   63.118038] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   64.334661] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   64.919271] gameport: CS46xx Gameport is pci0000:00:0c.0/gameport0, speed 890kHz
[   64.921147] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   64.921473] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   69.557020] lp0: using parport0 (interrupt-driven).
[   69.670926] Adding 763076k swap on /dev/sda3.  Priority:-1 extents:1 across:763076k
[   70.142960] EXT3 FS on sda5, internal journal
[   70.686109] kjournald starting.  Commit interval 5 seconds
[   70.686517] EXT3 FS on dm-2, internal journal
[   70.686526] EXT3-fs: mounted filesystem with ordered data mode.
[   70.754351] ReiserFS: sdc2: found reiserfs format "3.6" with standard journal
[   70.754403] ReiserFS: sdc2: using ordered data mode
[   70.785015] ReiserFS: sdc2: journal params: device sdc2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   70.788711] ReiserFS: sdc2: checking transaction log (sdc2)
[   70.877518] ReiserFS: sdc2: Using r5 hash to sort names
[   70.975302] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[   71.767996] ip_tables: (C) 2000-2006 Netfilter Core Team
[   73.102914] No dock devices found.
[   73.748903] powernow: No powernow capabilities detected
[   75.237777] NET: Registered protocol family 10
[   75.238942] lo: Disabled Privacy Extensions
[   76.172681] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   76.172693] apm: overridden by ACPI.
[   76.355163] ppdev: user-space parallel port driver
[   76.597858] audit(1250513440.233:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5258 profile="/usr/sbin/cupsd" namespace="default"
[   77.014316] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   77.014328] vboxdrv: Successfully done.
[   77.014332] vboxdrv: Found 1 processor cores.
[   77.015417] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   77.015425] vboxdrv: Successfully loaded version 3.0.0 (interface 0x000e0000).
[   81.703987] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.745403] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   81.857212] Bluetooth: Core ver 2.11
[   81.861493] NET: Registered protocol family 31
[   81.861504] Bluetooth: HCI device and connection manager initialized
[   81.861514] Bluetooth: HCI socket layer initialized
[   81.906750] Bluetooth: L2CAP ver 2.9
[   81.906761] Bluetooth: L2CAP socket layer initialized
[   82.007969] Bluetooth: RFCOMM socket layer initialized
[   82.008498] Bluetooth: RFCOMM TTY layer initialized
[   82.008506] Bluetooth: RFCOMM ver 1.8
[   84.742671] NET: Registered protocol family 17
[   97.518845] eth0: no IPv6 routers present
[ 2285.464316] SysRq : Emergency Sync
[ 2285.568253] Emergency Sync complete
[ 3541.900857] SysRq : Emergency Sync
[ 3541.902379] Emergency Sync complete

---

### Post by jeffthegodofbiscuits on 2009-08-18
I'm actually experiencing a similar issue. My system sees the USB device within lsusb and when I type dmesg I see that the system recognizes it. Though unlike other people my dmesg info displays no listing on the sdb line.  I have provided the output for lsusb and dmesg below.

lsusb:
Bus 001 Device 006: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive

dmesg:
[ 1540.924021] usb 1-6: new high speed USB device using ehci_hcd and address 6
[ 1541.100000] usb 1-6: configuration #1 chosen from 1 choice
[ 1541.150710] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1541.158708] usb-storage: device found at 6
[ 1541.158713] usb-storage: waiting for device to settle before scanning
[ 1546.156244] usb-storage: device scan complete
[ 1546.156965] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 1546.397580] sd 5:0:0:0: [sdb] 4030464 512-byte hardware sectors: (2.06 GB/1.92 GiB)
[ 1546.398062] sd 5:0:0:0: [sdb] Write Protect is off
[ 1546.398065] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1546.398068] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1546.402202] sd 5:0:0:0: [sdb] 4030464 512-byte hardware sectors: (2.06 GB/1.92 GiB)
[ 1546.402687] sd 5:0:0:0: [sdb] Write Protect is off
[ 1546.402690] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1546.402693] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1546.402700]  sdb:
[ 1546.403601] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 1546.403718] sd 5:0:0:0: Attached scsi generic sg3 type 0

---

