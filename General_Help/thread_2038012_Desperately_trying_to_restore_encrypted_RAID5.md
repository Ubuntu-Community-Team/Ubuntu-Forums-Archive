---
title: "Desperately trying to restore encrypted RAID5"
date: 2012-08-05
forum: General Help
---

### Post by jstretch on 2012-08-05
I had a three-disk RAID5 array which died on me last night. It's a 3x2TB array which holds a single 4TB dm-crypt-encrypted partition. It's possible that one of the hard disks had failed, but of course the array should still work (given that that's the primary purpose of RAID).

Here's the current content of **/proc/mdstat**:

```

Sandbox ~ # cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[4](S) sdc1[0](S) sde[2](S)
      5860538368 blocks
       
unused devices: <none>

```**mdadm --detail /dev/md0** is no help:

```

Sandbox ~ # mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: md device /dev/md0 does not appear to be active.

```And **mdadm --examine --scan** is just confusing; why would it return two entries for the same array (md0)?

```

Sandbox ~ # mdadm --examine --scan
mdadm: metadata format 00.90 unknown, ignored.
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=7d40dd6f:225c034d:361c770a:4fd605be
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=7e55fc46:2d52af2d:361c770a:4fd605be
   spares=1

```I've tried re-assembling the array with **mdadm --assemble** but I end up with the same results. I'm at my wit's end trying to fix this and desperate for someone to point me in the right direction! Any help at all is greatly appreciated!

---

### Post by jstretch on 2012-08-05
I got as far as re-mounting the LUKS partition only to find that my valid passphrase was no longer recognized. I guess that's that. Never again I will trust anything to software RAID.

---

