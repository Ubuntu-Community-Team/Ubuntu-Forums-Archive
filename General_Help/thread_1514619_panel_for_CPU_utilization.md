---
title: "panel for CPU utilization"
date: 2010-06-21
forum: General Help
---

### Post by MarD on 2010-06-21
Hello,

is there any package to check the CPU utilization as a panel in genom. 

I do not mean that i have to call the system monitor to check the CPU utilization but i want to see it always in the panel just lake the date panel.

Thanks

---

### Post by bruno9779 on 2010-06-21
System Monitor applet shows you graphs for CPU and optionally many other things.

Otherwise, conky is great.

---

### Post by WorMzy on 2010-06-21
What about the System Monitor applet? It displays histograms for any combination of Processor, Memory, Network, Swap Space, Load, and Harddisk usage. You can customise the size of the histograms, the update rate, and the colours it draws with.

To get it, just right click on the panel, choose "Add to panel...", search for System Monitor, and drag it on to the panel.

---

### Post by MarD on 2010-06-21
You did not understand me...

I do know that system monitor shows me alot of thing. but each time i have to call it. 

I do need to check the cpu utilization just lake the date. So you always have a look on it without hitting anything.


Best,
MarD

---

### Post by bruno9779 on 2010-06-21
Then conky.

---

### Post by WorMzy on 2010-06-21
You misunderstand us, we're not saying open the System Monitor, we're saying add the System Monitor *applet* to the panels. It looks like this: [IMG]http://www.ubuntu-pics.de/bild/87855/top_expanded_edge_panel_007_B4CSe7.png[/IMG]


Conky is another good suggestion that I didn't think to mention. It's very configurable. Here's what mine looks like:
[[img]http://www.ubuntu-pics.de/thumb/87856/workspace_1_008_k74JpD.png[/img]](http://www.ubuntu-pics.de/bild/87856/workspace_1_008_k74JpD.png)
As you see, I have my two CPU cores listed at the top, followed by a bar which fills up as more CPU is used.

---

### Post by MarD on 2010-06-21
I have added the monitor applet to the panel but i do see just the first segment of the graph which you attached.

My laptop has 2 cpu cores. So i want to see the utilization(or frequency) for each processor in the panel.

How can i do that?

any suggestion.

---

### Post by WorMzy on 2010-06-21
Right-click on the applet and choose Preferences to customise the appearance of it.

But if you want to see each core separately, then conky is the way to go.

---

### Post by philinux on 2010-06-21
There is also the CPU Frequency Scaling Monitor applet that can be added to the panel.

---

