---
title: "processor use all the way up all the time"
date: 2011-03-03
forum: General Help
---

### Post by KFwLsKvVAs on 2011-03-03
Hello.  So I'm working on this Intel Celeron HP33w Pavillion with 512mb ram and a 180 gb hard drive.  Installed xp on it, partitioned half the drive and left the other half blank.  xp installed no prob, then installed ubuntu on the second partition letting ubuntu create the partition and swap space (which was 3 gigs) and it installed fine (aside from being incredibly slow to go through the actual install process).  Once finally booted into ubuntu with no other programs running aside from the standard ones that start with ubuntu, i added the system monitor to the panel and expanded all the other monitors.  Memory was normal, cup average was 100% and cpu usage was 100%.  Figured something went wrong with the install so I reinstalled and got the same result.  Window xp runs just as fast as it should with 512mb of ram so I'm sort of at a loss as to why ubuntu is eating up all my memory with no programs running.  anybody have any ideas?

---

### Post by plucky on 2011-03-04
Open a terminal **Applications > Accessories > terminal** and type **top** and see what is using all your resources.

Good Luck

---

### Post by seawolf167 on 2011-03-04
I've got a crazed printer driver on an old computer that slowly eats up one cpu core and every so often I have to kill it. I like to use htop rather than top, but either one works.

```
sudo apt-get install htop
```

---

