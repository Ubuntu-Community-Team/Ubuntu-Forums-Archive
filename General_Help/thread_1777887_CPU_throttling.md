---
title: "CPU throttling"
date: 2011-06-08
forum: General Help
---

### Post by mörgæs on 2011-06-08
In Ubuntu I have been using CPU Frequency Panel Monitor for setting the frequency, which works fine and keeps the computer cool.

[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)

Does anybody know of a similar application for Xubuntu?

---

### Post by TBABill on 2011-06-08
If I'm not mistaken, the kernels are now set with CPUFREQ to automatically trigger to ondemand mode, which kicks your CPU down to about half speed until demand increases, then it incrementally steps up until demand drops again. Having it by default like that keeps your machine cool without intervention. I didn't see very impressive heat results with kernel 2.6.32, but now that I'm up to 2.6.38 the heat issue is pretty much gone altogether.

---

### Post by mörgæs on 2011-06-09
Yes, in the new kernel the problem is much less. I am just trying to get a completely quiet and cool machine. 

Will play around with CPUFREQ and report back.

---

### Post by Toz on 2011-06-09
Install **xfce4-cpufreq-plugin** and add it to your panel.

---

### Post by mörgæs on 2011-06-11
> **Toz said:**
> Install **xfce4-cpufreq-plugin** and add it to your panel.

Getting closer... now I can see the modes 'ondemand', 'powersave' and so on. Depending on the load, the computer switches mode by itself.

Is there a way I can make it stick with 'powersave'?

---

### Post by 3rdalbum on 2011-06-11
I find manual CPU or fan-speed correction to be a chronic waste of time. Computers are here to make our lives easier and to automate repetitive tasks, not to make additional work for ourselves. A computer can determine the correct fan speed or CPU throttle setting in mere microseconds, a human takes a lot longer than that.

Intel's engineers also discovered that OnDemand is the most power-efficient setting. When the CPU gets a load put on it, OnDemand will throttle-up the CPU, causing the workload to be finished quicker and the CPU to go back to sleep quicker. Powersave is only applicable when the CPU will be used for the same period of time regardless (for instance, when watching a movie) but not to its full capacity; but even then I think the "conservative" speed governor might be more appropriate still.

Now that I've given you my little lecture, I'm sure that you know by now whether or not you really want to use the powersave governor. In case you still REALLY want to do it, this page tells you:

[http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling#Using_Frequency_Scaling_Governors](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling#Using_Frequency_Scaling_Governors)

The lesswatts.org website also gives you some handy hints for saving power. Looks like it's been recently updated too.

---

### Post by pqwoerituytrueiwoq on 2011-06-11
if you want to change the default setting
[FONT=Courier New]gksu gedit /etc/init.d/ondemand[/FONT]
line 27

---

### Post by mörgæs on 2011-06-12
Thanks pqw..., it worked (when using mousepad in stead of gedit).

3rdalbum, I always appreciate an educated point of view, though it is not *my* point of view. That is the foundation for learning.

---

