---
title: "rsync / to flash"
date: 2011-01-16
forum: General Help
---

### Post by kacper on 2011-01-16
I made a initramfs image that mounts my flash drive as ro, copies and changes root to tmpfs. Then I made a shell script to run rsync to apply any changes in tmpfs to the flash drive. 

However after every reboot rsync insists in copying files that are the same in both location. For some reason rsync loves to copy files in /var/lib/apt/lists and /usr/share/local, to name a few, after every reboot. I doubt that all those files change during boot.

Am I doing something wrong with rsync or is it some kind of bug?

```
rsync -P -a -h –update –perms –owner –group –exclude=/sys/ –exclude=/proc/ –exclude=/mnt/ –exclude=/tmp/ –exclude=/var/tmp/ –exclude=/var/cache/ –exclude=/var/run/ –exclude=/etc/network/run/ –delete / /mnt/flash
```

The rsync log: [http://pastebin.com/9zg4Cv7V](http://pastebin.com/9zg4Cv7V)

---

### Post by kacper on 2011-01-16
I figured it out. The init script in initramfs wasn't preserving timestamps when issuing cp.

---

