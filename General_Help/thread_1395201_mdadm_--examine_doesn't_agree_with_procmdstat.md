---
title: "mdadm --examine doesn't agree with /proc/mdstat"
date: 2010-01-31
forum: General Help
---

### Post by ljwobker on 2010-01-31
I have a running raid5 setup built from two 1TB hard drives (sda/sdb) each with a single large partition (sda1/sdb1) created.  Created the array with the normal:
```
mdadm -Cv /dev/md0 -n2 -l5 /dev/sda1 /dev/sdb1
```Then made sure the config file looks right...

```
root@lwobker-ubuntu:~# cat /etc/mdadm/mdadm.conf | egrep 'ARRAY|DEVICE'
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=2 UUID=a543ef4c:2d8d7803:85273533:fa24306c
```I reboot and everything seems to be working fine... /proc/mdstat looks exactly as I would expect it to:

```
root@lwobker-ubuntu:~# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
[B]md0 : active raid5 sdb1[2] sda1[0]
      966799552 blocks super 1.0 level 5, 64k chunk, algorithm 2 [2/2] [UU][/B]
```but when I go to --examine the components, I get something that looks different than what I expect.  The output here from both components says that there are 2 raid devices, but beside "Array Slot" and "Array State" it certainly appears as if there are THREE devices, one of which is always failed.  Maybe it's just a matter of me not entirely understanding the syntax/output of these commands, but I would have expected to not see the word "failed" anywhere in an array that (at least as far as I can tell) functioning normally.  

```
root@lwobker-ubuntu:~# mdadm --examine /dev/sd[ab]1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : e66345e7:358b5381:7b96014b:25e328f2
           Name : lwobker-ubuntu:0  (local to host lwobker-ubuntu)
  Creation Time : Sat Jan 30 18:58:29 2010
     Raid Level : raid5
**   Raid Devices : 2**

 Avail Dev Size : 1933599128 (922.01 GiB 990.00 GB)
     Array Size : 1933599104 (922.01 GiB 990.00 GB)
  Used Dev Size : 1933599104 (922.01 GiB 990.00 GB)
   Super Offset : 1933599384 sectors
          State : clean
    Device UUID : f1e2129f:71372f61:5f43664a:e5133789

    Update Time : Sun Jan 31 14:06:24 2010
       Checksum : 41e8a24a - correct
         Events : 19

         Layout : left-symmetric
     Chunk Size : 64K

[B]    Array Slot : 0 (0, failed, 1)
   Array State : Uu 1 failed
[/B]

/dev/sdb1:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : e66345e7:358b5381:7b96014b:25e328f2
           Name : lwobker-ubuntu:0  (local to host lwobker-ubuntu)
  Creation Time : Sat Jan 30 18:58:29 2010
     Raid Level : raid5
**   Raid Devices : 2**

 Avail Dev Size : 1933599128 (922.01 GiB 990.00 GB)
     Array Size : 1933599104 (922.01 GiB 990.00 GB)
  Used Dev Size : 1933599104 (922.01 GiB 990.00 GB)
   Super Offset : 1933599384 sectors
          State : clean
    Device UUID : 098aaf09:648ceafe:f6a602e5:fe69e4f4

    Update Time : Sun Jan 31 14:06:24 2010
       Checksum : 508a5808 - correct
         Events : 19

         Layout : left-symmetric
     Chunk Size : 64K

[B]    Array Slot : 2 (0, failed, 1)
   Array State : uU 1 failed
[/B]
```Does anyone know where these differences might be coming from?

---

### Post by falconindy on 2010-01-31
The output is correct. What surprises me is that mdadm allowed you to create a RAID device with less devices than you need for a level 5 array.

---

### Post by ljwobker on 2010-01-31
//scratches head -- this has been a long-standing question (argument?) among a group of us here.  Are 3+ devices *strictly* required for RAID5 operation?  My understanding was that raid5 was designed to store 1/Nth parity information on each drive... so in a strictly general sense, you could have two components: each one with half the parity information.

If what's above is correct, where does the extra slot in the array come from?  Slot #1 is listed as failed, but I can't see anywhere along the way that it should have created an array with any more than two slots... 

At no point anywhere along the line did any of the source code complain about this... if the existing mdadm code doesn't really support raid5 mode with <3 devices, is it worth requesting a code change to reject a "create" that only has two components listed?  Note that this is separate from creating a raid5 array with only two active devices and one spare or missing device... 

my original intent was to create a two-component raid5 array and then at some point grow it into a three-component array.  One could argue that the "right" way to do this is to just start with a RAID1 two-component array and then migrate to raid5, but my thinking was that just starting with --level=5 to begin with made more sense.

