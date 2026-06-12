---
title: "Long boot time due to Network Manager"
date: 2012-07-29
forum: General Help
---

### Post by ravisghosh on 2012-07-29
Since the time I upgraded to 12.04, the boot time has gone up a bit. It shows around 1 min 15 seconds in bootchart. It is not too bad but I think there is scope for improvement.

Upon running dmesg, I see that my machine attempts many times to connect to network, fails, and finally, gets connected. I do not have any network issue but can't make out why it is taking such long time to connect. It keeps telling me **ADDRCONF(NETDEV_UP): eth0: link is not ready**

I searched and there is mention of this issue but could'nt find a solution. I tried changing cable, but to no avail.

[B]Also, I am attaching the bootchart for a perspective.
[/B]
Any help would be much appreciated.

DMESG output:
```
[    0.434706] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.434709] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    0.434712] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.434715] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.434718] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.434721] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.434724] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.434727] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.434730] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.434734] pci_bus 0000:08: resource 0 [io  0x6000-0x6fff]
[    0.434736] pci_bus 0000:08: resource 1 [mem 0xfc100000-0xfc1fffff]
[    0.434740] pci_bus 0000:08: resource 2 [mem 0xc0100000-0xc02fffff 64bit pref]
[    0.434743] pci_bus 0000:09: resource 1 [mem 0xfc200000-0xfc2fffff]
[    0.434746] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
[    0.434749] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
[    0.434752] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
[    0.434755] pci_bus 0000:09: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.434757] pci_bus 0000:09: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.434760] pci_bus 0000:09: resource 9 [mem 0x000dc000-0x000dffff]
[    0.434763] pci_bus 0000:09: resource 10 [mem 0xc0000000-0xfebfffff]
[    0.434809] NET: Registered protocol family 2
[    0.434955] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.436080] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.439851] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.440372] TCP: Hash tables configured (established 524288 bind 65536)
[    0.440375] TCP reno registered
[    0.440391] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.440433] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.440575] NET: Registered protocol family 1
[    0.440607] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.440628] pci 0000:00:1a.0: PCI INT A disabled
[    0.440646] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.440663] pci 0000:00:1a.1: PCI INT B disabled
[    0.440672] pci 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.440691] pci 0000:00:1a.2: PCI INT C disabled
[    0.440700] pci 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.440739] pci 0000:00:1a.7: PCI INT C disabled
[    0.440761] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.440780] pci 0000:00:1d.0: PCI INT A disabled
[    0.440788] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.440807] pci 0000:00:1d.1: PCI INT B disabled
[    0.440817] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.440836] pci 0000:00:1d.2: PCI INT C disabled
[    0.440845] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.440872] pci 0000:00:1d.7: PCI INT A disabled
[    0.440889] pci 0000:01:00.0: Boot video device
[    0.441065] PCI: CLS 64 bytes, default 64
[    0.441068] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.441071] Placing 64MB software IO TLB between ffff8800b9aa1000 - ffff8800bdaa1000
[    0.441073] software IO TLB at phys 0xb9aa1000 - 0xbdaa1000
[    0.441084] Simple Boot Flag at 0x36 set to 0x1
[    0.441440] audit: initializing netlink socket (disabled)
[    0.441449] type=2000 audit(1343602057.436:1): initialized
[    0.473796] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.497731] VFS: Disk quotas dquot_6.5.2
[    0.497791] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.498290] fuse init (API version 7.17)
[    0.498383] msgmni has been set to 7833
[    0.498747] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.498775] io scheduler noop registered
[    0.498777] io scheduler deadline registered
[    0.498810] io scheduler cfq registered (default)
[    0.498923] pcieport 0000:00:01.0: setting latency timer to 64
[    0.498954] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.499001] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.499052] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.499125] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.499176] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.499250] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.499300] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.499376] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.499426] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    0.499518] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.499542] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.499594] intel_idle: MWAIT substates: 0x3122220
[    0.499596] intel_idle: does not run on family 6 model 23
[    0.600027] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.700033] ACPI: AC Adapter [ADP1] (on-line)
[    0.700097] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.700101] ACPI: Power Button [PWRB]
[    0.700140] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.700143] ACPI: Sleep Button [SLPB]
[    0.700190] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.701589] ACPI: Lid Switch [LID0]
[    0.701633] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.701636] ACPI: Power Button [PWRF]
[    0.707081] Monitor-Mwait will be used to enter C-1 state
[    0.707119] Monitor-Mwait will be used to enter C-2 state
[    0.707152] Monitor-Mwait will be used to enter C-3 state
[    0.707162] Marking TSC unstable due to TSC halts in idle
[    0.707175] ACPI: acpi_idle registered with cpuidle
[    0.715578] thermal LNXTHERM:00: registered as thermal_zone0
[    0.715581] ACPI: Thermal Zone [TZ00] (44 C)
[    0.717040] thermal LNXTHERM:01: registered as thermal_zone1
[    0.717042] ACPI: Thermal Zone [TZ01] (34 C)
[    0.718540] thermal LNXTHERM:02: registered as thermal_zone2
[    0.718542] ACPI: Thermal Zone [TZ02] (51 C)
[    0.718563] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.718571] ACPI: Battery Slot [BAT0] (battery present)
[    0.718595] ERST: Table is not found!
[    0.718596] GHES: HEST is not enabled!
[    0.718669] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.732880] ACPI: Battery Slot [BAT0] (battery present)
[    0.880348] Linux agpgart interface v0.103
[    0.881925] brd: module loaded
[    0.882702] loop: module loaded
[    0.882823] ahci 0000:00:1f.2: version 3.0
[    0.882835] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.882884] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    0.882953] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    0.882956] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ccc sxs 
[    0.882961] ahci 0000:00:1f.2: setting latency timer to 64
[    0.883608] scsi0 : ahci
[    0.883699] scsi1 : ahci
[    0.883772] scsi2 : ahci
[    0.883843] scsi3 : ahci
[    0.883916] scsi4 : ahci
[    0.883987] scsi5 : ahci
[    0.884050] ata1: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 45
[    0.884054] ata2: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 45
[    0.884056] ata3: DUMMY
[    0.884057] ata4: DUMMY
[    0.884058] ata5: DUMMY
[    0.884061] ata6: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504380 irq 45
[    0.884455] Fixed MDIO Bus: probed
[    0.884475] tun: Universal TUN/TAP device driver, 1.6
[    0.884477] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.884529] PPP generic driver version 2.4.2
[    0.884640] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.884656] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.884670] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.884674] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.884715] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.884746] ehci_hcd 0000:00:1a.7: debug port 1
[    0.888645] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.888661] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfc504800
[    0.904018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.904136] hub 1-0:1.0: USB hub found
[    0.904140] hub 1-0:1.0: 6 ports detected
[    0.904215] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.904229] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.904233] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.904277] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.904303] ehci_hcd 0000:00:1d.7: debug port 1
[    0.908175] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.908190] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504c00
[    0.924016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.924131] hub 2-0:1.0: USB hub found
[    0.924135] hub 2-0:1.0: 6 ports detected
[    0.924209] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.924223] uhci_hcd: USB Universal Host Controller Interface driver
[    0.924238] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.924246] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.924249] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.924289] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.924323] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.924444] hub 3-0:1.0: USB hub found
[    0.924448] hub 3-0:1.0: 2 ports detected
[    0.924521] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.924529] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.924532] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.924569] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.924603] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.924718] hub 4-0:1.0: USB hub found
[    0.924721] hub 4-0:1.0: 2 ports detected
[    0.924784] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.924791] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.924794] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.924835] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.924859] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    0.924979] hub 5-0:1.0: USB hub found
[    0.924983] hub 5-0:1.0: 2 ports detected
[    0.925047] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.925055] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.925058] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.925096] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.925121] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.925232] hub 6-0:1.0: USB hub found
[    0.925236] hub 6-0:1.0: 2 ports detected
[    0.925299] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.925307] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.925310] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.925346] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.925371] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.925485] hub 7-0:1.0: USB hub found
[    0.925488] hub 7-0:1.0: 2 ports detected
[    0.925552] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.925559] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.925563] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.925600] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.925637] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.925752] hub 8-0:1.0: USB hub found
[    0.925756] hub 8-0:1.0: 2 ports detected
[    0.925868] usbcore: registered new interface driver libusual
[    0.925901] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.932888] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.932894] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.933016] mousedev: PS/2 mouse device common for all mice
[    0.933214] rtc_cmos 00:05: RTC can wake from S4
[    0.933323] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.933353] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.933426] device-mapper: uevent: version 1.0.3
[    0.933488] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.933550] cpuidle: using governor ladder
[    0.933631] cpuidle: using governor menu
[    0.933633] EFI Variables Facility v0.08 2004-May-17
[    0.933871] TCP cubic registered
[    0.933964] NET: Registered protocol family 10
[    0.934388] NET: Registered protocol family 17
[    0.934392] Registering the dns_resolver key type
[    0.934570] PM: Hibernation image not present or could not be loaded.
[    0.934580] registered taskstats version 1
[    0.948358] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.952213]   Magic number: 4:756:806
[    0.952332] rtc_cmos 00:05: setting system clock to 2012-07-29 22:47:38 UTC (1343602058)
[    0.957088] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.957090] EDD information not available.
[    1.216103] usb 1-6: new high-speed USB device number 2 using ehci_hcd
[    1.376052] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.380046] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.380102] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.383071] ata1.00: ATA-8: WDC WD3200BJKT-75F4T0, 11.01A11, max UDMA/133
[    1.383076] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.385756] ata1.00: configured for UDMA/133
[    1.385931] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BJKT-7 11.0 PQ: 0 ANSI: 5
[    1.386070] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.386081] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.386118] sd 0:0:0:0: [sda] Write Protect is off
[    1.386121] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.386182] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.393992] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7640S, HD18, max UDMA/100
[    1.407702] ata2.00: configured for UDMA/100
[    1.411111] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7640S HD18 PQ: 0 ANSI: 5
[    1.414087] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.414091] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.414266] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.414331] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.422288] ata6.00: ATA-8: ST9500325AS, 0001SDM1, max UDMA/133
[    1.422292] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.424376] ata6.00: configured for UDMA/133
[    1.424524] scsi 5:0:0:0: Direct-Access     ATA      ST9500325AS      0001 PQ: 0 ANSI: 5
[    1.424684] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    1.424703] sd 5:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.424800] sd 5:0:0:0: [sdb] Write Protect is off
[    1.424803] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.424856] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.435621]  sdb: sdb1
[    1.436080] sd 5:0:0:0: [sdb] Attached SCSI disk
[    1.466536]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
[    1.467274] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.468809] Freeing unused kernel memory: 920k freed
[    1.469026] Write protecting the kernel read-only data: 12288k
[    1.474230] Freeing unused kernel memory: 1616k freed
[    1.478360] Freeing unused kernel memory: 1200k freed
[    1.503979] udevd[131]: starting version 175
[    1.737995] tg3.c:v3.121 (November 2, 2011)
[    1.738166] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.738180] tg3 0000:08:00.0: setting latency timer to 64
[    1.758510] sdhci: Secure Digital Host Controller Interface driver
[    1.758512] sdhci: Copyright(c) Pierre Ossman
[    1.758757] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[    1.758774] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.759806] mmc0: no vmmc regulator found
[    1.769078] Registered led device: mmc0::
[    1.778753] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[    1.778801] firewire_ohci 0000:09:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.785214] tg3 0000:08:00.0: eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:f4:c7:34
[    1.785218] tg3 0000:08:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.785221] tg3 0000:08:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.785224] tg3 0000:08:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.832082] firewire_ohci: Added fw-ohci device 0000:09:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.881194] usb 7-1: new full-speed USB device number 2 using uhci_hcd
[    2.037473] hub 7-1:1.0: USB hub found
[    2.039421] hub 7-1:1.0: 4 ports detected
[    2.336142] firewire_core: created device fw0: GUID 384fc00005198d58, S400
[    2.341426] usb 7-1.2: new low-speed USB device number 3 using uhci_hcd
[    2.353416] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.597441] usb 7-1.3: new low-speed USB device number 4 using uhci_hcd
[COLOR="Red"]**[   19.880542] ADDRCONF(NETDEV_UP): eth0: link is not ready**[/COLOR]
[   19.937869] udevd[371]: starting version 175
[   20.299720] Adding 4200960k swap on /dev/sda5.  Priority:-1 extents:1 across:4200960k 
[   20.371263] lp: driver loaded but no devices found
[   20.398904] wmi: Mapper loaded
[   20.840619] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[   20.848397] acpi device:03: registered as cooling_device2
[   20.848544] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
[   20.848647] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)
[   20.984276] r592 0000:09:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   20.984399] r592: driver successfully loaded
[   21.012114] input: Dell WMI hotkeys as /devices/virtual/input/input6
[   21.022416] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.063385] type=1400 audit(1343582278.606:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=479 comm="apparmor_parser"
[   21.063391] type=1400 audit(1343582278.606:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=643 comm="apparmor_parser"
[   21.063749] type=1400 audit(1343582278.606:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=643 comm="apparmor_parser"
[   21.063760] type=1400 audit(1343582278.606:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=479 comm="apparmor_parser"
[   21.063954] type=1400 audit(1343582278.606:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=643 comm="apparmor_parser"
[   21.063968] type=1400 audit(1343582278.606:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=479 comm="apparmor_parser"
[   21.163293] cfg80211: Calling CRDA to update world regulatory domain
[   21.190474] cfg80211: World regulatory domain updated:
[   21.190477] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   21.190480] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.190483] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.190485] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   21.190488] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.190490] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.271310] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   21.271313] Copyright(c) 2003-2011 Intel Corporation
[   21.271365] iwlwifi 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   21.271374] iwlwifi 0000:04:00.0: setting latency timer to 64
[   21.271398] iwlwifi 0000:04:00.0: pci_resource_len = 0x00002000
[   21.271400] iwlwifi 0000:04:00.0: pci_resource_base = ffffc90000674000
[   21.271402] iwlwifi 0000:04:00.0: HW Revision ID = 0x0
[   21.271483] iwlwifi 0000:04:00.0: irq 46 for MSI/MSI-X
[   21.271523] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   21.271580] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   21.293295] iwlwifi 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   21.293298] iwlwifi 0000:04:00.0: Device SKU: 0Xf0
[   21.293330] iwlwifi 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   21.307321] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   21.307583] Registered led device: phy0-led
[   21.307634] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   21.360127] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   21.360685] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   21.360688] Disabling lock debugging due to kernel taint
[   21.440873] [fglrx] Maximum main memory to use for locked dma buffers: 3759 MBytes.
[   21.441330] [fglrx]   vendor: 1002 device: 9553 count: 1
[   21.442023] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   21.442038] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.442044] pci 0000:01:00.0: setting latency timer to 64
[   21.442327] [fglrx] Kernel PAT support is enabled
[   21.442345] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[   21.549723] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1.2/7-1.2:1.0/input/input7
[   21.549926] generic-usb 0003:045E:00DD.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.1-1.2/input0
[   21.573593] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1.2/7-1.2:1.1/input/input8
[   21.573684] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.1-1.2/input1
[   21.588736] input: DELL DELL USB Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1.3/7-1.3:1.0/input/input9
[   21.588850] generic-usb 0003:046D:C063.0003: input,hidraw2: USB HID v1.10 Mouse [DELL DELL USB Laser Mouse] on usb-0000:00:1d.1-1.3/input0
[   21.588870] usbcore: registered new interface driver usbhid
[   21.588872] usbhid: USB HID core driver
[   21.684703] Linux video capture interface: v2.00
[   21.688094] r852 0000:09:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   21.688176] r852: driver loaded successfully
[   21.712194] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:63ea)
[   21.716871] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input10
[   21.716944] usbcore: registered new interface driver uvcvideo
[   21.716946] USB Video Class driver (1.1.1)
[   21.801833] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   21.801902] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   21.801932] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   21.841054] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   21.882878] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   21.997732] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   21.998021] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   21.998106] snd_hda_intel 0000:01:00.1: irq 48 for MSI/MSI-X
[   21.998135] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[   22.253200] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[   22.253344] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   22.607075] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   22.607078] vesafb: scrolling: redraw
[   22.607081] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   22.609626] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011800000, using 3072k, total 3072k
[   22.609800] Console: switching to colour frame buffer device 128x48
[   22.609818] fb0: VESA VGA frame buffer device
[   22.622650] e4rat-preload: plymouth main process (300) killed by ABRT signal
[   22.634474] e4rat-preload: plymouth-splash main process (949) terminated with status 2
[   22.635440] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   22.794659] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   23.450747] e4rat-preload: failsafe main process (1011) killed by TERM signal
[   23.450966] e4rat-preload: plymouth-log main process (1005) terminated with status 1
[   23.647435] e4rat-preload: plymouth-upstart-bridge main process (1039) terminated with status 1
[   23.680360] type=1400 audit(1343582281.226:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1091 comm="apparmor_parser"
[   23.682273] type=1400 audit(1343582281.226:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1090 comm="apparmor_parser"
[   23.683043] type=1400 audit(1343582281.226:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1091 comm="apparmor_parser"
[   23.683254] type=1400 audit(1343582281.226:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1091 comm="apparmor_parser"
[   23.767596] Bluetooth: Core ver 2.16
[   23.767615] NET: Registered protocol family 31
[   23.767617] Bluetooth: HCI device and connection manager initialized
[   23.767620] Bluetooth: HCI socket layer initialized
[   23.767621] Bluetooth: L2CAP socket layer initialized
[   23.767627] Bluetooth: SCO socket layer initialized
[   23.805555] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   23.808611] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   23.890471] Bluetooth: RFCOMM TTY layer initialized
[   23.890477] Bluetooth: RFCOMM socket layer initialized
[   23.890478] Bluetooth: RFCOMM ver 1.11
[   23.917380] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.917383] Bluetooth: BNEP filters: protocol multicast
[   23.925515] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   23.928554] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[COLOR="red"][B][   23.975850] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.976697] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[/B][/COLOR][   24.004182] tg3 0000:08:00.0: irq 49 for MSI/MSI-X
[COLOR="red"][B][   24.121185] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.121621] ADDRCONF(NETDEV_UP): eth0: link is not ready
[/B][/COLOR][   24.606869] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[   24.607783] [fglrx] Firegl kernel thread PID: 1335
[   24.610087] [fglrx] Firegl kernel thread PID: 1338
[   24.610419] [fglrx] Firegl kernel thread PID: 1343
[   24.610576] [fglrx] IRQ 50 Enabled
[   26.262207] [fglrx] Gart USWC size:1224 M.
[   26.262210] [fglrx] Gart cacheable size:486 M.
[   26.262215] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   26.262217] [fglrx] Reserved FB block: Unshared offset:fc2b000, size:3d5000 
[   26.262219] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   31.855836] wlan0: authenticate with 00:1b:da:47:62:b5 (try 1)
[   31.858034] wlan0: authenticated
[   31.862617] wlan0: associate with 00:1b:da:47:62:b5 (try 1)
[   31.865047] wlan0: RX AssocResp from 00:1b:da:47:62:b5 (capab=0x411 status=0 aid=1)
[   31.865051] wlan0: associated
[   31.869475] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.592126] wlan0: no IPv6 routers present

```

