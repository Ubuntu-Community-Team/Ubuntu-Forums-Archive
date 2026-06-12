---
title: "Raid array slow to start/auto mount"
date: 2012-09-24
forum: General Help
---

### Post by golemcito on 2012-09-24
Hi everybody

First of all my apologies for reopen this thread, but i don´t know what to do...

I have an mdadm raid5 array. It seems it´s ok but when i try to mount it it takes about 2 minutes. I don´t know what to do, there are no errors in dmesg the file /proc/mdstat is ok...

The only thing i noticed is that not all the disks on the array have an UUID the array and 2 of 6 disks has the same UUID, the another 4 doesn´t show it.

Any clue?

Thanx in advance

---

### Post by oldos2er on 2012-09-24
Post moved to its own thread.

---

### Post by golemcito on 2012-09-25
Anyone have any ideas and or suggestions on this ?

Thanx

---

### Post by SaturnusDJ on 2012-09-26
So what does
```
blkid -o list

```
exactly say?

---

### Post by bomski on 2012-09-26
I also seem to be experiencing the same issue; last set of updates seems to have caused some issue where mounting RAID array takes a couple of minutes.

Prior to updates it mounted almost instantaneously..... will be interested to see if there is a solution to this; i'll check the blkid -o list output when i'm back at home and report back...

---

### Post by jxd on 2012-09-28
Having the same problem here, but, also had some other symptoms that may or may not be related!

At first, I found that disk utility was no longer showing the type of filesystem in any of my disks... things were seeming very strange, so, I re-installed Ubuntu 12.04 from scratch, allowed all the updates, then created a brand new RAID array (I happened to have everything backed up at that point in time). Disk utility now shows volumes normally again, however:

1) It takes 2 minutes or so to mount, I commented out the fstab altogether to keep this manual as it takes sooo long

2) Although I can create files on the mounted drive, the drive appears to be read-only in nautilus. All write-related content is grayed out, however, when I click on it, it still works! For example, create new folder option is grayed out, but I click on it, it still works!?

cat /proc/mdstat:
```

Personalities : [raid6] [raid5] [raid4] 
md0 : active raid6 sdj1[8] sdi1[7] sdh1[6] sdg1[5] sdf1[4] sde1[3] sdd1[2] sdc1[1] sdb1[0]
      20510934528 blocks super 1.2 level 6, 512k chunk, algorithm 2 [9/9] [UUUUUUUUU]
      
unused devices: <none>

```

blkid -o list
```

device                               fs_type       label          mount point                              UUID
------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                            ext4                         /                                        107a98ea-ba13-452b-9b5b-de2e1e0b78fe
/dev/sda5                            swap                         <swap>                                   37cf8fdb-1038-4bd0-ab32-b9053c44f82b
/dev/sdb1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/sdc1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/sde1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/sdf1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/sdd1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/sdg1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/sdh1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/sdi1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/sdj1                            linux_raid_member caveraid:0 (in use)                                 90634270-08e7-5acc-2e9f-b3e4beb24138
/dev/md0                             ext4          caveraid       /media/caveraid_                         860d691d-6ffc-4eff-94e6-32ddcfdd34a8

```

Can't shake this unstable feeling, things were working fine before updates!

[Edit] After rebooting, Nautilus now appears normal, the options are not greyed out anymore. However, the raid array still takes 2 minutes or so to mount.

---

### Post by bomski on 2012-09-29
Similar results here; nothing obvious from mdstat or blkid....

cat  /proc/mdstat:

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active (auto-read-only) raid5 sde1[3] sdd1[0] sdg1[1] sdf[4] sdc[6] sdb[5]
      9767564800 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/6] [UUUUUU]
      
unused devices: <none>

```blkid -o list:

```

device           fs_type  label     mount point          UUID
----------------------------------------------------------------------------------------------
/dev/sda1        ext4               /                    179600bb-d94d-4a9b-8477-7e20edfb8614
/dev/sda5        swap               <swap>               8aa55c3c-8c1e-4949-8777-c832afa76776
/dev/sdb         linux_raid_member :RAID Array (in use)  f2955339-e124-0dc9-de2d-0fff7e808229
/dev/sdc         linux_raid_member :RAID Array (in use)  f2955339-e124-0dc9-de2d-0fff7e808229
/dev/sdd1        linux_raid_member :RAID Array (in use)  f2955339-e124-0dc9-de2d-0fff7e808229
/dev/sde1        linux_raid_member :RAID Array (in use)  f2955339-e124-0dc9-de2d-0fff7e808229
/dev/sdf         linux_raid_member :RAID Array (in use)  f2955339-e124-0dc9-de2d-0fff7e808229
/dev/sdg1        linux_raid_member :RAID Array (in use)  f2955339-e124-0dc9-de2d-0fff7e808229
/dev/md127       ext4     Tumbler   (in use)             fc253373-9ccc-4fa0-9088-d943fb1492ac

```

Ze plot thickens...

---

### Post by bomski on 2012-10-02
UPDATE:

Bit of further digging seems to suggest that there is a bug in the current kernel; and it primarily affects ext4 large volume arrays:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054605](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1054605)

Hopefully a patch will be issued that will resolve this soon...

UPDATE 2: 

Seems upstream Kernel (3.6+) fixes mount issues; no sign of a fix in current kernel...

---

### Post by bomski on 2012-10-24
UPDATE 3:

Latest round of updates seems to have resolved all mount issues; hope this helps!

---

