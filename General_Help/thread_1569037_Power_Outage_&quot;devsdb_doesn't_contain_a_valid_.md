---
title: "Power Outage: &quot;/dev/sdb doesn't contain a valid partition table&quot; (ext4)"
date: 2010-09-06
forum: General Help
---

### Post by pneumatic on 2010-09-06
The message is what is produced by fdisk -l.

Does anyone know the best way to recover this?  

Also, for basic storage (2TB), does anyone know a more stable file system?  This happened during a power outage and ext4 doesn't seem real durable in this respect.

---

### Post by sgosnell on 2010-09-06
Are you indeed booting from sdb and not sda?  Ext4 is a journaling filesystem, and more robust than most other filesystems.  If the partition table is really whacked, you should be able to restore it and get your files back from the journal.

---

### Post by pneumatic on 2010-09-06
I'm not interested in booting.  This is just for storing ripped DVDs (which I'd prefer not to re-rip).  I just want the data and file structure.

I used testdisk to restore the partition but there are no files/folders.  Is there any hope?

---

### Post by sgosnell on 2010-09-06
Hard to say.  Exactly what did testdisk give you?  Did it recognize the partition correctly, and set the correct filesystem type?  Did you reboot afterwards?

---

### Post by Zill on 2010-09-06
> **pneumatic said:**
> ...Also, for basic storage (2TB), does anyone know a more stable file system?  This happened during a power outage and ext4 doesn't seem real durable in this respect.
After experiencing a few outages trashing my disks I came to the conclusion that Ext3 wasn't really very robust. I moved over to reiserfs on all our PCs and have never regretted it - after a power outage it "just works", with no cryptic error messages or mysterious "lost and found" files. :-)

I know that the personal problems with Hans Reiser mean that development has stalled and no doubt there are many who always want the latest and greatest filesystem.  However, reiserfs is, IMHO, simply an excellent ultra-reliable filesystem and that is all *I* want. ;-)

---

### Post by mcduck on 2010-09-06
Since it's the *partition table* that's broken, the filesystem used on the actual partitions is irrelevant to your problem. Ext4 isn't your problem here.

Even more so when the error message complains about /dev/sdb (the whole disk) instead of your ext4 partition (/dev/sdb1, if it's the only partition on that disk)

---

### Post by srs5694 on 2010-09-06
An important point: The partition table and the filesystem are two *very* different things.

A disk's partition table defines the start and end points of partitions, along with other related partition meta-data, such as partition type codes, special flags, etc. On most Linux disks, the Master Boot Record (MBR), aka the MS-DOS, partitioning system is used. MBR supports for primary partitions, one of which may be an extended partition that can hold an arbitrary number of logical partitions. Other partitioning systems, such as the GUID Partition Table (GPT) and the Apple Partition Map (APM), also exist, and some Linux systems use these systems. Except for the partition type code, which identifies which OSes should try to access which partitions, the partition table holds no filesystem data. The error message reported in the first post relates to the partition table, and indicates that the partition table is damaged. The filesystem(s) on the (lost) partition(s) might or might not be damaged, based on that original error message.

A filesystem, OTOH, is a much larger and more complex data structure than a partition table. Filesystems generally reside inside partitions -- that is, on a restricted range of sectors on the disk. They hold files, subdirectories, and related data. Sometimes a filesystem occupies an entire disk. This is most common with floppies, optical discs, and some types of removable disks; hard disks are almost always partitioned, and the partitions hold the filesystems.

A filesystem may be damaged without damage to a partition table, and vice-versa -- although if the partition table is damaged, it may be impossible to locate the filesystem without re-creating the partition table (that's your current problem, pneumatic). Since the reported problem was related to partition table damage, changing to another filesystem is unlikely to improve reliability, at least against the sort of problem that occurred. GPT is more reliable than MBR, though, at least in theory -- GPT includes two copies of its critical data structures, and it includes checksums to help OSes and utilities spot corruption. Thus, if you're interested in improving disk reliability, switching to GPT may make sense. You can also store a backup of your partition table to simplify recovery should a problem occur.

Ext4fs is still a pretty new filesystem, and contrary to what sgosnell wrote, I still see occasional problem reports with it. OTOH, this is anecdotal evidence. I don't know of any scientific studies of the reliability of different Linux filesystems. Based on the anecdotal evidence I've seen and my own limited experience, I'd recommend ext3fs or XFS for best reliability. Ext3fs is good for filesystems that hold small- and mid-sized files, whereas XFS is better for big files, such as the audio-visual files you're storing, pneumatic.

I recommend you post the output of "sudo fdisk -l /dev/sdb" on the testdisk-recovered disk, pneumatic, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. You might also post the output of "df -h /mount/point", where "/mount/point" is wherever the partition is mounted. This will show us what testdisk recovered and the size of the filesystem. It's conceivable that testdisk found remnants of an old partition, and that the current partition is still intact, but that it starts somewhere else on the disk. If so, it may be recoverable, but you'll either need to have testdisk search more or you'll have to guess about its location on the disk.

---

