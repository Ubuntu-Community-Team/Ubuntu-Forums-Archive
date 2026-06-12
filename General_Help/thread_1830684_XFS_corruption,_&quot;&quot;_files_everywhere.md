---
title: "XFS corruption, &quot;??????????&quot; files everywhere"
date: 2011-08-22
forum: General Help
---

### Post by CrimsonRider on 2011-08-22
I've recently had an unexpected powerloss on my mail box. Now all seems to work well again, but when I remounted one of the volumes, it seems the filesystem got damaged.

One of the symptoms is files with unknown attribute are all around, like these

```

?????????? ? ?          ?               ?            ? bayes.lock.ruby.27568
?????????? ? ?          ?               ?            ? bayes.lock.ruby.27593
-rw-rw-rw- 1 rider      rider           0 Aug 19 09:47 bayes.lock.ruby.27596
?????????? ? ?          ?               ?            ? bayes.lock.ruby.27643
?????????? ? ?          ?               ?            ? bayes.lock.ruby.2807
?????????? ? ?          ?               ?            ? bayes.lock.ruby.2888
?????????? ? ?          ?               ?            ? bayes.lock.ruby.2944

```

Note that most of the files on the system are still intact.

Another symptom is that no longer the correct space free left on the device can be read. Sometimes it's a nice 300GB left, sometimes it reports as being 'unable to determine free space'

The filesystem is quite big, 2.2 TB with about 300GB free. It's based on a LVM group based on a RAID5 array. 

I've tried running xfs_repair, to no avail.
I've tried runnig xfs_check, but that ran out of memory.

Now, there isn't anything critical on this system, mostly spam filter, music and the like. But I would like to be able to restore it to functionality. Right now, I can't even delete the ?????? files.

Any suggestions?

---

### Post by blazemore on 2011-08-22
Sounds obvious, but have you tried running fsck?

---

### Post by fdrake on 2011-08-22
boot from a live cd and run

```
fsck /dev/<your linux partition>
or fsck -y /dev/<your linux partition>

```

---

