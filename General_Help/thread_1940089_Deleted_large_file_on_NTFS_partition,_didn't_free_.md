---
title: "Deleted large file on NTFS partition, didn't free up space"
date: 2012-03-13
forum: General Help
---

### Post by Unwahrscheinlich on 2012-03-13
My install is through wubi, but I doubt this makes a difference. I had a 30GB disk file that I didn't need, so I deleted it. (Not root.disk of course)
My free space didn't change (~35GB), even after a restart. The file was located on my windows NTFS partition, which is mounted at /host.

A full scan on baobab says: Total filesystem capacity: 164.6GB (used: 126.3GB available: 38.4GB)
But the used size of / (which includes my ubuntu stuff and /host) is 94.4GB (the /host usage plus 17GB of other files on / (root.disk), which is basically 30GB short of the other total)
The usage for /host says 77.6GB.
I should also clarify that my total windows partition size is 134GB, and that my ubuntu wubi disk, which is on the windows partition /dev/sda3, is 20GB


If I pull up the properties window for /host on nautilus, it says contents: 75.2GB, free space: 35.2GB

In gnome-system-monitor, it says 134GB total, 33GB free, 101GB used.

If it was moved to a Trash type folder, shouldn't it show on baobab where it is?


```
$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/loop0    ext3     19G   17G  2.1G  89% /
udev      devtmpfs    1.5G  4.0K  1.5G   1% /dev
tmpfs        tmpfs    597M  1.2M  596M   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    1.5G  816K  1.5G   1% /run/shm
/dev/sda3  fuseblk    135G  102G   33G  76% /host

```


```
$ mount -l
/dev/loop0 on / type ext3 (rw,relatime,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /boot type none (rw,bind)
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096) [OS]
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
gvfs-fuse-daemon on /home/alex/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alex)

```

---

### Post by Mark Phelps on 2012-03-13
The space reported for Ubuntu when it is installed with Wubi is the space INSIDE the root.disk file.  Removing files on the balance of the same NTFS partition, outside the root.disk file, will not affect the space in Ubuntu.

IS that what you're trying to do?

---

### Post by bcbc on 2012-03-13
Boot into windows, run 'chkdsk /f' on the host partition. Then check for the presence of any \FOUND.00? folders on that partition (they are hidden and protected, so use an admin command prompt). Sometimes you'll find a file that has been 'recovered' to there and it's still taking up that space.

---

