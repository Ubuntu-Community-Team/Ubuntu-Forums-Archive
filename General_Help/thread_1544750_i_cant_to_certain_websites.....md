---
title: "i cant to certain websites...."
date: 2010-08-02
forum: General Help
---

### Post by snooty29 on 2010-08-02
i've been trying to login to many websites and i cant. what can i do to fix this problem? ive tried doing the sudo apt-get autoclean and it done it but its not fixing my problem. if anyone can help me fix this i would greatly appreciate it. :-k

---

### Post by corrytonapple on 2010-08-02
More info like wired or wireless connction, your browser and ubuntu version, and what kind of sites you trying to visit( secure or unsecure) would be usefull.

---

### Post by worksofcraft on 2010-08-03
It's funny you should mention this... I just had a similar problem [http://ubuntuforums.org/showthread.php?t=1544440](http://ubuntuforums.org/showthread.php?t=1544440)

In my case it had nothing to do with Ubuntu (because it happened when I booted to windows too), or my browser and it mysteriously fixed itself earlier today.

Try logging in via a proxy server. It might be a similar problem.

---

### Post by lisati on 2010-08-03
> **worksofcraft said:**
> It's funny you should mention this... I just had a similar problem [http://ubuntuforums.org/showthread.php?t=1544440](http://ubuntuforums.org/showthread.php?t=1544440)

In my case it had nothing to do with Ubuntu (because it happened when I booted to windows too), or my browser and it mysteriously fixed itself earlier today.

Try logging in via a proxy server. It might be a similar problem.

I saw your thread and the other staff member's comments.

@snooty29: It's unlikely the doing a sudo apt-get autoclean will help. It's more likely to be something similar to the routing problem mentioned by cariboo907 in worksofcraft's thread. If so, your ISP *might* be aware of the problem, and working on fixing it. 
What might potentially be more useful is cleaning firefox's cache. You can do this within Firefox by clicking on tools->clear recent history, and checking the "clear cache" option.

---

### Post by worksofcraft on 2010-08-03
Like right now I'm trying to learn gui programming in Python and what do I get?

The webpage at [http://wiki.python.org/](http://wiki.python.org/) might be temporarily down or it may have moved permanently to a new web address.

Error 324 (net::ERR_EMPTY_RESPONSE): Unknown error.

Z0mg :shock: an "unknown" error ?! What the flip does that mean? Hum... well it means I'll go follow a different link from Google this time round, but there is definitely something strange going on and I don't really know who to talk to about this :(

I try...
$> ping wiki.python.org
PING ximinez.python.org (82.94.164.163) 56(84) bytes of data.
64 bytes from ximinez.python.org (82.94.164.163): icmp_seq=1 ttl=46 time=302 ms
... etcetera
--- ximinez.python.org ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 9010ms
rtt min/avg/max/mdev = 302.418/305.238/315.488/3.934 ms


so their server is up and running just doesn't seem to like my http request

---

