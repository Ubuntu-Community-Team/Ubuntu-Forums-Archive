---
title: "Ubuntu unexpectedly shuts down itself  -- why?"
date: 2012-04-23
forum: General Help
---

### Post by alexei_ on 2012-04-23
Ubuntu unexpectedly shuts down itself  -- why?
How to troubleshoot?
How to fix?

---

### Post by newbie-user on 2012-04-23
Check the system log in /var/log/syslog and look for anything that might say restart, reboot, or shutdown.

---

### Post by agillator on 2012-04-23
Also check the system log for anything indicating overheating. If you find nothing in the logs, try using a fan to cool the machine, and if it is a laptop, get the machine off the surface so air can circulate under it. If it is a desktop machine, take a side off so the fan can blow directly inside. Overheating is, I have found, a common problem, easy to diagnose (not so easy to fix).

---

### Post by alexei_ on 2012-04-23
Yes, I have something like:
> 
DATE HOST kernel: [64350.171649] Critical temperature reached (96 C), shutting down.


Can I change action to "Suspend"?

---

### Post by QIII on 2012-04-23
Changing what happens when it overheats is pointless.

What you want to so is find out WHY it is overheating in the first place.

---

### Post by r-senior on 2012-04-23
96*C isn't just critical, it's verging on catastrophic. :o 

Is the processor fan spinning? Has the heat sink fallen off?

---

### Post by fara on 2012-04-23
if the cpu fan is working, and heat sink is in place, then the cpu might have not good contact with the heat sink, you can try cleaning the surface between them (both cpu and heat sink) and apply some thermal grease between the two

cheers

---

### Post by QIII on 2012-04-23
Any of the following, or a combination, are the most common:

Poor case ventilation:  dead case fans, dust bunnies.

Poor thermal performance of peripherals:  graphics cards can get very hot and, if not properly exhausted, fill the case with very hot air.

Run-away CPU conditions:  unwanted applications, kernel problems.

Poor HSF performance:  fan not operating, thermal compound can become dry and fail, a sudden jar or bump can break the HSF contact with the CPU.

---

### Post by audiomick on 2012-04-23
Open it up and have a look inside. The most likely thing is, at least if it is not brand new, that it is just full of dust and needs a clean out.
The next most likely is that a fan is broken or that the heat sink has no contact to the processor anymore.

---

### Post by QIII on 2012-04-23
I run all of my machines without filters because they become clogged so quickly.  Instead, I have a weekly ritual of taking them all out to the garage by the air compressor, setting the tool pressure very low, using a rubber tip nozzle and CAREFULLY dusting them out.

Even after a week, ther is plenty of dust.  But the filters get plugged and choked,too.  Damned if you do, damned if you don't.

Laptops breed dust bunnies like crazy.

---

### Post by collisionystm on 2012-04-23
> **QIII said:**
> I run all of my machines without filters because they become clogged so quickly.  Instead, I have a weekly ritual of taking them all out to the garage by the air compressor, setting the tool pressure very low, using a rubber tip nozzle and CAREFULLY dusting them out.

Even after a week, ther is plenty of dust.  But the filters get plugged and choked,too.  Damned if you do, damned if you don't.

Laptops breed dust bunnies like crazy.


I take old desktops out to the shop and hit them with 80 PSI full blast. They always look new when I am done lol

---

### Post by QIII on 2012-04-23
80 psi!  Dang, lad!

Don't you get memory modules and graphics cards flying around?  That's like a fire hose!

I wouldn't recommend *THAT* alexei_!  ;)

---

### Post by agillator on 2012-04-23
I had a desktop computer that, after a couple of years, starting overheating. The only thing that did any good was getting a small fan from WalMart ($4.98 or something), removing one side cover and having the fan blow on the cpu whenever the computer was on. That worked for a couple more years until finally even that didn't work. I haven't a clue why. But, it is a pain but a thought particularly if the option is a new computer that is not in the budget.

---

### Post by audiomick on 2012-04-23
> **agillator said:**
> I had a desktop computer that, after a couple of years, starting overheating. The only thing that did any good was getting a small fan from WalMart ($4.98 or something), removing one side cover and having the fan blow on the cpu whenever the computer was on. That worked for a couple more years until finally even that didn't work. I haven't a clue why. But, it is a pain but a thought particularly if the option is a new computer that is not in the budget.

I dare say the thermal paste between the CPU and the heat sink had dried out. I had to renew that myself on a laptop a couple of years back. It is not hard. The most difficult part is not putting too much on when you put it back together.

---

### Post by collisionystm on 2012-04-24
I never use thermal paste. I just smooth each surface. Metal to metal contact has always proven best for me.

---

### Post by QIII on 2012-04-24
The problem with lapping is that unless you have very precise equipment (machining equipment), you will not get a surface flat to the tolerances you need.  Doing it by hand will invariably lead to a convex surface.  Furthermore, there will always be microscopic voids on the surface of the heat sink that preclude a perfect metal to metal mating.  That means there will be air pockets.  Thermal compound is not really a very good conductor of heat, but it is in the range of 100 times better than air.

Besides, a glass smooth HSF base may not be really necessary.  The top of the CPU is not perfectly flat or smooth.  If you lap it flat, you run the risk of destroying it.

Lapping a cylinder head by hand on a piece of float glass on a dead flat surface works because the surface of the head is large, the head is short compared to its surface area and it doesn't tip.  The same is not true for a tall heat sink with a 1" square base.  

I think lapping is at best a waste of time and at worst dangerous.  A "metal to metal" HSF solution isn't metal to metal.  It's some metal to metal and some metal to air, meaning it's less, rather than more, efficient.

---

### Post by ekristia on 2012-12-21
This is quite an old thread, so I don't know whether anybody is still interested. 
Anyway, I also suffered from unexpected shutdowns.
Windows XP worked OK, as well as a very old Ubuntu I had on another disk.
I couldn't find anything relevant in the logs.
H/W indicators like temperature, voltages etc all seemed OK. Also measured power supply voltages, ran motherboard diagnostics (from Windows).
Trying to figure out when the shutdown first occurred, I was starting to suspect a software update gone wrong.
And, indeed, after poking around a lot, dpkg told me that the package "apparmor" and a few related packages were incompletely configured. Removing and re-installing those seems to have solved the problem.
Wasn't easy because the system kept shutting down a few minutes after booting. I eventually booted SuperGrub from CD, asked it to boot an Ubuntu system, and then worked from there to remove apparmor.

---

### Post by rnerwein on 2012-12-21
> **alexei_ said:**
> Ubuntu unexpectedly shuts down itself  -- why?
How to troubleshoot?
How to fix?
hi
before i red you message with the "critical ....". same hapened to some month ago a couple of times. my first idea was - oh same as my problem i had.
no message in /var/log just gone. looks like somebody execed the command "poweroff or halt". 
i ain't got the heat message - no warning - tschup and away.
my problem (fixed by self) was not the system.i was the problem. after cleaning the fan - every thing is ok - since month.
cheers

---

