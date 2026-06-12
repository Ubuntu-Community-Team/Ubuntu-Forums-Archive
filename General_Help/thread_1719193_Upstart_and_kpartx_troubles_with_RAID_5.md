---
title: "Upstart and kpartx troubles with RAID 5"
date: 2011-04-01
forum: General Help
---

### Post by BBUCommander on 2011-04-01
Hello,

I have an Intel Matrix RAID 5 disk with a couple data partitions.  I intend to mount both partitions on bootup via /etc/fstab - prior to loading my applications - and am having trouble.  Partitions on Intel RAID 5 must be mapped using kpartx, but Upstart only maps and mounts my Intel RAID 0 and RAID 1 disks.  Thus I assume that Upstart is not calling kpartx (or rather, if I understand how mounting works via Upstart, mountall does not call kpartx).

Currently I have resolved this by running a script (see attached) from /etc/rc.local which finds active RAID disks and maps them using kpartx.  This solution is ugly because it does not make use of /etc/fstab, boot applications complain about the missing partitions because rc.local is run too late in the boot process, and GNOME has the annoying habit of poppping up a window each script mounted partition in rc.local.

**My question**: How can I get this script to run on bootup using Upstart?

---

### Post by BBUCommander on 2011-04-02
You've got to bump the hump.

---

### Post by BBUCommander on 2011-10-22
In case anyone ever finds this thread and is in search for an answer, please see [bug #737027]("https://bugs.launchpad.net/ubuntu/+source/multipath-tools/+bug/737027") where I provide a detailed solution.

---

