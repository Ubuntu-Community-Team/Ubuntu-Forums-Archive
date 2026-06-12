---
title: "Ubuntu 10.10 mdadm RAID + moving device names"
date: 2011-03-25
forum: General Help
---

### Post by berto- on 2011-03-25
I'm having trouble with Ubuntu 10.10 and stable device names.  When I installed Ubuntu, the root drive was the only one in the machine; it obviously got [FONT="Courier New"]/dev/sda[/FONT].  After the base installation, I installed three additional 2TB drives to make RAID-5 array.  Ubuntu renamed the root drive to [FONT="Courier New"]/dev/sdd[/FONT].  While annoying I lived with it.

After creating a single partition set to "Linux raid autodetect" on each drive, I created the RAID-5 array:

```
mdadm --create /dev/md0 --level=raid5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1

```
All was going well until a reboot.  When rebooting Ubuntu decided to make the root drive /dev/sda this time and now [FONT="Courier New"]mdadm --detail /dev/md0[/FONT] reports:


```
    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed

```

Any ideas on how to fix the array and make the device names stable?

Thanks!

---

### Post by berto- on 2011-03-25
Some additional info from [FONT="Courier New"]/proc/mdstat[/FONT]:

```
root@raid:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[0] sdc1[1]
      3907023872 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      
md_d0 : inactive sdd1[3](S)
      1953511936 blocks
       
unused devices: <none>

```

I'm trying to figure out how to get [FONT="Courier New"]sdd1[/FONT] out of [FONT="Courier New"]md_d0[/FONT] and into [FONT="Courier New"]md0[/FONT], as well as how this even happens.

---

