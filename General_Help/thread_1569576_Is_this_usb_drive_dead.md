---
title: "Is this usb drive dead?"
date: 2010-09-06
forum: General Help
---

### Post by lorderico on 2010-09-06
Hello,

My friend gave me a usb drive which doesn't mount.  When I plugged it in, I got this on dmesg:

[17550.051368] hub 2-0:1.0: unable to enumerate USB device on port 1
[17551.940102] usb 2-1: new high speed USB device using ehci_hcd and address 55
[17552.095170] usb 2-1: configuration #1 chosen from 1 choice
[17552.103912] scsi46 : SCSI emulation for USB Mass Storage devices
[17552.104204] usb-storage: device found at 55
[17552.104209] usb-storage: waiting for device to settle before scanning
[17557.101649] usb-storage: device scan complete
[17557.102719] scsi 46:0:0:0: Direct-Access              USB MEMORY BAR   1000 PQ: 0 ANSI: 0 CCS
[17557.107982] sd 46:0:0:0: Attached scsi generic sg2 type 0
[17557.108932] sd 46:0:0:0: [sdb] Attached SCSI removable disk

The usb drive is supposed to be on /dev/sdb, however when I try to read /dev/sdb with head, I get:

head: cannot open `/dev/sdb' for reading: No medium found

I cannot get it to work with fdisk, gparted, mount, and all I can get is No medium found.  I am ready to call this drive dead.  What do you think?

Thanks,
Eric

---

### Post by bodhi.zazen on 2010-09-07
Sounds dead. You can try it on another OS and see what happens.

---

