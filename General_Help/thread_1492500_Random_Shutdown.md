---
title: "Random Shutdown"
date: 2010-05-24
forum: General Help
---

### Post by yoKenny on 2010-05-24
I've found a lot of related threads about this, but none of them actually fits my particular case.
Well' I've been using Ubuntu on my desktop for a while and it worked like a charm. Three months ago, I decided to put a new cpu fan because the old one was gathering dust and I wanted to have lower cpu temps. I decided to buy an Scythe Kabuto, nd installed it with no problems. Windows XP works perfect, but the problems come when I try to start Ubuntu, both from a Live CD or from the HD.
Ubuntu starts normally, but in a short period of time (2~15 minutes) the PC randomly shuts down. I've seen some errors when I restart and try to start Ubuntu again mentioning high CPU tempetatures. The fact is that the CPU temperature never reaches more than 65ºC, so my guess is that there is some problems with the ACPI and temp reading.
What do you people think?


Thanks

---

### Post by yoKenny on 2010-05-25
No one? :(

---

### Post by James78 on 2010-05-25
Ubuntu 10.04 has been said to run hotter. I could suggest that you install some cpufreq stuff to allow throttling the CPU, that way when it's not being used as much, it'll lower the GHz (useful if you use a laptop), and also when the heat is higher it'll slow it down to let it cool down, thus a less chance of freezing. If I remember right, a certain brand of processors, AMD I think, freeze when they get too hot, like a safety mechanism, that and AMD runs hot naturally, combine that with Ubuntu 10.04.. And ya... Just hope your BIOS will allow you to scale the CPU.. Good luck!

Did you put thermal paste on the CPU? It'll help transfer the heat from the CPU to the fan.

---

### Post by yoKenny on 2010-05-25
> **James78 said:**
> Ubuntu 10.04 has been said to run hotter. I could suggest that you install some cpufreq stuff to allow throttling the CPU, that way when it's not being used as much, it'll lower the GHz (useful if you use a laptop), and also when the heat is higher it'll slow it down to let it cool down, thus a less chance of freezing. If I remember right, a certain brand of processors, AMD I think, freeze when they get too hot, like a safety mechanism, that and AMD runs hot naturally, combine that with Ubuntu 10.04.. And ya... Just hope your BIOS will allow you to scale the CPU.. Good luck!

Did you put thermal paste on the CPU? It'll help transfer the heat from the CPU to the fan.
Yeah, I put thermal paste on the CPU, but the problem isn't only on Ubuntu 10.04. All the previous versions and even other Linux OS's have the same problem. While the Live CD is loading, it suddenly stops and tells me to take the CD away. And XP has no problems, I thought it is some kind of bad temp lecture :(

---

### Post by yoKenny on 2010-05-25
And the CPU is Intel (Quad Core) anyway, and always below 65ºC

---

### Post by dino99 on 2010-05-25
its time to look at xsession-errors and logs (system admin log viewer)

---

