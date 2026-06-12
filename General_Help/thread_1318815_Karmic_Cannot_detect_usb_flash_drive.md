---
title: "Karmic: Cannot detect usb flash drive"
date: 2009-11-07
forum: General Help
---

### Post by nisix on 2009-11-07
lsusb does not detect it; usb works fine when I tried it on a win7 machine

/var/log/messages output:
```
[ 3766.288093] usb 1-2: new full speed USB device using uhci_hcd and address 10
[ 3766.462860] usb 1-2: configuration #1 chosen from 1 choice
[ 3766.466189] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3771.468572] scsi 3:0:0:0: Direct-Access     Kingston DT 101 II        1.00 PQ: 0 ANSI: 2
[ 3771.469647] sd 3:0:0:0: Attached scsi generic sg3 type 0
[ 3771.485968] sd 3:0:0:0: [sdc] 7833600 512-byte logical blocks: (4.01 GB/3.73 GiB)
[ 3771.488769] sd 3:0:0:0: [sdc] Write Protect is off
[ 3771.510727]  sdc:
[ 3771.784565] usb 1-2: reset full speed USB device using uhci_hcd and address 10
[ 3773.368101] usb 1-2: reset full speed USB device using uhci_hcd and address 10
[ 3773.928555] usb 1-2: reset full speed USB device using uhci_hcd and address 10
[ 3774.448089] usb 1-2: reset full speed USB device using uhci_hcd and address 10
[ 3774.856250] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.856256] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.856277] __ratelimit: 5 callbacks suppressed
[ 3774.856437] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.856443] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.856576] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.856583] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.856691] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.856697] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.856805] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.856812] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.856929] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.856935] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857040] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857046] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857150] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857156] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857263] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857269] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857301] Dev sdc: unable to read RDB block 0
[ 3774.857383] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857388] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857493] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857499] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857659] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857666] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857768] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857773] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857873] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857878] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.857977] sd 3:0:0:0: [sdc] Unhandled error code
[ 3774.857983] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.858006]  unable to read partition table
[ 3774.858667] sd 3:0:0:0: [sdc] READ CAPACITY failed
[ 3774.858675] sd 3:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3774.858683] sd 3:0:0:0: [sdc] Sense not available.
[ 3774.858785] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[ 3774.858823] usb 1-2: USB disconnect, address 10
```

---

### Post by nisix on 2009-11-07
Any hint or link on a workaround for this? (I googled already and most of the stuff I found didn't work)

I need access to this usb as all my backups are there.

---

### Post by g000we on 2010-01-14
Hi,

In gnome, I went to the main bar.

1) System -> Administration -> Synatpic Package Manager
2) Search on 'usb'.
3) Selected the checkbox for 'usbmount'.
4) Click on 'Apply', and another popup to confirm details, etc.

Once finished installing, I plugged my USB storage device into my machine, and when I open Computer, I can see the removable drive accessible like any other drive.

Hope this helps in some way :)

g000we

---

### Post by Umang on 2010-02-01
> **g000we said:**
> Hi,

In gnome, I went to the main bar.

1) System -> Administration -> Synatpic Package Manager
2) Search on 'usb'.
3) Selected the checkbox for 'usbmount'.
4) Click on 'Apply', and another popup to confirm details, etc.

Once finished installing, I plugged my USB storage device into my machine, and when I open Computer, I can see the removable drive accessible like any other drive.

Hope this helps in some way :)

g000weI seriously didn't want to believe you. Didn't think that I needed to install something to read the very same USB Drive that worked last week. But out of helplessness I tried it. I still don't understand why it worked.

Thank you

---

