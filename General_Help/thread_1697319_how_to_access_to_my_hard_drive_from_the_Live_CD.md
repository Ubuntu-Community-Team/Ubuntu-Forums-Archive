---
title: "how to access to my hard drive from the Live CD?"
date: 2011-02-28
forum: General Help
---

### Post by joevmm on 2011-02-28
hi.. i have a big problem with my ubuntu linux.. last night i was trying to execute a windows aplicacion (with wine).. suddenly the pc turned off.. later i turned it on but i couldnt enter to ubuntu... now i want to format my pc but i need to save some files on my flash drive.. because i cannot enter to ubuntu so i can save those files.. I used the Live CD, actually im using the live cd right now... the problem is that i dont know how to acces to my hard drive so i can save those files. every time I try to acces, this error appears...

Unable to Mount Location
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

I tried with right click>Mount... but this error appears..

Unable to Mount Location
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Can please somebody tell me what to do? 
Thank you

---

### Post by blackmail on 2011-02-28
Try to force the mount of the disk. you could install gparted on the livecd:

```
sudo apt-get install gparted
```

and after that you should see how your HDD's partitions are named sda... and try to force the mount of these partitions. The problem is that when you get a failed shutdown you will not be able to mount your partition in normal mode and thus you will have to force the mounting of the partition. The code for this could be:

```
sudo mkdir /media/windows
sudo mount /dev/(yourdevice) /media/windows -o force
```

Write back and lemme know how it went...
Best Regards

---

### Post by joevmm on 2011-02-28
the gparted is already installed on the live cd..
I tried entering the codes you gave me.. but this what appears...

ubuntu@ubuntu:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda /media/windows -o force
mount: /dev/sda already mounted or /media/windows busy
ubuntu@ubuntu:~$ 
:(

I didnt understand that about forcing the mount. 

BTW i only have one partition...
thank you

---

### Post by pqwoerituytrueiwoq on 2011-02-28
on a live ubuntu cd the drive should be listed under the places menu which will mount the drive and open it in nautilus

---

### Post by joevmm on 2011-02-28
it appears but when i click it this error appears...

Unable to mount 77 GB Filesystem

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by seawolf167 on 2011-02-28
What is the output of 

```
mount
```

and 

```
sudo fdisk -l
```

---

### Post by joevmm on 2011-02-28
from mount is 

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/DANA MU type vfat (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


and from sudo fdisk -l is

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006bbb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 2002 MB, 2002747392 bytes
32 heads, 63 sectors/track, 1940 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69fa5168

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1940     1955488+   6  FAT16

---

### Post by seawolf167 on 2011-02-28
> **joevmm said:**
> 
   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended[/B]
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

To mount your Ubuntu partitions and get your info off it, try this:

```
sudo mkdir /media/ubuntuone
sudo mount /dev/sda1 /media/ubuntuone
```

and 

```
sudo mkdir /media/ubuntutwo
sudo mount /dev/sda2 /media/ubuntutwo
```

As blackmail said, you may have to use the force option if the above don't work (*-o force*)

---

### Post by joevmm on 2011-02-28
i used the first one> sudo mount /dev/sda1 /media/ubuntuone
but nothing happened... not even the ubuntu@ubuntu:~$ appeared...

then i used the second one> sudo mount /dev/sda2 /media/ubuntutwo
and this appeared... mount: you must specify the filesystem type

how do i use the -o force??? 

thank you all for the help

---

### Post by blackmail on 2011-03-01
to learn more about the mount option try to type in terminal:

```
man mount
```

or

```
mount --help
```

---

### Post by blackmail on 2011-03-01
If you start Gparted, try to use:

```
gksu gparted
```

and try to unmount your windows partition from there.

small explanation of all what is happening:

First when you make a directory in the /media folder , let's say /media/myhdd you actually just make a folder in the media directory where your windows partition will be mounted.

Second, when you look in the /dev directory you see the different drives you have where you have something like /dev/sda1
sda1 means:

a - is the letter that defines the hdd, if it is primary of secondary, meaning if you have sda then it is your first hdd if you have sdb then it is your second hdd

1 - the number means the number of the partition that you are accessing so for example if you want to access the third partition of your secondary hdd then you would have /sdb3

All of the above besides the part with gparted was just to inform you. Anyone else correct me if i am wrong.

---

### Post by blackmail on 2011-03-01
And i am not much of terminal stuff reader please start up gparted and make a screenshot of what it is showing and also if you could check the filesystem you are using. as i read from the output previously suggested the drive you should be trying to mount is sdb, mainly sbd1, but i could be wrong.

---

