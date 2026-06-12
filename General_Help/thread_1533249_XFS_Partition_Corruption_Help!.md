---
title: "XFS Partition Corruption: Help!"
date: 2010-07-17
forum: General Help
---

### Post by markekeller on 2010-07-17
So as my OS is loading, I get a "cannot mount /home" error, and end up in a root terminal.

My /home is mounted as its own XFS partition, so I tried a xfs_check on it, and I got the following:

```
[COLOR="Red"]kellerboys[/COLOR] [COLOR="Blue"]~ #[/COLOR]xfs_check /dev/sda1
xfs_check: size check failed
cache_node_purge: refcount was 1, not zero (node=0x93206a0)
xfs_check: cannot read root inode (22)
cache_node_purge: refcount was 1, not zero (node=0x9320a08)
xfs_check: cannot read realtime bitmap inode (22)
xfs_check: size check failed
ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_check.  If you are unable to mount the filesystem, then use
the xfs_repair -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.

```

So I tried mounting it again, as directed, and got this:

```
[COLOR="Red"]kellerboys[/COLOR] [COLOR="Blue"]~ #[/COLOR]mount /dev/sda1
mount: Structure needs cleaning.
```

I don't want to destroy the log, because I can't really risk any further corruption: I've got some pretty important data in this partition.

What can I do?

---

### Post by markekeller on 2010-07-17
Anyone?

---

### Post by markekeller on 2010-07-19
Still got this problem . . . Thanks in advance to anyone who can help!

---

### Post by rubylaser on 2010-07-19
I had this happen to my media mdadm array last year.  What I did at the time was mount the partition with the -o ro,norecovery options to recover my data first. Then I ran xfs_repair -L to fix the problem.

This was my /etc/fstab during recovery
```
/dev/md0        /var/videos     auto    ro,norecovery 0 3
```

---

### Post by markekeller on 2010-07-20
Thanks, rubylaser.  I tried running [FONT="Monospace"]mount -o ro,norecovery[/FONT] on it, but I still get the "Structure needs cleaning" message.  Is running [FONT="Monospace"]xfs_repair -L[/FONT] my only option, now?  Do you remember if you lost any data when you tried it?  Is there some other way to safely recover the data beforehand?

If anyone else wants to chime in here, too, that'd be great.

---

### Post by markekeller on 2010-07-20
Also, does anyone know what data is at risk of being lost in the event of running [FONT="Monospace"]xfs_repair -L[/FONT]?  Is it just the most recent changes?  Or random data from anywhere on the disk?

I can handle the former, but if I could lose *anything*, I need some way to recover the data before repairing.

---

### Post by bodhi.zazen on 2010-07-20
> **markekeller said:**
> Also, does anyone know what data is at risk of being lost in the event of running [FONT=Monospace]xfs_repair -L[/FONT]?  Is it just the most recent changes?  Or random data from anywhere on the disk?

I can handle the former, but if I could lose *anything*, I need some way to recover the data before repairing.

Not that it helps you, but, moving forward, I had similar issues with XFS.

Since you can not access your data now you do not have anything to loose and much to recover.

I suggest you attempt to recover as much data as possible with testdisk / photorec 

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

After you have recovered as much as possible, you can make a raw image of the partition with dd or similar tool. You can then restore the raw image if necessary.

[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

At that point, try to restore the partition with the commands you have been given. Most likely you will loose recent data, but, in the past, I have lost the entire XFS partition (which is why I stopped using XFS).

Now I understand one can loose data with any file system, but, IMO, data loss seems more problematic on XFS.

---

### Post by rubylaser on 2010-07-20
You definitely want to backup before you do anything.  In my case I only lost 2 of my most recent changes, everything else was intact.  But, your mileage may vary, so backup first.

---

