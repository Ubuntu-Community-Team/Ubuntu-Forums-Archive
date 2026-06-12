---
title: "Software RAID fails after reboot (Ubuntu 9.10)"
date: 2010-04-02
forum: General Help
---

### Post by sobeck on 2010-04-02
I set up a 4 disk RAID 5 arry using the Palimpsest utility several months ago, and all was well until last week. After a hard reboot, the RAID array failed to come up with the message:

Failed activating drive: Error assembling array: mdadm exited with exit code 1: mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted

The disk in question was still visible in Palimpsest, and the test utility succeeded. After searching the archives, I checked /proc/mdstat to see if another array had possession of the device. No such luck. I looked in syslog and found this, but don't know how to proceed:

Mar 28 08:42:26 david-phenom kernel: [   61.297959] md: md0 stopped.
Mar 28 08:42:26 david-phenom kernel: [   61.418841] md: bind<sdc1>
Mar 28 08:42:26 david-phenom kernel: [   61.424179] md: bind<sdb1>
Mar 28 08:42:26 david-phenom kernel: [   61.424384] md: bind<sda1>
Mar 28 08:42:26 david-phenom kernel: [   61.424543] md: bind<sdd1>
Mar 28 08:42:26 david-phenom kernel: [   61.424555] md: kicking non-fresh sda1 from array!
Mar 28 08:42:26 david-phenom kernel: [   61.424563] md: unbind<sda1>
Mar 28 08:42:26 david-phenom kernel: [   61.463793] md: export_rdev(sda1)
Mar 28 08:42:26 david-phenom kernel: [   61.482061] raid5: device sdd1 operational as raid disk 0
Mar 28 08:42:26 david-phenom kernel: [   61.482063] raid5: device sdb1 operational as raid disk 2
Mar 28 08:42:26 david-phenom kernel: [   61.482065] raid5: device sdc1 operational as raid disk 1
Mar 28 08:42:26 david-phenom kernel: [   61.482312] raid5: allocated 4280kB for md0
Mar 28 08:42:26 david-phenom kernel: [   61.482514] raid5: raid level 5 set md0 active with 3 out of 4 devices, algorithm 2
Mar 28 08:42:26 david-phenom kernel: [   61.482517] RAID5 conf printout:
Mar 28 08:42:26 david-phenom kernel: [   61.482518]  --- rd:4 wd:3
Mar 28 08:42:26 david-phenom kernel: [   61.482519]  disk 0, o:1, dev:sdd1
Mar 28 08:42:26 david-phenom kernel: [   61.482521]  disk 1, o:1, dev:sdc1
Mar 28 08:42:26 david-phenom kernel: [   61.482522]  disk 2, o:1, dev:sdb1
Mar 28 08:42:26 david-phenom kernel: [   61.505312] md0: bitmap initialized from disk: read 27/27 pages, set 270667 bits
Mar 28 08:42:26 david-phenom kernel: [   61.505315] created bitmap (420 pages) for device md0
Mar 28 08:42:26 david-phenom mdadm[1525]: NewArray event detected on md device /dev/md0
Mar 28 08:42:26 david-phenom kernel: [   61.527620] md0: detected capacity change from 0 to 5404575989760
Mar 28 08:42:26 david-phenom kernel: [   61.527998]  md0: unknown partition table

I would appreciate any help. I had not changed anything in the RAID definition. I had probably installed recommended updates.

---

### Post by gzarkadas on 2010-04-06
Just a few hints to start, since I cannot claim expertise in raid data recovery:

From what I figure seeing the mdadm's message and log entries:

[LIST=1]
[*]One of the raid disks is out-of-sync and thus not used (sda1). So, your raid starts with one failed disk.
[*]Another disk (sdb1) is unusable because of bad superblock. So your raid has two of 4 disks out and you have entered into the realm of data loss.
[/LIST]
Thus, first of all do not use your disks until you finalise a plan on how to recover; just another error may make this impossible or just too much of a pain to be worth of it. 

Depending on the filesystem used on the disks, you may be able to use a backup of the superblock and recover sdb1. See [http://www.linfo.org/superblock.html](http://www.linfo.org/superblock.html) and also try to google with terms `linux <your type of filesystem> superblock recovery' to find additional resources.

If you make it, then promptly resync sda1 so that you have 4 disks in your raid; just 3 disks do not provide fault tolerance.

If this don't work, try to google with terms `repair raid5 volume linux' to find additional resources. I have made it already and picked some. See for example:

[LIST]
[*][http://wiki.centos.org/TipsAndTricks/Repair_RAID5_Volumes](http://wiki.centos.org/TipsAndTricks/Repair_RAID5_Volumes)
[*][http://www.chiark.greenend.org.uk/~peterb/linux/raidextract/]("http://www.chiark.greenend.org.uk/%7Epeterb/linux/raidextract/")
[*][http://www.intelligentedu.com/how_to_recover_from_a_broken_raid5.html](http://www.intelligentedu.com/how_to_recover_from_a_broken_raid5.html)
[/LIST]
This is a more involved process and it is worth only if you have data on the raid that you care of. If it is just the os and some files that you can afford to loose or remake, then it will be easier to reformat and reinstall.

And by the way, always make backups; as you have seen already everything can fail - it is the only way to be on the safe side. Pick a backup suit that can be scripted (I use dar) make a few scripts that backup your data and system files and set-up suitable cron entries for them. If you use removable media for the backups, use zenity to prompt you with a dialog box to mount your media before the backup starts. And you are done; you will never again worry for such events.

---

