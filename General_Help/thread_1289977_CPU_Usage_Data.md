---
title: "CPU Usage Data"
date: 2009-10-13
forum: General Help
---

### Post by Spectre5 on 2009-10-13
When using the system monitor applet, if I bring up the main window and view the "resources" tab, it shows the CPU history in real-time.

I'm wonder how I can log and track down what programs are using the system CPU at those times - i.e. I'm looking for a way to see the data behind this graph.  The reason I want this data is because I see a bit of a bump in the CPU usage every 50-70 seconds.  I have a dual-core computer with 64-bit Ubuntu 9.04, fully updated.  The two CPU Usage lines stay around 3-5% each when my computer is just sitting still, then they both go up to ~30% for a second or two before going back down.  I want to know why.

Also, what is "normal" idle CPU usage?  3-5% on each CPU seems a little high when my computer is idle.  I could of course figure out more about this if if I can the data I want from the above step.

Thanks!

---

### Post by tigerking615 on 2009-10-13
By "sitting still," do you mean when you're not doing anything, or when you have nothing other than System Monitor running (no music, IM, browser, etc.)

Even then, if you're watching System Monitor, that still takes up some CPU. I'm not sure why it keeps fluctuating, but mine does that too.

---

### Post by DeMus on 2009-10-13
Open a terminal (Applications -> Accessories -> Terminal) and type ```
top
```
This will give you a list of programs and services currently running, the one taking most of the CPU's on top.
Enlarge your terminal window to see more listings.
Close all running programs and keep focusing on the top line.
To stop :top" type q

---

### Post by Spectre5 on 2009-10-13
> **tigerking615 said:**
> By "sitting still," do you mean when you're not doing anything, or when you have nothing other than System Monitor running (no music, IM, browser, etc.)

Even then, if you're watching System Monitor, that still takes up some CPU. I'm not sure why it keeps fluctuating, but mine does that too.

Ya, I know some fluctuation is normal, but up to 5% on both cores seems a little high to me...by "sitting still," I meant I have gnome up, no programs open except the monitor, and just watching it flow.

---

### Post by Spectre5 on 2009-10-13
> **DeMus said:**
> Open a terminal (Applications -> Accessories -> Terminal) and type ```
top
```
This will give you a list of programs and services currently running, the one taking most of the CPU's on top.
Enlarge your terminal window to see more listings.
Close all running programs and keep focusing on the top line.
To stop :top" type q

I do know about top and have used it before, do you know if there is a way to log the output from top at something like 1/2 sec intervals into a file so I could then plot it?

---

### Post by Spectre5 on 2009-10-13
> **Spectre5 said:**
> I do know about top and have used it before, do you know if there is a way to log the output from top at something like 1/2 sec intervals into a file so I could then plot it?

Looks like you can log output from top via the -b with -n options.  I'll try that.

---

