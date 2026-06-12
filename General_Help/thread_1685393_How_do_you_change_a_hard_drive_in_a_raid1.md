---
title: "How do you change a hard drive in a raid1"
date: 2011-02-10
forum: General Help
---

### Post by Bryan55 on 2011-02-10
Hi.
Some bad sectors have appeared in one of 2 hard drives and as it is still under warranty the supplier has agreed to replace it.

I think I need to say that my abilities are very limited. When I installed this raid1 I was completely new to linux and raid and it took me 3 goes at getting the partitions right but as it was a new install I had nothing to loss. I did it using an Alternate CD (Karmic) I have been look at some how tos but none seem to match my needs and now I have much more to lose so need to get it right.
I have backed up my home files.


Before I completely remove the faulty hdd I also need to delete (reformat) everything on it so I can send it back and not have anyone look at my details.
So I suppose the raid array has to be dismatled first. How please?
Then reformat.
Then when I get a new one back rebuild the array. Another How?

I would very much appreciate a simplish  walk through.

Thanks up front for any help.

Bryan

---

### Post by rubylaser on 2011-02-10
I'll assume this is an mdadm array.  If so, there's no reason to need to reformat after replacing the disk and uninstalling.  Can you provide more info?

```
cat /proc/mdstat
```
```
fdisk -l
```

And mention what drive is the bad one?

---

### Post by Bryan55 on 2011-02-10
Hi rubylaser
The reformatting is to delete all of my data from the faulty disc before I send it back.

Here is the result from the first. The second produced nothing
bryan@Bydand:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sda1[0]
      586240 blocks [2/2] [UU]
      
md2 : active raid1 sdb5[1] sda5[0]
      461916800 blocks [2/2] [UU]
      
md3 : active raid1 sdb6[1] sda6[0]
      6345536 blocks [2/2] [UU]
      
md1 : active raid1 sdb2[1] sda2[0]
      19534976 blocks [2/2] [UU]
      
unused devices: <none>
bryan@Bydand:~$ 

Bryan

PS bad HDD  /dev/sdb
b

---

### Post by rubylaser on 2011-02-10
Just so you know, your steps will be like this, if it's sdb that's at fault. The following is an example. You'll need to do this as superuser, so let's make you a superuser for the duration of this...
```
sudo -i
```

```
mdadm --manage /dev/md0 --fail /dev/sdb1
```
```
mdadm --manage /dev/md0 --remove /dev/sdb1
```

I'll assume since you mentioned "partitions" you have a few arrays on the disk, so you'll do that for all partitions...
```
mdadm --manage /dev/md1 --fail /dev/sdb2
```
```
mdadm --manage /dev/md1 --remove /dev/sdb2
```

```
mdadm --manage /dev/md2 --fail /dev/sdb5
```
```
mdadm --manage /dev/md2 --remove /dev/sdb5
```

```
mdadm --manage /dev/md3 --fail /dev/sdb6
```
```
mdadm --manage /dev/md3 --remove /dev/sdb6
```

Once you're done, shut down your machine, and replace the defective drive with a good one, then turn it back on.

Next, you'll want to copy the partitioning from the good disk to the new disk like this...
```
sfdisk -d /dev/sda | sfdisk /dev/sdb
```

Use fdisk -l to make sure that the two disks have the same partitioning at this point.
```
fdisk -l
```

Then, you just need to add the new disk back to the arrays...

```
mdadm --manage /dev/md0 --add /dev/sdb1
```
```
mdadm --manage /dev/md1 --add /dev/sdb2
```
```
mdadm --manage /dev/md2 --add /dev/sdb5
```
```
mdadm --manage /dev/md3 --add /dev/sdb6
```

Check everything with
```
cat /proc/mdstat
``` and once the sync is done, you'll be all set.  Just use dd to write zeros to your old drive so you can RMA it.

```
dd if=/dev/zero of=/dev/<old_drive> bs=1M
```

---

### Post by Bryan55 on 2011-02-10
I'm quite surprised that what you have put makes scene to me. (the jokes is on me)

Just 2 points.
1  the time between me taking out the faulty drive and getting the new one will be 10 days.      Will it be usable?

2  Whats this about?
      Just use dd to write zeros to your old drive so you can RMA it.

Bryan

Edit. Just to say I've marked this as solved as the rubylaser's instructions worked perfectly.

---

### Post by rubylaser on 2011-02-10
1. Yes, the array will be usable while you wait for your new one.  You just won't have redundancy, so you'll be running degraded.

2. You mentioned that you wanted to clean off your old drive before you send it back.  You can use dd to write zeroes over the whole disk, so you don't have to worry about someone else getting your data.

---

### Post by Bryan55 on 2011-02-10
Ok.
So in my case the code would be?

dd if=/dev/zero of=/dev/sdb bs=1M

Many thanks

Bryan

---

### Post by YesWeCan on 2011-02-10
[QUOTE=Bryan55]The second produced nothing[/quote]
fdisk must be run as root. Try sudo fdisk -l

dd is very obedient and very dangerous. It is crucial to get the disk dev name right or you will end up wiping the wrong disk. The dev name can change when you change what disks are connected, including external devices after a reboot. So use sudo fdisk -l to make sure you have got the disk dev names right. :)

Also, the dd can take a long time to finish, maybe an hour or more, and it gives no progress feedback whatsoever. The only way you will know it is doing something is from the disk drive light on you PC. It is also a good idea to unmount the drive first if it is mounted: sudo umount /dev/sdx

---

### Post by Bryan55 on 2011-02-11
Thank YesWeCan. 
I have posted the result below of that code. I will also  post later the result after removing sdb from the raid to see if the  name changes.(for completeness)

bryan@Bydand:~$ sudo fdisk -l
[sudo] password for bryan: 
Sorry, try again.
[sudo] password for bryan: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4857bf34

   Device      Boot        Start               End               Blocks      Id      System
/dev/sda1   *                     1                  73             586341      fd      Linux RAID autodetect
/dev/sda2                         74            2505        19535040      fd     Linux RAID autodetect
/dev/sda3                    2506         60801    468262620        5      Extended
/dev/sda5                   2506          60011    461916913+  fd       Linux RAID autodetect
/dev/sda6                60012          60801          6345643+  fd       Linux RAID autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000fff2

   Device       Boot           Start               End               Blocks       Id      System
/dev/sdb1   *                            1                 73              586341        fd       Linux RAID autodetect
/dev/sdb2                                74           2505       19535040       fd        Linux RAID autodetect
/dev/sdb3                          2506   60801    468262620         5        Extended
/dev/sdb5                          2506        60011     461916913+   fd         Linux RAID autodetect
/dev/sdb6                      60012         60801           6345643+   fd        Linux RAID autodetect

Disk /dev/md1: 20.0 GB, 20003815424 bytes
2 heads, 4 sectors/track, 4883744 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md3: 6497 MB, 6497828864 bytes
2 heads, 4 sectors/track, 1586384 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md0: 600 MB, 600309760 bytes
2 heads, 4 sectors/track, 146560 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 473.0 GB, 473002803200 bytes
2 heads, 4 sectors/track, 115479200 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table
bryan@Bydand:~$


Bryan.

---

