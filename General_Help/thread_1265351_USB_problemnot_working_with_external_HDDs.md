---
title: "USB problem/not working with external HDDs"
date: 2009-09-13
forum: General Help
---

### Post by NorQue on 2009-09-13
Hello,

since three or four days the USB port of my Laptop (a [Sony Vaio VGN-FE21S](http://vaio.sony.co.uk/view/ShowProduct.action?product=VGN-FE21S&productFilters=retired&site=voe_en_GB_cons&pageType=Overview&category=VN+FE+Series)) behaves very weird. No matter what external storage device I plug in, I can't mount any of them anymore. Tried two 3.5" HDDs with external power supply, one 2.5" w/o external power, a MicroSD card reader and a MP3 player, none of them work. I also have an external Keyboard and mouse connected to my Laptop, both of them work without problem. External storage itself works fine on my MacBook Pro 5,5 (would've been strange if *all* of them decided to quite around the same time, too ;) ).

Now to the really strange things:

lsusb just hangs! And so does the USB part of the "System Profiler and Benchmark" tool. top is showing a constant 50%wa all the time, same with the System Monitor (IOWait).

IIRC all this started shortly after the last "Important Update" for Ubuntu 9.04, though that could possibly just be a coincidence.

Relevant syslog bits:
```
Sep 12 15:44:01 akane kernel: [   56.720895] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Sep 12 15:44:01 akane kernel: [   56.720902] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Sep 12 15:44:33 akane kernel: [   89.553033] usb 1-1: new high speed USB device using ehci_hcd and address 6
Sep 12 15:44:33 akane kernel: [   89.686134] usb 1-1: configuration #1 chosen from 1 choice
Sep 12 15:44:33 akane kernel: [   89.686458] hub 1-1:1.0: USB hub found
Sep 12 15:44:33 akane kernel: [   89.686718] hub 1-1:1.0: 4 ports detected
Sep 12 15:44:33 akane kernel: [   89.960359] usb 1-1.4: new high speed USB device using ehci_hcd and address 7
Sep 12 15:44:34 akane kernel: [   90.072821] usb 1-1.4: configuration #1 chosen from 1 choice
Sep 12 15:44:34 akane kernel: [   90.076291] scsi5 : SCSI emulation for USB Mass Storage devices
Sep 12 15:44:34 akane kernel: [   90.076501] usb-storage: device found at 7
Sep 12 15:44:34 akane kernel: [   90.076503] usb-storage: waiting for device to settle before scanning
Sep 12 15:44:36 akane kernel: [   92.850408] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Sep 12 15:44:36 akane kernel: [   92.850420] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
Sep 12 15:44:39 akane kernel: [   95.076241] usb-storage: device scan complete
Sep 12 15:44:39 akane kernel: [   95.079971] scsi 5:0:0:0: Direct-Access     WDC WD10 EAVS-00D7B0           PQ: 0 ANSI: 2
Sep 12 15:44:43 akane kernel: [   99.680377] usb 1-1.1: new high speed USB device using ehci_hcd and address 8
Sep 12 15:44:43 akane kernel: [   99.773478] usb 1-1.1: configuration #1 chosen from 1 choice
Sep 12 15:44:43 akane kernel: [   99.773722] scsi6 : SCSI emulation for USB Mass Storage devices
Sep 12 15:44:43 akane kernel: [   99.773972] usb-storage: device found at 8
Sep 12 15:44:43 akane kernel: [   99.773976] usb-storage: waiting for device to settle before scanning
Sep 12 15:44:48 akane kernel: [  104.772314] usb-storage: device scan complete
Sep 12 15:44:48 akane kernel: [  104.772880] scsi 6:0:0:0: Direct-Access     NSI      HD103SI          2.06 PQ: 0 ANSI: 4
Sep 12 15:45:12 akane kernel: [  128.982349] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Sep 12 15:45:12 akane kernel: [  128.982361] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
```

Set up:
[Sony Vaio VGN-FE21S](http://vaio.sony.co.uk/view/ShowProduct.action?product=VGN-FE21S&productFilters=retired&site=voe_en_GB_cons&pageType=Overview&category=VN+FE+Series)
Core Duo (note the absence of a 2) T2400 @ 1.83 GHz, 1 GByte RAM, Geforce Go 7600 (running proprietary drivers, version 180)
Ubuntu 9.04/Jaunty, updated today
uname -a: Linux akane 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

Any help?

---

### Post by NorQue on 2009-09-14
Turns out the culprit was a defective SD card reader that I have completely forgotten about. Five days ago I seem to have inserted a SD card pretty much absent minded, after removing it today everything worked fine again.

The looping
```
Sep 12 15:44:36 akane kernel: [   92.850408] sd 4:0:0:0: [sdb] Sense Key : No Sense [current] 
Sep 12 15:44:36 akane kernel: [   92.850420] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
```messages in syslog (that I haven't written about in my post...) stopped and IOWait/wa is back to normal levels again. Phew. :)

---

