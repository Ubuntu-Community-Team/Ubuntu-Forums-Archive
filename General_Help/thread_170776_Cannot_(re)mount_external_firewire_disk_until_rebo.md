---
title: "Cannot (re)mount external firewire disk until reboot"
date: 2006-05-05
forum: General Help
---

### Post by calt129 on 2006-05-05
Hi ppl,

I have an external firewire hard disk which is automatically mounted during boot and I can use it without any problems. If I unmount the disk I can mount the partitions as long as the device is plugged in. So far so good.

However, if I unmount the disk and pull the plug, or similarly put the computer in standby mode and wake it back up, the disk is not automatically mounted anymore. Furthermore, the devices /dev/sda* are deleted so I cannot mount the disk manually.

I have these lines in /etc/fstab and I've tried every possible combination of them (uncommented, of course ;)
```

#/dev/sda1       /media/tigia_boot   vfat    rw,user,noexec,nosuid,nodev 0   0
#/dev/sda5       /media/tigia_data   vfat    rw,user,noexec,nosuid,nodev 0   0
#/dev/sda1       /media/tigia_boot   vfat    rw,user,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0   0
#/dev/sda5       /media/tigia_data   vfat    rw,user,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0   0
```


Before you ask for outputs from some commands, I'm including some here.

Before unmounting...:

```

cu@cyix:~$ mount | grep /sda
/dev/sda5 on /media/tigia_data type vfat (rw,noexec,nosuid,nodev,user=cu)
/dev/sda1 on /media/tigia_boot type vfat (rw,noexec,nosuid,nodev,user=cu)

cu@cyix:~$ fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         522     4192933+   c  W95 FAT32 (LBA)
/dev/sda2             523        9733    73987357+   f  W95 Ext'd (LBA)
/dev/sda5             523        9733    73987326    b  W95 FAT32
cu@cyix:~$ lsmod > before
cu@cyix:~$ sudo cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: OTOSTORE Model:  SCS12A          Rev: 4.67
  Type:   Direct-Access                    ANSI SCSI revision: 02
cu@cyix:~$
```


...and after unmounting:

```

cu@cyix:~$ mount | grep /sda
cu@cyix:~$ fdisk -l
cu@cyix:~$ lsmod > after
cu@cyix:~$ diff before after
25c25
< sd_mod                 17424  3
---
> sd_mod                 17424  0
47,49c47,49
< nls_iso8859_1           4224  3
< nls_cp437               5888  3
< vfat                   12288  3
---
> nls_iso8859_1           4224  1
> nls_cp437               5888  1
> vfat                   12288  1
63c63
< sbp2                   21128  3
---
> sbp2                   21128  1
cu@cyix:~$
```

