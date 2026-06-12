---
title: "sort of corrupted usb drive?"
date: 2012-07-16
forum: General Help
---

### Post by panther8644 on 2012-07-16
Hey guys!
I recently found a flash drive laying around and wanted to format it to use for myself. The problem occurred when the drive said it only had 5.6k of storage on it when it should be in the gigs range, and it will not show up in gparted. it shows up in disk management but won't let me do anything to it. I have tried accessing it via the terminal but I always get "Input/output error". I thought it was totally toast, but then i ran
 "sudo dd if=/dev/zero of=/dev/sdc"
and it actually wrote 0's to the 5.6k that is recognized.

i am so confused as to if the drive is actually toast, or just hiding its memory very well lol

thanks for any help you guys can give!

---

### Post by ajgreeny on 2012-07-16
Does ```
sudo fdisk -l
``` see it and show any useful info?

---

### Post by panther8644 on 2012-07-17
nope, it just lists the main drive and its partitions.

---

### Post by ajgreeny on 2012-07-17
OK, so plug it in (after removing it if it's already attached) then immediately run ```
dmesg | tail
``` and report back the output.

However, I suspect that the flash drive is probably dead.

---

### Post by panther8644 on 2012-07-17
this is what it output, thanks for helping btw :)

```
jonathan@jonathan-OptiPlex-745:~$ dmesg | tail
[ 1564.411527] sd 5:0:0:0: [sdc] Mode Sense: 10 00 00 00
[ 1564.412272] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1564.423481]  sdc: sdc1
[ 1564.425385] sd 5:0:0:0: [sdc] Attached SCSI disk
[ 1583.172284] usb 1-4: USB disconnect, device number 6
[ 1583.206738] sd 5:0:0:0: [sdc] Synchronizing SCSI cache
[ 1583.206780] sd 5:0:0:0: [sdc]  Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 9225.849885] usb 1-3: USB disconnect, device number 4
[ 9228.736025] usb 1-3: new high-speed USB device number 7 using ehci_hcd
[ 9228.887115] scsi6 : usb-storage 1-3:1.0
jonathan@jonathan-OptiPlex-745:~$ dmesg | tail
[ 9230.172904] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9230.172910] sd 6:0:0:0: [sdb]  Sense Key : Illegal Request [current] 
[ 9230.172916] sd 6:0:0:0: [sdb]  Add. Sense: Logical block address out of range
[ 9230.172922] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 01 00 00 01 00
[ 9230.172936] end_request: I/O error, dev sdb, sector 1
[ 9230.173903] sd 6:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9230.173907] sd 6:0:0:0: [sdb]  Sense Key : Illegal Request [current] 
[ 9230.173913] sd 6:0:0:0: [sdb]  Add. Sense: Logical block address out of range
[ 9230.173920] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 02 00 00 01 00
[ 9230.173933] end_request: I/O error, dev sdb, sector 2

```

---

