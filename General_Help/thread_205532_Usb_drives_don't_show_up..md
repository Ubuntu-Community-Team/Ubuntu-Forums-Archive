---
title: "Usb drives don't show up."
date: 2006-06-28
forum: General Help
---

### Post by ephesius on 2006-06-28
Most of the time I plug in my 4 gig nano or my 2 gb flash drive neither of them show up. I can't mount them manually because it isnt showing up on the system at all. I do the list usb command i forget what it is exactly right now but regardless it doesnt show that anything is connected. The usb drive is good because the flash drive and ipod connected when I was using a damn small live cd. It also worked with breezy, I think it is some kind of Dapper error. I have a thinkpad t40 but i dont know if that is the problem.
Any help is greatly appreciated. Thanks in advance.

---

### Post by ahaslam on 2006-06-28
What happens if you boot with the device activated & attached?

---

### Post by ephesius on 2006-06-28
Nothing with the nano, I had damn small linux on the thumbdrive but then took it off...the bios tries to boot from it but ubuntu just doesn't see it.

---

### Post by ahaslam on 2006-06-28
I had a similar problem with a beta version of Dapper, but it usually worked when it was inserted during boot. Seeing as it's different for you my fix may not work, but if may be worth a try.

I had installed with my usb device pulgged in and Dapper placed an entry for it in fstab (/etc/fstab). Removing this entry, leaving only entries for hard disc partitions & cd/dvd drives, solved my problem.

If this does't help, I'm sure someone here will have the answer.

Good luck,

Tony.

---

### Post by ephesius on 2006-06-28
Ok ill check on that when I get home, thanks man.

---

### Post by ozorba on 2006-06-28
try this script:

