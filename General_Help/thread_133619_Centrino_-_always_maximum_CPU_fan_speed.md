---
title: "Centrino - always maximum CPU fan speed"
date: 2006-02-20
forum: General Help
---

### Post by andrei33 on 2006-02-20
I just installed Ubuntu 5.10 on my Centrino 1.7 GHz Dell Laptop.

In Windows XP, I barely heard the cpu fan - I only heard it when performing CPU intensive taks.

However, in Ubuntu the fan is always at the maximum speed (It's very noisy).
What causes this?
The CPU is not heavily used - I checked that with top - there are no processes that constantly consume a lot of CPU time.
Maybe the fan speed is set by the CPU frequency and Ubuntu doesn't know how to lower the frequency when the CPU is not used?

Any suggestions/solutions are appreciated.

Thanks

---

### Post by Robgould on 2006-02-20
Check to make sure that powernowd is installed and running.  This is the program that should be scaling back your processor.  You can alos add a couple of things to a gnome panel to help you troubleshoot.  Add these by right clicking on the panel and add to panel.  There is a perromance monitor where you can see CPU load.  There is also one where you can see what frequency your CPU is operating at.  
 
There have been some people having issued with their processors running hard all the time.  
 
[http://www.ubuntuforums.org/showthread.php?t=129877]("http://www.ubuntuforums.org/showthread.php?t=129877")

---

### Post by andrei33 on 2006-02-21
Hello, 

I checked and I have powernowd installed and running.
Also, I enabled that gnome applet, and the CPU frequency is correctly scaled depending on CPU load.

However the fan is still noisy.

The fan doesn't start as soon as I boot into Linux, but rather seems to start when there is a high CPU load, and then never backs down.

Please help if you have anymore suggestions, so that I can get rid of this feeling when I'm using Ubuntu that something is wrong.

Thanks

---

### Post by Robgould on 2006-02-21
I'm really out of suggestions, but I'll bump this for you.  The fan works very well for me on my toshiba laptop.

---

### Post by Revolution on 2006-02-21
I'd be looking at the CPU load anyway.
Maybe something is making it work at 100%?

Whats the report from running top in a console?

---

### Post by andrei33 on 2006-02-21
Top shows no CPU intensive processes; the highest CPU consuming process is usually at 2% or 0%. Also the gnome applet, shows the frequency to be 600MHz most of the time, which is the lowest possible (1700 highest) for my CPU.

Thanks

---

### Post by Revolution on 2006-02-21
Some interesting notes here on CPU fan speed in Centrino machines

[http://home.wanadoo.nl/mvandenburg/topaz9500.html](http://home.wanadoo.nl/mvandenburg/topaz9500.html)

Also here
[http://www.linuxforums.org/forum/linux-laptops/29353-fan-running-acpi-problem.html](http://www.linuxforums.org/forum/linux-laptops/29353-fan-running-acpi-problem.html)

This one is really good.
[http://rffr.de/acpi](http://rffr.de/acpi)

---

### Post by Jagilya on 2007-01-11
Have u got a reply to it ever from anyone?
Thanx.

---

### Post by andrei33 on 2007-01-11
No, I have removed Ubuntu from the laptop.
I haven't tried it with the latest version though (6.10).

Are you experiencing the same problems?

Thanks

---

