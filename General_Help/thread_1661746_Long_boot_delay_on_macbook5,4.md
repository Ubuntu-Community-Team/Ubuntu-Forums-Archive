---
title: "Long boot delay on macbook5,4"
date: 2011-01-07
forum: General Help
---

### Post by bytbox on 2011-01-07
I'm running ubuntu on a macbook5,4, and I get a 30-second long pause during the boot sequence. (I have quiet turned off.) This shows up in dmesg as:

```
[    1.847208] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[    2.000059] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    2.239138] hub 4-1:1.0: USB hub found
[    2.242107] hub 4-1:1.0: 3 ports detected
[    2.590102] usb 3-5: new low speed USB device using ohci_hcd and address 2
[    2.672282] scsi 6:0:0:0: Direct-Access     APPLE    SD Card Reader   1.00 PQ: 0 ANSI: 0
[    2.672863] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.674243] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    3.160035] usb 3-6: new full speed USB device using ohci_hcd and address 3
[    3.492058] usb 4-1.1: new full speed USB device using ohci_hcd and address 3
[   34.373586] udev[417]: starting version 163
[   34.422599] lp: driver loaded but no devices found
[   34.503755] lib80211: common routines for IEEE802.11 drivers
[   34.503759] lib80211_crypt: registered algorithm 'NULL'
[   34.508256] wl: module license 'MIXED/Proprietary' taints kernel.
[   34.508260] Disabling lock debugging due to kernel taint

```

What could be causing this? And how can I get it to say what it's doing at that time or, better yet, just not take that long.

Details: 

Linux jagadai 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

Grub.

Dual boot with OS X 10.6.4 using rEFIt.

It shouldn't be at all relevant, but I'm using E17 on top of kdm.

---

### Post by dino99 on 2011-01-07
some links about your config:

[https://encrypted.google.com/search?hl=fr&lr=lang_en&tbs=qdr%3Ay%2Clr%3Alang_1en&q=grub2%2Brefit%2Bmacbook&btnG=Rechercher&aq=f&aqi=&aql=&oq=&gs_rfai=](https://encrypted.google.com/search?hl=fr&lr=lang_en&tbs=qdr%3Ay%2Clr%3Alang_1en&q=grub2%2Brefit%2Bmacbook&btnG=Rechercher&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by bytbox on 2011-01-07
Nothing here mentions boot delays. These are primarily concerned with how to set up ubuntu on a macbook and get it working properly, something I've already done.

Is there any way to increase the amount of kernel output past what you normally get with "quiet nosplash" in the grub config?

---

### Post by dino99 on 2011-01-07
sorry im not a mac user, and cant find anything else than settings into /etc/default/grub

[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/388135](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/388135)

---

