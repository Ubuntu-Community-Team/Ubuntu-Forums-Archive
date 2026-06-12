---
title: "mount point changing with external HD"
date: 2010-03-26
forum: General Help
---

### Post by majoob on 2010-03-26
I have an external hard drive /dev/sdb1 mounted as /media/backup
(I labeled the HD partition as "backup" using GParted).

My eSATA external HD is always powered on.

I use rsync to perform nightly backups to /media/backup. 

My problem is, every couple of days to a week, the mount point name changes to "/media/backup_" (note the underscore) and my rsync script, which has "/media/backup" hard-coded, backs up to a new _folder_ named "/media/backup".

I need this backup to be reliable. Does anyone know how I can prevent the name of my mount point from changing?

---

### Post by TitanusEramius on 2010-03-27
Have you made a fstab line for the ext-hdd?
If yes, could you please post your entire fstab here?

If no, I think you need to consider it:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by majoob on 2010-03-27
> **TitanusEramius said:**
> Have you made a fstab line for the ext-hdd?
If yes, could you please post your entire fstab here?

If no, I think you need to consider it:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

No, I had not.

I just added my ext-hdd to fstab though. Would you mind checking it? Here it is:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=228d6ffc-c50e-425d-a768-fcb9c22d8383 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aa75b03b-5037-4b0b-b73b-0c1f017c89dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# Only one of these two HDD's are connected at a time, the other is off-site
# external HD physical label = "BACKUP A" should be on /dev/sdb1
UUID=f13cde43-eec0-40dc-8418-0f41fb549073 /dev/sdb1	/media/backup ext3	user,realtime,noexec	0	2
# external HD physical label = "BACKUP B" should be on /dev/sdb1
# UUID=xxxxxxxxxxxxxxxx /dev/sdb1	/media/backup ext3	user,realtime,noexec	0	2
```

---

### Post by TitanusEramius on 2010-03-27
Sure thing majoob

It is very close to be right. When you use UUID you don't have to use /dev/*** as well, so the line should look like this instead:
```
UUID=f13cde43-eec0-40dc-8418-0f41fb549073 /media/backup ext3 user,realtime,noexec 0 2
```If you don't already have made the folder /media/backup you have to make it before mounting the disk. And you can very easy check if the line in fstab works by using the mount command in a terminal. First use "umount -a", then edit/change fstab and then use "mount -a" to see if Ubuntu mounts the disk correct.

In my opinion UUID is better to use than /dev/*** because the harddisk always will be recognize and mounted correct.

Good luck :)

---

### Post by majoob on 2010-03-27
Thanks, that worked. 
I did have to remove the "realtime" option. According to dmesg | tail it isn't compatible with the ext3 file system.

---

### Post by TitanusEramius on 2010-03-28
I'm very glad to hear :)
And I am sorry about realtime, the reason it is not working is because it's spelled wrong, but I didn't noticed before you said it didn't work... It's spelled "relatime".

(This is from [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/))
"Another approach was added in 2.6.20: the relatime mount option.  If this flag is set, access times are only updated if they are (before the update) earlier than the modification time.  This change allows utilities to see if the current version of a file has been read, but still cuts down significantly on atime updates.  This option is not heavily used, perhaps because few people have heard of it and many distributions lack a version of mount which is new enough to know about it.  Using relatime can still confuse tools which want to ask questions like "has this file been accessed in the last week?""

---

### Post by majoob on 2010-03-28
Ok, easy fix. Thanks for catching that!

---

### Post by geologic on 2010-05-08
Figure I'll piggy back onto this thread instead of starting a new one.

Having the exact same problem, as far as the whole /media/mountpoint_ with the addition of the underscore.

I realize I can manually set this in fstab. However, curiosity has me wondering how this can be fixed using the current mount system (is it devicekit/udev? I guess HAL was removed in 10.04).

If someone could point me to how/where to set the mount point with the current automount system, that would be great.
Thx

---

