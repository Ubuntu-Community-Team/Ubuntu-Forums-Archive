---
title: "Has anyone noticed that? [high memory usage after updates]"
date: 2009-12-19
forum: General Help
---

### Post by Lukas666 on 2009-12-19
Normally just after start my system uses 400-500MB. Here is a pattern I've observed a few times:

1. New updates window pops up and I install them.
2. No immediate reboot as I have things in progress
3. Finally I reboot and I always check the mem stats freshly after booting.

Today after the updates the system used 1.7GB, a few times before it was 1.3, 1.4GB.

When I reboot one more time, everything is normal again.

Correlation with system updates is something I am positive about.

My system is 64bit Karmic with 8GB of RAM.

Has anyone else noticed that?

---

### Post by stu500 on 2009-12-19
i think i get the same thing with xubuntu. Installed some system updates last night, turn laptop on today and my ram usage had tripled, did several shut downs / restarts and its back to normal now?

---

### Post by Lukas666 on 2009-12-19
> **stu500 said:**
> i think i get the same thing with xubuntu. Installed some system updates last night, turn laptop on today and my ram usage had tripled, did several shut downs / restarts and its back to normal now?

I was running mine for a few hours in this "high mem" mode and I was witnessing many crazy things:

1. terminal window would not start. Just the "starting terminal" message and it was gone after several seconds

2. In the system monitor window, the refresh speed of network/cpu information was about twice the normal speed. Never seen it before. 

3. The columns in the "Processes" tab were completely messed up. I tried to resort them but every window activation (bring to front) reset my changes.

I just rebooted it again, mem usage is 450MB and everything seems to be normal.

Very, very strange.

---

### Post by ivaarsen on 2009-12-28
I'm seeing this also.

When I have the machine down for a couple days then start up, I show memory usage at about 90% or so, and the machine is very sluggish.  More sluggish than usual, that is - this machine has only 384 MB of memory, but it usually runs well for what I use it for.

I haven't used the terminal to check, but I can't see what's causing this very well - I have conky running and it doesn't show any processes that are using a substantial amount of memory.  After a reboot it returns to normal.

---

### Post by Lukas666 on 2010-01-10
I just installed the updates, rebooted (required) and mem usage is 1.6GB.

---

### Post by wolfie2x on 2010-02-23
Same here. System is taking around 50% more memory for the same set of applications. It's swapping to disk too making my laptop sluggish. I'll try rebooting several times; If that doesn't work I'll have to switch to the previous kernel I guess.. ;(

---

### Post by NightwishFan on 2010-02-23
High RAM usage generally does not mean much. If it "requires" all that RAM, then it is using it fine. I actually prefer my system swapping with 895 MB of RAM. Stuff in the swap is memory mapped, which means it is faster than loading something back from the disk. It comes at the price of some responsiveness when you switch to a program that is swapped, but overall performance is better.

Perhaps try checking top or the system monitor to see exactly what processes are using all the memory. It is also safe to kill any standard user owned non critical process, such as jockey-gtk (if you are not using it).

---

### Post by wolfie2x on 2010-02-23
Restarting the machine solved the problem. Looks like I had forgotten to reboot the machine after the update. Now its snappy as usual :)

---

