---
title: "Boot time errors"
date: 2010-01-22
forum: General Help
---

### Post by nishant.singh28 on 2010-01-22
I'm running Karmic 64 bit on my laptop(specs in signature). Whenever I boot, there is an error message for a few seconds and then it disappears. It says something about some inaccessible USB device. The funny part is-all my hardware works fine. No device is inaccessible. I tried cycling the connected USB devices but no change. The error eats up a few extra seconds during boot which is irritating. What is the problem?
P.S.:I have solved the first error in the photo.

---

### Post by erlguta on 2010-01-22
it is possible to be something about one usb microphone?.
I had the same problem, with one microphone that does not was properly supported in ubuntu.

---

### Post by nishant.singh28 on 2010-01-22
Nopes. No mic problems. And it's started recently.

---

### Post by Saiko Berry on 2010-01-22
Is /etc/udev/user.rules empty?

Try updating your system. This was fixed I thought.

---

### Post by nishant.singh28 on 2010-01-22
> **Saiko Berry said:**
> Is /etc/udev/user.rules empty?

Try updating your system. This was fixed I thought.
I said the first error was fixed. The problem is the usb error message.

---

### Post by Saiko Berry on 2010-01-22
Oh, okay, sorry. Post the output of lsusb please.

Edit: It's a kernel issue. What kernel are you running? Its a problem with udev. Sometimes results in not seeing the ubuntu splash.

sudo apt-get update
sudo apt-get upgrade

---

### Post by 00_Spykes on 2010-01-22
It would indeed be handy with some more info about why it doesn't go any further. Gief dmesg output. 

I'm no udev expert but shouldn't the kernel/system boot up unless it can read the root filesystem, or does it halt at any error (mouse/keyboard/other partitions)?

---

### Post by Saiko Berry on 2010-01-22
It has nothing to do with USB to my knowledge. With e verything unplugged it should still give errors. udev still checks for those devices or something. some more feedback from the OP would be appreciative.

---

