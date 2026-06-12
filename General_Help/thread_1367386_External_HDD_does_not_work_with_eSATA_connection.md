---
title: "External HDD does not work with eSATA connection"
date: 2009-12-29
forum: General Help
---

### Post by johann_p on 2009-12-29
I have Ubuntu 9.10 32 bit with all the latest updates (2.6.31-17-generic) and I want to attach a Seagate FreeAgent XTreme external HDD via eSATA. However, this does not seem to work :(

The HDD appears in the BIOS and after booting in /proc/scsi/scsi the drive shows up as scsi7 Channel 00 Id 01 Lun 00 as "Seagate FreeAgen" Rev: 4115.
However nothing is mounted or shown. When I run "sudo gparted" the message "Input/output error during read on /dev/sdd" is shown and dmesg shows a large number of messages like this:

sd 7:0:1:0: [sdd] Unhandled error code
sd 2:0:1:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DIRVER_OK
end_request: I/O error, dev sdd, sector 0

This is after I successfully formatted the HDD when it was attached with USB, which seems to work fine. 

This is quite frustrating as I would really need the additional speed of the eSATA connection.

A bit earlier in the dmesg log I found this, not sure if any or all of it is related:
```

[   57.367499] ppdev: user-space parallel port driver
[   57.860028] ata8: device not ready (errno=-16), forcing hardreset
[   57.860037] ata8: soft resetting link
[   63.188010] ata8: link is slow to respond, please be patient (ready=0)
[   67.912010] ata8: SRST failed (errno=-16)
[   67.912019] ata8: soft resetting link
[   73.188012] ata8: link is slow to respond, please be patient (ready=0)
[   77.916209] ata8: SRST failed (errno=-16)
[   77.916220] ata8: soft resetting link
[   83.233911] ata8: link is slow to respond, please be patient (ready=0)
[  112.968519] ata8: SRST failed (errno=-16)
[  112.968531] ata8: soft resetting link
[  117.996514] ata8: SRST failed (errno=-16)
[  117.996520] ata8: reset failed, giving up
[  117.996524] ata8.01: disabled
[  117.996542] ata8: EH complete
[  117.997585] sd 7:0:1:0: [sdd] Unhandled error code
[  117.997589] sd 7:0:1:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  117.997594] end_request: I/O error, dev sdd, sector 63
[  117.997599] Buffer I/O error on device sdd1, logical block 0

```

---

### Post by hemebond on 2010-02-09
I have the exact same kernel version and came home today to find I couldn't access my secondary SATA HDD. I found the messages you did in dmesg and after a reboot the HDD isn't there at all.

My SATA HDD is internal, connected directly to the mainboard, not on an external connection.

---