I've run *sudo modprobe sd_mod* and tried to mount the disk but the devicefiles (/dev/sda*) don't seem to be created with this command (which isn't a big surprise). The problem is that fdisk doesn't even list the partitions as connected. 


And here is the output of dmesg:
```
cu@cyix:~$ dmesg
5)
[4294668.094000] burst-mode-ec-10-Aug
[4294668.094000] ACPI: Embedded Controller [H_EC] (gpe 23)
[4294668.095000] ACPI: Power Resource [CFAN] (on)
[4294668.096000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.096000] pnp: PnP ACPI init
[4294668.098000] pnp: PnP ACPI: found 11 devices
[4294668.098000] PnPBIOS: Disabled by ACPI PNP
[4294668.098000] PCI: Using ACPI for IRQ routing
[4294668.098000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.116000] Simple Boot Flag at 0x36 set to 0x1
[4294668.117000] audit: initializing netlink socket (disabled)
[4294668.117000] audit: initialized
[4294668.117000] highmem bounce pool size: 64 pages
[4294668.117000] VFS: Disk quotas dquot_6.5.1
[4294668.117000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.117000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.117000] devfs: boot_options: 0x0
[4294668.117000] Initializing Cryptographic API
[4294668.117000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294668.117000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[4294668.117000] assign_interrupt_mode Found MSI capability
[4294668.117000] Allocate Port Service[pcie00]
[4294668.117000] Allocate Port Service[pcie02]
[4294668.117000] Allocate Port Service[pcie03]
[4294668.117000] isapnp: Scanning for PnP cards...
[4294668.473000] isapnp: No Plug & Play device found
[4294668.487000] hpet_acpi_add: no address or irqs in _CRS
[4294668.487000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294668.493000] i8042.c: Detected active multiplexing controller, rev 1.1.
[4294668.496000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[4294668.496000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[4294668.497000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[4294668.497000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[4294668.497000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.498000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294668.499000] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 20
[4294668.499000] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[4294668.499000] io scheduler noop registered
[4294668.499000] io scheduler anticipatory registered
[4294668.499000] io scheduler deadline registered
[4294668.499000] io scheduler cfq registered
[4294668.500000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.501000] EISA: Probing bus 0 at eisa.0
[4294668.501000] Cannot allocate resource for EISA slot 1
[4294668.501000] Cannot allocate resource for EISA slot 2
[4294668.501000] Cannot allocate resource for EISA slot 3
[4294668.501000] EISA: Detected 0 cards.
[4294668.501000] NET: Registered protocol family 2
[4294668.510000] IP: routing cache hash table of 8192 buckets, 64Kbytes
[4294668.510000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[4294668.510000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[4294668.511000] TCP: Hash tables configured (established 131072 bind 65536)
[4294668.511000] NET: Registered protocol family 8
[4294668.511000] NET: Registered protocol family 20
[4294668.511000] ACPI wakeup devices:
[4294668.511000] PWRB RP01 LANC MODM
[4294668.511000] ACPI: (supports S0 S3 S4 S5)
[4294668.511000] Freeing unused kernel memory: 224k freed
[4294668.547000] Capability LSM initialized
[4294668.558000] NET: Registered protocol family 1
[4294668.574000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294668.574000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294668.574000] ACPI: bus type ide registered
[4294668.578000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[4294668.578000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[4294668.578000] ICH6: chipset revision 3
[4294668.578000] ICH6: not 100% native mode: will probe irqs later
[4294668.578000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
[4294668.578000] Probing IDE interface ide0...
[4294668.661000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294668.842000] hda: SAMSUNG MP0804H, ATA DISK drive
[4294669.556000] hdb: DV-W28E, ATAPI CD/DVD-ROM drive
[4294669.607000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294669.607000] Probing IDE interface ide1...
[4294670.120000] Probing IDE interface ide2...
[4294670.632000] Probing IDE interface ide3...
[4294671.144000] Probing IDE interface ide4...
[4294671.656000] Probing IDE interface ide5...
[4294672.170000] hda: max request size: 1024KiB
[4294672.622000] hda: Host Protected Area detected.
[4294672.622000]        current capacity is 155306477 sectors (79516 MB)
[4294672.622000]        native  capacity is 156368016 sectors (80060 MB)
[4294672.676000] hda: task_no_data_intr: status=0x51 { DriveReady SeekComplete Error }
[4294672.676000] hda: task_no_data_intr: error=0x04 { DriveStatusError }
[4294672.676000] ide: failed opcode was: 0x37
[4294672.676000] hda: 155306477 sectors (79516 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[4294672.677000] hda: cache flushes supported
[4294672.677000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 >
[4294672.739000] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2193kB Cache
[4294672.739000] Uniform CD-ROM driver Revision: 3.20
[4294673.000000] Attempting manual resume
[4294673.019000] swsusp: Suspend partition has wrong signature?
[4294673.056000] usbcore: registered new driver usbfs
[4294673.056000] usbcore: registered new driver hub
[4294673.057000] USB Universal Host Controller Interface driver v2.2
[4294673.057000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294673.057000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294673.057000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294673.119000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294673.119000] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[4294673.119000] hub 1-0:1.0: USB hub found
[4294673.119000] hub 1-0:1.0: 2 ports detected
[4294673.122000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[4294673.122000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294673.122000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294673.184000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294673.184000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[4294673.184000] hub 2-0:1.0: USB hub found
[4294673.184000] hub 2-0:1.0: 2 ports detected
[4294673.187000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294673.187000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294673.187000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294673.249000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294673.249000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[4294673.249000] hub 3-0:1.0: USB hub found
[4294673.249000] hub 3-0:1.0: 2 ports detected
[4294673.252000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[4294673.252000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294673.252000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294673.314000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294673.314000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[4294673.314000] hub 4-0:1.0: USB hub found
[4294673.314000] hub 4-0:1.0: 2 ports detected
[4294673.346000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[4294673.346000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294673.346000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294673.346000] ehci_hcd 0000:00:1d.7: debug port 1
[4294673.346000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294673.346000] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0040000
[4294673.350000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294673.350000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294673.350000] hub 5-0:1.0: USB hub found
[4294673.350000] hub 5-0:1.0: 8 ports detected
[4294673.357000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294673.422000] b44.c:v0.95 (Aug 3, 2004)
[4294673.422000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294673.425000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:00:f0:78:e3:25
[4294673.853000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[4294675.484000] usbcore: registered new driver hiddev
[4294675.501000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.1-1
[4294675.501000] usbcore: registered new driver usbhid
[4294675.501000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294675.731000] ACPI: Fan [FAN1] (on)
[4294675.734000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294675.734000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294675.736000] ACPI: Thermal Zone [THRM] (45 C)
[4294675.839000] Attempting manual resume
[4294675.840000] swsusp: Suspend partition has wrong signature?
[4294675.856000] kjournald starting.  Commit interval 5 seconds
[4294675.856000] EXT3-fs: mounted filesystem with ordered data mode.
[4294677.664000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294680.662000] Adding 2097136k swap on /dev/hda5.  Priority:-1 extents:1
[4294680.819000] EXT3 FS on hda1, internal journal
[4294696.395000] lp: driver loaded but no devices found
[4294696.419000] mice: PS/2 mouse device common for all mice
[4294696.678000] ieee1394: Initialized config rom entry `ip1394'
[4294696.683000] SCSI subsystem initialized
[4294696.687000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294696.715000] ieee80211_crypt: registered algorithm 'NULL'
[4294696.719000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4294696.719000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294696.727000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294696.728000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294696.728000] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 20
[4294696.731000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294697.386000] Linux agpgart interface v0.101 (c) Dave Jones
[4294697.387000] [drm] Initialized drm 1.0.0 20040925
[4294697.388000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294697.388000] [drm:drm_fill_in_dev] *ERROR* Cannot initialize the agpgart module.
[4294697.389000] DRM: Fill_in_dev failed.
[4294697.455000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0x2580b1, caps: 0xa04713/0x200000
[4294697.456000] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
[4294697.621000] ts: Compaq touchscreen protocol output
[4294700.339000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294701.559000] cdrom: open failed.
[4294702.352000] cdrom: open failed.
[4294702.757000] cdrom: open failed.
[4294707.197000] agpgart: Detected an Intel 915GM Chipset.
[4294707.197000] agpgart: Detected 7932K stolen memory.
[4294707.226000] agpgart: AGP aperture is 256M @ 0xc0000000
[4294707.326000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294707.335000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294707.592000] hw_random: RNG not detected
[4294707.744000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
[4294707.744000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294708.554000] intel8x0_measure_ac97_clock: measured 49489 usecs
[4294708.554000] intel8x0: clocking to 48000
[4294709.098000] Linux Kernel Card Services
[4294709.098000]   options:  [pci] [cardbus] [pm]
[4294709.119000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294709.119000] Yenta: CardBus bridge found at 0000:06:09.0 [144d:c01a]
[4294709.239000] Yenta: ISA IRQ mask 0x04b8, PCI irq 16
[4294709.239000] Socket status: 30000006
[4294709.334000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294709.334000] ACPI: PCI Interrupt 0000:06:09.1[B] -> GSI 17 (level, low) -> IRQ 17
[4294709.390000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[b8003000-b80037ff]  Max Packet=[2048]
[4294710.663000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[00303c0600104b35]
[4294710.667000] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0000f041200a50c6]
[4294710.667000] scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
[4294711.293000] Real Time Clock Driver v1.12
[4294711.770000] ieee1394: sbp2: Logged into SBP-2 device
[4294711.770000] ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[4294711.771000]   Vendor: OTOSTORE  Model:  SCS12A           Rev: 4.67
[4294711.771000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4294711.921000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[4294711.924000] SCSI device sda: drive cache: write back
[4294711.926000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
[4294711.928000] SCSI device sda: drive cache: write back
[4294711.928000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294712.437000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294713.264000] NET: Registered protocol family 17
[4294725.250000] ACPI: AC Adapter [ADP1] (on-line)
[4294725.290000] ACPI: Battery Slot [BAT1] (battery present)
[4294725.308000] ACPI: Power Button (FF) [PWRF]
[4294725.308000] ACPI: Lid Switch [LID0]
[4294725.308000] ACPI: Power Button (CM) [PWRB]
[4294725.308000] ACPI: Sleep Button (CM) [SLPB]
[4294725.402000] ibm_acpi: ec object not found
[4294725.506000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[4294729.405000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294729.405000] apm: overridden by ACPI.
[4294730.484000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294730.486000] cs: IO port probe 0xc00-0xcf7: clean.
[4294730.487000] cs: IO port probe 0xa00-0xaff: clean.
[4294735.738000] vmmon: module license 'unspecified' taints kernel.
[4294735.742000] /dev/vmmon[8211]: Module vmmon: registered with major=10 minor=165
[4294735.742000] /dev/vmmon[8211]: Module vmmon: initialized
[4294735.897000] /dev/vmnet: open called by PID 8241 (vmnet-bridge)
[4294735.897000] /dev/vmnet: hub 0 does not exist, allocating memory.
[4294735.897000] /dev/vmnet: port on hub 0 successfully opened
[4294735.898000] bridge-eth0: peer interface eth0 not found, will wait for it to come up
[4294735.898000] bridge-eth0: attached
[4294736.169000] /dev/vmnet: open called by PID 8255 (vmnet-natd)
[4294736.169000] /dev/vmnet: hub 8 does not exist, allocating memory.
[4294736.169000] /dev/vmnet: port on hub 8 successfully opened
[4294746.148000] /dev/vmnet: open called by PID 8377 (vmnet-netifup)
[4294746.148000] /dev/vmnet: hub 1 does not exist, allocating memory.
[4294746.148000] /dev/vmnet: port on hub 1 successfully opened
[4294746.150000] /dev/vmnet: open called by PID 8378 (vmnet-netifup)
[4294746.150000] /dev/vmnet: port on hub 8 successfully opened
[4294747.325000] /dev/vmnet: open called by PID 8437 (vmnet-dhcpd)
[4294747.325000] /dev/vmnet: port on hub 1 successfully opened
[4294747.327000] /dev/vmnet: open called by PID 8446 (vmnet-dhcpd)
[4294747.327000] /dev/vmnet: port on hub 8 successfully opened
cu@cyix:~$
```


How can I mount my disk without rebooting? :(

EDIT: The device recognition seems to be related to HAL. When I activate the auto-mounting via fstab, the drives are not recognized during booting, until HAL is started. Is there any manual script to trigger HAL?

---

### Post by physcsdrk on 2006-05-06
I have an external firewire disk that I have problems with.  I have an ext3 partition and an ntsf partition on the external drive.  Ubuntu says the ext3 partition is read only and i haven't been able to figure out how to change the permissions.  (that doesn't mean much as I am a total noob).  I would post code but I have no idea what code to post.  :)
Is there something I can do to change this?  Also I just want to use the external drive as backup.  Any good aps that I can use to schedule weekly backups with?

---

### Post by boltronics on 2006-05-08
I have exactly the same problem. I'm sure I've had it ever since the first Ubuntu release. I suspect there is a certain module that needs unloading prior to unplugging the device. Then perhaps the module can successfully re-load and the device will start working again. I haven't really looked into it though.

---

