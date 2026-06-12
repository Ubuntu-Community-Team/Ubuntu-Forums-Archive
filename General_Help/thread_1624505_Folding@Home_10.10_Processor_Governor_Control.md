---
title: "Folding@Home 10.10 Processor Governor Control"
date: 2010-11-17
forum: General Help
---

### Post by motonnerd on 2010-11-17
Alright, I've been working for a few days off and on on this problem.  Here it is:

I'm running a 64-bit Ubuntu 10.10 install.  I'm trying to run Folding@Home (and am running it through Origami using the nscd fix) without giving it free rein over my processors, especially considering that I would like to have it running while I'm taking notes in class, an activity which doesn't justify an i5.  However, I also would like to get more than an hour (or less) out of the battery.    I recall running Folding@Home in a previous version of Ubuntu (9.10?) and it had the perfect behavior:  The processor stayed at it's lowest clock and all cpu cycles were used, because the FAH process had the lowest priority (nice value of 19 if memory serves) and the CPU governor was set to ignore the nice load.  Whenever I launched anything, it would simply cut into the CPU time of the FAH process.  I'd like to replicate this behavior on 10.10.

The problem is that all the fixes I've found are only applicable to 10.04.  This includes:
     Creating a startup script with the commands:
```
echo 1 | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/ondemand/ignore_nice_load
```          These commands (4 'processors', 2 cores w/ HT) work for a little bit, but don't work on reboot -- even when putting them in a startup script I made for conky and putting them in /etc/rc.local or /etc/init.d/local according to this guide: [https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto) . Using the sysfs package and appropriately editing sysfs.conf also fails to produce results.

As it stands I'm using the cpulimit package (preinstalled) to slow down the process so it doesn't use enough clock cycles to run up the clock on the CPU (though occasionally it still does if I open a program, etc.)

Also, I've had even less success with my other machine, but if I get it working on the laptop I'll be happy.

I'd much appreciate any help with this.
](*,)

---

### Post by motonnerd on 2010-11-17
Did ever more digging and finally tracked down a post which helped with setting the ignore_nice_load variable -- the solution is to go into /etc/init.d/ondemand and add:
```
echo 1 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
```
after the 'done' (but on a new line) within the aforementioned file.

I have also tested it and can confirm that the variables are set automatically (hooray!).

At boot I see that there's still something making my cores clock higher -- which is going to eat battery life.  That may well be unrelated or something within the system and out of userland; but ten minutes in and it still hasn't settled down; there's still sporadic jumps up in the cpu clock.  I suppose for now I'll just have it go to powersave when I take the laptop off of power and when on power cpulimit the F@H process so my CPU isn't constantly running 20C over idle.

Any insights are appreciated.

---

### Post by motonnerd on 2010-11-18
Interesting comparison -- my uniprocessor machine is operating just as I have desired.  Ironically, though, this is the desktop.  The laptop's idle cpu usage is usually <5%, so I've set cpulimit to keep the F@H process below 90% and for the most part the cpu clocks stay low.
Why the different behavior?  If anything, shouldn't the laptop be prone to resist scaling up processor usage?  I know that the ondemand governor prefers to get the work done quickly and then idle the cpu, I guess that's what it's getting at.  Perhaps it has to do with the interplay between a hyper-threading processor and Origami detecting (and I assume configuring the SMP client for) four cores, though there's only two physical cores.

---

### Post by dcstar on 2010-11-18
> **motonnerd said:**
> Alright, I've been working for a few days off and on on this problem.  Here it is:

I'm running a 64-bit Ubuntu 10.10 install.  I'm trying to run Folding@Home (and am running it through Origami using the nscd fix) without giving it free rein over my processors, especially considering that I would like to have it running while I'm taking notes in class, an activity which doesn't justify an i5.  However, I also would like to get more than an hour (or less) out of the battery.    I recall running Folding@Home in a previous version of Ubuntu (9.10?) and it had the perfect behavior:  The processor stayed at it's lowest clock and all cpu cycles were used, because the FAH process had the lowest priority (nice value of 19 if memory serves) and the CPU governor was set to ignore the nice load.  Whenever I launched anything, it would simply cut into the CPU time of the FAH process.  I'd like to replicate this behavior on 10.10.
...........
I'd much appreciate any help with this.
](*,)

Install the **powernowd** package, niced processes will **not** up the clock speed by default.

---

### Post by motonnerd on 2010-11-19
That did it!  So now I have the desktop running without the daemon and the laptop running with it, otherwise identical configurations.  Looks like there's something different about powernowd vs. the builtin governor -- though apparently powernowd uses it as a backend?  (for some reason between that an some assumptions I had made I had got the impression that powernowd wouldn't solve my problem).  One way or another, it seems to be able to better handle multiple cores or something like that -- maybe the ondemand daemon doesn't offload processes to other cores or...  I have no idea.

Thanks for the help!

---

### Post by motonnerd on 2010-11-28
Interesting -- I either didn't notice it or something changed, but it appears that powernowd doesn't control the voltage on the i5 as well as I'd like it to -- CPU temperature was still really high.  Ironically, the power drain wasn't what I expected it to be.  As such I'm going to try to figure out what's different on the desktop which is keeping it from counting nice'd processes and let you know if I find it.  For now, a small utility to switch all my CPUs to conservative when off A/C power.

---

