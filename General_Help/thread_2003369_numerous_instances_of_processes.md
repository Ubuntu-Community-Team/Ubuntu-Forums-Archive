---
title: "numerous instances of processes"
date: 2012-06-14
forum: General Help
---

### Post by Park Bom on 2012-06-14
I didn't really know how to explain this without a visual aid, so:
[http://i.minus.com/iKKsd83R3eXbq.gif](http://i.minus.com/iKKsd83R3eXbq.gif)


Why would there be so many instances of the same processes? The xfce mixer plugin is what made me notice it; I only have one applet for controlling the volume in my panel, but it lists it 7 or 8 times. 

This occurs all the time, regardless of logging out, rebooting, etc. The gif was taken immediately after signing in; the only thing I did was open the terminal.

Any input would be greatly appreciated!

---

### Post by Ms. Daisy on 2012-06-14
I can't answer your question, but I can give you a tool to look at more details about the processes you're seeing. I'm not on my Ubuntu computer right now but if memory serves me the command is:
 
```
 sudo watch netstat -anlpee
```

---

### Post by Park Bom on 2012-06-25
> **Ms. Daisy said:**
> I can't answer your question, but I can give you a tool to look at more details about the processes you're seeing. I'm not on my Ubuntu computer right now but if memory serves me the command is:
 
```
 sudo watch netstat -anlpee
```

Sorry for the late reply; here is the output-

[IMG]http://i2.lulzimg.com/479802e5b2.png[/IMG]

---

### Post by rai4shu2 on 2012-06-25
I don't know if you've noticed, but those are actually threads, not processes. Given how CPUs nowadays tend to be multicore, this means those applications are more likely to be efficiently making use of your hardware.

If this is a problem for when you use htop, go into Setup (F2), select "Display Options" and select Hide threads.

---

