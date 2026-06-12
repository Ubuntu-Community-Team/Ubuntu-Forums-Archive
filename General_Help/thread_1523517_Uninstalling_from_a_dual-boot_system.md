---
title: "Uninstalling from a dual-boot system"
date: 2010-07-03
forum: General Help
---

### Post by neon401 on 2010-07-03
Hi
I want to uninstall Ubuntu from my machine, but I didn't find any direct instructions on how to do so.
I dual boot Windows 7 and Ubuntu 10.04 64-bit, with Windows 7 installed first.

Thanks

---

### Post by nautica17 on 2010-07-03
When you installed Ubuntu, did you make partitions manually or did you begin the installation within Windows? If it's the latter, then go to programs and features in Windows and find Ubuntu. Uninstall it and you should be set. :)

---

### Post by hansdown on 2010-07-03
Hi neon401.

Before you do that, download, and burn a gparted live cd.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

This will help restore your master boot record for windows.

Boot from an ubuntu live disk, and choose "try ubuntu without changes to your computer".

Click system> administration> gparted.

You can reformat the partition with ubuntu on it, to ntsf.

Close ubuntu, and remove the ubuntu disk.

Boot the gparted disk, and choose mbr and windows.

It will find your windows partition, and install the master boot record.

---

### Post by neon401 on 2010-07-03
> **hansdown said:**
> Hi neon401.

Before you do that, download, and burn a gparted live cd.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

This will help restore your master boot record for windows.

Boot from an ubuntu live disk, and choose "try ubuntu without changes to your computer".

Click system> administration> gparted.

You can reformat the partition with ubuntu on it, to ntsf.

Close ubuntu, and remove the ubuntu disk.

Boot the gparted disk, and choose mbr and windows.

It will find your windows partition, and install the master boot record.
Thanks a lot. I managed to solve some problems that were initially keeping me away from Ubuntu, so I decided against uninstalling for now.

Either way, your instructions will come in handy for later occasions.

---

### Post by hansdown on 2010-07-03
Glad you're sticking around neon401.

---

