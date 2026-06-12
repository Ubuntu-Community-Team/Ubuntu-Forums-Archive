---
title: "Smart Media Card Reader"
date: 2010-06-25
forum: General Help
---

### Post by NM5TF on 2010-06-25
trying to get my Olympus MAUSB-10 Smart Media card reader to work under Ubuntu....I know the reader works as I just used it on Wifes'laptop under Win XP....

searched all forums & they all seem to think that Aluda(sp?) supports
this card reader, but it just won't work with Ubuntu at all....

running Lucid Lynx with latest kernel....

running lsusb shows that it sees the card reader...

any ideas???

Tom

---

### Post by NM5TF on 2010-06-25
here is some more info without the card installed in reader...the system seems to recognize the device, but it won't mount.....:confused:

tommy@tommy-desktop:~$ dmesg |tail
[  400.034158] usb-storage: device found at 4
[  400.034163] usb-storage: waiting for device to settle before scanning
[  400.097744] usbcore: registered new interface driver alauda
[  405.032133] usb-storage: device scan complete
[  405.032360] scsi 6:0:0:0: Direct-Access     Olympus  MAUSB-10 (Alauda 0102 PQ: 0 ANSI: 0 CCS
[  405.032473] scsi 6:0:0:1: Direct-Access     Olympus  MAUSB-10 (Alauda 0102 PQ: 0 ANSI: 0 CCS
[  405.037605] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  405.038189] sd 6:0:0:1: Attached scsi generic sg3 type 0
[  405.056463] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  405.061135] sd 6:0:0:1: [sdc] Attached SCSI removable disk

---

### Post by NM5TF on 2010-06-25
some more info with the card installed in reader....any ideas???:confused:

tommy@tommy-desktop:~$ dmesg | tail
[  862.487371]  [<c0142b80>] ? default_wake_function+0x0/0x20
[  862.487381]  [<f8263bed>] ? usb_stor_transparent_scsi_command+0xd/0x10 [usb_storage]
[  862.487392]  [<f8265d66>] ? usb_stor_control_thread+0x146/0x1f0 [usb_storage]
[  862.487403]  [<f8265c20>] ? usb_stor_control_thread+0x0/0x1f0 [usb_storage]
[  862.487412]  [<c01674b4>] ? kthread+0x74/0x80
[  862.487418]  [<c0167440>] ? kthread+0x0/0x80
[  862.487427]  [<c0104087>] ? kernel_thread_helper+0x7/0x10
[  862.487431] Code: 00 8b 7d e8 29 7d e0 0f 84 4a 01 00 00 66 83 45 d0 01 c7 45 c4 00 00 00 00 8b 8e f0 00 00 00 8b 7e 5c 0f b7 45 d0 31 d2 89 45 e4 <f7> 75 c8 89 c3 8b 07 8b 40 44 8d 04 c0 8d 04 81 8b 50 1c 8b 14 
[  862.487502] EIP: [<f824a58a>] alauda_read_data+0x13a/0x280 [ums_alauda] SS:ESP 0068:f691fe64
[  862.487516] ---[ end trace 86869136786a816c ]---

---

### Post by NM5TF on 2010-08-08
I never could get this card reader(Olympus MAUSB-10) to work under *nix, so I sold it on e-bay & got a cheap ($2.99) USB 2.0 card reader that works great!!!

---

