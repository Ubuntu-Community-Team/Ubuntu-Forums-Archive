---
title: "Autofs remounting cycle"
date: 2010-03-18
forum: General Help
---

### Post by thebigob on 2010-03-18
Hi All,

Looking for some help.

I had set up a usb hdd on my server. I have autofs to mount this disc.

Up until recently this worked fine however now it just constantly mounts and unmounts.

Tailing my /var/log/syslog shows this issue:

```

Mar 18 07:50:41 SheevaPlug automount[4632]: expiring path /auto/erv
Mar 18 07:50:41 SheevaPlug automount[4632]: unmounting dir = /auto/erv
Mar 18 07:50:41 SheevaPlug automount[4632]: expired /auto/erv
Mar 18 07:50:50 SheevaPlug automount[4632]: attempting to mount entry /auto/erv
Mar 18 07:50:51 SheevaPlug automount[4632]: >> erv: clean, 625878/15269888 files, 23504924/61049000 blocks (check in 4 mounts)
Mar 18 07:50:51 SheevaPlug automount[4632]: mount(ext2): mounted /dev/sda1 type ext3 on /auto/erv
Mar 18 07:50:52 SheevaPlug automount[4632]: mounted /auto/erv
Mar 18 07:50:52 SheevaPlug kernel: kjournald starting.  Commit interval 5 seconds
Mar 18 07:50:52 SheevaPlug kernel: EXT3 FS on sda1, internal journal
Mar 18 07:50:52 SheevaPlug kernel: EXT3-fs: mounted filesystem with writeback data mode.
Mar 18 07:51:04 SheevaPlug automount[4632]: 1 remaining in /auto
Mar 18 07:51:27 SheevaPlug automount[4632]: 1 remaining in /auto
Mar 18 07:52:13 SheevaPlug last message repeated 2 times
Mar 18 07:52:36 SheevaPlug automount[4632]: expiring path /auto/erv
Mar 18 07:52:36 SheevaPlug automount[4632]: unmounting dir = /auto/erv
Mar 18 07:52:36 SheevaPlug automount[4632]: expired /auto/erv
Mar 18 07:52:42 SheevaPlug automount[4632]: attempting to mount entry /auto/erv
Mar 18 07:52:43 SheevaPlug automount[4632]: >> erv: clean, 625878/15269888 files, 23504924/61049000 blocks (check in 3 mounts)
Mar 18 07:52:43 SheevaPlug automount[4632]: mount(ext2): mounted /dev/sda1 type ext3 on /auto/erv
Mar 18 07:52:43 SheevaPlug automount[4632]: mounted /auto/erv
Mar 18 07:52:43 SheevaPlug kernel: kjournald starting.  Commit interval 5 seconds
Mar 18 07:52:43 SheevaPlug kernel: EXT3 FS on sda1, internal journal
Mar 18 07:52:43 SheevaPlug kernel: EXT3-fs: mounted filesystem with writeback data mode.
Mar 18 07:52:59 SheevaPlug automount[4632]: 1 remaining in /auto
Mar 18 07:53:45 SheevaPlug last message repeated 2 times
Mar 18 07:54:08 SheevaPlug automount[4632]: 1 remaining in /auto
Mar 18 07:54:31 SheevaPlug automount[4632]: expiring path /auto/erv
Mar 18 07:54:31 SheevaPlug automount[4632]: unmounting dir = /auto/erv
Mar 18 07:54:31 SheevaPlug automount[4632]: expired /auto/erv
Mar 18 07:54:34 SheevaPlug automount[4632]: attempting to mount entry /auto/erv
Mar 18 07:54:35 SheevaPlug automount[4632]: >> erv: clean, 625878/15269888 files, 23504924/61049000 blocks (check in 2 mounts)

```It does this constantly.

Here is my auto.master 

```

/auto /etc/auto.misc --timeout=90,--verbose

```and my auto.misc

```

erv        -fstype=ext3        :/dev/sda1

```

I am running Jaunty

uname -a:

```

Linux SheevaPlug 2.6.30.2 #11 PREEMPT Wed Jul 22 19:53:31 MDT 2009 armv5tel GNU/Linux

```

Any ideas gratefully received.

---

### Post by thebigob on 2010-03-18
Found out what was causing this by using the command fuser to see which process was accessing the disc. Hope this helps someone

---

### Post by foobar66 on 2010-05-19
> **thebigob said:**
> Found out what was causing this by using the command fuser to see which process was accessing the disc. Hope this helps someone

What did you do precisely to solve this issue? I believe I have the same problem.
thanks

---

### Post by edkmho on 2010-05-19
Would appreciate if you clearly specify what you have done to solve this issue. I am having the same problem with Lucid and autoFS.

Thanks.

---

### Post by thebigob on 2010-05-19
> **foobar66 said:**
> What did you do precisely to solve this issue? I believe I have the same problem.
thanks


Find the mount point for the disk.

eg. 

/media/mydisk

Change this to where ever you have mounted your disk.

If you do not know you can find this out by using the mount command.

eg.

```

callum@SheevaPlug:~$ mount
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/mmcblk0p1 on /media/SD type ext3 (rw,noatime)
callum@SheevaPlug:~$ 

```Here I can see a memory card is mounted to /media/SD

If you cant find this post the output of your mount command an I will be able to let you know.

Assuming you know where the disk is mounted you can then use the following commands to see what is accessing the disk using its mount point as a parameter.

Continuing using my /media/SD mount point

```

root@SheevaPlug:~# lsof /media/SD | more
COMMAND     PID       USER   FD   TYPE DEVICE     SIZE  NODE NAME
apache2     567   www-data  txt    REG  179,1   324004 35349 /media/SD/usr/sbin/
apache2
apache2     567   www-data  mem    REG  179,1   108876 19760 /media/SD/usr/lib/l
ibaprutil-1.so.0.2.12
apache2     567   www-data  mem    REG  179,1   215724 19756 /media/SD/usr/lib/l
ibapr-1.so.0.2.12
apache2     567   www-data  mem    REG  179,1   241144 18630 /media/SD/usr/lib/l
ibldap_r-2.4.so.2.4.1
apache2     567   www-data  mem    REG  179,1    46600 18638 /media/SD/usr/lib/l
iblber-2.4.so.2.4.1
apache2     567   www-data  mem    REG  179,1  1101860 18619 /media/SD/usr/lib/l
ibdb-4.6.so
apache2     567   www-data  mem    REG  179,1   114604 16875 /media/SD/usr/lib/l
ibpq.so.5.1
apache2     567   www-data  mem    REG  179,1  1857672 20599 /media/SD/usr/lib/l
ibmysqlclient_r.so.15.0.0
apache2     567   www-data  mem    REG  179,1   487452 16587 /media/SD/usr/lib/l
ibsqlite3.so.0.8.6
apache2     567   www-data  mem    REG  179,1   140744 19443 /media/SD/usr/lib/l
ibexpat.so.1.5.2
apache2     567   www-data  mem    REG  179,1    88236 16485 /media/SD/usr/lib/l
ibsasl2.so.2.0.22

```This is an example of the lsof output. This should be run as root. so the command you will want to run will look something like:

```

sudo lsof 'insert mount path here'

```from the above I can see that apache2 is using the file system and the path is is using to access this.

Also there is the fuser command.

Again this should be run as root

This will show  which user is accessing the disk (if any)

A combination of both will help you track down either what or who is accessing the disk.

---

