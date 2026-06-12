---
title: "need performance tools"
date: 2010-02-24
forum: General Help
---

### Post by el_fiqs on 2010-02-24
[FONT=Courier New][SIZE=3]is there any performance tool for linux? i av found phoronix but it cant provide testing on memory, CPU, hard disk utilization and also stress test. please help me :confused:[/SIZE][/FONT]

---

### Post by dabl on 2010-02-24
Not sure exactly what you have in mind, but a Parted Magic Live CD has quite a few tools on it -- CPU benchmarking, a GUI front-end for smartmon tool (hard drive testing), etc.

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

If you're looking for monitoring, then there are gkrellm and conky, to name two.  Searching this forum or a google on "conky" will give you enough to keep you busy the rest of today. :D

---

### Post by el_fiqs on 2010-02-24
i actually want the performance tools for IDS, meaning that when i run the IDS. the tools can read how much memory usage, cpu reading and hard disk utilization. just give the reading based on criteria i needs not give reading on all services running like task manager in windows. in specific, one output per criteria. please help... :confused:

---

### Post by 3rdalbum on 2010-02-24
> **el_fiqs said:**
> [FONT=Courier New][SIZE=3]is there any performance tool for linux? i av found phoronix but it cant provide testing on memory, CPU, hard disk utilization and also stress test. please help me :confused:[/SIZE][/FONT]

I suggest you take a closer look at Phoronix Test Suite. It can do benchmarking for memory and CPU power, as well as stress testing with 'cpuburn'.

If you want to know hard disk utilization, go to System > Administration > System Monitor and look at the File Systems tab.

---

### Post by el_fiqs on 2010-04-02
i av try the phoronix but it is not suitable.

can anyone suggest a performance monitor tools that can monitor :

- cpu usage that can focus on only one service such as snort.
- memory usage that also focus only on one service like snort.
- hard disk utilization that only focus on one service such as snort.

i hope that the tools also can provide graph as a output :confused:

please help..

---

