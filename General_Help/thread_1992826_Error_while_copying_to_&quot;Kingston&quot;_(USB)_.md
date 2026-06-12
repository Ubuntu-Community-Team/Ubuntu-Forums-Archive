---
title: "Error while copying to &quot;Kingston&quot; (USB) The destination is read-only"
date: 2012-05-31
forum: General Help
---

### Post by edwardtagg on 2012-05-31
Error while copying to "Kingston" (USB) The destination is read-only
 	I have been using this USB for 1 month with no problems but now it wont let me copy any file (large or small) into it ...
 	I right click and PERMISSIONS says ..."The permissions of "Kingston" could not be determined"
 	This started after I did some updates with the orange triangle at  the top left of the screen.... Updates always say that errors occur in  part of the process...? confused....
 	Please help - I am a newbie, and can only do basic terminal language....
 	You are using Ubuntu 10.04 LTS
	- the Lucid Lynx - released in April 2010 and supported until April 2013. (copied from "ABOUT UBUNTU")
 	This problem plagues other people, and all the other forums seem to fail to help?
 	Really appreciate the help - bless - Edward James Tagg

---

### Post by dcstar on 2012-06-01
> **edwardtagg said:**
> Error while copying to "Kingston" (USB) The destination is read-only
 	I have been using this USB for 1 month with no problems but now it wont let me copy any file (large or small) into it ...
.........

Use **gparted** to do a "check" on the partition.

---

### Post by drpjkurian on 2012-06-01
Please try this command ```
sudo nautilus
``` and then try to paste thr file to USB stick

---

### Post by Sularco on 2012-06-01
I had a USB stick once which I used successfully for a while. One day it produced exactly the same error as edwardtagg experienced. I fiddled for ages with it until I discovered that it had a really tiny mechanical switch at one side to set the device between read only and read/write - and I had by accident moved that switch without even knowing that it was there.

I just mention this because I know first hand that these things do happen...

---

