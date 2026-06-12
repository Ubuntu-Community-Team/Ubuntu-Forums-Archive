---
title: "DVD drive is stuck after some time"
date: 2010-04-28
forum: General Help
---

### Post by mbaitoff on 2010-04-28
When DVD is inserted in the drive, it mounts and is read perfectly. But after some time of inactivity disk and drive becomes "frozen". Any attempt to acces files on the disk leads to drive spin-up, and no response from the drive and disk for several minutes. "eject", "umount" and eject button for this drive in this situation fail. after some time of "spinned-up-frozen" the drive spins down. At this moment it is possible to eject the disk by drive button, close the tray (with the disk) back, and the disk is again mounted and read properly (until next period of inactivity). "dmesg" during the "freeze" time shows the repeated disk error messages:

> Apr 26 00:00:11 localhost kernel: [677228.729498] hda: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Apr 26 00:00:11 localhost kernel: [677228.729498] hda: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
Apr 26 00:00:11 localhost kernel: [677228.729498] ide: failed opcode was: unknown
Apr 26 00:00:11 localhost kernel: [677228.729898]   Error: Medium error -- (Sense key=0x03)
Apr 26 00:00:11 localhost kernel: [677228.729898]   "28 00 00 00 00 10 00 00 01 00 00 00 00 00 00 00 "
Apr 26 00:00:11 localhost kernel: [677228.729898] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
Apr 26 00:00:19 localhost kernel: [677237.830581] hda: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Apr 26 00:00:19 localhost kernel: [677237.830581] hda: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
Apr 26 00:00:19 localhost kernel: [677237.830581] ide: failed opcode was: unknown
Apr 26 00:00:19 localhost kernel: [677237.830581]   Error: Medium error -- (Sense key=0x03)
Apr 26 00:00:19 localhost kernel: [677237.830581]   "28 00 00 00 00 10 00 00 01 00 00 00 00 00 00 00 "


"dd" for this disk (at the moment of non-freeze) passes fine, copying all the data without problems, so disk quality is not the issue.

Please help me finding out the root of the problem.

---

### Post by ram2500 on 2010-04-28
It might be that either the disc is defective, or the lens is not clean. You can clean the lens if it isn't a burner; if it is a burner you have to find a cleaning kit safe for burner drives. I would also try to find a spare drive, if you have one, and swap it out.

---

### Post by mbaitoff on 2010-04-28
> **ram2500 said:**
> It might be that either the disc is defective, or the lens is not clean. You can clean the lens if it isn't a burner; if it is a burner you have to find a cleaning kit safe for burner drives. I would also try to find a spare drive, if you have one, and swap it out.

Disk is mounted perfectly once inserted in the drive. Disk is read perfectly. The disk is the Debian installation DVD, so when I boot it, and use the "DVD checksum" menu entry, it's checked fine. I think it's some kind of drive issue - either hardware or linux driver, because in Windows it works perfectly.

---

### Post by mbaitoff on 2010-05-03
So, did anyone encounter a "drive freeze" case in your practice?

---

### Post by bryanl on 2010-06-08
My gateway quad core will freeze when a DVD is inserted in most cases. Happens with both the internal drive as well as an external USB connected DVD drive. It seems to be media related.

---

