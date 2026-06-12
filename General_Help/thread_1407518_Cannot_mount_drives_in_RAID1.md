---
title: "Cannot mount drives in RAID1"
date: 2010-02-15
forum: General Help
---

### Post by skooter on 2010-02-15
I tried setting up my own partition table which apparently didn't go well.

I have 1 compactflash-disk for linux and 2 hard drives for data which are set up for RAID1. But the RAID-drives doesn't get mounted.

This is my first RAID-setup so help appreciated :)

```
me@server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc3             1,7G  543M  1,1G  34% /
udev                  975M  228K  975M   1% /dev
none                  975M     0  975M   0% /dev/shm
none                  975M   44K  975M   1% /var/run
none                  975M     0  975M   0% /var/lock
none                  975M     0  975M   0% /lib/init/rw
/dev/sdc1             228M   20M  197M  10% /boot

```

fstab ...
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc3 during installation
UUID=808c4415-c2a7-4461-b2e7-55e673c260de /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=d5f4d34b-9994-4a2b-87eb-63e0ae7bf118 /boot           ext4    defaults        0       2
# swap was on /dev/sdc2 during installation
UUID=257431e8-9f66-425b-a582-2c1e5dc67150 none            swap    sw              0       0

/dev/md0        /mnt/data           auto    defaults        0       0

