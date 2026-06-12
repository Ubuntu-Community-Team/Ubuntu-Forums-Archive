---
title: "Utility for filesystem caching in RAM"
date: 2010-11-29
forum: General Help
---

### Post by Fallingwater on 2010-11-29
I run Ubuntu Netbook 10.04 on my EeePC 1005HA. I'm going to get a SSD  for it eventually, but I can't afford one right now so it's running from  a 200GB hard disk I scavenged off a dead laptop.

I went in power management and set the option that says "spin down hard  drives whenever possible", but this accomplished a whole lot of nothing -  whenever the computer is on, the drive's spinning. I ran hdparm -y and  the drive clicked off, and then promptly spun back up after a few  seconds. Iotop shows occasional tiny bursts of activity from  "jdb2/sda1-8", which I don't really know how to interpret, but I don't  have anything weird installed so I'm assuming this is normal system  operation. 

Now, what I need is some sort of application, utility, command -  anything - that forces the computer to keep all filesystem changes in  RAM with the drive shut down; every five/ten minutes or so (this would  hopefully be configurable) it spins up the drive, dumps the filesystem  changes to it, and spins it down again.

I realize this presents data loss risks related to crashing and  poweroffs when the cache hasn't yet been dumped to disk, but I'm willing to  risk it as Linux never really crashes at all, and since it's a netbook  power failures won't cause unexpected shutdowns.

Does such a thing exist?

Thanks.

---

