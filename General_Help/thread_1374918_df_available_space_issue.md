---
title: "df available space issue"
date: 2010-01-07
forum: General Help
---

### Post by nicoseb on 2010-01-07
I was running an application in Matlab yesterday, and that one crashed because I was out of space. I then moved a 2.3GB file to another partition and started my program again.
Everything went well except that after stopping Matlab, my free space was 0b!

I checked with df and after several reboots, fsck, fsck -c, enptying the RAM... I still end up with this

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   35G   38M 100% /
none                  2.0G  324K  2.0G   1% /dev
none                  2.0G  1.2M  2.0G   1% /dev/shm
none                  2.0G  116K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G  4.0K  2.0G   1% /lib/init/rw
/dev/sda5             243G  241G  1.5G 100% /data
/dev/sda4              17G   14G  3.4G  80% /windows
```

It says that 35G are used out of 37G but I have only 38M available! If I start gparted for example, it does recognize my 2GB free of space!
What is going on? If I try to copy a file or do anything, I end up with "No space left on device"
:(:(:(

Anyone?

---

### Post by slakkie on 2010-01-07
The filesystem leaves about 5% of space allocated to root in case of your disk is full so the root user can login and fix the issues. You can change this with tunefs.

Please have a look here to clean up some of the files, 35Gb in use on a root partition is HUGE. Ahh, no seperate partition for /home. You might want to clean /data as well.

Have a look here: [http://newyork.ubuntuforums.org/showthread.php?t=1238309](http://newyork.ubuntuforums.org/showthread.php?t=1238309)

---

### Post by mcduck on 2010-01-07
Well, you clearly are out of space (the rest, 5% of disk space by default on Ext filesystems) is reserved for system and root user only, which is why your df output doesn't count it as available space. The reason for the reserved space is that the system needs to be able to create some files to be able to boot at all, so reserving som e space makes sure that user's can't fill the drive to the point where the system wouldn't be able to boot any more. Besides, while Ext filesystems don't fragment easily fragmentation still starts to become a problem when the drive gets full, and when the drive is over 90% full the performance will start do decrease quickly.

My suggestion is simply to remove some files to free some more space. You can start by running "sudo apt-get clean" to remove apt's cached package files, but you'll most likely have to delete some of your own files as well.

If you don't actually have much personal files then use the Disk Usage Analyzer (in Applications/Accessories menu) or the "du" command to find where the disk space is being used.

edit: Like the above post mentions, it's possible to change the amount of reserved space. But you definitely should leave enough reserved space on your root partition. Besides,, like I mentioned., you really don't want  to fill any Ext partition too full anyway. For any other partition than the ones used by the system changing the reserved amount to 0 is usually OK.

---

