---
title: "fastest way to clone disk"
date: 2010-05-01
forum: General Help
---

### Post by briandu on 2010-05-01
AMD 64   4CPU 8GB Ubuntu 9.10
2 SATA 1TB disks on 3Gb bus

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060aaf


I want to clone my 1 TB disk in the fastest manner.

I have used dd if=/dev/sdb of=/dev/sda  but it is too slow

After many hours I am to change to:
dd if=/dev/sdb of=/dev/sda bs=8225280

Does this make sense or should I increase it further to speed this up?

---

### Post by GSF1200S on 2010-05-01
> **briandu said:**
> AMD 64   4CPU 8GB Ubuntu 9.10
2 SATA 1TB disks on 3Gb bus

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00060aaf


I want to clone my 1 TB disk in the fastest manner.

I have used dd if=/dev/sdb of=/dev/sda  but it is too slow

After many hours I am to change to:
dd if=/dev/sdb of=/dev/sda bs=8225280

Does this make sense or should I increase it further to speed this up?

I would suggest taking a look at rsync.
```
sudo apt-get install rsync
```

Im not sure what you are cloning for: data backup I presume? Rsync does incremental transfer, meaning it only changes the parts of a file that have been changed since you last ran it. It is command line, but its very simple to use:
```
rsync -avh /directory/to/backup /location/to/backup/data/to
```
You can also have it sync a drive by appending --delete --recursive to that command, but be very careful (good idea to use --dry-run first to see what its going to do without actually doing it).

Im not sure if its the fastest, but it works great as a backup agent for me. It can even go over a network or ssh connection.

---

### Post by fyo on 2010-05-01
The problem with dd is that you're cloning the disk *in toto* -- even the empty parts. Since there are a few cases where empty doesn't mean empty, this can be handy, but in the vast majority of cases, it's unnecessary.

Try CloneZilla instead: [http://www.clonezilla.org/](http://www.clonezilla.org/)

---

