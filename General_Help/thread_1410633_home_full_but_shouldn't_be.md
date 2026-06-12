---
title: "/home full but shouldn't be"
date: 2010-02-19
forum: General Help
---

### Post by @B6Mwu8fN9M on 2010-02-19
I just got an error from Nautilus that my /home folder is full. On the partition there is still ~15 GB free. 

Here's my output for df -H
```

vlad@vlad-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              270G   255G   753M 100% /
udev                   1.6G   291k   1.6G   1% /dev
none                   1.6G   1.1M   1.6G   1% /dev/shm
none                   1.6G   369k   1.6G   1% /var/run
none                   1.6G      0   1.6G   0% /var/lock
none                   1.6G      0   1.6G   0% /lib/init/rw
/dev/sda2               42G    24G    18G  58% /media/328471178470DF33


```

The available space on / isn't the Size-Used. I don't know what that is.

I'm currently using Ubuntu 9.10 with all updates installed (kernel 2.61.31-19)

I did find [http://ubuntuforums.org/showthread.php?t=1402664](http://ubuntuforums.org/showthread.php?t=1402664) but I don't think that's the same problem. 

Thanks in advance!

---

### Post by darolu on 2010-02-19
I don't see your /home listed there? that's weird; what's in your fstab file?

---

### Post by @B6Mwu8fN9M on 2010-02-19
It's probably not there because it's not on a separate partition from /. 

My fstab (I added the last part about the cdrom but the rest is by default)

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=74609cf7-7aaa-4930-aa7c-dcd5e2d5fedb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=a848e5c2-8563-4c00-88d9-10e2e4c85301 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by dcstar on 2010-02-19
> **vlad003 said:**
> I just got an error from Nautilus that my /home folder is full. On the partition there is still ~15 GB free. 

Here's my output for df -H
```

vlad@vlad-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
**/dev/sda1              270G   255G   753M 100% /**
udev                   1.6G   291k   1.6G   1% /dev
none                   1.6G   1.1M   1.6G   1% /dev/shm
none                   1.6G   369k   1.6G   1% /var/run
none                   1.6G      0   1.6G   0% /var/lock
none                   1.6G      0   1.6G   0% /lib/init/rw
/dev/sda2               42G    24G    18G  58% /media/328471178470DF33


```


You have a full root partition and your /home folder is in your root partition, get rid of some files.

---

### Post by rnerwein on 2010-02-19
hi
those 15 GB you asumed to be free are the 5% reservation on creating a filesystem by default.
use the command ( as root ) tune2fs to see the truely layout of your partition ( man tune2fs ).
you can change this value and set it down ( e.g. 1% ) but don't set it to zero. give the system daemons a change to write emergency messages befor a disaster happens.
ciao

look at /var/log or in your home folder and try to get rid of huge files ( use the find command: man find )

---

### Post by @B6Mwu8fN9M on 2010-02-19
Thanks! I read about the reservation before but I didn't think that this is what it looks like. I guess I'll have to shrink my Windows partition. :popcorn:

---

