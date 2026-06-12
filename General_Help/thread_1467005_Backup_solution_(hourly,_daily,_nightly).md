---
title: "Backup solution (hourly, daily, nightly)"
date: 2010-04-30
forum: General Help
---

### Post by narsaw on 2010-04-30
At work on our Redhat based systems out IT department has setup a backup system that I was to emulate at home.

In each directory (or specified directories) in the file system there is a .snapshot (notice the .) directory that stores snapshots of the items in that directory taken a specified intervals (hourly.0,2,3, etc) an ls -al or the .snapshot looks like.

```

% ls -al .snapshot/
total 148
drwxrwxrwx  10 root    wheel     4096 2010-04-30 08:00 .
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 ..
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 dfm_sv_backup(users-snap09)SV0.0
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 hourly.0
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 hourly.1
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 hourly.2
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 hourly.3
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 nightly.0
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 nightly.1
drwxrwxrwx  22 jillr users 16384 2010-04-22 15:22 weekly.0

```

How are they doing this and can it be done on Ubuntu.

I have used rsnapshot in the past, but that puts these snapshots (hourly, daily, weekly, etc) in a specified location.

I want to put it in the same directory under a dot snapshot (.snapshot) directory.

Thanks

---

### Post by ronnyma on 2010-12-31
My guess is that you want to check this out:

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)


Cheers,

RM

---

