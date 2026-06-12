---
title: "Raid 5 array says 1.27tb free but I cant copy file over!"
date: 2012-06-24
forum: General Help
---

### Post by zac_haryy on 2012-06-24
I have had my RAID 5 setup for a 5+ years now and have ran into this issue yet. It has 8 1tb disks making 6.26tb of total usable data (one spare drive). There is 1.27tb free right now but when I try transferring a 4.5gig file over to my server it fails and tells me there is not enough space. I have win7 on one of my computers that I am trying to transfer the file from and it just keeps popping up with an error saying the disk is full. I have attatched a picture of the error bellow. Is there something I need to do to the RAID 5 configuration? All the disks are in the array and it shows it as an active sync. Please let me know any suggestions as this one has me baffled :(


-haryy

---

### Post by blackflame2996 on 2012-06-24
That is wierd. Are you using ubunt server?

---

### Post by Cheesemill on 2012-06-25
What is the output of:
```
df -i
```

---

### Post by rubylaser on 2012-06-25
> **Cheesemill said:**
> What is the output of:
```
df -i
```

+1 it is likely this is a free inodes problem.  Along with that, can you post the output of these?

```
df -h
```
```
mdadm --detail --scan
```
```
cat /etc/fstab
```

---

### Post by zac_haryy on 2012-06-26
> **rubylaser said:**
> +1 it is likely this is a free inodes problem.  Along with that, can you post the output of these?

```
df -h
```
```
mdadm --detail --scan
```
```
cat /etc/fstab
```

Sorry for the late reply never got an email alert :( Here is the outputs for what you guys asked:

df -i
```

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1             593344  148621  444723   26% /
none                   61783    1032   60751    2% /dev
none                   63477       3   63474    1% /dev/shm
none                   63477      68   63409    1% /var/run
none                   63477       1   63476    1% /var/lock
/dev/md0             854671360  374240 854297120    1% /var/media

```

df -h
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.9G  3.3G  5.3G  39% /
none                  242M  660K  241M   1% /dev
none                  248M  164K  248M   1% /dev/shm
none                  248M  3.0M  246M   2% /var/run
none                  248M     0  248M   0% /var/lock
/dev/md0              6.3T  4.8T  1.3T  79% /var/media

```

mdadm --detail --scan
```
ARRAY /dev/md0 metadata=0.90 UUID=72fa18f5:bf5d1a62:31a05266:02bffc2c

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
# / was on /dev/sda1 during installation
UUID=1baa5edb-438e-4012-b553-46d0f573b410 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=86f7fdfc-eded-41f7-aa9f-ad86656397d4 none            swap    sw              0       0

```

---

### Post by zac_haryy on 2012-06-27
Any ideas on what to do with this? I make HD videos for people (weddings, etc) and I have run out of room to store all of my current projects. Please let me know if there is anything that I can go to try and get this going for me, thanks!

-haryy

---

### Post by rubylaser on 2012-06-27
Your mdadm array isn't in your /etc/fstab, how are you mounting it, and what filesystem do you have on it?

```
sudo -i
mount
```

Also, what happens if you try to write to the array locally (not over SAMBA from Windows)?
```
dd if=/dev/zero of=/var/media/testfile.out bs=1M count=10000
```

This will make a 10GB file on your array at /var/media/testfile.out.  Please post the output of that command, and then feel free to delete the file.
```
rm /var/media/testfile.out
```

---

### Post by zac_haryy on 2012-06-27
Every time I have to boot up the server I manually mount it. I had issues when I first setup the array with auto mounting in the fstab. Reason being is that once in a great while it wouldnt recognize a disk and it would go ahead and build the array with 7 disks and then I would have to re-add the disk to the array and risk loosing data while it was being re-built. So I just manually do it now which I have never had any issues with and it gives me some security. 

Here is the result: 

dd if=/dev/zero of=/var/media/testfile.out bs=1M count=10000

```
dd if=/dev/zero of=/var/media/testfile.out bs=1M count=10000
dd: writing `/var/media/testfile.out': No space left on device
1697+0 records in
1696+0 records out
1779216384 bytes (1.8 GB) copied, 116.644 s, 15.3 MB/s

```

mount

```

/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/md0 on /var/media type ext3 (rw)

```

Looks like it only wrote 1.8GB onto the array. :( 


-haryy

---

### Post by zac_haryy on 2012-06-29
Any suggestions that I could try or anything? Thanks!

-haryy

---

### Post by rubylaser on 2012-07-02
Sorry for the delay, I was out of town with my family. This is interesting.  Your filesystem isn't out of inodes, and has available space.   You are not using quotas on your filesystem, so that isn't preventing the write either.  Can I see all the info for your array, and the permissions on that path?

```
mdadm --detail /dev/md0
```
```
ls /var/ | grep media
```
```
du -hs --max-depth=1 /var/media
```

Another thing, you could do is unmount your array, and run an fsck on it.  Have it run even if it says it's clean. You might find some inode links / counts are way off and for some reason the drive never got flagged as dirty.

```
sudo -i
umount /var/media
fsck.ext3 /var/media
```
After the fsck completes, you can remount the array.

---

### Post by zac_haryy on 2012-07-02
> **rubylaser said:**
> Sorry for the delay, I was out of town with my family. This is interesting.  Your filesystem isn't out of inodes, and has available space.   You are not using quotas on your filesystem, so that isn't preventing the write either.  Can I see all the info for your array, and the permissions on that path?

```
mdadm --detail /dev/md0
```
```
ls /var/ | grep media
```
```
du -hs --max-depth=1 /var/media
```

Another thing, you could do is unmount your array, and run an fsck on it.  Have it run even if it says it's clean. You might find some inode links / counts are way off and for some reason the drive never got flagged as dirty.

```
sudo -i
umount /var/media
fsck.ext3 /var/media
```
After the fsck completes, you can remount the array.

That's alright I would rather have you get back to me than not at all, I appreciate it! Here is the info that you asked for:

mdadm --detail /dev/md0
```
/dev/md0:
        Version : 0.90
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jul  2 20:45:58 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
         Events : 0.1451406

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       97        1      active sync   /dev/sdg1
       2       8       81        2      active sync   /dev/sdf1
       3       8      113        3      active sync   /dev/sdh1
       4       8      129        4      active sync   /dev/sdi1
       5       8       65        5      active sync   /dev/sde1
       6       8       33        6      active sync   /dev/sdc1
       7       8       17        7      active sync   /dev/sdb1

```

ls /var/ | grep media
```
media
```

du -hs --max-depth=1 /var/media
```
du: warning: summarizing conflicts with --max-depth=1
Try `du --help' for more information.

Not sure what the warning means with that last command. I will run the fsck on it and let you know the results!

-haryy

```

---

### Post by zac_haryy on 2012-07-02
> **rubylaser said:**
> Sorry for the delay, I was out of town with my family. This is interesting.  Your filesystem isn't out of inodes, and has available space.   You are not using quotas on your filesystem, so that isn't preventing the write either.  Can I see all the info for your array, and the permissions on that path?

```
mdadm --detail /dev/md0
```
```
ls /var/ | grep media
```
```
du -hs --max-depth=1 /var/media
```

Another thing, you could do is unmount your array, and run an fsck on it.  Have it run even if it says it's clean. You might find some inode links / counts are way off and for some reason the drive never got flagged as dirty.

```
sudo -i
umount /var/media
fsck.ext3 /var/media
```
After the fsck completes, you can remount the array.

Just tried to check the array with fsck and this is the output

```
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext3: Is a directory while trying to open /var/media

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by rubylaser on 2012-07-03
> **zac_haryy said:**
> Just tried to check the array with fsck and this is the output

```
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext3: Is a directory while trying to open /var/media

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

Boy, I must have been off yesterday. To run the ls command correctly, you need to run it without the --max-depth option (you'd need to run this prior to unmounting your array).
```
du -hs /var/media
```

Sorry, you need to run the fsck on your array, not on the filesystem after you've unmounted it.
```
fsck.ext3 /dev/md0
```

---

### Post by zac_haryy on 2012-07-05
> **rubylaser said:**
> Boy, I must have been off yesterday. To run the ls command correctly, you need to run it without the --max-depth option (you'd need to run this prior to unmounting your array).
```
du -hs /var/media
```

Sorry, you need to run the fsck on your array, not on the filesystem after you've unmounted it.
```
fsck.ext3 /dev/md0
```

When running "fsck.ext3 /dev/md0" how long does it normally take? I have had it running for almost 48 hrs and it has been here since it started:

```
e2fsck 1.41.14 (22-Dec-2010)
/dev/md0 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes

```

I was just checking if that is normal or if possibly my putty session froze up?

-haryy

---

