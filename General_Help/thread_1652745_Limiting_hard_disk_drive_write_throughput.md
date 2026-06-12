---
title: "Limiting hard disk drive write throughput"
date: 2010-12-25
forum: General Help
---

### Post by Sworddragon on 2010-12-25
Sometines a server application is running that needs a lot of write throughput on the hard disk drive. But this causes the system nearly to freeze for this time. A look in htop shows me that wa: is on both cores used from 30%-90% and the overall CPU usage is only at ~10-40% on both cores. It seems the hard disk drive is the brake. The application that must write a lot on the drive don't need to finish fast. So I'm thinking about to limiting the write throughput.

I have made a look in /etc/security/limits.conf but I haven't found a value for the write throughput. Have somebody an idea how to limit this for a user?

---

### Post by noah++ on 2010-12-25
Would *ionice* work for you? Looks like it has 24 priority levels if you are using the Completely Fair Queuing scheduler.

[http://linux.die.net/man/1/ionice](http://linux.die.net/man/1/ionice)

---

### Post by dcstar on 2010-12-25
> **Sworddragon said:**
> Sometines a server application is running that needs a lot of write throughput on the hard disk drive. But this causes the system nearly to freeze for this time.
........

Do this:

[http://ubuntuforums.org/showthread.php?t=1625233](http://ubuntuforums.org/showthread.php?t=1625233)

---

### Post by Sworddragon on 2010-12-26
None of both solutions has changed anything. ionice seems only to communicate from io to io and not from io to io and cpu. And while this problem is a bottleneck somewhere on the hardware this can't solve the problem. I'm using now nice -n 19 and ionice -c 3 but this doesn't change something feelable. The only solution is a tool that can communicate with more components at once and priorize them. Maybe I must wait for a kernel update (if in the next months/years will be a patch to optimize the hardware communication).

---

### Post by noah++ on 2010-12-26
Are you sure you are using the CFQ scheduler? If I am reading the *ionice *man page right, that seems to be a prerequisite if the command is to have any effect. In any case, you might try experimenting with compiling kernels with the different types of schedulers and different clock resolutions to see if it makes your system more responsive.

---

### Post by Sworddragon on 2010-12-27
What do you mean with CFQ sheduler? Is the programm only priorizing registered applications instead of the complete system?

I have now tried to give the file an exclusive write lock for a percentage time with a script. But this hasn't changed anything and I have made some tests. It seems that my filesystem (ext4) can't acquire file locks. I have a minimalistic configured system. Is there maybe a package or a special configuration needed to get file locks on ext4 working or is the file locking on ext4 hardcoded? The lock was flock() from PHP. If the locking is hardcoded I must have made a mistake and will make a look again.

Edit: It seems that a file lock with PHP/Python isn't global. The server application (executable file) doesn't acquire a lock so this solution doesn't work.

---

### Post by efflandt on 2010-12-27
**cat /sys/block/sdx/queue/scheduler** (replace sdx with each drive) tells you the scheduler for that drive.  The one in square brackets is the active scheduler ("cfq" is usually the default and best for mechanical hd's).  I don't know exactly what that means, but normally you would only change it to "deadline" (or possibly "noop") for SSD or other high speed flash drive.  If for some reason a drive is not using cfq and you want to change it to that, you can do that with:

```
**echo cfq > /sys/block/**sdx**/queue/scheduler** (replace sdx with your drive)
```Another setting that is sometimes adjusted down for high speed SSD, that maybe needs to be adjusted (up or down?) for a server is **/sys/block/sdx/queue/iosched/fifo_batch** (replace sdx with actual drive).

Or maybe you can find something else in /sys/block/ that can help.  But I am not really familiar with them other than what I set for SSD based on suggestions.

---

### Post by Sworddragon on 2010-12-27
I'm using a mechanical hard disk drive and sda - sde give me "noop deadline [cfq]".

---

### Post by Cheesehead on 2010-12-27
Perhaps use a ramdisk for all that I/O activity?
[http://ubuntuforums.org/showthread.php?t=182764](http://ubuntuforums.org/showthread.php?t=182764)

---

### Post by tgalati4 on 2010-12-27
I routinely use a ramdisk to run firefox and all of its pesky cache files.  Once every 10 minutes, it writes back to the harddisk to capture the cache snapshot.

Are you using a RAID setup?  Normally that will increase disk write speeds 2X or 3X depending on how you have it set up.

If you go the ramdisk route, make sure you use a decent UPS because your database won't survive power loss.

---

### Post by Sworddragon on 2010-12-28
The I/O writing comes from a tool which reads the content of a map from a game and creates a worldmap. I have only 4 GB RAM and the tool needs dependend of the options sometimes an own swap file which is more than 10 GB big. This is to much for a RAM drive. I'm not using a RAID system.

---

### Post by Sworddragon on 2011-01-06
I have made lot of tests with the vm settings in /etc/sysctl. My ext4 drive uses full data journaling with chattr. I figured out that the freeze appears if nr_dirty is beeing flushed. It makes even no difference between flushing 8000 pages or 100000 pages. The freeze has always the same duration. I got the best performance with tryinng to flush at late as possible and then flushing all at once (it seems only vm.dirty_writeback_centisecs forces a full flush).

After this I have removed full data journaling from a directory and made some tests. The writing speed with full data journaling is 23 MB/sec and with ordered data journaling it's 65 MB/sec.  I knew before that the writing throughput is theoretically reduced about ~half but there are even big differences in the performace. Without full data journaling other processes are running extremely better. I don't get every second a full freeze anymore. Now there are 3 behaviours (tested on a game during a write process):

1. The game is running without a problem for a long time
2. Objects in the game are freezing for a few seconds but I can still move (it's like a lag in online games).
3. The game is freezing for a short time.

That's not optimal but much better than secondly freezes and a total unsmoothy game (with full data journaling). My configuration is now:

vm.dirty_background_ratio = 0
vm.dirty_expire_centisecs = 0
vm.dirty_ratio = 100
vm.dirty_writeback_centisecs = 0

I figured out that I got the most overall and throughput performance if I try to write asynchronous at the beginning.

But maybe there are other things that I can optimize and somebody know such configurations.

---

