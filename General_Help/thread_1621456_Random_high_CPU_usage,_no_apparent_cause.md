---
title: "Random high CPU usage, no apparent cause"
date: 2010-11-14
forum: General Help
---

### Post by Sirron on 2010-11-14
Every so often - usually after listening to a lot of music with Banshee or watching videos in VLC - my CPU usage goes up to 80%+ (seemingly across more than one core) for no apparent reason and there's nothing I can do to stop it, there's no process that appears in System Monitor with that much usage, typically it's all 0% with maybe 10% for the system monitor itself.

If I try to logout, the Gnome panels disappear, but then it just sits with the mouse pointer over the wallpaper and I have to use the Reset button.

My CPU is a Core i7 with hyperthreading enabled, so 8 logical cores.

I'm using Ubuntu 10.10 x64 fully updated.

Any help would be greatly appreciated!

One other thing, on a related note: with Hyperthreading enabled, that means that one physical core represents two logical cores right? So if I had two threads that required a lot of processing, what is there to stop them both ending up on the same physical CPU, when others are doing nothing? Would that actually matter? Thanks

---

### Post by pqwoerituytrueiwoq on 2010-11-14
it is probably the update manager checking for updates

---

### Post by Sirron on 2010-11-14
Thanks for the reply pqwoerituytrueiwoq, I don't think it's update related since we're talking about really serious CPU usage here. If I run apt-get update manually, I can't see any spike in System Monitor at all, all the cores remain below 20%.

---

### Post by dino99 on 2010-11-14
let system-monitor open to watch which process(es) are the most active.

---

### Post by Sirron on 2010-11-14
Thanks, could you please explain that suggestion more?

---

### Post by pqwoerituytrueiwoq on 2010-11-14
basically keep an eye on your running programs with
gnome-system-monitor
if you want to see root's processes
gksu gnome-system-monitor
sort by cpu usage

---

### Post by dino99 on 2010-11-14
with synaptic, install gnome-system-monitor (if not already installed)

then rightclick on top panel to add system-monitor, then enable the settings you want in its property. That made, double click on it to open its screen, choose "process" tab to glance at %cpu of each process (the most used are on top list for ease)

---

### Post by Sirron on 2010-11-14
Awesome, will do.

I didn't know root had processes I couldn't see :D

---

