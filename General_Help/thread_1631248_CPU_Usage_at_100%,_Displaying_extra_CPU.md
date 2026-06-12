---
title: "CPU Usage at 100%, Displaying extra CPU?"
date: 2010-11-26
forum: General Help
---

### Post by brendan_charles on 2010-11-26
Hi, I'm relatively new with Ubuntu- but I'm pretty experienced otherwise with computers. I just installed Ubuntu on my Intel machine and it seemed to be running a little slow so I checked the System Monitor and found that there were 2 CPU's being displayed (I only have 1) and that one or both were maxed out at 100%. 

What I have for hardware is one Intel Atom 1.6Ghz processor, with 2GB of ram.  When I check what resources are running, none of them seem to be taking up that much memory (firefox being the most at 60mb). 

Any advice on what might be going on here? How is it displaying 2 CPU's when I only have one? And why are they peaking so much when I'm doing all that much on my PC?

Thanks for any helo!

---

### Post by tad1073 on 2010-11-26
> **brendan_charles said:**
> Hi, I'm relatively new with Ubuntu- but I'm pretty experienced otherwise with computers. I just installed Ubuntu on my Intel machine and it seemed to be running a little slow so I checked the System Monitor and found that there were 2 CPU's being displayed (I only have 1) and that one or both were maxed out at 100%. 

What I have for hardware is one Intel Atom 1.6Ghz processor, with 2GB of ram.  When I check what resources are running, none of them seem to be taking up that much memory (firefox being the most at 60mb). 

Any advice on what might be going on here? How is it displaying 2 CPU's when I only have one? And why are they peaking so much when I'm doing all that much on my PC?

Thanks for any helo!

does your processor support hyper threading?

---

### Post by dino99 on 2010-11-26
is flash installed ? (might be the problem) look at it into synaptic: system admin synaptic (flashplugin-installer from canonical partner repo)

you can try to uninstall it with synaptic, to see the difference.

Other possible reason: compiz

---

### Post by Jouke74 on 2010-11-26
Your Atom processor has Intel's hyperthreading. The "hyperthreading CPU" is visible as a second CPU under all operating systems including Ubuntu. This is normal behavior of your CPU / computer.

The problem why you are having such a load of cpu use is something else. If you are running Firefox with any flash video / advertisement on, then there is the reason for your high CPU use. Else you can use the command "top" to figure out which program is eating your resources.

---

