---
title: "Mounting usb device (mp4 player)"
date: 2011-05-08
forum: General Help
---

### Post by enimeizoo on 2011-05-08
Hello,
I have a mp4 player taht should work just like any usb mass storage device, provided the "pc connection" option on it is set on MSC, but it obviously doesn't since it isn't mounted automatically.

When I plug it in in MSC mode I get something like that in /var/log/messages (I get multiples lines each times I plug it in, with about one sec delay between lines): 
May  8 14:50:38 seb-laptop vmunix: [ 1047.910079] usb 6-2: new full speed USB device using uhci_hcd and address 16
May  8 14:50:39 seb-laptop vmunix: [ 1048.453107] usb 6-2: new full speed USB device using uhci_hcd and address 17

When in MTP mode I get :
May  8 15:11:34 seb-laptop vmunix: [ 2303.593088] usb 6-1: new full speed USB device using uhci_hcd and address 22
May  8 15:11:35 seb-laptop vmunix: [ 2304.190608] usb 6-1: new full speed USB device using uhci_hcd and address 23
May  8 15:11:36 seb-laptop vmunix: [ 2305.392604] usb 6-1: new full speed USB device using uhci_hcd and address 25

When I plug a usb key in, I get something like that :
May  8 15:08:46 seb-laptop vmunix: [ 2135.307415] usb 2-1: configuration #1 chosen from 1 choice
May  8 15:08:46 seb-laptop vmunix: [ 2135.307868] scsi7 : SCSI emulation for USB Mass Storage devices
May  8 15:08:51 seb-laptop vmunix: [ 2140.337079] scsi 7:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
May  8 15:08:51 seb-laptop vmunix: [ 2140.338985] sd 7:0:0:0: Attached scsi generic sg3 type 0
May  8 15:08:52 seb-laptop vmunix: [ 2141.454670] sd 7:0:0:0: [sdc] 7811072 512-byte logical blocks: (3.99 GB/3.72 GiB)
May  8 15:08:52 seb-laptop vmunix: [ 2141.455251] sd 7:0:0:0: [sdc] Write Protect is off
May  8 15:08:52 seb-laptop vmunix: [ 2141.459964]  sdc: sdc1

According to an article about it, I should get something like that :
usb 1-4: new high speed USB device using ehci_hcd and address 6
usb 1-4: configuration #1 chosen from 1 choice
scsi7 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete
scsi 7:0:0:0: Direct-Access     Samsung  YP-R1            0322 PQ: 0 ANSI: 2
sd 7:0:0:0: Attached scsi generic sg6 type 0
sd 7:0:0:0: [sdf] 31434752 512-byte logical blocks: (16.0 GB/14.9 GiB)
sd 7:0:0:0: [sdf] Write Protect is off
sd 7:0:0:0: [sdf] Mode Sense: 0f 00 00 00
sd 7:0:0:0: [sdf] Assuming drive cache: write through
sd 7:0:0:0: [sdf] Assuming drive cache: write through
 sdf:
sd 7:0:0:0: [sdf] Assuming drive cache: write through
sd 7:0:0:0: [sdf] Attached SCSI removable disk

The difference I see is that on the last example, ehci_hcd is used, whereas my laptop uses uhci_hcd. That doesn't make sense since uhci_hcd is for usb 1.0, but the device is described as "full speed", and I'm pretty sure it is a usb 2.0. But using a usb1.0 driver for a usb2.0 device shouldn't be a problem, right? Or a speed problem, but it should work...

Well, I'm pretty confused since it doesn't work with windows either. So any clue is welcome!

Thanks in advance!

---

### Post by enimeizoo on 2011-05-09
Ok, I wasn't looking at the right log, it seems.
/var/log/syslog gives :
May  9 18:10:28 seb-laptop vmunix: [29749.192565] usb 6-2: new full speed USB device using uhci_hcd and address 6
May  9 18:10:28 seb-laptop vmunix: [29749.322562] usb 6-2: device descriptor read/64, error -71
May  9 18:10:28 seb-laptop vmunix: [29749.562562] usb 6-2: device descriptor read/64, error -71
May  9 18:10:28 seb-laptop vmunix: [29749.792626] usb 6-2: new full speed USB device using uhci_hcd and address 7
May  9 18:10:28 seb-laptop vmunix: [29749.922559] usb 6-2: device descriptor read/64, error -71
May  9 18:10:29 seb-laptop vmunix: [29750.162564] usb 6-2: device descriptor read/64, error -71
May  9 18:10:29 seb-laptop vmunix: [29750.392568] usb 6-2: new full speed USB device using uhci_hcd and address 8
May  9 18:10:29 seb-laptop vmunix: [29750.812586] usb 6-2: device not accepting address 8, error -71
May  9 18:10:29 seb-laptop vmunix: [29750.932564] usb 6-2: new full speed USB device using uhci_hcd and address 9
May  9 18:10:30 seb-laptop vmunix: [29751.350057] usb 6-2: device not accepting address 9, error -71
May  9 18:10:30 seb-laptop vmunix: [29751.350078] hub 6-0:1.0: unable to enumerate USB device on port 2


I saw that some people solved the 71 error with echo Y > /sys/module/usbcore/parameters/old_scheme_first , but there was no effect so I reverted it.

Any idea, anyone?

---

