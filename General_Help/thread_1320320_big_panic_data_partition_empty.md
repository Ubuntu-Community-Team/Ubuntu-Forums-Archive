---
title: "big panic: data partition empty"
date: 2009-11-09
forum: General Help
---

### Post by Ampi on 2009-11-09
I have a 500GB internal HD with an empty primary partition (FAT32) and the rest extended with Ubuntu, swap, home and data (data is over 400GB).
The data-partition is where I practically keep everything.

So yesterday I was watching a movie (from data partition), finished it, turned the computer off and went to sleep. Right now I'm turning the computer on and suddenly my desktop background dissappeared. Weird, because I don't remember moving the file. 
Apparently my data partition is empty and just 6.5 GB!!!

So I rebooted, automatic file check, nothing! Still 6.5 GB!

The only thing I did yesterday worth mentioning is installing conky and conky-colors, didn't work out like I wanted so I removed them again including their directories. After that I watched the movie (which is on the data partition).

All my documents are on the data partition, it couldn't have just dissappeared overnight?!

EDIT: In Gparted all the partition are present with the correct size and used space..

---

### Post by bchurchill on 2009-11-09
Maybe your partition isn't mounted?  That would be a common reason for something like this.  Please run the following commands so we can get a little feedback:

```

sudo fdisk -l
cat /etc/fstab
cat /etc/mtab

```

---

### Post by Ampi on 2009-11-09
Thanks for the very quick reply.

I thought it might have been that it isn't mounted. But isn't that strange if it's just one HD? Because it still reads the partition with a certain amount of memory and that´s it.

Anyway, good news. I turned the computer off again and waited 10 minutes. Turned it back on and now everything is okay again, luckily. Seeing everything in GParted did take the stress away a little :|.

But you reckon I can expect this again? 
Mounting is the only thing I can think of so I guess you're right, but I don't understand why. I've never seen it before.

---

### Post by bchurchill on 2009-11-09
I can't explain why this would happen either.  It sometimes comes up with external HDs that don't get mounted on boot, but idk why some partitions on one hard drive wouldn't be mounted.

The best way to protect youself from real problems in the future is backup!!!!  It's hard to get into the habit of it, but it's really worth it if you have files you like.  I use scripts to backup files that I've changed from one day to the next, and do weekly images of my data partition.  On a nearly-montly basis I backup everything.

I've had to recover only one or two times, but it's really worth all the work.

---

### Post by Ampi on 2009-11-09
Yes, I have been trying to convince myself to backup, but well, it takes time :)
Backup has to be on an external HD, right? Would make the most sence, I guess..
I read something about SBackup, suppose to be easy, I'll look into backup-methods..
Thanks, I think today might just be convincing enough to finally start backupping..

---

### Post by coffeecat on 2009-11-09
**Ampi**, I'm glad the data is there, but you might want to consider a different filesystem for that partition. The only real reason to use FAT32 is compatibility with Windows. Also, consider that FAT32 is a frail filesystem - no journalling - and if the filesystem gets corrupted you may lose your data irretrievably.

And yes. Backup, backup and backup. :)

---

### Post by Ampi on 2009-11-09
But my filesystem is an ext3, only the primary partition is Fat32, because I had Windows on it. 
But I'm planning on merging and having only Ubuntu.
Backup is a must, tonight or tomorrow night is the night! :)

---

### Post by Wim Sturkenboom on 2009-11-09
Next time it happens the first thing to check is the */etc/mtab* as indicated by bchurchill. It's possible that your partition was mounted but something else was mounted on the same mountpoint afterwards (e.g. a memory stick that you left in the PC).

---

### Post by Ampi on 2009-11-09
Okay, I will do so. Hopefully don't need to. Though I didn't have any usb sticks in before, during or after it 'broke'.
Nice signature ;)

---

### Post by Ampi on 2009-12-07
So, luckily I made an backup of all the important data on my computer, because the exact same problem happened last night, the problem being my /data partition being not mountd correctly. It reads as if it were only 2GB big with no data in it but GParted does see the 300GB /data partition, so I know it's there. And the problem hasn't been fixed yet.
So hear the output of cat /etc/mtab
```
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda7 /home ext3 rw,relatime 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/amparo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=amparo 0 0
/dev/sda8 /data ext3 rw,relatime 0 0
```
and the output of cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b94e32b7-2241-4066-8c4d-54e080aa53e0 /               ext3    relatime,errors=remount-ro 0       1
# /data was on /dev/sda8 during installation
UUID=ef776aca-ba31-4578-990b-acc197ded8e9 /data           ext3    relatime        0       2
# /home was on /dev/sda7 during installation
UUID=feadb57a-fa3a-41c1-8b8f-493562b148c1 /home           ext3    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=f426788a-4b57-4c15-9f78-e8f2e97e44a5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
I do hope once I do the clean install it will less of an issue. I don't want this to be a regular happening...

---

### Post by Ampi on 2009-12-07
Okay, next morning and the problem is solved. Again.

Could this have anything to do with my upgrade to 9.10 ??? I hear upgrading ain't that great..
Therefore I should learn how to make my own liveCD from the current installation I guess.. :(

---

### Post by Ampi on 2010-01-07
I haven't had the time to make a clean install, still planning. But now it happened again, the DATA partition is empty and small. Now I am not that scared anymore but I finally found the pattern :).
It happend when I install updated through the update manager that need a restart of the system. When I do the restart, that's when the DATA partition goes wrong. 
This weekend, clean install!

---

