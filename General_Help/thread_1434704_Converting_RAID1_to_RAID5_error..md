---
title: "Converting RAID1 to RAID5 error."
date: 2010-03-20
forum: General Help
---

### Post by Weidbrewer on 2010-03-20
Hey, all.  I am in the process of converting a RAID 1 setup to a RAID 5 with a total of four disks.  I had been following [these instructions]("http://http://scott.wallace.sh/2007/04/14/converting-raid1-to-raid5-with-no-data-loss/").

Everything progressed exactly how he described (with the exception of me using a total of 4 instead of three) up until this point:

> ```
# mdadm --create /dev/md0 --level=5 -n 2 /dev/hda1 /dev/hdb1
  mdadm: /dev/hda1 appears to contain an ext2fs file system
      size=1946592K  mtime=Sat Apr 14 07:18:32 2007
  mdadm: /dev/hda1 appears to be part of a raid array:
      level=1 devices=2 ctime=Sat Sep 17 16:17:45 2005
  mdadm: /dev/hdb1 appears to contain an ext2fs file system
      size=1946592K  mtime=Sat Apr 17 07:18:32 2007
  mdadm: /dev/hdb1 appears to be part of a raid array:
      level=1 devices=2 ctime=Sat Sep 17 16:17:45 2005
  Continue creating array? y
  mdadm: array /dev/md0 started
```.

"At this point the RAID software decided it wanted to rebuild the array. Uh-oh, there goes my data&#8230; I quickly mounted /dev/md0 and had a look&#8230; all my data is still intact! Oh well, let the software do it&#8217;s thing. Who am I to argue?"

I did not get any sort of prompt about it rebuilding the array.  I continued and added my other drives.  next I reached:


```
# mdadm --grow /dev/md0 --raid-disks=3 --backup-file=/mnt/tmp/raid1-5.backup.file
  mdadm: Need to backup 128K of critical section ..
  mdadm: ... critical section passed.
```

(again, I had four.  Also, my array is md1) I received this error:

```
~$ sudo mdadm --grow /dev/md1 --raid-disks=4 --backup-file=/mnt/tmp/raid1-5.backup.file
mdadm: Need to backup 192K of critical section..
mdadm: /dev/md1: failed to find device 1. Array might be degraded.

```

At this point, I was able to remount md1 and everything was still there, albeit, not a larger array.  After a reboot, it was not.  I checked and got this:

```
~$ sudo fsck.jfs -a /dev/md1fsck.jfs version 1.1.12, 24-Aug-2007
processing started: 3/20/2010 15.51.37
The current device is:  /dev/md1

The superblock does not describe a correct jfs file system.

If device /dev/md1 is valid and contains a jfs file system,
then both the primary and secondary superblocks are corrupt
and cannot be repaired, and fsck cannot continue.

Otherwise, make sure the entered device /dev/md1 is correct.

```


IS there any fixing what I may have done?  If not, it is not the end of the world - I can wipe the drives and rebuild.  (I was smart enough to backup my data.)

Thanks in advance for any help.


**EDIT**  Looking at the partition editor, somehow - and I have no idea how - one of the new drives was listed as being totally full and formated as ext3.  I reformatted and was able to remount my existing RAID.  However, it is still at its original size.

---

### Post by Weidbrewer on 2010-03-21
I figured out what the problem was...right as I started rebuilding the RAID from scratch.  It *had* started creating the array, but I stupidly forgot about:

```
watch cat /proc/mdstat
```

...to see what it was doing.

---

