---
title: "Random reboots."
date: 2011-01-27
forum: General Help
---

### Post by schuelaw on 2011-01-27
Hi,

I installed 10.04 on 15 new dells last summer in my computer lab.  Ever since, users have reported random reboots while logged in and working (it's happened to me on at least two occasions).

These are fully patched 10.04 64-bit dell machines with the proprietary nvidia drivers.  It sounds crazy, but you'll be logged into the desktop (gnome, no substantial customizations), working along and the machine will simply shutdown and reboot--no warning.  I've searched log files and forums for any hint of what might be happening with no luck.

The only paltry clue I have is that this usually appears in the kernel log a few seconds before the reboot:

Jan 26 13:27:00 heaven kernel: [ 2119.621501] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Jan 26 13:27:00 heaven kernel: [ 2119.624212] SGI XFS Quota Management subsystem
Jan 26 13:27:00 heaven kernel: [ 2119.645230] JFS: nTxBlock = 8192, nTxLock = 65536
Jan 26 13:27:00 heaven kernel: [ 2119.695503] NTFS driver 2.1.29 [Flags: R/O MODULE].
Jan 26 13:27:01 heaven kernel: [ 2119.728029] QNX4 filesystem 0.2.3 registered.
Jan 26 13:27:01 heaven kernel: [ 2119.794883] Btrfs loaded

I'm not saying it's related, but it's all I've got.  

This has been going on since the lab was first set up in August.  Mostly I've been hoping that it would get patched away, but it happened yesterday while I was teaching, and it's somewhat embarrassing.  Any help?

Thanks,

Albert

---

### Post by tau-lepton on 2011-03-09
I just experienced this today, 10.10 64 bit on Dell Optiplex 360 (spare the jokes).  Have not looked at the logs yet.  Browser (Chrome 10 unstable) had focus, but probably unrelated.

---

### Post by Kirboosy on 2011-03-09
I would check the systems for "overheating" I know it sounds crazy but sometimes Ubuntu doesn't read the sensors right and reports over heating. This would cause the computers to shut down.



~Caboose

---

### Post by tau-lepton on 2011-03-09
Overheating is a possibility, The machine was very busy.  Unfortunately the sensors on the 360 are non-existent or proprietary (IIRC from a year ago).  I'll try underclocking.

---

### Post by JRV on 2011-03-09
Random reboots are usually caused by an inadequate or overheated power supply.

The power supply is often the weak link in all but the best store bought computers.
About two years ago I had to replace the power supplies in a number of Dell boxes.

---

