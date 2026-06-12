---
title: "Unable to mount XFS after an electricity cut"
date: 2010-12-16
forum: General Help
---

### Post by qip on 2010-12-16
Hi everyone I am new here and not sure about whether I'm posting at the right place or not...

I'm using Ubuntu 10.10 x86_64, with 2T HDD x5 grouped as RAID5 using RAID controller (dell perc 6/i), result in a 8TB disk, and I put it to a single partition in XFS

Just now one light bulb went wrong and caused whole house power fail, sadly during that time I'm copying some data to that partition.
After I clear the power issue and turn on the computer, the partition still can mount, so I continue copying, and that gives me some IO error.
I assume it is some kind of problem that need a file system check, so I unmount it, and run xfs_repair. However xfs_repair shows the partition has not been unmount so I restarted the computer.
Aftering restarting, during the loading screen the system prompt me that it cannot find the file system, and I pressed 'S' to skip (btw 'M' for manually maintenance, but I didn't try)
Then there comes the problem: the partition cannot be mounted anymore

I tried using palimpsest (the disk utility) to check, the partition shows normally (i.e., there's a 8T disk with a single partition in XFS), but when I try to mount it, the first time I click 'mount' results in nothing, repeat click will get an error 'The device is busy: A job is pending on /dev/sdb1'. Checking the process running I found this:
process 'mount', status 'uninterruptible', command line 'mount /dev/sdb1', waiting channel 'call_rwsem_down_write_failed'
Also other operations with that partition does not work, such as xfs_repair or mount, will just halt (and the waiting channel is 'get_sb_bdev')

Sorry if my expression is not clear or not to the right point, as I just switched to linux
There's 7T+ data in it and I really do not want to lose them...:cry:
Thank you for taking time reading this and I appreciate any suggestion:)

---

### Post by dmitryilyin on 2010-12-16
Try not to mount partition (comment out from fstab)
then boot and try to run [http://linux.die.net/man/8/xfs_check](http://linux.die.net/man/8/xfs_check)
[http://linux.die.net/man/8/xfs_repair](http://linux.die.net/man/8/xfs_repair)

---

### Post by qip on 2010-12-16
I comment out the line in fstab, then I try xfs_check, which gives me:
```
08:05:18 root@Peng-Server:/home/peng# xfs_check /dev/sdb1
ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_check.  If you are unable to mount the filesystem, then use
the xfs_repair -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.
```
So I try to mount it:
```
08:05:58 root@Peng-Server:/home/peng# mount -t xfs /dev/sdb1 /media/F4R5/
Killed
```
If I try a second mount it will still halt.
Any idea what is going on? Does that mean I have to destroy the log?
Thanks.

---

### Post by qip on 2010-12-16
OK even the xfs_repair -L seems scary to me I still tried it. After half an hour it seems coming back :)
Data lost about 30G, fairly lucky enough compare to the 7T data

Logs below:
```
09:20:13 root@Peng-Server:/home/peng# xfs_check /dev/sdb1
ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_check.  If you are unable to mount the filesystem, then use
the xfs_repair -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.
09:20:26 root@Peng-Server:/home/peng# xfs_repair -L /dev/sdb1
Phase 1 - find and verify superblock...
Phase 2 - using internal log
        - zero log...
ALERT: The filesystem has valuable metadata changes in a log which is being
destroyed because the -L option was used.
        - scan filesystem freespace and inode maps...
agi unlinked bucket 0 is 2470377152 in ag 0 (inode=2470377152)
agf_freeblks 25674922, counted 25672465 in ag 3
sb_icount 983040, counted 378944
sb_ifree 32, counted 6285
sb_fdblocks 68453958, counted 139263698
        - found root inode chunk
Phase 3 - for each AG...
        - scan and clear agi unlinked lists...
        - process known inodes and perform inode discovery...
        - agno = 0
7fc066a73700: Badness in key lookup (length)
bp=(bno 1235188560, len 16384 bytes) key=(bno 1235188560, len 8192 bytes)
data fork in regular inode 249038048 claims used block 427986474
bad data fork in inode 249038048
cleared inode 249038048
data fork in ino 2470377152 claims free block 956475686
correcting nblocks for inode 2470377152, was 1857111 - counted 1857746
correcting nextents for inode 2470377152, was 46484 - counted 46489
        - agno = 1
        - agno = 2
        - agno = 3
        - agno = 4
        - agno = 5
        - agno = 6
        - agno = 7
        - process newly discovered inodes...
Phase 4 - check for duplicate blocks...
        - setting up duplicate extent list...
        - check for inodes claiming duplicate blocks...
        - agno = 0
        - agno = 1
        - agno = 2
        - agno = 3
        - agno = 4
        - agno = 5
        - agno = 6
        - agno = 7
entry "Battlestar.Galactica.S03E17.720p.BluRay.DTS.x264-REPTiLE.mkv" at block 0 offset 1056 in directory inode 249038033 references free inode 249038048
    clearing inode number in entry at offset 1056...
Phase 5 - rebuild AG headers and trees...
        - reset superblock...
Phase 6 - check inode connectivity...
        - resetting contents of realtime bitmap and summary inodes
        - traversing filesystem ...
bad hash table for directory inode 249038033 (no data entry): rebuilding
rebuilding directory inode 249038033
        - traversal finished ...
        - moving disconnected inodes to lost+found ...
disconnected inode 2470377152, moving to lost+found
Phase 7 - verify and correct link counts...
done
09:57:11 root@Peng-Server:/home/peng# mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
10:01:30 root@Peng-Server:/home/peng# nano /etc/fstab 
10:01:35 root@Peng-Server:/home/peng# mount /dev/sdb1
10:01:43 root@Peng-Server:/media/F4R5# df -lhT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2      xfs     96G   21G   75G  22% /
none      devtmpfs    965M  240K  964M   1% /dev
none         tmpfs    972M  164K  971M   1% /dev/shm
none         tmpfs    972M  344K  971M   1% /var/run
none         tmpfs    972M     0  972M   0% /var/lock
/dev/sdc1      xfs    3.7T  1.8T  2.0T  48% /media/MR5
/dev/sda1     ext4    961M   56M  856M   7% /boot
/dev/sdb1      xfs    7.3T  6.8T  533G  93% /media/F4R5

```

---

### Post by nutznboltz on 2011-01-23
Could you do me a favour and run:

zgrep "page allocation failure. order:0, mode:0x4020" /var/log/*.log*

and post the results back to me.

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706136](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/706136) for why I'm asking.

Thanks,

---

