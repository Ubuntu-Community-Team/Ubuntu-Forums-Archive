---
title: "How can I check the CPU temp?"
date: 2011-07-29
forum: General Help
---

### Post by Skara Brae on 2011-07-29
Yesterday I have replaced my Athlon64 3000+ with an Athlon64 4000+ on an Asus A8V Deluxe motherboard with 2 GB RAM and a 6600GT.
(I have built my own core-i5 based machine a few weeks ago, just to show that I am not living in the past when it comes to PC hardware :) ).

In WinXP (dual boot with Ubuntu), the idle core temperature is (on average) 40°C (104°F) with Q-Fan enabled in the BIOS. (Isn't this a bit high?)
With AMD's "Cool'n'Quiet" enabled and "Q-Fan" disabled in the BIOS, the CPU fan makes too much noise (for my taste).
With both "Cool'n'Quiet" and "Q-Fan" enabled, the idle core temp is (on avarage) 27°C (80.6°F). The CPU speed drops to 1 GHz (instead of the 4000+'s 2.4 GHz).

This is all according to the Windows program "CoreTemp", and with the original, stock heatsink. I was struggling with a "Freezer 64 Pro" that came with the 4000+, and just ended up putting the stock cooler back on it (took 10 seconds).

-oo-

To get to the point: how can I measure the temperature of my "new" (second-hand) CPU in Ubuntu?

Does an OS influence the temperature of a CPU?

I have searched and read about "conky" (which according to Synaptic is installed on my 10.04 system, but I don't see it in the start menu), but it doesn't seem to be/do what I am looking for.

---

### Post by Skara Brae on 2011-07-29
I have just found this:

[http://www.connectedinternet.co.uk/2009/05/24/monitor-cpu-temperatures-in-ubuntu/]("http://www.connectedinternet.co.uk/2009/05/24/monitor-cpu-temperatures-in-ubuntu/")

"Sensors-applet". That seems to do it :)

Core0 temp: 30°C
Core1 temp: 34°C (why two?)
GPU temp: 36°C

---

### Post by Matt__ on 2011-07-29
```
sudo apt-get install hardinfo
```GUI will appear in system tools, or launch from terminal. lot of other useful info besides sensors

two temps as its a dual core cpu with dual sensor.

---

### Post by Skara Brae on 2011-07-29
Matt__

Thank you very much for your reply. Synaptic (the terminal) says that hardinfo is already installed. I don't see it anywhere, though...
I do have Sysinfo (in System Tools).

But that "Sensors Applet" does the trick.

---

### Post by birkopf on 2011-08-17
> **Skara Brae said:**
> 
GPU temp: 36°C


Hi Skara Brae,

Which command did you used in conky to get GPU temp please ? 
It should be something like 
```

${gpu temp} 

```

Could you check for me pls ?

---

### Post by Duncan Williams on 2011-08-17
hardinfo shows up as `System profiler' on my sys:
[IMG]http://files.myopera.com/DuncanWilliams/usercss/hard.png[/IMG]

---

### Post by birkopf on 2011-08-17
> **Duncan Williams said:**
> hardinfo shows up as `System profiler' on my sys:

Thanks... ;-) 
But I was wondering if you have a instruction/code for conkyrc :)

Sorry for not being clear 8-[

---

### Post by Duncan Williams on 2011-08-17
*But I was wondering if you have a instruction/code for conkyrc* 

No, sorry.

---

