---
title: "how-to make a raid5 storage"
date: 2011-03-30
forum: General Help
---

### Post by Azyx on 2011-03-30
Hi. I Have 10.04 LTS
I want to make a more secure storage with 3 PATA 300GB disks. I think a raid5 is the best. I don't need to boot or have a system on the storage volumes.i have find some guides, but they are for raid on system-disk and make them bootable, and seems to be to complicated for me.

I have made ext4 volumes on them and flaged them as raid in gparted.

Cheers

---

### Post by tyleruk on 2011-03-30
Try this guide, it helped me a lot when I was setting up raid arrays:
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid+howto]("http://ubuntuforums.org/showthread.php?t=408461&highlight=raid+howto")

You should be able to setup your arrays on your separate drives and leave your system drive as is with something like:

> mdadm --create /dev/md0 --chunk=4 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdc1

---

### Post by Azyx on 2011-03-30
Thanx :)  I came a bit on the way, but get some problem to mount :(

I typed this, after checking the name on my ext4 formated 3 300GB hdd:s.

```
sudo mdadm --create /dev/md0 --chunk=4 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
```I get a respones for my hdds with sizes and that it says it was ext2 partitions. It asked if I wanted an array and I typed 'yes'

Then a 600GB disk appeares under meny 'Places'. When I click on the 600GB I get this popup error-message:

[SIZE=3][COLOR=DarkSlateGray]Unable to mount 600 GB Filesystem
[/COLOR][/SIZE][COLOR=DarkSlateGray]
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[SIZE=1]
[COLOR=Black]
I then typed  [/COLOR][/SIZE][/COLOR]```
dmesg | tail
```[COLOR=DarkSlateGray][SIZE=1]
[/SIZE][/COLOR]
And get:

```
Azyx@DasBlack:~$ dmesg | tail
[27010.879070]  --- rd:3 wd:2
[27010.879073]  disk 0, o:1, dev:sda1
[27010.879075]  disk 1, o:1, dev:sdb1
[27010.879077]  disk 2, o:1, dev:sdc1
[27010.890916] md: recovery of RAID array md0
[27010.890922] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[27010.890925] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[27010.890930] md: using 128k window, over a total of 293033536 blocks.
[27052.901803] EXT4-fs (md0): ext4_check_descriptors: Checksum for group 0 failed (4323!=0)
[27052.901815] EXT4-fs (md0): group descriptors corrupted!
Azyx@DasBlack:~$ 
```Any Ideas whats wrong?

Cheers

---

### Post by Azyx on 2011-04-01
Someone how know how I shut down raid-arrays, cos I cannot format or change partitions cos it say the disk are bussy? Will try other ways to fix a raid 5, but if I cannot do anything. I tried to shut down with disk utility.

---

### Post by Azyx on 2011-04-03
> **Azyx said:**
> Someone how know how I shut down raid-arrays, cos I cannot format or change partitions cos it say the disk are bussy? Will try other ways to fix a raid 5, but if I cannot do anything. I tried to shut down with disk utility.

I can't find how Ishould mount the RAID-array, but Ubuntu do it automagically. May ubuntu mount it wrong?

---

