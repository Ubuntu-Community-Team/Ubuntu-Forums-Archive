---
title: "flush the cache"
date: 2010-09-05
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2010-09-05
Is there a way to do this in 8.04? Last night my system bogged down on me very badly, and after I rebooted it started working normally. This is the first time I've resorted to rebooting to flush cache, but you do what you gotta do. I would rather run a program that will flush it if there is one.

---

### Post by ihatetryingtopickaloginna on 2010-09-11
bump

---

### Post by 73ckn797 on 2010-09-11
What program is creating the cache? Firefox? Something else?

---

### Post by fluffman86 on 2010-09-11
What exactly do you mean by cache? If you mean that a program is bogging a system down, you can get to a terminal by pressing CTRL + ALT + F2 and log in there.

If you know the name of the process that is causing the trouble, e.g., firefox, type:
killall -9 firefox
killall -9 firefox-bin

If you don't know the exact name, run:
top
to list your most resource-intensive processes.

---

### Post by 73ckn797 on 2010-09-11
You can also go to System/Administration/System Monitor and see any running apps.

---

### Post by ihatetryingtopickaloginna on 2010-09-12
It happens when running a Second Life viewer called Snowglobe. I have looked at the processes and there are numerous instances of SLVoice running. But voice doesn't even work in this version I have and is turned off by default. When I start killing them off, the system speeds back up.

And when I say cache, I come from previously running OS/2 and then Windows systems. There was always a program to flush the memory of things that weren't being used, stuff that was getting loaded for whatever reason and then just sitting there and slowing the system down. So I hoped that there was a program like that, even though I haven't found one yet.

---

