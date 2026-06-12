---
title: "My Ubuntu instalation crashed!!!"
date: 2011-03-08
forum: General Help
---

### Post by _mOrgoth_ on 2011-03-08
My pc had hardware malfunction; power supply interruption. At this moment it is working stable. My Windows 7 installation is ok but Ubuntu Maverick which I used during crush has malfunction. When I start to boot it looks like this:
[[IMG]http://i1234.photobucket.com/albums/ff401/mOrgoth16/svastara/th_Screanshot.jpg[/IMG]](http://s1234.photobucket.com/albums/ff401/mOrgoth16/svastara/?action=view&current=Screanshot.jpg)
I had to make a foto so you all can see the problem. Please, please, please help cause all my important files are stored on Ubuntu partition..

---

### Post by sanderj on 2011-03-08
First of all, I would do this:

boot a Ubuntu live CD, do not install but run the live environment, and check if your important files are still there on your harddisk / Ubuntu filesystem. If so, copy them to an external harddisk.

---

### Post by _mOrgoth_ on 2011-03-08
So, I tried to approach to ubuntu partition over live cd. Its impossible. I see partition but when tried to approach to it I get this message: 

Unable to mount 89 GB Filesystem
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Then I tried to fix my problem over console. This is **fdisk -l** output:
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19123   153605466    7  HPFS/NTFS
/dev/sdc2           19124       29936    86855422+  83  Linux
/dev/sdc3           29937       30401     3735082    f  W95 Ext'd (LBA)
/dev/sdc5           29937       30401     3735081   82  Linux swap / Solaris

I need partition on /dev/sdc2, so I hit in console:
**fsck /dev/sdc2** and this is the outpoot:

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sdc2
Filesystem mounted or opened exclusively by another program?

Command: **umount /dev/sdc2** produce this:
umount: /dev/sdc2: not mounted

Notting happens and I cant save my files.. Tried also to mount partition over console, so I make dir mount3 in media folder to mount it there.. Hit command:
**mount -t ext4 /dev/sdc2 /media/mount3**
Nothing happens.. Console hangs..

tried **dmesg** and I get this:

[    0.232881] ACPI: bus type pnp registered
[    0.237162] pnp: PnP ACPI: found 13 devices
[    0.237164] ACPI: ACPI bus type pnp unregistered
[    0.237167] PnPBIOS: Disabled by ACPI PNP
[    0.237181] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.237183] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.237186] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.237189] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.237191] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.237194] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.237199] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.237202] system 00:02: [io  0x0200-0x027f] has been reserved
[    0.237204] system 00:02: [io  0x0290-0x030f] has been reserved
[    0.237207] system 00:02: [io  0x0290-0x0297] has been reserved
[    0.237213] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.237218] system 00:0c: [mem 0x000cd200-0x000cffff] has been reserved
[    0.237221] system 00:0c: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.237224] system 00:0c: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.237227] system 00:0c: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.237230] system 00:0c: [mem 0x7fee0000-0x7fefffff] could not be reserved
[    0.237232] system 00:0c: [mem 0xffff0000-0xffffffff] has been reserved
[    0.237235] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.237238] system 00:0c: [mem 0x00100000-0x7fedffff] could not be reserved
[    0.237241] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.237244] system 00:0c: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.237247] system 00:0c: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.237250] system 00:0c: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.237252] system 00:0c: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.237255] system 00:0c: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.273045] Switching to clocksource acpi_pm
[    2.147737] pci 0000:01:0a.0: BAR 6: assigned [mem 0xfdf00000-0xfdf1ffff pref]
[    2.147740] pci 0000:00:09.0: PCI bridge to [bus 01-01]
[    2.147744] pci 0000:00:09.0:   bridge window [io  0xb000-0xbfff]
[    2.147747] pci 0000:00:09.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    2.147750] pci 0000:00:09.0:   bridge window [mem 0xfdf00000-0xfdffffff pref]
[    2.147754] pci 0000:00:0b.0: PCI bridge to [bus 02-02]
[    2.147756] pci 0000:00:0b.0:   bridge window [io  0xa000-0xafff]
[    2.147759] pci 0000:00:0b.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    2.147763] pci 0000:00:0b.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    2.147766] pci 0000:00:0c.0: PCI bridge to [bus 03-03]
[    2.147769] pci 0000:00:0c.0:   bridge window [io  0x9000-0x9fff]
[    2.147772] pci 0000:00:0c.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    2.147775] pci 0000:00:0c.0:   bridge window [mem 0xfda00000-0xfdafffff 64bit pref]
[    2.147779] pci 0000:00:0d.0: PCI bridge to [bus 04-04]
[    2.147781] pci 0000:00:0d.0:   bridge window [io  0x8000-0x8fff]
[    2.147784] pci 0000:00:0d.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    2.147788] pci 0000:00:0d.0:   bridge window [mem 0xfd800000-0xfd8fffff 64bit pref]
[    2.147792] pci 0000:05:00.0: BAR 6: assigned [mem 0xfb000000-0xfb01ffff pref]
[    2.147795] pci 0000:00:0e.0: PCI bridge to [bus 05-05]
[    2.147797] pci 0000:00:0e.0:   bridge window [io  0x7000-0x7fff]
[    2.147800] pci 0000:00:0e.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    2.147803] pci 0000:00:0e.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.147812] pci 0000:00:09.0: setting latency timer to 64
[    2.147817] pci 0000:00:0b.0: setting latency timer to 64
[    2.147822] pci 0000:00:0c.0: setting latency timer to 64
[    2.147827] pci 0000:00:0d.0: setting latency timer to 64
[    2.147832] pci 0000:00:0e.0: setting latency timer to 64
[    2.147835] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    2.147838] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    2.147840] pci_bus 0000:00: resource 6 [mem 0xfe030000-0xffffffff]
[    2.147842] pci_bus 0000:00: resource 7 [mem 0x80000000-0xefffffff]
[    2.147845] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfe02ffff]
[    2.147847] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    2.147850] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    2.147852] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff pref]
[    2.147854] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    2.147857] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
[    2.147859] pci_bus 0000:01: resource 6 [mem 0xfe030000-0xffffffff]
[    2.147862] pci_bus 0000:01: resource 7 [mem 0x80000000-0xefffffff]
[    2.147864] pci_bus 0000:01: resource 8 [mem 0xf0000000-0xfe02ffff]
[    2.147866] pci_bus 0000:02: resource 0 [io  0xa000-0xafff]
[    2.147869] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    2.147871] pci_bus 0000:02: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    2.147874] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
[    2.147876] pci_bus 0000:03: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    2.147879] pci_bus 0000:03: resource 2 [mem 0xfda00000-0xfdafffff 64bit pref]
[    2.147881] pci_bus 0000:04: resource 0 [io  0x8000-0x8fff]
[    2.147883] pci_bus 0000:04: resource 1 [mem 0xfd900000-0xfd9fffff]
[    2.147886] pci_bus 0000:04: resource 2 [mem 0xfd800000-0xfd8fffff 64bit pref]
[    2.147888] pci_bus 0000:05: resource 0 [io  0x7000-0x7fff]
[    2.147891] pci_bus 0000:05: resource 1 [mem 0xf8000000-0xfbffffff]
[    2.147893] pci_bus 0000:05: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    2.147932] NET: Registered protocol family 2
[    2.147994] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    2.147994] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.147994] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    2.147994] TCP: Hash tables configured (established 131072 bind 65536)
[    2.147994] TCP reno registered
[    2.147994] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    2.147994] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    2.147994] NET: Registered protocol family 1
[    2.451848] Freeing initrd memory: 11144k freed
[    3.752021] pci 0000:00:02.1: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    3.752086] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    3.752092] pci 0000:00:0b.0: Found disabled HT MSI Mapping
[    3.752099] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    3.752103] pci 0000:00:0b.0: Linking AER extended capability
[    3.752139] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    3.752144] pci 0000:00:0c.0: Found disabled HT MSI Mapping
[    3.752151] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    3.752154] pci 0000:00:0c.0: Linking AER extended capability
[    3.752193] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    3.752198] pci 0000:00:0d.0: Found disabled HT MSI Mapping
[    3.752205] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    3.752207] pci 0000:00:0d.0: Linking AER extended capability
[    3.752249] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    3.752254] pci 0000:00:0e.0: Found disabled HT MSI Mapping
[    3.752261] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    3.752264] pci 0000:00:0e.0: Linking AER extended capability
[    3.752285] pci 0000:05:00.0: Boot video device
[    3.752288] PCI: CLS 32 bytes, default 64
[    3.752483] cpufreq-nforce2: No nForce2 chipset.
[    3.752510] Scanning for low memory corruption every 60 seconds
[    3.752603] audit: initializing netlink socket (disabled)
[    3.752619] type=2000 audit(1299617762.752:1): initialized
[    3.762254] highmem bounce pool size: 64 pages
[    3.762258] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.763585] VFS: Disk quotas dquot_6.5.2
[    3.763638] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.764175] fuse init (API version 7.14)
[    3.764269] msgmni has been set to 1703
[    3.766848] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.766851] io scheduler noop registered
[    3.766853] io scheduler deadline registered
[    3.766865] io scheduler cfq registered (default)
[    3.766963] pcieport 0000:00:0b.0: setting latency timer to 64
[    3.766979]   alloc irq_desc for 40 on node -1
[    3.766981]   alloc kstat_irqs on node -1
[    3.766988] pcieport 0000:00:0b.0: irq 40 for MSI/MSI-X
[    3.767031] pcieport 0000:00:0c.0: setting latency timer to 64
[    3.767042]   alloc irq_desc for 41 on node -1
[    3.767044]   alloc kstat_irqs on node -1
[    3.767049] pcieport 0000:00:0c.0: irq 41 for MSI/MSI-X
[    3.767090] pcieport 0000:00:0d.0: setting latency timer to 64
[    3.767101]   alloc irq_desc for 42 on node -1
[    3.767103]   alloc kstat_irqs on node -1
[    3.767108] pcieport 0000:00:0d.0: irq 42 for MSI/MSI-X
[    3.767147] pcieport 0000:00:0e.0: setting latency timer to 64
[    3.767158]   alloc irq_desc for 43 on node -1
[    3.767160]   alloc kstat_irqs on node -1
[    3.767164] pcieport 0000:00:0e.0: irq 43 for MSI/MSI-X
[    3.767223] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.767246] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.767418] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    3.767423] ACPI: Power Button [PWRB]
[    3.767478] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.767482] ACPI: Power Button [PWRF]
[    3.767532] ACPI: Fan [FAN] (on)
[    3.767969] ACPI: acpi_idle registered with cpuidle
[    3.771537] thermal LNXTHERM:01: registered as thermal_zone0
[    3.771543] ACPI: Thermal Zone [THRM] (40 C)
[    3.771595] ERST: Table is not found!
[    3.771652] isapnp: Scanning for PnP cards...
[    3.771734] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.771817] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.771901] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.772155] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.773169] brd: module loaded
[    3.773642] loop: module loaded
[    3.773846] pata_acpi 0000:00:06.0: setting latency timer to 64
[    3.774160] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    3.774164]   alloc irq_desc for 23 on node -1
[    3.774166]   alloc kstat_irqs on node -1
[    3.774174] pata_acpi 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    3.774188] pata_acpi 0000:00:07.0: setting latency timer to 64
[    3.774195] pata_acpi 0000:00:07.0: PCI INT A disabled
[    3.774482] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    3.774485]   alloc irq_desc for 22 on node -1
[    3.774486]   alloc kstat_irqs on node -1
[    3.774492] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    3.774506] pata_acpi 0000:00:08.0: setting latency timer to 64
[    3.774512] pata_acpi 0000:00:08.0: PCI INT A disabled
[    3.774817] Fixed MDIO Bus: probed
[    3.774848] PPP generic driver version 2.4.2
[    3.774878] tun: Universal TUN/TAP device driver, 1.6
[    3.774880] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.774948] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.775177] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    3.775179]   alloc irq_desc for 21 on node -1
[    3.775181]   alloc kstat_irqs on node -1
[    3.775186] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    3.775200] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.775202] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.775233] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.775253] ehci_hcd 0000:00:02.1: debug port 1
[    3.775258] ehci_hcd 0000:00:02.1: cache line size of 32 is not supported
[    3.775278] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfeb00000
[    3.784017] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    3.784119] hub 1-0:1.0: USB hub found
[    3.784124] hub 1-0:1.0: 10 ports detected
[    3.784188] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.784417] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    3.784419]   alloc irq_desc for 20 on node -1
[    3.784421]   alloc kstat_irqs on node -1
[    3.784426] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    3.784434] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.784436] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.784465] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    3.784486] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    3.842081] hub 2-0:1.0: USB hub found
[    3.842087] hub 2-0:1.0: 10 ports detected
[    3.842143] uhci_hcd: USB Universal Host Controller Interface driver
[    3.842209] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    3.842211] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    3.842986] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.843048] mice: PS/2 mouse device common for all mice
[    3.843142] rtc_cmos 00:04: RTC can wake from S4
[    3.843175] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    3.843197] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    3.843297] device-mapper: uevent: version 1.0.3
[    3.843396] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    3.843491] device-mapper: multipath: version 1.1.1 loaded
[    3.843493] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.843597] EISA: Probing bus 0 at eisa.0
[    3.843599] EISA: Cannot allocate resource for mainboard
[    3.843602] Cannot allocate resource for EISA slot 1
[    3.843604] Cannot allocate resource for EISA slot 2
[    3.843606] Cannot allocate resource for EISA slot 3
[    3.843608] Cannot allocate resource for EISA slot 4
[    3.843610] Cannot allocate resource for EISA slot 5
[    3.843612] Cannot allocate resource for EISA slot 6
[    3.843614] Cannot allocate resource for EISA slot 7
[    3.843616] Cannot allocate resource for EISA slot 8
[    3.843618] EISA: Detected 0 cards.
[    3.843687] cpuidle: using governor ladder
[    3.843689] cpuidle: using governor menu
[    3.843949] TCP cubic registered
[    3.844077] NET: Registered protocol family 10
[    3.844438] lo: Disabled Privacy Extensions
[    3.844675] NET: Registered protocol family 17
[    3.844704] powernow-k8: Found 1 Dual Core AMD Opteron(tm) Processor 170    (2 cpu cores) (version 2.20.00)
[    3.844712] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    3.844713] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    3.844729] Using IPI No-Shortcut mode
[    3.844797] PM: Resume from disk failed.
[    3.844808] registered taskstats version 1
[    3.844985]   Magic number: 3:594:952
[    3.845009] tty tty9: hash matches
[    3.845066] rtc_cmos 00:04: setting system clock to 2011-03-08 20:56:03 UTC (1299617763)
[    3.845069] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.845070] EDD information not available.
[    3.864237] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    4.124434] isapnp: No Plug & Play device found
[    4.124471] Freeing unused kernel memory: 684k freed
[    4.124899] Write protecting the kernel text: 4932k
[    4.124934] Write protecting the kernel read-only data: 1976k
[    4.143636] udev[81]: starting version 163
[    4.204916] pata_amd 0000:00:06.0: version 0.4.1
[    4.204961] pata_amd 0000:00:06.0: setting latency timer to 64
[    4.220727] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    4.220733]   alloc irq_desc for 18 on node -1
[    4.220735]   alloc kstat_irqs on node -1
[    4.220744] skge 0000:01:0a.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    4.220783] skge: 1.13 addr 0xfdef8000 irq 18 chip Yukon-Lite rev 9
[    4.245423] scsi0 : pata_amd
[    4.245797] skge 0000:01:0a.0: eth0: addr 00:01:29:d2:d9:51
[    4.246046] Linux agpgart interface v0.103
[    4.259578] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    4.259584]   alloc irq_desc for 17 on node -1
[    4.259587]   alloc kstat_irqs on node -1
[    4.259595] firewire_ohci 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    4.259650] scsi1 : pata_amd
[    4.261257] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.261260] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.261335] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    4.261553] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    4.261556] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    4.261560] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.261590] nv_probe: set workaround bit for reversed mac addr
[    4.262787] FDC 0 is a post-1991 82077
[    4.280934] [drm] Initialized drm 1.1.0 20060810
[    4.352027] firewire_ohci: Added fw-ohci device 0000:01:09.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x1
[    4.612273] ata2.00: ATAPI: ASUS    DRW-1604P, 1.18, max UDMA/66
[    4.612300] ata2.01: ATAPI: TSSTcorpDVD-ROM SH-D162C, TS03, max UDMA/33
[    4.612322] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5c0) ACPI=0x1f01f (30:60:0x1f)
[    4.612327] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc5c0) ACPI=0x701f (30:60:0x1f)
[    4.620209] ata2.00: configured for UDMA/66
[    4.624018] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    4.652212] ata2.01: configured for UDMA/33
[    4.658717] scsi 1:0:0:0: CD-ROM            ASUS     DRW-1604P        1.18 PQ: 0 ANSI: 5
[    4.682216] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.682219] Uniform CD-ROM driver Revision: 3.20
[    4.682319] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.682378] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    4.682932] scsi 1:0:1:0: CD-ROM            TSSTcorp DVD-ROM SH-D162C TS03 PQ: 0 ANSI: 5
[    4.683623] sr1: scsi3-mmc drive: 32x/48x cd/rw xa/form2 cdda tray
[    4.683693] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    4.683737] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    4.715050] pci 0000:05:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    4.715056] pci 0000:05:00.0: setting latency timer to 64
[    4.717777] [drm] nouveau 0000:05:00.0: Detected an NV50 generation card (0x092a00a2)
[    4.720773] [drm] Initialized nouveau 0.0.16 20090420 for 0000:05:00.0 on minor 0
[    4.781948] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x3f1 @ 1, addr 00:01:29:d2:d6:8f
[    4.781951] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
[    4.781977] sata_nv 0000:00:07.0: version 3.5
[    4.781992] sata_nv 0000:00:07.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    4.782047] sata_nv 0000:00:07.0: setting latency timer to 64
[    4.782196] scsi2 : sata_nv
[    4.782256] scsi3 : sata_nv
[    4.782424] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 23
[    4.782428] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 23
[    4.782453] sata_nv 0000:00:08.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    4.782501] sata_nv 0000:00:08.0: setting latency timer to 64
[    4.782561] scsi4 : sata_nv
[    4.782693] scsi5 : sata_nv
[    4.782830] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc800 irq 22
[    4.782833] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc808 irq 22
[    4.845093] firewire_core: created device fw0: GUID 000129200003b259, S400
[    4.888079] usbcore: registered new interface driver hiddev
[    4.896596] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
[    4.896700] generic-usb 0003:046D:C041.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:02.0-1/input0
[    4.908116] generic-usb 0003:046D:C041.0002: hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:02.0-1/input1
[    4.908131] usbcore: registered new interface driver usbhid
[    4.908134] usbhid: USB HID core driver
[    5.092074] ata5: SATA link down (SStatus 0 SControl 300)
[    5.164026] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    5.248032] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.288390] ata3.00: ATA-6: HDS722512VLSA80, V33OA6MA, max UDMA/100
[    5.288394] ata3.00: 241254720 sectors, multi 16: LBA48 
[    5.312380] ata3.00: configured for UDMA/100
[    5.312494] scsi 2:0:0:0: Direct-Access     ATA      HDS722512VLSA80  V33O PQ: 0 ANSI: 5
[    5.312652] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    5.312747] sd 2:0:0:0: [sda] 241254720 512-byte logical blocks: (123 GB/115 GiB)
[    5.312793] sd 2:0:0:0: [sda] Write Protect is off
[    5.312796] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.312816] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.312951]  sda: sda1
[    5.339672] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.708025] usb 2-6: new full speed USB device using ohci_hcd and address 4
[    5.780027] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.788723] ata4.00: ATA-8: WDC WD6400AAKS-00A7B0, 01.03B01, max UDMA/133
[    5.788726] ata4.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.804769] ata4.00: configured for UDMA/133
[    5.804884] scsi 3:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-0 01.0 PQ: 0 ANSI: 5
[    5.805042] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    5.805139] sd 3:0:0:0: [sdb] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    5.805183] sd 3:0:0:0: [sdb] Write Protect is off
[    5.805185] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.805205] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.805336]  sdb: sdb1 sdb2
[    5.818405] sd 3:0:0:0: [sdb] Attached SCSI disk
[    6.280030] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.288198] ata6.00: ATA-7: ST3250410AS, 3.AAC, max UDMA/133
[    6.288203] ata6.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.304213] ata6.00: configured for UDMA/133
[    6.304325] scsi 5:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[    6.304454] sd 5:0:0:0: [sdc] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    6.304486] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    6.304558] sd 5:0:0:0: [sdc] Write Protect is off
[    6.304561] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    6.304603] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.304843]  sdc: sdc1 sdc2 sdc3 < sdc5 >
[    6.342800] sd 5:0:0:0: [sdc] Attached SCSI disk
[    6.885036] Btrfs loaded
[    6.890016] xor: automatically using best checksumming function: pIII_sse
[    6.908003]    pIII_sse  :  7210.000 MB/sec
[    6.908005] xor: using function: pIII_sse (7210.000 MB/sec)
[    6.910513] device-mapper: dm-raid45: initialized v0.2594b
[    7.800602] EXT4-fs (sdc2): INFO: recovery required on readonly filesystem
[    7.800607] EXT4-fs (sdc2): write access will be enabled during recovery
[    7.825479] EXT4-fs warning (device sdc2): ext4_clear_journal_err: Filesystem error recorded from previous mount: IO failure
[    7.825484] EXT4-fs warning (device sdc2): ext4_clear_journal_err: Marking fs in need of filesystem check.
[    7.825496] BUG: unable to handle kernel paging request at 01f45000
[    7.825516] IP: [<c036228a>] __percpu_counter_sum+0x2a/0x70
[    7.825535] *pde = 00000000 
[    7.825546] Oops: 0000 [#1] SMP 
[    7.825560] last sysfs file: /sys/devices/pci0000:00/0000:00:08.0/host5/target5:0:0/5:0:0:0/block/sdc/uevent
[    7.825576] Modules linked in: dm_raid45 xor btrfs zlib_deflate crc32c libcrc32c usbhid hid nouveau ttm drm_kms_helper drm firewire_ohci floppy sata_nv firewire_core crc_itu_t skge forcedeth pata_amd agpgart i2c_algo_bit
[    7.825679] 
[    7.825686] Pid: 539, comm: exe Not tainted 2.6.35-22-generic #33-Ubuntu LP NF4 Series/ 
[    7.825716] EIP: 0060:[<c036228a>] EFLAGS: 00010293 CPU: 0
[    7.825736] EIP is at __percpu_counter_sum+0x2a/0x70
[    7.825754] EAX: 00000000 EBX: 00000000 ECX: 01f45000 EDX: 00000000
[    7.825774] ESI: 00000000 EDI: f6af6894 EBP: c134fd6c ESP: c134fd60
[    7.825794]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[    7.825813] Process exe (pid: 539, ti=c134e000 task=f60e58d0 task.ti=c134e000)
[    7.825841] Stack:
[    7.825856]  c11a5200 089688ac 00000000 c134fda0 c02ad8b6 c2492400 c134fd88 c05c6468
[    7.825900] <0> 00000001 c2492400 089688a8 00000000 f6f48af0 c11a5200 f6af6400 c2492400
[    7.825958] <0> c134fdd8 c02ada83 c11a5200 c05e91b5 c0730c54 c073dd3e f6af6400 c134fdd8
[    7.826028] Call Trace:
[    7.826048]  [<c02ad8b6>] ? ext4_commit_super+0xd6/0x1d0
[    7.826069]  [<c05c6468>] ? printk+0x2d/0x35
[    7.826087]  [<c02ada83>] ? ext4_clear_journal_err+0xa3/0xd0
[    7.826108]  [<c02d7ffc>] ? jbd2_journal_load+0x6c/0xd0
[    7.826128]  [<c02ad669>] ? ext4_msg+0x49/0x50
[    7.826147]  [<c02b0cff>] ? ext4_load_journal+0x14f/0x2e0
[    7.826167]  [<c02b219d>] ? ext4_fill_super+0x11fd/0x1a40
[    7.826187]  [<c03585b5>] ? vsnprintf+0xb5/0x430
[    7.826207]  [<c021b552>] ? get_sb_bdev+0x162/0x1a0
[    7.826226]  [<c02b0fa0>] ? ext4_fill_super+0x0/0x1a40
[    7.826245]  [<c02ac1d6>] ? ext4_get_sb+0x26/0x30
[    7.826264]  [<c02b0fa0>] ? ext4_fill_super+0x0/0x1a40
[    7.826284]  [<c021aee4>] ? vfs_kern_mount+0x74/0x1c0
[    7.826304]  [<c022f493>] ? get_fs_type+0x33/0xb0
[    7.826322]  [<c021b08e>] ? do_kern_mount+0x3e/0xe0
[    7.826341]  [<c023260c>] ? do_mount+0x1dc/0x220
[    7.826360]  [<c02326bb>] ? sys_mount+0x6b/0xa0
[    7.826378]  [<c05c90a4>] ? syscall_call+0x7/0xb
[    7.826396] Code: 00 55 89 e5 57 89 c7 56 53 e8 f3 68 26 00 8b 5f 04 b8 ff ff ff ff 8b 77 08 eb 1c 8d b6 00 00 00 00 8b 0c 85 80 56 81 c0 8b 57 14 <8b> 14 0a 89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 6c 93 5d c0 ba 
[    7.826658] EIP: [<c036228a>] __percpu_counter_sum+0x2a/0x70 SS:ESP 0068:c134fd60
[    7.826694] CR2: 0000000001f45000
[    7.826712] ---[ end trace d13d2c51b7a9e71c ]---
[    9.334356] ISO 9660 Extensions: Microsoft Joliet Level 3
[    9.365163] ISO 9660 Extensions: RRIP_1991A
[    9.480618] aufs 2-standalone.tree-35-rcN-20100705
[    9.540363] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   50.979390] Adding 3735076k swap on /dev/sdc5.  Priority:-1 extents:1 across:3735076k 
[   52.402999] udev[1503]: starting version 163
[   57.432649] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   57.432672] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   57.590158] Linux video capture interface: v2.00
[   57.996544] gspca: main v2.9.0 registered
[   58.535886] gspca: probing 046d:092d
[   58.702794] input: spca561 as /devices/pci0000:00/0000:00:02.0/usb2/2-6/input/input4
[   58.702896] gspca: video0 created
[   58.702916] usbcore: registered new interface driver spca561
[   58.702919] spca561: registered
[   60.070831] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0904
[   60.070857] usbcore: registered new interface driver usblp
[   60.080979] skge 0000:01:0a.0: eth0: enabling interface
[   60.086159] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.240488] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   62.240495]   alloc irq_desc for 19 on node -1
[   62.240497]   alloc kstat_irqs on node -1
[   62.240506] EMU10K1_Audigy 0000:01:07.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   62.242722] Audigy2 value: Special config.
[   65.047741] lp: driver loaded but no devices found
[   65.719013] ppdev: user-space parallel port driver
[   70.912016] eth1: no IPv6 routers present
[   72.903268] usb 2-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   74.641785] [drm] nouveau 0000:05:00.0: called without init
[   75.771504] mtrr: base(0xf9000000) is not aligned on a size(0xe00000) boundary
[  163.532158] usb 2-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[ 3424.554720] attempt to access beyond end of device
[ 3424.554725] sdc3: rw=0, want=4, limit=2
[ 3424.554728] EXT4-fs (sdc3): unable to read superblock


Is there any way to approach my files and documents or to fix filesystem????
Please :confused:

---

### Post by _mOrgoth_ on 2011-03-09
**SOLVED!!!!!** :D:D:D:D:D:D
I downloaded and boot SystemRescueCD from USB stick. I went into graphical environment and started gparted. I choosed partition with linux and click on check option. It automatically fixed my file system and Ubuntu boot's normal again!

---

### Post by NiksaVel on 2011-03-09
Neatto!

---

