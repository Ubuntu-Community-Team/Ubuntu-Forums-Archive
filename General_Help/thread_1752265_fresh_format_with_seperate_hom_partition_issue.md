---
title: "fresh format with seperate /hom partition issue"
date: 2011-05-07
forum: General Help
---

### Post by Foxcow on 2011-05-07
This past install, I decided to put /home on a separate partition to make the install processes easier.  I fresh installed 10.10 this way:

-8 gig swap 
-50 gig for /
-400+ gig for /home

During install, "swap" partition was left alone, "/" partition was formatted, and "/home" was mounted again as /home but not formatted.

Upon boot, there is a fresh /home folder with none of my previous stuff.  I cannot see the old /home partition unless I use the disk utility.

What have I done wrong?  :confused:

---

### Post by TeoBigusGeekus on 2011-05-07
Try editing your fstab, making your old home partition to be mounted as the new one.

---

### Post by WorMzy on 2011-05-07
Can you post the output of the following commands, here:


```
mount
```
```
sudo fdisk -l
```
```
cat /etc/fstab
```

---

### Post by Foxcow on 2011-05-07
Mount:
```

/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda3 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/foxcow/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=foxcow)

```

sudo fdisk -l

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e3eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         985     7905280   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         985        7064    48828416   83  Linux
/dev/sda3            7064       60802   431650816   83  Linux

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=240f8d41-3750-4d45-991b-0cafd236c372 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=5926bea3-720a-4705-96d3-840b20746ee7 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=f71db790-94b5-43bc-afd6-3820cba07eed none            swap    sw              0       0

```

---

### Post by Foxcow on 2011-05-07
> **TeoBigusGeekus said:**
> Try editing your fstab, making your old home partition to be mounted as the new one.



What would I need to change?  I've only edit fstab one time so I'm not at all familiar or confident.

Thanks

---

### Post by LostFarmer on 2011-05-07
looks like your fstab is good.  Did you install with a different username ?
post output of **ls /home**.  If you have 2 folders then the answer to above is yes.

---

### Post by Foxcow on 2011-05-07
> **LostFarmer said:**
> looks like your fstab is good.  Did you install with a different username ?
post output of **ls /home**.  If you have 2 folders then the answer to above is yes.



I thought I installed with the same username but must not have.

ls /home
```

chris foxcow lost+found

```

You were right.  'Chris' has all of my data.  should I delete 'foxcow' or change my username?

---

### Post by WorMzy on 2011-05-08
You can just rename the chris folder if you want to keep your username.

Firstly, rename the current foxcow folder
```
sudo mv /home/foxcow /home/foxcow.bak
```
Then rename the chris folder
```
sudo mv /home/chris /home/foxcow
```

If you'd rather change your username, this command should do it:
```
sudo usermod --login chris foxcow
```

I don't think you can run it while you're logged in though, which means you may find this option a lot more difficult to accomplish despite it looking a bit simpler. You may need to [boot into single/recovery mode]("http://ubuntuforums.org/showthread.php?p=9902528").

---

### Post by Foxcow on 2011-05-08
> **WorMzy said:**
> You can just rename the chris folder if you want to keep your username.

Firstly, rename the current foxcow folder
```
sudo mv /home/foxcow /home/foxcow.bak
```
Then rename the chris folder
```
sudo mv /home/chris /home/foxcow
```

If you'd rather change your username, this command should do it:
```
sudo usermod --login chris foxcow
```

I don't think you can run it while you're logged in though, which means you may find this option a lot more difficult to accomplish despite it looking a bit simpler. You may need to [boot into single/recovery mode]("http://ubuntuforums.org/showthread.php?p=9902528").




Excellent!  Renaming was just as easy and worked after a quick reboot.  Thank you very much!

---

