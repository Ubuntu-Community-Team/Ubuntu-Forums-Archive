---
title: "At what load is a cpu considered &quot;peged&quot;"
date: 2010-05-21
forum: General Help
---

### Post by jerome1232 on 2010-05-21
And does it take into account whether you have multiple processors or cores.

I ask because My desktop (a dual core) can reach loads of 2.5 or so and still feel very responsive, when my ancient single core voice server can reach a load of 1.7 and the command line starts feeling sluggish over ssh, on a lan connection. (ie typing takes a second to catch up, hitting tab it sits and thinks for long enough that I would be better off just typing the whole thing out)

I'm talking about the 5 minute average.

---

### Post by robvas on 2010-05-21
Holding a solid 100% is 'pegged'

I think the way the load # works is 1.0 means 1 CPU is busy 100% of the time. .5 would mean 50%, so anything over 1.0 (actually, close to 1.0) would be bad for a single-CPU system.

2.5 on a dual core feels more like 1.25 on a single core, that's why the 1.7 feels so slow to you. Not to mention it's probably quite a bit slower computer in the first place, which doesn't help.

---

### Post by tgalati4 on 2010-05-21
sudo apt-get install htop
htop

---

### Post by dcstar on 2010-05-21
> **jerome1232 said:**
> And does it take into account whether you have multiple processors or cores.

I ask because My desktop (a dual core) can reach loads of 2.5 or so and still feel very responsive, when my ancient single core voice server can reach a load of 1.7 and the command line starts feeling sluggish over ssh, on a lan connection. (ie typing takes a second to catch up, hitting tab it sits and thinks for long enough that I would be better off just typing the whole thing out)

I'm talking about the 5 minute average.

CPU load rarely is a factor in "sluggish" performance, more likely there are other issues causing a bottleneck which manifests itself this way.

Most modern systems have more than enough CPU grunt that they will ever need for normal use, disk I/O and general bad configuration are more likely to be problems.

---

### Post by jerome1232 on 2010-05-21
tbh it's not a modern cpu, it's an old computer I grabbed from a friend, they were going to throw it away and I wanted it as a mumble server. 500 mhz celeron with 112 MB's of ram.

It's served that purpose well for a few years now.

I started using it to toss backups of my personal files as well and rsync'ing to it can throw it up to 3.00 Load, usually 2.5 and it get's pretty unresponsive, I was thinking (and I think I'm correct) that the cpu in it is just getting overtaxed and I may be due to just shell out a little cash and get a more up to date computer for the task.

---

### Post by tgalati4 on 2010-05-21
Celeron is a crappy processor and only 112 MB of RAM will be a bottleneck.  Buy some used RAM on craigslist and it will be more responsive.  Look for jumpers to overclock the processor.  Some celerons of that vintage can go up to 1 GHz without problems.

---

### Post by BoneKracker on 2010-05-21
Here's a good, if somewhat simplified, explanation:

[http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages](http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages)

vmstat also provides a nice concise picture (once you read the man page and know what the various fields mean).

Top and htop server their purpose as diagnostic tools, but are themselves resource pigs.

---

