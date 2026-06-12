---
title: "USB printer not recognized"
date: 2009-09-28
forum: General Help
---

### Post by Roofle on 2009-09-28
I'm currently running Karmic.  I have a HP Photosmart C4240 hooked up and it was previously working fine.  I, for some reason or another, deleted the printer under the "Printing" settings in Ubuntu.  Now, when I plug the printer into the computer, it is not auto-detected.  I attempted to re-discover the printer under the "Printing" tab, however it was also not detected then.  While trying to diagnose the issue, I attempted "lsusb", only for it to come up blank.  I found this odd since both a printer and USB mouse were hooked up to ports.

Below is the resulting dump when I hooked the printer in.  It appears to recognize the storage device (the printer has an SD slot built in), but not the printer itself.

$ tail -f /var/log/messages 
Sep 28 00:02:00 server kernel: [ 4674.011620] scsi6 : SCSI emulation for USB Mass Storage devices
Sep 28 00:02:00 server kernel: [ 4679.010711] scsi 6:0:0:0: Direct-Access     HP       Photosmart C4240 1.00 PQ: 0 ANSI: 5
Sep 28 00:02:00 server kernel: [ 4679.011188] sd 6:0:0:0: Attached scsi generic sg2 type 0
Sep 28 00:02:00 server kernel: [ 4679.021908] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Sep 28 07:41:12 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1726" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Sep 28 12:13:44 server kernel: [48578.532961] usb 1-1: USB disconnect, address 5
Sep 28 12:13:44 server kernel: [48594.040020] usb 1-1: new high speed USB device using ehci_hcd and address 6
Sep 28 12:13:44 server kernel: [48594.190992] usb 1-1: configuration #1 chosen from 1 choice
Sep 28 12:13:44 server kernel: [48594.192256] scsi7 : SCSI emulation for USB Mass Storage devices
Sep 28 12:13:44 server kernel: [48599.193210] scsi 7:0:0:0: Direct-Access     HP       Photosmart C4240 1.00 PQ: 0 ANSI: 5

Any help would be appreciated!

---

