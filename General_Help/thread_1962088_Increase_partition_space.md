---
title: "Increase partition space"
date: 2012-04-20
forum: General Help
---

### Post by kgilmore on 2012-04-20
Hi,

Im trying to install an application on the root drive under /opt/zimbra

Output of fdisk is 

```
ubuntu@mail:~$ sudo fdisk -l

Disk /dev/sda1: 22.5 GB, 22548578304 bytes
255 heads, 63 sectors/track, 2741 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table
```however the /opt directory size is only 4.0gb can this be increased without effecting the os?

PS. its an amazon ec2 instance on 10.04 is that makes any difference.

Thanks.

---

### Post by ZekeGraal on 2012-04-20
As long as the space you are expanding into is not being used by anything, it should be okay. If the terminal is confusing or you would like a GUI like I would, you could always install gparted.

Just be careful, always take your time when editing partitions. ;)

---

### Post by jerome1232 on 2012-04-20
> **kgilmore said:**
> Hi,

Im trying to install an application on the root drive under /opt/zimbra

Output of fdisk is 

```
ubuntu@mail:~$ sudo fdisk -l

Disk /dev/sda1: 22.5 GB, 22548578304 bytes
255 heads, 63 sectors/track, 2741 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table
```however the /opt directory size is only 4.0gb can this be increased without effecting the os?

PS. its an amazon ec2 instance on 10.04 is that makes any difference.

Thanks.

What do these commands show?

```
mount
df -h
```

---

### Post by kgilmore on 2012-04-20
```
ubuntu@mail:~$ mount
/dev/sda1 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

``````
ubuntu@mail:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.9G  3.6G  4.0G  47% /
none                  285M  108K  284M   1% /dev
none                  318M  112K  318M   1% /dev/shm
none                  318M   88K  318M   1% /var/run
none                  318M     0  318M   0% /var/lock
none                  318M     0  318M   0% /lib/init/rw
```

gparted says no devices detected?

Thanks for posts

---

### Post by jerome1232 on 2012-04-20
I'm not sure what is going on, fdisk says sda1 has no partition table, but your system is happily using sda1 none-the-less. I fear your going to need more expert advice than I can offer.

---

### Post by kgilmore on 2012-04-20
I managed to expand the partition while ubuntu was running and without effecting the OS or files. I used . . .

```
sudo resize2fs /dev/sda1
```

Now the root directory is using the full hard drive space and not just 4g, so now I can install the app. didn't even need to reboot.

Thanks for help

---

### Post by ZekeGraal on 2012-04-20
Great to hear! If you would, please use the "thread tools" at the top of the page to mark as solved.

Thanks,
~Zeke :)

---

