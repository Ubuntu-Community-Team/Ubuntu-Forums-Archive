---
title: "XFS Filesystem on RAID 5"
date: 2011-05-01
forum: General Help
---

### Post by annagel on 2011-05-01
This issue started for me after upgrading to 11.04, but at this point I think I am well past upgrade related issues and on into general problems.  First a background.

After upgrading my 5 disk RAID5 array is no longer correctly assembling, the array appears as two distinct arrays both of which expect 5 disks one containing 3 and the other 2, the disks appear to be in the correct locations in each of the two arrays:

md127 : inactive sda[0](S) sdb[2](S)
      2930274816 blocks
       
md0 : inactive sdc[1](S) sde[4](S) sdd[3](S)
      4395415488 blocks

But examining the raid superblock a and b have different UUIDs and are not tagged with the correct homehost.  My thought since I know the order of the disks is to just perform a create to get new metadata written to the disks and get the array back online.  I do this and get errors trying to mount the array.  I think my issue here is that the version of mdadm in 11.04 now uses 1.2 format rather than 0.9 which had been on the disks.  The location of the superblock is different in each of these formats and I think this action messed up some important information on the disks.

After realizing the issue, I recreated the array with the right version of the metadata but still no go on mounting.   I get the error : "mount: /dev/md0: can't read superblock" when I attempt to mount the array. 

XFS is used as the filesystem on the array and running xfs_check gives me the message:

ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_check.  If you are unable to mount the filesystem, then use
the xfs_repair -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.

I have been trying to run xfs_repair (with the -n option for now) but have yet to get past step 1 of the repair process I get the message 

Phase 1 - find and verify superblock...
couldn't verify primary superblock - not enough secondary superblocks with matching geometry !!!

attempting to find secondary superblock...

followed by many "." marks with the message 

found candidate secondary superblock...
unable to verify superblock, continuing...

interspersed throughout.  I am trying to let this process play through which I have not done in the past (it has run for a couple of hours before I stop it) but am not holding out much hope that it will find a good superblock.

Any thing else I can try?

---

### Post by rubylaser on 2011-05-01
What do you have in /etc/mdadm/mdadm.conf and what's the output of cat /proc/mdstat?

```
cat /etc/mdadm/mdadm.conf
```
```
cat /proc/mdstat
```

---

### Post by annagel on 2011-05-01
I dumped my old mdadm.conf so at the moment nothing as the UUID is referenced was trashed with the first create statement.  

mdstat is bellow....looks as good as it can, I guess.  I am thinking my issue is with the XFS filesystem at this point but take that thought with a giant grain of salt.


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde[4] sdd[3] sdb[2] sdc[1] sda[0]
      5860548608 blocks level 5, 512k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

---

### Post by annagel on 2011-05-02
The xfs_repair process finally finished with the message:

Sorry, could not find a valid secondary superblock.  Exiting Now.

Through the run it found a number of candidate superblocks and rejected them all.  Is there any way to force it to accept the primary superblock in spite of the fact it is invalidated?  Just to try to get the disk mounted for recovery?

---

### Post by rubylaser on 2011-05-02
With no valid superblocks, there's not a way that I know of to mount the drive.  You could try running photorec against the block md device.

---

### Post by annagel on 2011-05-02
I am running photorec now targeted at JPGS  and it is pulling a good deal of stuff off the disk.  I was also going to give UFS explorer a try once photorec completes.

---

