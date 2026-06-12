---
title: "No My Computer"
date: 2009-08-14
forum: General Help
---

### Post by shanali4 on 2009-08-14
[SIZE=4]I was previously using microsoft windows xp sp3 pirated. i today switched to kubuntu. i am very new to linux. this first time i ever seen linux. I clicked the start menu and their was no My Computer. Then i clicked File manager from start menu. it opened a windows then i clicked root. it was not showing any hard dish drive (C:, D:, E:) etc. from where can i access the drives and my files stored. kubuntu user interface is very irritating for me
[/SIZE]

---

### Post by konqui on 2009-08-14
There is nothing like C: D: etc in linux

In Kubuntu when you open file manager (the name of the program is dolphin), you click on partition on side bar. it is recommend to have volume labels. When you click root it shows you the contents of partition where kubuntu is installed. Once you mount a partition by clicking on it in dolphin, it appears in the folder media of your root partition

---

### Post by oldos2er on 2009-08-14
The OP might want to read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) and [http://kubuntuguide.org/Jaunty](http://kubuntuguide.org/Jaunty)

---

### Post by slakkie on 2009-08-14
In Unix/Linux everything is considered a file. Even disks :)

If you type in mount in a terminal you will see something like this:

```

mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro,commit=600)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
/dev/sda7 on /var/log type ext3 (rw,relatime,errors=remount-ro,commit=600)
/dev/sda6 on /home type ext3 (rw,relatime,commit=600)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wesleys/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wesleys)

```

The more important entries are /dev/sdaX

One partition of the first disk (/dev/sda1) is mounted as / (which is basicly the equivalent of C:)
One partition of the first disk (/dev/sda6) is mounted as /home, my documents if you will
One other partition (/dev/sda7) is mounted as /var/log, the location where the system and all applications log to.

For more information about this:

man mount
man fstab

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by AmerNewbieInDE on 2009-08-14
actually, being new to linux myself, i had o search around because everything everyone told me was so complicated... first off, which ubuntu are you using, second, if you look on the menu bar, see application, places and system.. places is for your physical disk partitions, cd, dvd ect. if you click on it, it opens a menu of the partition and their names, just click on the partition name of what you want to open..

---

