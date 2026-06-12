---
title: "RAID5 ReiserFS Recovery"
date: 2010-11-11
forum: General Help
---

### Post by Richard_ on 2010-11-11
Hi guys,

I've got a server which runs a non-bootable array of drives in a software RAID5 configuration with ReiserFS as the filesystem and mdadm managing the array. A couple of days ago the server overheated in a catastrophic way and crashed. I've subsequently taken the 5 drives which made up the RAID 5 array and cloned them with dd onto a new set of identical drives. Now, as far as I can tell there was no physical damage to the old drives and I suspect the server shut down before any damage occurred. There does however seem to have been some software corruption. Now this is where my dilemma comes in:

I have taken the new drives (copied with dd from the old drives) and installed them in the same order on the server. The problem is that I have absolutely no clue in what order the drives are supposed to be added to the RAID array and the array was not assembling at all. So I recreated the array by doing the following, hoping that the order would be correct:

```

mdadm --create /dev/md1 --force --assume-clean -l5 -n5 -c4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sde1 /dev/sdf1

```

For interest's sakes, /dev/sdd is also present in the machine, but it is a drive which has long been removed from the raid array, and is not supposed to be part of the array.

I initially suspected that the order in which I added the drives was correct, but I think I may have been mistaken on this one... Also, the chunk size is correct, so that shouldn't be a problem. Now when I run a reiserfsck on /dev/md1 I get the following output: 

```

Replaying journal: Done.
Reiserfs journal '/dev/md1' in blocks [18..8211]: 0 transactions replayed
Zero bit found in on-disk bitmap after the last valid bit.
Checking internal tree..  

Bad root block 0. (--rebuild-tree did not complete)

Aborted

```

If I rerun reiserfsck with the fix-fixable flag, I get almost the same output: 

```

Replaying journal: Done.
Reiserfs journal '/dev/md1' in blocks [18..8211]: 0 transactions replayed
Zero bit found in on-disk bitmap after the last valid bit. Fixed.
Checking internal tree..  

Bad root block 0. (--rebuild-tree did not complete)

Aborted

```

Lastly, if I actually try to mount /dev/md1, I get the following:
```

livecd ~ # mount /dev/md1 /mnt/drive/
mount: wrong fs type, bad option, bad superblock on /dev/md1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The output of dmesg is as follows:
```

REISERFS (device md1): found reiserfs format "3.6" with standard journal
REISERFS (device md1): using ordered data mode
REISERFS (device md1): journal params: device md1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
REISERFS (device md1): checking transaction log (md1)
REISERFS warning: reiserfs-5090 is_tree_node: node level 0 does not match to the expected one -1
REISERFS error (device md1): vs-5150 search_by_key: invalid format found in block 0. Fsck?
REISERFS (device md1): Remounting filesystem read-only
REISERFS error (device md1): vs-13070 reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [1 2 0x0 SD]
REISERFS warning: reiserfs-5090 is_tree_node: node level 0 does not match to the expected one -1
REISERFS error (device md1): vs-5150 search_by_key: invalid format found in block 0. Fsck?

```

Lastly, here's my output from /proc/mdstat

```

livecd ~ # cat /proc/mdstat 
Personalities : [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdf1[4] sde1[3] sdc1[2] sdb1[1] sda1[0]
      1953535744 blocks level 5, 4k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

```

Now, does anybody have any suggestions for me? I realise that some of the things I've done weren't the best of ideas, but I do still have the original drives which I can clone again if I need to.

I'm hoping somebody with the required ninja skills can help me out with this one :)

---

