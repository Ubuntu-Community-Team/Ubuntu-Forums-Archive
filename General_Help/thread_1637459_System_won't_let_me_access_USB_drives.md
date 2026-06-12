---
title: "System won't let me access USB drives"
date: 2010-12-04
forum: General Help
---

### Post by Vahkiti on 2010-12-04
Ok, from what I can tell this is a common issue with nobody getting a definite fix. I've tried different things, SD card reader, PSP, flash drive, and nothing happens with any of them. The PSP won't connect and nothing else shows up. I know the system RECOGNIZES them and to further stress this point, in light of saving time, I have the kernel log here:

> Dec  4 14:15:00 MataNui2 kernel: [36407.510532] usb 1-2.3: new full speed USB device using uhci_hcd and address 7
Dec  4 14:15:00 MataNui2 kernel: [36407.826064] scsi5 : usb-storage 1-2.3:1.0
Dec  4 14:15:02 MataNui2 kernel: [36409.606401] scsi 5:0:0:0: Direct-Access     Generic  USB  SD Reader   0.00 PQ: 0 ANSI: 2
Dec  4 14:15:02 MataNui2 kernel: [36409.633269] sd 5:0:0:0: Attached scsi generic sg3 type 0
Dec  4 14:15:02 MataNui2 kernel: [36409.646468] sd 5:0:0:0: [sdb] 3932160 512-byte logical blocks: (2.01 GB/1.87 GiB)
Dec  4 14:15:02 MataNui2 kernel: [36409.649975] sd 5:0:0:0: [sdb] Write Protect is off
Dec  4 14:15:02 MataNui2 kernel: [36409.670352]  sdb: sdb1
Dec  4 14:15:02 MataNui2 kernel: [36409.694311] sd 5:0:0:0: [sdb] Attached SCSI removable disk

I'm running Xubuntu 10.10 on a Pentuim II system, (I know, ugh...). I just installed it yesterday and already it seems to be buggier than windows running Kernel Ex. All the devices I've tried are formatted in FAT filesystem and worked perfectly fine under my previous OS, Windows ME, and other computers including my friend's Mac. 

Can anyone give me a solid solution to this issue? :)

---

