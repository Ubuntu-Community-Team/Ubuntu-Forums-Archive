---
title: "Mp3 player not mounting on ubuntu 9.04"
date: 2009-09-20
forum: General Help
---

### Post by cherva on 2009-09-20
When I plug it in I get this in dmesg
```
[  433.523030] usb 5-3: new high speed USB device using ehci_hcd and address 6
[  433.751667] usb 5-3: configuration #1 chosen from 1 choice
cherva@mitosoft:~$ dmesg | tail
[  427.311458] scsi 4:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  427.311461] scsi 4:0:0:0: [sda] Sense not available.
[  427.311465] scsi 4:0:0:0: rejecting I/O to dead device
[  427.311468] scsi 4:0:0:0: [sda] Write Protect is off
[  427.311470] scsi 4:0:0:0: [sda] Mode Sense: 00 00 00 00
[  427.311472] scsi 4:0:0:0: [sda] Assuming drive cache: write through
[  427.311505] scsi 4:0:0:0: rejecting I/O to dead device
[  427.311513] scsi 4:0:0:0: rejecting I/O to dead device

```
and then the device restarts and the same mesage pops up again and again ... anyone knowing how to fix this ?

---

### Post by 3rdalbum on 2009-09-20
Try plugging it directly into the computer, i.e. not into a hub and not using an extension cable.

---

### Post by cherva on 2009-09-20
I can't I have to use usb to mini usb cable, because the mini usb is the only jack on the mp3 player

---

