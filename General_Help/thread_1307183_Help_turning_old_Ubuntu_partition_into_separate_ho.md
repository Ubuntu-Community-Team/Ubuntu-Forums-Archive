---
title: "Help turning old Ubuntu partition into separate home partition?"
date: 2009-10-30
forum: General Help
---

### Post by Solarisphere on 2009-10-30
I religiously upgrade Ubuntu with a clean install within a couple days of the new versions being released, except this time around I've filled up my HDs too much to back up without buying a new external drive. I'd also like to end up with a separate /home partition so I won't have to worry about this for future upgrades.

I've got a 1TB drive with about 600GB on it, and a 500GB drive with nothing important on it. I'd like to end up with a single main /home partition on the 1TB and various OS and backup partitions on the 500GB.

The problem is that I can't reformat the 1TB without losing everything on it. It used to be my main 9.04 partition. Can I turn it into a /home partition without reformatting? All the info I can find on /home partitions assumes that you're starting fresh.

---

### Post by zzzBrett on 2009-10-30
I had a thread a few weeks ago that may help you.
[http://ubuntuforums.org/showthread.php?t=1291452](http://ubuntuforums.org/showthread.php?t=1291452)

You can mount your 1TB HDD in fstab and use a symlink (or one of the other methods discussed) to link it to your /home directory.

---

