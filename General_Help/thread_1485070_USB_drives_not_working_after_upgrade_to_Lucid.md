---
title: "USB drives not working after upgrade to Lucid"
date: 2010-05-16
forum: General Help
---

### Post by timgood on 2010-05-16
After upgrading my wife's machine from Karmic to Lucid 64bit, USB drives will not automount and do not show in Nautilus. If I lsusb the drive is shown. I have tried several things - installing hal, removing the legacy floppy in the BIOS, sudo modprobe -r floppy and rebooting but nothing works. Help on this would be greatly appreciated.

I have tried with several flash drives, all work and automount on my computer (a clean install of Lucid) but none will work on the upgraded machine.

---

### Post by timgood on 2010-05-16
tail -f /var/log/messages gives this on my machine:

May 16 17:33:48 tim-desktop kernel: [26698.761306] usb 1-7: new high speed USB device using ehci_hcd and address 8
May 16 17:33:48 tim-desktop kernel: [26698.912156] usb 1-7: configuration #1 chosen from 1 choice
May 16 17:33:48 tim-desktop kernel: [26698.915810] scsi8 : SCSI emulation for USB Mass Storage devices
May 16 17:33:53 tim-desktop kernel: [26703.913730] scsi 8:0:0:0: Direct-Access     JetFlash TS512MJF2A/120   0.00 PQ: 0 ANSI: 2
May 16 17:33:53 tim-desktop kernel: [26703.914767] sd 8:0:0:0: Attached scsi generic sg3 type 0
May 16 17:33:53 tim-desktop kernel: [26703.916600] sd 8:0:0:0: [sdc] 1024000 512-byte logical blocks: (524 MB/500 MiB)
May 16 17:33:53 tim-desktop kernel: [26703.917100] sd 8:0:0:0: [sdc] Write Protect is off
May 16 17:33:53 tim-desktop kernel: [26703.918611]  sdc: sdc1
May 16 17:33:53 tim-desktop kernel: [26703.997487] sd 8:0:0:0: [sdc] Attached SCSI removable disk

However, on my wife's machine I only get this:

May 16 17:33:48 vivien-desktop kernel: [26698.761306] usb 1-7: new high speed USB device using ehci_hcd and address 8
May 16 17:33:48 vivien-desktop kernel: [26698.912156] usb 1-7: configuration #1 chosen from 1 choice

Nothing more. Does this give us a clue?

---

### Post by timgood on 2010-05-16
*bump*

---

### Post by timgood on 2010-05-16
bump again

Any ideas? I would really like to get the machine working without a re-install.

---

### Post by timgood on 2010-05-17
I eventually solved this problem by uninstalling pmount, then re-installing together with libpmount0.0

Now drives are detected, automount and can be safely removed. No idea what caused the problem on the upgrade, but hope that this helps other people with the same problem.

---

### Post by mjs355 on 2010-05-31
I have the same problem but your solution did not work for me. I've tried some other things with no satisfaction.Any suggestions would be welcome.

---

### Post by elr140 on 2010-06-03
I also tried installing pmount and the library and that didn't fix my problem either.  Any ideas?  I upgraded through the synaptic package manager from 9.10 to 10.04

Thanks!

---

