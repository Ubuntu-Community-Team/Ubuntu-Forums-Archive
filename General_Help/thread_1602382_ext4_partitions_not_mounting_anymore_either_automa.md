---
title: "ext4 partitions not mounting anymore either automatically or manually"
date: 2010-10-21
forum: General Help
---

### Post by scottybwoy on 2010-10-21
Hi Ubuntu Community,

I have various drives and partitions that I have been mounting through  fstab, but sometimes I had to do it manually, but now, I can't get them  to mount at all.

At first I thought it might be a disk failure, but booting to a Live CD shows all the drives working fine.

when the entries are added into fstab, $mount -l shows them as mounted  to their relevant mount points, but the data does't show in either  terminal or dolphin?

Typing $umount /dev/drive always returns /dev/drive not mounted.

When I comment out the entries in fstab and reboot and try a manual  mount, I always get /dev/drive already mounted or /mount/point busy.   $mount -l does not show any mount entry points for the drive.

My /home/user partition is now full as I can't save data on the other drives, so I don't know if this is an issue.

Also I use a mixture of encrypted partitions and non encrypted partitions, but this wasn't an issue before.

Checking some of the logs didn't show any errors.  The problem seemed to  start when gdd was saving data to a partition mount point I thought was  mounted but wasn't.  I have since removed that data. and even created a  new mount point.

Tried all avenues I know of and can't find anything in other forums that help.  Is there a way to clear the drive cache?

Thanks in advance

---

### Post by VMC on 2010-10-21
Are you confusing device with mount point?

Print out your *fstab* so we can see what your referencing.

---

### Post by gordintoronto on 2010-10-21
> **scottybwoy said:**
> I have various drives and partitions ...


How about picking one example, and spell out the details. If you open the Place, "Computer," what appears?

---

### Post by scottybwoy on 2010-10-22
Here is the list from $fdisk -l

```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864       38914   273508802    5  Extended
/dev/sda5            4864        6079     9767488+  82  Linux swap / Solaris
/dev/sda6           17022       23100    48829536   83  Linux
/dev/sda7            6080        7295     9764864   83  Linux
/dev/sda8           23101       38914   127020032   83  Linux
/dev/sda9            7295        8511     9764864   83  Linux

/dev/sdb1   *           1        4863    39062016    7  HPFS/NTFS
/dev/sdb2            4864        8754    31254457+   5  Extended
/dev/sdb3            8755       24792   128825235    7  HPFS/NTFS
/dev/sdb5            6323        8754    19535008+  83  Linux

/dev/sdc1               1      121601   976760001   83  Linux

/dev/sdd1               1       25497   204804621   83  Linux
/dev/sdd2           25498       30515    40307085   83  Linux


```

And from mount -l

```


/dev/mapper/sda1_crypt on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda9 on /boot type ext4 (rw)
/dev/mapper/sda6_crypt on /home type ext4 (rw)
/dev/mapper/sda8_crypt on /home/user/Media type ext4 (rw)
/home/user/.Private on /home/user type ecryptfs (ecryptfs_sig=5ef485e60c75afa3,ecryptfs_fnek_sig=06956205a200b641,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
/dev/sde1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)


```

And my fstab

