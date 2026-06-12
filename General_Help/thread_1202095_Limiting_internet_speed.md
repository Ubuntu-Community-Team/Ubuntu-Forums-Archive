---
title: "Limiting internet speed"
date: 2009-07-01
forum: General Help
---

### Post by s3a on 2009-07-01
Is there some sort of *network limiter* I can use to limit my terminal from apt-get installing something at a maximum of lets say 30 kb/s? Or is there an application to limit my whole computer to a certain download speed?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by DGortze380 on 2009-07-01
> **s3a said:**
> Is there some sort of *network limiter* I can use to limit my terminal from apt-get installing something at a maximum of lets say 30 kb/s? Or is there an application to limit my whole computer to a certain download speed?

Any help would be greatly appreciated!
Thanks in advance!

Not exactly what you're looking for, but a start: [http://ubuntuforums.org/showthread.php?t=605121](http://ubuntuforums.org/showthread.php?t=605121)

Site Down for Maintenance: [http://stackoverflow.com/questions/31537/how-to-throttle-bandwidth-on-a-linux-network-interface](http://stackoverflow.com/questions/31537/how-to-throttle-bandwidth-on-a-linux-network-interface)

And this one: [http://brainstorm.ubuntu.com/idea/553/](http://brainstorm.ubuntu.com/idea/553/)

I handle throttling through my Cisco Router, I'm not familiar with host-based solutions.

---

### Post by s3a on 2009-07-01
Actually, I found exactly what I was looking for with a google search!!!

[http://xlife.zuavra.net/index.php/14/](http://xlife.zuavra.net/index.php/14/)

---

### Post by t4thfavor on 2009-07-01
If your router supports QoS you can limit everything from a certain machine, or just a certain type of traffic. (I limit http > 500K to 20kbps while browsing stays at full speed)

---

