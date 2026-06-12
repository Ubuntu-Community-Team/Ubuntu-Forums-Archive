---
title: "how to make hard drive partition stay same/mount?"
date: 2009-07-20
forum: General Help
---

### Post by serious7 on 2009-07-20
Hi I have a one tb hard drive partitioned into many drives (triple boot/data storage) and I have one large partition dedicated to all my music/homework files. The problem is that the file path keeps changing. Right now it reads:
----------------------
/media/disk/Music/
--------------------

but if i restart computer it might read:

-----------------
/media/disk-1/Music/
--------------------

and this is causing a lot of problems with exaile and playlists. How do I keep it so that it will stay constant?

And another problem that is an issue...Ubuntu reads the harddrive as 706.6 gb and vista reads it as 68X.0 gb (x=any digit i forgot tho.. lol). Is this normal or something that I should worry about? I know for a fact that actual space of the partition is around 680 gb.

---

### Post by HermanAB on 2009-07-20
Howdy,

Two ways to fix it:
[LIST=1]
[*]Put an entry in /etc/fstab
[*]Give the file system a label
[/LIST]

Eg:
```
sudo tune2fs -L muzak /dev/sdb5
```

Read the tune2fs man page for details.
Find the device with 'mount', 'df' or 'ls /dev/sd*'.

---

### Post by serious7 on 2009-07-20
I do not understand what you are saying. Can you explain in english please? lol.

---

### Post by serious7 on 2009-07-20
bump

---

### Post by serious7 on 2009-07-21
someone there that can help me please?

---

### Post by michy99 on 2009-07-21
What is the output from these commands?```
sudo fdisk -l
mount
cat /etc/fstab
ls -l /media
```

---

### Post by serious7 on 2009-07-21
nicky@nicky-desktop:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a0f3a6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100      121600   935794282+   f  W95 Ext'd (LBA)
/dev/sda5            5100       30595   204796588+   7  HPFS/NTFS
/dev/sda6           30596       35694    40957686   83  Linux
/dev/sda7           35695      121600   690039913+   7  HPFS/NTFS



nicky@nicky-desktop:~$ mount
/dev/sda6 on / type reiserfs (rw,relatime,notail)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nicky/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nicky)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=nicky)
/dev/sda7 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)



nicky@nicky-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=15a57a7f-8186-4357-a85b-b5c9795e1c50 /               reiserfs notail,relatime 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0




nicky@nicky-desktop:~$ ls -l /media
total 6
lrwxrwxrwx 1 root root    6 2009-07-18 14:50 cdrom -> cdrom0
dr-xr-xr-x 1 root root 2048 2009-04-29 05:02 cdrom0
drwxrwxrwx 1 root root 4096 2009-07-20 15:56 disk

---

### Post by serious7 on 2009-07-21
bump??? why is there no one here to help T.T

---

### Post by michy99 on 2009-07-21
Since /dev/sda7 is formatted as NTFS, I suggest you check out this thread on how to automount it. That way the path should always be the same.

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by serious7 on 2009-07-21
The ntfs config tool does not show sda7 as an option (which is the partition i'm having problem with).

---

### Post by michy99 on 2009-07-21
Did you make sure the partition was unmounted first?```
sudo umount /media/disk
```Yes, that is umount, not unmount.

---

### Post by egalvan on 2009-07-21
I have an internal NTFS partition that I use in much the same way.

I booted into XP and gave the partition the following label...

gx280-xp

ntfs-3g put the following in the fstab...

```
/dev/sda1  [COLOR="Red"]/mnt[/COLOR]/gx280-xp   ntfs-3g  defaults,locale=en_US.UTF-8  0  0 
```

As my preference, it does not appear on the desktop.
 For that to happen, you need to substitute /media for /mnt...

```
/dev/sda1  [COLOR="Red"]/media[/COLOR]/gx280-xp   ntfs-3g  defaults,locale=en_US.UTF-8  0  0 
```

So you should have something like this in your fstab

```
/dev/sda7  [COLOR="Red"]/mnt[/COLOR]/gx280-xp   ntfs-3g  defaults,locale=en_US.UTF-8  0  0 
```

or this


```
/dev/sda7  [COLOR="Red"]/media[/COLOR]/gx280-xp   ntfs-3g  defaults,locale=en_US.UTF-8  0  0 
```

---

