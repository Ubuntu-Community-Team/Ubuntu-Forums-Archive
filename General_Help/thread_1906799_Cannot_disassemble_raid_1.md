---
title: "Cannot disassemble raid 1"
date: 2012-01-10
forum: General Help
---

### Post by jeliocranch on 2012-01-10
I'm at the end of my rope.

installed Server 11.10 on soft raid 1, then numerous problems booting first in degraded mode, then not at all.  Try to reinstall, the whole array is gone.  Booting to a live cd, both drives are present, showing they are intended for linux raid

fdisk to delete partitions and make new DOS partition table, go to reinstall server, it still see's raid on sata devices.
Try again with live cd, this time dd if=/dev/zero of=/dev/sdx bs=446 count=1 to over-write MBR for both disks.
RE-install again, Server still see's raid device.  back to live CD, dd overwrite more than just MBR.  fdisk -l shows no valid partition table.
try to re-install server again, still see's raid device.  I select don't activate, partitioner see's the drives individually.  This time, I install to just one drive, mounting the other as /backup.  install grub to drive with active partition.  no boot the first time.  Second time, it says cannot mount md4, drops to intramfs shell.
HOW CAN I UNDO THE RAIDNESS?
Why/how do fresh installs of server after reformatting drive and repartitioning them several times still see raid.  What switch?  Please help!

---

### Post by jeliocranch on 2012-01-10
from initramfs, I can cat /proc/mdstat where I see a raid md4, set to inactive.  think I remember seeing commands to remove raid.

---

### Post by dcstar on 2012-01-10
> **jeliocranch said:**
> 
........
HOW CAN I UNDO THE RAIDNESS?


Boot off Live CD, use **gparted** to write new Partition Tables to both disks.

---

### Post by jeliocranch on 2012-01-14
> **dcstar said:**
> Boot off Live CD, use **gparted** to write new Partition Tables to both disks.

I've done that.  Turns out, there was an artifact from an early attempt at raiding individual partitions.  It was on the swap partition, so I wiped it out and created a new one while in a live-environment, then updated the fstab with the new uuid.

worked a charm.

---

