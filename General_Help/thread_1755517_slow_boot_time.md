---
title: "slow boot time"
date: 2011-05-11
forum: General Help
---

### Post by l3ecl on 2011-05-11
I have a slow boot time and there seems to be a bottleneck in between 7 seconds and 16 seconds:

> [    5.609357] ata2.00: configured for UDMA/100
[    5.615439] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633F  AC00 PQ: 0 ANSI: 5
[    5.624352] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.624357] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.624503] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.624554] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.630810] Initializing USB Mass Storage driver...
[    5.630924] scsi4 : usb-storage 1-1.2:1.0
[    5.631006] usbcore: registered new interface driver usb-storage
[    5.631007] USB Mass Storage support registered.
[    5.633286] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input5
[    5.633363] generic-usb 0003:04B3:310C.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1.3/input0
[    5.633373] usbcore: registered new interface driver usbhid
[    5.633374] usbhid: USB HID core driver
[    6.624635] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    6.626013] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    6.631634] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.197297] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   16.612745] <30>udev[331]: starting version 167
[   16.634353] lp: driver loaded but no devices found
[   16.658970] Adding 2734076k swap on /dev/sda5.  Priority:-1 extents:1 across:2734076k 
[   17.370665] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   17.506119] type=1400 audit(1305115174.622:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=463 comm="apparmor_parser"
[   17.506608] type=1400 audit(1305115174.622:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=463 comm="apparmor
_parser"


I was wondering what's going?

---

