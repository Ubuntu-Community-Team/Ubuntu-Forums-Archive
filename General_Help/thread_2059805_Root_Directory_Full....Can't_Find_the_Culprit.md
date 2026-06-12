---
title: "Root Directory Full....Can't Find the Culprit"
date: 2012-09-18
forum: General Help
---

### Post by drmrgd on 2012-09-18
I'm probably being a bonehead here, but my root directory (~50GB) is showing that it's full.  However, checking the usual suspects, I can't seem to find the source. 

First my file system usage:

```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda3      ext4       46G   46G     0 100% /
udev           devtmpfs  7.9G   12K  7.9G   1% /dev
tmpfs          tmpfs     3.2G  944K  3.2G   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     7.9G  248K  7.9G   1% /run/shm
/dev/sda1      vfat      190M  122K  190M   1% /boot/efi
/dev/sda4      ext4      233G   87G  135G  40% /home
overflow       tmpfs     1.0M   64K  960K   7% /tmp
/dev/sdb3      fuseblk   120G   95G   25G  80% /media/windows
```

If I check the Trash folders:

```
# sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
du: cannot access `/media/LinuxShare/backup/homebak/daily.1/home/dave/.thunderbird/8i2g8fmo.default/Mail/Local': No such file or directory
du: cannot access `Folders/Trash.sbd': No such file or directory
du: cannot access `/media/LinuxShare/backup/homebak/daily.0/home/dave/.thunderbird/8i2g8fmo.default/Mail/Local': No such file or directory
du: cannot access `Folders/Trash.sbd': No such file or directory
du: cannot access `/home/dave/.thunderbird/8i2g8fmo.default/Mail/Local': No such file or directory
du: cannot access `Folders/Trash.sbd': No such file or directory
12K     /media/LinuxShare/backup/homebak/daily.0/home/dave/.local/share/Trash
16K     /home/dave/.local/share/Trash
16K     /home/dave/recovered_to_delete/.local/share/Trash
16K     /media/LinuxShare/backup/homebak/daily.1/home/dave/.local/share/Trash
4.0K    /home/dave/.local/share/Trash/files
4.0K    /home/dave/.local/share/Trash/info
4.0K    /home/dave/recovered_to_delete/.local/share/Trash/files
4.0K    /home/dave/recovered_to_delete/.local/share/Trash/info
4.0K    /home/dave/.thunderbird/8i2g8fmo.default/Mail/pop.secureserver-1.net/Trash.sbd
4.0K    /media/LinuxShare/backup/homebak/daily.0/home/dave/.local/share/Trash/files
4.0K    /media/LinuxShare/backup/homebak/daily.0/home/dave/.local/share/Trash/info
4.0K    /media/LinuxShare/backup/homebak/daily.0/home/dave/.thunderbird/8i2g8fmo.default/Mail/pop.secureserver-1.net/Trash.sbd
4.0K    /media/LinuxShare/backup/homebak/daily.1/home/dave/.local/share/Trash/files
4.0K    /media/LinuxShare/backup/homebak/daily.1/home/dave/.local/share/Trash/info
4.0K    /media/LinuxShare/backup/homebak/daily.1/home/dave/.thunderbird/8i2g8fmo.default/Mail/pop.secureserver-1.net/Trash.sbd
```

This is odd since it's showing folders that are located on another HDD that is not even plugged in (mountpoint = /media/LinuxShare/.  That being the case, I can still access that partition, even though it's not mounted as far as I can tell (and I did run umount to remove any devices not in use even though the drive where /media/LinuxShare is mounted is actually unplugged at the moment):

```
# mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /boot/efi type vfat (rw)
/dev/sda4 on /home type ext4 (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb3 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

Also:

```
# cat /etc/mtab
/dev/sda3 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda4 /home ext4 rw 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0

