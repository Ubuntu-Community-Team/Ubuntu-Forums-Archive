---
title: "Ubuntu 11.04 takes too long to boot up [DRDY ERR]"
date: 2011-09-16
forum: General Help
---

### Post by NedNguyen on 2011-09-16
Hi all, 
Suddenly, my Ubuntu 11.04 (2.6.38-11-generic) takes very long to boot up. I swear that I did not install anything to make this happen. 

Here is my dmseg:

```
2 (level, low) -> IRQ 22
[    1.124532] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.124535] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.124566] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.124609] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.124724] hub 7-0:1.0: USB hub found
[    1.124728] hub 7-0:1.0: 2 ports detected
[    1.124852] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.138003] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.138007] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.138116] mousedev: PS/2 mouse device common for all mice
[    1.138671] rtc_cmos 00:04: RTC can wake from S4
[    1.138731] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.138763] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.138834] device-mapper: uevent: version 1.0.3
[    1.138907] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    1.138966] device-mapper: multipath: version 1.2.0 loaded
[    1.138969] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.139039] EISA: Probing bus 0 at eisa.0
[    1.139042] EISA: Cannot allocate resource for mainboard
[    1.139043] Cannot allocate resource for EISA slot 1
[    1.139045] Cannot allocate resource for EISA slot 2
[    1.139046] Cannot allocate resource for EISA slot 3
[    1.139048] Cannot allocate resource for EISA slot 4
[    1.139050] Cannot allocate resource for EISA slot 5
[    1.139051] Cannot allocate resource for EISA slot 6
[    1.139053] Cannot allocate resource for EISA slot 7
[    1.139054] Cannot allocate resource for EISA slot 8
[    1.139055] EISA: Detected 0 cards.
[    1.139165] cpuidle: using governor ladder
[    1.139254] cpuidle: using governor menu
[    1.139512] TCP cubic registered
[    1.139633] NET: Registered protocol family 10
[    1.140172] NET: Registered protocol family 17
[    1.140187] Registering the dns_resolver key type
[    1.141104] Using IPI No-Shortcut mode
[    1.141185] PM: Hibernation image not present or could not be loaded.
[    1.141195] registered taskstats version 1
[    1.141567]   Magic number: 11:432:719
[    1.141669] rtc_cmos 00:04: setting system clock to 2011-09-16 05:44:54 UTC (1316151894)
[    1.141671] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.141673] EDD information not available.
[    1.162060] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.244630] ata1.00: ATAPI: MATSHITA DVD+/-RW UJ-875S, D200, max UDMA/33
[    1.260506] ata1.00: configured for UDMA/33
[    1.263053] scsi 0:0:0:0: CD-ROM            MATSHITA DVD+-RW UJ-875S  D200 PQ: 0 ANSI: 5
[    1.265560] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.265565] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.265716] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.265766] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.265897] Freeing unused kernel memory: 700k freed
[    1.266263] Write protecting the kernel text: 5192k
[    1.266345] Write protecting the kernel read-only data: 2148k
[    1.296532] <30>udev[87]: starting version 167
[    1.390083] sky2: driver version 1.28
[    1.390120] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.390134] sky2 0000:09:00.0: setting latency timer to 64
[    1.390165] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    1.390293] sky2 0000:09:00.0: irq 44 for MSI/MSI-X
[    1.390721] sdhci: Secure Digital Host Controller Interface driver
[    1.390723] sdhci: Copyright(c) Pierre Ossman
[    1.392209] sky2 0000:09:00.0: eth0: addr 00:21:9b:ea:dc:a5
[    1.393817] firewire_ohci 0000:03:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.396785] ahci 0000:00:1f.2: version 3.0
[    1.396793] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.396834] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.396904] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.396907] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    1.396912] ahci 0000:00:1f.2: setting latency timer to 64
[    1.407551] scsi2 : ahci
[    1.407736] scsi3 : ahci
[    1.410349] scsi4 : ahci
[    1.410503] ata3: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb900 irq 45
[    1.410505] ata4: DUMMY
[    1.410507] ata5: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffba00 irq 45
[    1.412034] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.456157] firewire_ohci: Added fw-ohci device 0000:03:09.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.456240] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 22)
[    1.456260] sdhci-pci 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.457286] mmc0: no vmmc regulator found
[    1.458304] Registered led device: mmc0::
[    1.459337] mmc0: SDHCI controller on PCI [0000:03:09.1] using DMA
[    1.728121] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.728838] ata3.00: ATA-8: ST9250827AS, 3.ADB, max UDMA/133
[    1.728843] ata3.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.729314] ata3.00: configured for UDMA/133
[    1.729515] scsi 2:0:0:0: Direct-Access     ATA      ST9250827AS      3.AD PQ: 0 ANSI: 5
[    1.729660] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.729669] sd 2:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.729720] sd 2:0:0:0: [sda] Write Protect is off
[    1.729723] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.729742] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.732103] ata5: SATA link down (SStatus 0 SControl 300)
[    1.863527]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    1.864020] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.956174] firewire_core: created device fw0: GUID 464fc000166bd9e1, S400
[    2.132052] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.544044] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    2.721734] hub 7-2:1.0: USB hub found
[    2.723663] hub 7-2:1.0: 3 ports detected
[    2.960994] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.968127] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    3.225682] usb 7-2.1: new full speed USB device using uhci_hcd and address 3
[    3.429683] usb 7-2.2: new full speed USB device using uhci_hcd and address 4
[    3.637683] usb 7-2.3: new full speed USB device using uhci_hcd and address 5
[    4.659416] Adding 1998844k swap on /dev/sda7.  Priority:-1 extents:1 across:1998844k 
[    5.484834] <30>udev[327]: starting version 167
[    7.268099] acpi device:31: registered as cooling_device2
[    7.268564] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input4
[    7.268654] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    7.523874] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    7.568324] input: Dell WMI hotkeys as /devices/virtual/input/input5
[    7.645159] Bluetooth: Core ver 2.15
[    7.645199] NET: Registered protocol family 31
[    7.645201] Bluetooth: HCI device and connection manager initialized
[    7.645203] Bluetooth: HCI socket layer initialized
[    7.657515] cfg80211: Calling CRDA to update world regulatory domain
[    7.726261] type=1400 audit(1316177101.081:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=535 comm="apparmor_parser"
[    7.726269] type=1400 audit(1316177101.081:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=534 comm="apparmor_parser"
[    7.727018] type=1400 audit(1316177101.081:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=535 comm="apparmor_parser"
[    7.727028] type=1400 audit(1316177101.081:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=534 comm="apparmor_parser"
[    7.727493] type=1400 audit(1316177101.081:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=535 comm="apparmor_parser"
[    7.727507] type=1400 audit(1316177101.081:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=534 comm="apparmor_parser"
[    7.741052] lp: driver loaded but no devices found
[    7.763571] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    7.765870] usbcore: registered new interface driver btusb
[    7.795897] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input6
[    7.796178] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    7.801529] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input7
[    7.802103] generic-usb 0003:046D:C526.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    7.824152] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input8
[    7.824726] generic-usb 0003:0A5C:4502.0003: input,hidraw2: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2/input0
[    7.830313] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input9
[    7.830414] generic-usb 0003:0A5C:4503.0004: input,hidraw3: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3/input0
[    7.830428] usbcore: registered new interface driver usbhid
[    7.830430] usbhid: USB HID core driver
[    7.921719] Linux video capture interface: v2.00
[    8.085404] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
[    8.112200] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[    8.218862] r852 0000:03:09.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    8.218928] r852: driver loaded succesfully
[    8.368846] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    8.369209] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[    8.369884] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input12
[    8.369954] usbcore: registered new interface driver uvcvideo
[    8.369956] USB Video Class driver (v1.0.0)
[    8.745831] cfg80211: World regulatory domain updated:
[    8.745833] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.745836] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.745838] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.745840] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.745843] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.745845] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.902048] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    8.902051] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    8.902144] iwlagn 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.902153] iwlagn 0000:0b:00.0: setting latency timer to 64
[    8.902181] iwlagn 0000:0b:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[    8.941298] iwlagn 0000:0b:00.0: device EEPROM VER=0x36, CALIB=0x5
[    8.941300] iwlagn 0000:0b:00.0: Device SKU: 0Xb
[    8.941331] iwlagn 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    8.941411] iwlagn 0000:0b:00.0: irq 46 for MSI/MSI-X
[    9.135516] iwlagn 0000:0b:00.0: loaded firmware version 228.61.2.24
[    9.135691] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    9.293299] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.293363] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    9.293394] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.448948] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    9.644178] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    9.644311] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    9.644418] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   11.164342] nvidia: module license 'NVIDIA' taints kernel.
[   11.164348] Disabling lock debugging due to kernel taint
[   12.125405] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.125415] nvidia 0000:01:00.0: setting latency timer to 64
[   12.125420] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.125546] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   12.178143] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   12.272162] vesafb: framebuffer at 0xf3000000, mapped to 0xf8380000, using 9024k, total 9024k
[   12.272165] vesafb: mode is 1920x1200x32, linelength=7680, pages=0
[   12.272167] vesafb: scrolling: redraw
[   12.272169] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   12.272376] Console: switching to colour frame buffer device 240x75
[   12.272426] fb0: VESA VGA frame buffer device
[   14.042545] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   16.647818] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   17.683103] type=1400 audit(1316177111.037:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=890 comm="apparmor_parser"
[   17.683866] type=1400 audit(1316177111.037:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=890 comm="apparmor_parser"
[   17.684377] type=1400 audit(1316177111.041:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=890 comm="apparmor_parser"
[   17.775693] type=1400 audit(1316177111.129:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=889 comm="apparmor_parser"
[   17.855297] type=1400 audit(1316177111.209:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=900 comm="apparmor_parser"
[   17.856225] type=1400 audit(1316177111.213:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=900 comm="apparmor_parser"
[   17.917383] type=1400 audit(1316177111.273:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=901 comm="apparmor_parser"
[   18.078818] type=1400 audit(1316177111.433:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=891 comm="apparmor_parser"
[   18.088443] type=1400 audit(1316177111.445:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=891 comm="apparmor_parser"
[   18.094341] type=1400 audit(1316177111.449:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=891 comm="apparmor_parser"
[   18.408060] ppdev: user-space parallel port driver
[   21.035114] sky2 0000:09:00.0: eth0: enabling interface
[   21.035338] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.276611] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.989415] Bluetooth: L2CAP ver 2.15
[   25.989417] Bluetooth: L2CAP socket layer initialized
[   26.118548] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.118551] Bluetooth: BNEP filters: protocol multicast
[   26.319829] Bluetooth: SCO (Voice Link) ver 0.6
[   26.319831] Bluetooth: SCO socket layer initialized
[   26.511672] Bluetooth: RFCOMM TTY layer initialized
[   26.511676] Bluetooth: RFCOMM socket layer initialized
[   26.511677] Bluetooth: RFCOMM ver 1.11
[   30.606212] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   30.606219] ata3.00: irq_stat 0x40000008
[   30.606225] ata3.00: failed command: READ FPDMA QUEUED
[   30.606235] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[   30.606237]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   30.606242] ata3.00: status: { DRDY ERR }
[   30.606246] ata3.00: error: { UNC }
[   30.610566] ata3.00: configured for UDMA/133
[   30.610578] ata3: EH complete
[   34.730701] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   34.730707] ata3.00: irq_stat 0x40000008
[   34.730712] ata3.00: failed command: READ FPDMA QUEUED
[   34.730723] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   34.730725]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   34.730730] ata3.00: status: { DRDY ERR }
[   34.730733] ata3.00: error: { UNC }
[   34.735020] ata3.00: configured for UDMA/133
[   34.735033] ata3: EH complete
[   37.203107] ata3.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[   37.203113] ata3.00: irq_stat 0x40000008
[   37.203118] ata3.00: failed command: READ FPDMA QUEUED
[   37.203129] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[   37.203131]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   37.203136] ata3.00: status: { DRDY ERR }
[   37.203139] ata3.00: error: { UNC }
[   37.207430] ata3.00: configured for UDMA/133
[   37.207441] ata3: EH complete
[   39.642300] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   39.642306] ata3.00: irq_stat 0x40000008
[   39.642311] ata3.00: failed command: READ FPDMA QUEUED
[   39.642321] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   39.642323]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   39.642328] ata3.00: status: { DRDY ERR }
[   39.642331] ata3.00: error: { UNC }
[   39.646625] ata3.00: configured for UDMA/133
[   39.646635] ata3: EH complete
[   42.092611] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   42.092617] ata3.00: irq_stat 0x40000008
[   42.092621] ata3.00: failed command: READ FPDMA QUEUED
[   42.092631] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   42.092633]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   42.092638] ata3.00: status: { DRDY ERR }
[   42.092642] ata3.00: error: { UNC }
[   42.096985] ata3.00: configured for UDMA/133
[   42.096996] ata3: EH complete
[   44.531796] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   44.531802] ata3.00: irq_stat 0x40000008
[   44.531807] ata3.00: failed command: READ FPDMA QUEUED
[   44.531817] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   44.531819]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   44.531824] ata3.00: status: { DRDY ERR }
[   44.531828] ata3.00: error: { UNC }
[   44.536133] ata3.00: configured for UDMA/133
[   44.536148] sd 2:0:0:0: [sda] Unhandled sense code
[   44.536152] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   44.536158] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[   44.536165] Descriptor sense data with sense descriptors (in hex):
[   44.536169]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   44.536186]         18 51 ce ee 
[   44.536199] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[   44.536204] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[   44.536211] end_request: I/O error, dev sda, sector 408014574
[   44.536234] ata3: EH complete
[   47.020373] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   47.020380] ata3.00: irq_stat 0x40000008
[   47.020385] ata3.00: failed command: READ FPDMA QUEUED
[   47.020395] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   47.020397]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   47.020402] ata3.00: status: { DRDY ERR }
[   47.020405] ata3.00: error: { UNC }
[   47.024892] ata3.00: configured for UDMA/133
[   47.024899] ata3: EH complete
[   49.487783] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   49.487789] ata3.00: irq_stat 0x40000008
[   49.487794] ata3.00: failed command: READ FPDMA QUEUED
[   49.487804] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   49.487806]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   49.487811] ata3.00: status: { DRDY ERR }
[   49.487815] ata3.00: error: { UNC }
[   49.492124] ata3.00: configured for UDMA/133
[   49.492136] ata3: EH complete
[   53.845029] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   53.845036] ata3.00: irq_stat 0x40000008
[   53.845041] ata3.00: failed command: READ FPDMA QUEUED
[   53.845052] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   53.845053]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   53.845059] ata3.00: status: { DRDY ERR }
[   53.845062] ata3.00: error: { UNC }
[   53.849300] ata3.00: configured for UDMA/133
[   53.849314] ata3: EH complete
[   56.295364] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   56.295370] ata3.00: irq_stat 0x40000008
[   56.295374] ata3.00: failed command: READ FPDMA QUEUED
[   56.295385] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   56.295387]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   56.295392] ata3.00: status: { DRDY ERR }
[   56.295395] ata3.00: error: { UNC }
[   56.299682] ata3.00: configured for UDMA/133
[   56.299693] ata3: EH complete
[   58.778914] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   58.778921] ata3.00: irq_stat 0x40000008
[   58.778926] ata3.00: failed command: READ FPDMA QUEUED
[   58.778936] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   58.778938]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   58.778943] ata3.00: status: { DRDY ERR }
[   58.778946] ata3.00: error: { UNC }
[   58.783230] ata3.00: configured for UDMA/133
[   58.783243] ata3: EH complete
[   61.262470] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   61.262476] ata3.00: irq_stat 0x40000008
[   61.262481] ata3.00: failed command: READ FPDMA QUEUED
[   61.262491] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   61.262493]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   61.262498] ata3.00: status: { DRDY ERR }
[   61.262501] ata3.00: error: { UNC }
[   61.266780] ata3.00: configured for UDMA/133
[   61.266795] sd 2:0:0:0: [sda] Unhandled sense code
[   61.266799] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   61.266805] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[   61.266813] Descriptor sense data with sense descriptors (in hex):
[   61.266816]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   61.266833]         18 51 ce ee 
[   61.266841] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[   61.266850] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[   61.266866] end_request: I/O error, dev sda, sector 408014574
[   61.266892] ata3: EH complete
[   63.768215] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[   63.768218] ata3.00: irq_stat 0x40000008
[   63.768220] ata3.00: failed command: READ FPDMA QUEUED
[   63.768225] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[   63.768226]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   63.768228] ata3.00: status: { DRDY ERR }
[   63.768229] ata3.00: error: { UNC }
[   63.772566] ata3.00: configured for UDMA/133
[   63.772581] ata3: EH complete
[   66.241266] ata3.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[   66.241272] ata3.00: irq_stat 0x40000008
[   66.241277] ata3.00: failed command: READ FPDMA QUEUED
[   66.241287] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[   66.241289]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   66.241294] ata3.00: status: { DRDY ERR }
[   66.241297] ata3.00: error: { UNC }
[   66.245544] ata3.00: configured for UDMA/133
[   66.245555] ata3: EH complete
[   68.724174] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   68.724179] ata3.00: irq_stat 0x40000008
[   68.724185] ata3.00: failed command: READ FPDMA QUEUED
[   68.724199] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   68.724200]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   68.724202] ata3.00: status: { DRDY ERR }
[   68.724204] ata3.00: error: { UNC }
[   68.728446] ata3.00: configured for UDMA/133
[   68.728456] ata3: EH complete
[   71.174408] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   71.174414] ata3.00: irq_stat 0x40000008
[   71.174419] ata3.00: failed command: READ FPDMA QUEUED
[   71.174430] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   71.174432]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   71.174436] ata3.00: status: { DRDY ERR }
[   71.174440] ata3.00: error: { UNC }
[   71.178676] ata3.00: configured for UDMA/133
[   71.178689] ata3: EH complete
[   73.635776] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   73.635782] ata3.00: irq_stat 0x40000008
[   73.635787] ata3.00: failed command: READ FPDMA QUEUED
[   73.635798] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   73.635800]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   73.635804] ata3.00: status: { DRDY ERR }
[   73.635808] ata3.00: error: { UNC }
[   73.640111] ata3.00: configured for UDMA/133
[   73.640124] ata3: EH complete
[   76.075075] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   76.075081] ata3.00: irq_stat 0x40000008
[   76.075086] ata3.00: failed command: READ FPDMA QUEUED
[   76.075096] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   76.075098]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   76.075103] ata3.00: status: { DRDY ERR }
[   76.075106] ata3.00: error: { UNC }
[   76.079391] ata3.00: configured for UDMA/133
[   76.079406] sd 2:0:0:0: [sda] Unhandled sense code
[   76.079410] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   76.079416] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[   76.079424] Descriptor sense data with sense descriptors (in hex):
[   76.079427]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   76.079444]         18 51 ce ee 
[   76.079451] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[   76.079461] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[   76.079477] end_request: I/O error, dev sda, sector 408014574
[   76.079503] ata3: EH complete
[   78.926194] ata3.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[   78.926201] ata3.00: irq_stat 0x40000008
[   78.926207] ata3.00: failed command: READ FPDMA QUEUED
[   78.926217] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[   78.926219]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   78.926224] ata3.00: status: { DRDY ERR }
[   78.926228] ata3.00: error: { UNC }
[   78.930516] ata3.00: configured for UDMA/133
[   78.930528] ata3: EH complete
[   81.396955] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   81.396961] ata3.00: irq_stat 0x40000008
[   81.396966] ata3.00: failed command: READ FPDMA QUEUED
[   81.396976] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   81.396978]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   81.396983] ata3.00: status: { DRDY ERR }
[   81.396986] ata3.00: error: { UNC }
[   81.401233] ata3.00: configured for UDMA/133
[   81.401248] ata3: EH complete
[   83.836116] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   83.836122] ata3.00: irq_stat 0x40000008
[   83.836127] ata3.00: failed command: READ FPDMA QUEUED
[   83.836137] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   83.836139]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   83.836144] ata3.00: status: { DRDY ERR }
[   83.836148] ata3.00: error: { UNC }
[   83.840449] ata3.00: configured for UDMA/133
[   83.840461] ata3: EH complete
[   86.319693] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   86.319698] ata3.00: irq_stat 0x40000008
[   86.319704] ata3.00: failed command: READ FPDMA QUEUED
[   86.319714] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   86.319716]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   86.319721] ata3.00: status: { DRDY ERR }
[   86.319724] ata3.00: error: { UNC }
[   86.324026] ata3.00: configured for UDMA/133
[   86.324038] ata3: EH complete
[   88.747714] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   88.747720] ata3.00: irq_stat 0x40000008
[   88.747725] ata3.00: failed command: READ FPDMA QUEUED
[   88.747735] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   88.747737]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   88.747742] ata3.00: status: { DRDY ERR }
[   88.747746] ata3.00: error: { UNC }
[   88.752040] ata3.00: configured for UDMA/133
[   88.752052] ata3: EH complete
[   91.198045] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   91.198051] ata3.00: irq_stat 0x40000008
[   91.198056] ata3.00: failed command: READ FPDMA QUEUED
[   91.198066] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   91.198068]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   91.198073] ata3.00: status: { DRDY ERR }
[   91.198077] ata3.00: error: { UNC }
[   91.202358] ata3.00: configured for UDMA/133
[   91.202373] sd 2:0:0:0: [sda] Unhandled sense code
[   91.202377] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   91.202383] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[   91.202391] Descriptor sense data with sense descriptors (in hex):
[   91.202394]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   91.202411]         18 51 ce ee 
[   91.202418] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[   91.202428] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[   91.202444] end_request: I/O error, dev sda, sector 408014574
[   91.202469] ata3: EH complete
[   93.648267] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   93.648273] ata3.00: irq_stat 0x40000008
[   93.648278] ata3.00: failed command: READ FPDMA QUEUED
[   93.648288] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[   93.648290]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   93.648295] ata3.00: status: { DRDY ERR }
[   93.648298] ata3.00: error: { UNC }
[   93.652604] ata3.00: configured for UDMA/133
[   93.652617] ata3: EH complete
[   96.109637] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[   96.109642] ata3.00: irq_stat 0x40000008
[   96.109647] ata3.00: failed command: READ FPDMA QUEUED
[   96.109657] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[   96.109659]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[   96.109664] ata3.00: status: { DRDY ERR }
[   96.109668] ata3.00: error: { UNC }
[   96.113956] ata3.00: configured for UDMA/133
[   96.113968] ata3: EH complete
[  100.245250] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  100.245256] ata3.00: irq_stat 0x40000008
[  100.245262] ata3.00: failed command: READ FPDMA QUEUED
[  100.245272] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  100.245274]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  100.245279] ata3.00: status: { DRDY ERR }
[  100.245283] ata3.00: error: { UNC }
[  100.249624] ata3.00: configured for UDMA/133
[  100.249638] ata3: EH complete
[  102.695473] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  102.695480] ata3.00: irq_stat 0x40000008
[  102.695485] ata3.00: failed command: READ FPDMA QUEUED
[  102.695495] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  102.695498]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  102.695503] ata3.00: status: { DRDY ERR }
[  102.695506] ata3.00: error: { UNC }
[  102.699789] ata3.00: configured for UDMA/133
[  102.699802] ata3: EH complete
[  105.190192] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  105.190198] ata3.00: irq_stat 0x40000008
[  105.190203] ata3.00: failed command: READ FPDMA QUEUED
[  105.190214] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  105.190216]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  105.190220] ata3.00: status: { DRDY ERR }
[  105.190224] ata3.00: error: { UNC }
[  105.194514] ata3.00: configured for UDMA/133
[  105.194527] ata3: EH complete
[  107.684772] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  107.684777] ata3.00: irq_stat 0x40000008
[  107.684782] ata3.00: failed command: READ FPDMA QUEUED
[  107.684793] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  107.684794]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  107.684799] ata3.00: status: { DRDY ERR }
[  107.684803] ata3.00: error: { UNC }
[  107.689117] ata3.00: configured for UDMA/133
[  107.689131] sd 2:0:0:0: [sda] Unhandled sense code
[  107.689135] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  107.689141] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  107.689149] Descriptor sense data with sense descriptors (in hex):
[  107.689152]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  107.689169]         18 51 ce ee 
[  107.689177] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  107.689186] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  107.689202] end_request: I/O error, dev sda, sector 408014574
[  107.689225] ata3: EH complete
[  111.853629] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  111.853635] ata3.00: irq_stat 0x40000008
[  111.853640] ata3.00: failed command: READ FPDMA QUEUED
[  111.853651] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  111.853653]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  111.853658] ata3.00: status: { DRDY ERR }
[  111.853661] ata3.00: error: { UNC }
[  111.857956] ata3.00: configured for UDMA/133
[  111.857968] ata3: EH complete
[  114.326035] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  114.326041] ata3.00: irq_stat 0x40000008
[  114.326046] ata3.00: failed command: READ FPDMA QUEUED
[  114.326057] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  114.326059]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  114.326063] ata3.00: status: { DRDY ERR }
[  114.326067] ata3.00: error: { UNC }
[  114.330357] ata3.00: configured for UDMA/133
[  114.330369] ata3: EH complete
[  116.787403] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  116.787410] ata3.00: irq_stat 0x40000008
[  116.787415] ata3.00: failed command: READ FPDMA QUEUED
[  116.787426] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  116.787428]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  116.787432] ata3.00: status: { DRDY ERR }
[  116.787436] ata3.00: error: { UNC }
[  116.791723] ata3.00: configured for UDMA/133
[  116.791736] ata3: EH complete
[  119.237736] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  119.237741] ata3.00: irq_stat 0x40000008
[  119.237746] ata3.00: failed command: READ FPDMA QUEUED
[  119.237757] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  119.237759]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  119.237763] ata3.00: status: { DRDY ERR }
[  119.237767] ata3.00: error: { UNC }
[  119.242057] ata3.00: configured for UDMA/133
[  119.242069] ata3: EH complete
[  121.699104] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  121.699110] ata3.00: irq_stat 0x40000008
[  121.699115] ata3.00: failed command: READ FPDMA QUEUED
[  121.699126] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  121.699128]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  121.699133] ata3.00: status: { DRDY ERR }
[  121.699137] ata3.00: error: { UNC }
[  121.703427] ata3.00: configured for UDMA/133
[  121.703440] ata3: EH complete
[  124.138264] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  124.138270] ata3.00: irq_stat 0x40000008
[  124.138275] ata3.00: failed command: READ FPDMA QUEUED
[  124.138285] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  124.138287]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  124.138292] ata3.00: status: { DRDY ERR }
[  124.138295] ata3.00: error: { UNC }
[  124.142577] ata3.00: configured for UDMA/133
[  124.142590] sd 2:0:0:0: [sda] Unhandled sense code
[  124.142594] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  124.142600] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  124.142608] Descriptor sense data with sense descriptors (in hex):
[  124.142611]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  124.142628]         18 51 ce ee 
[  124.142635] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  124.142645] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  124.142661] end_request: I/O error, dev sda, sector 408014574
[  124.142684] ata3: EH complete
[  126.632648] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  126.632654] ata3.00: irq_stat 0x40000008
[  126.632660] ata3.00: failed command: READ FPDMA QUEUED
[  126.632670] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  126.632672]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  126.632677] ata3.00: status: { DRDY ERR }
[  126.632681] ata3.00: error: { UNC }
[  126.637021] ata3.00: configured for UDMA/133
[  126.637035] ata3: EH complete
[  129.072052] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  129.072057] ata3.00: irq_stat 0x40000008
[  129.072062] ata3.00: failed command: READ FPDMA QUEUED
[  129.072073] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  129.072075]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  129.072080] ata3.00: status: { DRDY ERR }
[  129.072083] ata3.00: error: { UNC }
[  129.076352] ata3.00: configured for UDMA/133
[  129.076366] ata3: EH complete
[  131.500179] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  131.500185] ata3.00: irq_stat 0x40000008
[  131.500190] ata3.00: failed command: READ FPDMA QUEUED
[  131.500202] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  131.500203]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  131.500205] ata3.00: status: { DRDY ERR }
[  131.500207] ata3.00: error: { UNC }
[  131.504523] ata3.00: configured for UDMA/133
[  131.504535] ata3: EH complete
[  133.950411] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  133.950417] ata3.00: irq_stat 0x40000008
[  133.950423] ata3.00: failed command: READ FPDMA QUEUED
[  133.950434] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  133.950436]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  133.950441] ata3.00: status: { DRDY ERR }
[  133.950445] ata3.00: error: { UNC }
[  133.954735] ata3.00: configured for UDMA/133
[  133.954748] ata3: EH complete
[  138.063832] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  138.063838] ata3.00: irq_stat 0x40000008
[  138.063844] ata3.00: failed command: READ FPDMA QUEUED
[  138.063854] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  138.063856]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  138.063861] ata3.00: status: { DRDY ERR }
[  138.063865] ata3.00: error: { UNC }
[  138.068166] ata3.00: configured for UDMA/133
[  138.068181] ata3: EH complete
[  140.547386] ata3.00: exception Emask 0x0 SAct 0x5 SErr 0x0 action 0x0
[  140.547392] ata3.00: irq_stat 0x40000008
[  140.547398] ata3.00: failed command: READ FPDMA QUEUED
[  140.547408] ata3.00: cmd 60/08:10:e8:ce:51/00:00:18:00:00/40 tag 2 ncq 4096 in
[  140.547410]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  140.547415] ata3.00: status: { DRDY ERR }
[  140.547419] ata3.00: error: { UNC }
[  140.551700] ata3.00: configured for UDMA/133
[  140.551718] sd 2:0:0:0: [sda] Unhandled sense code
[  140.551722] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  140.551728] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  140.551736] Descriptor sense data with sense descriptors (in hex):
[  140.551739]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  140.551757]         18 51 ce ee 
[  140.551764] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  140.551773] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  140.551789] end_request: I/O error, dev sda, sector 408014574
[  140.551812] ata3: EH complete
[  143.055539] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  143.055545] ata3.00: irq_stat 0x40000008
[  143.055551] ata3.00: failed command: READ FPDMA QUEUED
[  143.055561] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  143.055563]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  143.055568] ata3.00: status: { DRDY ERR }
[  143.055572] ata3.00: error: { UNC }
[  143.059867] ata3.00: configured for UDMA/133
[  143.059882] ata3: EH complete
[  145.539069] ata3.00: exception Emask 0x0 SAct 0x4 SErr 0x0 action 0x0
[  145.539071] ata3.00: irq_stat 0x40000008
[  145.539074] ata3.00: failed command: READ FPDMA QUEUED
[  145.539079] ata3.00: cmd 60/08:10:e8:ce:51/00:00:18:00:00/40 tag 2 ncq 4096 in
[  145.539080]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  145.539082] ata3.00: status: { DRDY ERR }
[  145.539084] ata3.00: error: { UNC }
[  145.543407] ata3.00: configured for UDMA/133
[  145.543418] ata3: EH complete
[  148.009088] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  148.009093] ata3.00: irq_stat 0x40000008
[  148.009098] ata3.00: failed command: READ FPDMA QUEUED
[  148.009109] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  148.009111]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  148.009116] ata3.00: status: { DRDY ERR }
[  148.009120] ata3.00: error: { UNC }
[  148.013407] ata3.00: configured for UDMA/133
[  148.013418] ata3: EH complete
[  150.514848] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  150.514853] ata3.00: irq_stat 0x40000008
[  150.514858] ata3.00: failed command: READ FPDMA QUEUED
[  150.514869] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  150.514871]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  150.514876] ata3.00: status: { DRDY ERR }
[  150.514880] ata3.00: error: { UNC }
[  150.519179] ata3.00: configured for UDMA/133
[  150.519190] ata3: EH complete
[  152.965051] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  152.965057] ata3.00: irq_stat 0x40000008
[  152.965063] ata3.00: failed command: READ FPDMA QUEUED
[  152.965073] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  152.965075]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  152.965081] ata3.00: status: { DRDY ERR }
[  152.965084] ata3.00: error: { UNC }
[  152.969405] ata3.00: configured for UDMA/133
[  152.969419] ata3: EH complete
[  155.426418] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  155.426423] ata3.00: irq_stat 0x40000008
[  155.426428] ata3.00: failed command: READ FPDMA QUEUED
[  155.426438] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  155.426440]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  155.426445] ata3.00: status: { DRDY ERR }
[  155.426448] ata3.00: error: { UNC }
[  155.430721] ata3.00: configured for UDMA/133
[  155.430735] sd 2:0:0:0: [sda] Unhandled sense code
[  155.430739] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  155.430745] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  155.430753] Descriptor sense data with sense descriptors (in hex):
[  155.430756]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  155.430773]         18 51 ce ee 
[  155.430781] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  155.430790] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  155.430806] end_request: I/O error, dev sda, sector 408014574
[  155.430830] ata3: EH complete
[  157.900394] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  157.900401] ata3.00: irq_stat 0x40000008
[  157.900407] ata3.00: failed command: READ FPDMA QUEUED
[  157.900417] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  157.900419]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  157.900424] ata3.00: status: { DRDY ERR }
[  157.900427] ata3.00: error: { UNC }
[  157.904724] ata3.00: configured for UDMA/133
[  157.904737] ata3: EH complete
[  160.382499] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  160.382505] ata3.00: irq_stat 0x40000008
[  160.382510] ata3.00: failed command: READ FPDMA QUEUED
[  160.382520] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  160.382522]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  160.382527] ata3.00: status: { DRDY ERR }
[  160.382531] ata3.00: error: { UNC }
[  160.386827] ata3.00: configured for UDMA/133
[  160.386838] ata3: EH complete
[  164.517992] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  164.517998] ata3.00: irq_stat 0x40000008
[  164.518004] ata3.00: failed command: READ FPDMA QUEUED
[  164.518015] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  164.518016]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  164.518021] ata3.00: status: { DRDY ERR }
[  164.518025] ata3.00: error: { UNC }
[  164.522333] ata3.00: configured for UDMA/133
[  164.522346] ata3: EH complete
[  166.957184] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  166.957191] ata3.00: irq_stat 0x40000008
[  166.957196] ata3.00: failed command: READ FPDMA QUEUED
[  166.957207] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  166.957209]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  166.957213] ata3.00: status: { DRDY ERR }
[  166.957217] ata3.00: error: { UNC }
[  166.961526] ata3.00: configured for UDMA/133
[  166.961539] ata3: EH complete
[  171.081639] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  171.081646] ata3.00: irq_stat 0x40000008
[  171.081651] ata3.00: failed command: READ FPDMA QUEUED
[  171.081661] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  171.081663]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  171.081668] ata3.00: status: { DRDY ERR }
[  171.081672] ata3.00: error: { UNC }
[  171.085959] ata3.00: configured for UDMA/133
[  171.085972] ata3: EH complete
[  173.531968] ata3.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  173.531974] ata3.00: irq_stat 0x40000008
[  173.531980] ata3.00: failed command: READ FPDMA QUEUED
[  173.531990] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  173.531992]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  173.531997] ata3.00: status: { DRDY ERR }
[  173.532001] ata3.00: error: { UNC }
[  173.536311] ata3.00: configured for UDMA/133
[  173.536325] sd 2:0:0:0: [sda] Unhandled sense code
[  173.536329] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  173.536335] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  173.536343] Descriptor sense data with sense descriptors (in hex):
[  173.536347]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  173.536364]         18 51 ce ee 
[  173.536371] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  173.536381] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  173.536396] end_request: I/O error, dev sda, sector 408014574
[  173.536419] ata3: EH complete
[  176.014268] ata3.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  176.014274] ata3.00: irq_stat 0x40000008
[  176.014280] ata3.00: failed command: READ FPDMA QUEUED
[  176.014290] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  176.014292]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  176.014297] ata3.00: status: { DRDY ERR }
[  176.014300] ata3.00: error: { UNC }
[  176.018619] ata3.00: configured for UDMA/133
[  176.018636] ata3: EH complete
[  178.675198] ata3.00: exception Emask 0x0 SAct 0x9 SErr 0x0 action 0x0
[  178.675204] ata3.00: irq_stat 0x40000008
[  178.675209] ata3.00: failed command: READ FPDMA QUEUED
[  178.675220] ata3.00: cmd 60/08:18:e8:ce:51/00:00:18:00:00/40 tag 3 ncq 4096 in
[  178.675222]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  178.675227] ata3.00: status: { DRDY ERR }
[  178.675230] ata3.00: error: { UNC }
[  178.679518] ata3.00: configured for UDMA/133
[  178.679530] ata3: EH complete
[  181.137715] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  181.137720] ata3.00: irq_stat 0x40000008
[  181.137725] ata3.00: failed command: READ FPDMA QUEUED
[  181.137736] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  181.137738]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  181.137743] ata3.00: status: { DRDY ERR }
[  181.137747] ata3.00: error: { UNC }
[  181.142052] ata3.00: configured for UDMA/133
[  181.142064] ata3: EH complete
[  183.599082] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  183.599088] ata3.00: irq_stat 0x40000008
[  183.599093] ata3.00: failed command: READ FPDMA QUEUED
[  183.599103] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  183.599106]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  183.599111] ata3.00: status: { DRDY ERR }
[  183.599114] ata3.00: error: { UNC }
[  183.603402] ata3.00: configured for UDMA/133
[  183.603414] ata3: EH complete
[  186.093779] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  186.093784] ata3.00: irq_stat 0x40000008
[  186.093790] ata3.00: failed command: READ FPDMA QUEUED
[  186.093800] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  186.093802]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  186.093807] ata3.00: status: { DRDY ERR }
[  186.093810] ata3.00: error: { UNC }
[  186.098128] ata3.00: configured for UDMA/133
[  186.098140] ata3: EH complete
[  188.555148] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  188.555154] ata3.00: irq_stat 0x40000008
[  188.555159] ata3.00: failed command: READ FPDMA QUEUED
[  188.555169] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  188.555172]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  188.555177] ata3.00: status: { DRDY ERR }
[  188.555180] ata3.00: error: { UNC }
[  188.559447] ata3.00: configured for UDMA/133
[  188.559458] sd 2:0:0:0: [sda] Unhandled sense code
[  188.559460] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  188.559463] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  188.559467] Descriptor sense data with sense descriptors (in hex):
[  188.559469]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  188.559477]         18 51 ce ee 
[  188.559480] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  188.559486] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  188.559493] end_request: I/O error, dev sda, sector 408014574
[  188.559509] ata3: EH complete
[  191.086201] ata3.00: exception Emask 0x0 SAct 0x5 SErr 0x0 action 0x0
[  191.086207] ata3.00: irq_stat 0x40000008
[  191.086212] ata3.00: failed command: READ FPDMA QUEUED
[  191.086222] ata3.00: cmd 60/08:10:e8:ce:51/00:00:18:00:00/40 tag 2 ncq 4096 in
[  191.086224]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  191.086229] ata3.00: status: { DRDY ERR }
[  191.086232] ata3.00: error: { UNC }
[  191.090550] ata3.00: configured for UDMA/133
[  191.090563] ata3: EH complete
[  195.196393] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  195.196399] ata3.00: irq_stat 0x40000008
[  195.196404] ata3.00: failed command: READ FPDMA QUEUED
[  195.196415] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  195.196417]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  195.196422] ata3.00: status: { DRDY ERR }
[  195.196425] ata3.00: error: { UNC }
[  195.200744] ata3.00: configured for UDMA/133
[  195.200758] ata3: EH complete
[  197.668803] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  197.668809] ata3.00: irq_stat 0x40000008
[  197.668814] ata3.00: failed command: READ FPDMA QUEUED
[  197.668824] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  197.668826]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  197.668831] ata3.00: status: { DRDY ERR }
[  197.668835] ata3.00: error: { UNC }
[  197.673134] ata3.00: configured for UDMA/133
[  197.673148] ata3: EH complete
[  200.119125] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  200.119130] ata3.00: irq_stat 0x40000008
[  200.119136] ata3.00: failed command: READ FPDMA QUEUED
[  200.119146] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  200.119148]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  200.119153] ata3.00: status: { DRDY ERR }
[  200.119156] ata3.00: error: { UNC }
[  200.123453] ata3.00: configured for UDMA/133
[  200.123466] ata3: EH complete
[  204.265796] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  204.265803] ata3.00: irq_stat 0x40000008
[  204.265808] ata3.00: failed command: READ FPDMA QUEUED
[  204.265819] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  204.265821]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  204.265826] ata3.00: status: { DRDY ERR }
[  204.265830] ata3.00: error: { UNC }
[  204.270124] ata3.00: configured for UDMA/133
[  204.270137] ata3: EH complete
[  206.882337] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  206.882342] ata3.00: irq_stat 0x40000008
[  206.882348] ata3.00: failed command: READ FPDMA QUEUED
[  206.882358] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  206.882360]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  206.882365] ata3.00: status: { DRDY ERR }
[  206.882368] ata3.00: error: { UNC }
[  206.886666] ata3.00: configured for UDMA/133
[  206.886680] sd 2:0:0:0: [sda] Unhandled sense code
[  206.886683] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  206.886689] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  206.886697] Descriptor sense data with sense descriptors (in hex):
[  206.886701]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  206.886718]         18 51 ce ee 
[  206.886725] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  206.886735] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  206.886750] end_request: I/O error, dev sda, sector 408014574
[  206.886773] ata3: EH complete
[  209.815550] ata3.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  209.815556] ata3.00: irq_stat 0x40000008
[  209.815562] ata3.00: failed command: READ FPDMA QUEUED
[  209.815572] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  209.815574]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  209.815579] ata3.00: status: { DRDY ERR }
[  209.815583] ata3.00: error: { UNC }
[  209.819888] ata3.00: configured for UDMA/133
[  209.819898] ata3: EH complete
[  212.270785] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  212.270791] ata3.00: irq_stat 0x40000008
[  212.270797] ata3.00: failed command: READ FPDMA QUEUED
[  212.270807] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  212.270809]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  212.270814] ata3.00: status: { DRDY ERR }
[  212.270818] ata3.00: error: { UNC }
[  212.275116] ata3.00: configured for UDMA/133
[  212.275129] ata3: EH complete
[  214.732146] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  214.732151] ata3.00: irq_stat 0x40000008
[  214.732156] ata3.00: failed command: READ FPDMA QUEUED
[  214.732167] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  214.732169]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  214.732174] ata3.00: status: { DRDY ERR }
[  214.732177] ata3.00: error: { UNC }
[  214.736493] ata3.00: configured for UDMA/133
[  214.736505] ata3: EH complete
[  217.193518] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  217.193523] ata3.00: irq_stat 0x40000008
[  217.193528] ata3.00: failed command: READ FPDMA QUEUED
[  217.193539] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  217.193541]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  217.193546] ata3.00: status: { DRDY ERR }
[  217.193550] ata3.00: error: { UNC }
[  217.197845] ata3.00: configured for UDMA/133
[  217.197856] ata3: EH complete
[  219.654885] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  219.654890] ata3.00: irq_stat 0x40000008
[  219.654894] ata3.00: failed command: READ FPDMA QUEUED
[  219.654905] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  219.654907]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  219.654911] ata3.00: status: { DRDY ERR }
[  219.654915] ata3.00: error: { UNC }
[  219.659216] ata3.00: configured for UDMA/133
[  219.659227] ata3: EH complete
[  222.127282] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  222.127286] ata3.00: irq_stat 0x40000008
[  222.127289] ata3.00: failed command: READ FPDMA QUEUED
[  222.127293] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  222.127295]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  222.127297] ata3.00: status: { DRDY ERR }
[  222.127299] ata3.00: error: { UNC }
[  222.131623] ata3.00: configured for UDMA/133
[  222.131637] sd 2:0:0:0: [sda] Unhandled sense code
[  222.131641] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  222.131647] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  222.131655] Descriptor sense data with sense descriptors (in hex):
[  222.131658]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  222.131675]         18 51 ce ee 
[  222.131683] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  222.131692] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  222.131708] end_request: I/O error, dev sda, sector 408014574
[  222.131737] ata3: EH complete
[  228.757474] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  228.757481] ata3.00: irq_stat 0x40000008
[  228.757487] ata3.00: failed command: READ FPDMA QUEUED
[  228.757498] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  228.757500]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  228.757505] ata3.00: status: { DRDY ERR }
[  228.757508] ata3.00: error: { UNC }
[  228.761796] ata3.00: configured for UDMA/133
[  228.761809] ata3: EH complete
[  231.252061] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  231.252067] ata3.00: irq_stat 0x40000008
[  231.252072] ata3.00: failed command: READ FPDMA QUEUED
[  231.252083] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  231.252085]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  231.252090] ata3.00: status: { DRDY ERR }
[  231.252093] ata3.00: error: { UNC }
[  231.256418] ata3.00: configured for UDMA/133
[  231.256431] ata3: EH complete
[  233.757917] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  233.757923] ata3.00: irq_stat 0x40000008
[  233.757928] ata3.00: failed command: READ FPDMA QUEUED
[  233.757938] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  233.757940]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  233.757945] ata3.00: status: { DRDY ERR }
[  233.757949] ata3.00: error: { UNC }
[  233.762245] ata3.00: configured for UDMA/133
[  233.762259] ata3: EH complete
[  237.882270] ata3.00: exception Emask 0x0 SAct 0xd SErr 0x0 action 0x0
[  237.882277] ata3.00: irq_stat 0x40000008
[  237.882283] ata3.00: failed command: READ FPDMA QUEUED
[  237.882293] ata3.00: cmd 60/08:10:e8:ce:51/00:00:18:00:00/40 tag 2 ncq 4096 in
[  237.882295]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  237.882300] ata3.00: status: { DRDY ERR }
[  237.882304] ata3.00: error: { UNC }
[  237.886598] ata3.00: configured for UDMA/133
[  237.886614] ata3: EH complete
[  240.332490] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  240.332497] ata3.00: irq_stat 0x40000008
[  240.332502] ata3.00: failed command: READ FPDMA QUEUED
[  240.332513] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  240.332515]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  240.332520] ata3.00: status: { DRDY ERR }
[  240.332523] ata3.00: error: { UNC }
[  240.336826] ata3.00: configured for UDMA/133
[  240.336840] ata3: EH complete
[  242.805003] ata3.00: exception Emask 0x0 SAct 0xe SErr 0x0 action 0x0
[  242.805009] ata3.00: irq_stat 0x40000008
[  242.805014] ata3.00: failed command: READ FPDMA QUEUED
[  242.805024] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  242.805027]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  242.805032] ata3.00: status: { DRDY ERR }
[  242.805035] ata3.00: error: { UNC }
[  242.809386] ata3.00: configured for UDMA/133
[  242.809400] sd 2:0:0:0: [sda] Unhandled sense code
[  242.809404] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  242.809410] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  242.809417] Descriptor sense data with sense descriptors (in hex):
[  242.809421]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  242.809438]         18 51 ce ee 
[  242.809445] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  242.809455] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  242.809471] end_request: I/O error, dev sda, sector 408014574
[  242.809494] ata3: EH complete
[  245.310758] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  245.310764] ata3.00: irq_stat 0x40000008
[  245.310770] ata3.00: failed command: READ FPDMA QUEUED
[  245.310780] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  245.310782]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  245.310787] ata3.00: status: { DRDY ERR }
[  245.310791] ata3.00: error: { UNC }
[  245.315078] ata3.00: configured for UDMA/133
[  245.315089] ata3: EH complete
[  247.760960] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  247.760966] ata3.00: irq_stat 0x40000008
[  247.760971] ata3.00: failed command: READ FPDMA QUEUED
[  247.760981] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  247.760983]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  247.760988] ata3.00: status: { DRDY ERR }
[  247.760992] ata3.00: error: { UNC }
[  247.765299] ata3.00: configured for UDMA/133
[  247.765304] ata3: EH complete
[  250.211287] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  250.211293] ata3.00: irq_stat 0x40000008
[  250.211298] ata3.00: failed command: READ FPDMA QUEUED
[  250.211308] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  250.211310]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  250.211315] ata3.00: status: { DRDY ERR }
[  250.211319] ata3.00: error: { UNC }
[  250.215627] ata3.00: configured for UDMA/133
[  250.215633] ata3: EH complete
[  254.324605] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  254.324612] ata3.00: irq_stat 0x40000008
[  254.324617] ata3.00: failed command: READ FPDMA QUEUED
[  254.324627] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  254.324629]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  254.324635] ata3.00: status: { DRDY ERR }
[  254.324638] ata3.00: error: { UNC }
[  254.328976] ata3.00: configured for UDMA/133
[  254.328988] ata3: EH complete
[  256.774929] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  256.774934] ata3.00: irq_stat 0x40000008
[  256.774940] ata3.00: failed command: READ FPDMA QUEUED
[  256.774950] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  256.774952]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  256.774957] ata3.00: status: { DRDY ERR }
[  256.774961] ata3.00: error: { UNC }
[  256.779288] ata3.00: configured for UDMA/133
[  256.779299] ata3: EH complete
[  259.258501] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  259.258507] ata3.00: irq_stat 0x40000008
[  259.258511] ata3.00: failed command: READ FPDMA QUEUED
[  259.258522] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  259.258524]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  259.258529] ata3.00: status: { DRDY ERR }
[  259.258533] ata3.00: error: { UNC }
[  259.262841] ata3.00: configured for UDMA/133
[  259.262854] sd 2:0:0:0: [sda] Unhandled sense code
[  259.262858] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  259.262864] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  259.262872] Descriptor sense data with sense descriptors (in hex):
[  259.262876]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  259.262893]         18 51 ce ee 
[  259.262900] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  259.262910] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  259.262925] end_request: I/O error, dev sda, sector 408014574
[  259.262952] ata3: EH complete
[  261.912027] ata3.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  261.912034] ata3.00: irq_stat 0x40000008
[  261.912040] ata3.00: failed command: READ FPDMA QUEUED
[  261.912051] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  261.912053]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  261.912058] ata3.00: status: { DRDY ERR }
[  261.912061] ata3.00: error: { UNC }
[  261.916360] ata3.00: configured for UDMA/133
[  261.916372] ata3: EH complete
[  264.347434] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  264.347440] ata3.00: irq_stat 0x40000008
[  264.347445] ata3.00: failed command: READ FPDMA QUEUED
[  264.347456] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  264.347458]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  264.347463] ata3.00: status: { DRDY ERR }
[  264.347466] ata3.00: error: { UNC }
[  264.351775] ata3.00: configured for UDMA/133
[  264.351786] ata3: EH complete
[  266.808818] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  266.808824] ata3.00: irq_stat 0x40000008
[  266.808829] ata3.00: failed command: READ FPDMA QUEUED
[  266.808839] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  266.808841]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  266.808846] ata3.00: status: { DRDY ERR }
[  266.808850] ata3.00: error: { UNC }
[  266.813133] ata3.00: configured for UDMA/133
[  266.813143] ata3: EH complete
[  269.244755] ata3: failed to read log page 10h (errno=-5)
[  269.244765] ata3.00: exception Emask 0x1 SAct 0xf SErr 0x0 action 0x0
[  269.244769] ata3.00: irq_stat 0x40000008
[  269.244775] ata3.00: failed command: READ FPDMA QUEUED
[  269.244785] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  269.244787]          res 40/00:08:b8:5b:99/00:00:18:00:00/40 Emask 0x1 (device error)
[  269.244792] ata3.00: status: { DRDY }
[  269.244796] ata3.00: failed command: READ FPDMA QUEUED
[  269.244806] ata3.00: cmd 60/08:08:b8:5b:99/00:00:18:00:00/40 tag 1 ncq 4096 in
[  269.244808]          res 40/00:08:b8:5b:99/00:00:18:00:00/40 Emask 0x1 (device error)
[  269.244813] ata3.00: status: { DRDY }
[  269.244817] ata3.00: failed command: READ FPDMA QUEUED
[  269.244826] ata3.00: cmd 60/00:10:d8:90:87/01:00:18:00:00/40 tag 2 ncq 131072 in
[  269.244828]          res 40/00:08:b8:5b:99/00:00:18:00:00/40 Emask 0x1 (device error)
[  269.244833] ata3.00: status: { DRDY }
[  269.244842] ata3.00: failed command: READ FPDMA QUEUED
[  269.244846] ata3.00: cmd 60/08:18:78:6f:4a/00:00:18:00:00/40 tag 3 ncq 4096 in
[  269.244847]          res 40/00:08:b8:5b:99/00:00:18:00:00/40 Emask 0x1 (device error)
[  269.244849] ata3.00: status: { DRDY }
[  269.248020] ata3.00: model number mismatch 'ST9250827AS' != ''
[  269.248025] ata3.00: revalidation failed (errno=-19)
[  269.248033] ata3: limiting SATA link speed to 1.5 Gbps
[  269.248038] ata3.00: limiting speed to UDMA/133:PIO3
[  269.248045] ata3: hard resetting link
[  269.568070] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  269.569593] ata3.00: configured for UDMA/133
[  269.569610] ata3: EH complete
[  272.042049] ata3.00: exception Emask 0x0 SAct 0xb SErr 0x0 action 0x0
[  272.042056] ata3.00: irq_stat 0x40000008
[  272.042061] ata3.00: failed command: READ FPDMA QUEUED
[  272.042072] ata3.00: cmd 60/08:18:e8:ce:51/00:00:18:00:00/40 tag 3 ncq 4096 in
[  272.042074]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  272.042079] ata3.00: status: { DRDY ERR }
[  272.042082] ata3.00: error: { UNC }
[  272.046412] ata3.00: configured for UDMA/133
[  272.046427] ata3: EH complete
[  274.536664] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  274.536669] ata3.00: irq_stat 0x40000008
[  274.536674] ata3.00: failed command: READ FPDMA QUEUED
[  274.536684] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  274.536686]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  274.536691] ata3.00: status: { DRDY ERR }
[  274.536695] ata3.00: error: { UNC }
[  274.541022] ata3.00: configured for UDMA/133
[  274.541035] sd 2:0:0:0: [sda] Unhandled sense code
[  274.541038] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  274.541044] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  274.541052] Descriptor sense data with sense descriptors (in hex):
[  274.541056]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  274.541073]         18 51 ce ee 
[  274.541080] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  274.541090] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  274.541106] end_request: I/O error, dev sda, sector 408014574
[  274.541127] ata3: EH complete
[  277.607851] ata3.00: exception Emask 0x0 SAct 0x4 SErr 0x0 action 0x0
[  277.607858] ata3.00: irq_stat 0x40000008
[  277.607864] ata3.00: failed command: READ FPDMA QUEUED
[  277.607874] ata3.00: cmd 60/08:10:e8:ce:51/00:00:18:00:00/40 tag 2 ncq 4096 in
[  277.607876]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  277.607881] ata3.00: status: { DRDY ERR }
[  277.607885] ata3.00: error: { UNC }
[  277.612225] ata3.00: configured for UDMA/133
[  277.612236] ata3: EH complete
[  280.069219] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  280.069224] ata3.00: irq_stat 0x40000008
[  280.069229] ata3.00: failed command: READ FPDMA QUEUED
[  280.069239] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  280.069241]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  280.069246] ata3.00: status: { DRDY ERR }
[  280.069250] ata3.00: error: { UNC }
[  280.073534] ata3.00: configured for UDMA/133
[  280.073543] ata3: EH complete
[  282.497257] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  282.497263] ata3.00: irq_stat 0x40000008
[  282.497269] ata3.00: failed command: READ FPDMA QUEUED
[  282.497279] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  282.497281]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  282.497287] ata3.00: status: { DRDY ERR }
[  282.497290] ata3.00: error: { UNC }
[  282.501586] ata3.00: configured for UDMA/133
[  282.501598] ata3: EH complete
[  284.958615] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  284.958622] ata3.00: irq_stat 0x40000008
[  284.958628] ata3.00: failed command: READ FPDMA QUEUED
[  284.958638] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  284.958640]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  284.958645] ata3.00: status: { DRDY ERR }
[  284.958649] ata3.00: error: { UNC }
[  284.962946] ata3.00: configured for UDMA/133
[  284.962958] ata3: EH complete
[  289.304835] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  289.304841] ata3.00: irq_stat 0x40000008
[  289.304847] ata3.00: failed command: READ FPDMA QUEUED
[  289.304861] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  289.304863]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  289.304867] ata3.00: status: { DRDY ERR }
[  289.304869] ata3.00: error: { UNC }
[  289.309180] ata3.00: configured for UDMA/133
[  289.309191] ata3: EH complete
[  291.744020] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  291.744026] ata3.00: irq_stat 0x40000008
[  291.744032] ata3.00: failed command: READ FPDMA QUEUED
[  291.744042] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  291.744044]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  291.744049] ata3.00: status: { DRDY ERR }
[  291.744053] ata3.00: error: { UNC }
[  291.748390] ata3.00: configured for UDMA/133
[  291.748404] sd 2:0:0:0: [sda] Unhandled sense code
[  291.748408] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  291.748414] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  291.748422] Descriptor sense data with sense descriptors (in hex):
[  291.748425]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  291.748443]         18 51 ce ee 
[  291.748448] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  291.748453] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  291.748463] end_request: I/O error, dev sda, sector 408014574
[  291.748481] ata3: EH complete
[  294.227577] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  294.227584] ata3.00: irq_stat 0x40000008
[  294.227590] ata3.00: failed command: READ FPDMA QUEUED
[  294.227600] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  294.227602]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  294.227607] ata3.00: status: { DRDY ERR }
[  294.227611] ata3.00: error: { UNC }
[  294.231935] ata3.00: configured for UDMA/133
[  294.231947] ata3: EH complete
[  296.822064] ata3.00: exception Emask 0x0 SAct 0x1f SErr 0x0 action 0x0
[  296.822071] ata3.00: irq_stat 0x40000008
[  296.822083] ata3.00: failed command: READ FPDMA QUEUED
[  296.822091] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  296.822092]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  296.822096] ata3.00: status: { DRDY ERR }
[  296.822099] ata3.00: error: { UNC }
[  296.826390] ata3.00: configured for UDMA/133
[  296.826409] ata3: EH complete
[  299.298955] ata3.00: exception Emask 0x0 SAct 0x1d SErr 0x0 action 0x0
[  299.298964] ata3.00: irq_stat 0x40000008
[  299.298973] ata3.00: failed command: READ FPDMA QUEUED
[  299.298989] ata3.00: cmd 60/08:20:e8:ce:51/00:00:18:00:00/40 tag 4 ncq 4096 in
[  299.298991]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  299.298999] ata3.00: status: { DRDY ERR }
[  299.299004] ata3.00: error: { UNC }
[  299.303190] ata3.00: configured for UDMA/133
[  299.303209] ata3: EH complete
[  303.407777] ata3.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  303.407783] ata3.00: irq_stat 0x40000008
[  303.407788] ata3.00: failed command: READ FPDMA QUEUED
[  303.407802] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  303.407803]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  303.407807] ata3.00: status: { DRDY ERR }
[  303.407810] ata3.00: error: { UNC }
[  303.412106] ata3.00: configured for UDMA/133
[  303.412118] ata3: EH complete
[  306.017669] ata3.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  306.017676] ata3.00: irq_stat 0x40000008
[  306.017682] ata3.00: failed command: READ FPDMA QUEUED
[  306.017692] ata3.00: cmd 60/08:18:e8:ce:51/00:00:18:00:00/40 tag 3 ncq 4096 in
[  306.017694]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  306.017699] ata3.00: status: { DRDY ERR }
[  306.017703] ata3.00: error: { UNC }
[  306.021993] ata3.00: configured for UDMA/133
[  306.022010] ata3: EH complete
[  308.496864] ata3.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  308.496869] ata3.00: irq_stat 0x40000008
[  308.496874] ata3.00: failed command: READ FPDMA QUEUED
[  308.496889] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  308.496890]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  308.496894] ata3.00: status: { DRDY ERR }
[  308.496897] ata3.00: error: { UNC }
[  308.501184] ata3.00: configured for UDMA/133
[  308.501198] sd 2:0:0:0: [sda] Unhandled sense code
[  308.501202] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  308.501208] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  308.501222] Descriptor sense data with sense descriptors (in hex):
[  308.501224]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  308.501237]         18 51 ce ee 
[  308.501243] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  308.501250] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  308.501262] end_request: I/O error, dev sda, sector 408014574
[  308.501280] ata3: EH complete
[  311.587127] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  311.587134] ata3.00: irq_stat 0x40000008
[  311.587145] ata3.00: failed command: READ FPDMA QUEUED
[  311.587153] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  311.587155]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  311.587159] ata3.00: status: { DRDY ERR }
[  311.587161] ata3.00: error: { UNC }
[  311.591462] ata3.00: configured for UDMA/133
[  311.591474] ata3: EH complete
[  314.018282] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  314.018289] ata3.00: irq_stat 0x40000008
[  314.018295] ata3.00: failed command: READ FPDMA QUEUED
[  314.018309] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  314.018310]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  314.018314] ata3.00: status: { DRDY ERR }
[  314.018316] ata3.00: error: { UNC }
[  314.022643] ata3.00: configured for UDMA/133
[  314.022655] ata3: EH complete
[  316.457457] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  316.457462] ata3.00: irq_stat 0x40000008
[  316.457467] ata3.00: failed command: READ FPDMA QUEUED
[  316.457482] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  316.457484]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  316.457488] ata3.00: status: { DRDY ERR }
[  316.457490] ata3.00: error: { UNC }
[  316.461779] ata3.00: configured for UDMA/133
[  316.461789] ata3: EH complete
[  318.918934] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  318.918943] ata3.00: irq_stat 0x40000008
[  318.918952] ata3.00: failed command: READ FPDMA QUEUED
[  318.918968] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  318.918971]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  318.918978] ata3.00: status: { DRDY ERR }
[  318.918984] ata3.00: error: { UNC }
[  318.923162] ata3.00: configured for UDMA/133
[  318.923176] ata3: EH complete
[  321.369151] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  321.369157] ata3.00: irq_stat 0x40000008
[  321.369163] ata3.00: failed command: READ FPDMA QUEUED
[  321.369177] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  321.369179]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  321.369183] ata3.00: status: { DRDY ERR }
[  321.369185] ata3.00: error: { UNC }
[  321.373478] ata3.00: configured for UDMA/133
[  321.373490] ata3: EH complete
[  323.808339] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  323.808346] ata3.00: irq_stat 0x40000008
[  323.808351] ata3.00: failed command: READ FPDMA QUEUED
[  323.808366] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  323.808367]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  323.808371] ata3.00: status: { DRDY ERR }
[  323.808374] ata3.00: error: { UNC }
[  323.812697] ata3.00: configured for UDMA/133
[  323.812718] sd 2:0:0:0: [sda] Unhandled sense code
[  323.812720] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  323.812725] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  323.812731] Descriptor sense data with sense descriptors (in hex):
[  323.812734]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  323.812747]         18 51 ce ee 
[  323.812752] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  323.812760] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  323.812771] end_request: I/O error, dev sda, sector 408014574
[  323.812793] ata3: EH complete
[  326.253690] ata3.00: exception Emask 0x0 SAct 0x1f SErr 0x0 action 0x0
[  326.253695] ata3.00: irq_stat 0x40000008
[  326.253700] ata3.00: failed command: READ FPDMA QUEUED
[  326.253711] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  326.253713]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  326.253718] ata3.00: status: { DRDY ERR }
[  326.253722] ata3.00: error: { UNC }
[  326.258029] ata3.00: configured for UDMA/133
[  326.258045] ata3: EH complete
[  328.750763] ata3.00: exception Emask 0x0 SAct 0xc SErr 0x0 action 0x0
[  328.750769] ata3.00: irq_stat 0x40000008
[  328.750775] ata3.00: failed command: READ FPDMA QUEUED
[  328.750786] ata3.00: cmd 60/08:18:e8:ce:51/00:00:18:00:00/40 tag 3 ncq 4096 in
[  328.750788]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  328.750793] ata3.00: status: { DRDY ERR }
[  328.750796] ata3.00: error: { UNC }
[  328.755141] ata3.00: configured for UDMA/133
[  328.755155] ata3: EH complete
[  331.192438] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  331.192443] ata3.00: irq_stat 0x40000008
[  331.192448] ata3.00: failed command: READ FPDMA QUEUED
[  331.192463] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  331.192465]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  331.192469] ata3.00: status: { DRDY ERR }
[  331.192471] ata3.00: error: { UNC }
[  331.196787] ata3.00: configured for UDMA/133
[  331.196804] ata3: EH complete
[  333.675985] ata3.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  333.675990] ata3.00: irq_stat 0x40000008
[  333.675995] ata3.00: failed command: READ FPDMA QUEUED
[  333.676010] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  333.676011]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  333.676032] ata3.00: status: { DRDY ERR }
[  333.676034] ata3.00: error: { UNC }
[  333.680333] ata3.00: configured for UDMA/133
[  333.680350] ata3: EH complete
[  336.148385] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  336.148391] ata3.00: irq_stat 0x40000008
[  336.148397] ata3.00: failed command: READ FPDMA QUEUED
[  336.148411] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  336.148413]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  336.148416] ata3.00: status: { DRDY ERR }
[  336.148419] ata3.00: error: { UNC }
[  336.152724] ata3.00: configured for UDMA/133
[  336.152744] ata3: EH complete
[  338.587668] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  338.587673] ata3.00: irq_stat 0x40000008
[  338.587678] ata3.00: failed command: READ FPDMA QUEUED
[  338.587689] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  338.587691]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  338.587696] ata3.00: status: { DRDY ERR }
[  338.587700] ata3.00: error: { UNC }
[  338.591987] ata3.00: configured for UDMA/133
[  338.592001] sd 2:0:0:0: [sda] Unhandled sense code
[  338.592029] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  338.592035] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  338.592043] Descriptor sense data with sense descriptors (in hex):
[  338.592046]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  338.592066]         18 51 ce ee 
[  338.592074] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  338.592082] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  338.592100] end_request: I/O error, dev sda, sector 408014574
[  338.592116] ata3: EH complete
[  341.093307] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  341.093314] ata3.00: irq_stat 0x40000008
[  341.093319] ata3.00: failed command: READ FPDMA QUEUED
[  341.093329] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  341.093331]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  341.093336] ata3.00: status: { DRDY ERR }
[  341.093340] ata3.00: error: { UNC }
[  341.097667] ata3.00: configured for UDMA/133
[  341.097679] ata3: EH complete
[  343.521444] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  343.521450] ata3.00: irq_stat 0x40000008
[  343.521462] ata3.00: failed command: READ FPDMA QUEUED
[  343.521470] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  343.521472]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  343.521475] ata3.00: status: { DRDY ERR }
[  343.521478] ata3.00: error: { UNC }
[  343.525768] ata3.00: configured for UDMA/133
[  343.525782] ata3: EH complete
[  345.971774] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  345.971779] ata3.00: irq_stat 0x40000008
[  345.971784] ata3.00: failed command: READ FPDMA QUEUED
[  345.971799] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  345.971800]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  345.971804] ata3.00: status: { DRDY ERR }
[  345.971807] ata3.00: error: { UNC }
[  345.976132] ata3.00: configured for UDMA/133
[  345.976152] ata3: EH complete
[  348.410959] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  348.410965] ata3.00: irq_stat 0x40000008
[  348.410970] ata3.00: failed command: READ FPDMA QUEUED
[  348.410980] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  348.410982]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  348.410987] ata3.00: status: { DRDY ERR }
[  348.410991] ata3.00: error: { UNC }
[  348.415299] ata3.00: configured for UDMA/133
[  348.415311] ata3: EH complete
[  350.872331] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  350.872338] ata3.00: irq_stat 0x40000008
[  350.872344] ata3.00: failed command: READ FPDMA QUEUED
[  350.872358] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  350.872359]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  350.872363] ata3.00: status: { DRDY ERR }
[  350.872366] ata3.00: error: { UNC }
[  350.876657] ata3.00: configured for UDMA/133
[  350.876672] ata3: EH complete
[  353.322550] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  353.322556] ata3.00: irq_stat 0x40000008
[  353.322562] ata3.00: failed command: READ FPDMA QUEUED
[  353.322572] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  353.322574]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  353.322579] ata3.00: status: { DRDY ERR }
[  353.322583] ata3.00: error: { UNC }
[  353.326887] ata3.00: configured for UDMA/133
[  353.326907] sd 2:0:0:0: [sda] Unhandled sense code
[  353.326910] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  353.326916] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  353.326925] Descriptor sense data with sense descriptors (in hex):
[  353.326928]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  353.326945]         18 51 ce ee 
[  353.326953] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  353.326962] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  353.326978] end_request: I/O error, dev sda, sector 408014574
[  353.327002] ata3: EH complete
[  355.835582] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  355.835589] ata3.00: irq_stat 0x40000008
[  355.835595] ata3.00: failed command: READ FPDMA QUEUED
[  355.835605] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  355.835607]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  355.835612] ata3.00: status: { DRDY ERR }
[  355.835616] ata3.00: error: { UNC }
[  355.839916] ata3.00: configured for UDMA/133
[  355.839930] ata3: EH complete
[  359.919504] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  359.919511] ata3.00: irq_stat 0x40000008
[  359.919522] ata3.00: failed command: READ FPDMA QUEUED
[  359.919530] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  359.919532]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  359.919535] ata3.00: status: { DRDY ERR }
[  359.919538] ata3.00: error: { UNC }
[  359.923836] ata3.00: configured for UDMA/133
[  359.923849] ata3: EH complete
[  364.010638] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  364.010644] ata3.00: irq_stat 0x40000008
[  364.010649] ata3.00: failed command: READ FPDMA QUEUED
[  364.010660] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  364.010662]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  364.010666] ata3.00: status: { DRDY ERR }
[  364.010670] ata3.00: error: { UNC }
[  364.014977] ata3.00: configured for UDMA/133
[  364.014991] ata3: EH complete
[  368.090722] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  368.090729] ata3.00: irq_stat 0x40000008
[  368.090735] ata3.00: failed command: READ FPDMA QUEUED
[  368.090748] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  368.090750]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  368.090754] ata3.00: status: { DRDY ERR }
[  368.090756] ata3.00: error: { UNC }
[  368.095077] ata3.00: configured for UDMA/133
[  368.095091] ata3: EH complete
[  370.563254] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  370.563260] ata3.00: irq_stat 0x40000008
[  370.563266] ata3.00: failed command: READ FPDMA QUEUED
[  370.563276] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  370.563279]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  370.563284] ata3.00: status: { DRDY ERR }
[  370.563288] ata3.00: error: { UNC }
[  370.567594] ata3.00: configured for UDMA/133
[  370.567608] ata3: EH complete
[  372.980229] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  372.980236] ata3.00: irq_stat 0x40000008
[  372.980242] ata3.00: failed command: READ FPDMA QUEUED
[  372.980255] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  372.980257]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  372.980261] ata3.00: status: { DRDY ERR }
[  372.980264] ata3.00: error: { UNC }
[  372.984563] ata3.00: configured for UDMA/133
[  372.984584] sd 2:0:0:0: [sda] Unhandled sense code
[  372.984587] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  372.984591] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  372.984597] Descriptor sense data with sense descriptors (in hex):
[  372.984600]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  372.984613]         18 51 ce ee 
[  372.984618] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  372.984626] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  372.984637] end_request: I/O error, dev sda, sector 408014574
[  372.984658] ata3: EH complete
[  377.204476] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  377.204482] ata3.00: irq_stat 0x40000008
[  377.204489] ata3.00: failed command: READ FPDMA QUEUED
[  377.204499] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  377.204501]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  377.204506] ata3.00: status: { DRDY ERR }
[  377.204510] ata3.00: error: { UNC }
[  377.208839] ata3.00: configured for UDMA/133
[  377.208850] ata3: EH complete
[  379.654698] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  379.654703] ata3.00: irq_stat 0x40000008
[  379.654708] ata3.00: failed command: READ FPDMA QUEUED
[  379.654723] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  379.654725]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  379.654729] ata3.00: status: { DRDY ERR }
[  379.654731] ata3.00: error: { UNC }
[  379.659029] ata3.00: configured for UDMA/133
[  379.659039] ata3: EH complete
[  382.105017] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  382.105022] ata3.00: irq_stat 0x40000008
[  382.105027] ata3.00: failed command: READ FPDMA QUEUED
[  382.105042] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  382.105043]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  382.105047] ata3.00: status: { DRDY ERR }
[  382.105050] ata3.00: error: { UNC }
[  382.109342] ata3.00: configured for UDMA/133
[  382.109351] ata3: EH complete
[  384.566365] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  384.566370] ata3.00: irq_stat 0x40000008
[  384.566375] ata3.00: failed command: READ FPDMA QUEUED
[  384.566386] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  384.566388]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  384.566393] ata3.00: status: { DRDY ERR }
[  384.566396] ata3.00: error: { UNC }
[  384.570705] ata3.00: configured for UDMA/133
[  384.570714] ata3: EH complete
[  387.060956] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  387.060961] ata3.00: irq_stat 0x40000008
[  387.060965] ata3.00: failed command: READ FPDMA QUEUED
[  387.060976] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  387.060978]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  387.060983] ata3.00: status: { DRDY ERR }
[  387.060986] ata3.00: error: { UNC }
[  387.065280] ata3.00: configured for UDMA/133
[  387.065289] ata3: EH complete
[  389.511306] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  389.511311] ata3.00: irq_stat 0x40000008
[  389.511316] ata3.00: failed command: READ FPDMA QUEUED
[  389.511331] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  389.511333]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  389.511337] ata3.00: status: { DRDY ERR }
[  389.511339] ata3.00: error: { UNC }
[  389.515632] ata3.00: configured for UDMA/133
[  389.515644] sd 2:0:0:0: [sda] Unhandled sense code
[  389.515648] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  389.515654] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  389.515667] Descriptor sense data with sense descriptors (in hex):
[  389.515670]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  389.515683]         18 51 ce ee 
[  389.515688] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  389.515696] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  389.515707] end_request: I/O error, dev sda, sector 408014574
[  389.515725] ata3: EH complete
[  391.983700] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  391.983706] ata3.00: irq_stat 0x40000008
[  391.983711] ata3.00: failed command: READ FPDMA QUEUED
[  391.983726] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  391.983728]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  391.983732] ata3.00: status: { DRDY ERR }
[  391.983734] ata3.00: error: { UNC }
[  391.988037] ata3.00: configured for UDMA/133
[  391.988047] ata3: EH complete
[  394.445069] ata3.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  394.445075] ata3.00: irq_stat 0x40000008
[  394.445080] ata3.00: failed command: READ FPDMA QUEUED
[  394.445095] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  394.445096]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  394.445100] ata3.00: status: { DRDY ERR }
[  394.445103] ata3.00: error: { UNC }
[  394.449390] ata3.00: configured for UDMA/133
[  394.449405] ata3: EH complete
[  396.917591] ata3.00: exception Emask 0x0 SAct 0xa SErr 0x0 action 0x0
[  396.917597] ata3.00: irq_stat 0x40000008
[  396.917602] ata3.00: failed command: READ FPDMA QUEUED
[  396.917617] ata3.00: cmd 60/08:18:e8:ce:51/00:00:18:00:00/40 tag 3 ncq 4096 in
[  396.917618]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  396.917622] ata3.00: status: { DRDY ERR }
[  396.917625] ata3.00: error: { UNC }
[  396.921889] ata3.00: configured for UDMA/133
[  396.921901] ata3: EH complete
[  401.019858] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  401.019864] ata3.00: irq_stat 0x40000008
[  401.019870] ata3.00: failed command: READ FPDMA QUEUED
[  401.019883] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  401.019885]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  401.019889] ata3.00: status: { DRDY ERR }
[  401.019891] ata3.00: error: { UNC }
[  401.024218] ata3.00: configured for UDMA/133
[  401.024232] ata3: EH complete
[  403.503426] ata3.00: exception Emask 0x0 SAct 0xf SErr 0x0 action 0x0
[  403.503432] ata3.00: irq_stat 0x40000008
[  403.503437] ata3.00: failed command: READ FPDMA QUEUED
[  403.503447] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  403.503449]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  403.503454] ata3.00: status: { DRDY ERR }
[  403.503458] ata3.00: error: { UNC }
[  403.507759] ata3.00: configured for UDMA/133
[  403.507775] ata3: EH complete
[  406.042376] ata3.00: exception Emask 0x0 SAct 0x5 SErr 0x0 action 0x0
[  406.042382] ata3.00: irq_stat 0x40000008
[  406.042388] ata3.00: failed command: READ FPDMA QUEUED
[  406.042402] ata3.00: cmd 60/08:10:e8:ce:51/00:00:18:00:00/40 tag 2 ncq 4096 in
[  406.042403]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  406.042407] ata3.00: status: { DRDY ERR }
[  406.042410] ata3.00: error: { UNC }
[  406.046731] ata3.00: configured for UDMA/133
[  406.046748] sd 2:0:0:0: [sda] Unhandled sense code
[  406.046752] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  406.046764] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  406.046770] Descriptor sense data with sense descriptors (in hex):
[  406.046773]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  406.046786]         18 51 ce ee 
[  406.046791] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  406.046798] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  406.046810] end_request: I/O error, dev sda, sector 408014574
[  406.046826] ata3: EH complete
[  409.157863] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  409.157870] ata3.00: irq_stat 0x40000008
[  409.157882] ata3.00: failed command: READ FPDMA QUEUED
[  409.157890] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  409.157891]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  409.157895] ata3.00: status: { DRDY ERR }
[  409.157898] ata3.00: error: { UNC }
[  409.162190] ata3.00: configured for UDMA/133
[  409.162200] ata3: EH complete
[  413.249105] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  413.249110] ata3.00: irq_stat 0x40000008
[  413.249116] ata3.00: failed command: READ FPDMA QUEUED
[  413.249130] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  413.249132]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  413.249136] ata3.00: status: { DRDY ERR }
[  413.249138] ata3.00: error: { UNC }
[  413.253428] ata3.00: configured for UDMA/133
[  413.253439] ata3: EH complete
[  415.710459] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  415.710464] ata3.00: irq_stat 0x40000008
[  415.710469] ata3.00: failed command: READ FPDMA QUEUED
[  415.710484] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  415.710486]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  415.710489] ata3.00: status: { DRDY ERR }
[  415.710492] ata3.00: error: { UNC }
[  415.714781] ata3.00: configured for UDMA/133
[  415.714791] ata3: EH complete
[  418.160684] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  418.160690] ata3.00: irq_stat 0x40000008
[  418.160695] ata3.00: failed command: READ FPDMA QUEUED
[  418.160705] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  418.160707]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  418.160713] ata3.00: status: { DRDY ERR }
[  418.160716] ata3.00: error: { UNC }
[  418.165008] ata3.00: configured for UDMA/133
[  418.165020] ata3: EH complete
[  420.622051] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  420.622056] ata3.00: irq_stat 0x40000008
[  420.622061] ata3.00: failed command: READ FPDMA QUEUED
[  420.622076] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  420.622078]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  420.622081] ata3.00: status: { DRDY ERR }
[  420.622084] ata3.00: error: { UNC }
[  420.626351] ata3.00: configured for UDMA/133
[  420.626360] ata3: EH complete
[  423.061217] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  423.061223] ata3.00: irq_stat 0x40000008
[  423.061228] ata3.00: failed command: READ FPDMA QUEUED
[  423.061243] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  423.061244]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  423.061248] ata3.00: status: { DRDY ERR }
[  423.061251] ata3.00: error: { UNC }
[  423.065538] ata3.00: configured for UDMA/133
[  423.065552] sd 2:0:0:0: [sda] Unhandled sense code
[  423.065556] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  423.065562] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  423.065575] Descriptor sense data with sense descriptors (in hex):
[  423.065578]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  423.065591]         18 51 ce ee 
[  423.065596] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  423.065603] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  423.065615] end_request: I/O error, dev sda, sector 408014574
[  423.065635] ata3: EH complete
[  425.511531] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  425.511536] ata3.00: irq_stat 0x40000008
[  425.511541] ata3.00: failed command: READ FPDMA QUEUED
[  425.511552] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  425.511554]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  425.511559] ata3.00: status: { DRDY ERR }
[  425.511563] ata3.00: error: { UNC }
[  425.515853] ata3.00: configured for UDMA/133
[  425.515862] ata3: EH complete
[  427.958467] ata3: failed to read log page 10h (errno=-5)
[  427.958475] ata3.00: exception Emask 0x1 SAct 0xf SErr 0x0 action 0x0
[  427.958479] ata3.00: irq_stat 0x40000008
[  427.958484] ata3.00: failed command: READ FPDMA QUEUED
[  427.958494] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  427.958496]          res 40/00:10:80:70:48/00:00:18:00:00/40 Emask 0x1 (device error)
[  427.958501] ata3.00: status: { DRDY }
[  427.958505] ata3.00: failed command: READ FPDMA QUEUED
[  427.958515] ata3.00: cmd 60/20:08:60:bb:39/00:00:18:00:00/40 tag 1 ncq 16384 in
[  427.958517]          res 40/00:10:80:70:48/00:00:18:00:00/40 Emask 0x1 (device error)
[  427.958522] ata3.00: status: { DRDY }
[  427.958526] ata3.00: failed command: READ FPDMA QUEUED
[  427.958535] ata3.00: cmd 60/08:10:80:70:48/00:00:18:00:00/40 tag 2 ncq 4096 in
[  427.958537]          res 40/00:10:80:70:48/00:00:18:00:00/40 Emask 0x1 (device error)
[  427.958542] ata3.00: status: { DRDY }
[  427.958546] ata3.00: failed command: READ FPDMA QUEUED
[  427.958561] ata3.00: cmd 60/30:18:90:70:48/00:00:18:00:00/40 tag 3 ncq 24576 in
[  427.958562]          res 40/00:10:80:70:48/00:00:18:00:00/40 Emask 0x1 (device error)
[  427.958564] ata3.00: status: { DRDY }
[  427.961708] ata3.00: model number mismatch 'ST9250827AS' != ''
[  427.961713] ata3.00: revalidation failed (errno=-19)
[  427.961720] ata3.00: limiting speed to UDMA/133:PIO2
[  427.961727] ata3: hard resetting link
[  428.280275] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  428.281827] ata3.00: configured for UDMA/133
[  428.281843] ata3: EH complete
[  432.385567] ata3.00: exception Emask 0x0 SAct 0x9 SErr 0x0 action 0x0
[  432.385572] ata3.00: irq_stat 0x40000008
[  432.385578] ata3.00: failed command: READ FPDMA QUEUED
[  432.385592] ata3.00: cmd 60/08:18:e8:ce:51/00:00:18:00:00/40 tag 3 ncq 4096 in
[  432.385594]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  432.385598] ata3.00: status: { DRDY ERR }
[  432.385600] ata3.00: error: { UNC }
[  432.389889] ata3.00: configured for UDMA/133
[  432.389902] ata3: EH complete
[  436.454625] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  436.454631] ata3.00: irq_stat 0x40000008
[  436.454636] ata3.00: failed command: READ FPDMA QUEUED
[  436.454646] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  436.454648]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  436.454653] ata3.00: status: { DRDY ERR }
[  436.454657] ata3.00: error: { UNC }
[  436.458954] ata3.00: configured for UDMA/133
[  436.458966] ata3: EH complete
[  438.915995] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  438.916001] ata3.00: irq_stat 0x40000008
[  438.916027] ata3.00: failed command: READ FPDMA QUEUED
[  438.916035] ata3.00: cmd 60/08:08:e8:ce:51/00:00:18:00:00/40 tag 1 ncq 4096 in
[  438.916037]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  438.916042] ata3.00: status: { DRDY ERR }
[  438.916045] ata3.00: error: { UNC }
[  438.920331] ata3.00: configured for UDMA/133
[  438.920349] ata3: EH complete
[  441.388497] ata3.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x0
[  441.388502] ata3.00: irq_stat 0x40000008
[  441.388507] ata3.00: failed command: READ FPDMA QUEUED
[  441.388522] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  441.388523]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  441.388527] ata3.00: status: { DRDY ERR }
[  441.388530] ata3.00: error: { UNC }
[  441.392825] ata3.00: configured for UDMA/133
[  441.392838] sd 2:0:0:0: [sda] Unhandled sense code
[  441.392842] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  441.392848] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  441.392855] Descriptor sense data with sense descriptors (in hex):
[  441.392859]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  441.392876]         18 51 ce ee 
[  441.392883] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  441.392892] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  441.392908] end_request: I/O error, dev sda, sector 408014574
[  441.392932] ata3: EH complete
[  443.876417] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  443.876423] ata3.00: irq_stat 0x40000008
[  443.876428] ata3.00: failed command: READ FPDMA QUEUED
[  443.876443] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  443.876444]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  443.876448] ata3.00: status: { DRDY ERR }
[  443.876451] ata3.00: error: { UNC }
[  443.880801] ata3.00: configured for UDMA/133
[  443.880812] ata3: EH complete
[  446.322247] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  446.322252] ata3.00: irq_stat 0x40000008
[  446.322257] ata3.00: failed command: READ FPDMA QUEUED
[  446.322267] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  446.322269]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  446.322274] ata3.00: status: { DRDY ERR }
[  446.322278] ata3.00: error: { UNC }
[  446.326588] ata3.00: configured for UDMA/133
[  446.326598] ata3: EH complete
[  448.772473] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  448.772478] ata3.00: irq_stat 0x40000008
[  448.772483] ata3.00: failed command: READ FPDMA QUEUED
[  448.772498] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  448.772499]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  448.772503] ata3.00: status: { DRDY ERR }
[  448.772506] ata3.00: error: { UNC }
[  448.776915] ata3.00: configured for UDMA/133
[  448.776925] ata3: EH complete
[  452.819346] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  452.819351] ata3.00: irq_stat 0x40000008
[  452.819356] ata3.00: failed command: READ FPDMA QUEUED
[  452.819371] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  452.819373]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  452.819377] ata3.00: status: { DRDY ERR }
[  452.819379] ata3.00: error: { UNC }
[  452.823670] ata3.00: configured for UDMA/133
[  452.823680] ata3: EH complete
[  455.280738] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  455.280743] ata3.00: irq_stat 0x40000008
[  455.280748] ata3.00: failed command: READ FPDMA QUEUED
[  455.280763] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  455.280765]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  455.280769] ata3.00: status: { DRDY ERR }
[  455.280771] ata3.00: error: { UNC }
[  455.285064] ata3.00: configured for UDMA/133
[  455.285074] ata3: EH complete
[  457.742038] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  457.742043] ata3.00: irq_stat 0x40000008
[  457.742048] ata3.00: failed command: READ FPDMA QUEUED
[  457.742058] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  457.742061]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  457.742066] ata3.00: status: { DRDY ERR }
[  457.742070] ata3.00: error: { UNC }
[  457.746377] ata3.00: configured for UDMA/133
[  457.746388] sd 2:0:0:0: [sda] Unhandled sense code
[  457.746392] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  457.746398] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  457.746405] Descriptor sense data with sense descriptors (in hex):
[  457.746408]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  457.746425]         18 51 ce ee 
[  457.746433] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  457.746442] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  457.746457] end_request: I/O error, dev sda, sector 408014574
[  457.746475] ata3: EH complete
[  460.225649] ata3.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  460.225654] ata3.00: irq_stat 0x40000008
[  460.225659] ata3.00: failed command: READ FPDMA QUEUED
[  460.225674] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  460.225675]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  460.225679] ata3.00: status: { DRDY ERR }
[  460.225682] ata3.00: error: { UNC }
[  460.229979] ata3.00: configured for UDMA/133
[  460.229989] ata3: EH complete
[  464.339065] ata3.00: exception Emask 0x0 SAct 0x1f SErr 0x0 action 0x0
[  464.339070] ata3.00: irq_stat 0x40000008
[  464.339075] ata3.00: failed command: READ FPDMA QUEUED
[  464.339090] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  464.339091]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  464.339095] ata3.00: status: { DRDY ERR }
[  464.339098] ata3.00: error: { UNC }
[  464.343385] ata3.00: configured for UDMA/133
[  464.343402] ata3: EH complete
[  464.360074] CE: hpet increased min_delta_ns to 20113 nsec
[  466.832720] ata3.00: exception Emask 0x0 SAct 0x19 SErr 0x0 action 0x0
[  466.832726] ata3.00: irq_stat 0x40000008
[  466.832731] ata3.00: failed command: READ FPDMA QUEUED
[  466.832745] ata3.00: cmd 60/08:20:e8:ce:51/00:00:18:00:00/40 tag 4 ncq 4096 in
[  466.832747]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  466.832751] ata3.00: status: { DRDY ERR }
[  466.832753] ata3.00: error: { UNC }
[  466.837002] ata3.00: configured for UDMA/133
[  466.837016] ata3: EH complete
[  469.295005] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  469.295010] ata3.00: irq_stat 0x40000008
[  469.295015] ata3.00: failed command: READ FPDMA QUEUED
[  469.295025] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  469.295027]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  469.295032] ata3.00: status: { DRDY ERR }
[  469.295036] ata3.00: error: { UNC }
[  469.299346] ata3.00: configured for UDMA/133
[  469.299359] ata3: EH complete
[  471.778555] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  471.778560] ata3.00: irq_stat 0x40000008
[  471.778565] ata3.00: failed command: READ FPDMA QUEUED
[  471.778576] ata3.00: cmd 60/08:10:e8:ce:51/00:00:18:00:00/40 tag 2 ncq 4096 in
[  471.778578]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  471.778583] ata3.00: status: { DRDY ERR }
[  471.778587] ata3.00: error: { UNC }
[  471.782883] ata3.00: configured for UDMA/133
[  471.782896] ata3: EH complete
[  474.317522] ata3.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[  474.317528] ata3.00: irq_stat 0x40000008
[  474.317533] ata3.00: failed command: READ FPDMA QUEUED
[  474.317548] ata3.00: cmd 60/08:00:e8:ce:51/00:00:18:00:00/40 tag 0 ncq 4096 in
[  474.317549]          res 41/40:08:ee:ce:51/00:00:18:00:00/40 Emask 0x409 (media error) <F>
[  474.317553] ata3.00: status: { DRDY ERR }
[  474.317556] ata3.00: error: { UNC }
[  474.321848] ata3.00: configured for UDMA/133
[  474.321860] sd 2:0:0:0: [sda] Unhandled sense code
[  474.321864] sd 2:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  474.321869] sd 2:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
[  474.321883] Descriptor sense data with sense descriptors (in hex):
[  474.321886]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  474.321899]         18 51 ce ee 
[  474.321904] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  474.321911] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 18 51 ce e8 00 00 08 00
[  474.321923] end_request: I/O error, dev sda, sector 408014574
[  474.321937] ata3: EH complete
[  497.973702] wlan0: authenticate with 00:1f:b3:c5:fb:71 (try 1)
[  497.976312] wlan0: authenticated
[  497.976389] wlan0: associate with 00:1f:b3:c5:fb:71 (try 1)
[  498.176032] wlan0: associate with 00:1f:b3:c5:fb:71 (try 2)
[  498.177793] wlan0: RX AssocResp from 00:1f:b3:c5:fb:71 (capab=0x31 status=0 aid=1)
[  498.177796] wlan0: associated
[  498.203600] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  498.205594] cfg80211: Calling CRDA for country: US
[  498.208799] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  498.208802] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208804] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  498.208806] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208808] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  498.208810] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208812] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  498.208815] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208817] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  498.208819] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208821] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  498.208823] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208825] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  498.208827] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208829] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  498.208832] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208834] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  498.208836] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208838] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  498.208840] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208842] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  498.208844] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  498.208846] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  498.208849] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  498.208851] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  498.208853] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  498.208855] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  498.208858] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  498.208860] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  498.208862] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  498.208864] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[  498.208866] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  498.208868] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[  498.208870] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  498.208872] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[  498.208875] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  498.208877] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[  498.208879] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  498.208881] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  498.208883] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  498.208885] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  498.208887] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  498.208889] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  498.208892] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  498.208894] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  498.208896] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  498.208898] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  498.208900] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  498.208903] cfg80211: Regulatory domain changed to country: US
[  498.208904] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  498.208907] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  498.208909] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  498.208911] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  498.208913] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  498.208916] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  498.208918] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  508.400245] wlan0: no IPv6 routers present
[  577.450089] exe (3424): /proc/3424/oom_adj is deprecated, please use /proc/3424/oom_score_adj instead.

```

I am a newbie to Ubuntu, but I really love it! I don't want to go back to windows ](*,).

Any help will be greatly appreciated! (sorry for my terrible English)

---

### Post by dino99 on 2011-09-16
you got: " failed command: READ FPDMA QUEUED "

which is related to the chipset used on your mobo (marvell). Read the mobo doc about how to plug hardware and look at bios settings.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550559)

---

### Post by NedNguyen on 2011-09-16
I am sorry for my ignorance but could you please be more specific dino99 (I don't have much knowledge with hardware and OS :sad)? 

My machine is a Dell XPS M1530 laptop. From the link you give, I find this post: [http://ubuntuforums.org/showpost.php?p=9684933&postcount=12](http://ubuntuforums.org/showpost.php?p=9684933&postcount=12)

I am not sure whether this maybe a fix for my case.

---

