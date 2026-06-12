---
title: "linux software raid / mdadm UUID problems"
date: 2009-12-31
forum: General Help
---

### Post by mdschiller on 2009-12-31
[FONT=Courier New]I upgraded the motherboard in my nas system today, and reinstalled
Ubuntu 9.10. There are 2 Linux software raid arrays in the system,
/dev/md0 which is comprised of 8 devices, and /dev/md1 which is
comprised of 2 devices. I can get mdadm to automatically assemble
/dev/md1 on boot, but it won't auto assemble /dev/md0. For some reason
(possibly because I had a 4 disk array with some of the same disks
years ago), mdadm finds two instances of /dev/md0. One is correctly
comprised of /dev/sd[abcdefgh]1, the other is incorrectly comprised of
/dev/sd[bc] and two missing devices:

mike@storage1:~$ sudo mdadm --examine --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=4
UUID=7aa116e9:6de51617:82eda4d1:8807c2ac
  devices=/dev/sdc,/dev/sdb
ARRAY /dev/md1 level=raid1 num-devices=2
UUID=5e4d8185:a0cc963f:796f3e2c:ec945a20
  devices=/dev/sde3,/dev/sda3
ARRAY /dev/md0 level=raid5 num-devices=8
UUID=afdf5b45:8b930e27:66ac6d52:07eb4ce7
  spares=1   devices=/dev/sdh1,/dev/sdg1,/dev/sdf1,/dev/sde1,/dev/sdd1,/dev/sdc1,/dev/sdb1,/dev/sda1

I'm not sure why these mis-marked partitions weren't a problem for me before.

When I use fdisk to look for partitions marked as Linux raid, I see
exactly what I would expect:
mike@storage1:~$ sudo fdisk -l |grep auto
/dev/sda1   *           1       36481   293033601   fd  Linux raid autodetect
/dev/sda3           36743       38913    17438557+  fd  Linux raid autodetect
/dev/sdb1   *           1       36481   293033601   fd  Linux raid autodetect
/dev/sdc1   *           1       36481   293033601   fd  Linux raid autodetect
/dev/sdd1               1       36481   293033601   fd  Linux raid autodetect
/dev/sde1   *           1       36481   293033601   fd  Linux raid autodetect
/dev/sde3           36743       38913    17438557+  fd  Linux raid autodetect
/dev/sdf1   *           1       36481   293033601   fd  Linux raid autodetect
/dev/sdg1   *           1       36481   293033601   fd  Linux raid autodetect
/dev/sdh1               1       36481   293033601   fd  Linux raid autodetect

Note that sd[ae]3 are part of /dev/md1

I can manually start the array with:
sudo mdadm --assemble --uuid=afdf5b45:8b930e27:66ac6d52:07eb4ce7
/dev/md0 , so I know the array is intact.

How do I get rid of the erroneous /dev/md0?  It looks like I may be
able to use the --zero-superblock option on /dev/sd[bc], but I value
the data on the array, and am wary of doing anything that could
jeopardize the data on /dev/sd[bc]1.

--Mike[/FONT]

---

