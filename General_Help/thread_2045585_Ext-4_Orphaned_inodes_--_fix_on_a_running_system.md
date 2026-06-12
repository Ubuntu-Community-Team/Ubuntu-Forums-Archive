---
title: "Ext-4 Orphaned inodes -- fix on a running system?"
date: 2012-08-21
forum: General Help
---

### Post by mgoldey on 2012-08-21
Folks:

This is a variant on the typical "my disk is full" problem.  

An application goes nuts and is generates a 850 GB log file within a day or two, which completely fills the  root partition.  By the time I notice this, the box is having some  issues due to lack of file space, but it's still up and running.  Unfortunately, even though I delete the offending file using "rm filename.log", the disk space is  not actually cleared.  I'm pretty sure that the space is being orphaned  -- the inode is still marked as in use, even though the file system as deleted all reference to the file.  

The result is that bash, File Manager, etc., cannot find the file -- and it's not in the trash, or lost and found -- but the kernel thinks that the disc is still full.  Compare:

```
root@box:/# find / -type f -size +10000000k -exec ls -lh {} \;
 find: `/proc/10245/task/10245/fd/5': No such file or directory
 find: `/proc/10245/task/10245/fdinfo/5': No such file or directory
 find: `/proc/10245/fd/5': No such file or directory
 find: `/proc/10245/fdinfo/5': No such file or directory
```with . . . 

```
root@box:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              912G  866G     0 100% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
udev                 1004M  180K 1004M   1% /dev
tmpfs                1008M     0 1008M   0% /dev/shm
```On reboot, the disc is repaired.  This snippet from the syslog pretty much sums it up:

```
Aug 21 12:24:52 faf kernel: [    3.094316] EXT4-fs (md0): INFO: recovery required on readonly filesystem
Aug 21 12:24:52 faf kernel: [    3.094325] EXT4-fs (md0): write access will be enabled during recovery
Aug 21 12:24:52 faf kernel: [    9.335591] EXT4-fs (md0): orphan cleanup on readonly fs
Aug 21 12:24:52 faf kernel: [    9.335622] EXT4-fs (md0): ext4_orphan_cleanup: deleting unreferenced inode 786856
Aug 21 12:24:52 faf kernel: [    9.335699] EXT4-fs (md0): ext4_orphan_cleanup: deleting unreferenced inode 786688
Aug 21 12:24:52 faf kernel: [   20.158834] EXT4-fs (md0): 2 orphan inodes deleted
Aug 21 12:24:52 faf kernel: [   20.158845] EXT4-fs (md0): recovery complete
Aug 21 12:24:52 faf kernel: [   22.791091] EXT4-fs (md0): mounted filesystem with ordered data mode

```(This is a RAID 1 volume.)

What I'd like to know is whether there is any way to find and re-allocate these orphaned inodes on a running system, without a reboot?  

Many thanks, in advance.



root@box:/# uname -a
Linux box 2.6.32-5-686 #1 SMP Sun May 6 04:01:19 UTC 2012 i686 GNU/Linux

---

### Post by matt_symes on 2012-08-21
Hi

The file is not totally deleted until the process that holds the open file is stopped/restarted - even if all the inodes to the file are deleted as the kernel has its own internal data structures about the file and, as far as the kernel is concerned, the file is still open.

The first thing i would ask myself is why the file is so big after only being open for a day or two. That just seems crazy; 850GB is not a typo ? This you need to fix !!!

Deleting all the links to the file and restarting the service/process that created the file will free up the drive space.

Kind regards

---

### Post by mgoldey on 2012-08-21
Thanks, that's a good point about killing the process that made the file.  If this happens again, I will check the inode of the log file before rebooting, to see if it really is orphaned, or if it's really still in use by the process.

Yes, 850 GB is correct.  The underlying problem clearly needs to be fixed.  But, you know, one problem per thread . . .

---

### Post by matt_symes on 2012-08-23
Hi
> 
Thanks, that's a good point about killing the process that made the  file.  If this happens again, I will check the inode of the log file  before rebooting, to see if it really is orphaned, or if it's really  still in use by the process.

The log file may have no inodes in the filing system pointing to it, but the kernel will still have open file descriptors to the file while the process that opened the file has not closed the file descriptors.

Don't take my word for it., you can check this for yourself by looking in /proc. 

Checking to see if it has no hard links, before you close the process that opened it, will not make any difference to the file. It is not deleted until you also close the program that opened the file descriptor for the file.

Depending on what program is making the log file, you may be able to send it a HUP signal instead of restarting it.

For example..

A syslog file can be moved, a new log file created and then rsyslog sent a sighup signal to reread its config file and to then start loging to the new file. Something along the lines of...

```

sudo mv /var/log/syslog{,.old}
sudo touch /var/log/syslog
sudo kill -HUP $(cat /var/run/rsyslogd.pid)
```A believe that logrotate does something similar to rsyslog, which brings me to my next question..

Is is possble for you to use logratate to rotate (and compress) the log file daily; at least until you get to the root cause of the problem ?

That way you can also create a cron job to clean up (delete, copy to other storage, etc) the compressed log files that are older than, say, three days old.

BTW: You never mentioned what log file was causing you the problem.

Kind regards.

---

### Post by mgoldey on 2012-09-16
Thanks for the detail and clarification. 

The misbehaving program is VNC Server.  The problem is along the lines of writing to the log file 10 or 20 times a second, every second, which eventually creates an 850 GB file.  Tail showed the same message over and over -- essentially "unauthorized connection attempt."  The problem seems to start when someone w/o credentials, or with the wrong credentials, attempts to log in, but why it spirals out of control is still a mystery, as this hasn't happened again since I made some changes to my firewall.   

I appreciate the idea about logrotate + gzip, but it's become moot since the problem hasn't recurred.

---

