---
title: "What is job-mkfs-guyqgm for?"
date: 2012-07-07
forum: General Help
---

### Post by kosajaffe on 2012-07-07
Hi there, 

while mounting my sdhc card I got the following error message:

```
Error creating file system: helper exited with exit code 1: cannot mount /dev/mmcblk0 at /var/run/udisks/job-mkfs-guyqgm: Invalid argument

Discarding device blocks:   4096/994944528384/994944             done                            
Filesystem label=extremeiii
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
248992 inodes, 994944 blocks
49747 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1019215872
31 block groups
32768 blocks per group, 32768 fragments per group
8032 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736

Allocating group tables:  0/31 1/31 2/31 3/31 4/31 5/31 6/31 7/31 8/31 9/3110/3111/3112/3113/3114/3115/3116/3117/3118/3119/3120/3121/3122/3123/3124/3125/3126/3127/3128/3129/3130/31     done                            
Writing inode tables:  0/31 1/31 2/31 3/31 4/31 5/31 6/31 7/31 8/31 9/3110/3111/3112/3113/3114/3115/3116/3117/3118/3119/3120/3121/3122/3123/3124/3125/3126/3127/3128/3129/3130/31     done                            
Creating journal (16384 blocks): done
Writing superblocks and filesystem accounting information:  0/31 1/31 2/31 3/31 4/31 5/31 6/31 7/31 8/31 9/3110/3111/3112/3113/3114/3115/3116/3117/3118/3119/3120/3121/3122/3123/3124/3125/3126/3127/3128/3129/3130/31     done
```

Can someone explain what "cannot mount /dev/mmcblk0 at /var/run/udisks/job-mkfs-guyqgm: Invalid argument" means and what can I do about it? I couldn't find anything on google.

---

