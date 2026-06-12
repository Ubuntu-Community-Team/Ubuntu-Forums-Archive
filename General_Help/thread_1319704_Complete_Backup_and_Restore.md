---
title: "Complete Backup and Restore"
date: 2009-11-08
forum: General Help
---

### Post by shoaibi on 2009-11-08
My Hard Disk Partitions:
```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda7     ext3     19G   12G  6.0G  67% /
/dev/sda6     ext2    2.3G  261M  2.0G  12% /tmp
/dev/sda2     ext2     89M   45M   40M  54% /boot
/dev/sda5 reiserfs    4.9G  614M  4.3G  13% /var
/dev/sda8     ext4    264G  133G  132G  51% /home

```

I am about to do some experimentation with this laptop. What i want is that somehow i should be able to take a snapshot of the current state of ubuntu install on my laptop and later restore it. This include all data, configurations, installations, etc....

I am looking for a tool that preferably should be cross platform and fast, should be able to clone all partitions on my system, and later create same partitioning scheme and restore data from an earlier image.

Any ideas?

---

### Post by sc30317 on 2009-11-08
You can create a hard drive with filezilla, a liveCD download.

It makes backups and restores them (like Norton Ghost) but its freeware

---

### Post by winotree on 2009-11-08
[http://clonezilla.org/](http://clonezilla.org/) will come up time and again as the application of choice in threads like this.

---

### Post by shoaibi on 2009-11-11
I have almost 150G data on 320G HD, rest if all Zeros, i zeroed out manually, so that if i go for a compression option it would be even less as it would ignore Zeroed out blocks.

which would be fastest? Sort them with respect to them time they will take.
1. a plan dd img
2. a big gzip image
3. filezilla
4. clonezilla

---