[http://www.garloff.de/kurt/linux/rescan-scsi-bus.sh](http://www.garloff.de/kurt/linux/rescan-scsi-bus.sh)

OZ

---

### Post by ephesius on 2006-06-29
[QUOTE=ozorba]try this script:

[http://www.garloff.de/kurt/linux/rescan-scsi-bus.sh](http://www.garloff.de/kurt/linux/rescan-scsi-bus.sh)

OZ[/QUOTE]
When I try that it tells me the scsi subsystem in inactive, how do I activate it, it seems like this is my problem considering usb drives are mounted as scsi drives right?

---

### Post by ahaslam on 2006-06-29
I found these threads, they look very thorough & shoud sort out any usb mounting problems:

[http://ubuntuforums.org/showthread.php?t=191963]("http://ubuntuforums.org/showthread.php?t=191963")
[http://ubuntuforums.org/showthread.php?t=103071]("http://ubuntuforums.org/showthread.php?t=103071")

I hope they help ;) 

Tony.

---

### Post by ephesius on 2006-06-29
After about a minute in mounted...this is way too long right?
It tells me the following:

Jun 29 18:54:21 localhost kernel: [17180056.240000] usb 4-3: new high speed USB device using ehci_hcd and address 19
Jun 29 18:54:23 localhost kernel: [17180058.004000] usb 4-3: new high speed USB device using ehci_hcd and address 25
Jun 29 18:54:24 localhost kernel: [17180059.264000] usb 4-3: new high speed USB device using ehci_hcd and address 29
Jun 29 18:54:28 localhost kernel: [17180063.548000] usb 4-3: new high speed USB device using ehci_hcd and address 45
Jun 29 18:54:39 localhost kernel: [17180073.628000] usb 4-3: new high speed USB device using ehci_hcd and address 84
Jun 29 18:54:41 localhost kernel: [17180075.644000] usb 4-3: new high speed USB device using ehci_hcd and address 91
Jun 29 18:54:44 localhost kernel: [17180078.668000] usb 4-3: new high speed USB device using ehci_hcd and address 102
Jun 29 18:54:45 localhost kernel: [17180080.432000] usb 4-3: new high speed USB device using ehci_hcd and address 108
Jun 29 18:54:46 localhost kernel: [17180081.440000] usb 4-3: new high speed USB device using ehci_hcd and address 111
Jun 29 18:54:49 localhost kernel: [17180084.464000] usb 4-3: new high speed USB device using ehci_hcd and address 122
Jun 29 18:54:55 localhost kernel: [17180090.008000] usb 4-3: new high speed USB device using ehci_hcd and address 17
Jun 29 18:54:57 localhost kernel: [17180092.276000] usb 4-3: new high speed USB device using ehci_hcd and address 25
Jun 29 18:55:01 localhost kernel: [17180096.056000] usb 4-3: new high speed USB device using ehci_hcd and address 39
Jun 29 18:55:02 localhost kernel: [17180097.064000] usb 4-3: new high speed USB device using ehci_hcd and address 42
Jun 29 18:55:06 localhost kernel: [17180101.600000] usb 4-3: new high speed USB device using ehci_hcd and address 59
Jun 29 18:55:11 localhost kernel: [17180106.388000] usb 4-3: new high speed USB device using ehci_hcd and address 77
Jun 29 18:55:26 localhost kernel: [17180121.256000] usb 4-3: new high speed USB device using ehci_hcd and address 88
Jun 29 18:55:28 localhost kernel: [17180123.272000] usb 4-3: new high speed USB device using ehci_hcd and address 95
Jun 29 18:55:29 localhost kernel: [17180124.028000] usb 4-3: new high speed USB device using ehci_hcd and address 97
Jun 29 18:55:32 localhost kernel: [17180126.800000] usb 4-3: new high speed USB device using ehci_hcd and address 107
Jun 29 18:55:34 localhost kernel: [17180129.320000] usb 4-3: new high speed USB device using ehci_hcd and address 116
Jun 29 18:55:40 localhost kernel: [17180134.612000] usb 4-3: new high speed USB device using ehci_hcd and address 10
Jun 29 18:55:42 localhost kernel: [17180136.628000] usb 4-3: new high speed USB device using ehci_hcd and address 17
Jun 29 18:55:44 localhost kernel: [17180139.400000] usb 4-3: new high speed USB device using ehci_hcd and address 27
Jun 29 18:55:45 localhost kernel: [17180140.156000] usb 4-3: new high speed USB device using ehci_hcd and address 29
Jun 29 18:55:46 localhost kernel: [17180140.660000] usb 4-3: new high speed USB device using ehci_hcd and address 30
Jun 29 18:55:47 localhost kernel: [17180141.668000] usb 4-3: new high speed USB device using ehci_hcd and address 33
Jun 29 18:55:49 localhost kernel: [17180143.936000] usb 4-3: new high speed USB device using ehci_hcd and address 41
Jun 29 18:55:50 localhost kernel: [17180145.196000] usb 4-3: new high speed USB device using ehci_hcd and address 45
Jun 29 18:55:52 localhost kernel: [17180146.708000] usb 4-3: new high speed USB device using ehci_hcd and address 50
Jun 29 18:55:58 localhost kernel: [17180153.260000] usb 4-3: new high speed USB device using ehci_hcd and address 75
Jun 29 18:56:05 localhost kernel: [17180160.316000] usb 4-3: new high speed USB device using ehci_hcd and address 102
Jun 29 18:56:08 localhost kernel: [17180162.836000] usb 4-3: new high speed USB device using ehci_hcd and address 111
Jun 29 18:56:09 localhost kernel: [17180164.096000] usb 4-3: new high speed USB device using ehci_hcd and address 115
Jun 29 18:56:09 localhost kernel: [17180164.600000] usb 4-3: new high speed USB device using ehci_hcd and address 116
Jun 29 18:56:12 localhost kernel: [17180167.120000] usb 4-3: new high speed USB device using ehci_hcd and address 125
Jun 29 18:56:13 localhost kernel: [17180167.876000] usb 4-3: new high speed USB device using ehci_hcd and address 127
Jun 29 18:56:14 localhost kernel: [17180168.632000] usb 4-3: new high speed USB device using ehci_hcd and address 3
Jun 29 18:56:14 localhost kernel: [17180169.388000] usb 4-3: new high speed USB device using ehci_hcd and address 5
Jun 29 18:56:24 localhost kernel: [17180178.712000] usb 4-3: new high speed USB device using ehci_hcd and address 41
Jun 29 18:56:28 localhost kernel: [17180183.248000] usb 4-3: new high speed USB device using ehci_hcd and address 58
Jun 29 18:56:36 localhost kernel: [17180191.564000] usb 4-3: new high speed USB device using ehci_hcd and address 90
Jun 29 18:56:37 localhost kernel: [17180192.572000] usb 4-3: new high speed USB device using ehci_hcd and address 93
Jun 29 18:56:42 localhost kernel: [17180197.108000] usb 4-3: new high speed USB device using ehci_hcd and address 108
Jun 29 18:56:43 localhost kernel: [17180198.368000] usb 4-3: new high speed USB device using ehci_hcd and address 110
Jun 29 18:56:46 localhost kernel: [17180200.888000] usb 4-3: new high speed USB device using ehci_hcd and address 119
Jun 29 18:56:47 localhost kernel: [17180201.644000] usb 4-3: new high speed USB device using ehci_hcd and address 121
Jun 29 18:56:49 localhost kernel: [17180203.660000] usb 4-3: new high speed USB device using ehci_hcd and address 2
Jun 29 18:56:50 localhost kernel: [17180205.424000] usb 4-3: new high speed USB device using ehci_hcd and address 8
Jun 29 18:57:05 localhost kernel: [17180220.292000] usb 4-3: new high speed USB device using ehci_hcd and address 66
Jun 29 18:57:11 localhost kernel: [17180225.836000] usb 4-3: new high speed USB device using ehci_hcd and address 87
Jun 29 18:57:13 localhost kernel: [17180228.356000] usb 4-3: new high speed USB device using ehci_hcd and address 96
Jun 29 18:57:15 localhost kernel: [17180230.372000] usb 4-3: new high speed USB device using ehci_hcd and address 103
Jun 29 18:57:18 localhost kernel: [17180233.396000] usb 4-3: new high speed USB device using ehci_hcd and address 114
Jun 29 18:57:20 localhost kernel: [17180234.656000] usb 4-3: new high speed USB device using ehci_hcd and address 118
Jun 29 18:57:25 localhost kernel: [17180240.384000] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jun 29 18:57:25 localhost kernel: [17180240.516000] usb 2-1: not running at top speed; connect to a high speed hub
Jun 29 18:57:25 localhost kernel: [17180240.528000] usb 2-1: configuration #1 chosen from 2 choices
Jun 29 18:57:26 localhost kernel: [17180240.648000] SCSI subsystem initialized
Jun 29 18:57:26 localhost kernel: [17180240.680000] Initializing USB Mass Storage driver...
Jun 29 18:57:26 localhost kernel: [17180240.680000] scsi0 : SCSI emulation for USB Mass Storage devices
Jun 29 18:57:26 localhost kernel: [17180240.680000] usbcore: registered new driver usb-storage
Jun 29 18:57:26 localhost kernel: [17180240.680000] USB Mass Storage support registered.
Jun 29 18:57:31 localhost kernel: [17180245.684000]   Vendor: Apple     Model: iPod              Rev: 1.62
Jun 29 18:57:31 localhost kernel: [17180245.684000]   Type:   Direct-Access                  ANSI SCSI revision: 00
Jun 29 18:57:31 localhost kernel: [17180245.932000] Driver 'sd' needs updating - please use bus_type methods
Jun 29 18:57:31 localhost kernel: [17180245.948000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
Jun 29 18:57:31 localhost kernel: [17180245.952000] sda: Write Protect is off
Jun 29 18:57:31 localhost kernel: [17180245.968000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
Jun 29 18:57:31 localhost kernel: [17180245.972000] sda: Write Protect is off
Jun 29 18:57:31 localhost kernel: [17180245.972000]  sda: sda1 sda2
Jun 29 18:57:31 localhost kernel: [17180245.988000] sd 0:0:0:0: Attached scsi removable disk sda
Jun 29 18:57:31 localhost kernel: [17180246.012000] sd 0:0:0:0: Attached scsi generic sg0 type 0

---

### Post by ephesius on 2006-06-30
bump

---

### Post by ephesius on 2006-07-05
Further searching led me to this post [http://ubuntuforums.org/showthread.php?t=27416](http://ubuntuforums.org/showthread.php?t=27416)

There isn't a solution but there is a workaround.

```
sudo modprobe -r ehci-hcd
```

---

