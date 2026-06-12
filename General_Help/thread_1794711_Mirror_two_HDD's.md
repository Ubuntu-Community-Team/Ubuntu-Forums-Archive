---
title: "Mirror two HDD's"
date: 2011-07-01
forum: General Help
---

### Post by Beatboxx on 2011-07-01
I want to backup pretty much files to another HDD. I got dev/sda2, and dev/sdb. So I made a simple script:

```

!/bin/bash
rsync -a --delete /dev/sda2/ /dev/sdab/backup
```

Then chmod a+x it, and run it:

```


/home/bastiaan/backups/scripts/mirror.sh: line 1: !/bin/bash: No such file or directory
rsync: change_dir "/dev/sda2" failed: Not a directory (20)
rsync: change_dir#3 "/dev/sdab" failed: No such file or directory (2)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(633) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

```

How do I get this working?

---

### Post by dino99 on 2011-07-01
why not using deja-dup (watch synaptic)

[http://techie-buzz.com/foss/deja-dup-ubuntu-1.html](http://techie-buzz.com/foss/deja-dup-ubuntu-1.html)

---

### Post by collisionystm on 2011-07-01
You dont need to make it a script. Just run the rsync command as is.

---

### Post by Beatboxx on 2011-07-01
But then it still doesnt work. It backups, not syncs....

---

### Post by psusi on 2011-07-01
That is because the destination you are giving it is nonsense.  It wants a destination directory, so you need to mount the drive somewhere ( usually in /media ) and point it there.

---

### Post by collisionystm on 2011-07-01
You can set rsync to run in your crontab. You can make it run every few seconds, minutes, hours...etc.

If you want a true sync, you need RAID.

---

### Post by dino99 on 2011-07-01
so install raid if you need to mirror

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by Beatboxx on 2011-07-01
I want to have this working. I don't want raid, I just want to have this working...

---

### Post by collisionystm on 2011-07-01
Okay, well. Without Raid, you will want to use rsync and have it backup nightly or while the computer is not in use. Backing up files without a raid system while they are in use can cause corruption.

So if you dont want raid, put your rsync command into crontab and have it run at midnight or so.

---

### Post by jerome1232 on 2011-07-01
okay rsync doesn't work on block devices. You need to make rsync source a folder not a block device. You also need to make some exceptions that it doesn't copy (such as the destination).


Why not just use raid or lvm to get mirroring?

---

### Post by SeijiSensei on 2011-07-02
/dev/sdb refers to the entire drive.  You need to partition it and put a filesystem on it.  Then you can copy from /dev/sda1 to /dev/sdb1.

If you simply want to clone the entire drive /dev/sda to /dev/sdb, you can use dd

```
dd if=/dev/sda of=/dev/sdb
```

However the two drives have to be identical for this to work.  Otherwise partition /dev/sdb, create a filesystem with mke2fs, then use rsync as others have described.

---

### Post by Roasted on 2011-07-02
> **Beatboxx said:**
> I want to have this working. I don't want raid, I just want to have this working...

You'll have to excuse my short answer as I'm running out the door, but I'd like to offer you some insight. I used Ubuntu since early 2006 and ever since I had used multiple drives with an rsync script. It worked great and I had no issues with it, besides the occasional manual run of the script to make sure it was working. Once in a while, I had an issue I had to fix, but for the most part it ran great.

Recently I just took two drives across two different boxes and set up software raid with mdadm. I highly recommend this setup. It was relatively painless for me to set up.

Now I have:

4gb USB Flash Drive - OS for Ubuntu 11.04 (File Server)
500gb HDD - RAID 1 Mirror
500gb HDD - RAID 1 Mirror

250gb SATA HDD - OS for Windows 7 + Ubuntu 11.04 (Personal Desktop)
1TB HDD - RAID 1 Mirror
1TB HDD - RAID 1 Mirror

It's really not hard to set up. Why not give it a shot? If you want to use rsync, that's fine too. Just trying to offer some insight since I was a heavy rsync'er and now I'm a heavy software raid'er. :P

---

### Post by psusi on 2011-07-03
> **SeijiSensei said:**
> 
```
dd if=/dev/sda of=/dev/sdb
```

However the two drives have to be identical for this to work.  Otherwise partition /dev/sdb, create a filesystem with mke2fs, then use rsync as others have described.

And it wastes time copying free space, and preserves any fragmentation, and leaves you with two drives having the same UUIDs, which causes all kinds of problems.

---

