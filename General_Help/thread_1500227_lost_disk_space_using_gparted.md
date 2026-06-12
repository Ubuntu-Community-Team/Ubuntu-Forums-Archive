---
title: "lost disk space using gparted?"
date: 2010-06-02
forum: General Help
---

### Post by bluemannew on 2010-06-02
I installed Ubuntu 9.04 on my laptop last week.  I had it dual-booted with Vista, but when it became apparent that I would be using Ubuntu much more than Vista from now on I wanted to resize my partitions.  Originally, Vista was ~180 Gib with about 100 Gib of free space and Ubuntu was ~ 40 Gib with about 5 Gib of free space. So all in all there was ~105 Gib of free space on my system.

When I tried to resize my partitions from the Ubuntu live CD, it bombed out after it had already resized the two main partitions.  When I rebooted, Ubuntu loaded fine and Gparted now says that it is 120 Gib, which is right but there is still about 5 Gib of free space.  The Vista partition only has ~28 Gib of free space, so now I only have ~33 Gib of free space!  Is there anything I can do to restore the 70 Gib I lost?

---

### Post by Mark Phelps on 2010-06-03
If you can boot into Vista, and you want the Vista OS partition to incorporate the free space, run the Vista Disk Management utility to see if it works.

IF you can't boot into Vista, it's likely you corrupted the OS partition by ignoring SCORES of posts that say NOT to use GParted to shrink Vista OS partitions.  You will have to repair the Vista boot using a Vista installation DVD, or Vista repair cd.

---

### Post by srs5694 on 2010-06-03
I have two suggestions, both of which you should attempt from a live CD rather than a regular boot, with the partition in question *un*mounted:


[list=1]
[*]Run a filesystem check on the Ubuntu partition, as in "sudo e2fsck -f /dev/sda5" (or whatever the partition ID is). If you're not using an ext2/3/4 filesystem, you'll need to use fsck rather than e2fsck, and I believe it doesn't support the -f (--force) option.
[*]If #1 doesn't help, run resize2fs (or another filesystem-appropriate resize tool) on the partition, as in "sudo resize2fs /dev/sda5" (again, change /dev/sda5 as appropriate for your system).
[/list]

---