```

Looking for files larger than 1 GB returns a ton of large stuff on the partition that should be mounted on /media/LinuxShare, but nothing very large on /.  I think that somehow something's wrong with that mount point, but I can't seem to figure it out.  If it's not listed in fstab or mtab, where can I find it?  Could it be that somehow something on / is being mounted there and that's why it's filling up?

---

### Post by drmrgd on 2012-09-18
I just had a moment of "clarity".  Maybe what's happening is that /media/LinuxShare is not actually a mount point but actually acting as a folder because something didn't go right when I made a mount point in fstab (which is why it's not listed there).  Could that be possible?

Here's more info:

When I plugged the drive back in and looked at mtab and blkid:

```
# cat /etc/mtab
/dev/sda3 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda4 /home ext4 rw 0 0
overflow /tmp tmpfs rw,size=1048576,mode=1777 0 0
root@CygnusX1:/# blkid
/dev/sda1: UUID="DEEB-3A1A" TYPE="vfat" 
/dev/sda2: UUID="b170157f-8d99-4f06-8ce2-92e8e3f44f43" TYPE="swap" 
/dev/sda3: UUID="58702a5d-45aa-4c17-9de9-650e2d21d30e" TYPE="ext4" 
/dev/sda4: UUID="1b1c5499-2500-4432-a049-41c93399382d" TYPE="ext4" 
/dev/sdb1: UUID="1261-7FB0" TYPE="vfat" 
/dev/sdb3: LABEL="windows" UUID="4ECC6BF6CC6BD6AD" TYPE="ntfs"

```

```

# blkid
/dev/sda1: UUID="DEEB-3A1A" TYPE="vfat" 
/dev/sda2: UUID="b170157f-8d99-4f06-8ce2-92e8e3f44f43" TYPE="swap" 
/dev/sda3: UUID="58702a5d-45aa-4c17-9de9-650e2d21d30e" TYPE="ext4" 
/dev/sda4: UUID="1b1c5499-2500-4432-a049-41c93399382d" TYPE="ext4" 
/dev/sdb1: UUID="1261-7FB0" TYPE="vfat" 
/dev/sdb3: LABEL="windows" UUID="4ECC6BF6CC6BD6AD" TYPE="ntfs" 
/dev/sdc1: LABEL="FreeAgent Drive" UUID="9E68AD6368AD3B43" TYPE="ntfs" 
/dev/sdc2: LABEL="LinuxShare" UUID="dda21609-0a4b-4072-afe7-6d7de00a3873" TYPE="ext4"

```

```

# ls -al /media/
total 36
drwxr-xr-x  6 root root  4096 Sep 18 19:02 .
drwxr-xr-x 27 root root  4096 Sep  6 17:49 ..
lrwxrwxrwx  1 root root    45 Jul 27 16:13 .directory -> /etc/kubuntu-default-settings/directory-media
drwx------  1 dave dave 16384 Sep 16 03:01 FreeAgent Drive
lrwxrwxrwx  1 root root    42 Jul 27 16:13 .hidden -> /etc/kubuntu-default-settings/hidden-media
drwx------  3 root root  4096 Sep 16 07:50 LinuxShare
drwxr-xr-x  5 dave dave  4096 Aug 13 20:29 LinuxShare_
drwxr-xr-x  2 root root  4096 Jul 27 16:39 winEFI

