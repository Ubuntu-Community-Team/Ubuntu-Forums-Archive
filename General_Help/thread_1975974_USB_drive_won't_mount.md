---
title: "USB drive won't mount"
date: 2012-05-08
forum: General Help
---

### Post by woodyg on 2012-05-08
I have a problem with a USB drive that won't mount unless I reboot. I really don't know where to start looking for the underlying problem...  **/var/log/syslog **looks like this[B]:

[/B][PHP]May  8 08:06:06 mu-ThinkPad-Edge kernel: [77879.136591] usb 1-1.1: new high-speed USB device number 8 using ehci_hcd
May  8 08:06:06 mu-ThinkPad-Edge kernel: [77879.230431] scsi10 : usb-storage 1-1.1:1.0
May  8 08:06:06 mu-ThinkPad-Edge mtp-probe: checking bus 1, device 8: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1"
May  8 08:06:06 mu-ThinkPad-Edge mtp-probe: bus: 1, device: 8 was not an MTP device
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.227548] scsi 10:0:0:0: Direct-Access     Generic  USB Flash Drive  1.00 PQ: 0 ANSI: 2
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.228911] sd 10:0:0:0: Attached scsi generic sg2 type 0
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.231649] sd 10:0:0:0: [sdb] 2048001 512-byte logical blocks: (1.04 GB/1000 MiB)
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.233933] sd 10:0:0:0: [sdb] Write Protect is off
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.233942] sd 10:0:0:0: [sdb] Mode Sense: 03 00 00 00
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.234428] sd 10:0:0:0: [sdb] No Caching mode page present
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.234434] sd 10:0:0:0: [sdb] Assuming drive cache: write through
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.237157] sd 10:0:0:0: [sdb] No Caching mode page present
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.237163] sd 10:0:0:0: [sdb] Assuming drive cache: write through
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.241226]  sdb: sdb1
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.243406] sd 10:0:0:0: [sdb] No Caching mode page present
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.243412] sd 10:0:0:0: [sdb] Assuming drive cache: write through
May  8 08:06:07 mu-ThinkPad-Edge kernel: [77880.243417] sd 10:0:0:0: [sdb] Attached SCSI removable disk[/PHP]Ideas what the problem might be or what I should look at?[B] :confused:
[/B]

---

