---
title: "External USB hard-disk randomly shutting down"
date: 2010-08-30
forum: General Help
---

### Post by DGarret on 2010-08-30
Hey guys, always hate having to post here, usually pretty successful digging up solutions through searches on my own but not having any luck this time and it's driving me crazy. Hope someone around here has an idea of what's up.

I've got an external Toshiba USB hard drive, never caused me problems before, and never used to act up like this under Ubuntu (at least not this badly, but I've only been on Ubuntu for a few months now). Basically, I can turn it on and use it and everything is lovely, but after a few minutes, especially if I'm not using it, it shuts off. I used to figure it was just a power-down feature, because it never used to turn off when I was listening to music or watching a movie off the drive or what have you (just when I left it idle), but lately it's been switching itself off or otherwise glitching every few minutes regardless.

Just a few details for the record, I have another older external external USB disk I've never have this switching-off problem with. Both are powered externally, so I wouldn't think pulling too much juice from the USB port and inadvertently knocking it out would be the issue here. Likewise, it doesn't seem to be overheating in the least. And just to clarify, it does run just fine under my Windows boot all day long, no problems, so I was thinking it had to be something Ubuntu-specific.

Anyway, any help would be much appreciated. Thanks in advance!

---

### Post by Sam on 2010-08-30
When your HD shutdowns, run in a terminal:```
dmesg
```Is there any error related to your external HD (look at the end of the output) ?

---

### Post by DGarret on 2010-08-30
Hey, now there's a command that's good to know. :D

Looks like the error is about here:

```
[12464.224420] usb 1-4: USB disconnect, address 9
[12464.224554] sd 5:0:0:1: [sdb] Unhandled error code
[12464.224558] sd 5:0:0:1: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[12464.224562] sd 5:0:0:1: [sdb] CDB: Read(10): 28 20 03 4a 75 67 00 00 60 00
[12464.224575] end_request: I/O error, dev sdb, sector 55211367
[12464.224787] sd 5:0:0:1: [sdb] Unhandled error code
[12464.224790] sd 5:0:0:1: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[12464.224794] sd 5:0:0:1: [sdb] CDB: Read(10): 28 20 03 4a 75 67 00 00 08 00
[12464.224804] end_request: I/O error, dev sdb, sector 55211367
[12468.064181] scsi 5:0:0:0: rejecting I/O to dead device

```

---

### Post by Sam on 2010-08-30
It looks like a physical problem.

Does the disk has the SMART feature? Check in System/Administration/Disk Utility if there is a failure.

Are you using the default power cord?

---

