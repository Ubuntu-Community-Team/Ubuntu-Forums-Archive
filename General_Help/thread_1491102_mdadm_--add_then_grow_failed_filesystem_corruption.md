---
title: "mdadm --add then grow failed: filesystem corruption"
date: 2010-05-23
forum: General Help
---

### Post by damien_d on 2010-05-23
Hi All,

I'm trying to work out what I did wrong, or why the problem that I did turned into such a messy failure.

I am running Ubuntu 10.04, and in that I had 5x 1.5TB HDDs in a RAID5 array mounted as /home.  It has grown from 3x 1.5TBs originally, so I'm fairly comfortable in adding disks to an array and growing the (EXT4) filesystem to match.

A few days ago, I added a 6th 1.5TB HDD and after an --add and --grow operation, I waited for /proc/mdstat to state that it's all complete before rebooting.

After rebooting, all chaos broke loose.

Ubuntu dropped to a shell, unable to mount /home. Strange.  Attemped fsck.ext4 and it was unable to find a superblock and refused to go any further.

Upon examining, it came up with something like this (note, it's doctored, I'm doing this from another workstation)
```

[sudo] password for damien: 
/dev/sda: UUID="0ad3ed48-850b-e0e2-286c-21aee577e768" TYPE="linux_raid_member" 
/dev/sdb1: UUID="0ad3ed48-850b-e0e2-286c-21aee577e768" TYPE="linux_raid_member" 
/dev/sdc1: UUID="E42A21422A2112DA" TYPE="ntfs" 
/dev/sdc2: UUID="caa16306-ddb1-49ab-91f1-471a6ed79b7e" TYPE="swap" 
/dev/md0: UUID="574f93f0-a63a-478d-9803-d0102b96e5ec" TYPE="ext4" 
damien@damien-desktop:~$ 

```

dmesg complained of not being able to start the array, IIRC.

Note that it's /dev/sda NOT /dev/sda1.  I'm guessing I did something like mdadm --add /dev/md0 /dev/sda rather than /dev/sda1.  Yes, the UUID is on the disk, not on a partition and it's reporting as a Linux Raid Member.

I physically disconnected /dev/sda, where I was able to start the array in degraded mode.  I then did fsck on it, where it returned thousand upon thousands of errors, making the filesystem cactus.

I've managed to retrieve about half my stuff off it, and I'm running around trying to find all the scattered backups I have of everything else.

My question is, is this the likely cause of what went wrong. If not, what would be a plausible explanation?  As you may imagine, I'm not all that keen to try to reproduce the problem!

  -- Damien

p.s. When someone says "RAID is not a backup" please believe them :)

---

