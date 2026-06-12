---
title: "'tune2fs -c 50' alternative for vfat (avoiding dosfsck at each boot)"
date: 2009-06-28
forum: General Help
---

### Post by manolo_asdf on 2009-06-28
hi,

I want to increase the boot-check occurrence for letting run dosfsck (currently it runs each boot, which takes very long). For ext4/ext3 I use the tune2fs -c xxx approach but tune2fs won't work for vfat partitions. 

So what is the equivalent of increasing check of mount time for vfat partitions? 

Disabling it forever ([http://ubuntuforums.org/showthread.php?t=225280](http://ubuntuforums.org/showthread.php?t=225280)) is a bit too much for me because I want to run the fs-check occasionally.

thanks.

---

### Post by geirha on 2009-06-28
FAT doesn't store the number of times it has been mounted, and the time since last check, like ext3/4, so as far as I know, there's no way to "tune" it. 

I guess you could hack your way around it though. Perhaps something like the following:

In /etc/default/rcS you can add the line:
```
FSCKTYPES="ext2,ext3"
```
to only have it run checks on ext2 and ext3 filesystems. Further, set that value depending on the existance of another file, maybe "/checkvfat"
```
[ -f /checkvfat ] && FSCKTYPE="ext2,ext3,vfat" || FSCKTYPE="ext2,ext3"
```
You'll need to make sure /checkvfat is removed after it has been handled. The best place for that is probably /etc/init.d/checkfs.sh. Find the line near the end that removes /fastboot and /forcefsck, and have it also remove /checkvfat
```
    rm -f /fastboot /forcefsck /checkvfat
```

Now, lastly, make a cronjob that creates the /checkvfat file once in a while. Weekly perhaps?

If so, create the following script: /etc/cron.weekly/checkvfat
```
#!/bin/sh
touch /checkvfat

```

Haven't tested this myself, it's just an idea I came up with just now... There might be a better way to do it that I'm just not seeing.

---

### Post by manolo_asdf on 2009-06-28
thanks for the hints!

I'll see whether this workaround is worth it (makes system configuration more complicated) or if I just remove the automatic switch for my vfat partition and run dosfsck once a while (once a month or so).

vfat partition anyway is seldom used, just for integration issues with my windows system.

---

