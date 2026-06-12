---
title: "Can Only Mount FAT32 Drive as Read Only"
date: 2006-06-01
forum: General Help
---

### Post by TheFifth on 2006-06-01
Hi All,

I've got an odd problem!  I rebooted my machine earlier today and now for some reason my Windows FAT32 drive is only showing as read only.  The fstab entry for the partition is:

```
/dev/hdb1	/mnt/data	vfat	defaults,auto,uid=1000,gid=1000 0 0
```

I haven't changed anything in fstab for months and it's been fine, also I use the same code on my laptop running Dapper and it allows me RW access to FAT drives on that machine.

It was working fine this morning, I downloaded the overnight updates using Synaptic, re-booted, and now I can't write to the FAT32 drive.

Any ideas?  I'm stuck!

---

### Post by frodon on 2006-06-01
Try add this option : ```
/dev/hdb1	/mnt/data	vfat	defaults,auto,**umask=000**,uid=1000,gid=1000 0 0
```
Then unmount the partition and run a : ```
sudo mount -a
```

---

### Post by TheFifth on 2006-06-04
I worked out what it was.  The drive had somehow developed a lot of errors!  I booted to windows and did a scan disk and it found a load of bad allocation units etc.  I can now read and wrtie to it again in Linux.

The drive is mechanically sound and seems fine now.  I hope it was a power surge or something that effected the data and not Dapper somehow screwing up while writing to it!

I'll keep an eye on it and see what happens!

---

