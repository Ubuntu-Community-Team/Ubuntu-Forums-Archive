---
title: "restricting cpu usage by process"
date: 2012-10-03
forum: General Help
---

### Post by malakar.subhendu on 2012-10-03
i have matlab installed in my machine and want to execute a matlab script which will possibly take around 1-1.30 hrs and use my full cpu.
i want to restrict the cpu usage of the program to around 60-70% so that it doesn't heat the laptop too much.

What is the way to do that?

---

### Post by Doug S on 2012-10-03
I would suggest to just set your CPU frequency governors into powersave mode (lock them at the lowest clock frequency) during the long matlab run. You could also use the "userspace" governor and set the frequency to something higher, from the list of available frequencies, if that ends up being too slow. Example (for my i7 computer, adjust for your number of CPUs):```
doug@s15:~/temp$ cat set_cpu_powersave2
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu4/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu5/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu6/cpufreq/scaling_governor
echo "powersave" > /sys/devices/system/cpu/cpu7/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

``````
doug@s15:~/temp$ sudo ./set_cpu_powersave2
[sudo] password for doug:
userspace
userspace
userspace
userspace
userspace
userspace
userspace
userspace
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave

``````
doug@s15:~/temp$ cat set_cpu_inquire
#! /bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
grep MHz /proc/cpuinfo

``````
doug@s15:~/temp$ ./set_cpu_inquire
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000
cpu MHz         : 1600.000

```Hope this helps.
Oh, the available frequencies is here:```
doug@s15:~/temp$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
3401000 3400000 3300000 3100000 3000000 2900000 2800000 2600000 2500000 2400000 2200000 2100000 2000000 1900000 1700000 1600000
```I am assuming your computer supports the frequency scaling stuff with this reply.
 
Edit: You could also try "cpulimit" (sudo apt-get install cpulimit) (Note: I have never used it.)

---

### Post by malakar.subhendu on 2012-10-04
Doug S thanks for the reply. but i want to restrict only a single process to be restricted. i do not want to restrict all the processes.

---

### Post by malakar.subhendu on 2012-10-04
Doug S thanks for the reply. but i want to restrict only a single process.
i do not want to restrict the cpu usage of all the processes.

---

### Post by malakar.subhendu on 2012-10-04
Doug S thanks for the reply. but i want to restrict only a single process. i do not want to restrict cpu usage of all the processes.

---

### Post by Doug S on 2012-10-04
I think "cpulimit" will do what you want. See the line I edited and added to my original reply above.

---

