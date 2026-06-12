---
title: "System CPU speed"
date: 2010-01-21
forum: General Help
---

### Post by texas.chef94 on 2010-01-21
SOLVED thanks much

---

### Post by iponeverything on 2010-01-21
you can right click on the status bar go to add and add the cpu freq applet. 

Or you can open a terminal and type:

```
cat /proc/cpuinfo

```

---

### Post by tommcd on 2010-01-21
I like using **gkrellm**, which is a lightweight system monitor that can moitor CPU and GPU temps, CPU and memory usage, hard drive access, etc. You can install gkrellm from apt-get or synaptic.
You may need to add **lm_sensors** and run that to get the system temps. I think Ubuntu includes lm_sensors when you install gkrellm.

---

