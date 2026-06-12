---
title: "my user's home directory has disappeared entirely"
date: 2009-08-14
forum: General Help
---

### Post by yelirekim on 2009-08-14
Yesterday as I was shutting down my computer it froze for about 5 minutes, totally unresponsive, so I just held down the power button.

This morning when I booted it up it went through the normal bootup process and under normal circumstances it would automatically log in to my desktop, instead I was presented with an error message that said my home directory no longer exists.  /home is mounted on its own partition, which still exists, i was able to log in to a failsafe terminal, create a new user, log out and then start a normal gnome desktop session with that user.  Everything seems to be fine, nothing else is missing, except my entire /home/mike directory, which was pretty much everything....

Basically I need some help on how I can reboot, run fsck (i don't really know how to do this) and just generally troubleshoot this.

Please help! ](*,)

---

### Post by michy99 on 2009-08-14
Are you sure that your home partition is mounted? What is the output of these commands?```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by yelirekim on 2009-08-14
Here is the output:


```

henry@xavier-do:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f03c1e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381   83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda3            1306        5221    31455270   83  Linux
/dev/sda4            5222       18662   107964832+  83  Linux
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Partition table entries are not in disk order

```

```

henry@xavier-do:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=fba52206-c967-46ae-b45d-eb936143ffb7 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=1a156d38-ebb5-4b7c-8808-7505b61515e5 /home           ext4    relatime        0       2
# /var was on /dev/sda3 during installation
UUID=7fb89c94-65e6-4128-a168-c0113b3cdf8b /var            ext4    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=1ca73116-9947-4026-906a-504a5af755cc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```

henry@xavier-do:~$ mount
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-14-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /var type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/henry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=henry)

```

---

### Post by michy99 on 2009-08-14
As I suspected, sda4 is not mounted at /home. If you look over the output from 'mount' you will see entries for sda1 (/) and sda3 (/var), but not for sda4. Your /mike directory is still on sda4, the question is why it is not mounting.

The new users home is in /home, but since sda4 is not mounted there, it is on the / partiton (sda1).

---

### Post by michy99 on 2009-08-14
Try mounting from the command line and see what errors you get.```
sudo mount -t ext4 /dev/sda4 /home
```

---

### Post by yelirekim on 2009-08-14
i just ran:

```

sudo fsck -a /dev/sda4

```

and it output:

```

[...this same message repeated starting with 0...]
/dev/sda4: Group descriptor 822 checksum is invalid.  FIXED.
/dev/sda4: Group descriptor 823 checksum is invalid.  FIXED.
/dev/sda4 contains a file system with errors, check forced.
/dev/sda4: Deleted inode 3275 has zero dtime.  FIXED.
/dev/sda4: 170971/6750208 files (0.4% non-contiguous), 6417695/26991208 blocks

```

and it seems to be hung right there, i'm afraid to cancel the operation though

---

### Post by yelirekim on 2009-08-14
Everything is working :) I'm logged in on my normal desktop session and happy as can be.

Thanks for your help!  You really really saved me and I appreciate it.

---

