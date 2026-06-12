---
title: "Can't write to my new drive?"
date: 2009-12-29
forum: General Help
---

### Post by Redundant Username on 2009-12-29
*note: I'm using wubi
For some reason only sda2 is showing, and not the other partition on the drive. 

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                          /proc        proc  defaults                                                      0  0  
/host/ubuntu/disks/root.disk  /            ext3  loop,errors=remount-ro                                        0  1  
/host/ubuntu/disks/boot       /boot        none  bind                                                          0  0  
/host/ubuntu/disks/swap.disk  none         swap  loop,sw                                                       0  0  
/dev/sdb1                     /media/sdb1  ntfs  nls=iso8859-1,users,umask=000,gid=anthony,posix=1,user,owner  0  0  
/dev/sdb3                     /media/sdb3  ntfs  nls=iso8859-1,users,umask=000,gid=anthony,posix=1,user,owner  0  0  
/dev/sda2                     /media/sda2  ntfs  nls=iso8859-1,users,umask=000,gid=anthony,posix=1,user,owner  0  0   
```

---

### Post by x33a on 2009-12-29
which one is your new drive? sda or sdb.

please post the output of```
sudo fdisk -l
df -h
```

---

### Post by Redundant Username on 2009-12-29
sda2

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce70f9dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20235   162537606    7  HPFS/NTFS
/dev/sda2           20236       38913   150031035    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             19G   13G  5.7G  69% /
udev                  1.5G  312K  1.5G   1% /dev
none                  1.5G  476K  1.5G   1% /dev/shm
none                  1.5G  208K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sdb1             142G   96G   47G  67% /host
/dev/sdb1             142G   96G   47G  67% /media/sdb1
/dev/sdb3             7.1G  6.3G  902M  88% /media/sdb3
/dev/sda2             144G  834M  143G   1% /media/sda2
/dev/sda1             156G   31G  125G  20% /media/309383BE32AECF9F

``` why is the second partition have random numbers and letters and mounted in a different place?

---

### Post by Redundant Username on 2009-12-30
bump

---

### Post by x33a on 2009-12-30
sda2 cannot be the new drive, if you mean the new partition then that's a different thing.

in linux drives are assigned sda, sdb, sdc etc. and their partitions are like sda1, sda2, etc.

back to the problem:

try 
```
sudo mkdir /media/sda1
```

also, add this line to your fstab.

```
/dev/sda1                    /media/sda1  ntfs  nls=iso8859-1,users,umask=000,gid=anthony,posix=1,user,owner  0  0
```

now see if it mounts fine.

---

### Post by Redundant Username on 2009-12-30
Yes, I mean sda2 is one of the partitions on the drive. Thanks, I can write to it now. The other partition has is mounted in a different place and has random numbers and letters. I still can't write to that partition.

---

### Post by Redundant Username on 2009-12-30
bump.

---