---

### Post by ravisghosh on 2012-07-29
Of note, I have the following hardware.

Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)

---

### Post by brainwash on 2012-07-29
I guess the gap in your log file (2.597441 -  19.880542) is caused by [ureadahead]("http://manpages.ubuntu.com/manpages/precise/man8/ureadahead.8.html"). The tool is simply doing its job by preloading a bunch of boot files in advance to minimize the access time later.

Try this:
Delete all the pack files which are located in /var/lib/ureadahead to force a retrace of the boot sequence. Now reboot and compare the dmesg log files.

---

### Post by ravisghosh on 2012-07-29
> **brainwash said:**
> I guess the gap in your log file (2.597441 -  19.880542) is caused by [ureadahead]("http://manpages.ubuntu.com/manpages/precise/man8/ureadahead.8.html"). The tool is simply doing its job by preloading a bunch of boot files in advance to minimize the access time later.

Try this:
Delete all the pack files which are located in /var/lib/ureadahead to force a retrace of the boot sequence. Now reboot and compare the dmesg log files.


Thanks for the reply dude. However, i have removed ureadahead and have been using e4rat to see if there is any difference in boot time.

---

### Post by wildmanne39 on 2012-07-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by brainwash on 2012-07-29
> **ravisghosh said:**
> However, i have removed ureadahead and have been using **e4rat** to see if there is any difference in boot time.
Oh, my fault... should have taken a closer look at your log file. :) Can you upload the dmesg log file after booting wihtout the e4rat preload mechanism.