### Post by nishant.singh28 on 2010-01-22
lsusb:
```
Bus 002 Device 003: ID 0bc2:2300 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63eb Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by nishant.singh28 on 2010-01-22
dmesg
```
[    1.054091] processor LNXCPU:01: registered as cooling_device1
[    1.054094] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.058099] thermal LNXTHERM:01: registered as thermal_zone0
[    1.058105] ACPI: Thermal Zone [TZ00] (56 C)
[    1.059789] thermal LNXTHERM:02: registered as thermal_zone1
[    1.059796] ACPI: Thermal Zone [TZ01] (50 C)
[    1.061405] thermal LNXTHERM:03: registered as thermal_zone2
[    1.061411] ACPI: Thermal Zone [TZ02] (66 C)
[    1.062387] Linux agpgart interface v0.103
[    1.062394] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.063366] brd: module loaded
[    1.063724] loop: module loaded
[    1.063779] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.063867] ahci 0000:00:1f.2: version 3.0
[    1.063880] ahci 0000:00:1f.2: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.063912]   alloc irq_desc for 29 on node 0
[    1.063914]   alloc kstat_irqs on node 0
[    1.063923] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    1.063991] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    1.063994] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part 
[    1.063998] ahci 0000:00:1f.2: setting latency timer to 64
[    1.064232] scsi0 : ahci
[    1.064349] scsi1 : ahci
[    1.064452] scsi2 : ahci
[    1.064498] scsi3 : ahci
[    1.064583] scsi4 : ahci
[    1.064625] scsi5 : ahci
[    1.064661] ata1: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 29
[    1.064664] ata2: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 29
[    1.064666] ata3: DUMMY
[    1.064667] ata4: DUMMY
[    1.064668] ata5: DUMMY
[    1.064670] ata6: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504380 irq 29
[    1.065558] Fixed MDIO Bus: probed
[    1.065588] PPP generic driver version 2.4.2
[    1.065661] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.065703] ehci_hcd 0000:00:1a.7: PCI INT C -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.065764] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.065767] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.065809] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.069762] ehci_hcd 0000:00:1a.7: debug port 1
[    1.069769] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.069775] ehci_hcd 0000:00:1a.7: irq 11, io mem 0xfc504800
[    1.083872] ACPI: Battery Slot [BAT0] (battery present)
[    1.090013] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.090129] usb usb1: configuration #1 chosen from 1 choice
[    1.090155] hub 1-0:1.0: USB hub found
[    1.090161] hub 1-0:1.0: 6 ports detected
[    1.090381] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 7
[    1.090383] PCI: setting IRQ 7 as level-triggered
[    1.090388] ehci_hcd 0000:00:1d.7: PCI INT A -> Link[LNKH] -> GSI 7 (level, low) -> IRQ 7
[    1.090397] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.090400] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.090475] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.094360] ehci_hcd 0000:00:1d.7: debug port 1
[    1.094366] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.094372] ehci_hcd 0000:00:1d.7: irq 7, io mem 0xfc504c00
[    1.110014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.110076] usb usb2: configuration #1 chosen from 1 choice
[    1.110097] hub 2-0:1.0: USB hub found
[    1.110102] hub 2-0:1.0: 6 ports detected
[    1.110166] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.110179] uhci_hcd: USB Universal Host Controller Interface driver
[    1.110244] uhci_hcd 0000:00:1a.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    1.110250] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.110253] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.110280] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.110308] uhci_hcd 0000:00:1a.0: irq 5, io base 0x00001800
[    1.110370] usb usb3: configuration #1 chosen from 1 choice
[    1.110390] hub 3-0:1.0: USB hub found
[    1.110396] hub 3-0:1.0: 2 ports detected
[    1.110599] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    1.110602] uhci_hcd 0000:00:1a.1: PCI INT B -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[    1.110608] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.110611] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.110637] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.110662] uhci_hcd 0000:00:1a.1: irq 11, io base 0x00001820
[    1.110727] usb usb4: configuration #1 chosen from 1 choice
[    1.110750] hub 4-0:1.0: USB hub found
[    1.110755] hub 4-0:1.0: 2 ports detected
[    1.110823] uhci_hcd 0000:00:1a.2: PCI INT C -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.110829] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.110832] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.110856] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.110881] uhci_hcd 0000:00:1a.2: irq 11, io base 0x00001840
[    1.110943] usb usb5: configuration #1 chosen from 1 choice
[    1.110965] hub 5-0:1.0: USB hub found
[    1.110970] hub 5-0:1.0: 2 ports detected
[    1.111034] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKH] -> GSI 7 (level, low) -> IRQ 7
[    1.111040] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.111043] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.111073] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.111097] uhci_hcd 0000:00:1d.0: irq 7, io base 0x00001860
[    1.111157] usb usb6: configuration #1 chosen from 1 choice
[    1.111179] hub 6-0:1.0: USB hub found
[    1.111184] hub 6-0:1.0: 2 ports detected
[    1.111245] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.111251] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.111254] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.111279] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.111304] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001880
[    1.111368] usb usb7: configuration #1 chosen from 1 choice
[    1.111388] hub 7-0:1.0: USB hub found
[    1.111393] hub 7-0:1.0: 2 ports detected
[    1.111597] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    1.111599] PCI: setting IRQ 10 as level-triggered
[    1.111604] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    1.111610] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.111613] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.111639] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.111665] uhci_hcd 0000:00:1d.2: irq 10, io base 0x000018a0
[    1.111732] usb usb8: configuration #1 chosen from 1 choice
[    1.111752] hub 8-0:1.0: USB hub found
[    1.111760] hub 8-0:1.0: 2 ports detected
[    1.111844] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.124088] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.124093] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.124143] mice: PS/2 mouse device common for all mice
[    1.124242] rtc_cmos 00:05: RTC can wake from S4
[    1.124268] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.124292] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.124387] device-mapper: uevent: version 1.0.3
[    1.124462] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.124523] device-mapper: multipath: version 1.1.0 loaded
[    1.124526] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.124729] cpuidle: using governor ladder
[    1.124821] cpuidle: using governor menu
[    1.125167] TCP cubic registered
[    1.125267] NET: Registered protocol family 10
[    1.125615] lo: Disabled Privacy Extensions
[    1.125850] NET: Registered protocol family 17
[    1.125865] Bluetooth: L2CAP ver 2.13
[    1.125867] Bluetooth: L2CAP socket layer initialized
[    1.125870] Bluetooth: SCO (Voice Link) ver 0.6
[    1.125871] Bluetooth: SCO socket layer initialized
[    1.125920] Bluetooth: RFCOMM TTY layer initialized
[    1.125923] Bluetooth: RFCOMM socket layer initialized
[    1.125924] Bluetooth: RFCOMM ver 1.11
[    1.130530] PM: Resume from disk failed.
[    1.130541] registered taskstats version 1
[    1.130648]   Magic number: 10:131:52
[    1.130756] rtc_cmos 00:05: setting system clock to 2010-01-22 00:03:27 UTC (1264118607)
[    1.130758] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.130760] EDD information not available.
[    1.132563] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.430112] ata6: SATA link down (SStatus 0 SControl 300)
[    1.500097] Clocksource tsc unstable (delta = -342319361 ns)
[    1.530138] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.590090] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.602584] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.617220] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633A, D600, max UDMA/100
[    1.617231] ata2.00: applying bridge limits
[    1.630603] ata2.00: configured for UDMA/100
[    1.641263] ata1.00: ATA-8: WDC WD3200BEVT-75ZCT2, 11.01A11, max UDMA/133
[    1.641267] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.643442] ata1.00: configured for UDMA/133
[    1.660189] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-7 11.0 PQ: 0 ANSI: 5
[    1.660288] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.660308] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.660344] sd 0:0:0:0: [sda] Write Protect is off
[    1.660347] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.660366] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.660465]  sda:
[    1.662682] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633A D600 PQ: 0 ANSI: 5
[    1.664758]  sda1 sda2 sda3 sda4 <sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.667144] Uniform CD-ROM driver Revision: 3.20
[    1.667233] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.667279] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.686004]  sda5 sda6 >
[    1.695833] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.695874] Freeing unused kernel memory: 660k freed
[    1.696066] Write protecting the kernel read-only data: 7584k
[    1.753232] usb 1-6: configuration #1 chosen from 1 choice
[    1.790815] ACPI Warning: \_SB_.PCI0.P0P2.M86_.LCD_._BCL: Return type mismatch - found Integer, expected Package 20090521 nspredef-940
[    1.790821] ACPI: Invalid _BCL data
[    1.790918] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[    1.790953] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)
[    1.822844] tg3.c:v3.99 (April 20, 2009)
[    1.823017] tg3 0000:08:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.823029] tg3 0000:08:00.0: setting latency timer to 64
[    1.839438] ohci1394 0000:09:01.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.841025] tg3 0000:08:00.0: PME# disabled
[    1.892084] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fc200000-fc2007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.930058] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    2.081424] usb 2-2: configuration #1 chosen from 1 choice
[    2.086314] Initializing USB Mass Storage driver...
[    2.086444] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.086591] usbcore: registered new interface driver usb-storage
[    2.086594] USB Mass Storage support registered.
[    2.086597] usb-storage: device found at 3
[    2.086599] usb-storage: waiting for device to settle before scanning
[    2.360052] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    2.540211] usb 3-1: configuration #1 chosen from 1 choice
[    2.541409] hub 3-1:1.0: USB hub found
[    2.543372] hub 3-1:1.0: 3 ports detected
[    2.880108] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    3.072226] usb 6-1: configuration #1 chosen from 1 choice
[    3.078964] usbcore: registered new interface driver hiddev
[    3.093437] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input7
[    3.093489] generic-usb 0003:0603:00F2.0001: input,hidraw0: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input0
[    3.129235] input: NOVATEK USB Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.1/input/input8
[    3.129328] generic-usb 0003:0603:00F2.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-0000:00:1d.0-1/input1
[    3.129340] usbcore: registered new interface driver usbhid
[    3.129342] usbhid: v2.6:USB HID core driver
[    3.151372] usb 3-1.1: new full speed USB device using uhci_hcd and address 3
[    3.171524] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:f3:98:03
[    3.171527] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.171529] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.171531] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.210143] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc00029a60d58]
[    3.320068] usb 3-1.1: configuration #1 chosen from 1 choice
[    3.360228] input: HID 413c:8157 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input9
[    3.360280] generic-usb 0003:413C:8157.0003: input,hidraw2: USB HID v1.11 Keyboard [HID 413c:8157] on usb-0000:00:1a.0-1.1/input0
[    3.471371] usb 3-1.2: new full speed USB device using uhci_hcd and address 4
[    3.566287] xor: automatically using best checksumming function: generic_sse
[    3.597430] usb 3-1.2: configuration #1 chosen from 1 choice
[    3.604668] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input10
[    3.604724] generic-usb 0003:413C:8158.0004: input,hidraw3: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2/input0
[    3.610017]    generic_sse:  9556.800 MB/sec
[    3.610019] xor: using function: generic_sse (9556.800 MB/sec)
[    3.630005] device-mapper: dm-raid45: initialized v0.2594b
[    7.080294] usb-storage: device scan complete
[    7.080859] scsi 6:0:0:0: Direct-Access     Seagate  Portable         0130 PQ: 0 ANSI: 4
[    7.081215] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.082378] sd 6:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    7.082969] sd 6:0:0:0: [sdb] Write Protect is off
[    7.082971] sd 6:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[    7.082979] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.084328] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.084332]  sdb: sdb1
[    7.086983] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    7.086986] sd 6:0:0:0: [sdb] Attached SCSI disk
[    8.936516] EXT4-fs (sda6): barriers enabled
[    8.959891] kjournald2 starting: pid 509, dev sda6:8, commit interval 5 seconds
[    8.959910] EXT4-fs (sda6): delayed allocation enabled
[    8.959913] EXT4-fs: file extents enabled
[    8.961250] EXT4-fs: mballoc enabled
[    8.961261] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    9.934086] type=1505 audit(1264118616.299:2): operation="profile_load" pid=532 name=/usr/share/gdm/guest-session/Xsession
[    9.936128] type=1505 audit(1264118616.299:3): operation="profile_load" pid=533 name=/sbin/dhclient3
[    9.936715] type=1505 audit(1264118616.299:4): operation="profile_load" pid=533 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.937015] type=1505 audit(1264118616.299:5): operation="profile_load" pid=533 name=/usr/lib/connman/scripts/dhclient-script
[    9.968441] type=1505 audit(1264118616.329:6): operation="profile_load" pid=534 name=/usr/bin/evince
[    9.977599] type=1505 audit(1264118616.341:7): operation="profile_load" pid=534 name=/usr/bin/evince-previewer
[    9.982937] type=1505 audit(1264118616.351:8): operation="profile_load" pid=534 name=/usr/bin/evince-thumbnailer
[    9.999584] type=1505 audit(1264118616.361:9): operation="profile_load" pid=536 name=/usr/lib/cups/backend/cups-pdf
[   10.000271] type=1505 audit(1264118616.361:10): operation="profile_load" pid=536 name=/usr/sbin/cupsd
[   10.030450] type=1505 audit(1264118616.391:11): operation="profile_load" pid=537 name=/usr/sbin/mysqld-akonadi
[   15.371353] usplash:401 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   33.216489] udev: starting version 147
[   33.237239] Adding 4996172k swap on /dev/sda5.  Priority:-1 extents:1 across:4996172k 
[   33.242832] lp: driver loaded but no devices found
[   33.285195] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   33.285199] Disabling lock debugging due to kernel taint
[   33.326612] [fglrx] Maximum main memory to use for locked dma buffers: 3768 MBytes.
[   33.326908] [fglrx]   vendor: 1002 device: 9553 count: 1
[   33.327299] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   33.327323] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[   33.327329] pci 0000:01:00.0: setting latency timer to 64
[   33.327472] [fglrx] Kernel PAT support is enabled
[   33.327506] [fglrx] module loaded - fglrx 8.67.4 [Nov  4 2009] with 1 minors
[   33.342878] sdhci: Secure Digital Host Controller Interface driver
[   33.342881] sdhci: Copyright(c) Pierre Ossman
[   33.343842] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[   33.343861] sdhci-pci 0000:09:01.1: PCI INT B -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[   33.345970] Registered led device: mmc0::
[   33.347001] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[   33.379226] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   33.415978] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.418231] input: Dell WMI hotkeys as /devices/virtual/input/input11
[   33.442907] Linux video capture interface: v2.00
[   33.445127] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:63eb)
[   33.475834] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input12
[   33.475881] usbcore: registered new interface driver uvcvideo
[   33.475884] USB Video Class driver (v0.1.0)
[   33.477696] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   33.477701] HDA Intel 0000:00:1b.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[   33.477750] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   33.501826] cfg80211: Calling CRDA to update world regulatory domain
[   33.532155] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   33.532158] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   33.532555] iwlagn 0000:04:00.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   33.532586] iwlagn 0000:04:00.0: setting latency timer to 64
[   33.532655] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   33.574755] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   33.574818]   alloc irq_desc for 30 on node 0
[   33.574820]   alloc kstat_irqs on node 0
[   33.574838] iwlagn 0000:04:00.0: irq 30 for MSI/MSI-X
[   33.584833] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   33.616804] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input13
[   33.631118] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   33.692658] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   33.692720] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   33.693536] HDA Intel 0000:01:00.1: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   33.693593] HDA Intel 0000:01:00.1: setting latency timer to 64
[   34.051378] usb 3-1.3: new full speed USB device using uhci_hcd and address 5
[   34.131559] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   34.177670] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input17
[   34.204467] usb 3-1.3: configuration #1 chosen from 1 choice
[   34.209090] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   34.209192] usbcore: registered new interface driver btusb
[   35.145828] cfg80211: World regulatory domain updated:
[   35.145831]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   35.145839]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.145842]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   35.145844]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   35.145846]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.145847]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   37.053868] EXT4-fs (sda6): internal journal on sda6:8
[   38.275347] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   38.312946] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
[   38.444673] Registered led device: iwl-phy0::radio
[   38.444695] Registered led device: iwl-phy0::assoc
[   38.444714] Registered led device: iwl-phy0::RX
[   38.444780] Registered led device: iwl-phy0::TX
[   38.493357] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.494516] tg3 0000:08:00.0: PME# disabled
[   38.494850]   alloc irq_desc for 31 on node 0
[   38.494853]   alloc kstat_irqs on node 0
[   38.494872] tg3 0000:08:00.0: irq 31 for MSI/MSI-X
[   38.641915] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.772252] __ratelimit: 3 callbacks suppressed
[   38.772254] type=1505 audit(1264098845.139:13): operation="profile_replace" pid=1329 name=/usr/share/gdm/guest-session/Xsession
[   38.773747] type=1505 audit(1264098845.139:14): operation="profile_replace" pid=1330 name=/sbin/dhclient3
[   38.774351] type=1505 audit(1264098845.139:15): operation="profile_replace" pid=1330 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   38.775423] type=1505 audit(1264098845.139:16): operation="profile_replace" pid=1330 name=/usr/lib/connman/scripts/dhclient-script
[   38.778862] type=1505 audit(1264098845.139:17): operation="profile_replace" pid=1333 name=/usr/bin/evince
[   38.789267] type=1505 audit(1264098845.149:18): operation="profile_replace" pid=1333 name=/usr/bin/evince-previewer
[   38.795277] type=1505 audit(1264098845.159:19): operation="profile_replace" pid=1333 name=/usr/bin/evince-thumbnailer
[   38.803619] type=1505 audit(1264098845.169:20): operation="profile_replace" pid=1348 name=/usr/lib/cups/backend/cups-pdf
[   38.804413] type=1505 audit(1264098845.169:21): operation="profile_replace" pid=1348 name=/usr/sbin/cupsd
[   38.824301] type=1505 audit(1264098845.189:22): operation="profile_replace" pid=1366 name=/usr/sbin/mysqld-akonadi
[   39.250738]   alloc irq_desc for 32 on node 0
[   39.250741]   alloc kstat_irqs on node 0
[   39.250753] fglrx_pci 0000:01:00.0: irq 32 for MSI/MSI-X
[   39.251771] kjournald starting.  Commit interval 5 seconds
[   39.251777] [fglrx] Firegl kernel thread PID: 1563
[   39.251781] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   39.253109] EXT3 FS on sda2, internal journal
[   39.253115] EXT3-fs: mounted filesystem with writeback data mode.
[   39.429080] [fglrx] Gart USWC size:1227 M.
[   39.429084] [fglrx] Gart cacheable size:487 M.
[   39.429088] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   39.429090] [fglrx] Reserved FB block: Unshared offset:fc27000, size:3d9000 
[   39.429092] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   40.874379] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   40.874382] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   40.874383] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   40.874384] vboxdrv: the usage of hardware performance counters by
[   40.874385] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   40.874388] vboxdrv: Found 2 processor cores.
[   40.874438] VBoxDrv: dbg - g_abExecMemory=ffffffffa050b280
[   40.874459] vboxdrv: fAsync=0 offMin=0x13b offMax=0x1368
[   40.874496] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   40.874498] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   41.146540] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   41.146542] Bluetooth: BNEP filters: protocol multicast
[   41.152298] Bridge firewalling registered
[   41.289807] ppdev: user-space parallel port driver
[   43.178124] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   45.482530] UDF-fs: No VRS found
[   45.482534] UDF-fs: No partition found (1)
[   61.823635] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   61.824035] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:11/input18
[   61.824110] generic-bluetooth 0005:046D:B006.0005: input,hidraw3: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on 00:24:2B:FC:F7:08
[  109.246213] __ratelimit: 3 callbacks suppressed
[  109.246217] evolution[2699]: segfault at 7f3c020afe08 ip 00007f3c194a1df4 sp 00007fffdc83ad40 error 7 in libpangoft2-1.0.so.0.2600.0[7f3c1948a000+27000]
[  316.915256] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  316.915264] tg3: eth0: Flow control is off for TX and off for RX.
[  316.916325] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  316.996331] tg3: eth0: Link is down.
[  326.930121] eth0: no IPv6 routers present
[  344.846343] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  344.846351] tg3: eth0: Flow control is off for TX and off for RX.
[  345.677416] tg3: eth0: Link is down.
[  347.278968] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  347.278976] tg3: eth0: Flow control is off for TX and off for RX.
[  347.747433] tg3: eth0: Link is down.
[  365.817840] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  365.817848] tg3: eth0: Flow control is off for TX and off for RX.
[  402.328216] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 5466.259925] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 6462.732158] CE: hpet increasing min_delta_ns to 15000 nsec
[ 8404.212543] ACPI: EC: missing confirmations, switch off interrupt mode.
[ 8404.726324] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
[ 8404.726342] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.TZ01._TMP] (Node ffff88013ba3ccc0), AE_TIME
[ 9505.363127] tg3: eth0: Link is down.
[ 9638.902353] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 9638.902356] tg3: eth0: Flow control is off for TX and off for RX.
[27355.605494] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:12/input19
[27355.605698] generic-bluetooth 0005:046D:B006.0006: input,hidraw3: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on 00:24:2B:FC:F7:08
[32592.344532] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:11/input20
[32592.344736] generic-bluetooth 0005:046D:B006.0007: input,hidraw3: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on 00:24:2B:FC:F7:08
[32764.830085] usb 2-3: new high speed USB device using ehci_hcd and address 4
[32764.991467] usb 2-3: configuration #1 chosen from 2 choices
[32764.996497] scsi7 : SCSI emulation for USB Mass Storage devices
[32764.996615] usb-storage: device found at 4
[32764.996617] usb-storage: waiting for device to settle before scanning
[32770.000272] usb-storage: device scan complete
[32770.002282] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[32770.002891] sd 7:0:0:0: Attached scsi generic sg3 type 0
[32770.025621] sd 7:0:0:0: [sdc] 1946049 4096-byte logical blocks: (7.97 GB/7.42 GiB)
[32770.026221] sd 7:0:0:0: [sdc] Write Protect is off
[32770.026225] sd 7:0:0:0: [sdc] Mode Sense: 68 00 00 08
[32770.026228] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[32770.027724] sd 7:0:0:0: [sdc] 1946049 4096-byte logical blocks: (7.97 GB/7.42 GiB)
[32770.028222] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[32770.028227]  sdc: sdc1
[32770.031121] sd 7:0:0:0: [sdc] 1946049 4096-byte logical blocks: (7.97 GB/7.42 GiB)
[32770.031733] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[32770.031741] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[33152.960296] sdc: detected capacity change from 7971016704 to 0
[33445.420051] usb 2-3: USB disconnect, address 4
[37443.140498] tg3: eth0: Link is down.
[37613.149589] tg3: eth0: Link is up at 100 Mbps, full duplex.
[37613.149597] tg3: eth0: Flow control is off for TX and off for RX.
[40617.203090] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:12/input21
[40617.203171] generic-bluetooth 0005:046D:B006.0008: input,hidraw3: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on 00:24:2B:FC:F7:08
[50754.269405] tg3: eth0: Link is down.
[50921.929930] tg3: eth0: Link is up at 100 Mbps, full duplex.
[50921.929933] tg3: eth0: Flow control is off for TX and off for RX.
[55564.100041] usb 2-3: new high speed USB device using ehci_hcd and address 5
[55564.310149] usb 2-3: configuration #1 chosen from 2 choices
[55564.310631] scsi8 : SCSI emulation for USB Mass Storage devices
[55564.310725] usb-storage: device found at 5
[55564.310727] usb-storage: waiting for device to settle before scanning
[55569.310266] usb-storage: device scan complete
[55569.320686] scsi 8:0:0:0: Direct-Access     Sony     DSC              1.00 PQ: 0 ANSI: 0 CCS
[55569.387265] sd 8:0:0:0: Attached scsi generic sg3 type 0
[55569.430894] sd 8:0:0:0: [sdc] 3938304 512-byte logical blocks: (2.01 GB/1.87 GiB)
[55569.443112] sd 8:0:0:0: [sdc] Write Protect is off
[55569.443116] sd 8:0:0:0: [sdc] Mode Sense: 00 6a 20 00
[55569.443118] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[55569.471958] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[55569.471965]  sdc: sdc1
[55569.500054] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[55569.500060] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[55880.180099] usb 2-2: reset high speed USB device using ehci_hcd and address 3
[56345.365003] drivemount_appl[2752]: segfault at 0 ip (null) sp 00007fff5bbc2f38 error 14 in drivemount_applet2[400000+8000]
[56357.067178] usb 2-3: USB disconnect, address 5
[64410.542596] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:11/input22
[64410.543315] generic-bluetooth 0005:046D:B0
```
This is the maximum that I can see.

---

### Post by nishant.singh28 on 2010-01-22
The Kernel in use is ****.17. Same kernel in a friend's laptop. Same make, model, no errors there.

---

### Post by nishant.singh28 on 2010-01-22
And the system boots and works fine. I'm on the very same laptop.

---

### Post by 00_Spykes on 2010-01-22
I can't see exactly what's wrong, I do see some segfaults and some ACPI errors... but nothing I can tell about that. If I were you I think I would boot from the install CD (so that you can see that your hardware is operational). Then I would chroot into the partition where you installed Ubuntu, and re-install the kernel.

I think Ubuntu's kernel-building approach is the same as genkernels, it takes info from your booted system, and copies that info, and generates a new kernel. So, be sure to boot from the CD with the correct hardware, then chroot correctly (that is, mount the proc, and dev and sys filesystems), then when you are chrooted into the installed environment (not the boot-from-cd environment) re-install the kernel. Then ofc make sure that you boot that kernel too, i.e. configure the bootloader correctly.

---

### Post by Saiko Berry on 2010-01-22
[   15.371353] usplash:401 freeing invalid memtype ffffffffd0000000-ffffffffd1000000
[   33.216489] udev: starting version 147

I was right, its related to udev and usplash.

Unplug all usb devices and restart with the CD.

Im guessing its a video card problem but I'm unsure.

---

### Post by nishant.singh28 on 2010-01-22
What after restarting with the CD?

---

### Post by Saiko Berry on 2010-01-22
Come back and tell us how it went? >_> Post error log? Does the udev/usplash show up when you boot from a CD/does it ever show up? There is still lacking information here dispite your quintuple post up there.

---

### Post by nishant.singh28 on 2010-01-22
I'm quite new so please...

---

### Post by Saiko Berry on 2010-01-22
Does this screen look familliar?

[IMG]http://img4.imageshack.us/img4/9990/96514479.jpg[/IMG]

---

### Post by 00_Spykes on 2010-01-22
Kind of depends on which CD you boot with too I guess, I'm assuming it's the standard Ubuntu desktop variant, because I'm not sure if the minimal or server comes with X or video drivers...

---

### Post by nishant.singh28 on 2010-01-22
Ok. I have the 64 bit iso on a flash drive. I booted into it. No errors. Then into the HDD, same errors. I reinstalled the kernel in use, no change. I recorded both of the boots. Will post the links once the vids are uploaded.

---

### Post by nishant.singh28 on 2010-01-22
Boot from flash drive:
[http://www.youtube.com/watch?v=jC9wvfWuk0Q](http://www.youtube.com/watch?v=jC9wvfWuk0Q)
From the HDD ( I have KDE too-I wanted to get familiar with it )
[http://www.youtube.com/watch?v=KOmyc-MAY6I](http://www.youtube.com/watch?v=KOmyc-MAY6I)

 The point where the progress bar gets stuck is where the error appears. Sometimes, like in the video the bar gets stuck. Sometimes, the error appears. I'll post a snapshot next.

---

### Post by nishant.singh28 on 2010-01-22
Here is a snap of the screen during the last boot.

---

### Post by 00_Spykes on 2010-01-22
You are sure that the right kernel image and initrd gets booted from the Grub menu?

Well, at least we know your hardware is ok, right? 

What is your boot device?

By the way, your only problem is that you think those usb errors are annoying, right? Otherwise your system is fine?

---

### Post by Saiko Berry on 2010-01-22
Am I blind or did nothing errorous happen in the video o.o

Sidenote: Warnings dont matter. Rule 1 of Linux is they are going to happen, care about the errors.

---

### Post by nishant.singh28 on 2010-01-22
Yes. I'm sure. New as I may be, I'm not so inexperienced :D. Yeah the errors are kind of annoying and I guess they slow down startup a little. The system is fine overall except for the fact that my laptop's eject button does not work.
Boot device is /dev/sda6

---

### Post by nishant.singh28 on 2010-01-22
> **Saiko Berry said:**
> Am I blind or did nothing errorous happen in the video o.o

Sidenote: Warnings dont matter. Rule 1 of Linux is they are going to happen, care about the errors.
I can say you are :P....I  wrote that either the error shows up or the progress bar stops for some time as it did in the 2nd video.

---

### Post by Saiko Berry on 2010-01-22
You know there is an edit button right? Seriously stop double/triple/quadruple posting.

Anyways I dont think its a problem. It's not doing anything and everything seems to be running well. Wait for a kernel upgrade, upgrade kernal and it will probably go away.

Anyways, on the topic of usplashes.. I hate Karmic's. It's so boring -_-

---

### Post by nishant.singh28 on 2010-01-22
> **Saiko Berry said:**
> You know there is an edit button right? Seriously stop double/triple/quadruple posting.

Anyways I dont think its a problem. It's not doing anything and everything seems to be running well. Wait for a kernel upgrade, upgrade kernal and it will probably go away.

Anyways, on the topic of usplashes.. I hate Karmic's. It's so boring -_-
I know about the edit button. It's just a general policy of mine not to put too much info in one post. It becomes too cluttered. It's easier to read when broken up. Atleast that's what I think. If you have a problem, I'll take care not to do it in a thread involving you :D. And any inputs about the eject button?
[http://ubuntuforums.org/showthread.php?t=1333742](http://ubuntuforums.org/showthread.php?t=1333742)

---

### Post by 00_Spykes on 2010-01-22
Well, then it's not that very urgent to fix then, and I think that the Ubuntu-generated kernel is configured to probe your devices at start-up, whether it finds them or not doesn't matter very much.

If you are concerned about start-up time I've seen a few "tweaking"-posts around here somewhere. Basically configure your own kernel and put the drivers inside the kernel, not as modules. ;) Oh, and disable network at boot, it takes time to configure DHCP and stuff, unless we can have it to run in the background somehow... hmm... anyone?

---

### Post by nishant.singh28 on 2010-01-22
No DHCP here. Manual settings for the college LAN.

---

### Post by bodhi.zazen on 2010-01-22
There is a bug report here :

[https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/439648](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/439648)

I did not see any explanation of exactly why you are getting this message or what the fix would be (other then to update your kernel).

The consensus appears to be that this is a warning and as long as your system is working properly once booted not something to be concerned about.

---

