---
title: "RAID 6 .. Working but why?"
date: 2012-01-27
forum: General Help
---

### Post by Silicon Knight on 2012-01-27
[SIZE="1"]Linux AR-NAS 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux[/SIZE]

So, I upgraded from 10.04 -> 11.10.  Originally I was having an issue where when I booked I would get the usual degraded RAID message but I could boot into Ubuntu and assemble.

To go back a slight bit, when I installed 11.10 I forgot to hit advanced so it tried to install GRUB on one of my RAID drive (i wish it would default tot he drive you installed Ubuntu on).

The error message prevented boot and was annoying so I went to find a solution.  Not much helped but I did upgrade MDADM, then it all hit the fan, it said all of my superblocks were wiped.  I thought odd, so I went back to the default MDADM 3.1.4.  Now everything works.

But why?  So if I check
```
$ sudo mdadm /dev/md0 --examine
mdadm: No md superblock detected on /dev/md0
```

Also blkid

```
$ sudo blkid
/dev/sda1: UUID="dbc177fc-3ea1-b5de-47c8-a34029e9aa0a" UUID_SUB="18403661-1d25-ee9e-7445-a64b36bdf774" LABEL=":STORAGE" TYPE="linux_raid_member" 
/dev/sdb1: UUID="dbc177fc-3ea1-b5de-47c8-a34029e9aa0a" UUID_SUB="085b2491-c1d3-3c3b-89a2-b9a0f4767c2f" LABEL=":STORAGE" TYPE="linux_raid_member" 
/dev/sdc: UUID="dbc177fc-3ea1-b5de-47c8-a34029e9aa0a" UUID_SUB="09820f1d-2299-7ce7-0f29-30a07e3c05ab" LABEL=":STORAGE" TYPE="linux_raid_member" 
/dev/sdd1: UUID="d3f962ea-4629-4349-a879-5ef27db724d6" TYPE="ext4" 
/dev/sdd5: UUID="7b81d4c5-863f-4839-a87d-736ebbf0b266" TYPE="swap" 
/dev/sde1: UUID="dbc177fc-3ea1-b5de-47c8-a34029e9aa0a" UUID_SUB="20332d0a-3ba0-b43a-7365-0ff7a3781d96" LABEL=":STORAGE" TYPE="linux_raid_member" 
/dev/sdf1: UUID="dbc177fc-3ea1-b5de-47c8-a34029e9aa0a" UUID_SUB="cb532086-b58a-ec92-c822-35c30c664116" LABEL=":STORAGE" TYPE="linux_raid_member" 
/dev/sdg1: UUID="dbc177fc-3ea1-b5de-47c8-a34029e9aa0a" UUID_SUB="950803c5-01d5-0162-8e83-2ee690851459" LABEL=":STORAGE" TYPE="linux_raid_member" 
/dev/sdh1: UUID="dbc177fc-3ea1-b5de-47c8-a34029e9aa0a" UUID_SUB="84a0a0d7-b3b0-6ae9-e2ff-9d5b18e35ee3" LABEL=":STORAGE" TYPE="linux_raid_member" 
/dev/sdi1: UUID="dbc177fc-3ea1-b5de-47c8-a34029e9aa0a" UUID_SUB="3cbc6ee5-34bb-6d81-45ce-cc7af3fd2ec1" LABEL=":STORAGE" TYPE="linux_raid_member" 
/dev/md0: LABEL="STORAGE" UUID="e768e4a4-7c7e-40b5-8300-9bc955829f7a" TYPE="ext4" 

```

Lastly mdstat

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sde1[5] sdf1[4] sdh1[2] sdi1[6] sdg1[3] sdb1[0] sda1[1] sdc[8]
      8787578880 blocks super 1.2 level 6, 1024k chunk, algorithm 2 [8/8] [UUUUUUUU]
      bitmap: 0/11 pages [0KB], 65536KB chunk

unused devices: <none>

```

Thoughts?  Is there anything I should worry about?

---

### Post by Silicon Knight on 2012-01-27
One more thing, I figured I would stop the md0 array and try assembling it with verbose to see whats going on.

Here is the output

```
$ sudo mdadm --assemble --scan -v
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdj1: Device or resource busy
mdadm: cannot open device /dev/sdj: Device or resource busy
mdadm: no RAID superblock on /dev/sdi
mdadm: no RAID superblock on /dev/sdh
mdadm: no RAID superblock on /dev/sdg
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde
mdadm: cannot open device /dev/sdd5: Device or resource busy
mdadm: no RAID superblock on /dev/sdd2
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdi1 is identified as a member of /dev/md/:STORAGE, slot 6.
mdadm: /dev/sdh1 is identified as a member of /dev/md/:STORAGE, slot 2.
mdadm: /dev/sdg1 is identified as a member of /dev/md/:STORAGE, slot 3.
mdadm: /dev/sdf1 is identified as a member of /dev/md/:STORAGE, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md/:STORAGE, slot 5.
mdadm: /dev/sdc is identified as a member of /dev/md/:STORAGE, slot 7.
mdadm: /dev/sdb1 is identified as a member of /dev/md/:STORAGE, slot 0.
mdadm: /dev/sda1 is identified as a member of /dev/md/:STORAGE, slot 1.
mdadm: added /dev/sda1 to /dev/md/:STORAGE as 1
mdadm: added /dev/sdh1 to /dev/md/:STORAGE as 2
mdadm: added /dev/sdg1 to /dev/md/:STORAGE as 3
mdadm: added /dev/sdf1 to /dev/md/:STORAGE as 4
mdadm: added /dev/sde1 to /dev/md/:STORAGE as 5
mdadm: added /dev/sdi1 to /dev/md/:STORAGE as 6
mdadm: added /dev/sdc to /dev/md/:STORAGE as 7
mdadm: added /dev/sdb1 to /dev/md/:STORAGE as 0
mdadm: /dev/md/:STORAGE has been started with 8 drives.
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdi: Device or resource busy
mdadm: cannot open device /dev/sdh: Device or resource busy
mdadm: cannot open device /dev/sdg: Device or resource busy
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdd2
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/md127
mdadm: cannot open device /dev/sdj1: Device or resource busy
mdadm: cannot open device /dev/sdj: Device or resource busy
mdadm: cannot open device /dev/sdi1: Device or resource busy
mdadm: cannot open device /dev/sdi: Device or resource busy
mdadm: cannot open device /dev/sdh1: Device or resource busy
mdadm: cannot open device /dev/sdh: Device or resource busy
mdadm: cannot open device /dev/sdg1: Device or resource busy
mdadm: cannot open device /dev/sdg: Device or resource busy
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: cannot open device /dev/sdd5: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdd2
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy

```

---

### Post by Silicon Knight on 2012-02-01
So I"ve tried a whole host of things to fix this.  I tried to recreate the array with --assume-clean and I've resynced the drives but same problem.

Anyone have any thoughts?  Every time I boot up it pauses and takes me into initramfs and then I can boot and assemble the drive.

Thoughts?

---