### Post by raja.genupula on 2012-06-01
[https://help.ubuntu.com/community/Mount/USB#USB-Device_is.2C_or_become_suddenly_read_only_without_errors](https://help.ubuntu.com/community/Mount/USB#USB-Device_is.2C_or_become_suddenly_read_only_without_errors)

---

### Post by kurt18947 on 2012-06-01
> **Sularco said:**
> I had a USB stick once which I used successfully for a while. One day it produced exactly the same error as edwardtagg experienced. I fiddled for ages with it until I discovered that it had a really tiny mechanical switch at one side to set the device between read only and read/write - and I had by accident moved that switch without even knowing that it was there.

I just mention this because I know first hand that these things do happen...

That was my thought .............

---

### Post by edwardtagg on 2012-06-05
> **drpjkurian said:**
> Please try this command ```
sudo nautilus
``` and then try to paste thr file to USB stick

I did and got this...

Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Bless - Edward James Tagg

---

### Post by edwardtagg on 2012-06-05
> **kurt18947 said:**
> That was my thought .............


No such switch on my USB - thanks for you suggestion...?

Bless - Edward James Tagg

---

### Post by edwardtagg on 2012-06-05
> **raja.genupula said:**
> [https://help.ubuntu.com/community/Mount/USB#USB-Device_is.2C_or_become_suddenly_read_only_without_errors](https://help.ubuntu.com/community/Mount/USB#USB-Device_is.2C_or_become_suddenly_read_only_without_errors)


Dear Raja - I took your advice and got this print out... hope someone can translate - I am a newbie... Gee higgedy dog.....?

[    0.270241] ACPI: Power Button [PWRB]
[    0.270337] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.270343] ACPI: Power Button [PWRF]
[    0.270651] processor LNXCPU:00: registered as cooling_device0
[    0.297576] isapnp: Scanning for PnP cards...
[    0.303820] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.304038] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.304254] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.304815] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.305092] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.307267] brd: module loaded
[    0.308297] loop: module loaded
[    0.308637] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.357849] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.357878] pata_acpi 0000:00:07.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.357888] pata_acpi 0000:00:07.1: VIA VLink IRQ fixup, from 0 to 11
[    0.358067] pata_acpi 0000:00:07.1: PCI INT A disabled
[    0.358749] Fixed MDIO Bus: probed
[    0.358815] PPP generic driver version 2.4.2
[    0.359018] tun: Universal TUN/TAP device driver, 1.6
[    0.359022] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.359308] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.359374] ehci_hcd 0000:00:0e.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.359426] ehci_hcd 0000:00:0e.2: EHCI Host Controller
[    0.359518] ehci_hcd 0000:00:0e.2: new USB bus registered, assigned bus number 1
[    0.381185] ehci_hcd 0000:00:0e.2: irq 19, io mem 0xf4800000
[    0.393532] ehci_hcd 0000:00:0e.2: USB 2.0 started, EHCI 0.95
[    0.393917] usb usb1: configuration #1 chosen from 1 choice
[    0.393989] hub 1-0:1.0: USB hub found
[    0.394029] hub 1-0:1.0: 5 ports detected
[    0.394193] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.394248] ohci_hcd 0000:00:0e.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.394301] ohci_hcd 0000:00:0e.0: OHCI Host Controller
[    0.394461] ohci_hcd 0000:00:0e.0: new USB bus registered, assigned bus number 2
[    0.394560] ohci_hcd 0000:00:0e.0: irq 17, io mem 0xf5800000
[    1.303697] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.476197] isapnp: No Plug & Play device found
[    1.584258] Freeing initrd memory: 7767k freed
[    1.614902] usb usb2: configuration #1 chosen from 1 choice
[    1.614976] hub 2-0:1.0: USB hub found
[    1.615036] hub 2-0:1.0: 3 ports detected
[    1.615176] ohci_hcd 0000:00:0e.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.615228] ohci_hcd 0000:00:0e.1: OHCI Host Controller
[    1.615364] ohci_hcd 0000:00:0e.1: new USB bus registered, assigned bus number 3
[    1.615459] ohci_hcd 0000:00:0e.1: irq 18, io mem 0xf5000000
[    2.174345] usb usb3: configuration #1 chosen from 1 choice
[    2.174434] hub 3-0:1.0: USB hub found
[    2.174470] hub 3-0:1.0: 2 ports detected
[    2.174590] uhci_hcd: USB Universal Host Controller Interface driver
[    2.174735] uhci_hcd 0000:00:07.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    2.174761] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    2.174914] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 4
[    2.175000] uhci_hcd 0000:00:07.2: irq 21, io base 0x0000d400
[    2.175345] usb usb4: configuration #1 chosen from 1 choice
[    2.175409] hub 4-0:1.0: USB hub found
[    2.175441] hub 4-0:1.0: 2 ports detected
[    2.175558] uhci_hcd 0000:00:07.3: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    2.175581] uhci_hcd 0000:00:07.3: UHCI Host Controller
[    2.175708] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 5
[    2.175752] uhci_hcd 0000:00:07.3: irq 21, io base 0x0000d000
[    2.176198] usb usb5: configuration #1 chosen from 1 choice
[    2.176271] hub 5-0:1.0: USB hub found
[    2.176304] hub 5-0:1.0: 2 ports detected
[    2.176522] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.176528] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.176781] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.177138] mice: PS/2 mouse device common for all mice
[    2.177442] rtc_cmos 00:05: RTC can wake from S4
[    2.177593] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.177663] rtc0: alarms up to one year, 242 bytes nvram
[    2.177872] device-mapper: uevent: version 1.0.3
[    2.178307] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    2.178544] device-mapper: multipath: version 1.1.0 loaded
[    2.178553] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.178922] EISA: Probing bus 0 at eisa.0
[    2.178984] EISA: Detected 0 cards.
[    2.179369] usb 1-2: configuration #1 chosen from 1 choice
[    2.179986] cpuidle: using governor ladder
[    2.179993] cpuidle: using governor menu
[    2.180872] TCP cubic registered
[    2.181251] NET: Registered protocol family 10
[    2.182708] NET: Registered protocol family 17
[    2.182835] powernow-k8: Processor cpuid 671 not supported
[    2.182899] Using IPI No-Shortcut mode
[    2.183228] PM: Resume from disk failed.
[    2.183263] registered taskstats version 1
[    2.183651]   Magic number: 0:862:385
[    2.183679] usb usb3: hash matches
[    2.183781] thermal cooling_device0: hash matches
[    2.183906] rtc_cmos 00:05: setting system clock to 2012-06-06 15:23:50 UTC (1338996230)
[    2.183912] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.183915] EDD information not available.
[    2.184153] Freeing unused kernel memory: 680k freed
[    2.186956] Write protecting the kernel text: 4856k
[    2.187066] Write protecting the kernel read-only data: 1884k
[    2.198562] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.258616] udev: starting version 151
[    2.344155] usb 1-4: new high speed USB device using ehci_hcd and address 5
[    2.481544] usb 1-4: configuration #1 chosen from 1 choice
[    2.656211] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    2.747959] pata_via 0000:00:07.1: version 0.3.4
[    2.748034] pata_via 0000:00:07.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    2.748045] pata_via 0000:00:07.1: VIA VLink IRQ fixup, from 0 to 11
[    2.776602] scsi0 : pata_via
[    2.779911] scsi1 : pata_via
[    2.781196] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xd800 irq 14
[    2.781205] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xd808 irq 15
[    2.826018] Initializing USB Mass Storage driver...
[    2.834638] Floppy drive(s): fd0 is 1.44M
[    2.840167] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.845981] usbcore: registered new interface driver usb-storage
[    2.845990] USB Mass Storage support registered.
[    2.846012] usb-storage: device found at 5
[    2.846015] usb-storage: waiting for device to settle before scanning
[    2.851926] FDC 0 is a post-1991 82077
[    2.874005] usb 2-1: configuration #1 chosen from 1 choice
[    2.948551] ata1.00: ATA-7: Maxtor 2F040J0, VAM51JJ0, max UDMA/133
[    2.948561] ata1.00: 80293248 sectors, multi 16: LBA 
[    2.964374] ata1.00: configured for UDMA/100
[    2.964719] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2F040J0   VAM5 PQ: 0 ANSI: 5
[    2.965187] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.966171] sd 0:0:0:0: [sda] 80293248 512-byte logical blocks: (41.1 GB/38.2 GiB)
[    2.966279] sd 0:0:0:0: [sda] Write Protect is off
[    2.966284] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.966335] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.966757]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.044978] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.128409] ata2.00: ATAPI: CD-ROM F565E,  1.07, max UDMA/66
[    3.128449] ata2.00: limited to UDMA/33 due to 40-wire cable
[    3.136239] ata2.00: configured for UDMA/33
[    3.137183] scsi 1:0:0:0: CD-ROM                     CD-ROM F565E     1.07 PQ: 0 ANSI: 5
[    3.141067] sr0: scsi3-mmc drive: 0x/40x cd/rw xa/form2 cdda tray
[    3.141081] Uniform CD-ROM driver Revision: 3.20
[    3.142151] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.142824] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.177104] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.177196] 8139cp 0000:00:12.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.180146] usb 2-2: new low speed USB device using ohci_hcd and address 3
[    3.229071] usbcore: registered new interface driver hiddev
[    3.237109] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0e.0/usb2/2-1/2-1:1.0/input/input4
[    3.237984] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0e.0-1/input0
[    3.238083] usbcore: registered new interface driver usbhid
[    3.238507] usbhid: v2.6:USB HID core driver
[    3.244119] 8139too Fast Ethernet driver 0.9.28
[    3.244248] 8139too 0000:00:12.0: enabling device (0004 -> 0007)
[    3.244267] 8139too 0000:00:12.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.245992] eth0: RealTek RTL8139 at 0xa000, 00:e0:18:74:b9:2a, IRQ 17
[    3.423010] usb 2-2: configuration #1 chosen from 1 choice
[    3.457874] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:0e.0/usb2/2-2/2-2:1.0/input/input5
[    3.458866] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:0e.0-2/input0
[    3.477944] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:0e.0/usb2/2-2/2-2:1.1/input/input6
[    3.479868] microsoft 0003:045E:00DB.0003: input,hidraw2: USB HID v1.11 Device [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:0e.0-2/input1
[    3.536093] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    3.683023] usb 4-2: not running at top speed; connect to a high speed hub
[    3.714274] usb 4-2: configuration #1 chosen from 1 choice
[    3.722945] scsi3 : SCSI emulation for USB Mass Storage devices
[    3.724335] usb-storage: device found at 2
[    3.724342] usb-storage: waiting for device to settle before scanning
[    3.954853] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    7.844793] usb-storage: device scan complete
[    7.845688] scsi 2:0:0:0: Direct-Access     SONY     IC RECORDER      3.00 PQ: 0 ANSI: 0 CCS
[    7.846767] scsi 2:0:0:1: Direct-Access     SONY     IC RECORDER      3.00 PQ: 0 ANSI: 0 CCS
[    7.849267] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    7.849647] sd 2:0:0:1: Attached scsi generic sg3 type 0
[    7.854054] sd 2:0:0:0: [sdb] 3896819 512-byte logical blocks: (1.99 GB/1.85 GiB)
[    7.855748] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    7.857673] sd 2:0:0:0: [sdb] Write Protect is off
[    7.857689] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    7.857694] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.864768] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.864786]  sdb: sdb1
[    7.869871] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.869884] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    8.725513] usb-storage: device scan complete
[    8.729423] scsi 3:0:0:0: Direct-Access                               1.00 PQ: 0 ANSI: 2
[    8.730604] sd 3:0:0:0: Attached scsi generic sg4 type 0
[    8.735396] sd 3:0:0:0: [sdd] 15204352 512-byte logical blocks: (7.78 GB/7.25 GiB)
[    8.741386] sd 3:0:0:0: [sdd] Write Protect is off
[    8.741393] sd 3:0:0:0: [sdd] Mode Sense: 2f 00 00 00
[    8.741398] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[    8.759380] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[    8.759392]  sdd: sdd1
[    9.451625] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[    9.451641] sd 3:0:0:0: [sdd] Attached SCSI removable disk
[   23.164714] Adding 416760k swap on /dev/sda6.  Priority:-1 extents:1 across:416760k 
[   24.754110] udev: starting version 151
[   25.079057] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.439365] Linux agpgart interface v0.103
[   25.887805] lp: driver loaded but no devices found
[   25.903956] vga16fb: initializing
[   25.903969] vga16fb: mapped to 0xc00a0000
[   25.904235] fb0: VGA16 VGA frame buffer device
[   25.916199] agpgart: Detected VIA KLE133 chipset
[   26.058122] parport_pc: VIA 686A/8231 detected
[   26.058131] parport_pc: probing current configuration
[   26.058154] parport_pc: Current parallel port base: 0x378
[   26.058245] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   26.172440] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   26.189922] lp0: using parport0 (interrupt-driven).
[   26.189937] parport_pc: VIA parallel port: io=0x378, irq=7
[   26.824564] Linux video capture interface: v2.00
[   26.950866] ppdev: user-space parallel port driver
[   27.021532] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0809)
[   27.059310] input: UVC Camera (046d:0809) as /devices/pci0000:00/0000:00:0e.2/usb1/1-2/1-2:1.0/input/input7
[   27.059507] usbcore: registered new interface driver uvcvideo
[   27.059513] USB Video Class driver (v0.1.0)
[   27.736686] Console: switching to colour frame buffer device 80x30
[   27.908844] type=1505 audit(1338953056.224:2):  operation="profile_load" pid=591 name="/sbin/dhclient3"
[   27.909424] type=1505 audit(1338953056.224:3):  operation="profile_load" pid=591 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.909762] type=1505 audit(1338953056.224:4):  operation="profile_load" pid=591 name="/usr/lib/connman/scripts/dhclient-script"
[   27.911180] type=1505 audit(1338953056.224:5):  operation="profile_replace" pid=558 name="/sbin/dhclient3"
[   27.911944] type=1505 audit(1338953056.224:6):  operation="profile_replace" pid=558 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   27.912410] type=1505 audit(1338953056.228:7):  operation="profile_replace" pid=558 name="/usr/lib/connman/scripts/dhclient-script"
[   28.937876]   alloc irq_desc for 22 on node -1
[   28.937885]   alloc kstat_irqs on node -1
[   28.937904] VIA 82xx Audio 0000:00:07.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   28.938093] VIA 82xx Audio 0000:00:07.5: setting latency timer to 64
[   29.609354] usbcore: registered new interface driver snd-usb-audio
[   77.209911] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   77.307273] type=1505 audit(1338953105.620:8):  operation="profile_load" pid=753 name="/usr/share/gdm/guest-session/Xsession"
[   77.316648] type=1505 audit(1338953105.632:9):  operation="profile_replace" pid=757 name="/sbin/dhclient3"
[   77.317410] type=1505 audit(1338953105.632:10):  operation="profile_replace" pid=757 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   77.317757] type=1505 audit(1338953105.632:11):  operation="profile_replace" pid=757 name="/usr/lib/connman/scripts/dhclient-script"
[   77.739259] type=1505 audit(1338953106.052:12):  operation="profile_load" pid=758 name="/usr/bin/evince"
[   77.751921] type=1505 audit(1338953106.064:13):  operation="profile_load" pid=758 name="/usr/bin/evince-previewer"
[   77.768628] type=1505 audit(1338953106.084:14):  operation="profile_load" pid=758 name="/usr/bin/evince-thumbnailer"
[   77.842554] type=1505 audit(1338953106.156:15):  operation="profile_load" pid=828 name="/usr/lib/cups/backend/cups-pdf"
[   77.843406] type=1505 audit(1338953106.156:16):  operation="profile_load" pid=828 name="/usr/sbin/cupsd"
[   77.864803] type=1505 audit(1338953106.180:17):  operation="profile_load" pid=831 name="/usr/sbin/mysqld"
[   87.660017] eth0: no IPv6 routers present
[  108.356721] FAT: Filesystem error (dev sdd1)
[  108.356737]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.356745]     File system has been set read-only
[  108.358177] FAT: Filesystem error (dev sdd1)
[  108.358194]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.359046] FAT: Filesystem error (dev sdd1)
[  108.359060]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.359885] FAT: Filesystem error (dev sdd1)
[  108.359899]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.363088] FAT: Filesystem error (dev sdd1)
[  108.363106]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.368933] FAT: Filesystem error (dev sdd1)
[  108.368951]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.369906] FAT: Filesystem error (dev sdd1)
[  108.369922]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.379649] FAT: Filesystem error (dev sdd1)
[  108.379669]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.385935] FAT: Filesystem error (dev sdd1)
[  108.385952]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.386860] FAT: Filesystem error (dev sdd1)
[  108.386874]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.387516] FAT: Filesystem error (dev sdd1)
[  108.387529]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.397533] FAT: Filesystem error (dev sdd1)
[  108.397549]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.398448] FAT: Filesystem error (dev sdd1)
[  108.398463]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.399095] FAT: Filesystem error (dev sdd1)
[  108.399107]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.399925] FAT: Filesystem error (dev sdd1)
[  108.399939]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.409625] FAT: Filesystem error (dev sdd1)
[  108.409644]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.410507] FAT: Filesystem error (dev sdd1)
[  108.410521]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.434632] FAT: Filesystem error (dev sdd1)
[  108.434650]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.435826] FAT: Filesystem error (dev sdd1)
[  108.435842]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.437625] FAT: Filesystem error (dev sdd1)
[  108.437640]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.438477] FAT: Filesystem error (dev sdd1)
[  108.438491]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.439327] FAT: Filesystem error (dev sdd1)
[  108.439340]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.441181] FAT: Filesystem error (dev sdd1)
[  108.441197]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.442133] FAT: Filesystem error (dev sdd1)
[  108.442147]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.442979] FAT: Filesystem error (dev sdd1)
[  108.442993]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.443803] FAT: Filesystem error (dev sdd1)
[  108.443816]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.445728] FAT: Filesystem error (dev sdd1)
[  108.445744]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.446440] FAT: Filesystem error (dev sdd1)
[  108.446453]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.447070] FAT: Filesystem error (dev sdd1)
[  108.447084]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.447688] FAT: Filesystem error (dev sdd1)
[  108.447700]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.449379] FAT: Filesystem error (dev sdd1)
[  108.449395]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.457073] FAT: Filesystem error (dev sdd1)
[  108.457093]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.457989] FAT: Filesystem error (dev sdd1)
[  108.458004]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.461408] FAT: Filesystem error (dev sdd1)
[  108.461426]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  108.926826] FAT: Filesystem error (dev sdd1)
[  108.926844]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  113.239923] __ratelimit: 6 callbacks suppressed
[  113.239935] type=1505 audit(1338953140.701:20):  operation="profile_replace" pid=1536 name="/usr/sbin/mysqld"
[  144.437559] type=1505 audit(1338953171.901:21):  operation="profile_replace" pid=1682 name="/usr/sbin/mysqld"
[  175.135214] type=1505 audit(1338953202.597:22):  operation="profile_replace" pid=1774 name="/usr/sbin/mysqld"
[  205.765638] type=1505 audit(1338953233.229:23):  operation="profile_replace" pid=1853 name="/usr/sbin/mysqld"
[  236.387163] type=1505 audit(1338953263.849:24):  operation="profile_replace" pid=1932 name="/usr/sbin/mysqld"
[  267.013124] type=1505 audit(1338953294.477:25):  operation="profile_replace" pid=2011 name="/usr/sbin/mysqld"
[  297.632865] type=1505 audit(1338953325.097:26):  operation="profile_replace" pid=2090 name="/usr/sbin/mysqld"
[  328.247250] type=1505 audit(1338953355.709:27):  operation="profile_replace" pid=2169 name="/usr/sbin/mysqld"
[  358.867465] type=1505 audit(1338953386.329:28):  operation="profile_replace" pid=2248 name="/usr/sbin/mysqld"
[  389.479354] type=1505 audit(1338953416.941:29):  operation="profile_replace" pid=2327 name="/usr/sbin/mysqld"
[  420.520355] type=1505 audit(1338953447.985:30):  operation="profile_replace" pid=2437 name="/usr/sbin/mysqld"
[  451.997268] type=1505 audit(1338953479.461:31):  operation="profile_replace" pid=2527 name="/usr/sbin/mysqld"
[  483.035467] type=1505 audit(1338953510.497:32):  operation="profile_replace" pid=2630 name="/usr/sbin/mysqld"
[  514.081587] type=1505 audit(1338953541.545:33):  operation="profile_replace" pid=2714 name="/usr/sbin/mysqld"
[  545.016943] type=1505 audit(1338953572.481:34):  operation="profile_replace" pid=2794 name="/usr/sbin/mysqld"
[  576.221784] type=1505 audit(1338953603.685:35):  operation="profile_replace" pid=2874 name="/usr/sbin/mysqld"
[  607.193113] type=1505 audit(1338953634.657:36):  operation="profile_replace" pid=2954 name="/usr/sbin/mysqld"
[  638.313382] type=1505 audit(1338953665.777:37):  operation="profile_replace" pid=3051 name="/usr/sbin/mysqld"
[  669.377127] type=1505 audit(1338953696.841:38):  operation="profile_replace" pid=3146 name="/usr/sbin/mysqld"
[  700.043308] type=1505 audit(1338953727.505:39):  operation="profile_replace" pid=3225 name="/usr/sbin/mysqld"
[  717.664080] end_request: I/O error, dev fd0, sector 0
[  717.688049] end_request: I/O error, dev fd0, sector 0
[  730.846299] type=1505 audit(1338953758.309:40):  operation="profile_replace" pid=3318 name="/usr/sbin/mysqld"
[  762.233794] type=1505 audit(1338953789.697:41):  operation="profile_replace" pid=3397 name="/usr/sbin/mysqld"
[  793.197195] type=1505 audit(1338953820.661:42):  operation="profile_replace" pid=3477 name="/usr/sbin/mysqld"
[  824.473995] type=1505 audit(1338953851.937:43):  operation="profile_replace" pid=3557 name="/usr/sbin/mysqld"
[  855.654617] type=1505 audit(1338953883.117:44):  operation="profile_replace" pid=3636 name="/usr/sbin/mysqld"
[  886.635928] type=1505 audit(1338953914.097:45):  operation="profile_replace" pid=3715 name="/usr/sbin/mysqld"
[  896.512149] usb 4-2: USB disconnect, address 2
[  917.397408] type=1505 audit(1338953944.861:46):  operation="profile_replace" pid=3810 name="/usr/sbin/mysqld"
[  924.968054] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  925.114028] usb 4-2: not running at top speed; connect to a high speed hub
[  925.146101] usb 4-2: configuration #1 chosen from 1 choice
[  925.150825] scsi4 : SCSI emulation for USB Mass Storage devices
[  925.151559] usb-storage: device found at 3
[  925.151566] usb-storage: waiting for device to settle before scanning
[  930.149636] usb-storage: device scan complete
[  930.153571] scsi 4:0:0:0: Direct-Access                               1.00 PQ: 0 ANSI: 2
[  930.168651] sd 4:0:0:0: Attached scsi generic sg4 type 0
[  930.178689] sd 4:0:0:0: [sdd] 15204352 512-byte logical blocks: (7.78 GB/7.25 GiB)
[  930.186710] sd 4:0:0:0: [sdd] Write Protect is off
[  930.186722] sd 4:0:0:0: [sdd] Mode Sense: 2f 00 00 00
[  930.186728] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[  930.214607] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[  930.214635]  sdd: sdd1
[  930.918508] sd 4:0:0:0: [sdd] Assuming drive cache: write through
[  930.918532] sd 4:0:0:0: [sdd] Attached SCSI removable disk
[  932.565439] FAT: Filesystem error (dev sdd1)
[  932.565457]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.565465]     File system has been set read-only
[  932.566968] FAT: Filesystem error (dev sdd1)
[  932.566983]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.567835] FAT: Filesystem error (dev sdd1)
[  932.567850]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.574479] FAT: Filesystem error (dev sdd1)
[  932.574497]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.575447] FAT: Filesystem error (dev sdd1)
[  932.575463]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.584090] FAT: Filesystem error (dev sdd1)
[  932.584104]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.585116] FAT: Filesystem error (dev sdd1)
[  932.585131]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.585995] FAT: Filesystem error (dev sdd1)
[  932.586009]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.586837] FAT: Filesystem error (dev sdd1)
[  932.586852]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.587689] FAT: Filesystem error (dev sdd1)
[  932.587704]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.604718] FAT: Filesystem error (dev sdd1)
[  932.604737]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.605492] FAT: Filesystem error (dev sdd1)
[  932.605507]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.606140] FAT: Filesystem error (dev sdd1)
[  932.606155]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.606781] FAT: Filesystem error (dev sdd1)
[  932.606794]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.607626] FAT: Filesystem error (dev sdd1)
[  932.607640]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.616795] FAT: Filesystem error (dev sdd1)
[  932.616811]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.617708] FAT: Filesystem error (dev sdd1)
[  932.617723]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.686970] FAT: Filesystem error (dev sdd1)
[  932.686988]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.696696] FAT: Filesystem error (dev sdd1)
[  932.696714]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.697702] FAT: Filesystem error (dev sdd1)
[  932.697716]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.698586] FAT: Filesystem error (dev sdd1)
[  932.698601]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.699456] FAT: Filesystem error (dev sdd1)
[  932.699471]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.708692] FAT: Filesystem error (dev sdd1)
[  932.708711]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.709687] FAT: Filesystem error (dev sdd1)
[  932.709702]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.710573] FAT: Filesystem error (dev sdd1)
[  932.710589]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.711426] FAT: Filesystem error (dev sdd1)
[  932.711441]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.723343] FAT: Filesystem error (dev sdd1)
[  932.723361]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.728488] FAT: Filesystem error (dev sdd1)
[  932.728505]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.729292] FAT: Filesystem error (dev sdd1)
[  932.729306]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.729955] FAT: Filesystem error (dev sdd1)
[  932.729969]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.740436] FAT: Filesystem error (dev sdd1)
[  932.740452]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.741442] FAT: Filesystem error (dev sdd1)
[  932.741456]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.742334] FAT: Filesystem error (dev sdd1)
[  932.742349]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  932.743213] FAT: Filesystem error (dev sdd1)
[  932.743227]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  933.299360] FAT: Filesystem error (dev sdd1)
[  933.299379]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  948.419753] type=1505 audit(1338953975.881:47):  operation="profile_replace" pid=3925 name="/usr/sbin/mysqld"
[  979.494955] type=1505 audit(1338954006.957:48):  operation="profile_replace" pid=4004 name="/usr/sbin/mysqld"
[ 1010.466430] type=1505 audit(1338954037.929:49):  operation="profile_replace" pid=4083 name="/usr/sbin/mysqld"
[ 1041.224237] type=1505 audit(1338954068.689:50):  operation="profile_replace" pid=4162 name="/usr/sbin/mysqld"
[ 1071.937213] type=1505 audit(1338954099.401:51):  operation="profile_replace" pid=4243 name="/usr/sbin/mysqld"
[ 1102.769635] type=1505 audit(1338954130.233:52):  operation="profile_replace" pid=4344 name="/usr/sbin/mysqld"

Kind regards - Edward James Tagg

---

