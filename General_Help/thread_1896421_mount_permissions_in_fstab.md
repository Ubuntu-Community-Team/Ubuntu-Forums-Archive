---
title: "mount permissions in fstab"
date: 2011-12-16
forum: General Help
---

### Post by psycho5 on 2011-12-16
I have an ntfs partition mounted in fstab since ubuntu installation, I know that the mount options allowed me to write to the partition, but lately, I can't write to the partition.

UUID=369AE9CD9AE98A27 /media/Media    ntfs    defaults,umask=007,gid=46 0       0

I know umask gives me full permissions, but then, the defaults options are rw, exec, auto, nouser, dev, suid, etc. 

that nouser option is bugging me, is that the reason why I can't write to it? 

Should i replace defaults with rw, exec, auto, **user**, dev, suid, async, ... etc?

---

### Post by mikewhatever on 2011-12-16
I suspect that you need to run a check on that partition in Windows. If a file system is unclean, Ubuntu will often remount it as read only (ro). The 'nouser' option doesn't really have anything to do with write permissions.

---

### Post by ajgreeny on 2011-12-16
It si also worth checking in both 11.04 and 11.10 that you have ntfs-3g installed, and that you let that mount the partition.  It should then mount with full read write permissions without you doing anything else, I believe, but I don't have any ntfs partitions to check that out.

---

### Post by psycho5 on 2011-12-17
Uh oh, i feel that the disk might have bad sectors, could that be the reason of unable to write to it? I still haven't scanned it though..

---

