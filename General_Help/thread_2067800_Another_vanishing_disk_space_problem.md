---
title: "Another vanishing disk space problem"
date: 2012-10-07
forum: General Help
---

### Post by tarkawebfoot on 2012-10-07
I have a server with 4 disks in it that has been running Ubuntu for years. I did the upgrade to Pangolin when it dropped into LTS. Since then, it's been very slow, but seemed to work as before overall.

That was until two weeks ago. Suddenly I found I couldn't run X programs after logging in with SSH. Further investigation revealed my root filesystem was full. I have nowhere near enough stuff on that filesystem to fill it.

I moved some stuff off of the root filesystem onto the 2TB backup disk, and could launch X programs again. But later that same night I was logged in over SSH playing FreeCell, and suddenly the game dumped with the same X  messages as before. I checked system logs and found that the rsync backup had kicked off and apparently filled the root filesystem again. The backup normally goes to my Time Capsule which is a CIFS mount.

This backup scheme has worked well for over a year. I see on other posts that it's common for rsync to fill the root filesystem if the target directory is on a device that's not mounted. That should not have been the case, but it's still true that my free space vanished again immediately after rsync kicked off.

Anyway, what I need to do now is get my free disk space back. The problem is that I can't find where it went. Normally when rsync fails in that way, it writes a directory to the root filesystem that can be deleted. I have no such directory. In fact nothing in my root filesystem says it's using more than about 20G of space. I've read many different posts about i-nodes, lsof, fsck, and tried all the suggestions. Nothing's worked.

The problem persists across reboots, and fs checks.

Any more ideas about where to look for missing free disk space, or should I backup - reformat - restore?

```
df -h 

Filesystem      Size  Used Avail Use% Mounted on
/dev/md1        220G  213G     0 100% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  896K  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
overflow        1.0M  4.0K 1020K   1% /tmp
/dev/md0        464M   74M  367M  17% /boot
/dev/sdd1       1.8T 1017G  724G  59% /media/bigdisk

df -hi

Filesystem     Inodes IUsed IFree IUse% Mounted on
/dev/md1          14M  322K   14M    3% /
udev             492K   574  491K    1% /dev
tmpfs            495K   494  494K    1% /run
none             495K     4  495K    1% /run/lock
none             495K     1  495K    1% /run/shm
overflow         495K     7  495K    1% /tmp
/dev/md0         120K   284  120K    1% /boot
/dev/sdd1        117M   22K  117M    1% /media/bigdisk


mount

/dev/md1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
/dev/md0 on /boot type ext3 (rw,relatime)
/dev/sdd1 on /media/bigdisk type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

cat /etc/fstab

proc            /proc           proc    defaults        0       0
UUID=d7d65735-9b30-4d49-8e2f-13573c2d0b38 /               ext3    relatime,errors=remount-ro 0       1
UUID=94476466-8de2-4063-9145-ead9993fcf14 /boot           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdd1 /media/bigdisk ext4 defaults 0 2


sudo du -h --max-depth=1 /

[sudo] password for tarka: 
4.9G    /usr
du: cannot access `/proc/14029/task/14029/fd/4': No such file or directory
du: cannot access `/proc/14029/task/14029/fdinfo/4': No such file or directory
du: cannot access `/proc/14029/fd/4': No such file or directory
du: cannot access `/proc/14029/fdinfo/4': No such file or directory
0       /proc
11M     /sbin
1.1G    /opt
1.2G    /var
200K    /srv
5.1M    /root
896K    /run
4.0K    /dev
391M    /lib
1.2T    /media
63M     /boot
8.9M    /bin
3.4M    /lib32
16K     /lost+found
20M     /etc
4.0K    /selinux
4.0K    /lib64
8.0K    /mnt
296M    /home
4.0K    /tmp
0       /sys
1.2T    /

sudo mdadm --query --detail /dev/md1

/dev/md1:
        Version : 0.90
  Creation Time : Thu Sep 17 01:36:07 2009
     Raid Level : raid5
     Array Size : 233456384 (222.64 GiB 239.06 GB)
  Used Dev Size : 116728192 (111.32 GiB 119.53 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Oct  7 13:06:29 2012
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : cec65ad0:e50c35ac:ea57701c:192c502d
         Events : 0.2685508

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5

```

---

### Post by tarkawebfoot on 2013-01-26
Well, finally figured out what happened.

During the Pangolin upgrade, I must have chosen to replace my fstab or something when I shouldn't. I finally realized that the /media/Delta directory was NOT a mount point any more. It was just a directory on the local filesystem created by rsync when it's remote mount point no longer existed.

I deleted the entire directory and all is well. Now if I could only figure out why my CIFS mount disappeared from my fstab....

Oh well, I probably never will.

---

