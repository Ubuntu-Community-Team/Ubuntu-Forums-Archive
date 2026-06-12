---
title: "cron.daily hanging my system?"
date: 2011-06-12
forum: General Help
---

### Post by RansomOttawa on 2011-06-12
Hi all.  I've been dealing with a multimedia-related issue that causes my entire Lucid system to hang; the details can be found [here](http://ubuntuforums.org/showthread.php?t=1772314).

While trying to determine the cause of *that* problem, I discovered another pattern of system failures: almost every day, sometime between about 7:45 and 8:00 am, it locks up. This is annoying, because it happens only a few minutes after I have to leave for work, but I have some automated jobs that I want to run while I'm away, but I I'm not around to reboot the system. (Of course it's even more annoying that this happens at all!)

The last thing in the syslog before the crash happens is always something like this:

```

Jun 12 07:30:01 deepthought CRON[15858]: (root) CMD (start -q anacron || :)
Jun 12 07:30:01 deepthought anacron[15861]: Anacron 2.3 started on 2011-06-12
Jun 12 07:30:01 deepthought anacron[15861]: Will run job `cron.daily' in 5 min.
Jun 12 07:30:01 deepthought anacron[15861]: Jobs will be executed sequentially
Jun 12 07:35:01 deepthought anacron[15861]: Job `cron.daily' started
Jun 12 07:35:02 deepthought anacron[15979]: Updated timestamp for job `cron.daily' to 2011-06-12
Jun 12 07:37:25 deepthought kernel: [80685.521907] usb 3-2: USB disconnect, address 2
Jun 12 07:37:26 deepthought kernel: [80686.056643] usb 2-3: USB disconnect, address 2
Jun 12 07:39:02 deepthought CRON[16127]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

```

So if I'm right, then something in cron.daily is taking the computer down. Any suggestions to help me determine the specific cause? I'm a relative cron newbie, but I gather from perusing /etc/cron.daily that it is actually a set of scripts, correct?

I've made no changes to cron.daily - hardly even knew it was there - so presumably what it does is factory default.

Alternatively, is it possible to disable cron.daily, at least temporarily, as a way to eliminate some possible causes?  Is it even wise to do so? (I assume this job involves some daily housekeeping but have no idea how vital it is to run regularly, every day.)

Finally, is it possible there's a connection between these crashes and the ones I've been experiencing with my media players crashing?  It'd be great if solving one problem solved the other.

---

### Post by DaithiF on 2011-06-13
Hi,
the last command in the log before the hang is pretty innocuous:

```
[ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin 
+$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm

```

This checks for the /usr/lib/php/maxlifetime file, and deletes files from /var/lib/php5 where those files are older than the timestamp in the maxlifetime file.  This will come from a script **php5** in the /etc/cron.daily directory, whose purpose is to clear php session files older than a certain duration.

I would:
1. try executing the command above from the command line (as sudo) to see if it throws out any interesting behaviour (ie. hangs, errors, etc)

2. there are a couple of USB disconnects in the logfile too just before then hang.  Do you have some parts of your filesystem mounted on removable media by any chance (e.g. parts of /var ?).  post the output of **sudo fdisk -l** if you're not sure.

thanks

---

### Post by RansomOttawa on 2011-06-13
> **DaithiF said:**
> Hi,

I would:
1. try executing the command above from the command line (as sudo) to see if it throws out any interesting behaviour (ie. hangs, errors, etc)

Done.  No messages of any kind - it just came back with the command prompt.

> 2. there are a couple of USB disconnects in the logfile too just before then hang.  Do you have some parts of your filesystem mounted on removable media by any chance (e.g. parts of /var ?).  post the output of **sudo fdisk -l** if you're not sure.

I do frequently have thumb drives or my iPod plugged in, but that doesn't seem to affect these particular crashes - and neither has been connected for some of the most recent crashes.  But just for giggles, here's the output of fdisk -l:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050712

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6398    51391903+  83  Linux
/dev/sda2           19393       19457      522112+  82  Linux swap / Solaris
/dev/sda3            6399       19392   104374305   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000baca5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1           2       15088+   4  FAT16 <32M
Partition 1 does not end on cylinder boundary.
/dev/sdb2               3        4865    39062047+  83  Linux

```

Nothing surprising there: two ext4 partitions and one swap on the primary drive, and ext4 and FAT partitions on the slave.  This is the configuration I've had for about a year and a half now.

---

### Post by DaithiF on 2011-06-14
Ok, nothing strange there.  We can definitely discount the php5 job as an issue since in fact its not even being run by cron.daily, instead its an entry in /etc/cron.d, and it gets run twice an hour at 9 and 39 minutes past the hour ... so if it was the problem you would lock up twice an hour rather than once per day.

at this stage I would suggest running the scripts in /etc/cron.daily manually (as sudo) and see what behaviour ensues.

note that 'apt' script includes a sleep for a random amount of time (default 30mins) (to prevent all ubuntu machines hitting update mirrors at the same time!), so you may want to comment out the random_sleep line for the purposes of your test, otherwise you'll be waiting while it naps.

---

### Post by RansomOttawa on 2011-06-14
Running each script manually would have been my next step. However, in diagnosing the crash problems I was having with media players, I think these problems are actually caused by a hard drive that is in the act of failing.  After unmounting that drive last night, the daily crash didn't occur this morning.

I suspect that one of the daily scripts was probably trying to access the drive and hanging the system - and had I run all the scripts from the command line, I'd have figured it out sooner or later anyway.

Well, that stinks, but it's better to replace a cheap hard drive than the entire system . . .

Thanks a lot for your help - it did help focus my thinking.  I'm going to mark this thread solved.

---

### Post by DaithiF on 2011-06-14
ok good.  Certainly mlocate would be a likely candidate -- as it updates its index of all local filesystems.

---

