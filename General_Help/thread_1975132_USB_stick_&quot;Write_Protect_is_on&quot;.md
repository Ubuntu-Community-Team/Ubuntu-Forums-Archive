---
title: "USB stick &quot;Write Protect is on&quot;"
date: 2012-05-07
forum: General Help
---

### Post by MichaelBurns on 2012-05-07
I just purchased this PATRIOT 16GB Axle tonight.  The first thing that I did was to change the fs label from "patriot" to "pinky" (because they come in black and pink, and I already have a black one, so I bought a pink one).
```

$ dosfslabel /dev/sdd1 pinky

```
I unplugged and replugged "pinky" into the USB port, just to make sure that Ubuntu would recognize it as "pinky".  Then, I plugged in my other PATRIOT 16GB stick named "patriot", mounted them both (clicking their names in the nautilus side pane), and then used nautilus to copy all of the files from "patriot" to "pinky" (Ctl-A Ctl-C at the root of "patriot" and then Ctl-V at the root of "pinky").

After about 20 minutes, the errors began.  It became obvious that something had gone horribly wrong when I clicked the "skip" button over and over again.  So, I clicked the "cancel" button on the file transfer dialog box, and then unmounted both drives (by clicking the ejection symbol in the nautilus side pane).  I killed pinky!

dmesg indicates that the partition table was destroyed (I guess).
```

[ 6027.272275]  sdd: unknown partition table

```
(I realize that the device node can change from one plug to the next; this is the same device.)
So, I tried to recreate the partition and filesystem with fdsik, but ...
```

$ sudo fdisk /dev/sdd
n,p,,,t,b,w
Unable to write /dev/sdd

```
Uh oh.  So, I tried to simply wipe the entire stick.
```

$ sudo dd if=/dev/zero of=/dev/sdd
dd: opening `/dev/sdd': Read-only file system

```
Well $#!t.  Now what.  For whatever reason, I decided to view the output of dmesg again (because it is so thoroughly entertaining and meaningful).  There was something that I found kind of strange.
```

[10200.895135] sd 17:0:0:0: [sdd] Write Protect is on

```
Now what on Earth could that possibly mean?  This is NOT and SD card; it is a USB stick; there's no switch to set such a mode.  Any ideas?  (i.e. how to turn off the write protect?)

BTW, the first several thousand bytes (according to dd) are null.  (Thus the missing partition table, right?)  However, after running dd open-ended, I saw that there is definitely much data stored somewhere on the stick, at least in the first 30MB when I cancelled dd.

---

### Post by MichaelBurns on 2012-05-07
What is the meaning of "Mode Sense" in the dmesg output?  I'm wondering if this is the culprit, and is there a way to disable it.

The normal-functioning 16GB PATRIOT:
```

[ 1052.894685] usb 1-2: configuration #1 chosen from 1 choice
[ 1052.895387] scsi14 : SCSI emulation for USB Mass Storage devices
[ 1052.895791] usb-storage: device found at 14
[ 1052.895803] usb-storage: waiting for device to settle before scanning
[ 1057.892433] usb-storage: device scan complete
[ 1058.160865] scsi 14:0:0:0: Direct-Access     General  USB Flash Disk   1100 PQ: 0 ANSI: 0 CCS
[ 1058.165875] sd 14:0:0:0: Attached scsi generic sg3 type 0
[ 1058.169617] sd 14:0:0:0: [sdd] 31494144 512-byte logical blocks: (16.1 GB/15.0 GiB)
[ 1058.170457] sd 14:0:0:0: [sdd] Write Protect is off
[ 1058.170473] sd 14:0:0:0: [sdd] Mode Sense: 43 00 00 00
[ 1058.170483] sd 14:0:0:0: [sdd] Assuming drive cache: write through
[ 1058.173937] sd 14:0:0:0: [sdd] Assuming drive cache: write through
[ 1058.173961]  sdd: sdd1
[ 1058.177824] sd 14:0:0:0: [sdd] Assuming drive cache: write through
[ 1058.177847] sd 14:0:0:0: [sdd] Attached SCSI removable disk

```

The read-only-device-node brand-new 16GB PATRIOT:
```

[  865.066569] usb 1-1: configuration #1 chosen from 1 choice
[  865.067309] scsi12 : SCSI emulation for USB Mass Storage devices
[  865.067781] usb-storage: device found at 10
[  865.067793] usb-storage: waiting for device to settle before scanning
[  870.064416] usb-storage: device scan complete
[  870.227605] scsi 12:0:0:0: Direct-Access     SMI      USB DISK         1100 PQ: 0 ANSI: 4
[  870.230746] sd 12:0:0:0: Attached scsi generic sg3 type 0
[  870.237985] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[  870.254822] sd 12:0:0:0: [sdd] 31405824 512-byte logical blocks: (16.0 GB/14.9 GiB)
[  870.255611] sd 12:0:0:0: [sdd] Write Protect is on
[  870.255627] sd 12:0:0:0: [sdd] Mode Sense: 43 00 80 00
[  870.255639] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[  870.258346] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[  870.258504]  sdd: unknown partition table

```

Note the subtle differences:
The read-only stick has the line
```

[  870.237985] sd 12:0:0:0: [sdd] Attached SCSI removable disk

```
whereas the normal-functioning stick does not.
And then the mode sense lines are different: with 43 00 00 00 for the normal-functioning stick, but 43 00 80 00 for the read-only stick.

---

### Post by MichaelBurns on 2012-05-07
Is there a tool available in ubuntu that can access the firmware on a usb drive?  Or this is too esoteric (and I am at the mercy of PATRIOT)?  I am only guessing that this is some firmware setting that I need to change on the usb drive.  (I hope that it isn't a symptom of outright physical damage, because this was literally the first file transfer operation that I attempted with the drive right out of the package.)

(up way too late last night annoyed by this issue)

---

