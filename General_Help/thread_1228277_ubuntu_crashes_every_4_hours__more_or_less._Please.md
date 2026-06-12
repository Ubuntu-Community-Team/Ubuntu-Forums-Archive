---
title: "ubuntu crashes every 4 hours  more or less. Please Help"
date: 2009-07-31
forum: General Help
---

### Post by nestor123 on 2009-07-31
Hi, I'm very new to ubuntu, I really like the system but I have the problem that's **crashing every 4 hours or less**.

I tried reinstalling the driver for the video card, I have used several different versions but has not been solved.

 Now I reinstall the entire system (before  had installed ubuntu 9.04 now ubuntu 8.04) without using the nvidia drivers of video card. But this problem persists. 

         
**PC:**
Ubuntu 8.04 Kernel 2.4.24-24-generic
Motherboard: EliteGroup P4M800Pro
CPU: Intel P4 2.4 Ghz
RAM: 512MB
Sound: Sound Blaster Live 5.1

**I leave my  records for the last two crashes file /var/log/ messege**



> CRASH 2********************************************************************************

Jul 31 13:45:29 nestor-desktop kernel: [   31.647859] sd 2:0:0:0: [sdb] Attached SCSI disk
Jul 31 13:45:29 nestor-desktop kernel: [   31.659506] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 31 13:45:29 nestor-desktop kernel: [   31.659538] sr 0:0:1:0: Attached scsi generic sg1 type 5
Jul 31 13:45:29 nestor-desktop kernel: [   31.659568] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jul 31 13:45:29 nestor-desktop kernel: [   32.020697] Attempting manual resume
Jul 31 13:45:29 nestor-desktop kernel: [   32.040311] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 31 13:45:29 nestor-desktop kernel: [   32.040317] EXT3-fs: write access will be enabled during recovery.
Jul 31 13:45:29 nestor-desktop kernel: [   34.209832] kjournald starting.  Commit interval 5 seconds
Jul 31 13:45:29 nestor-desktop kernel: [   34.209858] EXT3-fs: sdb2: orphan cleanup on readonly fs
Jul 31 13:45:29 nestor-desktop kernel: [   34.209909] EXT3-fs: sdb2: 2 orphan inodes deleted
Jul 31 13:45:29 nestor-desktop kernel: [   34.209911] EXT3-fs: recovery complete.
Jul 31 13:45:29 nestor-desktop kernel: [   34.258619] EXT3-fs: mounted filesystem with ordered data mode.
Jul 31 13:45:29 nestor-desktop kernel: [   41.048390] Linux agpgart interface v0.102
Jul 31 13:45:29 nestor-desktop kernel: [   41.124883] agpgart: Detected VIA VT3314 chipset
Jul 31 13:45:29 nestor-desktop kernel: [   41.130471] agpgart: AGP aperture is 64M @ 0xf8000000
Jul 31 13:45:29 nestor-desktop kernel: [   41.185276] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 31 13:45:29 nestor-desktop kernel: [   41.237125] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 31 13:45:29 nestor-desktop kernel: [   41.547799] gameport: EMU10K1 is pci0000:00:0a.1/gameport0, io 0xe800, speed 1065kHz
Jul 31 13:45:29 nestor-desktop kernel: [   41.740643] input: Power Button (FF) as /devices/virtual/input/input2
Jul 31 13:45:29 nestor-desktop kernel: [   41.755570] ACPI: Power Button (FF) [PWRF]
Jul 31 13:45:29 nestor-desktop kernel: [   41.755775] input: Sleep Button (CM) as /devices/virtual/input/input3
Jul 31 13:45:29 nestor-desktop kernel: [   41.767560] ACPI: Sleep Button (CM) [SLPB]
Jul 31 13:45:29 nestor-desktop kernel: [   41.767688] input: Power Button (CM) as /devices/virtual/input/input4
Jul 31 13:45:29 nestor-desktop kernel: [   41.783608] ACPI: Power Button (CM) [PWRB]
Jul 31 13:45:29 nestor-desktop kernel: [   43.813499] input: PC Speaker as /devices/platform/pcspkr/input/input5
Jul 31 13:45:29 nestor-desktop kernel: [   43.874969] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 19
Jul 31 13:45:29 nestor-desktop kernel: [   43.905882] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 20
Jul 31 13:45:29 nestor-desktop kernel: [   45.235925] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Jul 31 13:45:29 nestor-desktop kernel: [   45.267031] parport_pc 00:08: reported by Plug and Play ACPI
Jul 31 13:45:29 nestor-desktop kernel: [   45.267115] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 31 13:45:29 nestor-desktop kernel: [   47.280342] lp0: using parport0 (interrupt-driven).
Jul 31 13:45:29 nestor-desktop kernel: [   47.341100] Adding 4883720k swap on /dev/sdb1.  Priority:-1 extents:1 across:4883720k
Jul 31 13:45:29 nestor-desktop kernel: [   47.904369] EXT3 FS on sdb2, internal journal
Jul 31 13:45:29 nestor-desktop kernel: [   51.174800] kjournald starting.  Commit interval 5 seconds
Jul 31 13:45:29 nestor-desktop kernel: [   51.175241] EXT3 FS on sdb3, internal journal
Jul 31 13:45:29 nestor-desktop kernel: [   51.175247] EXT3-fs: mounted filesystem with ordered data mode.
Jul 31 13:45:29 nestor-desktop kernel: [   51.209399] kjournald starting.  Commit interval 5 seconds
Jul 31 13:45:29 nestor-desktop kernel: [   51.209786] EXT3 FS on sdb4, internal journal
Jul 31 13:45:29 nestor-desktop kernel: [   51.209791] EXT3-fs: mounted filesystem with ordered data mode.
Jul 31 13:45:29 nestor-desktop kernel: [   51.628285] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 31 13:45:29 nestor-desktop kernel: [   52.935781] ppdev: user-space parallel port driver
Jul 31 13:45:29 nestor-desktop kernel: [   53.057376] audit(1249058729.866:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4859 profile="/usr/sbin/cupsd" namespace="default"
Jul 31 13:45:29 nestor-desktop dhcdbd: Started up.
Jul 31 13:45:31 nestor-desktop kernel: [   54.250920] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 31 13:45:32 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 31 13:45:34 nestor-desktop kernel: [   57.371570] NET: Registered protocol family 17
Jul 31 13:45:35 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 31 13:45:35 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 31 13:45:35 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 31 13:45:35 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 31 13:45:36 nestor-desktop kernel: [   59.632991] NET: Registered protocol family 10
Jul 31 13:45:36 nestor-desktop kernel: [   59.633614] lo: Disabled Privacy Extensions
Jul 31 13:45:53 nestor-desktop pulseaudio[5455]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.

CRASH 1********************************************************************************

Jul 30 17:05:16 nestor-desktop kernel: [   31.817290] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Jul 30 17:05:16 nestor-desktop kernel: [   31.817310] sd 2:0:0:0: [sdb] Write Protect is off
Jul 30 17:05:16 nestor-desktop kernel: [   31.817343] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 30 17:05:16 nestor-desktop kernel: [   31.817406] sd 2:0:0:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Jul 30 17:05:16 nestor-desktop kernel: [   31.817423] sd 2:0:0:0: [sdb] Write Protect is off
Jul 30 17:05:16 nestor-desktop kernel: [   31.817453] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 30 17:05:16 nestor-desktop kernel: [   31.817457]  sdb:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 30 17:05:16 nestor-desktop kernel: [   31.823306] Uniform CD-ROM driver Revision: 3.20
Jul 30 17:05:16 nestor-desktop kernel: [   31.825325]  sdb1 sdb2 sdb3 sdb4
Jul 30 17:05:16 nestor-desktop kernel: [   31.825902] sd 2:0:0:0: [sdb] Attached SCSI disk
Jul 30 17:05:16 nestor-desktop kernel: [   31.836991] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 30 17:05:16 nestor-desktop kernel: [   31.837021] sr 0:0:1:0: Attached scsi generic sg1 type 5
Jul 30 17:05:16 nestor-desktop kernel: [   31.837049] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jul 30 17:05:16 nestor-desktop kernel: [   32.235192] Attempting manual resume
Jul 30 17:05:16 nestor-desktop kernel: [   32.255293] EXT3-fs: INFO: recovery required on readonly filesystem.
Jul 30 17:05:16 nestor-desktop kernel: [   32.255300] EXT3-fs: write access will be enabled during recovery.
Jul 30 17:05:16 nestor-desktop kernel: [   35.988339] kjournald starting.  Commit interval 5 seconds
Jul 30 17:05:16 nestor-desktop kernel: [   35.988368] EXT3-fs: sdb2: orphan cleanup on readonly fs
Jul 30 17:05:16 nestor-desktop kernel: [   35.988447] EXT3-fs: sdb2: 3 orphan inodes deleted
Jul 30 17:05:16 nestor-desktop kernel: [   35.988450] EXT3-fs: recovery complete.
Jul 30 17:05:16 nestor-desktop kernel: [   36.041159] EXT3-fs: mounted filesystem with ordered data mode.
Jul 30 17:05:16 nestor-desktop kernel: [   42.263595] Linux agpgart interface v0.102
Jul 30 17:05:16 nestor-desktop kernel: [   42.355514] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 30 17:05:16 nestor-desktop kernel: [   42.393318] agpgart: Detected VIA VT3314 chipset
Jul 30 17:05:16 nestor-desktop kernel: [   42.399602] agpgart: AGP aperture is 64M @ 0xf8000000
Jul 30 17:05:16 nestor-desktop kernel: [   42.439511] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 30 17:05:16 nestor-desktop kernel: [   42.722998] gameport: EMU10K1 is pci0000:00:0a.1/gameport0, io 0xe800, speed 1065kHz
Jul 30 17:05:16 nestor-desktop kernel: [   43.070878] input: Power Button (FF) as /devices/virtual/input/input2
Jul 30 17:05:16 nestor-desktop kernel: [   43.078606] ACPI: Power Button (FF) [PWRF]
Jul 30 17:05:16 nestor-desktop kernel: [   43.078807] input: Sleep Button (CM) as /devices/virtual/input/input3
Jul 30 17:05:16 nestor-desktop kernel: [   43.091549] ACPI: Sleep Button (CM) [SLPB]
Jul 30 17:05:16 nestor-desktop kernel: [   43.091706] input: Power Button (CM) as /devices/virtual/input/input4
Jul 30 17:05:16 nestor-desktop kernel: [   43.106565] ACPI: Power Button (CM) [PWRB]
Jul 30 17:05:16 nestor-desktop kernel: [   45.000854] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 19
Jul 30 17:05:16 nestor-desktop kernel: [   45.189882] input: PC Speaker as /devices/platform/pcspkr/input/input5
Jul 30 17:05:16 nestor-desktop kernel: [   45.218598] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 20
Jul 30 17:05:16 nestor-desktop kernel: [   46.185880] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
Jul 30 17:05:16 nestor-desktop kernel: [   46.214318] parport_pc 00:08: reported by Plug and Play ACPI
Jul 30 17:05:16 nestor-desktop kernel: [   46.214402] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Jul 30 17:05:16 nestor-desktop kernel: [   48.432284] lp0: using parport0 (interrupt-driven).
Jul 30 17:05:16 nestor-desktop kernel: [   48.492911] Adding 4883720k swap on /dev/sdb1.  Priority:-1 extents:1 across:4883720k
Jul 30 17:05:16 nestor-desktop kernel: [   49.056071] EXT3 FS on sdb2, internal journal
Jul 30 17:05:16 nestor-desktop kernel: [   50.786837] kjournald starting.  Commit interval 5 seconds
Jul 30 17:05:16 nestor-desktop kernel: [   50.787274] EXT3 FS on sdb3, internal journal
Jul 30 17:05:16 nestor-desktop kernel: [   50.787281] EXT3-fs: mounted filesystem with ordered data mode.
Jul 30 17:05:16 nestor-desktop kernel: [   50.821434] kjournald starting.  Commit interval 5 seconds
Jul 30 17:05:16 nestor-desktop kernel: [   50.821782] EXT3 FS on sdb4, internal journal
Jul 30 17:05:16 nestor-desktop kernel: [   50.821787] EXT3-fs: mounted filesystem with ordered data mode.
Jul 30 17:05:16 nestor-desktop kernel: [   51.223714] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 30 17:05:16 nestor-desktop kernel: [   51.606406] No dock devices found.
Jul 30 17:05:16 nestor-desktop kernel: [   52.716259] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jul 30 17:05:16 nestor-desktop kernel: [   52.716268] apm: overridden by ACPI.
Jul 30 17:05:16 nestor-desktop kernel: [   52.814144] ppdev: user-space parallel port driver
Jul 30 17:05:16 nestor-desktop kernel: [   52.893821] audit(1248984316.557:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4978 profile="/usr/sbin/cupsd" namespace="default"
Jul 30 17:05:16 nestor-desktop dhcdbd: Started up.
Jul 30 17:05:17 nestor-desktop kernel: [   54.113716] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jul 30 17:05:17 nestor-desktop kernel: [   54.243794] Bluetooth: Core ver 2.11
Jul 30 17:05:17 nestor-desktop kernel: [   54.244696] NET: Registered protocol family 31
Jul 30 17:05:17 nestor-desktop kernel: [   54.244702] Bluetooth: HCI device and connection manager initialized
Jul 30 17:05:17 nestor-desktop kernel: [   54.244708] Bluetooth: HCI socket layer initialized
Jul 30 17:05:17 nestor-desktop kernel: [   54.265924] Bluetooth: L2CAP ver 2.9
Jul 30 17:05:17 nestor-desktop kernel: [   54.265932] Bluetooth: L2CAP socket layer initialized
Jul 30 17:05:17 nestor-desktop kernel: [   54.318452] Bluetooth: RFCOMM socket layer initialized
Jul 30 17:05:17 nestor-desktop kernel: [   54.318770] Bluetooth: RFCOMM TTY layer initialized
Jul 30 17:05:17 nestor-desktop kernel: [   54.318774] Bluetooth: RFCOMM ver 1.8
Jul 30 17:05:18 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 30 17:05:20 nestor-desktop kernel: [   57.232829] NET: Registered protocol family 17
Jul 30 17:05:23 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 30 17:05:23 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 30 17:05:23 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 30 17:05:23 nestor-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 30 17:05:24 nestor-desktop kernel: [   60.754610] NET: Registered protocol family 10
Jul 30 17:05:24 nestor-desktop kernel: [   60.755251] lo: Disabled Privacy Extensions
Jul 30 17:05:58 nestor-desktop pulseaudio[5615]: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.

---

### Post by MaxIBoy on 2009-07-31
Might it be an overheating issue? It could be that Ubuntu's fan-control software doesn't work well with your computer.

Try opening your case and blowing all the dust out, moving the computer to a more-ventilated spot, etc.

---

### Post by stlsaint on 2009-07-31
yea sounds like hardware issues...try on another system!

---

### Post by mike555 on 2009-07-31
Take the side panel off and see if the fans are running on the processor and also the power supply ... fans go , but are cheap to buy new.

---

### Post by MaxIBoy on 2009-08-01
99% of all overheating issues can be prevented if you regularly vacuum out the case to stop dust buildup. Take care of your computers, they will last you years!

---

