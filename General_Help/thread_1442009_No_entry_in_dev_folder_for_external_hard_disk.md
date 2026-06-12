---
title: "No entry in /dev/ folder for external hard disk"
date: 2010-03-29
forum: General Help
---

### Post by uast23 on 2010-03-29
Hi,

I am trying to mount an external hard disk using a USB docking station but I am kind of stuck.

I can see the entries for different partitions of the hard disk in fdisk -l but there is no node file created in /dev folder. So, I am not able to mount. 

Something like this -

#sudo fdisk -l

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5bdf0ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1             131         654     4196352+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdd2             654        1176     4196352+  83  Linux
/dev/sdd3            1176        1437     2098176+  fe  LANstep
/dev/sdd4            1437       38914   301031254+  83  Linux

#ls -l /dev/ | grep sdd
brw-rw----  1 root disk      8,  48 2010-03-29 17:38 sdd

So, there are the entries sdd1, sdd2 .. in fdisk -l but I dont see any entries in /dev/ folder for separate partitions.

Any inputs on how to mount this disk ?

---

### Post by sisco311 on 2010-03-29
Unplug it and plug it back, then post the output of:
```
dmesg | tail -20
```

---

### Post by uast23 on 2010-03-29
#dmesg | tail -20
[707905.800184] VFS: Can't find ext3 filesystem on dev sdd.
[707912.733093] FAT: bogus number of reserved sectors
[707912.733105] VFS: Can't find a valid FAT filesystem on dev sdd.
[709978.836226] usb 1-5: USB disconnect, address 30
[709999.340076] usb 1-6: new high speed USB device using ehci_hcd and address 31
[709999.473738] usb 1-6: configuration #1 chosen from 1 choice
[709999.474773] scsi70 : SCSI emulation for USB Mass Storage devices
[709999.475099] usb-storage: device found at 31
[709999.475104] usb-storage: waiting for device to settle before scanning
[710004.472246] usb-storage: device scan complete
[710004.473874] scsi 70:0:0:0: Direct-Access     Generic  External         2.10 PQ: 0 ANSI: 4
[710004.474872] sd 70:0:0:0: Attached scsi generic sg2 type 0
[710004.477434] sd 70:0:0:0: [sdd] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[710004.478289] sd 70:0:0:0: [sdd] Write Protect is off
[710004.478296] sd 70:0:0:0: [sdd] Mode Sense: 21 00 00 00
[710004.478302] sd 70:0:0:0: [sdd] Assuming drive cache: write through
[710004.479783] sd 70:0:0:0: [sdd] Assuming drive cache: write through
[710004.479791]  sdd: sdd1 sdd2 sdd3 sdd4
[710004.530285] sd 70:0:0:0: [sdd] Assuming drive cache: write through
[710004.530293] sd 70:0:0:0: [sdd] Attached SCSI disk

---

### Post by uast23 on 2010-03-31
I think my machine was acting kind of weird. After an "unintentional" reboot, everything came back to shape. I could see all the entries sdc1,sdc2... in /dev folder. 

I am not sure about the reason yet (may be my machine was tired of running endlessly without reboot :-) which is highly unlikely).

Thanks for all the replies

---

