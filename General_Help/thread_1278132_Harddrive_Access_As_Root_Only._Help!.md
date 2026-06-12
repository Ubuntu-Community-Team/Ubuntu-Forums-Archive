---
title: "Harddrive Access As Root Only. Help!"
date: 2009-09-29
forum: General Help
---

### Post by jaqian on 2009-09-29
I have a dual boot system winXp & Mint7. I needed more space so I reduced the windows drive and took 30gig, formated as ext2. All grand except it seems I need to be in root to copy files to it.

Any idea how I can change this?

Cheers,
Rob

---

### Post by arrange on 2009-09-29
I guess you made a new partition. How do you mount it?

---

### Post by Hallvor on 2009-09-29
> **jaqian said:**
> I have a dual boot system winXp & Mint7. I needed more space so I reduced the windows drive and took 30gig, formated as ext2. All grand except it seems I need to be in root to copy files to it.

Any idea how I can change this?

Cheers,
Rob

To make myself owner of partition /media/sda5 with read and write permission:

```
sudo chown -R hallvor:hallvor /media/sda5
```

You probably have a different username and a different partition, but that is how you do it.

---

### Post by jaqian on 2009-09-29
> **arrange said:**
> I guess you made a new partition. How do you mount it?

It mounts when I click on it as I can see a Lost+Found folder whatever that is for.

> **Hallvor said:**
> To make myself owner of partition /media/sda5 with read and write permission:

```
sudo chown -R hallvor:hallvor /media/sda5
```

You probably have a different username and a different partition, but that is how you do it.

Thanks Hallvor. I tried looking at fstab but not much use anymore. I remember having to set read/write permissions there on SUSE 9 years ago.

---

### Post by jaqian on 2009-09-30
> **Hallvor said:**
> To make myself owner of partition /media/sda5 with read and write permission:

```
sudo chown -R hallvor:hallvor /media/sda5
```



Tried this but didn't work :( Any other suggestions?

Does it make any difference that my drive is mounted at /dev/sda3 instead of /mount?

---

### Post by Hallvor on 2009-09-30
Please post the output of ```
cat /etc/fstab
``` from the terminal.

---

### Post by anaconda on 2009-09-30
yep.. the fstab file would show how you mount your drive, so. post it here.

By the way, why did you decide to use ext2-filesystem for your drive? Isn't it a bit old?

---

### Post by jaqian on 2009-09-30
> **Hallvor said:**
> Please post the output of ```
cat /etc/fstab
``` from the terminal.

Ok here you go but doesn't show much...

```

rob@glas ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=6c29b7f2-cfcc-4af4-9c03-9d18cbaac384 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b2bc0f25-2178-4566-9a4b-1901055afc43 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

> **anaconda said:**
> 
By the way, why did you decide to use ext2-filesystem for your drive? Isn't it a bit old?

It was first on the list :) Should have gone for ext3 probably.

---

### Post by Hallvor on 2009-09-30
It isn`t mounted. How do you copy files to a drive that isn`t mounted? :confused:

Try
```
sudo mount -a
```

and see if it mounts.

---

### Post by arrange on 2009-09-30
Unmount the drive, if it's mounted. Then click on it again. Then post the output of```
mount
dmesg | tail
```

---

### Post by jaqian on 2009-09-30
> **Hallvor said:**
> It isn`t mounted. How do you copy files to a drive that isn`t mounted? :confused:


I right click on the drive under My Computer and choose "Mount" then I go into the drive right click again and choose "Open as root" so I can copy files etc.


> **arrange said:**
> Unmount the drive, if it's mounted. Then click on it again. Then post the output of```
mount
dmesg | tail
```

mount...
```

rob@glas ~ $ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rob)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=rob)
[COLOR="Green"]/dev/sda3 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)[/COLOR]

```

dmesg | tail...
```

~ $ dmesg | tail
[   22.636628] [drm] Loading R300 Microcode
[   22.636695] [drm] Num pipes: 1
[   22.636729] [drm] writeback test succeeded in 1 usecs
[   25.439267] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.070967] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   27.070971] tg3: eth0: Flow control is on for TX and on for RX.
[   27.071014] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   37.656014] eth0: no IPv6 routers present
[10521.748242] UDF-fs: Partition marked readonly; forcing readonly mount
[10521.773788] UDF-fs INFO UDF: Mounting volume 'MARIES_WEDDING', timestamp 2006/09/25 13:16 (103c)

```

---

### Post by jaqian on 2009-09-30
):P [SIZE="5"]Btw thanks for all the help lads[/SIZE] :D

---

### Post by bodhi.zazen on 2009-09-30
```
sudo chown rob.users /media/disk
sudo chmod 770 /media/disk
```

See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

