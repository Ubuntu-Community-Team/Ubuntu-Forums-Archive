---
title: "Incorrect disk space issue"
date: 2012-07-13
forum: General Help
---

### Post by TheGrave on 2012-07-13
Hi guys,

I'm struggling for quite some time with a stupid free disk space issue. For some reason df reports some strange numbers which do not match the gparted output and ocassionally I end up deleting unnecessary stuff to free more than 20-30GB on a 500GB drive just to make Ubuntu believe I don't have 100% disk usage on the root partition. Here is the output:

```
df -ah
Filesystem        Size  Used Avail Use% Mounted on
/dev/sda1         386G  363G  3.5G 100% /
/dev/sda3          65G   62G  3.5G  95% /media/OS
proc                 0     0     0    - /proc
none                 0     0     0    - /sys
fusectl              0     0     0    - /sys/fs/fuse/connections
none                 0     0     0    - /sys/kernel/debug
none                 0     0     0    - /sys/kernel/security
none              3.9G  708K  3.9G   1% /dev
none                 0     0     0    - /dev/pts
none              3.9G   14M  3.9G   1% /dev/shm
none              3.9G  156K  3.9G   1% /var/run
none              3.9G     0  3.9G   0% /var/lock

```

Look at /dev/sda1 - 363G used out of 386G but only 3.5G available:confused:

At the same time gparted shows a completely different story (attached). The net result of the whole stupidity is a "Gnome Power Manager installation error" at startup and GDM restarting the moment I type my pass and hit Enter (fixed by emptying a LOT of space). FSCK doesn't find any errors so I decided it might be a df bug. Upgraded to this version of coreutils but no joy:

[https://launchpad.net/~ondrej/+archive/pkg-dpkg/+build/3609583]("https://launchpad.net/%7Eondrej/+archive/pkg-dpkg/+build/3609583")

Any ideas how to track down this nasty little problem?

---

### Post by Cheesemill on 2012-07-14
It's not a problem, it's the normal expected behaviour.
Ext partitions reserve 5% of their space for emergency use, this is probably what you are seeing.

[http://backdrift.org/freeing-disk-space-in-linux](http://backdrift.org/freeing-disk-space-in-linux)

---

### Post by TheGrave on 2012-07-14
5% sounds about right with this output from df. I'm thinking of trying this solution, doesn't look unsafe:

[http://blog.tuxcoder.com/2011/5/11/reclaim-wasted-hard-disk-space-on-ext-volumes/](http://blog.tuxcoder.com/2011/5/11/reclaim-wasted-hard-disk-space-on-ext-volumes/)

I guess it should be run on a non-mounted partition, right?

Being constantly harassed with 20G free space really drives me overboard.

---

### Post by Cheesemill on 2012-07-14
Yes, you need to unmount the partition first.

And you think 30GB is bad, I lost 600GB on one of my RAID arrays :)

---

### Post by TheGrave on 2012-07-14
> **Cheesemill said:**
> Yes, you need to unmount the partition first.

And you think 30GB is bad, I lost 600GB on one of my RAID arrays :smile:

Due to a fault I guess? Otherwise this would mean you have a 12TB storage :grin:

After  the last data loss I started mutual rsyncing between a few independent  places and now I'm sleeping tight. It saved my *** a couple of times  already.

By the way the solution I mentioned above works like a  charm for those who have the same problem. Booted from a Live CD and  executed the command from there. Before that make sure your partition is not automounted.

---

### Post by papibe on 2012-07-14
Hi TheGrave.

Tuning the reserved space to zero is not recommended for the system partition, only for data-only disks. For example: /home

When you manage to solve your problem, I would recommend separating / from /home, returning the default reserve to /, and optionally eliminating the reserve on /home

Just a few thoughts.
Regards.

---

