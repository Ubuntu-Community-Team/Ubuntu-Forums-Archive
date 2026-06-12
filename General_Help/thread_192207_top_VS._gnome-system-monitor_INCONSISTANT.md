---
title: "top VS. gnome-system-monitor INCONSISTANT?"
date: 2006-06-08
forum: General Help
---

### Post by barakaspeed on 2006-06-08
Ok, every since I installed 6.06, I have been noticing high cpu usage for xorg.  I searched threads on this topic to see others having the same issue.  One thing I am pretty sure about is that everyone was measuring their cpu usage with gnome-system-montior.   I am getting 40% + usage during standby with xorg!!!  

I decided to close that down and check what top was reporting.  I was seeing a EXTREME different usage amount!!!  So I thought to myself that gnome-system-monitor must be creating this flux.  So the next logical step is to run them side by side.   Amazingly tops shows very little cpu usage for xorg and gnome-system-monitor, but in contrast gnome-system-monitor is showing the higher results.

So my question is which one is accurate?  Is this a flaw in gnome-system-monitor that is making people believe that ubuntu 6.06 is more of a memory hog, when in reality it is just as efficient as earlier releases?


Attached is a screenshot showing both...

---

### Post by jongkind on 2006-06-08
It's not only the cpu usage which is inconsistant: the same is true for memory usage. I don't have an explanation.

---

### Post by pyromithrandir on 2006-06-08
No, the memory usage is consistant. Notic that top lists it in percent while gnome-system-monitor lists it in MB. Since top also shows that he has 512MB of total RAM, I did a little check of multiplying 512 by .064 (the percent of memory top shows Xorg to be using) and I got 32 MB (the number that gnome-system-monitor gives).

The memory is fine, but the CPU... that's weird.
I think the problem may be with top, actually. If you look at the "Cpu(s):" line, it tells how much of the CPU is being used (22%) and that doesn't match up with the  %CPU column when you add it up (2%).

Oh, and nice background, btw. ;)

---

### Post by jongkind on 2006-06-08
Memory usage:

Top: 
Mem:    513984k total,   498704k used,    15280k free, 

System Monitor:
User Memory 176 MiB of 501.9 Mib

I would n't call this consistant.

---

### Post by barakaspeed on 2006-06-08
What are you guys getting for Xorg usuage on your systems?  Does it hover around 20-35% idle?  (this is what I see in gnome-system-monitor)

