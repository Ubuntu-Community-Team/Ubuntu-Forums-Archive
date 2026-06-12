---
title: "Tips for minimizing disk access on slow USB flash?"
date: 2011-07-16
forum: General Help
---

### Post by BrendanM on 2011-07-16
I'm running Ubuntu 10.04 as a full install from a USB flash drive. In other words, I've installed to the flash stick just as though it were a normal hard drive. This is not a Live USB/Persistent install.

The drive is an off-the shelf 8GB Gigaware stick, and its read/write performance is pretty slow. Any time I do anything that requires disk access, it's very sluggish and tends to hang.

I'm looking for advice on things I could do to minimize the amount of disk-access made in the course of using the system, so that it will feel snappier and more responsive.

Some things I've done already:
[LIST]
[*][Installed 'preload']("http://ubuntu-tutorials.com/2008/07/08/improve-application-startup-times-with-preload/"), which is a daemon that monitors what programs you use frequently, and pre-loads them into RAM to reduce startup time.
[*][Mounted /tmp as a tmpfs]("http://brainstorm.ubuntu.com/idea/16244/") (RAM disk) and moved my Firefox and Chrome browser caches into RAM.
[*][Set noatime]("http://blog.loxal.net/2009/04/tuning-ext4-for-performance-with.html") for my root and home partitions.
[/LIST]

Should I be trying to disable the filesystem journal as well? I'm less concerned with potentially burning out the flash drive with too many writes than I am with just making the system more responsive and nicer to use.

One other thing I was reading about is the so-called "Laptop Mode" that appears to be kernel settings to allow you to spin down a laptop hard drive: [http://www.mjmwired.net/kernel/Documentation/laptops/laptop-mode.txt](http://www.mjmwired.net/kernel/Documentation/laptops/laptop-mode.txt)

Obviously a flash drive doesn't spin, but it seems like some of those same techniques could be helpful here. Is there anyone who has experience running Linux in a situation with a very slow hard drive?

FYI, the computers I'm using this flash drive with all have between 2 and 8 GB of RAM, so moving more stuff into RAM is unlikely to be an issue.

---

### Post by oldfred on 2011-07-16
A lot of the settings are the same as for a SSD (just a lot slower).

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

