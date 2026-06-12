---
title: "broke my external hd. can i fix it?"
date: 2009-09-04
forum: General Help
---

### Post by daweefolk on 2009-09-04
i was partitioning my external hd with gparted and it froze/crashed. now when i reopened it to try and do it again, i got this in the terminal. ```
 Input/output error during read on /dev/sdb
```
I'm guessing that mean i corrupted it or something. is there any command or something i can use to fix it?

---

### Post by Whiffle on 2009-09-04
what is the output of "sudo fdisk -l" with teh drive plugged in ?

---

### Post by daweefolk on 2009-09-04
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd02fd02

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

```

---

### Post by Whiffle on 2009-09-04
Hmm don't see it there.  Unplug it from the computer, power it off, plug it back into the computer, turn it on, and then post the last 30 lines or so of "dmesg".

---

### Post by daweefolk on 2009-09-04
```

[ 1811.610593] end_request: I/O error, dev sdb, sector 1953525160
[ 1811.610602] Buffer I/O error on device sdb, logical block 244190645
[ 1811.640931] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1811.640943] sd 7:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1811.640953] sd 7:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1811.640964] end_request: I/O error, dev sdb, sector 0
[ 1811.640971] Buffer I/O error on device sdb, logical block 0
[ 1811.670940] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1811.670951] sd 7:0:0:0: [sdb] Sense Key : Medium Error [current] 
[ 1811.670961] sd 7:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1811.670971] end_request: I/O error, dev sdb, sector 0
[ 2290.797455] usb 1-2: USB disconnect, address 5
[ 2315.428114] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 2315.564981] usb 1-1: configuration #1 chosen from 1 choice
[ 2315.566081] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2315.566255] usb-storage: device found at 6
[ 2315.566261] usb-storage: waiting for device to settle before scanning
[ 2320.564351] usb-storage: device scan complete
[ 2320.568104] scsi 8:0:0:0: Direct-Access     WDC WD10 EAVS-00D7B0           PQ: 0 ANSI: 2
[ 2320.570413] sd 8:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 2320.572781] sd 8:0:0:0: [sdb] Write Protect is off
[ 2320.572788] sd 8:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 2320.572793] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2320.584276] sd 8:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[ 2320.588027] sd 8:0:0:0: [sdb] Write Protect is off
[ 2320.588037] sd 8:0:0:0: [sdb] Mode Sense: 38 00 00 00
[ 2320.588043] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 2320.588318]  sdb: sdb1
[ 2320.592190] sd 8:0:0:0: [sdb] Attached SCSI disk
[ 2320.592343] sd 8:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by Whiffle on 2009-09-04
Looks like it connected correctly.  Now try "sudo fdisk -l" it should show up.  If that works give gparted another shot.

---

### Post by hal10000 on 2009-09-04
> Looks like it connected correctly
No, i don't think it looks correct, there are I/O errors although it seems to connect after a few trials.

Try to plug it in and off and mount/unmount it a few times. If th errors occur repeatedly, then it either the harddrive itself, the cable or the harrdives case might be damaged.

---

### Post by Whiffle on 2009-09-05
I've seen perfectly good drives do this in the past.  They'll screw up a couple of times if something isn't right with the usb, then it'll work correctly and not have a problem again.  USB is picky :/

---

### Post by daweefolk on 2009-09-10
what exactly does this mean? ```
[ 1627.361053] Buffer I/O error on device sdc, logical block 6805059
[ 1627.361066] Buffer I/O error on device sdc, logical block 6805059
[ 1627.361078] Buffer I/O error on device sdc, logical block 6805059
[ 1627.361095] Buffer I/O error on device sdc, logical block 6805060
[ 1627.361106] Buffer I/O error on device sdc, logical block 6805060
[ 1627.361117] Buffer I/O error on device sdc, logical block 6805060
[ 1627.361129] Buffer I/O error on device sdc, logical block 6805060
[ 1627.361145] Buffer I/O error on device sdc, logical block 6805061
[ 1627.361156] Buffer I/O error on device sdc, logical block 6805061
[ 1627.361168] Buffer I/O error on device sdc, logical block 6805061

```
and how do i fix it?

---

### Post by Whiffle on 2009-09-10
Sounds like you've got a failing hard drive.

---

### Post by daweefolk on 2009-09-10
nothing I can do?

---

### Post by Whiffle on 2009-09-10
Not really, it sounds like its either crashing or about to crash.  I'd probably just get a new one, continuing to use that one will only be a pain in the rear.

---

### Post by daweefolk on 2009-09-10
ok. i guess i'll shrink my main partition so i can get some room. i want to install solaris or pc-bsd

---

