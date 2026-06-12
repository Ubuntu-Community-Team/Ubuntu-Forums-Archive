---
title: "recover data from an external drive, need help"
date: 2010-01-19
forum: General Help
---

### Post by Netrunner on 2010-01-19
i'm trying to recover my old seagate 500gb hd

to understand where it is and mount it or use ddrescue i use

```
tail -f /var/log/messages
[  160.869237] sd 4:0:0:0: [sdb] Write Protect is off
[  160.872593]  sdb: sdb1
[  160.885411] sd 4:0:0:0: [sdb] Attached SCSI disk
[  183.762551] CE: hpet increasing min_delta_ns to 15000 nsec
[  359.770169] usb 2-2: new high speed USB device using ehci_hcd and address 5
[  359.922875] usb 2-2: configuration #1 chosen from 1 choice
[  359.937610] scsi5 : SCSI emulation for USB Mass Storage devices
[  364.942727] scsi 5:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[  364.943298] sd 5:0:0:0: Attached scsi generic sg3 type 0
[  364.955805] sd 5:0:0:0: [sdc] Attached SCSI disk

```

My guess is it's /dev/sdc/ am i right?
gparted testimage photorec can't see it when i plug it in.
and Palimpsest show an unrecognized 0,0 kb drive.

when i run 
#ddrescue -v /dev/sdc /media/suppo/image /media/suppo/log
it says there are no errors and make an image of 0kb

is it /dev/sdc or not?
how can i make the disk image?

---

### Post by Netrunner on 2010-01-19
[http://ubuntu-rescue-remix.org/node/168](http://ubuntu-rescue-remix.org/node/168)
i guess the problem is similar to that.

---

