---
title: "hard drive"
date: 2009-09-08
forum: General Help
---

### Post by bkimbro on 2009-09-08
I recently installed Ubuntu on my computer on a second partition of the hard drive.  But for some reason it is telling me that I cannot put anything on my hard drive as the hard drive is full.  Yet the partition Ubuntu is using only has 1.3 GB of 30 GB used.  I'm thinking that it may be trying to put everything in the swap file which is only 250 MB.  How can I fix this so that I can use the main partition?

---

### Post by moody_mark on 2009-09-08
That sounds a bit odd. Usually the default place for all files is in your /home/<user> directory. Open a terminal and type the command

```

df -h
```

and then paste it here. Also the output of the command

```

mount
```

Might help too to see whats mounted on where

---

### Post by bkimbro on 2009-09-08
"df -h" gives me
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G     0   100% /
tmpfs                 498M     0    498M    0% /lib/init/rw
varrun               498M   116K  497M   1% /var/run
varlock              498M        0  498M   0% /var/lock
udev                  498M  164K  497M   1% /dev
tmpfs                 498M    88K  497M   1% /dev/shm
lrm                    498M   2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K  1008K   2% /tmp
/dev/sda3              27G  510M   25G   2% /media/disk

"mount" gives me
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bkimbro/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bkimbro)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

---

### Post by raymondh on 2009-09-08
> **bkimbro said:**
> "df -h" gives me
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G     0   100% /
tmpfs                 498M     0    498M    0% /lib/init/rw
varrun               498M   116K  497M   1% /var/run
varlock              498M        0  498M   0% /var/lock
udev                  498M  164K  497M   1% /dev
tmpfs                 498M    88K  497M   1% /dev/shm
lrm                    498M   2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K  1008K   2% /tmp
/dev/sda3              27G  510M   25G   2% /media/disk

"mount" gives me
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bkimbro/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bkimbro)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

As you've noticed ... you have the 2.3GB install error for root (/).

2 options.

1.  take space away from elsewhere and give to Ubuntu root
2.  re-do.

Post back if you need assistance.  Back-up files.

---

### Post by moody_mark on 2009-09-09
As raymondhenson says you only have 2.3G allocated to / and everything else. It seems that your disc has another partition;

/dev/sda3 27G 510M 25G 2% /media/disk

Im guessing here but when you installed perhaps you didnt allocate enough size to Ubuntu, and it only used a minimal amount. Depending on how you installed, I think part of the installer you have a option to use the whole disc which you obviously didnt use, or allocated a partition. When you use that partition option theres a slider bar on the screen you can drag to adjust the size of the ubuntu partition, perhaps (and again im guessing) you didnt resize that?

Anyway never mind, its not the end of the world. Have a look at the community documentation here;

[https://help.ubuntu.com/community/DrivesAndPartitions]("https://help.ubuntu.com/community/DrivesAndPartitions")

Otherwise you could just re-do the install if you only just started with it -you'll have nothing to loose. Another option is to use a package called "gparted" which you can install with the Add / Remove programs and makes for a nice interface into changing your partitions from within ubuntu. However if you are low on disc space then you might not be able to install even that

NOTE: backup your data before attempting any partition changes!

---

### Post by raymondh on 2009-09-09
> **moody_mark said:**
> As raymondhenson says you only have 2.3G allocated to / and everything else. It seems that your disc has another partition;

 When you use that partition option theres a slider bar on the screen you can drag to adjust the size of the ubuntu partition, perhaps (and again im guessing) you didnt resize that?


NOTE: backup your data before attempting any partition changes!

As moody_mark says, when you install side-by-side, there is a slider at the bottom of the screen that you grab/use to allocate partition sizes ... otherwise ubuntu defaults to 2.3GB.

---

### Post by bkimbro on 2009-09-10
ok thanks for the help, I simply reinstalled ubuntu and manually told it which partition to use and now it is working just fine.

---

