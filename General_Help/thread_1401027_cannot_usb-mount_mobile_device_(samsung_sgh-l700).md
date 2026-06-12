---
title: "cannot usb-mount mobile device (samsung sgh-l700)"
date: 2010-02-07
forum: General Help
---

### Post by manolo_asdf on 2010-02-07
hi,

cannot mount external-drive to my linux ubuntu 9.10, and wonder why...

i cannot mount it by using 'mount /dev/sdb'. itself linux seems to be notice it: 

```

Feb  7 22:07:21 manolo kernel: [ 3144.800060] usb 3-2: new full speed USB device using uhci_hcd and address 7
Feb  7 22:07:22 manolo kernel: [ 3144.976244] usb 3-2: configuration #3 chosen from 1 choice
Feb  7 22:07:22 manolo kernel: [ 3144.993264] cdc_acm 3-2:3.1: ttyACM0: USB ACM device
Feb  7 22:07:22 manolo kernel: [ 3145.304123] usb 3-2: USB disconnect, address 7
Feb  7 22:07:23 manolo kernel: [ 3146.788061] usb 3-2: new full speed USB device using uhci_hcd and address 8
Feb  7 22:07:24 manolo kernel: [ 3146.962249] usb 3-2: configuration #2 chosen from 1 choice
Feb  7 22:07:24 manolo kernel: [ 3146.972617] scsi4 : SCSI emulation for USB Mass Storage devices
Feb  7 22:07:29 manolo kernel: [ 3151.981114] scsi 4:0:0:0: Direct-Access     Nexperia Dev. 0 LUN 0     1.25 PQ: 0 ANSI: 0
Feb  7 22:07:29 manolo kernel: [ 3151.982074] sd 4:0:0:0: Attached scsi generic sg1 type 0
Feb  7 22:07:29 manolo kernel: [ 3151.999098] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```

are there some specialities with mobile devices connecting through usb? i am having a samsung SGH-L700.

thanks.

---

### Post by zvacet on 2010-02-07
Try install pysdm (it is in synaptic) and run in terminal

```
gksudo pysdm
```

Maybe that will help you.

---