```


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/sda1_crypt /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda9 during installation
UUID=52f1a298-3871-4570-ad0d-82ec3c82cafc /boot           ext4    defaults        0       2
/dev/mapper/sda6_crypt /home           ext4    defaults        0       2
#/dev/mapper/sda7_crypt /home/android   ext4    defaults        0       2
/dev/mapper/sda8_crypt /home/user/Media     ext4    defaults        0       2
/dev/mapper/sda5_crypt none            swap    sw              0       0
#UUID=c6b291fc-07ee-4e6d-b17d-420357d8681e      /home/user/share  ext4    defaults        0       2
#UUID=f7a23ac1-7877-4688-bbd9-5363e237d43e      /home/user/spare  ext4    defaults        0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

Typing $sudo mount -t ext4 /dev/sdc1 /home/user/share/

Just returns

mount: /dev/sdc1 already mounted or /home/user/share/ busy

At this point, terminal is just at the home directory and no other file browsers are trying to access those directories or drives (that I know of).

If I uncomment those lines with the UUID's from fstab and boot normally, those drives still don't mount.
If I run a Live CD I can see all the files normally on those drives and they can be mounted.

Any other ideas?  Thanks in Advance

---

### Post by scottybwoy on 2010-10-22
Don't think I'm confusing Device with Mount Point.  According to that script in your signature it seems fuse is struggling with the mount.

I thought it might be a problem with mapper, but I don't really understand what's happening here to judge where the problem could be?

---

### Post by VMC on 2010-10-22
Download and run boot_info_script(see my "blue" link), then we can match up UUID's and see your boot process.

---

### Post by scottybwoy on 2010-10-23
I've just added a link in my signature to it.  See if you can make any sense of it.  In another forum I've been told there was an issue with UUIDs in Ubuntu 10.04 and the bug might still exist in Kubuntu, do you think I should file a bug?

---

### Post by scottybwoy on 2010-10-30
Bump,

Anyone see where my issue lies?

---

### Post by zaphod777 on 2010-10-30
I don't think it will show up as an actual HDD unless you mount it as a removable drive in the /media folder. Otherwise it will just be accessible in whatever folder you mounted it in.

What do you get if you do a 
```
df -h
```

---

### Post by zaphod777 on 2010-10-30
Also in your fstab "#" comments out that line so anything with a "#" won't mount.

assuming "df -h" doesn't show them mounted what happens if you manually try and mount them at their mount points?

example
```
sudo mount /dev/sdb2 /mnt/data
```

---

### Post by scottybwoy on 2010-10-30
```
df -h
```

Just returns

```

/dev/mapper/sda1_crypt
                       37G  3.5G   32G  10% /
none                  998M  416K  997M   1% /dev
none                 1005M  4.0K 1005M   1% /dev/shm
none                 1005M  104K 1005M   1% /var/run
none                 1005M     0 1005M   0% /var/lock
none                 1005M     0 1005M   0% /lib/init/rw
/dev/sda9             9.2G  191M  8.6G   3% /boot
/dev/mapper/sda6_crypt
                       46G   43G  850M  99% /home
/dev/mapper/1ATA_SAMSUNG_HD103UJ_S1PVJDWQ718206-part1
                       46G   43G  850M  99% /home/user/share
/dev/mapper/1ATA_Maxtor_6Y250P0_Y64VRV8E-part1
                       46G   43G  850M  99% /home/user/spare
/dev/mapper/sda8_crypt
                       46G   43G  850M  99% /home/user/Media
/home/user/.Private
                       46G   43G  850M  99% /home/user
/dev/sde1             4.0G  454M  3.5G  12% /media/disk

```

Manually mounting returns Disk drive already mounted or mount point busy.  I have already tried creating a new mount point and deleting the original and it still won't mount.

---

### Post by zaphod777 on 2010-10-30
If it were me I would try unmounting them and then running a fsck on each drive. 

If the drives mount fine using a live disk I would also try and copy entry for entry exactly what the fstab says on the livecd for those drives. 

If you unmount them and can't re-mount them I would also do a dmesg|tail and see what the logs show.

---

### Post by scottybwoy on 2010-10-30
I can only do an fsck from a Live CD, and it returns no errors.

From my installation, fsck returns drive already mounted even though it hasn't been at all (commented out from fstab).
```

$dmes|tail >

[  131.813717] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1780
[  133.893239] Valid eCryptfs headers not found in file header region or xattr region
[  133.893246] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[  135.798952] Valid eCryptfs headers not found in file header region or xattr region
[  135.798959] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[  164.721924] Valid eCryptfs headers not found in file header region or xattr region
[  164.721932] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[  191.813732] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1175
[  271.810087] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1318
[  371.815402] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1374

```
The partition I'm trying to mount isn't encrypted, don't know why those errors show.

---

### Post by scottybwoy on 2010-11-08
As stated before, I've tried mounting, unmounting, filechecking etc.  I  don't think the problem lies there, I think mapper is getting confused  at boot.  Any logs I've looked at I either don't understand or am  looking the wrong ones as so far I have not seen anything leading to the  issue.  I've given all the info in the thread I can so far, could this  be a bug?  I've submitted the problem to Launchpad, but I've never filed  a bug so am not sure of the procedure.  Is there anyone here reading  this that can point me in the right direction.  I'm getting tired of  this issue, but can't even find a workaround.  I'm getting similar  results on other partitions, including ones on the same disk as the root  filesystem, but booting into a Live CD shows no errors at all.

---

### Post by scottybwoy on 2010-11-11
bump, anyone?

---

