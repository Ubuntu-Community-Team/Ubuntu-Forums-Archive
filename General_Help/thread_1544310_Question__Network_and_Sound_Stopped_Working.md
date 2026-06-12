---
title: "Question  Network and Sound Stopped Working"
date: 2010-08-02
forum: General Help
---

### Post by JasonSilver on 2010-08-02
I have posted this in networking, but perhaps it should have been here. Can anyone give me a clue on how to get my networking to work again? I don't care about sound.

> Last night I was trying to get my printer working, and when I rebooted, I lost networking and sound.

I am currently booting on a live CD, and sound and networking are fine-- so it can't be a hardware issue (obviously). I must have inadvertently broken something, but I can't figure it out.

I have tried restarting networking, but it doesn't respond-- it says stop/waiting or something like that.

I can't access the sound preferences-- it says waiting for sound to respond (or something like that).

When I reboot, sometimes I see a terminal window with the same line scrolling very, very quickly-- something about waiting for USB.

Additionally, the system is very slow to respond-- clicking a menu item can take a long time for it to appear, etc.

What could have occurred, and how might I troubleshoot it?

Thanks,
Jason Silver

---

### Post by JasonSilver on 2010-08-02
Some more information.

The systems is so unresponsive because pulseaudio is trying to connect or something.... if I try to kill a pulseaudio process, it says process not found, and there's a new PID for it already... it uses a crazy amount of processor (200% apparently) at times.

If I kill Xorg, I get a stream of messages similar to this:

12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
12312:123123 usb_set_interface failed
... on down the screen ...

lsusb is:
```
ubuntu@ubuntu:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 0461:0a00 Primax Electronics, Ltd Micro Innovations Web Cam 320
Bus 005 Device 004: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 003: ID 046d:c313 Logitech, Inc. 
Bus 005 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0d8d:0105 Promotion & Display Technology, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1307:0163 Transcend Information, Inc. 512MB/1GB Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I'm not sure what's wrong with the networking, I'm trying to connect with wireless, so maybe it's a USB issue as well?

ALSO I tried the previous kernel, and that didn't get me anywhere.

Anyone give me any direction at all? Where should I look next?

Thanks!
Jason

---

### Post by JasonSilver on 2010-08-02
A little bit more information:


```

~$ sudo service networking start
networking stop/waiting

~$ sudo service networking restart
restart: Unknown instance: 

```

```

vi /var/log/user.log

Aug  2 12:13:01 jasonsilver-laptop pulseaudio[11545]: module.c: Failed to load  module "module-console-kit" (argument: ""): initialization failed.
Aug  2 12:13:01 jasonsilver-laptop pulseaudio[11545]: main.c: Module load failed.
Aug  2 12:13:01 jasonsilver-laptop pulseaudio[11545]: main.c: Failed to initialize daemon.
Aug  2 12:13:01 jasonsilver-laptop pulseaudio[11461]: main.c: Daemon startup failed.
Aug  2 12:13:01 jasonsilver-laptop pulseaudio[11588]: module-alsa-card.c: Failed to find a working profile.
Aug  2 12:13:01 jasonsilver-laptop pulseaudio[11588]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-Promotion_and_Display_Technology_Ltd_VoIPvoice_USB_Cyberphone_K-00-K" card_name="alsa_card.usb-Promotion_and_Display_Technology_Ltd_VoIPvoice_USB_Cyberphone_K-00-K" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug  2 12:13:02 jasonsilver-laptop pulseaudio[11588]: module-console-kit.c: GetSessionsForUnixUser() call failed: org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of the setuid helper is not correct
Aug  2 12:13:02 jasonsilver-laptop pulseaudio[11588]: module.c: Failed to load  module "module-console-kit" (argument: ""): initialization failed.
Aug  2 12:13:02 jasonsilver-laptop pulseaudio[11588]: main.c: Module load failed.
Aug  2 12:13:02 jasonsilver-laptop pulseaudio[11588]: main.c: Failed to initialize daemon.
Aug  2 12:13:02 jasonsilver-laptop pulseaudio[11547]: main.c: Daemon startup failed.
Aug  2 12:13:02 jasonsilver-laptop pulseaudio[11631]: module-alsa-card.c: Failed to find a working profile.
Aug  2 12:13:02 jasonsilver-laptop pulseaudio[11631]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-Promotion_and_Display_Technology_Ltd_VoIPvoice_USB_Cyberphone_K-00-K" card_name="alsa_card.usb-Promotion_and_Display_Technology_Ltd_VoIPvoice_USB_Cyberphone_K-00-K" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Aug  2 12:13:03 jasonsilver-laptop pulseaudio[11631]: module-console-kit.c: GetSessionsForUnixUser() call failed: org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of the setuid helper is not correct
Aug  2 12:13:03 jasonsilver-laptop pulseaudio[11631]: module.c: Failed to load  module "module-console-kit" (argument: ""): initialization failed.
Aug  2 12:13:03 jasonsilver-laptop pulseaudio[11631]: main.c: Module load failed.
Aug  2 12:13:03 jasonsilver-laptop pulseaudio[11631]: main.c: Failed to initialize daemon.
Aug  2 12:13:03 jasonsilver-laptop pulseaudio[11589]: main.c: Daemon startup failed.
Aug  2 12:13:03 jasonsilver-laptop pulseaudio[11674]: module-alsa-card.c: Failed to find a working profile.

