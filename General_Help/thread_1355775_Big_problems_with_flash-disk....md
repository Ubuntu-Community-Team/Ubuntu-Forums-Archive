---
title: "Big problems with flash-disk..."
date: 2009-12-15
forum: General Help
---

### Post by fr0d0 on 2009-12-15
Hello. I have a problem with my flash disk... I have an old computer and I've installed Debian 5 on it. I downloaded some packages from my laptop with a script, uploaded it to a flash disk and inserted it the old computer. This wasn't mounted. I turned it off and than taked my flash disk. But it is not mounting now in my ubuntu...:(
What can I do? How can I create a filesystem on it and what is the problem?

Also, if needed, lsusb output about this device:
Bus 002 Device 014: ID 090c:3000 Feiya Technology Corp.

---

### Post by bonfire89 on 2009-12-15
the output of

sudo fdisk -l

might help in solving this.

---

### Post by fr0d0 on 2009-12-15
sudo fdisk -l
Output:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d342d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2562    20579233+   7  HPFS/NTFS
/dev/sda2            2563        8311    46178842+   5  Extended
/dev/sda3            8312       10743    19535040   83  Linux
/dev/sda4           10744       10986     1951897+  82  Linux swap / Solaris
/dev/sda5            2563        8311    46178811    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x296e2f22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS

---

### Post by fr0d0 on 2009-12-15
There is no flash disk...

---

### Post by fr0d0 on 2009-12-15
output of "tail -f /var/log/messages" when I insert flash disk:
Dec 15 17:33:00 localhost kernel: [29957.296121] usb 2-1: new high speed USB device using ehci_hcd and address 15
Dec 15 17:33:00 localhost kernel: [29957.440707] usb 2-1: configuration #1 chosen from 1 choice
Dec 15 17:33:00 localhost kernel: [29957.441122] scsi11 : SCSI emulation for USB Mass Storage devices
Dec 15 17:33:05 localhost kernel: [29962.443221] scsi 11:0:0:0: Direct-Access              USB MEMORY BAR   1000 PQ: 0 ANSI: 0 CCS
Dec 15 17:33:05 localhost kernel: [29962.447048] sd 11:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
Dec 15 17:33:05 localhost kernel: [29962.447926] sd 11:0:0:0: [sdc] Write Protect is off
Dec 15 17:33:05 localhost kernel: [29962.469274] sd 11:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
Dec 15 17:33:05 localhost kernel: [29962.470157] sd 11:0:0:0: [sdc] Write Protect is off
Dec 15 17:33:05 localhost kernel: [29962.470184]  sdc:<3>end_request: I/O error, dev sdc, sector 0
Dec 15 17:33:05 localhost kernel: [29962.471414] __ratelimit: 4 callbacks suppressed
Dec 15 17:33:06 localhost kernel: [29962.503438] Dev sdc: unable to read RDB block 0
Dec 15 17:33:06 localhost kernel: [29962.519196]  unable to read partition table
Dec 15 17:33:06 localhost kernel: [29962.519450] sd 11:0:0:0: [sdc] Attached SCSI removable disk
Dec 15 17:33:06 localhost kernel: [29962.519633] sd 11:0:0:0: Attached scsi generic sg3 type 0

---

