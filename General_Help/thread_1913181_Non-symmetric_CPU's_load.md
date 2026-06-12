---
title: "Non-symmetric CPU's load"
date: 2012-01-22
forum: General Help
---

### Post by avi9526 on 2012-01-22
Ubuntu 11.10 amd64 (with unity and gnome and kde)
CPU: AMD Phenom II X4 955

I launch "gnome-system-monitor" and found that my CPU's loaded not symmetrically.
Most of all loaded CPU1 and CPU2, lowest load have CPU4. I don't sure that it is normal.
If I run some application that highly load only one CPU - most of time loaded CPU1 and CPU2.
This is problem or it should be like this?

[[IMG]http://storage4.static.itmages.ru/i/12/0122/s_1327224724_2632582_06f122e5c4.png[/IMG]]("http://itmages.ru/image/view/397942/06f122e5")

---

### Post by mcduck on 2012-01-22
That is perfectly normal. Many kinds of tasks simply can't be broken into separate threads for different CPU's/cores to run, so they will only use one core at a time.

---

### Post by avi9526 on 2012-01-22
I understand that many applications can't use all cores, but it's not what I talking about. Problem that when my system is idle (applications that require 100% load not running) and I run gnome-system-monitor - I see that CPU4 always loaded lower than others. Even if some application load one core for 100%, CPU4 loaded for shorter period than other CPU's. On win7 no such problem.
CPU4 slacker)

---

### Post by mcduck on 2012-01-22
It simply depends on how many threads are running on each core at the moment when a new thread is created, and how much CPU time each of them is using.

I wouldn't worry about it, it makes no difference really, and all the cores will be used when needed. And of course if there isn't much work to do, it's more effective to use fewer cores and let the other ones sleep, that will both save power and reduce heat. (and in that situation it makes no difference which are the cores that are sued and which ones are sleeping)

Of course if you want to be absolutely sure all the cores are working fine, just try running some task that effectively uses as many cores as you have. Compressing  music on multiple threads, or some video rendering task, and you should see all the cores used pretty much equally.

Edit: also depending a bit on the processor internal architecture, some of the cores may be sharing cache in which case it might be more effective to run threads of the same application on the cores sharing the same cache. Which would make the scheduler favour first and second core, for example, on low load situation.

---

