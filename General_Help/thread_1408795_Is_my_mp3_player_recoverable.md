---
title: "Is my mp3 player recoverable ?"
date: 2010-02-16
forum: General Help
---

### Post by Cigue on 2010-02-16
Edit : I only want to be able to connect it again to my computer, not recover what was on it !

Hey all, I have recently bought an mp3 player which I then tried to format. However, Windows failed me here and 99% through the formatting process it gave out an error. From then on, every time I plugged my mp3 player into my windows computer, the system froze.

Now I've plugged my player into ubuntu, hoping to repair it. here is what dmesg | tail returns :

```
carl@JohnnyCash:~$ dmesg | tail
[  140.935642] Buffer I/O error on device sdb, logical block 67064581
[  140.935650] Buffer I/O error on device sdb, logical block 67064582
[  140.935657] Buffer I/O error on device sdb, logical block 67064583
[  140.935909] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  140.935920] end_request: I/O error, dev sdb, sector 67064576
[  140.935927] Buffer I/O error on device sdb, logical block 67064576
[  140.935935] Buffer I/O error on device sdb, logical block 67064577
[  140.942632] scsi 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[  140.942650] end_request: I/O error, dev sdb, sector 67064736
[  140.951944] scsi 7:0:0:0: rejecting I/O to dead device
carl@JohnnyCash:~$ dmesg | tail
[  702.895739] sd 30:0:0:0: [sdb] Write Protect is off
[  702.895753] sd 30:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  702.895761] sd 30:0:0:0: [sdb] Assuming drive cache: write through
[  702.915082] sd 30:0:0:0: [sdb] 67064753 512-byte hardware sectors: (34.3 GB/31.9 GiB)
[  702.921627] sd 30:0:0:0: [sdb] Write Protect is off
[  702.921645] sd 30:0:0:0: [sdb] Mode Sense: 00 c0 00 00
[  702.921653] sd 30:0:0:0: [sdb] Assuming drive cache: write through
[  702.921677]  sdb:
[  703.076369] sd 30:0:0:0: [sdb] Attached SCSI removable disk
[  703.076647] sd 30:0:0:0: Attached scsi generic sg2 type 0
```

---

### Post by sgosnell on 2010-02-16
Why did you try to format it?  Having no idea what the brand or model is, I can't say at all whether it can be fixed.

---

### Post by Cigue on 2010-02-16
I thought it was a quick way to get rid of everything on it. I formatted it to FAT32, and the brand is a cheap chinese thing I got off Ebay (the only marks on it are MP4 PLAYER).

for information, fdisk -l won't show it.

---

### Post by Chronon on 2010-02-16
You might try to power down the player and connect USB while it is powered off.  Maybe there's a bootloader USB mode that still works properly.

---

### Post by Cigue on 2010-02-16
> **Chronon said:**
> You might try to power down the player and connect USB while it is powered off.  Maybe there's a bootloader USB mode that still works properly.

Awesome ! There was an evolution, here is what dmesg | tail shows :

```
[ 3168.428070] sd 129:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3168.428083] end_request: I/O error, dev sdb, sector 67064752
[ 3180.784346] usb 1-3: new high speed USB device using ehci_hcd and address 6
[ 3181.312054] usb 1-3: device not accepting address 6, error -71
[ 3181.740088] usb 2-2: new full speed USB device using ohci_hcd and address 4
[ 3181.940963] usb 2-2: not running at top speed; connect to a high speed hub
[ 3182.008137] usb 2-2: configuration #1 chosen from 1 choice
[ 3182.054479] scsi130 : SCSI emulation for USB Mass Storage devices
[ 3182.060325] usb-storage: device found at 4
[ 3182.060335] usb-storage: waiting for device to settle before scanning

```

EDIT : Seconds later...

```
[ 3341.969274] Buffer I/O error on device sdb, logical block 67064577
[ 3341.969283] Buffer I/O error on device sdb, logical block 67064578
[ 3341.969291] Buffer I/O error on device sdb, logical block 67064579
[ 3341.969298] Buffer I/O error on device sdb, logical block 67064580
[ 3341.969306] Buffer I/O error on device sdb, logical block 67064581
[ 3341.969314] Buffer I/O error on device sdb, logical block 67064582
[ 3341.969323] Buffer I/O error on device sdb, logical block 67064583
[ 3341.979153] sd 136:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 3341.979179] end_request: I/O error, dev sdb, sector 67064576
[ 3341.979198] Buffer I/O error on device sdb, logical block 67064576
[ 3341.979211] Buffer I/O error on device sdb, logical block 67064577
[ 3341.981952] sd 136:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3341.981974] end_request: I/O error, dev sdb, sector 67064736
[ 3354.346523] usb 1-3: new high speed USB device using ehci_hcd and address 20
[ 3354.876046] usb 1-3: device not accepting address 20, error -71

```

---

### Post by Cigue on 2010-02-16
bring up my post !

---

### Post by sgosnell on 2010-02-16
I'm afraid Windows may have toasted it.  Good luck with it.

---

### Post by NFblaze on 2010-02-16
Man I got this error + something similar when I kept wringling and moving my mp3 player back and forth. 

If I were you see if in the settings you have a format mode for in there. Try reformating. 

Also, what's fixed my mp3 player twice is using scandisk/checkdisk in Windows on the device. FAT32 has giving me some woes.

---