```

```
me@server:~$ cat /var/log/syslog | grep md
Feb 15 12:55:31 server kernel: [    1.080679] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Feb 15 12:55:31 server kernel: [    1.080687] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Feb 15 12:55:31 server kernel: [    2.134151] md: linear personality registered for level -1
Feb 15 12:55:31 server kernel: [    2.211445] md: multipath personality registered for level -4
Feb 15 12:55:31 server kernel: [    2.286977] md: raid0 personality registered for level 0
Feb 15 12:55:31 server kernel: [    2.490573] md: raid1 personality registered for level 1
Feb 15 12:55:31 server kernel: [    3.269228] md: raid6 personality registered for level 6
Feb 15 12:55:31 server kernel: [    3.269236] md: raid5 personality registered for level 5
Feb 15 12:55:31 server kernel: [    3.269241] md: raid4 personality registered for level 4
Feb 15 12:55:31 server kernel: [    3.340861] md: raid10 personality registered for level 10
Feb 15 12:55:31 server kernel: [    3.360962] md: bind<sdb5>
Feb 15 12:55:31 server kernel: [    3.563052] md: bind<sda5>
Feb 15 12:55:31 server kernel: [    3.566951] raid1: md0 is not clean -- starting background reconstruction
Feb 15 12:55:31 server kernel: [    3.566960] raid1: raid set md0 active with 2 out of 2 mirrors
Feb 15 12:55:31 server kernel: [    3.567024] md0: detected capacity change from 0 to 750153629696
Feb 15 12:55:31 server kernel: [    3.571178]  md0:
Feb 15 12:55:31 server kernel: [    3.571332] md: resync of RAID array md0
Feb 15 12:55:31 server kernel: [    3.571338] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Feb 15 12:55:31 server kernel: [    3.571344] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Feb 15 12:55:31 server kernel: [    3.571353] md: using 128k window, over a total of 732571904 blocks.
Feb 15 12:55:31 server kernel: [    3.571359] md: resuming resync of md0 from checkpoint.
Feb 15 13:16:35 server mdadm[798]: Rebuild40 event detected on md device /dev/md0
Feb 15 13:29:07 server kernel: [    1.080952] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Feb 15 13:29:07 server kernel: [    1.080959] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Feb 15 13:29:07 server kernel: [    2.286213] md: linear personality registered for level -1
Feb 15 13:29:07 server kernel: [    2.422325] md: multipath personality registered for level -4
Feb 15 13:29:07 server kernel: [    2.486595] md: raid0 personality registered for level 0
Feb 15 13:29:07 server kernel: [    2.520296] md: raid1 personality registered for level 1
Feb 15 13:29:07 server kernel: [    2.636722] md: bind<sda5>
Feb 15 13:29:07 server kernel: [    3.345042] md: raid6 personality registered for level 6
Feb 15 13:29:07 server kernel: [    3.345050] md: raid5 personality registered for level 5
Feb 15 13:29:07 server kernel: [    3.345056] md: raid4 personality registered for level 4
Feb 15 13:29:07 server kernel: [    3.347466] md: bind<sdb5>
Feb 15 13:29:07 server kernel: [    3.360411] raid1: md0 is not clean -- starting background reconstruction
Feb 15 13:29:07 server kernel: [    3.360420] raid1: raid set md0 active with 2 out of 2 mirrors
Feb 15 13:29:07 server kernel: [    3.360477] md0: detected capacity change from 0 to 750153629696
Feb 15 13:29:07 server kernel: [    3.363909] md: resync of RAID array md0
Feb 15 13:29:07 server kernel: [    3.363919] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Feb 15 13:29:07 server kernel: [    3.363925] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Feb 15 13:29:07 server kernel: [    3.363935] md: using 128k window, over a total of 732571904 blocks.
Feb 15 13:29:07 server kernel: [    3.363940] md: resuming resync of md0 from checkpoint.
Feb 15 13:29:07 server kernel: [    3.381892]  md0:
Feb 15 13:29:07 server kernel: [    3.392373] md: raid10 personality registered for level 10
Feb 15 16:10:52 server kernel: [    1.080848] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Feb 15 16:10:52 server kernel: [    1.080856] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Feb 15 16:10:52 server kernel: [    2.475464] md: linear personality registered for level -1
Feb 15 16:10:52 server kernel: [    2.508915] md: multipath personality registered for level -4
Feb 15 16:10:52 server kernel: [    2.532781] md: raid0 personality registered for level 0
Feb 15 16:10:52 server kernel: [    2.559833] md: raid1 personality registered for level 1
Feb 15 16:10:52 server kernel: [    2.644241] md: bind<sda5>
Feb 15 16:10:52 server kernel: [    3.332530] md: bind<sdb5>
Feb 15 16:10:52 server kernel: [    3.346588] raid1: raid set md0 active with 2 out of 2 mirrors
Feb 15 16:10:52 server kernel: [    3.346652] md0: detected capacity change from 0 to 750153629696
Feb 15 16:10:52 server kernel: [    3.350789]  md0:
Feb 15 16:10:52 server kernel: [    3.352101] md: raid6 personality registered for level 6
Feb 15 16:10:52 server kernel: [    3.352108] md: raid5 personality registered for level 5
Feb 15 16:10:52 server kernel: [    3.352114] md: raid4 personality registered for level 4
Feb 15 16:10:52 server kernel: [    3.382661] md: raid10 personality registered for level 10
Feb 15 16:27:39 server kernel: [ 1011.842610] EXT4-fs (md0): VFS: Can't find ext4 filesystem
```

sda and sdb are the RAID-drives...

```

