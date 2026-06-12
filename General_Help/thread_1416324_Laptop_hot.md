---
title: "Laptop hot"
date: 2010-02-25
forum: General Help
---

### Post by sincerelyydavid on 2010-02-25
when i had windows 7, my laptop was never hot, NEVER. now i'm running ubuntu, full install. and it gets really hot when i'm on it. is this a driver issue? does this only happen on ubuntu vs. other distros? i've searched the forums, but couldn't find a solution.

---

### Post by n0dix on 2010-02-26
Specifications of the laptop?
There is a program that get 100% CPU process?

---

### Post by PaulReaver on 2010-02-26
right click gnome-panel(taskbar), add to panel, cpu frequency scaling monitor. 
try changing cpu frequency scaling from performance to on-demand
might help.
works with my netbook (which doesn't have a heatsink)

---

### Post by Andreas1 on 2010-02-26
open gnome-system-monitor and watch cpu usage, see if any process goes 100%

---

### Post by sincerelyydavid on 2010-02-26
i'm using Disk Usage Analyzer under applications>accessories. i scanned home, nothing is 100% except for <my name>. and then mozilla's 50.8%. everything else is less than 50%.
Paulreaver: it's already on on-demand.
N0dix: i don't know the specifications of my laptop lol sorry.

---

### Post by Andreas1 on 2010-02-27
> **sincerelyydavid said:**
> i'm using Disk Usage Analyzer under applications>accessories. i scanned home, nothing is 100% except for <my name>. and then mozilla's 50.8%. everything else is less than 50%.
Paulreaver: it's already on on-demand.
N0dix: i don't know the specifications of my laptop lol sorry.

ok there is a misunderstanding here. cpu is the processor (central processing unit), if it is 100% busy doing calculations for some program then it gets hot. this has nothing to do with hard disk space.

press Alt+F2
type "gnome-system-monitor"
in the "resources" tab you can see your cpu usage, is it at 100%?
if so, go to "processes" tab, sort by "% cpu" and see which process uses (near) 100%.

---

### Post by Mark Phelps on 2010-02-27
> **sincerelyydavid said:**
> when i had windows 7, my laptop was never hot, NEVER. now i'm running ubuntu, full install. and it gets really hot when i'm on it. is this a driver issue? does this only happen on ubuntu vs. other distros? i've searched the forums, but couldn't find a solution.

To prevent laptops from overheating, two actions typically need to take place: fan speeds have to throttle up to keep the CPU cool during heavy use, CPU speeds need to throttle down to keep the laptop cool during idle.

In MS Windows (in general) the drivers and SW for doing this are installed by the vendors prior to your using the laptops. Why? Because they warranty the laptop and don't want to deal with the hassle of you returning it because it's overheating.

Linux is a different story because these same vendors generally do NOT supply SW or drivers to do the same stuff.  The Linux community, and the distro developers, have to do that.

Unfortunately, when the kernel changes, or when driver infrastructures change (as in dropping HAL), the game starts all over again for Linux users -- and with Ubuntu 9.10, given the number of posts about overheating laptops, it seems that there is farther to go now to handle the heating problem.

Sorry ... don't have a solution.  Just wanted to let you know you're not alone in this overheating laptop problem.

---

### Post by s.fox on 2010-02-27
> **Mark Phelps said:**
> Just wanted to let you know you're not alone in this overheating laptop problem.

I had this problem also,  I resolved it by purchasing a laptop cooling pad.  Not a perfect solution by any means,  but thought I should mention it as an option.  :D

-Silver Fox

---

### Post by sincerelyydavid on 2010-02-27
Andreas1: under resources, i have  CPU1: 2-10%, and CPU2: 5-10%.
and Mark Phelps: so is ubuntu the only distro having this problem?

---

### Post by sincerelyydavid on 2010-02-28
bump. are other distros having this same problem?

---

