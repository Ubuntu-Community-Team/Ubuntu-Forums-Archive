---
title: "Wake from sleep, PC locks up without Mouse activity?"
date: 2011-10-04
forum: General Help
---

### Post by Superorb on 2011-10-04
I searched through a lot of posts and didn't find anyone with my problem.

When I resume from sleep, after a few seconds of not using the mouse everything locks up. If I move the mouse around right when it wakes and I continue to do so for 30 seconds or so, everything seems to be Ok. Is there any reason why it would lock up without mouse activity? It just seems weird. I tried unplugging and re plugging in the wireless keyboard/mouse and it didn't help.

11.04 Ubuntu Classic
i3-2100 (using integrated graphics)
H67 ITX motherboard
USB wireless keyboard/mouse

Ideas?

---

### Post by jonnyboysmithy on 2011-10-04
What graphics driver are you using? I've had some lockups because of a experimental driver I had installed.
Other than that I cant think of much.

---

### Post by Superorb on 2011-10-05
> **jonnyboysmithy said:**
> What graphics driver are you using? I've had some lockups because of a experimental driver I had installed.
Other than that I cant think of much.
I'm using the driver that came with 11.04 with the Intel HD2000 integrated graphics from the i3-2100.

---

### Post by iiiears on 2011-10-05
Hello, 
first let me say i don't have an answer for you. :/
But.. There is more info in your logs to feed Google.
System>>Administration>>Log File Viewer.
pmsuspendlog
kern.log
dmesg

Risky? sudo nautilus /var/log

Best Wishes.

---

