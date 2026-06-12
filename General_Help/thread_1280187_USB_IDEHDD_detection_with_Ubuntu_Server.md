---
title: "USB IDEHDD detection with Ubuntu Server"
date: 2009-10-01
forum: General Help
---

### Post by vuco on 2009-10-01
Hello all,

Sorry if it is a newby question.
My system:
Ubuntu Jaunty 32bits running on 64bits platform.
kernel: "2.6.28-15-server #52-Ubuntu SMP"

The problem:
Cannot detect an USB IDE HDD.

The symptons:
After booting, I connect the USB HDD. Not a single new line
at dmesg. Doing cat /proc/partitions shows no new drive. No
device detected at lsusb.
Then I disconnect the USB HDD and reconnect again. This is shown
at dmesg:

[  115.808011] usb 1-2: new high speed USB device using ehci_hcd and address 2
[  115.942600] usb 1-2: configuration #1 chosen from 1 choice
[  115.943761] scsi4 : SCSI emulation for USB Mass Storage devices
[  115.944352] usb-storage: device found at 2
[  115.944354] usb-storage: waiting for device to settle before scanning
[  120.944171] usb-storage: device scan complete
[  120.944798] scsi 4:0:0:0: Direct-Access     ST312002 2A                    PQ: 0 ANSI: 2 CCS
[  120.946041] sd 4:0:0:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[  120.946784] sd 4:0:0:0: [sdb] Write Protect is off
[  120.946786] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  120.946789] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  120.947529] sd 4:0:0:0: [sdb] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[  120.948303] sd 4:0:0:0: [sdb] Write Protect is off
[  120.948306] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  120.948309] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  120.948376]  sdb: sdb1
[  120.973118] sd 4:0:0:0: [sdb] Attached SCSI disk
[  120.973171] sd 4:0:0:0: Attached scsi generic sg2 type 0

/proc/partitions is:
   8       16  117220824 sdb
   8       17  117218241 sdb1

lsusb shows:
Bus 001 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge


Then I disconnect the USB HDD and reconnect. It acts like the first 
attempt: not a single sign of detection. Disconnecting and reconnecting
again takes no effect, no matter the time I wait before a new try. From
this point on, I need to reboot. After rebooting, everything starts
over: the first attempt doesn't works, the second one detects the USB HDD
and the third and all subsequent attempts simply fails slently.

Now. If reboot with the "2.6.28-15-generic #52-Ubuntu SMP" kernel, I
can connect/disconnect the USB HDD freely and everything works just
fine.

Any ideas of what is going on here?

Thank you for your attention and Best Regards

Luis Otavio de Colla Furquim

---

### Post by Giblet5 on 2009-10-01
Odds are, there's a change (probably in the kconfig) that affects the usb driver in the second kernel, causing it to mysteriously work as intended.

I'd use the one that works. ;)

---

