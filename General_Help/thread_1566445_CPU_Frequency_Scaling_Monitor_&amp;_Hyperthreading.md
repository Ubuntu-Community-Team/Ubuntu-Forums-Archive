---
title: "CPU Frequency Scaling Monitor &amp; Hyperthreading"
date: 2010-09-02
forum: General Help
---

### Post by zaho0006 on 2010-09-02
I recently installed 10.04 and really like it so far, however I was wondering if it is possible to scale all hypertheading cores at once, currently I am using an applet for each and have to use several clicks to get into the desired powerstate.

I have read that with dual cores you will not have the option to go into different powerstates because it scales all cores at once, however the logical cores that show up with hyperthreading allow each to have a different power state, and will show up as different states if I use cpufreq-info in the terminal, so it seems like it is allowing it.
 
Not a huge issue but would just be more convenient.

Thanks for the help

---

### Post by inso_741 on 2010-09-02
[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)
you can control both cores with a script

---

### Post by TBABill on 2010-09-02
Or save a ton of work and install CPUFREQ utilities via Synaptic. Once installed you can setup the configuration by processor or just overall. Since you stated each core, I'll assume you mean CPU 0 and CPU1. You can set one to ondemand and the other to performance, or whatever configuration you choose. I haven't done it, but the options are there to do so. I am making a huge assumption that the processor will allow it (different settings per CPU).
 
In a terminal as ROOT after CPUFREQ is installed:
> cpufreq-set --cpu 0 --governor ondemand
> cpufreq-set --cpu 1 --governor performance
 
Once finished, just run cpufreq-info and see if the text for each CPU is listed with different settings in quotes. In the example above, CPU0 should state "ondemand" and CPU1 "performance". Choose whatever settings you like in place of ondemand and performance.

---

### Post by zaho0006 on 2010-09-02
I apologize for this, I don't think that I described the question very well. Currently I am running this on a single core atom netbook, however since the processor is threaded 2 cores show up.

I was hoping that I would be able to edit the CPU Frequency Scaling Monitor, so that all cores would change to the same powerstate if one had been changed. Currently separate powerstates for each core are allowed.

While its not a big deal on my netbook (I only have to change 2 cores instead of 1), I was debating trying Ubuntu on my work laptop, however I believe that 6 cores would show up in this case, and if it works the same way it would be a pain to change each one at a time whenever I wanted to change the powerstate.

---

### Post by TBABill on 2010-09-03
You could just try the Gnome frequency scaling applet and set the first core displayed (should be CPU 0) to whatever setting you want. Then choose properties and tell it to display only CPU 1, then CPU 2, etc. If they all switched to the setting you chose, which I think they will, then you will have control of all of them from a single setting change.

---