```

```

vi /var/log/kern.log

Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361053] usb usb4: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361081] hub 4-0:1.0: USB hub found
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361088] hub 4-0:1.0: 2 ports detected
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361144] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361151] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361155] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361193] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361223] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361322] usb usb5: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361353] hub 5-0:1.0: USB hub found
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361360] hub 5-0:1.0: 2 ports detected
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361412] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361419] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361423] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361454] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361493] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361590] usb usb6: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361621] hub 6-0:1.0: USB hub found
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361628] hub 6-0:1.0: 2 ports detected
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361679] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361686] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361690] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361727] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361757] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361857] usb usb7: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361885] hub 7-0:1.0: USB hub found
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361892] hub 7-0:1.0: 2 ports detected
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.361998] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.364470] i8042.c: Detected active multiplexing controller, rev 1.1.
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372158] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372166] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372202] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372227] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372251] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372380] mice: PS/2 mouse device common for all mice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372541] rtc_cmos 00:06: RTC can wake from S4
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372583] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372617] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372734] device-mapper: uevent: version 1.0.3
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.372837] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.402251] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409253] device-mapper: multipath: version 1.1.0 loaded
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409257] device-mapper: multipath round-robin: version 1.0.0 loaded
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409422] EISA: Probing bus 0 at eisa.0
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409430] Cannot allocate resource for EISA slot 1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409434] Cannot allocate resource for EISA slot 2
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409436] Cannot allocate resource for EISA slot 3
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409438] Cannot allocate resource for EISA slot 4
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409441] Cannot allocate resource for EISA slot 5
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.409457] EISA: Detected 0 cards.
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.416361] Freeing initrd memory: 7776k freed
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.421373] cpuidle: using governor ladder
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.421506] cpuidle: using governor menu
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.422062] TCP cubic registered
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.422235] NET: Registered protocol family 10
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.423193] NET: Registered protocol family 17
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.423833] Using IPI No-Shortcut mode
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.423944] PM: Resume from disk failed.
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.423958] registered taskstats version 1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.424630]   Magic number: 6:642:941
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.424735] rtc_cmos 00:06: setting system clock to 2010-08-02 15:55:56 UTC (1280764556)
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.424739] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.424741] EDD information not available.
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.671168] isapnp: No Plug & Play device found
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.671194] Freeing unused kernel memory: 660k freed
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.671695] Write protecting the kernel text: 4680k
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.671755] Write protecting the kernel read-only data: 1840k
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.690008] udev: starting version 151
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.771711] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.771743] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.771809] r8169 0000:03:00.0: setting latency timer to 64
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.771898]   alloc irq_desc for 28 on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.771901]   alloc kstat_irqs on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.771921] r8169 0000:03:00.0: irq 28 for MSI/MSI-X
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.772682] eth0: RTL8101e at 0xf8074000, 00:1e:68:1f:4e:a2, XID 94200000 IRQ 28
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.819487] ahci 0000:00:1f.2: version 3.0
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.819510] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.819565]   alloc irq_desc for 29 on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.819568]   alloc kstat_irqs on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.819581] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.819658] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.819662] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.819669] ahci 0000:00:1f.2: setting latency timer to 64
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.827783] scsi2 : ahci
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.831663] scsi3 : ahci
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.831755] scsi4 : ahci
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.831915] ata3: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704100 irq 29
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.831920] ata4: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704180 irq 29
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.831924] ata5: SATA max UDMA/133 abar m2048@0xf0704000 port 0xf0704200 irq 29
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.833292] ohci1394 0000:0a:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.890097] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f0400000-f04007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Aug  2 11:56:22 jasonsilver-laptop kernel: [    0.996074] usb 4-1: new full speed USB device using uhci_hcd and address 2
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.152062] ata4: SATA link down (SStatus 0 SControl 300)
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.152100] ata5: SATA link down (SStatus 0 SControl 300)
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.419158] usb 4-1: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.432052] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.432763] ACPI Warning for \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.432772] ata3.00: _GTF unexpected object type 0x1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.664073] usb 5-1: new full speed USB device using uhci_hcd and address 2
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.823441] usb 5-1: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.825359] hub 5-1:1.0: USB hub found
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.827284] hub 5-1:1.0: 4 ports detected
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.846561] ata3.00: ATA-8: TOSHIBA MK1246GSX, LB213M, max UDMA/100
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.846568] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.847638] ata3.00: _GTF unexpected object type 0x1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.847878] ata3.00: configured for UDMA/100
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.860251] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK1246GS LB21 PQ: 0 ANSI: 5
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.860428] sd 2:0:0:0: Attached scsi generic sg0 type 0
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.860453] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.860526] sd 2:0:0:0: [sda] Write Protect is off
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.860529] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.860555] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.860695]  sda: sda1 sda2 < sda5 >
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.931799] sd 2:0:0:0: [sda] Attached SCSI disk
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.936339] usbcore: registered new interface driver hiddev
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.949125] input: Promotion and Display Technology Ltd VoIPvoice USB Cyberphone K as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.3/input/input5
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.949249] generic-usb 0003:0D8D:0105.0001: input,hidraw0: USB HID v1.00 Device [Promotion and Display Technology Ltd VoIPvoice USB Cyberphone K] on usb-0000:00:1a.1-1/input3
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.949281] usbcore: registered new interface driver usbhid
Aug  2 11:56:22 jasonsilver-laptop kernel: [    1.949284] usbhid: v2.6:USB HID core driver
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.113302] usb 5-1.1: new low speed USB device using uhci_hcd and address 3
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.164244] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b240000bc78c1]
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.262437] usb 5-1.1: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.280608] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1.1/5-1.1:1.0/input/input6
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.280695] generic-usb 0003:046D:C313.0002: input,hidraw1: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1d.0-1.1/input0
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.294237] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.294242] EXT4-fs (sda1): write access will be enabled during recovery
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.299415] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1.1/5-1.1:1.1/input/input7
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.299530] generic-usb 0003:046D:C313.0003: input,hidraw2: USB HID v1.10 Device [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1d.0-1.1/input1
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.357037] EXT4-fs (sda1): recovery complete
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.357511] EXT4-fs (sda1): mounted filesystem with ordered data mode
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.373294] usb 5-1.2: new low speed USB device using uhci_hcd and address 4
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.507463] usb 5-1.2: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.522609] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1.2/5-1.2:1.0/input/input8
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.522698] generic-usb 0003:046D:C018.0004: input,hidraw3: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-1.2/input0
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.597317] usb 5-1.4: new full speed USB device using uhci_hcd and address 5
Aug  2 11:56:22 jasonsilver-laptop kernel: [    2.742442] usb 5-1.4: configuration #1 chosen from 1 choice
Aug  2 11:56:22 jasonsilver-laptop kernel: [   14.349113] udev: starting version 151
Aug  2 11:56:22 jasonsilver-laptop kernel: [   14.383895] Adding 4805624k swap on /dev/sda5.  Priority:-1 extents:1 across:4805624k
Aug  2 11:56:22 jasonsilver-laptop kernel: [   14.817536] lp: driver loaded but no devices found
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.016710] Linux agpgart interface v0.103
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.038656] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.039274] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.044684] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.091789] type=1505 audit(1280764571.163:2):  operation="profile_load" pid=679 name="/sbin/dhclient3"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.092589] type=1505 audit(1280764571.167:3):  operation="profile_load" pid=679 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.092993] type=1505 audit(1280764571.167:4):  operation="profile_load" pid=679 name="/usr/lib/connman/scripts/dhclient-script"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.146673] [drm] Initialized drm 1.1.0 20060810
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.259907] cfg80211: Calling CRDA to update world regulatory domain
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.264284] ricoh-mmc: Ricoh MMC Controller disabling driver
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.264287] ricoh-mmc: Copyright(c) Philip Langdale
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.264318] ricoh-mmc: Ricoh MMC controller found at 0000:0a:01.2 [1180:0843] (rev 12)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.264338] ricoh-mmc: Controller is now disabled.
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.270306] Linux video capture interface: v2.00
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.271879] sdhci: Secure Digital Host Controller Interface driver
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.271882] sdhci: Copyright(c) Pierre Ossman
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.289685] cfg80211: World regulatory domain updated:
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.289689]       (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.289692]       (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.289695]       (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.289698]       (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.289701]       (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.289704]       (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.308336] sdhci-pci 0000:0a:01.1: SDHCI controller found [1180:0822] (rev 22)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.308358] sdhci-pci 0000:0a:01.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.309399] sdhci-pci 0000:0a:01.1: Will use DMA mode even though HW doesn't fully claim to support it.
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.310479] Registered led device: mmc0::
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.311561] mmc0: SDHCI controller on PCI [0000:0a:01.1] using DMA
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.314098] gspca: main v2.7.0 registered
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.511714] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.511720] i915 0000:00:02.0: setting latency timer to 64
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.511975] gspca: probing 0461:0a00
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.517161]   alloc irq_desc for 30 on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.517165]   alloc kstat_irqs on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.517175] i915 0000:00:02.0: irq 30 for MSI/MSI-X
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.517183] [drm] set up 7M of stolen space
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.644468] [drm] initialized overlay support
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.665802] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x81c0b1, caps: 0xa04711/0xa00000
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.665810] synaptics: Toshiba Satellite Pro U300 detected, limiting rate to 40pps.
Aug  2 11:56:22 jasonsilver-laptop kernel: [   15.699700] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.204048] fb0: inteldrmfb frame buffer device
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.204052] registered panic notifier
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.212605] acpi device:02: registered as cooling_device2
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.213382] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.213509] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.213770] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.401168] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.401172] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.401246] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.401256] iwlagn 0000:04:00.0: setting latency timer to 64
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.401287] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.406784] vga16fb: initializing
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.406788] vga16fb: mapped to 0xc00a0000
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.406792] vga16fb: not registering due to another framebuffer present
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.444858] iwlagn 0000:04:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.444927]   alloc irq_desc for 31 on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.444930]   alloc kstat_irqs on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.444952] iwlagn 0000:04:00.0: irq 31 for MSI/MSI-X
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.717892] phy0: Selected rate control algorithm 'iwl-agn-rs'
Aug  2 11:56:22 jasonsilver-laptop kernel: [   16.905663] Console: switching to colour frame buffer device 160x50
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.007170]   alloc irq_desc for 22 on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.007173]   alloc kstat_irqs on node -1
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.007181] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.007374] HDA Intel 0000:00:1b.0: setting latency timer to 64
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.141662] hda_codec: ALC268: BIOS auto-probing.
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.141957] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.379303] zc3xx: probe 2wr ov vga 0x0000
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.498308] zc3xx: probe 3wr vga 1 0x0000
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.711280] zc3xx: probe 3wr vga 2 0x0000
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.756308] zc3xx: Sensor UNKNOW_0 force Tas5130
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.760361] gspca: probe ok
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.778678] usbcore: registered new interface driver snd-usb-audio
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.778694] usbcore: registered new interface driver zc3xx
Aug  2 11:56:22 jasonsilver-laptop kernel: [   17.778698] zc3xx: registered
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.480794] type=1505 audit(1280764582.555:5):  operation="profile_load" pid=929 name="/usr/share/gdm/guest-session/Xsession"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.483285] type=1505 audit(1280764582.555:6):  operation="profile_replace" pid=931 name="/sbin/dhclient3"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.484130] type=1505 audit(1280764582.559:7):  operation="profile_replace" pid=931 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.484542] type=1505 audit(1280764582.559:8):  operation="profile_replace" pid=931 name="/usr/lib/connman/scripts/dhclient-script"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.492291] type=1505 audit(1280764582.567:9):  operation="profile_load" pid=933 name="/usr/bin/evince"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.504170] r8169: eth0: link down
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.505197] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.514870] type=1505 audit(1280764582.587:10):  operation="profile_load" pid=933 name="/usr/bin/evince-previewer"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.518254] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-4965-2.ucode
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.523259] type=1505 audit(1280764582.595:11):  operation="profile_load" pid=933 name="/usr/bin/evince-thumbnailer"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.527349] iwlagn 0000:04:00.0: loaded firmware version 228.61.2.24
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.534226] type=1505 audit(1280764582.607:12):  operation="profile_load" pid=943 name="/usr/lib/cups/backend/cups-pdf"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.535125] type=1505 audit(1280764582.607:13):  operation="profile_load" pid=943 name="/usr/sbin/cupsd"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.537930] type=1505 audit(1280764582.611:14):  operation="profile_load" pid=944 name="/usr/sbin/tcpdump"
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.765448] vboxdrv: Trying to deactivate the NMI watchdog permanently...
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.765451] vboxdrv: Successfully done.
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.765454] vboxdrv: Found 2 processor cores.
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.765539] vboxdrv: fAsync=0 offMin=0x1a2 offMax=0x6a9
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.765586] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.765588] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.893225] Registered led device: iwl-phy0::radio
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.893251] Registered led device: iwl-phy0::assoc
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.893269] Registered led device: iwl-phy0::RX
Aug  2 11:56:22 jasonsilver-laptop kernel: [   26.893286] Registered led device: iwl-phy0::TX
Aug  2 11:56:23 jasonsilver-laptop kernel: [   27.141124] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  2 11:56:23 jasonsilver-laptop kernel: [   27.190511] ppdev: user-space parallel port driver
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.518128] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.520405] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.521055] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.522065] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.523057] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.525037] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.526060] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.527041] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.528067] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.529042] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.531062] 2:2:4: usb_set_interface failed
Aug  2 11:59:10 jasonsilver-laptop kernel: [  194.532071] 2:2:4: usb_set_interface failed

```

---

### Post by JasonSilver on 2010-08-02
Is there a reason this isn't getting any replies? Am I missing something obvious? Or is that I haven't described the problem accurately enough?

Jason

---

### Post by JasonSilver on 2010-08-03
bump??

---

### Post by JasonSilver on 2010-08-05
bump

---