me@server:~$ dmesg |grep sda
[    1.285524] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.285598] sd 0:0:0:0: [sda] Write Protect is off
[    1.285605] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.285644] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.285865]  sda: sda1 < sda5 >
[    1.300283] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.644241] md: bind<sda5>
me@server:~$ dmesg |grep sdb
[    1.300308] sd 0:0:1:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.300377] sd 0:0:1:0: [sdb] Write Protect is off
[    1.300384] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.300421] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.300620]  sdb: sdb1 < sdb5 >
[    1.316071] sd 0:0:1:0: [sdb] Attached SCSI disk
[    3.332530] md: bind<sdb5>
me@server:~$ dmesg |grep sdc
[    1.496780] sd 1:0:0:0: [sdc] 7962192 512-byte logical blocks: (4.07 GB/3.79 GiB)
[    1.496853] sd 1:0:0:0: [sdc] Write Protect is off
[    1.496860] sd 1:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.496899] sd 1:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    1.497120]  sdc: sdc1 sdc2 sdc3
[    1.498353] sd 1:0:0:0: [sdc] Attached SCSI disk
[    3.810657] EXT4-fs (sdc3): barriers enabled
[    3.815474] kjournald2 starting: pid 333, dev sdc3:8, commit interval 5 seconds
[    3.815500] EXT4-fs (sdc3): delayed allocation enabled
[    3.815813] EXT4-fs (sdc3): mounted filesystem with ordered data mode
[    4.363504] Adding 1951888k swap on /dev/sdc2.  Priority:-1 extents:1 across:1951888k
[    4.698372] EXT4-fs (sdc3): internal journal on sdc3:8
[    5.490251] EXT4-fs (sdc1): barriers enabled
[    5.491963] kjournald2 starting: pid 591, dev sdc1:8, commit interval 5 seconds
[    5.542362] EXT4-fs (sdc1): internal journal on sdc1:8
[    5.542375] EXT4-fs (sdc1): delayed allocation enabled
[    5.543084] EXT4-fs (sdc1): mounted filesystem with ordered data mode

```

---

### Post by skooter on 2010-02-15
Found this in the log (notice "unknown partition table") ...
```
[    3.332530] md: bind<sdb5>
[    3.346588] raid1: raid set md0 active with 2 out of 2 mirrors
[    3.346652] md0: detected capacity change from 0 to 750153629696
[    3.350789]  md0:
[    3.352101] md: raid6 personality registered for level 6
[    3.352108] md: raid5 personality registered for level 5
[    3.352114] md: raid4 personality registered for level 4
[    3.353830]  **unknown partition table**
[    3.382661] md: raid10 personality registered for level 10

```

Then i did
```
sudo mkfs -t ext4 /dev/md0
```

Now it works.

---

### Post by skooter on 2010-02-16
Hmm I was too fast...

The size of det partition is incorrect - it should be 750 GB, but it's 688 GB:
```
me@server:~$ df -h | grep home
/dev/md0              688G   44G  609G   7% /home
```

fdisk gives error, but shows correct size:
```
skooter@NASty:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000942ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001    5  Extended
/dev/sda5               1       91201   732571969+  fd  Linux raid autodetect

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003caaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001    5  Extended
/dev/sdb5               1       91201   732571969+  fd  Linux raid autodetect

Disk /dev/sdc: 4076 MB, 4076642304 bytes
255 heads, 63 sectors/track, 495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x001c2022

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          30      240943+  83  Linux
/dev/sdc2              31         273     1951897+  82  Linux swap / Solaris
/dev/sdc3             274         495     1783215   83  Linux

Disk /dev/md0: 750.2 GB, 750153629696 bytes
2 heads, 4 sectors/track, 183142976 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

Also theres a /dev/sda1 anad /dev/sda5 (sdb for the other drive) for both drives. Does this look correct to you?

Pyuh... soon I'm going for a reinstall :neutral:

---

### Post by skooter on 2010-02-18
After reinstalling with XFS (instead of ext4) "df" now reports 699 GB. That's about 10 GB extra. But I still need 50 GB.

I'm wondering if there's an issue with the df command? Like this guy ...
[http://forums.debian.net/viewtopic.php?f=10&t=48365](http://forums.debian.net/viewtopic.php?f=10&t=48365)

---

### Post by skooter on 2010-02-19
Still talking to myself :p

Anyway, after re-thinking this i guess it's a taste of calulation

**fdisk** tells that 750156374016 bytes is equal to 750.2 GB which is correct if you: 750156374016 / (1000 * 3) = 750

**df** tells that 750156374016 bytes is equal to 699 GB which is correct if you: 750156374016 / (1024 * 3) = 698,6

Now the question is why are the calculating diffrently? I think the last method would be the correct one. Though i see the reason for the first method from a sales point of view ;)

---

