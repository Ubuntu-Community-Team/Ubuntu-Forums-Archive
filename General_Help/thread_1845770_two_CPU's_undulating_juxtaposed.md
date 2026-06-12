---
title: "two CPU's undulating juxtaposed"
date: 2011-09-17
forum: General Help
---

### Post by murderd2death on 2011-09-17
so i was running puppy inside virtual box, and i was reading system monitor, and my cpu's were [acting odd]("http://i.imgur.com/a7ZRk.png"). often times they run around the same percentage, but for some reason here, where one was running at 100%, the other wasn't running at all, and they would rise and fall to take eachothers place, exactly mirroring eachother almost perfectly. this isn't a real big problem since puppy ran just fine, i was just curious as to why that was,, and if thats unusual or something to worry about

---

### Post by dcstar on 2011-09-18
> **murderd2death said:**
> so i was running puppy inside virtual box, and i was reading system monitor, and my cpu's were [acting odd]("http://i.imgur.com/a7ZRk.png"). often times they run around the same percentage, but for some reason here, where one was running at 100%, the other wasn't running at all, and they would rise and fall to take eachothers place, exactly mirroring eachother almost perfectly. this isn't a real big problem since puppy ran just fine, **i was just curious as to why that was,, and if thats unusual or something to worry about**

[LIST=1]
[*]Because intelligent OSs share the load between all available CPUs - usually to make sure no "hot spots" develop on the CPU die.
[*]No.
[/LIST]

---

### Post by deserthowler on 2011-09-18
> **murderd2death said:**
> ,, and if thats unusual or something to worry about

Happens all of the time.

Earl

---

### Post by NightwishFan on 2011-09-18
If tasks jump cpus too often you can add this line to /etc/rc.local:
```
echo 1500000 > /proc/sys/kernel/sched_migration_cost &&
```

Or just run that command above as root to make the change temporary. It is not a problem though and the defaults are likely fine.

More background on the issue: It is called 'load balancing' and Linux uses a task scheduler to do so. A task running on a single cpu obviously makes better use of the cpu's cache and thus keeping a task on a single core is better for performance. A task tends to jump cpus or nodes whenever another task preempts it. The command above makes it a bit less likely for the task the be scheduled to another node. This is obviously not the best option for all circumstances or tasks would always try to use the same cpu as much as possible.

---

### Post by iLeet on 2011-09-18
Is your guest OS set to use both CPUs?

---