And please fix the image size of your bootchart. You can barely read the text.

---

### Post by ravisghosh on 2012-07-30
> **brainwash said:**
> Oh, my fault... should have taken a closer look at your log file. :) Can you upload the dmesg log file after booting wihtout the e4rat preload mechanism.

And please fix the image size of your bootchart. You can barely read the text.

Thanks buddy. In order to boot without e4rat, I just need to uninstall it, right?

For bootchart, i believe the issue is with the image size that ubuntuforum allows. I uploaded it to GDrive, but it would still require to be downloaded and zoomed in :(

[https://docs.google.com/open?id=0Bxh-vFMLJQByak8tVnp6a0xwVW8](https://docs.google.com/open?id=0Bxh-vFMLJQByak8tVnp6a0xwVW8)

---

### Post by ravisghosh on 2012-07-31
I removed e4rat and here is the bootchart attached. It gives me 1 min. Of note, with e4rat, i was getting around 1:15 min of boot time. That sounds kind of strange.

I uploaded the bootchart log file here - [https://docs.google.com/open?id=0Bxh-vFMLJQByR2VEUTAxWlNaUDg](https://docs.google.com/open?id=0Bxh-vFMLJQByR2VEUTAxWlNaUDg)

I have also attached the dmesg log but that doesn't seem to have all the lines displayed in terminal. Hence, I'm copying the output from terminal here.

> ]
[    0.420359] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.420362] pci_bus 0000:02: resource 1 [mem 0xf6000000-0xf7ffffff]
[    0.420365] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.420369] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.420372] pci_bus 0000:04: resource 1 [mem 0xf8000000-0xf9ffffff]
[    0.420375] pci_bus 0000:04: resource 2 [mem 0xf2000000-0xf3ffffff 64bit pref]
[    0.420379] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.420382] pci_bus 0000:06: resource 1 [mem 0xfa000000-0xfbffffff]
[    0.420385] pci_bus 0000:06: resource 2 [mem 0xf4000000-0xf5ffffff 64bit pref]
[    0.420388] pci_bus 0000:08: resource 0 [io  0x6000-0x6fff]
[    0.420391] pci_bus 0000:08: resource 1 [mem 0xfc100000-0xfc1fffff]
[    0.420394] pci_bus 0000:08: resource 2 [mem 0xc0100000-0xc02fffff 64bit pref]
[    0.420398] pci_bus 0000:09: resource 1 [mem 0xfc200000-0xfc2fffff]
[    0.420401] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7]
[    0.420404] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff]
[    0.420407] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff]
[    0.420410] pci_bus 0000:09: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.420413] pci_bus 0000:09: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.420416] pci_bus 0000:09: resource 9 [mem 0x000dc000-0x000dffff]
[    0.420419] pci_bus 0000:09: resource 10 [mem 0xc0000000-0xfebfffff]
[    0.420507] NET: Registered protocol family 2
[    0.420730] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.422483] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.427767] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.428292] TCP: Hash tables configured (established 524288 bind 65536)
[    0.428295] TCP reno registered
[    0.428306] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.428349] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.428483] NET: Registered protocol family 1
[    0.428515] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.428536] pci 0000:00:1a.0: PCI INT A disabled
[    0.428554] pci 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.428571] pci 0000:00:1a.1: PCI INT B disabled
[    0.428579] pci 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.428599] pci 0000:00:1a.2: PCI INT C disabled
[    0.428609] pci 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.428647] pci 0000:00:1a.7: PCI INT C disabled
[    0.428670] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.428689] pci 0000:00:1d.0: PCI INT A disabled
[    0.428697] pci 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.428715] pci 0000:00:1d.1: PCI INT B disabled
[    0.428725] pci 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.428744] pci 0000:00:1d.2: PCI INT C disabled
[    0.428753] pci 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.428779] pci 0000:00:1d.7: PCI INT A disabled
[    0.428795] pci 0000:01:00.0: Boot video device
[    0.428971] PCI: CLS 64 bytes, default 64
[    0.428974] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.428977] Placing 64MB software IO TLB between ffff8800b9aa1000 - ffff8800bdaa1000
[    0.428979] software IO TLB at phys 0xb9aa1000 - 0xbdaa1000
[    0.428990] Simple Boot Flag at 0x36 set to 0x1
[    0.429357] audit: initializing netlink socket (disabled)
[    0.429366] type=2000 audit(1343782966.424:1): initialized
[    0.461790] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.485731] VFS: Disk quotas dquot_6.5.2
[    0.485790] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.486290] fuse init (API version 7.17)
[    0.486383] msgmni has been set to 7833
[    0.486754] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.486785] io scheduler noop registered
[    0.486787] io scheduler deadline registered
[    0.486820] io scheduler cfq registered (default)
[    0.486932] pcieport 0000:00:01.0: setting latency timer to 64
[    0.486963] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.487011] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.487062] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.487135] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.487186] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.487260] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.487310] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.487386] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.487437] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    0.487528] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.487552] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.487604] intel_idle: MWAIT substates: 0x3122220
[    0.487606] intel_idle: does not run on family 6 model 23
[    0.588028] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.688033] ACPI: AC Adapter [ADP1] (on-line)
[    0.688099] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.688104] ACPI: Power Button [PWRB]
[    0.688144] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.688147] ACPI: Sleep Button [SLPB]
[    0.688189] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    0.689761] ACPI: Lid Switch [LID0]
[    0.689805] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.689808] ACPI: Power Button [PWRF]
[    0.695268] Monitor-Mwait will be used to enter C-1 state
[    0.695295] Monitor-Mwait will be used to enter C-2 state
[    0.695322] Monitor-Mwait will be used to enter C-3 state
[    0.695329] Marking TSC unstable due to TSC halts in idle
[    0.695342] ACPI: acpi_idle registered with cpuidle
[    0.702873] thermal LNXTHERM:00: registered as thermal_zone0
[    0.702875] ACPI: Thermal Zone [TZ00] (57 C)
[    0.704794] thermal LNXTHERM:01: registered as thermal_zone1
[    0.704796] ACPI: Thermal Zone [TZ01] (50 C)
[    0.706256] thermal LNXTHERM:02: registered as thermal_zone2
[    0.706258] ACPI: Thermal Zone [TZ02] (65 C)
[    0.706279] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.706289] ACPI: Battery Slot [BAT0] (battery present)
[    0.706313] ERST: Table is not found!
[    0.706314] GHES: HEST is not enabled!
[    0.706386] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.719360] ACPI: Battery Slot [BAT0] (battery present)
[    0.868354] Linux agpgart interface v0.103
[    0.869956] brd: module loaded
[    0.870737] loop: module loaded
[    0.870855] ahci 0000:00:1f.2: version 3.0
[    0.870867] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.870915] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    0.870985] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    0.870988] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ccc sxs 
[    0.870993] ahci 0000:00:1f.2: setting latency timer to 64
[    0.871639] scsi0 : ahci
[    0.871728] scsi1 : ahci
[    0.871801] scsi2 : ahci
[    0.871874] scsi3 : ahci
[    0.871947] scsi4 : ahci
[    0.872027] scsi5 : ahci
[    0.872078] ata1: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 45
[    0.872081] ata2: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 45
[    0.872083] ata3: DUMMY
[    0.872085] ata4: DUMMY
[    0.872086] ata5: DUMMY
[    0.872088] ata6: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504380 irq 45
[    0.872444] Fixed MDIO Bus: probed
[    0.872464] tun: Universal TUN/TAP device driver, 1.6
[    0.872466] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.872514] PPP generic driver version 2.4.2
[    0.872617] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.872635] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.872649] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.872653] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.872697] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.872729] ehci_hcd 0000:00:1a.7: debug port 1
[    0.876613] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.876628] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfc504800
[    0.892018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.892157] hub 1-0:1.0: USB hub found
[    0.892161] hub 1-0:1.0: 6 ports detected
[    0.892238] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.892252] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.892255] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.892301] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.892327] ehci_hcd 0000:00:1d.7: debug port 1
[    0.896206] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.896220] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504c00
[    0.912016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.912118] hub 2-0:1.0: USB hub found
[    0.912122] hub 2-0:1.0: 6 ports detected
[    0.912197] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.912209] uhci_hcd: USB Universal Host Controller Interface driver
[    0.912224] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.912232] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.912235] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.912280] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.912316] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.912434] hub 3-0:1.0: USB hub found
[    0.912438] hub 3-0:1.0: 2 ports detected
[    0.912501] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.912508] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.912512] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.912554] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.912589] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.912704] hub 4-0:1.0: USB hub found
[    0.912711] hub 4-0:1.0: 2 ports detected
[    0.912773] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.912781] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.912784] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.912826] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.912851] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    0.912968] hub 5-0:1.0: USB hub found
[    0.912971] hub 5-0:1.0: 2 ports detected
[    0.913033] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.913041] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.913044] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.913083] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.913108] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.913222] hub 6-0:1.0: USB hub found
[    0.913225] hub 6-0:1.0: 2 ports detected
[    0.913288] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.913296] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.913299] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.913344] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.913368] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.913482] hub 7-0:1.0: USB hub found
[    0.913485] hub 7-0:1.0: 2 ports detected
[    0.913550] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.913557] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.913560] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.913599] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.913632] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.913744] hub 8-0:1.0: USB hub found
[    0.913748] hub 8-0:1.0: 2 ports detected
[    0.913859] usbcore: registered new interface driver libusual
[    0.913894] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.920995] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.921000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.921128] mousedev: PS/2 mouse device common for all mice
[    0.921321] rtc_cmos 00:05: RTC can wake from S4
[    0.921431] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.921460] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.921531] device-mapper: uevent: version 1.0.3
[    0.921596] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    0.921657] cpuidle: using governor ladder
[    0.921748] cpuidle: using governor menu
[    0.921751] EFI Variables Facility v0.08 2004-May-17
[    0.921974] TCP cubic registered
[    0.922077] NET: Registered protocol family 10
[    0.922498] NET: Registered protocol family 17
[    0.922502] Registering the dns_resolver key type
[    0.922675] PM: Hibernation image not present or could not be loaded.
[    0.922687] registered taskstats version 1
[    0.936409] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.940388]   Magic number: 8:150:2
[    0.940506] rtc_cmos 00:05: setting system clock to 2012-08-01 01:02:48 UTC (1343782968)
[    0.945262] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.945264] EDD information not available.
[    1.204103] usb 1-6: new high-speed USB device number 2 using ehci_hcd
[    1.364055] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.366639] ata1.00: ATA-8: WDC WD3200BJKT-75F4T0, 11.01A11, max UDMA/133
[    1.366642] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.368124] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.368918] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.370198] ata1.00: configured for UDMA/133
[    1.370400] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BJKT-7 11.0 PQ: 0 ANSI: 5
[    1.370525] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.370537] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.370570] sd 0:0:0:0: [sda] Write Protect is off
[    1.370573] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.370605] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.383111] ata2.00: ATAPI: Optiarc DVD+/-RW AD-7640S, HD18, max UDMA/100
[    1.396587] ata2.00: configured for UDMA/100
[    1.400118] scsi 1:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7640S HD18 PQ: 0 ANSI: 5
[    1.403393] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.403397] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.403568] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.403681] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.418931] ata6.00: ATA-8: ST9500325AS, 0001SDM1, max UDMA/133
[    1.418936] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.420989] ata6.00: configured for UDMA/133
[    1.421142] scsi 5:0:0:0: Direct-Access     ATA      ST9500325AS      0001 PQ: 0 ANSI: 5
[    1.421311] sd 5:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.421317] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    1.421354] sd 5:0:0:0: [sdb] Write Protect is off
[    1.421357] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.421414] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.432620]  sdb: sdb1
[    1.433019] sd 5:0:0:0: [sdb] Attached SCSI disk
[    1.448837]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 sda9 >
[    1.449736] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.451227] Freeing unused kernel memory: 920k freed
[    1.451450] Write protecting the kernel read-only data: 12288k
[    1.456508] Freeing unused kernel memory: 1616k freed
[    1.460591] Freeing unused kernel memory: 1200k freed
[    1.486158] udevd[130]: starting version 175
[    1.737536] tg3.c:v3.121 (November 2, 2011)
[    1.737710] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.737828] tg3 0000:08:00.0: setting latency timer to 64
[    1.751099] tg3 0000:08:00.0: eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:f4:c7:34
[    1.751104] tg3 0000:08:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.751107] tg3 0000:08:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.751110] tg3 0000:08:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.755468] sdhci: Secure Digital Host Controller Interface driver
[    1.755470] sdhci: Copyright(c) Pierre Ossman
[    1.755801] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[    1.755818] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.756866] mmc0: no vmmc regulator found
[    1.757888] Registered led device: mmc0::
[    1.760046] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[    1.760074] firewire_ohci 0000:09:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.820085] firewire_ohci: Added fw-ohci device 0000:09:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.880042] usb 7-1: new full-speed USB device number 2 using uhci_hcd
[    2.033487] hub 7-1:1.0: USB hub found
[    2.035420] hub 7-1:1.0: 4 ports detected
[    2.269124] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.320184] firewire_core: created device fw0: GUID 384fc00005198d58, S400
[    2.337441] usb 7-1.2: new low-speed USB device number 3 using uhci_hcd
[    2.597438] usb 7-1.3: new low-speed USB device number 4 using uhci_hcd
[    4.419075] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.534742] Adding 4200960k swap on /dev/sda5.  Priority:-1 extents:1 across:4200960k 
[    4.585582] udevd[530]: starting version 175
[    4.994816] lp: driver loaded but no devices found
[    5.162977] wmi: Mapper loaded
[    5.338238] ACPI Warning: _BQC returned an invalid level (20110623/video-480)
[    5.346044] acpi device:03: registered as cooling_device2
[    5.346149] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5
[    5.346240] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)
[    5.418509] r592 0000:09:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    5.420311] r592: driver successfully loaded
[    5.495357] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    5.734353] cfg80211: Calling CRDA to update world regulatory domain
[    6.034280] input: Dell WMI hotkeys as /devices/virtual/input/input6
[    6.062892] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    6.062895] Disabling lock debugging due to kernel taint
[    6.140069] [fglrx] Maximum main memory to use for locked dma buffers: 3759 MBytes.
[    6.140526] [fglrx]   vendor: 1002 device: 9553 count: 1
[    6.141221] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[    6.141236] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.141242] pci 0000:01:00.0: setting latency timer to 64
[    6.141525] [fglrx] Kernel PAT support is enabled
[    6.141544] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[    6.169401] r852 0000:09:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    6.169489] r852: driver loaded successfully
[    6.338731] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1.2/7-1.2:1.0/input/input7
[    6.338823] generic-usb 0003:045E:00DD.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.1-1.2/input0
[    6.362759] input: Microsoft Comfort Curve Keyboard 2000 as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1.2/7-1.2:1.1/input/input8
[    6.362852] generic-usb 0003:045E:00DD.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Comfort Curve Keyboard 2000] on usb-0000:00:1d.1-1.2/input1
[    6.378077] input: DELL DELL USB Laser Mouse as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1.3/7-1.3:1.0/input/input9
[    6.378465] generic-usb 0003:046D:C063.0003: input,hidraw2: USB HID v1.10 Mouse [DELL DELL USB Laser Mouse] on usb-0000:00:1d.1-1.3/input0
[    6.379372] usbcore: registered new interface driver usbhid
[    6.379375] usbhid: USB HID core driver
[    6.484337] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    6.484340] Copyright(c) 2003-2011 Intel Corporation
[    6.484396] iwlwifi 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.484406] iwlwifi 0000:04:00.0: setting latency timer to 64
[    6.484432] iwlwifi 0000:04:00.0: pci_resource_len = 0x00002000
[    6.484434] iwlwifi 0000:04:00.0: pci_resource_base = ffffc90000674000
[    6.484436] iwlwifi 0000:04:00.0: HW Revision ID = 0x0
[    6.484521] iwlwifi 0000:04:00.0: irq 46 for MSI/MSI-X
[    6.484560] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    6.484616] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[    6.506367] iwlwifi 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[    6.506369] iwlwifi 0000:04:00.0: Device SKU: 0Xf0
[    6.506401] iwlwifi 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    6.582031] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.582364] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    6.582394] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    6.625362] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[    6.668257] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[    6.693912] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[    6.694109] Registered led device: phy0-led
[    6.694140] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    6.740208] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[    6.740213] cfg80211: World regulatory domain updated:
[    6.740214] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.740217] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.740219] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.740222] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.740224] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.740227] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.792491] Linux video capture interface: v2.00
[    6.900694] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:63ea)
[    6.905454] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input11
[    6.905539] usbcore: registered new interface driver uvcvideo
[    6.905541] USB Video Class driver (1.1.1)
[    6.925726] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    6.926002] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.926089] snd_hda_intel 0000:01:00.1: irq 48 for MSI/MSI-X
[    6.926119] snd_hda_intel 0000:01:00.1: setting latency timer to 64
[    6.980095] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
[    6.980174] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    7.006059] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    7.116618] type=1400 audit(1343763174.672:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=779 comm="apparmor_parser"
[    7.116628] type=1400 audit(1343763174.672:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=869 comm="apparmor_parser"
[    7.116975] type=1400 audit(1343763174.672:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=779 comm="apparmor_parser"
[    7.116987] type=1400 audit(1343763174.672:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=869 comm="apparmor_parser"
[    7.117180] type=1400 audit(1343763174.672:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=779 comm="apparmor_parser"
[    7.117193] type=1400 audit(1343763174.672:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=869 comm="apparmor_parser"
[    7.117751] type=1400 audit(1343763174.672:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=777 comm="apparmor_parser"
[    7.118557] type=1400 audit(1343763174.672:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=777 comm="apparmor_parser"
[    7.118764] type=1400 audit(1343763174.672:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=777 comm="apparmor_parser"
[    8.294823] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    8.294825] vesafb: scrolling: redraw
[    8.294828] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    8.297751] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90011800000, using 3072k, total 3072k
[    8.297914] Console: switching to colour frame buffer device 128x48
[    8.297933] fb0: VESA VGA frame buffer device
[    8.472178] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    9.331183] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   10.281114] init: failsafe main process (1031) killed by TERM signal
[   10.636458] type=1400 audit(1343763178.192:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1094 comm="apparmor_parser"
[   11.327416] Bluetooth: Core ver 2.16
[   11.327434] NET: Registered protocol family 31
[   11.327436] Bluetooth: HCI device and connection manager initialized
[   11.327439] Bluetooth: HCI socket layer initialized
[   11.327441] Bluetooth: L2CAP socket layer initialized
[   11.327447] Bluetooth: SCO socket layer initialized
[   11.358770] Bluetooth: RFCOMM TTY layer initialized
[   11.358775] Bluetooth: RFCOMM socket layer initialized
[   11.358777] Bluetooth: RFCOMM ver 1.11
[   11.435314] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.435317] Bluetooth: BNEP filters: protocol multicast
[   12.613073] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   12.616130] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   12.741089] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   12.744156] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   12.792091] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.792732] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.878939] tg3 0000:08:00.0: irq 49 for MSI/MSI-X
[   12.981059] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.981365] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.504479] fglrx_pci 0000:01:00.0: irq 50 for MSI/MSI-X
[   14.505083] [fglrx] Firegl kernel thread PID: 1378
[   14.505146] [fglrx] Firegl kernel thread PID: 1379
[   14.505209] [fglrx] Firegl kernel thread PID: 1380
[   14.505340] [fglrx] IRQ 50 Enabled
[   14.603232] tg3 0000:08:00.0: eth0: Link is up at 100 Mbps, full duplex
[   14.603235] tg3 0000:08:00.0: eth0: Flow control is on for TX and on for RX
[   14.603619] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.985115] [fglrx] Gart USWC size:1224 M.
[   14.985119] [fglrx] Gart cacheable size:486 M.
[   14.985123] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   14.985126] [fglrx] Reserved FB block: Unshared offset:fc2b000, size:3d5000 
[   14.985128] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   21.980057] CE: hpet increased min_delta_ns to 20113 nsec
[   22.942421] wlan0: authenticate with 00:1b:da:47:62:b5 (try 1)
[   22.945677] wlan0: authenticated
[   22.950300] wlan0: associate with 00:1b:da:47:62:b5 (try 1)
[   22.954877] wlan0: RX AssocResp from 00:1b:da:47:62:b5 (capab=0x411 status=0 aid=1)
[   22.954882] wlan0: associated
[   22.960473] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.720041] eth0: no IPv6 routers present
[   33.328030] wlan0: no IPv6 routers present



Much appreciate your help in getting this issue fixed.

---

### Post by brainwash on 2012-07-31
First of all I'm not an expert on how to improve the boot time of a Linux system. Like I stated in a previous post the ~17sec gap in your dmesg log file is the result of a preload mechanism reading data in advance. Disabling it might not be a wise choice, because it could slow down the last phase of the boot process and the initialization of your preferred desktop environment.

Moreover, your bootcharts (hosted via Google Docs) are still not accessible. Looking at your latest dmesg log, do you still suspect that your network devices are slowing down the boot process? May it be due to hardware failure or a software bug.

Well, one last thing you could test is to blacklist the corresponding network modules and load them manually after your system is ready.

---

### Post by ravisghosh on 2012-08-01
> **brainwash said:**
> Well, one last thing you could test is to blacklist the corresponding network modules and load them manually after your system is ready.

That sounds a good idea. I would also blacklist the modules I don't need such as bluetooth.

---

