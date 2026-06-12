---
title: "Dual Boot Problems"
date: 2009-11-12
forum: General Help
---

### Post by gus_zernial on 2009-11-12
I have a Kubuntu 9.04 system with a custom 2.6.28.9 kernel.
Kubuntu is on two disks in software RAID, and I have a WinXP
install on a partition on one of the disks.

When I start Kubuntu it mounts the WinXP partition so I can
access it from linux.

The problem is that the WinXP partition periodically gets
hosed, and I can't figure out why. The result is the same
each time - the WinXP partition won't boot, but other 
symptoms are not always the same .... boot.ini lost, NTFS
file system corruption, GRUB boot issues ....

I can sometime fix the WinXP problem and sometimes not.
I've had to reinstall WinXP several times, a real PITA.

One idea I have is that mounting and accessing NTFS from 
linux is not reliable and may cause corruption, but I'm 
not sure. Anyone know why this might be (repeatedly)
happening????   

Thanks

---

### Post by Giblet5 on 2009-11-12
NTFS support is pretty stable on 9.04. That's not it.

Do you shut your system down by unplugging the computer? That would certainly do it. :)

Does anyone else have physical or network access to this system?

What kind of drive is XP on? SSD? Those are guaranteed to fail sooner than you ever thought possible.

Is XP on a software raid? Software raid is the short-path to data loss, btw. Google [agrees]("http://www.google.com/search?q=software+raid+sucks&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").

If you can't afford hardware RAID (a Real raid controller is pricey - that's how you can tell), use straight SCSI or IDE. Otherwise you WILL regret it eventually.

---

