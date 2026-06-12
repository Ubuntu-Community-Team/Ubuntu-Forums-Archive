---
title: "slow boot stays about 10 seconds on &quot;starting up...&quot; message"
date: 2009-07-06
forum: General Help
---

### Post by BobbyBertrands on 2009-07-06
Hello, I'm kinda new to Ubuntu, I use Ubuntu 9.04. 
My PC sort of hangs for about 10 seconds on the starting up... message just after choosing ubuntu from the grub menu.
I found another post which, at first sight seemed to talk about this : [http://ubuntuforums.org/showthread.php?t=1139546](http://ubuntuforums.org/showthread.php?t=1139546) but apparently is another problem

HEEELP

dmesg: 
```
[    1.400806] TCP: Hash tables configured (established 131072 bind 65536)
[    1.400808] TCP reno registered
[    1.408076] NET: Registered protocol family 1
[    1.408186] checking if image is initramfs... it is
[    2.010504] Freeing initrd memory: 7388k freed
[    2.010540] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    2.010542] Simple Boot Flag at 0x44 set to 0x1
[    2.010698] cpufreq: No nForce2 chipset.
[    2.010824] audit: initializing netlink socket (disabled)
[    2.010840] type=2000 audit(1246895630.008:1): initialized
[    2.018006] highmem bounce pool size: 64 pages
[    2.018011] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.019288] VFS: Disk quotas dquot_6.5.1
[    2.019344] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.019926] fuse init (API version 7.10)
[    2.020004] msgmni has been set to 1671
[    2.020168] alg: No test for stdrng (krng)
[    2.020177] io scheduler noop registered
[    2.020179] io scheduler anticipatory registered
[    2.020181] io scheduler deadline registered
[    2.020193] io scheduler cfq registered (default)
[   10.020007] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   18.020007] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   18.020152] pci 0000:01:00.0: Boot video device
[   18.257479] pcieport-driver 0000:00:01.0: setting latency timer to 64
[   18.257518] pcieport-driver 0000:00:01.0: found MSI capability
[   18.257542] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[   18.257553] pci_express 0000:00:01.0:pcie00: allocate port service
[   18.257566] pci_express 0000:00:01.0:pcie02: allocate port service
[   18.257578] pci_express 0000:00:01.0:pcie03: allocate port service
[   18.257630] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[   18.257681] pcieport-driver 0000:00:1c.0: found MSI capability
[   18.257715] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[   18.257732] pci_express 0000:00:1c.0:pcie00: allocate port service
[   18.257743] pci_express 0000:00:1c.0:pcie02: allocate port service
[   18.257755] pci_express 0000:00:1c.0:pcie03: allocate port service
[   18.257830] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[   18.257880] pcieport-driver 0000:00:1c.1: found MSI capability
[   18.257914] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[   18.257931] pci_express 0000:00:1c.1:pcie00: allocate port service
[   18.257948] pci_express 0000:00:1c.1:pcie02: allocate port service
[   18.257960] pci_express 0000:00:1c.1:pcie03: allocate port service
[   18.258035] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[   18.258086] pcieport-driver 0000:00:1c.2: found MSI capability
[   18.258120] pcieport-driver 0000:00:1c.2: irq 2300 for MSI/MSI-X
[   18.258137] pci_express 0000:00:1c.2:pcie00: allocate port service
[   18.258149] pci_express 0000:00:1c.2:pcie02: allocate port service
[   18.258160] pci_express 0000:00:1c.2:pcie03: allocate port service
[   18.258235] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[   18.258286] pcieport-driver 0000:00:1c.3: found MSI capability
[   18.258320] pcieport-driver 0000:00:1c.3: irq 2299 for MSI/MSI-X
[   18.258336] pci_express 0000:00:1c.3:pcie00: allocate port service
[   18.258348] pci_express 0000:00:1c.3:pcie02: allocate port service
[   18.258360] pci_express 0000:00:1c.3:pcie03: allocate port service
[   18.258436] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[   18.258487] pcieport-driver 0000:00:1c.4: found MSI capability
[   18.258521] pcieport-driver 0000:00:1c.4: irq 2298 for MSI/MSI-X
[   18.258538] pci_express 0000:00:1c.4:pcie00: allocate port service
[   18.258550] pci_express 0000:00:1c.4:pcie02: allocate port service
[   18.258562] pci_express 0000:00:1c.4:pcie03: allocate port service
[   18.258637] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[   18.258688] pcieport-driver 0000:00:1c.5: found MSI capability
[   18.258722] pcieport-driver 0000:00:1c.5: irq 2297 for MSI/MSI-X
[   18.258739] pci_express 0000:00:1c.5:pcie00: allocate port service
[   18.258751] pci_express 0000:00:1c.5:pcie02: allocate port service
[   18.258765] pci_express 0000:00:1c.5:pcie03: allocate port service
[   18.258849] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.259145] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   18.388089] ACPI: AC Adapter [AC] (on-line)
[   18.610049] ACPI: Battery Slot [BAT0] (battery present)
[   18.610127] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[   18.610130] ACPI: Power Button (FF) [PWRF]
[   18.610171] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[   18.610174] ACPI: Power Button (CM) [PWRB]
[   18.610213] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[   18.610295] ACPI: Lid Switch [LID0]
[   18.610335] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[   18.610345] ACPI: Sleep Button (CM) [SLPB]
[   18.657171] fan PNP0C0B:00: registered as cooling_device0
[   18.657177] ACPI: Fan [FAN] (on)
[   18.657971] ACPI: SSDT BFC77C18, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[   18.658533] ACPI: SSDT BFC75618, 0594 (r1  PmRef  Cpu0Cst     3001 INTL 20060912)
[   18.659154] Monitor-Mwait will be used to enter C-1 state
[   18.659157] Monitor-Mwait will be used to enter C-2 state
[   18.659160] Monitor-Mwait will be used to enter C-3 state
[   18.659173] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.659192] processor ACPI_CPU:00: registered as cooling_device1
[   18.659196] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.659682] ACPI: SSDT BFC76E18, 01CF (r1  PmRef    ApIst     3000 INTL 20060912)
[   18.660266] ACPI: SSDT BFC77F18, 008D (r1  PmRef    ApCst     3000 INTL 20060912)
[   18.660981] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   18.661000] processor ACPI_CPU:01: registered as cooling_device2
[   18.661004] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.801063] thermal LNXTHERM:01: registered as thermal_zone0
[   18.828413] ACPI: Thermal Zone [THRM] (66 C)
[   18.828469] isapnp: Scanning for PnP cards...
[   19.184266] isapnp: No Plug & Play device found
[   19.196744] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   19.197748] brd: module loaded
[   19.198050] loop: module loaded
[   19.198108] Fixed MDIO Bus: probed
[   19.198113] PPP generic driver version 2.4.2
[   19.198166] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[   19.198193] Driver 'sd' needs updating - please use bus_type methods
[   19.198202] Driver 'sr' needs updating - please use bus_type methods
[   19.198239] ahci 0000:00:1f.2: version 3.0
[   19.198253] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   19.198292] ahci 0000:00:1f.2: irq 2296 for MSI/MSI-X
[   19.198380] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[   19.198384] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ems 
[   19.198390] ahci 0000:00:1f.2: setting latency timer to 64
[   19.198660] scsi0 : ahci
[   19.198739] scsi1 : ahci
[   19.198789] scsi2 : ahci
[   19.198841] scsi3 : ahci
[   19.198893] scsi4 : ahci
[   19.198942] scsi5 : ahci
[   19.199117] ata1: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304100 irq 2296
[   19.199121] ata2: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304180 irq 2296
[   19.199123] ata3: DUMMY
[   19.199124] ata4: DUMMY
[   19.199127] ata5: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304300 irq 2296
[   19.199130] ata6: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304380 irq 2296
[   19.680016] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.681266] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.681469] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.681664] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
[   19.681667] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   19.681875] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.682077] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.682740] ata1.00: ATA-8: Hitachi HTS543225L9A300, FBEOC44C, max UDMA/100
[   19.682742] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   19.684142] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.684344] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.684347] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   19.684549] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.684752] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   19.684777] ata1.00: configured for UDMA/100
[   20.588015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   20.588858] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.588962] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.589021] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 succeeded
[   20.589023] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   20.589125] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.589226] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.871730] ata2.00: ATA-8: WDC WD2500BEVS-00UST0, 01.01A01, max UDMA/133
[   20.871732] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   20.872892] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.873059] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.873062] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   20.873223] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.873385] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   20.873525] ata2.00: configured for UDMA/133
[   21.776015] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.780810] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.781331] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.781790] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.781792] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   21.782310] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.782770] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.782774] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T50L, SC04, max UDMA/100
[   21.788172] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.788693] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.789218] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.789221] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   21.789738] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.790199] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.790224] ata5.00: configured for UDMA/100
[   22.232017] ata6: SATA link down (SStatus 0 SControl 300)
[   22.248097] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54322 FBEO PQ: 0 ANSI: 5
[   22.248184] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   22.248199] sd 0:0:0:0: [sda] Write Protect is off
[   22.248201] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.248225] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.248281] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   22.248295] sd 0:0:0:0: [sda] Write Protect is off
[   22.248297] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.248320] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.248323]  sda: sda1 sda2 < sda5 sda6 >
[   22.628152] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.628194] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.628261] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-0 01.0 PQ: 0 ANSI: 5
[   22.628336] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   22.628350] sd 1:0:0:0: [sdb] Write Protect is off
[   22.628352] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.628375] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.628422] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   22.628436] sd 1:0:0:0: [sdb] Write Protect is off
[   22.628438] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.628461] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.628464]  sdb: sdb1 sdb2
[   22.673826] sd 1:0:0:0: [sdb] Attached SCSI disk
[   22.673861] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   22.676959] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50L  SC04 PQ: 0 ANSI: 5
[   23.003029] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.003032] Uniform CD-ROM driver Revision: 3.20
[   23.003115] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   23.003148] sr 4:0:0:0: Attached scsi generic sg2 type 5
[   23.003871] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   23.003890] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   23.003905] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   23.003909] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   23.003963] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   23.007872] ehci_hcd 0000:00:1a.7: debug port 1
[   23.007879] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[   23.007893] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xdf304c00
[   23.020009] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[   23.020070] usb usb1: configuration #1 chosen from 1 choice
[   23.020095] hub 1-0:1.0: USB hub found
[   23.020102] hub 1-0:1.0: 4 ports detected
[   23.020198] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   23.020209] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   23.020213] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.020249] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   23.024170] ehci_hcd 0000:00:1d.7: debug port 1
[   23.024177] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   23.024189] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf304800
[   23.040008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   23.040059] usb usb2: configuration #1 chosen from 1 choice
[   23.040084] hub 2-0:1.0: USB hub found
[   23.040090] hub 2-0:1.0: 8 ports detected
[   23.040190] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.040206] uhci_hcd: USB Universal Host Controller Interface driver
[   23.040225] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.040232] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[   23.040236] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   23.040274] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[   23.040310] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000090e0
[   23.040380] usb usb3: configuration #1 chosen from 1 choice
[   23.040404] hub 3-0:1.0: USB hub found
[   23.040411] hub 3-0:1.0: 2 ports detected
[   23.040487] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   23.040493] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[   23.040497] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   23.040538] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[   23.040572] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000090c0
[   23.040643] usb usb4: configuration #1 chosen from 1 choice
[   23.040667] hub 4-0:1.0: USB hub found
[   23.040673] hub 4-0:1.0: 2 ports detected
[   23.040755] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   23.040762] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   23.040765] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.040802] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[   23.040830] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000090a0
[   23.040896] usb usb5: configuration #1 chosen from 1 choice
[   23.040919] hub 5-0:1.0: USB hub found
[   23.040925] hub 5-0:1.0: 2 ports detected
[   23.041010] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   23.041016] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   23.041020] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.041057] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[   23.041091] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00009080
[   23.041160] usb usb6: configuration #1 chosen from 1 choice
[   23.041186] hub 6-0:1.0: USB hub found
[   23.041192] hub 6-0:1.0: 2 ports detected
[   23.041270] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   23.041277] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   23.041280] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.041318] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[   23.041344] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009060
[   23.041413] usb usb7: configuration #1 chosen from 1 choice
[   23.041435] hub 7-0:1.0: USB hub found
[   23.041441] hub 7-0:1.0: 2 ports detected
[   23.041523] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   23.041530] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   23.041533] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.041571] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[   23.041605] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00009040
[   23.041674] usb usb8: configuration #1 chosen from 1 choice
[   23.041698] hub 8-0:1.0: USB hub found
[   23.041704] hub 8-0:1.0: 2 ports detected
[   23.041836] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[   23.092895] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.092900] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.096038] mice: PS/2 mouse device common for all mice
[   23.116071] rtc_cmos 00:03: RTC can wake from S4
[   23.116102] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[   23.116134] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[   23.116192] device-mapper: uevent: version 1.0.3
[   23.116272] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   23.116333] device-mapper: multipath: version 1.0.5 loaded
[   23.116336] device-mapper: multipath round-robin: version 1.0.0 loaded
[   23.116405] EISA: Probing bus 0 at eisa.0
[   23.116412] Cannot allocate resource for EISA slot 1
[   23.116414] Cannot allocate resource for EISA slot 2
[   23.116416] Cannot allocate resource for EISA slot 3
[   23.116418] Cannot allocate resource for EISA slot 4
[   23.116420] Cannot allocate resource for EISA slot 5
[   23.116422] Cannot allocate resource for EISA slot 6
[   23.116425] Cannot allocate resource for EISA slot 7
[   23.116427] Cannot allocate resource for EISA slot 8
[   23.116428] EISA: Detected 0 cards.
[   23.116536] cpuidle: using governor ladder
[   23.116651] cpuidle: using governor menu
[   23.117142] TCP cubic registered
[   23.117236] NET: Registered protocol family 10
[   23.117657] lo: Disabled Privacy Extensions
[   23.117983] NET: Registered protocol family 17
[   23.117998] Bluetooth: L2CAP ver 2.11
[   23.118000] Bluetooth: L2CAP socket layer initialized
[   23.118003] Bluetooth: SCO (Voice Link) ver 0.6
[   23.118005] Bluetooth: SCO socket layer initialized
[   23.118035] Bluetooth: RFCOMM socket layer initialized
[   23.118042] Bluetooth: RFCOMM TTY layer initialized
[   23.118044] Bluetooth: RFCOMM ver 1.10
[   23.118070] Marking TSC unstable due to TSC halts in idle
[   23.118622] Using IPI No-Shortcut mode
[   23.118686] registered taskstats version 1
[   23.118831]   Magic number: 1:386:891
[   23.118919] rtc_cmos 00:03: setting system clock to 2009-07-06 15:54:12 UTC (1246895652)
[   23.118922] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.118924] EDD information not available.
[   23.119193] Freeing unused kernel memory: 532k freed
[   23.119341] Write protecting the kernel text: 4112k
[   23.119398] Write protecting the kernel read-only data: 1524k
[   23.147661] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[   23.376081] usb 2-5: new high speed USB device using ehci_hcd and address 2
[   23.479716] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   23.479736] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   23.479759] r8169 0000:05:00.0: setting latency timer to 64
[   23.479877] r8169 0000:05:00.0: irq 2295 for MSI/MSI-X
[   23.480537] eth0: RTL8168c/8111c at 0xf7c6e000, 00:1e:ec:ea:e7:1c, XID 3c2000c0 IRQ 2295
[   23.499260] ohci1394 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.499270] ohci1394 0000:06:00.0: setting latency timer to 64
[   23.517282] usb 2-5: configuration #1 chosen from 1 choice
[   23.551020] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[da100000-da1007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   23.997161] PM: Starting manual resume from disk
[   23.997164] PM: Resume from partition 8:6
[   23.997166] PM: Checking hibernation image.
[   23.997296] PM: Resume from disk failed.
[   24.020054] usb 8-1: new low speed USB device using uhci_hcd and address 2
[   24.030461] kjournald starting.  Commit interval 5 seconds
[   24.030466] EXT3-fs: mounted filesystem with ordered data mode.
[   24.196737] usb 8-1: configuration #1 chosen from 1 choice
[   24.500552] Clocksource tsc unstable (delta = -131549414 ns)
[   24.908276] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[8a3f0200962e41d9]
[   30.275932] udev: starting version 141
[   30.503615] lis3lv02d: laptop model unknown, using default axes configuration
[   30.515554] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input6
[   30.522458] lis3lv02d driver loaded.
[   30.584225] acpi device:09: registered as cooling_device3
[   30.584523] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/device:08/input/input7
[   30.612598] ACPI: Video Device [EVGA] (multi-head: yes  rom: no  post: no)
[   30.862909] sdhci: Secure Digital Host Controller Interface driver
[   30.862911] sdhci: Copyright(c) Pierre Ossman
[   30.965307] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
[   30.965330] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   30.965498] sdhci-pci 0000:06:00.1: setting latency timer to 64
[   30.965572] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
[   30.965582] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[   30.965600] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   30.965607] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[   30.965615] sdhci-pci 0000:06:00.2: PCI INT A disabled
[   31.085163] Linux agpgart interface v0.103
[   31.148865] leds-hp-disk driver loaded.
[   31.231786] ieee80211_crypt: registered algorithm 'NULL'
[   31.324685] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   31.358128] iTCO_vendor_support: vendor-support=0
[   31.405602] usbcore: registered new interface driver hiddev
[   31.418999] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb8/8-1/8-1:1.0/input/input9
[   31.419320] generic-usb 0003:046D:C00E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.3-1/input0
[   31.419337] usbcore: registered new interface driver usbhid
[   31.419359] usbhid: v2.6:USB HID core driver
[   31.780165] nvidia: module license 'NVIDIA' taints kernel.
[   31.812625] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   31.812639] wl 0000:02:00.0: setting latency timer to 64
[   31.859496] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   31.859634] iTCO_wdt: Found a ICH9M TCO device (Version=2, TCOBASE=0x0460)
[   31.859718] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.901581] ieee80211_crypt: registered algorithm 'TKIP'
[   31.903092] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   31.958839] Linux video capture interface: v2.00
[   32.033209] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.033224] nvidia 0000:01:00.0: setting latency timer to 64
[   32.034140] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   32.056241] uvcvideo: Found UVC 1.00 device HP Webcam (090c:c371)
[   32.064318] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   32.165811] input: HP Webcam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input10
[   32.173381] usbcore: registered new interface driver uvcvideo
[   32.173386] USB Video Class driver (v0.1.0)
[   32.280140] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   32.280151] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   32.280278] HDA Intel 0000:00:1b.0: irq 2294 for MSI/MSI-X
[   32.280319] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   32.611593] lp: driver loaded but no devices found
[   32.718673] Adding 9759416k swap on /dev/sda6.  Priority:-1 extents:1 across:9759416k
[   33.375005] EXT3 FS on sda5, internal journal
[   33.379566] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04751/0xa00000
[   33.497375] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   34.725971] EXT4-fs: barriers enabled
[   34.743681] kjournald2 starting.  Commit interval 5 seconds
[   34.743720] EXT4-fs warning: maximal mount count reached, running e2fsck is recommended
[   34.744041] EXT4 FS on sdb1, internal journal on sdb1:8
[   34.744045] EXT4-fs: delayed allocation enabled
[   34.744048] EXT4-fs: file extents enabled
[   34.744492] EXT4-fs: mballoc enabled
[   34.744495] EXT4-fs: mounted filesystem with ordered data mode.
[   35.096702] type=1505 audit(1246888464.477:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2329
[   35.142526] type=1505 audit(1246888464.521:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2333
[   35.142627] type=1505 audit(1246888464.521:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2333
[   35.142668] type=1505 audit(1246888464.521:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2333
[   35.142705] type=1505 audit(1246888464.521:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2333
[   35.265717] type=1505 audit(1246888464.645:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2338
[   35.265883] type=1505 audit(1246888464.645:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2338
[   35.292214] type=1505 audit(1246888464.673:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2342
[   39.599806] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   39.599809] Bluetooth: BNEP filters: protocol multicast
[   39.639720] Bridge firewalling registered
[   41.127880] ppdev: user-space parallel port driver
[   44.632868] r8169: eth0: link down
[   44.633067] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.588017] eth1: no IPv6 routers present
[   69.421307] CPU0 attaching NULL sched-domain.
[   69.421312] CPU1 attaching NULL sched-domain.
[   69.421386] CPU0 attaching sched-domain:
[   69.421389]  domain 0: span 0-1 level MC
[   69.421391]   groups: 0 1
[   69.421396] CPU1 attaching sched-domain:
[   69.421398]  domain 0: span 0-1 level MC
[   69.421401]   groups: 1 0

```

---