Who is the final source on this... Neil?

---

### Post by falconindy on 2010-01-31
RAID5 uses a minimum of 3 drives, setting aside one of them in order to maintain redundancy. That is, if one drive fails, the array continues in limp mode at reduced performance until the failed device is replaced. I suppose mdadm allowed you to create the array with 2 drives and immediately forced it into limp mode, which is why you see a "missing" 3rd drive, and this is why the device actually "works".

[http://en.wikipedia.org/wiki/RAID#RAID_5](http://en.wikipedia.org/wiki/RAID#RAID_5)

---

### Post by ljwobker on 2010-01-31
Hrm... I was thinking along the same lines, but then I tried creating a more "legitimate" array using three devices from the very beginning.  (I've moved to using ghost/loopback filesystems for my testing instead of real drives... ain't virtualization great?)

First, I create a 3-component array using the default v0.90 metadata...
```
mdadm -Cv /dev/md0 -n3 -l5 /dev/loop[123]
```Then for comparison I create another 3-component array but this one is with the v1.0 metadata...
```
mdadm -Cv /dev/md1 -n3 -l5 -e1 /dev/loop[456]
```the v0.90 one doesn't show me any kind of failed device when I do an examine on it...
```

lwobker-ubuntu:/dev# mdadm --examine /dev/loop1
/dev/loop1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 48fd3492:2ca9586a:85273533:fa24306c (local to host lwobker-ubuntu)
  Creation Time : Sun Jan 31 20:54:42 2010
     Raid Level : raid5
  Used Dev Size : 10176 (9.94 MiB 10.42 MB)
     Array Size : 20352 (19.88 MiB 20.84 MB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jan 31 20:55:34 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 34ead325 - correct
         Events : 18

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       7        1        0      active sync   /dev/loop1

   0     0       7        1        0      active sync   /dev/loop1
   1     1       7        2        1      active sync   /dev/loop2
   2     2       7        3        2      active sync   /dev/loop3
```but when I look at the v1.0 array component, there is a failed device listed:

```
lwobker-ubuntu:/dev# mdadm -E /dev/loop4
/dev/loop4:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 0d7e851c:90e343cf:eb722f4d:52929ae9
           Name : lwobker-ubuntu:1  (local to host lwobker-ubuntu)
  Creation Time : Sun Jan 31 20:55:04 2010
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 20456 (9.99 MiB 10.47 MB)
     Array Size : 40704 (19.88 MiB 20.84 MB)
  Used Dev Size : 20352 (9.94 MiB 10.42 MB)
   Super Offset : 20464 sectors
          State : clean
    Device UUID : 9596b79f:6790c3d4:0aea6cfe:96422046

    Update Time : Sun Jan 31 20:56:10 2010
       Checksum : 4b2a18df - correct
         Events : 19

         Layout : left-symmetric
     Chunk Size : 64K

    Array Slot : 0 (0, 1, failed, 2)
   Array State : Uuu 1 failed
```Right now my best guess (and it's only that...) is that something about superblock 1.0 arrays will always build-in a "failed" device... I tried creating a 4-component array and I get this:

```
lwobker-ubuntu:/dev# mdadm --examine /dev/loop1 | grep Array
     Array UUID : 04335b1f:26ad659b:124d85ed:62fd9b48
     Array Size : 61056 (29.82 MiB 31.26 MB)
    Array Slot : 0 (0, 1, 2, failed, 3)
   Array State : Uuuu 1 failed

```and if I create a five-component array the same pattern:

```
lwobker-ubuntu:/dev# mdadm --examine /dev/loop1 | grep Array
     Array UUID : 2790f512:309ae031:04158100:fc28b273
     Array Size : 81408 (39.76 MiB 41.68 MB)
    Array Slot : 0 (0, 1, 2, 3, failed, 4)
   Array State : Uuuuu 1 failed
```

so **something **in there wants to create that failed component... I'm just not sure what or exactly why.

---

### Post by falconindy on 2010-01-31
HMMMM. The plot thickens. I can't recreate this behavior, but I'm also using a newer version of the mdadm utility because my man page says 1.0 is the default.
```
$ mdadm -V
mdadm - v3.1.1 - 19th November 2009
```

Here's a v.9 array:
```
/dev/loop4:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 8dde79be:f253cbb7:3aae4e5c:efa5d843 (local to host mabase)
  Creation Time : Sun Jan 31 17:08:24 2010
     Raid Level : raid5
  Used Dev Size : 19968 (19.50 MiB 20.45 MB)
     Array Size : 39936 (39.01 MiB 40.89 MB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Sun Jan 31 17:08:25 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : ea8608a2 - correct
         Events : 17

         Layout : left-symmetric
     Chunk Size : 512K

      Number   Major   Minor   RaidDevice State
this     0       7        4        0      active sync   /dev/loop4

   0     0       7        4        0      active sync   /dev/loop4
   1     1       7        5        1      active sync   /dev/loop5
   2     2       7        6        2      active sync   /dev/loop6
```

And the 1.1 array...
```
/dev/loop1:
          Magic : a92b4efc
        Version : 1.1
    Feature Map : 0x0
     Array UUID : ed9feba0:46fc9ef1:57fbeaf6:48008b3a
           Name : mabase:0  (local to host mabase)
  Creation Time : Sun Jan 31 17:06:26 2010
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 40944 (20.00 MiB 20.96 MB)
     Array Size : 79872 (39.01 MiB 40.89 MB)
  Used Dev Size : 39936 (19.50 MiB 20.45 MB)
    Data Offset : 16 sectors
   Super Offset : 0 sectors
          State : clean
    Device UUID : 206e5e21:44fdf305:851385e5:1169f78b

    Update Time : Sun Jan 31 17:06:27 2010
       Checksum : 2e68d50a - correct
         Events : 14

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)
```

And it'll happily make me a 5 device array as well.
```
     Array UUID : 1e9ba9d0:8f7f27eb:cc2c6594:f2712abf
     Array Size : 159744 (78.01 MiB 81.79 MB)
   Array State : AAAAA ('A' == active, '.' == missing)
```
I has no idea whatsoever on how to interpret the A v. U symbols in the 1.1 metadata but it's gotta be related. A little bit of Googling around shows that you're not the only one baffled by this behavior. Perhaps faulty behavior in the older mdadm release?

P.S. I had no prior knowledge of the 'losetup' program. That is insanely nifty... I see many broken btrfs formatted loopbacks in my future.

---

### Post by ljwobker on 2010-02-01
so in the v 0.90 show commands, a capital "U" is something like "this is me, and I'm 'up' ..."

a lowercase 'u' is something like " this device is up, but it's not me " -- then you have underscores or spaces for missing drives and a number indication of the failed devices.

Methinks that 3.1.1 should be in my future soon with 1.1 metadata and hopefully things will be much more sensikal after that.

And yes, losetup and image-file based devices are uber uber cool.  My next goal (maybe tomorrow?) is to build an array out of loopbacks bound to image files, then copy those image files over to a different machine, set up corresponding loop devices there, and see if I can correctly re-assemble the array with and without the superblocks...mainly proving to myself that no matter what the status of various superblocks/etc, as long as I have (N-1) readable disks from my array I will be able to get my data back.

I lost my main backup array a few months ago, and I'm pretty sure it's because I wasn't really sure how mdadm worked.  that mistake AIN'T GONNA HAPPEN again.  ;-)

---

### Post by ljwobker on 2010-02-01
> **falconindy said:**
> P.S. I had no prior knowledge of the 'losetup' program. That is insanely nifty... I see many broken btrfs formatted loopbacks in my future.

On this topic.. I'm pretty sure you already know that /dev/shm is just a block of RAM that you can do pretty much whatever you want with.  So if you have a machine with a lot of RAM in it, you can create your image files for losetup in here... and then you basically get a bunch of ramdisks that look like regular block devices that you can build all your "fake" drives on.  Needless to say that if you keep it all in memory (instead of doing it on actual physical disks) all your operations like building/resizing/destroying/syncing raid-arrays or other filesystems becomes screaming-fast... be aware that if you try to allocate more RAM than is allowed things may not work so smoothly, but it's a really really fast way to test things.

Examples for anyone who may stumble across this...

```
# create a 100MB all-zeros "image file" in RAM:  (1024 * 1024 is 1MB, so 100 of those)
dd if=/dev/zero of=/dev/shm/img0 bs=1024 count=102400
# use "losetup -f" to tell us what the next available loop device is
losetup -f
# in my case it was loop3, so we build /dev/loop3 on the image file from before...
losetup /dev/loop3 /dev/shm/img0
# now we have /dev/loop3, which we can build a filesystem on
mkfs.ext4 /dev/loop3
# because this is all in memory, it's SCREAMING fast...
# now we just mount this somewhere...
#    in my case, /var/vd0 -- "vd0" is my lingo for "virtual drive zero")
mount /dev/loop3 /var/vd0
```

---

