---
title: "Continually repeating Kernel error"
date: 2010-03-28
forum: General Help
---

### Post by AVH on 2010-03-28
I have a kernel error that repeats itself every few seconds that Ubuntu is up. After a couple of hours my /var/log file is up to 625M. It doesn't seem to hurt anything, but I would like to know what's going on.

Here it is in my kernel log

```
Mar 28 09:33:12 livingroom-ubuntu kernel: [  818.341486] ata2.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
Mar 28 09:33:12 livingroom-ubuntu kernel: [  818.341499] ata2: hard resetting link
Mar 28 09:33:13 livingroom-ubuntu kernel: [  818.660082] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 28 09:33:13 livingroom-ubuntu kernel: [  818.684274] ata2.00: configured for UDMA/100
Mar 28 09:33:13 livingroom-ubuntu kernel: [  818.684741] ata2: EH complete
```

Here is its first appearance in dmseg. It repeats mixed in with other stuff untill the end of the log.

```
[    1.920011] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    1.968070] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.992256] ata2.00: configured for UDMA/100
[    1.992764] ata2: EH complete
[    1.993580] ata2.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
[    1.993653] ata2: hard resetting link
[    2.134763] usb 4-1: configuration #1 chosen from 1 choice
[    2.312070] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.336256] ata2.00: configured for UDMA/100
[    2.336928] ata2: EH complete
[    2.337787] ata2.00: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6
[    2.337859] ata2: hard resetting link
[    2.440010] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    2.656066] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.664570] usb 2-2: configuration #1 chosen from 1 choice
[    2.680257] ata2.00: configured for UDMA/100
[    2.680775] ata2: EH complete
[    2.683117] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
```

---

### Post by ShayWC on 2010-04-09
I got the same problem . 
Did you find anything on that???

---

### Post by AVH on 2010-04-14
No solution yet. Since sata 2 seems to be my dvd burner I wonder if this is related to the problems I'm having with Brasero and burning disks and also the fact that the disk tray won't stay open for more than a second.

---

### Post by chitowner2 on 2010-04-27
BUMP!

I have a similar issue on my box (9.10/kde 4.3):


Apr 27 13:53:18 kernel: [185178.011611] ata2: hard resetting link
Apr 27 13:53:25 kernel: [185184.570577] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 27 13:53:25 kernel: [185184.592991] ata2.00: configured for UDMA/133
Apr 27 13:53:25 kernel: [185184.593012] ata2: EH complete

I also suspect my optical drive may be involved. But it is plugged into a PCI card, not a mobo port.

CT

---

