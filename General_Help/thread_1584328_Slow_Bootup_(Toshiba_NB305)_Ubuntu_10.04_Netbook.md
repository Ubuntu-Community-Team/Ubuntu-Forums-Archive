---
title: "Slow Bootup (Toshiba NB305) Ubuntu 10.04 Netbook"
date: 2010-09-29
forum: General Help
---

### Post by Mick671 on 2010-09-29
After running Ubuntu Netbook off a USB for a while, I decided to format completely and install Ubuntu as the main OS. Except now the bootup is incredibly slow. Once I start the computer it goes to a black screen that resembles the Terminal. I have to wait 5-10 mins to get it completely booted up. Again, if I run it off the Ubuntu USB over the installed Ubuntu, the USB one is much faster. Common problem?

---

### Post by P4man on 2010-09-29
Doesnt sound very common to me.
Can you post the output of 

```
dmesg
```

Also bootchart could be useful to find out whats taking so long. Its very easy to use. See here:
[http://ubuntuforums.org/showthread.php?t=868189](http://ubuntuforums.org/showthread.php?t=868189)

---

### Post by Mick671 on 2010-10-04
Voila! Sorry for the late reply, college just ramped up. Also I will give that boot program a whirl and see what it comes up with.







[    0.475113] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.475367] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.475423]   alloc irq_desc for 23 on node -1
[    0.475430]   alloc kstat_irqs on node -1
[    0.475447] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.475483] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.475492] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.475603] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.475643] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.475662] ehci_hcd 0000:00:1d.7: debug port 1
[    0.479564] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.479633] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x40a04000
[    0.483572] isapnp: Scanning for PnP cards...
[    0.517051] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.517349] usb usb1: configuration #1 chosen from 1 choice
[    0.517434] hub 1-0:1.0: USB hub found
[    0.517459] hub 1-0:1.0: 8 ports detected
[    0.517622] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.517665] uhci_hcd: USB Universal Host Controller Interface driver
[    0.517746] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.517762] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.517770] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.517871] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.517917] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.518154] usb usb2: configuration #1 chosen from 1 choice
[    0.518235] hub 2-0:1.0: USB hub found
[    0.518254] hub 2-0:1.0: 2 ports detected
[    0.518371]   alloc irq_desc for 19 on node -1
[    0.518377]   alloc kstat_irqs on node -1
[    0.518392] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.518406] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.518414] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.518517] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.518570] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.518796] usb usb3: configuration #1 chosen from 1 choice
[    0.518875] hub 3-0:1.0: USB hub found
[    0.518892] hub 3-0:1.0: 2 ports detected
[    0.518998] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.519012] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.519020] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.519103] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.519154] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.519389] usb usb4: configuration #1 chosen from 1 choice
[    0.519464] hub 4-0:1.0: USB hub found
[    0.519482] hub 4-0:1.0: 2 ports detected
[    0.519584] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.519598] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.519606] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.519694] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.519744] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.519973] usb usb5: configuration #1 chosen from 1 choice
[    0.520050] hub 5-0:1.0: USB hub found
[    0.520068] hub 5-0:1.0: 2 ports detected
[    0.520282] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.601363] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.601388] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.601663] mice: PS/2 mouse device common for all mice
[    0.601974] rtc_cmos 00:04: RTC can wake from S4
[    0.602069] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.602112] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.602418] device-mapper: uevent: version 1.0.3
[    0.609602] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.629150] device-mapper: multipath: version 1.1.0 loaded
[    0.629160] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.629540] EISA: Probing bus 0 at eisa.0
[    0.629553] Cannot allocate resource for EISA slot 1
[    0.629560] Cannot allocate resource for EISA slot 2
[    0.629566] Cannot allocate resource for EISA slot 3
[    0.629573] Cannot allocate resource for EISA slot 4
[    0.629597] EISA: Detected 0 cards.
[    0.641505] cpuidle: using governor ladder
[    0.641804] cpuidle: using governor menu
[    0.643032] TCP cubic registered
[    0.643498] NET: Registered protocol family 10
[    0.644722] lo: Disabled Privacy Extensions
[    0.645622] NET: Registered protocol family 17
[    0.646754] Using IPI No-Shortcut mode
[    0.646984] PM: Resume from disk failed.
[    0.647015] registered taskstats version 1
[    0.647677]   Magic number: 14:691:145
[    0.647743] acpi device:16: hash matches
[    0.647812] rtc_cmos 00:04: setting system clock to 2010-10-05 21:07:51 UTC (1286312871)
[    0.647821] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.647826] EDD information not available.
[    0.668310] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.704732] Freeing initrd memory: 7771k freed
[    0.836045] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.837962] isapnp: No Plug & Play device found
[    0.837992] Freeing unused kernel memory: 656k freed
[    0.838549] Write protecting the kernel text: 4676k
[    0.838620] Write protecting the kernel read-only data: 1840k
[    0.848648] ACPI: Battery Slot [BAT1] (battery present)
[    0.875334] udev: starting version 151
[    0.982129] usb 1-4: configuration #1 chosen from 1 choice
[    1.101099] usb 1-8: new high speed USB device using ehci_hcd and address 3
[    1.173430] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.173486] r8169 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.173592] r8169 0000:09:00.0: setting latency timer to 64
[    1.173746]   alloc irq_desc for 27 on node -1
[    1.173753]   alloc kstat_irqs on node -1
[    1.173798] r8169 0000:09:00.0: irq 27 for MSI/MSI-X
[    1.175604] eth0: RTL8102e at 0xf805e000, 00:26:22:f6:65:24, XID 04e00000 IRQ 27
[    1.179087] ahci 0000:00:1f.2: version 3.0
[    1.179119] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.179190]   alloc irq_desc for 28 on node -1
[    1.179197]   alloc kstat_irqs on node -1
[    1.179222] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    1.179454] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.179468] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.179480] ahci 0000:00:1f.2: setting latency timer to 64
[    1.180084] scsi0 : ahci
[    1.201357] scsi1 : ahci
[    1.201788] Initializing USB Mass Storage driver...
[    1.202068] scsi3 : SCSI emulation for USB Mass Storage devices
[    1.202352] usbcore: registered new interface driver usb-storage
[    1.202363] USB Mass Storage support registered.
[    1.202678] usb-storage: device found at 2
[    1.202686] usb-storage: waiting for device to settle before scanning
[    1.202737] scsi2 : ahci
[    1.203363] scsi4 : ahci
[    1.203804] ata1: SATA max UDMA/133 abar m1024@0x40a04400 port 0x40a04500 irq 28
[    1.203816] ata2: SATA max UDMA/133 abar m1024@0x40a04400 port 0x40a04580 irq 28
[    1.203826] ata3: SATA max UDMA/133 abar m1024@0x40a04400 port 0x40a04600 irq 28
[    1.203836] ata4: SATA max UDMA/133 abar m1024@0x40a04400 port 0x40a04680 irq 28
[    1.260511] usb 1-8: configuration #1 chosen from 1 choice
[    1.524085] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.524132] ata4: SATA link down (SStatus 0 SControl 300)
[    1.524159] ata2: SATA link down (SStatus 0 SControl 300)
[    1.524183] ata3: SATA link down (SStatus 0 SControl 300)
[    1.640146] ata1.00: ATA-8: TOSHIBA MK2555GSX, FG001M, max UDMA/100
[    1.640154] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.892173] ata1.00: configured for UDMA/100
[    1.908354] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    1.908727] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.909053] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.909238] sd 0:0:0:0: [sda] Write Protect is off
[    1.909246] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.909316] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.909682]  sda: sda1 sda2 < sda5 >
[    2.805345] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.200586] usb-storage: device scan complete
[    6.203291] scsi 3:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.205182] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    6.211376] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   10.857651] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[   10.857661] EXT4-fs (sda1): write access will be enabled during recovery
[   48.660177] EXT4-fs (sda1): orphan cleanup on readonly fs
[   48.660202] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2621496
[   48.660321] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2621498
[   48.660343] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2621497
[   48.660367] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10485931
[   48.660446] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10485890
[   48.660528] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10485875
[   48.660571] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 10485872
[   48.660606] EXT4-fs (sda1): 7 orphan inodes deleted
[   48.660614] EXT4-fs (sda1): recovery complete
[   49.318170] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   71.607311] udev: starting version 151
[   71.660660] Adding 2975736k swap on /dev/sda5.  Priority:-1 extents:1 across:2975736k 
[   71.731337] lp: driver loaded but no devices found
[   72.112262] Linux agpgart interface v0.103
[   72.252457] agpgart-intel 0000:00:00.0: Intel IGD Chipset
[   72.252766] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[   72.328208] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   72.416383] [drm] Initialized drm 1.1.0 20060810
[   72.508870] cfg80211: Calling CRDA to update world regulatory domain
[   72.513697] Linux video capture interface: v2.00
[   72.561408] cfg80211: World regulatory domain updated:
[   72.561418]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   72.561429]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   72.561438]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   72.561446]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   72.561455]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   72.561464]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   72.602006] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b15d)
[   72.642312] input: Chicony USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input5
[   72.642472] usbcore: registered new interface driver uvcvideo
[   72.642485] USB Video Class driver (v0.1.0)
[   72.682221] type=1505 audit(1286276943.532:2):  operation="profile_load" pid=601 name="/sbin/dhclient3"
[   72.682979] type=1505 audit(1286276943.532:3):  operation="profile_load" pid=601 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   72.683415] type=1505 audit(1286276943.532:4):  operation="profile_load" pid=601 name="/usr/lib/connman/scripts/dhclient-script"
[   72.697588] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   72.697647] ath9k 0000:07:00.0: setting latency timer to 64
[   72.747471] ath: EEPROM regdomain: 0x65
[   72.747479] ath: EEPROM indicates we should expect a direct regpair map
[   72.747489] ath: Country alpha2 being used: 00
[   72.747495] ath: Regpair used: 0x65
[   72.791157] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   72.791172] i915 0000:00:02.0: setting latency timer to 64
[   72.817337]   alloc irq_desc for 29 on node -1
[   72.817347]   alloc kstat_irqs on node -1
[   72.817366] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[   72.817381] [drm] set up 7M of stolen space
[   72.839835] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   72.841805] Registered led device: ath9k-phy0::radio
[   72.841860] Registered led device: ath9k-phy0::assoc
[   72.841907] Registered led device: ath9k-phy0::tx
[   72.841955] Registered led device: ath9k-phy0::rx
[   72.842001] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8780000, irq=17
[   72.960938] [drm] initialized overlay support
[   73.505696] fb0: inteldrmfb frame buffer device
[   73.505704] registered panic notifier
[   73.505746] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   73.505939]   alloc irq_desc for 22 on node -1
[   73.505947]   alloc kstat_irqs on node -1
[   73.505965] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   73.506031] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   73.517201] vga16fb: initializing
[   73.517213] vga16fb: mapped to 0xc00a0000
[   73.517224] vga16fb: not registering due to another framebuffer present
[   73.557515] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   73.576680] r8169: eth0: link down
[   73.578697] [drm] Big FIFO is enabled
[   73.579288] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.613378] type=1505 audit(1286276944.464:5):  operation="profile_replace" pid=742 name="/sbin/dhclient3"
[   73.614129] type=1505 audit(1286276944.464:6):  operation="profile_replace" pid=742 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   73.614562] type=1505 audit(1286276944.464:7):  operation="profile_replace" pid=742 name="/usr/lib/connman/scripts/dhclient-script"
[   73.631755] type=1505 audit(1286276944.480:8):  operation="profile_load" pid=746 name="/usr/bin/evince"
[   73.654680] type=1505 audit(1286276944.504:9):  operation="profile_load" pid=746 name="/usr/bin/evince-previewer"
[   73.667594] type=1505 audit(1286276944.516:10):  operation="profile_load" pid=746 name="/usr/bin/evince-thumbnailer"
[   73.671866] [drm] Big FIFO is enabled
[   73.671887] [drm] Big FIFO is enabled
[   73.688775] [drm] Big FIFO is enabled
[   73.689822] hda_codec: ALC272: BIOS auto-probing.
[   73.691620] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   73.702948] type=1505 audit(1286276944.552:11):  operation="profile_load" pid=751 name="/usr/lib/cups/backend/cups-pdf"
[   73.716207] [drm] Big FIFO is enabled
[   73.724111] Console: switching to colour frame buffer device 128x37
[   73.740335] [drm] Big FIFO is enabled
[   74.076970] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   74.214706] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   74.599448] ppdev: user-space parallel port driver
[   75.503336] CPU0 attaching NULL sched-domain.
[   75.503348] CPU1 attaching NULL sched-domain.
[   75.524208] CPU0 attaching sched-domain:
[   75.524216]  domain 0: span 0-1 level SIBLING
[   75.524223]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   75.524236]   domain 1: span 0-1 level MC
[   75.524241]    groups: 0-1 (cpu_power = 1178)
[   75.524252] CPU1 attaching sched-domain:
[   75.524256]  domain 0: span 0-1 level SIBLING
[   75.524262]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   75.524273]   domain 1: span 0-1 level MC
[   75.524278]    groups: 0-1 (cpu_power = 1178)
[   78.019102] CPU0 attaching NULL sched-domain.
[   78.019114] CPU1 attaching NULL sched-domain.
[   78.040150] CPU0 attaching sched-domain:
[   78.040159]  domain 0: span 0-1 level SIBLING
[   78.040165]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   78.040177]   domain 1: span 0-1 level MC
[   78.040183]    groups: 0-1 (cpu_power = 1178)
[   78.040193] CPU1 attaching sched-domain:
[   78.040198]  domain 0: span 0-1 level SIBLING
[   78.040203]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   78.040214]   domain 1: span 0-1 level MC
[   78.040219]    groups: 0-1 (cpu_power = 1178)
[   95.160532] wlan0: direct probe to AP 00:14:f2:03:e7:c0 (try 1)
[   95.160606] wlan0: deauthenticating from 00:14:f2:03:e7:c0 by local choice (reason=3)
[   95.160678] wlan0: direct probe to AP 00:14:f2:03:e7:c0 (try 1)
[   95.165462] wlan0: direct probe responded
[   95.165476] wlan0: authenticate with AP 00:14:f2:03:e7:c0 (try 1)
[   95.168816] wlan0: authenticated
[   95.168871] wlan0: associate with AP 00:14:f2:03:e7:c0 (try 1)
[   95.170991] wlan0: RX AssocResp from 00:14:f2:03:e7:c0 (capab=0x421 status=0 aid=246)
[   95.171002] wlan0: associated
[   95.171819] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
star@star-laptop:~$

