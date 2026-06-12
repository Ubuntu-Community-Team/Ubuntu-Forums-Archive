---
title: "14 Seconds freeze while booting, caused by SCSI device"
date: 2010-06-25
forum: General Help
---

### Post by fontanini on 2010-06-25
Hello everyone, i'm having a 14 seconds freeze while booting. Dmesg  reports this:
(......)
[    6.228695] scsi 8:0:0:0: Direct-Access     Generic  Storage Device    0.00 PQ: 0 ANSI: 2
[    6.229137] sd 8:0:0:0: Attached scsi generic sg4 type 0
[    6.230428] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[   22.733453] udev: starting version 151
[   22.804051] Linux agpgart interface v0.103
(...)

/dev/sdd corresponds to a USB card reader(it is empty). I've seen many  posts on forums about this, but no solutions... 
I'm using lucid 32bits.
Hope somebody can help me!
Thanks in advance

---

### Post by fontanini on 2010-06-26
I've got something to add. Today when i first power on the pc, i was surprised to see that  this problem was gone:

(...)
[    6.232694] scsi 8:0:0:0: Direct-Access     Generic  Storage Device   0.00 PQ: 0 ANSI: 2
[    6.234331] sd 8:0:0:0: Attached scsi generic sg4 type 0
[    6.235675] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[    6.673181] Linux agpgart interface v0.103
[    6.974565] vga16fb: initializing
(...)

There was no longer a freeze when detecting the device. However, i restarted to see if it was fixed, and noticed the second time i powered on, the freeze appeared again.

Any help will be appreciated.

---

