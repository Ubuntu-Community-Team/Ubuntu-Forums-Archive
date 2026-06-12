---
title: "Problem syncing iTouch 4G in Rhythmbox."
date: 2010-12-16
forum: General Help
---

### Post by Furi on 2010-12-16
This is some really weird issue. Whenever I plug in the iTouch, it plays that one connection sound twice, pretty close to eachother. The first time, on Rhythmbox, it shows up the iTouch. On the second tone, which is the same tone, it disappears. What's up with this?

EDIT: It shows it up as "Unknown Device".
Also,
```

Device 0 (VID=05ac and PID=129e) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
LIBMTP WARNING: no MTP vendor extension on device 27 on bus 2LIBMTP WARNING: VendorExtensionID: 00000000LIBMTP WARNING: VendorExtensionDesc: Device has no vendor extensionsLIBMTP WARNING: this typically means the device is PTP (i.e. a camera) but not an MTP device at all. Trying to continue anyway.LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!
LIBMTP PANIC: could not inspect object property descriptions!

(rhythmbox:727): RhythmDB-CRITICAL **: rhythmdb_entry_unref: assertion `entry != NULL' failed

(rhythmbox:727): RhythmDB-CRITICAL **: rhythmdb_entry_unref: assertion `entry != NULL' failed
```
This is what it says on terminal when this happens.

---

### Post by Furi on 2010-12-17
Bump.

If it helps any, it claims that the "iPod" (folder's name) is a photo device, and recommends me to open Shotwell to check it out. I've tried this, and it calls it a "USB PTP Class Camera". Nothing is on it though.

---

### Post by Furi on 2010-12-17
Bump.
I've used my sister's laptop as a quick-fix alternative, but I still need to be able to sync on my laptop.

---

### Post by Furi on 2010-12-18
New stuff.
Just tried out Banshee.
When I plug the touch in, same thing happens, but a pop-up window appears.
```
**Could not display "gphoto2://[usb:002,031]/".**

Error: DBus error org.freedesktop.DBus.Error.UnknownMethod: Method "QueryInfo" with signature "aysus" on interface "org.gtk.vfs.Mount" doesn't exist

Please select another viewer and try again.
```

Tried again, and...
```
**Could not display "gphoto2://[usb:002,032]/".**

Error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Please select another viewer and try again.

```

---

### Post by Furi on 2010-12-19
I've managed to get everything working up to the point to where it actually knows the iPod touch's name, but now I deleted the iTunes_Control folder for it to be regenerated in hopes of being able to resync. Now nothing is working again. Great.

Rhythmbox asks to initialize the iTouch.
Banshee is stuck on loading it, and I can't even try to sync.

---

### Post by JeffoOfMetal on 2010-12-27
Broski! I've got the same problem. I've tried installing libimobiledevice, usbmuxd, ifuse, iphith-utils...I've tried the

ifuse mount /media/iPod 

thing after making the directory and nothing's working...I've had the same thing happen, the iPod connecting and disconnecting right away. At one point, Banshee seemed to recognize it, but I couldn't transfer music due to some error about the music not being in a correct format.

What a headache.

---

