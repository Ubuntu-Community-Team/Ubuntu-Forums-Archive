---
title: "ipod mounting problems"
date: 2011-03-21
forum: General Help
---

### Post by JohnReid on 2011-03-21
Hi,

I'm having problems mounting my ipod on both my ubuntu and mythbuntu boxes.

I've already some details here about mounting on mythbuntu.
[http://ubuntuforums.org/showthread.php?t=1679204](http://ubuntuforums.org/showthread.php?t=1679204)

On ubuntu I get the following from sudo fdisk -l:
```

Disk /dev/sdb: 159.8 GB, 159840301056 bytes
26 heads, 50 sectors/track, 30018 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30019   156093788    b  W95 FAT32
Partition 1 does not start on physical sector boundary.

```

which looks fishy to me. I guess fdisk should be able to understand the partitions.

When I run gtkpod. I get messages about:

- checksum information does not match in iTunesDB
- iPod database import failed. Illegal seek to offset 0 in one of the playlist files.

Which also kind of worries me. Then gtkpod won't let me save the changes.

I'm not sure where to go for help though. My last post here didn't get much response.

This is the part of dmesg resulting from plugging the ipod in via usb

```
[ 8739.581604] usb 2-1: new high speed USB device using ehci_hcd and address 3
[ 8739.732378] usb 2-1: configuration #1 chosen from 2 choices
[ 8739.835538] Initializing USB Mass Storage driver...
[ 8739.835818] scsi6 : SCSI emulation for USB Mass Storage devices
[ 8739.836019] usbcore: registered new interface driver usb-storage
[ 8739.836026] USB Mass Storage support registered.
[ 8739.836798] usb-storage: device found at 3
[ 8739.836804] usb-storage: waiting for device to settle before scanning
[ 8744.830426] usb-storage: device scan complete
[ 8744.838964] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 8744.840863] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 8744.861232] sd 6:0:0:0: [sdb] Spinning up disk....ready
[ 8748.591025] sd 6:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 8748.591644] sd 6:0:0:0: [sdb] Write Protect is off
[ 8748.591651] sd 6:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 8748.591657] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 8748.593999] sd 6:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 8748.594628] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 8748.594638]  sdb: sdb1
[ 8748.776382] sd 6:0:0:0: [sdb] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 8748.776979] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 8748.776989] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```


Any help appreciated!

Thanks,
John.

---

### Post by Wobblybob on 2011-03-21
Hi mate, I think your problem is probabley iPod related and therefore would recommend a complete reset of the ipod, this can be done in gtkpod [I think] or floola [google it] if you do not have access to Windows itunes prog.

it may be work telling us what model of ipod you have mke, model, size etc

---

