---
title: "Rsync hangs repeatably... and I can't figure out why"
date: 2010-04-14
forum: General Help
---

### Post by youdigit on 2010-04-14
I'm hoping somebody can find something here that I haven't.  

I'm trying to use rsync to backup home directories to a nas.  First, I NFS mounted the nas and ran an rsync and everything worked out fine... the transfer completed after a few hours and everyting was transferred (lots of stuff!).  I then decided that I don't want to leave the nas mounted all the time and I didn't want to automate mounting and unmounting of the nas as I didn't think I could produce a script that would work reliably enough.  So I decided to start an rsync daemon on the nas and upgrade via that.  I run the following command (results are included... the ^C is me killing it after it hangs).

```
ryan@server:/etc/backup$ sudo rsync -ax --stats --progress --delete /data root@192.168.0.98:backups1
root@192.168.0.98's password: 
sending incremental file list
data/home/user/Documents/
data/home/user/Documents/The File.wmv
     2228224   6%    2.05MB/s    0:00:16  ^C
rsync error: unexplained error (code 130) at rsync.c(544) [sender=3.0.6]
```Before it started hanging on this line, it was transferring updated files for a good while.  Now it essentially stops as soon as it starts, always ending when "The File.wmv" (~32MB) is between 6 and 9%.  I've checked the permissions/owners/groups on both ends and it is consistent with all the other files that have already been transferred.

I also checked the dmesg on the nas and after the transfer becomes inactive for awhile, the hard drive goes to sleep.

I've tried changing the --delete option to --delete-delay which made no difference.  When I tried --delete-after I got the following:
```
ryan@server:/etc/backup$ sudo rsync -ax --stats --progress --verbose --delete-after /data root@192.168.0.98:backups1
root@192.168.0.98's password: 
building file list ... 
rsync: readlink_stat("/data/home/ryan/.gvfs") failed: Permission denied (13)
71060 files to consider
data/home/user/Documents/
data/home/user/Documents/The File.wmv
     2850816   7%    2.69MB/s    0:00:12  
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: connection unexpectedly closed (31 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.6]
```... which I don't understand and haven't found a solution for.   So if anybody can shed some light on how to fix this problem I would greatly appreciate it!  I'm running a fully updated v9.10.

Thanks!

---

### Post by youdigit on 2010-04-15
Some more information:  The drive on the nas is basically empty (/dev/sda2).  I deleted everything manually and tried again and still got nothing.

```
root@BACKUP:/mnt/HD_a2/ffp/start# df
Filesystem           1k-blocks      Used Available Use% Mounted on
rootfs                    9911      9240       159  98% /
/dev/root                 9911      9240       159  98% /
/dev/loop0                5760      5760         0 100% /sys/crfs
/dev/sda2            960404324    241908 960162416   0% /mnt/HD_a2
/dev/sdb2            960404324 266601388 693802936  28% /mnt/HD_b2
/dev/sda4               497861     10550    487311   2% /mnt/HD_a4
/dev/sdb4               497861        20    497841   0% /mnt/HD_b4

```

---

### Post by youdigit on 2010-04-22
Ok, so after screwing around for awhile (as in days) I figured out the problem.  The files were copying to the root user's home directory, instead of the defined module.  The mistake:

```
root@192.168.0.98:backups1
```[FONT=monospace]

should have been

[/FONT][FONT=monospace][/FONT]```
r[FONT=monospace][/FONT]oot@192.168.0.98::backups1
```

I know I tried that syntax at some point in the process, but there must have been another obvious error that caused me to revert back to the original way I did it.

---

### Post by Chronon on 2010-04-22
Well done: You solved your own problem!  :KS

It would still be good to mark it as "Solved" to help others find this solution in the future.

---