---

### Post by K7522 on 2010-10-04
I have seen this as well with the NB205, even hangs when returning from hibernate.

---

### Post by Agent Smith on 2010-10-05
This also happens with NB200 series as well. Boot into the BIOS then change the SATA Controller Mode to "compatibility" instead of AHCI. Hope this helps.

---

### Post by JamesScullin on 2010-10-07
Changing the bios sata to compatibility works on nb305

---

### Post by cilynx on 2010-10-07
It has to be something weird with interrupts.  If you watch the hard drive light, it generally stays off.  If you press a key, it will blink.  If you hold a key (like shift, to be safe), the hard drive light blinks with activity as expected and everything proceeds at normal speed.  Wiggling the mouse works as well so long as you're booted far enough that the mouse has been enabled. 

My guess is that something with AHCI is handing off control of the CPU and blocking disk access until something CPU related happens.  Once another interrupts goes through, AHCI picks back up until its next programmed hand-off and the cycle repeats.

The same trick (holding shift) works fine to resurrect from comatose hibernation.

All that said, switching the SATA controller over to Compatibility mode solved the issues on my NB205.

---

### Post by Old_Grey_Wolf on 2010-10-07
> **Mick671 said:**
> After running Ubuntu Netbook off a USB for a while, I decided to format completely and install Ubuntu as the main OS. Except now the bootup is incredibly slow. Once I start the computer it goes to a black screen that resembles the Terminal. I have to wait 5-10 mins to get it completely booted up. Again, if I run it off the Ubuntu USB over the installed Ubuntu, the USB one is much faster. Common problem?

I can't help you with Ubuntu; however, I'm running Linux Mint 9 Isadora (a derivative of Ubuntu 10.04) as a dual boot on my Toshiba NB305. It boots very fast. You may want to try Linux Mint 9 Isadora. The NB305 display was large enough that I didn't think about installing a Netbook version of Ubuntu. :)

---

