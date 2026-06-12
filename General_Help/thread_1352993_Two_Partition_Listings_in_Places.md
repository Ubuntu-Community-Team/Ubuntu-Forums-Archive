---
title: "Two Partition Listings in Places"
date: 2009-12-12
forum: General Help
---

### Post by NertSkull on 2009-12-12
So I finally decided to learn to use fstab and I got my partition mounted.

I wanted to mount it in media so I could see it in "places".

But now I get two drives showing up when I boot.  I get one that is the mounted "Storage" drive.

But then I get another, unmounted "Storage" drive.  And if I click on it to mount it I get the following error:

mount: /dev/sdb1 already mounted or /media/Storage busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/Storage


Somehow I must have it listed an extra place.

If I do mount it into /mnt then I don't get this problem, but I kind of want it mounted in media.

Any idea how to remove that extra listing?

Thanks!!!

oh, and here is the fstab line I'm using

> UUID=355851cb-7ba5-4efd-bdd0-cffb479b3a13       /media/Storage     ext3     rw,auto,user,exec 0        0

---

### Post by Vishnu V on 2009-12-12
This is due to the mounting of two different drives into same folder
I think you have another drive named Storage .

---

### Post by NertSkull on 2009-12-12
Unfortunately I don't.  I have to HDD in my computer, with a total of 5 partitions.

Hard Drive 1
1. WindowsXP
2. Linux
3. Swap
4. Data

HDD2
1. Storage

So I don't see how it could be trying to mount two drives as Storage.  I actually am getting the same problem with my Data drive.  So I have a total of 4 drives showing up in my places menu, 2 Data and 2 Storage.  

Any other thoughts?

I feel like somehow its keeping a remnant of my previous manual mountings of these drives on record before I changed my fstab file.  Is that possible?

---

### Post by Vishnu V on 2009-12-12
Did u have 2 entry for same drive on fstab
like 1 using uuid and other using device name (like /dev/sdxx) ?
Can you post complete fstab

---

### Post by NertSkull on 2009-12-12
I don't think so, but it is possible.  I just figured fstab out in the past day.  Here is the file I am using.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=748e747c-395b-4f91-b62e-29eb80a932b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=2090a017-523c-42b6-84f0-b7bb8af76754 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# my fstab settings for other drives
UUID=1A84C50D84C4EC77        /media/Data    ntfs-3g    auto,user,exec,nls=utf8 0        0
UUID=355851cb-7ba5-4efd-bdd0-cffb479b3a13       /media/Storage     ext3     rw,auto,user,exec 0        0
```

---

### Post by Vishnu V on 2009-12-12
Hmm. fstab settings seems to be ok. Did you edit /etc/mtab. ?

---

### Post by NertSkull on 2009-12-12
No, but I did just open it for the first time ever and saw two lines defining dev sda5 and sdb1 which are my two drives that are mounting funny.  But I'm mounting them through the UUID in fstab.  

If I delete those two lines (near the bottom) and restart would that fix the problem?  I was thinking maybe they are there from when I manually mounted the drives.  But I don't know anything about mtab and don't know if I can edit it at all?

mtab:

```
/dev/sda3 / ext4 rw,errors=remount-ro 0 0
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
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda5 /media/Data fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/Storage ext3 rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/jimmy/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=jimmy 0 0
```

---

### Post by NertSkull on 2009-12-12
So I've discovered that mtab is just a listing of current settings, kind of.  So removing those two lines is only like unmounting a drive.  I still have the same problem.

But I did try unmounting on of the drives.  Then clicking on the other (extra) "Storage" or "Data" drive.

When I click on it, it jumps to the other drive and loads it, the one I clicked on stays unmounted.  And about 5 seconds later I get the error:

```

Unable to mount Storage

Timeout waiting for mount to appear
```

---

### Post by NertSkull on 2009-12-12
So I went back to the fstab and changed the device listing location to not use UUID but instead to use /dev/sda5 and /dev/sdb1

Now everything works just fine.  I don't get two listings for each drive (the unmountable listing is now gone).

I can use this for now, and it works.  But I would still really like to figure out why the UUID mode did not work for me, and gave me multiple listings of the drive.

Any thoughts would be greatly appreciated, but at least its kind of working now.

---

### Post by Junkieman on 2010-01-21
Hi NertSkull, did you find out why this happens? I get the same behavior on my storage drive too. 

It didn't always do this, but only after I did some drive swapping to install another OS. I checked, and double checked my fstab, and it all seems fine.

Nothing serious, but something I'd like to get fixed. Sure you would too ;) I found a closely [related bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/42017") that creates this behavior, but it was logged for a USB drive, still, I wonder if the same bug applies to fixed drives.

No solution on my side, yet.

---

### Post by NertSkull on 2010-02-07
I haven't figured out exactly why its happening.  I've tried a bunch of settings and nothing seems to work.

It kept messing with my USB flash drives as well.  It made them difficult to mount.  I'm actually think its getting time for a fresh install on my part for other reasons.  

I'll see what happens with a new install and hopefully the problem will be no more.  If it happens again then I'll spend some more time delving into it because there must be a more serious issue.

---

