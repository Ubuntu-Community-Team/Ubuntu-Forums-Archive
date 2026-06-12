---
title: "Question about cpufreq_selector"
date: 2006-05-28
forum: General Help
---

### Post by shalinmangar on 2006-05-28
Hi,

I am using the new Dapper RC. I was just wondering whether I can use cpufreq_selector on this system. My system is:
Intel Pentium 4 HT EM64T 3.0GHz
1GB DDR2 RAM
linux-image-2.6.15-23-686

Since the motherboard manufacturer provided a CD with Intel Speedstep software, I just wanted to lower the cpu freq a bit to lower the fan noise.

Trying to use the cpufreq_selector said that cpufreq is not supported on this system. Any help would be appreciated. Thanks.

---

### Post by jobezone on 2006-05-28
This blog post [http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/) has a pretty good run down on how to know if your cpu supports changing the cpu, and how to do it with the cpufreq-selector applet. 
It's possible that the linux module that you need to have loaded for your cpu already is (loaded). But in case it isn't, meaning, in case you followed the above link and saw no frequency steps capability from your cpu, you may need to check if you're using the 686 linux image package, and/or load the module yourself. A good way to "browse" modules available, is to use **modconf**.
Install it:
```
sudo apt-get install modconf
```
Then run it with sudo:
```
sudo modconf
```
Then look inside the "kernel/arch/i386/kernel/cpu/cpufreq" category. It will list a bunch of modules. To load a module, just press enter on it. The module you load with modconf will automatically be loaded on boot (since it adds them to /etc/modules), and if it doesn't give any error, it could mean that you've hit the jackpot .

Perhaps someone with a P4 could help you more, as I have an AMD (I have powernow-k8 loaded, but don't know if this is the correct one for you as well). And if someone notices I "said" something wrong, please correct me.

---

### Post by starkes on 2006-05-28
i think if its supported you should be able to use it by default right?
on my laptop, i added the CPU frequency Monitor to my top panel so i could see what the CPU speed currently is, and then i found some nice configuration files in /sys/devices/system/cpu/cpu0/cpufreq


```

affected_cpus     scaling_available_frequencies  scaling_governor  stats
cpuinfo_cur_freq  scaling_available_governors    scaling_max_freq
cpuinfo_max_freq  scaling_cur_freq               scaling_min_freq
cpuinfo_min_freq  scaling_driver                 scaling_setspeed

```

If you see changes in your speed in the cpu frequency monitor, you can screw with things through these files.

---

### Post by shalinmangar on 2006-05-29
Thanks for the help.

My CPU is a Pentium 4 3GHz HT running the 686 kernel. The system monitor shows two CPUs because of HT.

I installed the module p4-clockmod using modconf. When I use the cpufreq-selector, it modifies the speed of the cpu0 but not the cpu1. Specifying cpu1 with the -c option also does nothing. Is that normal? How do I know that it is actually modifying the speed of the CPU. I can't notice any difference even when I set the frequence to 25% of the capacity.

---

### Post by jobezone on 2006-05-30
About the 2 cpus you have, I don't know, as I don't have any experience with that. As far as knowing the frequency your cpu is at the moment, you could see it with the CPU frequency Monitor applet (right-click on a panel, then choose "add to panel", and choose this specific applet), or you can go into the directory **/sys/devices/system/cpu/cpu0/cpufreq** and see the value of **cpuinfo_cur_freq** by doing:
```
cat cpuinfo_cur_freq
```
You can also "cat" the other files, and you can even change their values, but I'm not too knowledgable on that. Since you have 2 cpus, you'll probably also have this directory to play with: **/sys/devices/system/cpu/cpu1/cpufreq** .

---

### Post by Belyel on 2006-06-14
I know this is an old thread, but I'll shed some light about my experience.  I have the CoreDuo (sweet proc, btw), and used the frequency selector panel tool for cpu0 and cpu1, and was having the same problem modifying cpu1.  I think what happens is that it changes, but does not update the icon properly.  When I checked the frequency using /sys/devices/system/cpu/cpu1/cpufreq with 'cat cpuinfo_cur_freq', it showed 200000 (2Ghz, as expected), then the icon updated.  CPU0 keeps changing for some reason, probably because of the bios throttling the processor.

---

