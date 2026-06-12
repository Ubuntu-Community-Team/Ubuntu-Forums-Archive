---
title: "No USB drive?"
date: 2010-11-14
forum: General Help
---

### Post by icehammer on 2010-11-14
I plug in my Maxtor 1TB external USB drive, and here's what dmesg says:

```

[   82.480054] usb 3-2: new full speed USB device using ohci_hcd and address 7
[   82.660052] usb 3-2: device descriptor read/64, error -62
[   82.950076] usb 3-2: device descriptor read/64, error -62
[   83.240064] usb 3-2: new full speed USB device using ohci_hcd and address 8
[   83.420053] usb 3-2: device descriptor read/64, error -62
[   83.710065] usb 3-2: device descriptor read/64, error -62
[   84.000057] usb 3-2: new full speed USB device using ohci_hcd and address 9
[   84.420053] usb 3-2: device not accepting address 9, error -62
[   84.600072] usb 3-2: new full speed USB device using ohci_hcd and address 10
[   85.020058] usb 3-2: device not accepting address 10, error -62
[   85.020102] hub 3-0:1.0: unable to enumerate USB device on port 2

```

lsusb produces no results, and "fdisk -l" yields nothing as well.
The drive is not recognised as /dev/sdb1 as it was until yesterday.

Help?

---

### Post by TeoBigusGeekus on 2010-11-14
[This]("http://ubuntuforums.org/showthread.php?t=1195601&page=3") perhaps?

---

### Post by icehammer on 2010-11-14
Tried something similar. No joy.

---

### Post by TeoBigusGeekus on 2010-11-14
Perhaps [this]("http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/") then?

---

### Post by icehammer on 2010-11-14
Still nothing. I don't think its really a problem of the device not supporing USB 2.0. It's been working for the past 7-8 months! Something random happened in the past day or two, i guess.
I'll try a diff cable soon, see if that helps.

---

### Post by TeoBigusGeekus on 2010-11-14
Sorry man, I'm just googling and posting whatever seems appropriate.
I've never encountered something like this - I hope you'll have it sorted.

---

### Post by icehammer on 2010-11-14
No worries. I appreciate the help!

---

### Post by icehammer on 2010-11-14
I dunno what I did, but it works now.
It always wanted to mount to a certain point, which existed, but it wouldn't use. So I booted with a different USB drive this time, and even that wanted to go that same mount point! Anyway, so I got rid of the mount point, formatted one of them, and now both drives work.

Any explanations why both drives wanted to go to /media/DRIVE2 as a mountpoint?

---

