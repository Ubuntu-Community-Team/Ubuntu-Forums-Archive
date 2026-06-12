---
title: "Raid5 problems after upgrade to 12.04"
date: 2012-09-11
forum: General Help
---

### Post by oldschl on 2012-09-11
I'm totally lost here, and I hope I haven't already destroyed TB's worth of data.  I have a SoftwareRaid5 4 disk system.  I recently upgraded from 11.02 to 12.04 LTS, but I never shutdown my server (Ubuntu server).  I recently went on vacation and did a shutdown, but now that I'm back, I turned on the machine and I received an error that looked like one of the drives on the server were "removed" from the RAID.  It may or may not be related to [http://neil.brown.name/blog/20120615073245#4](http://neil.brown.name/blog/20120615073245#4).
So, when I boot, I am kicked into the initramfs prompt.  I tried unsuccessfully to re-add the drive to the RAID.  You can see that /dev/sdc3 has been removed.
```
  sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Jul 11 23:17:13 2011
     Raid Level : raid5
     Array Size : 8782299648 (8375.45 GiB 8993.07 GB)
  Used Dev Size : 2927433216 (2791.82 GiB 2997.69 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Tue Sep 11 12:57:00 2012
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : barta-fileserve:0  (local to host barta-fileserve)
           UUID : 08ec77fd:bb48c57e:af1ac842:c61ecce2
         Events : 1467508

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       0        0        2      removed
       3       8       51        3      active sync   /dev/sdd3

```I tried to mdadm --stop, mdadm --remove and then mdadm --create using 
```
   mdadm --create /dev/md0 --assume-clean --level=5 --raid-disk=4 --chunk 512 --metadata=1.2 /dev/sda3 /dev/sb3 missing /dev/sdd3

```But I get an error that sdd3 is an ex2fs filesystem and it appears as if the raid is not working.  It could be because of the way the drive is setup (it was working before I left).  Here is the parted print from the offending drive:  
```
Number  Start   End     Size    File system     Name        Flags
 1      17.4kB  200MB   200MB   ext4            ext4        boot
 2      200MB   2900MB  2700MB  linux-swap(v1)  linux-swap
 3      2900MB  3001GB  2998GB  ext4            ext4        raid

```So, I tried zeroing out the superblocks of the drives to see if I could then recreate the raid.  It looks as if the raid is active, but when I exit from initramfs, it says that it couldn't mount md0 (I take it because the new UUID for the RAID is different from the old mdadm.conf??).  So, I tried mdadm -Es | grep md0 >> /etc/mdadm/mdadm.conf, but this is getting me nowhere (doesn't work), and I'm afraid that I'm digging myself a deeper hole.
I would appreciate if I could get some assistance, and I hope I haven't destroyed my RAID and the data it contains.  The point of creating a RAID is for data redundancy and I don't want to lose my data.  I have had a hell of a time getting this thing operable.  Please help!!!

---

### Post by oldschl on 2012-09-11
I see that it MAY be possible to recover, but I'm having a hard time getting anywhere on this.  I tried to use a LiveCD to boot from, and it is kicking me out to initramfs as well because it sees a recreated RAID, but because of the problems I'm having it doesn't allow me to boot to Ubuntu.

---

### Post by oldschl on 2012-09-20
After completely trashing my software RAID5 system, and a week of attempted recovery, my Ubuntu experimentation days are done.  Just too much of a headache.  Probably shouldn't have used Ubuntu server in the first place, but I'm disappointed that Ubuntu and this forum have let me down.  So much potential, but not if errors like this make me lose 9TB worth of data.
I'm going to have to start from scratch using Win7 server and use some recovery software to see if I can get something back.  My recommendation - unless you're a sysadmin and are willing to spend hours upon hours troubleshooting and waiting for answers from a non-existent community, save yourself the time and go with another OS.

---

### Post by SaturnusDJ on 2012-09-23
Linux/mdadm can be difficult, especially when things don't go well, but if you know what you are doing (and always backup data) it's very very powerful.

If you have the data still untouched: Maybe you can boot into the OS first before attaching the hard drives.

---

### Post by Dapilot1 on 2012-10-29
Hey dunno if you have left, but I'm having a similar problem.

End of last week bad blocks through me into this loop.
fsck seems fine (2.4% non-contiguous)
badblocks had 124 errors all at the end
SMART believed there was 188 bad sectors

Since it is raid5, I have been able to still get my data with the one drive removed. In the long run I plan to remove the offending drive out, add another as a spare, sync, and activate. In 12.04, the disk utility had a tool for doing this easily through a gui, but in 12.10 it doesn't appear to have as much functionality.

---

