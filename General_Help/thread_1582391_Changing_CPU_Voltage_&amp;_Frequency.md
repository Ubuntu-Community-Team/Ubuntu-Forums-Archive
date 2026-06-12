---
title: "Changing CPU Voltage &amp; Frequency"
date: 2010-09-26
forum: General Help
---

### Post by charliehorse55 on 2010-09-26
I am doing a project on how power consumption of a CPU can be improved by underclocking the lower P-states and overclocking the highest p-state.In this way you can increase both the performance of the chip and it's average power usage (assuming you don't run the chip at 100% 24/7). 

To do this project I need to be able to change the voltage and frequency of the chip for all of the different p-states of the chip. On Windows I can use k10stat, RMClock or AMD Overdrive. 

What can I use in Linux? I found k10ctl, but it always complained about not being able to find /dev/cpu/0, so I looked in /dev and noticed that their isn't even a cpu directory in there!

I have a moderate amount of experience so I don't mind changing kernels or doing other hard tasks to get this to work.

---

### Post by andrewthomas on 2010-09-26
Do you have the cpufrequtils package installed?

---

### Post by charliehorse55 on 2010-09-26
Yes, it doesn't work unfortunatley. 

$ sudo cpufreqd-get
No cpufreqd socket found

EDIT: Besides, I don't think it allows voltage control

---

### Post by charliehorse55 on 2010-10-01
bump

---

### Post by doru001 on 2011-08-30
cpufreqd?

---

