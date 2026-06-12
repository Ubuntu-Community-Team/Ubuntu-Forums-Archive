---
title: "Memory Savings: Using xterm instead of gnome-terminal?"
date: 2012-01-26
forum: General Help
---

### Post by draco verum on 2012-01-26
I'd hoped I wouldn't have to ask. Ubuntu has come a long way since I first tried it, and I've managed to work through most of the real issues. 

However, right now I have memory constraints and I'd like to lower the desktop environments usage. I read about using Xterm instead of gnome-terminal to save on memory and swaps. I have to be honest, I understand memory, and swap files but I have no idea what gnome terminal is doing or where/how I would go about changing the config files to make gnome use xterm instead. I thought about switching from gnome to xdm in order to lower memory usage even further, but even THIS simple task seemed complex to me, let alone changing out the window manager. 

I'm running Ubuntu 10.10 32-Bit Kernel 2.6.35-32-generic GNOME 2.32.0

Please help. Thanks.

d

---

### Post by Paqman on 2012-01-26
Using a different terminal is unlikely to save you a lot of memory unless you like to have a ton of terminal windows open concurrently.

How much RAM do you actually have?

---

### Post by wolfen69 on 2012-01-26
You could just install the Lubuntu desktop to save on memory.
```
sudo apt-get install lubuntu-desktop
```
It should use much less than regular ubuntu, and generally be faster.

---

### Post by draco verum on 2012-01-26
212MB total. I'll be upgrading soon. But we have to hold out a bit longer. I thought now when it was necessary was a good time to tweak it anyhow. We're running Java and Flash apps and a 35MB savings makes all of the difference in the world. I've noticed that as it has to swap things out, some stay swapped out and there's more memory available. When that happens, the apps run well enough to be usable. I'm not sure what the most direct route to memory savings is. But thanks for responding so quickly.

--will installing lubuntu also remove the currently installed desktop?

d

---

### Post by draco verum on 2012-01-26
Installed Lubuntu...really like the look of it...but.. Now 120MB instead of 98MB used. Gnome is still being loaded. Synaptic Package Manager? 

daf

---

### Post by ajgreeny on 2012-01-26
> **draco verum said:**
> Installed Lubuntu...really like the look of it...but.. Now 120MB instead of 98MB used. Gnome is still being loaded. Synaptic Package Manager? 

daf
You managed to run ubuntu with a gnome desktop and only use 98MB ram?

How did you do that?  There can not have been much running that would normally be on a default ubuntu.  If you managed to tweak you memory use in gnome down to 98MB, I am sure you must be able to find a way to reduce your lxde memory use similarly.

---

### Post by draco verum on 2012-01-26
THere were times when the system monitor read 64.4M or something in the Resources graph. I'm assuming it's because lots of things were swapped out and sleeping. I dunno. That said. Where do I go to unload these GNOME screen savers and what-not? What else can I do to reduce memory consumption? I'm down to 82 MB. I'm shooting for 70 MB or so.

Any help is appreciated. Sorry I don't know a thing and I really don't know where to continue looking. 

THanks

d

---

### Post by draco verum on 2012-01-26
K...got it down to 77.5 in lubuntu with System Monitor open .System Monitor shows itself at 7.1M so thats real near the goal of 70MB. If anyone can think of other ways to lower memory consumption and still run a browser w/ Java and Flash..I'd appreciate it. Thanks.


d

---

### Post by wolfen69 on 2012-01-26
To be honest, you probably won't get it much lower than that. You *could* wipe your install and do a minimal install of ubuntu, then install openbox, but you probably wouldn't save much more memory.

Better yet, if there is an electronics recycling center in your area, you could get some more memory *real* cheap. I would try to get 1gb (2 x 512) if you can.

---