### Post by jerome1232 on 2012-03-13
Any trash will be located on the root of the volume, in a folder called .Trash-xxxx, the xxxx being replaced with your uid (the first user on Ubuntu is always 1000, so it is probably /host/.Trash-1000. If anything is in there your trash icon will show it, I assume you have tried to empty your trash correct?

---

### Post by Unwahrscheinlich on 2012-03-13
> **bcbc said:**
> Boot into windows, run 'chkdsk /f' on the host partition. Then check for the presence of any \FOUND.00? folders on that partition (they are hidden and protected, so use an admin command prompt). Sometimes you'll find a file that has been 'recovered' to there and it's still taking up that space.

This worked! Thanks! Would the ubuntu way of doing this be to use fsck?
Details: I rebooted into windows. Ran 'chkdsk /f' on an admin cmd. It asked to schedule check on next reboot, since filesystem is mounted. I said yes, rebooted into windows, and it ran. Rebooted into ubuntu and my 30GB free space was back.


> **Mark Phelps said:**
> The space reported for Ubuntu when it is installed with Wubi is the space INSIDE the root.disk file.  Removing files on the balance of the same NTFS partition, outside the root.disk file, will not affect the space in Ubuntu.

IS that what you're trying to do?

No, I was trying to free up space on my windows partition.



> **jerome1232 said:**
> Any trash will be located on the root of the volume, in a folder called .Trash-xxxx, the xxxx being replaced with your uid (the first user on Ubuntu is always 1000, so it is probably /host/.Trash-1000. If anything is in there your trash icon will show it, I assume you have tried to empty your trash correct?

There is no /host/.Trash*, and I've emptied my ubuntu trash (which shouldn't matter because the file wouldn't fit on my ubuntu partition anyway). Even if the file was moved somewhere else on my /host partition, wouldn't baobab locate it and count it towards used space?

---

### Post by jerome1232 on 2012-03-13
It's a hidden folder, you would have to hit ctrl+h to see it.

Emptying your Trash empties the trash bin for all mounted partitions that your user has access to. The Linux equivalent to chkdsk is fsck, but for Linux file systems, for MS file systems I would always recommend using Microsoft's tools.

This is just as an fyi since it turns out there was an error with the file system anyways.

---

### Post by bcbc on 2012-03-13
Windows won't store such a large file in trash (recycle bin). Doing it in Ubuntu might - but I normally use 'rm' or shift-delete in Ubuntu when I want to make sure something is gone. 

Anyway - that's a good thing to remember to check! Thanks jerome1232

---

### Post by Unwahrscheinlich on 2012-03-13
> **jerome1232 said:**
> It's a hidden folder, you would have to hit ctrl+h to see it.

Emptying your Trash empties the trash bin for all mounted partitions that your user has access to. The Linux equivalent to chkdsk is fsck, but for Linux file systems, for MS file systems I would always recommend using Microsoft's tools.

This is just as an fyi since it turns out there was an error with the file system anyways.

Yeees, I know how hidden files/folders work ^_^ and baobab doesn't ignore them. Alright then I will stick to chkdsk and only use fsck if I can't use windows. Thanks!


> **bcbc said:**
> Windows won't store such a large file in trash (recycle bin). Doing it in Ubuntu might - but I normally use 'rm' or shift-delete in Ubuntu when I want to make sure something is gone. 

Anyway - that's a good thing to remember to check! Thanks jerome1232

Yea I was deleting a lot of files.. When I deleted the 30GB disk it just disappeared without a fuss, which made me think I forgot to hold shift on the one file that mattered :lolflag:. Next time I'll be more careful!

---

### Post by bcbc on 2012-03-13
Holding shift or not should not make a difference that results in NTFS corruption. So I guess it's more likely a bug. (When I wrote my last response I hadn't seen your edit that the chkdsk had worked. If I have the time I might experiment and see if I can reproduce this. There was one time I found a virtual disk sitting in found.000 and I think I had deleted it from  ubuntu - I do a lot of fiddling around so can't be certain). 

And you cannot run fsck on an ntfs partition - as far as I am aware, only chkdsk will fix ntfs corruption.

---

### Post by jerome1232 on 2012-03-13
> **bcbc said:**
> 
And you cannot run fsck on an ntfs partition - as far as I am aware, only chkdsk will fix ntfs corruption.

ntfsfix will correct some common errors, and then flag the disk for chkdsk to be run. I'm not sure if fsck will call ntfsfix if ran on an ntfs partition. I just might test that right now.

edit: It does work, if you install ntfsprogs and then link /usr/bin/ntfsfix to /usr/sbin/fsck.ntfs

---

### Post by Unwahrscheinlich on 2012-03-13
> **bcbc said:**
> Holding shift or not should not make a difference that results in NTFS corruption. So I guess it's more likely a bug.

And you cannot run fsck on an ntfs partition - as far as I am aware, only chkdsk will fix ntfs corruption.

Ah you're right; I can't do the normal "move to trash" delete on the /host partition. I wish I'd immediately checked dmesg.. Oh well.

> **jerome1232 said:**
> ntfsfix will correct some common errors, and then flag the disk for chkdsk to be run. I'm not sure if fsck will call ntfsfix if ran on an ntfs partition. I just might test that right now.

edit: It does work, if you install ntfsprogs and then link /usr/bin/ntfsfix to /usr/sbin/fsck.ntfs

Interesting. Do you mean make fsck.ntfs a link to ntfsfix?

---

### Post by jerome1232 on 2012-03-13
> **Unwahrscheinlich said:**
> 
Interesting. Do you mean make fsck.ntfs a link to ntfsfix?

Yes

---

### Post by bcbc on 2012-03-13
It seems a little pointless if it always schedules chkdsk to run the next time windows boots (which would have fixed the problem anyway). If it could fix minor problems without doing that, it might be a plus.

Also I think the partition has to be unmounted so wouldn't work on the /host

---

### Post by jerome1232 on 2012-03-14
> **bcbc said:**
> It seems a little pointless if it always schedules chkdsk to run the next time windows boots (which would have fixed the problem anyway). If it could fix minor problems without doing that, it might be a plus.

Also I think the partition has to be unmounted so wouldn't work on the /host

Good point about /host (can that be unmounted?)

I think the man entry describes it's usefullness well (Not actually applicable in this situation) I merely wanted to point there are Linux options when it comes to dealing with ntfs.

```
DESCRIPTION
       ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it cannot be mounted.

```

---

