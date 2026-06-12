---
title: "Increase GPT filesystem fails with GParted"
date: 2009-11-22
forum: General Help
---

### Post by lajo01 on 2009-11-22
I have a large filesystem with GPT partition table, it consists of 4 disks in a RAID-5.
Now I want to a fifth disk to the raid and increase the size of the filesystem (using GParted), but I get an error message as below:[I]

[SIZE=1]The backup GPT table is not at the end of the disk, as it should be. This might mean that another operating system believes the disk is smaller. Fix, by moving the backup to the end (and removing the old backup)?       [/SIZE][/I][SIZE=1]*Not all of the space available to /dev/sdd appears to be used, you can fix the GPT to use all of the space (an extra 1953103872 blocks) or continue with the current setting? *[/SIZE]

Any ideas what this is about, I Googled it but found not obvious soultion but many reports about the problem in the past. Is it a bug in Gparted?

---

