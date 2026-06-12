---
title: "I have a /boot, /usr, /tmp, /var partition. Beneficial?"
date: 2010-10-22
forum: General Help
---

### Post by akand074 on 2010-10-22
Hey guys,

Right now I'm running Ubuntu 10.04 on my desktop and I had made a partition for /boot, /usr, /tmp and /var. All ext4 except /var I made as reiserFS (supposed to be a good choice for /var because its very efficient for a large amount of small files). (Also have a /home partition but that's for obvious reasons).

I'm going to do a clean install of 10.10 really soon and was wondering if there is even any pros/cons to it. I originally did it because I expected a small performance boost, I never ended up paying attention to it and I don't think there was really any major performance boosts seeing as I haven't noticed it. Though I think it might have slowed down my boot speed a bit.

Does anyone else have partitions for any of these? Any inputs on whether I should keep them or not, or is it not a big deal either way? Thanks for the input.

---

### Post by matt_symes on 2010-10-22
Hi

IMHO i try put put my home directory on a separate partition (this has been a life saver). Also maybe /var is good for the log files. That's all i do. Anything else is a preference. I am interested in what others think of this.

I don't do it for performance though

Kind regards

---

### Post by oldfred on 2010-10-22
For standard desktops, I see no reason for any system partition other than root, swap & home. Servers, RAID, old systems that need a /boot are another story. I like to use extra partitions for /data and additional roots so I can keep an old version, a beta version & maybe a test of something else. If I have all those partitions for each install I would be totally lost.

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by akand074 on 2010-10-22
> **oldfred said:**
> For standard desktops, I see no reason for any system partition other than root, swap & home. Servers, RAID, old systems that need a /boot are another story. I like to use extra partitions for /data and additional roots so I can keep an old version, a beta version & maybe a test of something else. If I have all those partitions for each install I would be totally lost.

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Herman sold me. I'll remove all the other partitions. My /home is actually a completely different hard drive so even if I didn't want it its necessary. Plus I still find it very handy.

---

### Post by dcstar on 2010-10-23
> **matt_symes said:**
> Hi

IMHO i try put put my home directory on a separate partition (this has been a life saver). Also maybe /var is good for the log files. That's all i do. Anything else is a preference. I am interested in what others think of this.


A separate /home allows for simple Linux reinstallation/upgrade without any loss of user data, changing anything else from the standard setup is usually a waste of time.

If you use a SSD and also have a "normal" drive available you can mount folders that have frequent writes away from the SSD to reduce the wear on it (this is what I do with /tmp and swap).

---

