---
title: "Job scheduling software"
date: 2011-04-22
forum: General Help
---

### Post by cbabef on 2011-04-22
I would like your opinion on which software to install for job scheduling on a simple desktop.  

My situation is as follows.  Our research lab has a desktop (quad-core) which I'll use as an extra Linux machine for scientific software.

I want a few of my Windows-colleagues to be able to use this computing power, either indirectly by requesting the execution of specific jobs through a website (Apache server), or perhaps directly using SSH.

The thing is that I want to be able to have the requested jobs scheduled automatically, (1) so that I always have priority (the jobs of my colleagues can wait and run over night or when I'm away), and (2) the pending jobs are nicely scheduled in function of available computing resources to avoid jams.

I used to work on a large university cluster which used [PBS]("http://en.wikipedia.org/wiki/Portable_Batch_System") (worked great).  This simple desktop, however, clearly is not a cluster.  After Googling the whole afternoon, I am considering free alternatives such as [SLURM]("https://computing.llnl.gov/linux/slurm/") or [TORQUE]("http://www.clusterresources.com/products/torque-resource-manager.php"), but perhaps this is an overkill.  Any advise on this?

---

### Post by deconstrained on 2011-04-22
For prioritizing CPU consumption, a much simpler solution would be setting the nice levels of your running programs using nice (when you invoke/spawn them) or renice (to change nice levels of already-running programs). You could also give the [Auto-Nice daemon](http://linux.die.net/man/8/and) a try.

For scheduling jobs, i.e. having them run at a later time, what's wrong with just atd/cron? PBS would indeed be totally overkill. You could write a simple script to check the CPU consumption (if the jobs are resource-intensive) and submits/spawns them when the coast is clear.

Edit:
[http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html](http://www.cyberciti.biz/tips/how-do-i-find-out-linux-cpu-utilization.html)
mpstat combined with a little awk magic will get you the CPU utilization for each core.

---