```

There are two entries for LinuxShare now (one with an underscore), and the one with the underscore is the correct mount.  So, something's hosed with my mount point for that partition.  I'm not entirely sure how to fix this, though.

---

### Post by f8l_0e on 2012-09-18
That original entry from Sep 16 is owned by root and has no read or write permission for any other users.

---

### Post by drmrgd on 2012-09-18
So, the solution is to chown that mount point and then recreate an fstab entry for that folder?

---

### Post by uRock on 2012-09-18
Have you run bleachbit as root. You will have to install it via the Ubuntu Software Center or just as easily by entering the following into a terminal,```
sudo apt-get install bleachbit
```Once installed, use Unity to run Bleachbit (as Root), then check the boxes as seen in the screenshot to clear up some space.

---

### Post by drmrgd on 2012-09-18
Thanks for the advice uRock!  I'm 99% sure at this point that what happened is that instead of /media/LinuxShare pointing to the partition on my external drive where I archive things, it acted just as a regular folder, which is why root filled up so quickly. 

So, now what I need to do is to appropriately recreate that mount point pointing to sdc2.  Since it's an external USB drive, would it be correct to just create a new fstab entry, or should I be doing this another way?  I'm not entirely sure how USB devices are automounted when they're recognized.  I read up a little on udev rules, but I can't quite grasp it.

---

### Post by Bashing-om on 2012-09-18
In a situation such as this ..the quick/easy thing is to rule out a log issue.
Look in /var/log/ for any run-a-way files (find cause) and delete the old log files.
If an older install and no  house cleaning has been done ...the file space usage could be huge !

[INDENT][INDENT]hth <==BDQ

[/INDENT][/INDENT]

---

### Post by drmrgd on 2012-09-18
> **Bashing-om said:**
> In a situation such as this ..the quick/easy thing is to rule out a log issue.
Look in /var/log/ for any run-a-way files (find cause) and delete the old log files.
If an older install and no  house cleaning has been done ...the file space usage could be huge !

[INDENT][INDENT]hth <==BDQ

[/INDENT][/INDENT]

Thanks for the advice.  However, the cause of the problem is a poorly mounted archive partition.  I moved the "LinuxShare" folder to a different drive and re-checked the filesystem usage, and everything's back to normal.  What I need now is to figure out the best way to automount that backup partition so that this doesn't happen again.  I guess just creating a new fstab entry will do it.  If anyone has advice on a more appropriate way (assuming this is wrong), please let me know.

---

### Post by Silver Knight on 2012-10-05
> **drmrgd said:**
> I'm 99% sure at this point that what happened is that instead of /media/LinuxShare pointing to the partition on my external drive where I archive things, it acted just as a regular folder, which is why root filled up so quickly.

You've hit the nail on the head here.  This sounds like EXACTLY what's happened.

> **drmrgd said:**
>  So, now what I need to do is to appropriately recreate that mount point pointing to sdc2.  Since it's an external USB drive, would it be correct to just create a new fstab entry, or should I be doing this another way?  I'm not entirely sure how USB devices are automounted when they're recognized.

If you've done nothing about this yet, (though I suspect you have already solved it by this time) then what you want to do is first move the folder out of the way (rename it) so that when you plug in the external it automounts where you expect to find it, then copy/move any content from the folder into the external drive as appropriate.

The drive should create it's own mount point when plugged in thanks to udev, although depending on which desktop you're running, you may need to click some little gizmo in the desktop somewhere to force it to mount the first time or each time.  (On my KDE system it tends to be mostly automatic.)

---

### Post by drmrgd on 2012-10-06
> **Silver Knight said:**
> You've hit the nail on the head here.  This sounds like EXACTLY what's happened.



If you've done nothing about this yet, (though I suspect you have already solved it by this time) then what you want to do is first move the folder out of the way (rename it) so that when you plug in the external it automounts where you expect to find it, then copy/move any content from the folder into the external drive as appropriate.

The drive should create it's own mount point when plugged in thanks to udev, although depending on which desktop you're running, you may need to click some little gizmo in the desktop somewhere to force it to mount the first time or each time.  (On my KDE system it tends to be mostly automatic.)

Thanks for the advice!  I guess I forgot to mark this as solved (going to do that right now!).

Your suggestion is exactly what I did, although I did make a new fstab entry for that mount just to be sure that it always mounts correctly.  This is an external device that I always have connected to use as a backup drive.  So, I figured a permanent mount in fstab would be a good way to go.  

Seems like everything is working as I expect it to now.  Thanks again!

---

### Post by fyfe54 on 2012-10-06
I have found Bleachbit to be a very useful piece of software.  You should have it on your system.

---

### Post by Tralce on 2012-10-06
Might be a boneheaded idea but have you tried running the Disk Usage Analyzer as root? Terminal, sudo baobab. Scan /, and it's helped me every time.

---

