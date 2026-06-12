---
title: "Write privileges disappear on fat32 mount"
date: 2010-02-07
forum: General Help
---

### Post by rfmx49 on 2010-02-07
I am dual booting Xubuntu and XP, I have a small Fat32 partition that I use to access files from both operating systems, I am able to mount the drive and and able t write to it briefly but then if I try to write to it again I get a read-only file system error.

Output after umounting and mounting using "sudo mount -a"

```


jason@pc:~$ cd /mnt/shared
jason@pc:/mnt/shared$ mkdir a
jason@pc:/mnt/shared$ mkdir b
mkdir: cannot create directory `b': Read-only file system
```

I was able to write to it for a short while but then not even 30 seconds later I lost write privileges.

My fstab entry

```
/dev/sda3     	/mnt/shared     vfat    defaults,user,umask=000     	0       0
```

have tried and unknown amount of fstab entries the one above has best so far but i lose write privileges.

I noticed in other threads where people had similar issues they posted the results of "ls -l" of the mount point. So here it is.

```
drwxrwxrwx 13 root root 4096 1969-12-31 19:00 shared
```

---