I am using the 686 kernel on my system.  (It's what was installed by default)



jongkind:   I was more concerned about the cpu usage percentages.

---

### Post by jongkind on 2006-06-08
Xorg: 0-2%CPU while I'm typing this.

---

### Post by pyromithrandir on 2006-06-08
"System Monitor:
User Memory 176 MiB of 501.9 Mib"
Where are you getting these numbers? I don't see them in the screenshot or in barak's post.

barakaspeed: Have you made sure you are using the latest versions of these packages? You might even want to try removing them and then reinstalling them to see if that fixes it.
Oh, and my xorg uses under 1% of my CPU.

---

### Post by barakaspeed on 2006-06-08
I haven't checked if they are the latest, but I just assumed they were pretty new considering this was a fresh install of 6.06 just 2 days ago.

---

### Post by jongkind on 2006-06-09
[QUOTE=pyromithrandir]"System Monitor:
User Memory 176 MiB of 501.9 Mib"
Where are you getting these numbers? I don't see them in the screenshot or in barak's post.
[/QUOTE]


Oh, sorry, I was refering to my system and to the discrepancy in memory usage that I observe between top and system monitor.

---

### Post by pyromithrandir on 2006-06-09
> Oh, sorry, I was refering to my system and to the discrepancy in memory usage that I observe between top and system monitor.
Oh, okay. Well, there is a simple explanation for this behavior: top counts cached memory as used while gnome-system monitor doesn't.

---

### Post by mcduck on 2006-06-09
In the screenshot System Monitor reports 32.2MB for Xorg and 14.3 for itself, and top reports 32MB for Xorg and 14MB for gnome-system-monitor. (note that you need to look under 'res' tab in top to see the amount of RAM the process is actually using (not including shared memory). So both apps report the same memory usage..
Also, in top, the Mem used line tells how much memory is used *including cache*, so it's always pretty close to the amount of RAM installed on your machine. To get a better view of you memory usage, run 'free -m' and look at the line with '+/- buffers&cache'..

Anyway, the difference in CPU usage is indeed strange.. :-k

---

### Post by jongkind on 2006-06-09
That explains a lot, thanx.

---

### Post by barakaspeed on 2006-06-09
But what about cpu usage?  That is my main concern now.  I can't figure out why they are reporting separate values.  I have been doing some troubleshooting more with this and booted into a Live CD of 5.10 and performed the same test.  

Here are the screenshots of it as well as a screenshot showing my pkg versions in 6.06.

Could it be a bug in gnome-system-monitor or the fact that I'm using 686 kernel instead of 386 in the 5.10 version?



EDIT:

I came across some new websites in my search.  Apparently there is a bug report stating high cpu usage in 686 kernels.  JongKind, you said your xorg usage was very low.  Which version of the kernel are you running?  686 or 386?

Links to what I just found out:
[http://www.oreillynet.com/onlamp/blog/2006/03/high_cpu_utilization_in_dapper.html?CMP=OTC-6YE827253101&ATT=High+CPU+Utilization+in+Dapper/](http://www.oreillynet.com/onlamp/blog/2006/03/high_cpu_utilization_in_dapper.html?CMP=OTC-6YE827253101&ATT=High+CPU+Utilization+in+Dapper/)
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570)

---

### Post by jongkind on 2006-06-09
Barakspeed, I'm using the 686-smp kernel for dual core processors. I don't experience a lot of speed differences (if any at all) by using either this one or the 383 kernel. I suggest that you try the 383 kernel also to see how it performs and how it affects your CPU usage.

---

### Post by barakaspeed on 2006-06-09
Thank you for checking.  I'm in the process of trying to figure out how to actually add the 386 kernel to see.  Is it complicated? I'm trying to find a HOWTO for it now...  

I'll post later with the results after I succeeded

---

### Post by jongkind on 2006-06-09
[QUOTE=barakaspeed]Thank you for checking.  I'm in the process of trying to figure out how to actually add the 386 kernel to see.  Is it complicated? I'm trying to find a HOWTO for it now...  

I'll post later with the results after I succeeded[/QUOTE]

This is easy with Synaptic. I assume that you've an Intel Pentium processor (right?). 

I installed the following packages for the 383 Kernel:

Linux kernel image for version 2.6.15 on 386.
Linux kernel image on 386.
Non-free Linux 2.6.15 modules on 386
Restricted Linux modules on 386.

---

### Post by mcduck on 2006-06-09
[QUOTE=barakaspeed]Thank you for checking.  I'm in the process of trying to figure out how to actually add the 386 kernel to see.  Is it complicated? I'm trying to find a HOWTO for it now...  

I'll post later with the results after I succeeded[/QUOTE]
run 'sudo apt-get install linux-386', or install the 'linux-386' package with synaptic. It will get you latest versions of all needed packages. (and also updates for those packages, when available)

It might be true that the strange CPU usage is problem with 686 kernel. I'm running K7 and I've never had any problems. Xorg runs between 0 and 0,7%..

---

### Post by dipswitch on 2006-06-09
umm... I don't know about the system monitor or cpu usage BUT...

can you post a link to that background from the first screen?

---

### Post by barakaspeed on 2006-06-09
VOILA!!!  

I just switched to the 386 kernel and I am happily running an average system cpu usage under 5%!!!    Apparently there is some bug at work here.  I wonder what I might be losing by switching back to a 386 kernel.  Oh well, I'm much happier now with the lighter load on the cpu.



For the sake of future people running across this problem, here are my relevant system specs:

Dell Inspiron 9300  (Centrino) Pentium M 1.6 Ghz

Thank you guys for helping me along here.  Much appreciated!  



Oh.. and for the request for that wallpaper, here it is!

---

### Post by dipswitch on 2006-06-09
Thank you sir!

---

