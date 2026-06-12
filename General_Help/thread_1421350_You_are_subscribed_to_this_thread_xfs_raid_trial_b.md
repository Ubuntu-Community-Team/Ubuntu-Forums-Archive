---
title: "You are subscribed to this thread xfs raid: trial barrier write failed - is it xfs"
date: 2010-03-04
forum: General Help
---

### Post by maxw9 on 2010-03-04
Just set up a new "serious" MythTV backend with 4x1.5TB Samsung hdds to be set up as a raid6 with expansion planned to 6 hdds in my Silverstone LC17 box. 

I normally solve all my problems with google so this is my first post here... but long time reader.

My system: running Ubuntu 9.10 (Karmic) on an i5-750 quad core. This is not a fresh install, it is an Ubuntu 9.04 system, upgraded to 9.10 (Karmic), then copied from my old system to the new and running lilo (not grub2) to cope with a raid boot.

Over 4 drives, I wanted a 200MB ext3 raid1 /boot parition (/dev/md10), a 20GB ext3 raid6 partition (/dev/md6) for root, and a 2.9TB xfs raid6 partition (/dev/md8 ) for "storage" eg recordings, videos, music & photos. All partitions were initally installed as raid 1 over 2 drives (as I only had 2 new drives to begin with). I then acquired a further 2 drives and did an mdadm --grow to raid6 over 4 drives, using the latest mdadm 3.1 from [Converting RAID5 to RAID6 and other shape changing in md/raid]("http://neil.brown.name/blog/20090817000931") - this version 3.1 of mdadm allows growth of a raid 1 to raid 5/6 and growth of raid 5/6 to more disks.

*(In case you're wondering why raid6? Raid5 doesn't offer enough protection in a system I never want to go down - I've lost one Myth backend before due HDD failure and it took many weeks to get it back to how I had it! And raid10 is still not expandable - even under mdadm 3.1. Raid6 over 6 drives (my goal) is 66% space-efficient and can suffer two drive failures. I could even go to more drives in future.)*

Anyway, it all seemed to work perfectly - after reshaping (which took a couple of days), I was successfully running raid6 on 4 drives on both root and storage partitions until ... the system failed to shutdown cleanly... had to hard-reset... on reboot the xfs partition (/dev/md8 ) failed to mount and when I looked at the syslog it was reporting (prior to the shutdown event, hundreds of times):

```
"Filesystem "md8": xfs_log_force: error 5 returned."
```syslog was reporting during the boot phase (dozens of times):

```
 Filesystem "md8": Disabling barriers, trial barrier write failed
XFS mounting filesystem md8
Ending clean XFS mount for filesystem: md8
Starting XFS recovery on filesystem: md8 (logdev: internal)
Failed to recover EFIs on filesystem: md8
```I tried xfs_repair and it did successfully repair the filesystem but only after running xfs_repair -L (dump logfile - "some filesystem corruption may result"). No filesystem corruption was evident and I hoped this would be the end of my troubles but several hours later the machine froze - had to hard-reset again and md8 again failed to mount with the same messages in the syslog.

This time xfs_repair can't even get through stage 1 - it now reports:

```
$ sudo xfs_repair -n  /dev/md8
Phase 1 - find and verify superblock...
superblock read failed, offset 0, size 524288, ag 0, rval 0

fatal error -- Invalid argument
``````
$ cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid10] 

md8 : inactive sdc8[4](S) sdd8[0](S) sde8[1](S)
      4356152767 blocks super 1.2
       
md6 : active raid6 sdc6[4] sdd6[0] sdf6[3] sde6[1]
      19534592 blocks super 1.2 level 6, 128k chunk, algorithm 18 [4/4] [UUUU]
      
md10 : active raid1 sdd1[0] sdc1[3] sde1[1] sdf1[2]
      192640 blocks [4/4] [UUUU]
```In the above, md8 is the xfs partition, md6 is the ext3 root partition and md10 is a raid1 /boot partition.

I don't know what's going with on the the mdstat for md8 - I thought this was only an xfs issue but it appears that only 3 of the 4 drives have been recognised by mdadm and they are all listed as spares and the array is listed as inactive.

Now, it's fair to report that the computer was rebooted a few times during the raid1-raid6 reshaping and during this time about 900GB was copied from my old backup drive to the new array - maybe I overstressed what is a beta version of mdadm 3.1. I used exactly the same process to create md6 (root) and it hasn't missed a beat - but it also wasn't stressed with reboots and huge file activity during reshaping.

So I don't know if this is an mdadm 3.1 reshaping problem (the array seemed to be clean and working perfectly once reshaping had finished) or an xfs problem. I suspected an xfs problem but the mdstat reporting only 3 of the 4 drives has me suspicious now. I'm tempted to try re-creating the array as raid6 over 4 drives using only ext3 (forget xfs) and hopefully all problems will go away - but would love any clues as to the source of my problems - is it purely an xfs issue or is it an mdadm/raid issue?

Cheers, max

---

### Post by maxw9 on 2010-03-04
Further attempts to re-create the array:

```
$ sudo mdadm --examine /dev/md8
mdadm: No md superblock detected on /dev/md8.

$ sudo mdadm --detail /dev/md8
mdadm: md device /dev/md8 does not appear to be active.

$ sudo mdadm --assemble /dev/md8 /dev/sdd8 /dev/sde8 /dev/sdf8 /dev/sdc8
mdadm: cannot open device /dev/sdd8: Device or resource busy
mdadm: /dev/sdd8 has no superblock - assembly aborted

$ sudo mdadm --create /dev/md8 --level=6 --raid-devices=4 --chunk=8192 /dev/sdd8 /dev/sde8 /dev/sdf8 /dev/sdc8
mdadm: device /dev/sdd8 not suitable for any style of array

$ sudo mdadm --examine --scan /dev/sdd8
ARRAY /dev/md/8 metadata=1.2 UUID=8aab3137:53541c75:f77e666c:9731b8eb name=onigiri:8

$ sudo mdadm --examine --scan /dev/sdc8
ARRAY /dev/md/8 metadata=1.2 UUID=8aab3137:53541c75:f77e666c:9731b8eb name=onigiri:8

$ sudo mdadm --examine --scan /dev/sde8
ARRAY /dev/md/8 metadata=1.2 UUID=8aab3137:53541c75:f77e666c:9731b8eb name=onigiri:8

$ sudo mdadm --examine --scan /dev/sdf8

$ sudo mdadm /dev/md8 -f /dev/sdf8
mdadm: cannot get array info for /dev/md8
```So it appears the raid6 array is corrupt and /dev/sdf8 is the culprit (no superblock? it won't return a UUID) - but I can't even fail that drive and have it rebuild!?

I still can't help feeling that xfs is involved here but it also seems to be a raid problem.

---

