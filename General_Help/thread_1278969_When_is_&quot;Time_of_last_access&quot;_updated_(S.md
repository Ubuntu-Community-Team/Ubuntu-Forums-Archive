---
title: "When is &quot;Time of last access&quot; updated? (ST_ATIME)"
date: 2009-09-30
forum: General Help
---

### Post by Krijk on 2009-09-30
When programming I want to use the Time of last access. When testing though it seems that it isn't always updated.

The code below gives the st_atime of a new file in Unixtime:

```
>>> created new file
1254310331
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310331, st_mtime=1254309770, st_ctime=1254310331)
>>> opened file for the 1th time -> st_atime is modified
1254310352
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310352, st_mtime=1254309770, st_ctime=1254310331)
>>> opened file for the 2nd time --> st_atime is not modified!
1254310352
posix.stat_result(st_mode=33188, st_ino=27525131L, st_dev=2069L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=13L, 
st_atime=1254310352, st_mtime=1254309770, st_ctime=1254310331)
```

When I open an existing file it is not modified. When I create a new file the st_atime is modified the 1th time it opens and afterwards it doesn't change.

Can anybody explain to me how this works?

---

### Post by Giblet5 on 2009-09-30
stat.st_atime is updated anytime the file is opened for read or write, unless that feature has been turned off during the filesystem mount (noatime option).

For obvious reasons, updating st_atime can eat a lot of I/O bandwidth, so this is often disabled to boost I/O performance.

The difference is significant, but disabling atime degrades security via audit...

Check the filesystem's options in /etc/fstab.

---

### Post by Krijk on 2009-09-30
> **Giblet5 said:**
> stat.st_atime is updated anytime the file is opened for read or write, unless that feature has been turned off during the filesystem mount (noatime option).

For obvious reasons, updating st_atime can eat a lot of I/O bandwidth, so this is often disabled to boost I/O performance.

The difference is significant, but disabling atime degrades security via audit...

Check the filesystem's options in /etc/fstab.

I've checked it, but noatime is not used when mounting. Also checked flushing the caches ( echo 2 > /proc/sys/vm/drop_caches
) , but that didn't work either.

PS also posted this in other forum:
[http://ubuntuforums.org/showthread.php?p=8030482#post8030482](http://ubuntuforums.org/showthread.php?p=8030482#post8030482)

---

### Post by Giblet5 on 2009-09-30
Interesting!

What's that filesystem's fstab entry?

I set relatime, myself. Here's an [interesting discussion]("http://kerneltrap.org/node/14148") that drove me to make that change.

I guess noatime is the default now?

---

