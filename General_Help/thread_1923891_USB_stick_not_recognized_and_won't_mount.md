---
title: "USB stick not recognized and won't mount"
date: 2012-02-11
forum: General Help
---

### Post by polig4e on 2012-02-11
I'm trying to format a USB stick that got messed up somehow.

I created a Windows 7 Bootable USB stick of it, which initally worked and started Windows 7. I tried to recover another machine, which didn't work, and in the process the USB somehow got messed up - it wasn't a bootable USB anymore, and wouldn't get recognized as a USB storage device by any OS (Windows, Mac OS, neither Ubuntu).

From dmesg, when I remove/attach it, I get:

[  191.215957] usb 1-2: USB disconnect, device number 4
[  192.924124] usb 1-2: new high speed USB device number 5 using ehci_hcd
[  193.061822] usb 1-2: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[  193.071015] scsi5 : usb-storage 1-2:1.0
[  194.069287] scsi 5:0:0:0: Enclosure                                        PQ: 6 ANSI: 7
[  194.096537] scsi 5:0:0:0: Attached scsi generic sg2 type 13
[  194.097487] scsi 5:0:0:0: Failed to get diagnostic page 0x8000002
[  194.097497] scsi 5:0:0:0: Failed to bind enclosure -19

As you can imagine the device is not viewable from Disk Utility at all... if I get it there, I would format it easily :)

Apparently it is mapped to /dev/sg2 , but not to /dev/sdaN or /dev/sdbN (sda3 or sdb4, for example) but I don't know how to mount or how to format that. Any ideas?

Thank you,
Anton

---

### Post by P_Squiddy on 2012-04-02
Well, given that you've been booting Windows 7 on it, there's obviously nothing of value on there...  ;)

Seriously, though, if it is actually mapping to a /dev/sg2, have you tried forcing it to mount somewhere?  (i.e. mount /dev/sg2 /mnt/usbdrive)

If you can mount it and see the contents, the next step may be to use the disk utility to reformat the drive entirely.  Failing that, if you can't see what's on the drive, a simpler mkfs.vfat /dev/sg2 might do the trick!

---

