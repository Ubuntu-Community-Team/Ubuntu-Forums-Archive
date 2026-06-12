---
title: "CPU usage in system monitor."
date: 2011-01-06
forum: General Help
---

### Post by jaronron10 on 2011-01-06
Hey. 

     I am having a slight issue with my netbook (toshiba nb305) Just fully switched to Ubuntu 10.10 from Windows 7 starter so still a little new.

     I first installed the 32 bit version and everything was all sorts of peachy. But while reading some documentation on my model I ran across a cryptic line that hinted at my cpu being 64 bit. Did a little research on these forums and ran a command in terminal (honestly cant remember it) that listed the specs on my hardware. Sure enough my "width" was listed as 64 bit. 

     Well just to give it a shot i Downloaded the 64 bit version of 10.10 and Installed it on another partition. Up and running checked over everything. Appears to be normal. But on a whim i went into the System Monitor and noticed not one cpu but 2?? Confirmed same situation on 32 bit. 

Processor 0: Intel(R) Atom(TM) CPU N455 @ 1.66 GHz
Processor 1: Intel(R) Atom(TM) CPU N455 @ 1.66 GHz

     Ok i was a tad bit confused so i was about to do a lil research on it. But then I noticed on the Resources tab that under 64 bit my CPU History graph showed both processors Pegged at 100% With nothing running except for the basics. Under the 32 bit it was reliantly low.?.? Odd 

     I checked the Processes tab in both to confirm there wasnt a unusual process out there jamming up cpu usage but the highest cup listed was the gnome-system-monitor at like 40 est %. Nothing showing up using the CPU that vigorously. 

So I ask...

What gives. :)

Thank you all for your help with this in advance.

Aaron

---

### Post by jaronron10 on 2011-01-07
Any ideas?

---

### Post by Old_Grey_Wolf on 2011-01-07
I have a Toshiba NB305 with the N455 Atom processor. The N455 processor is a single core processor; however, it is dual threaded. I noticed that the 32-bit Ubuntu recognized it as a dual core processor. It seems to interpret each thread as a core. I don't use the 64-bit version because the mini-notebook I have only supports 2GB of RAM. I think the N455 processor only supports some types of RAM above 2GB, DDR3 if I remember correctly.  It could be that the 64-bit version is even more confused about multi-threaded processors than the 32-bit version.

My Toshiba mini-notebook is working fine so I don't worry about what Ubuntu thinks the hardware specs are. :)

---

### Post by Krytarik on 2011-01-07
Old_Grey_Wolf may be right. If there aren't any individual processes which consume unreasonably much CPU power and the task/programs you start are working as fast as expected, I wouldn't care about the then obviously false 100%-usage-statement.

EDIT: To display the CPU-usage without getting disturbed by the high CPU-usage of the monitor itself, enter "top" in a terminal.

---

### Post by jaronron10 on 2011-01-07
That makes perfect sense... i think... ... lol.  I wasnt too worried about it, I just like to poke around.

In hindsight my fascination with "POKING" around is the cause of most of my problems in my life... Eh some people will never learn. 

Thanks for your input. I will most likely stick with 32bit Ubuntu because it is already set up the way i like it...

And Major kudos for the "Top" command. I did not know that.

---

### Post by Krytarik on 2011-01-07
> **jaronron10 said:**
> In hindsight my fascination with "POKING" around is the cause of most of my problems in my life... Eh some people will never learn.
:lolflag:
> **jaronron10 said:**
> And Major kudos for the "Top" command. I did not know that.
I just learned it either in the last days, running Linux systems since some 10 years.:P

---

### Post by Old_Grey_Wolf on 2011-01-07
jaronron10 is using the 64-bit version of Ubuntu. I described my experience with the 32-bit version and the way it treats a dual-threaded single core processor. I was speculating that the 64-bit version may have problems with multi-threaded processors. jaronron10 may actually have a problem. However, it should be evident if the computer runs hot or has other strange behavior.

---

### Post by Krytarik on 2011-01-07
@Old_Grey_Wolf: Considered that. As I said:
> If there aren't any individual processes which consume unreasonably much CPU power and the task/programs you start are working as fast as expected ...

---

### Post by efflandt on 2011-01-07
One thing that can be a mystery is whether cpu% is % of what.  For example 100% of idle speed may not be a big of an issue as 100% of max cpu speed.  You can find out current cpu speeds with:

**grep MHz /proc/cpuinfo**

Do that repeatedly while running **top** in another terminal, pressing **1** after starting top to see % of each virtual cpu.

---

### Post by sdennie on 2011-01-08
That CPU has hyperthreading and, in userland, it's presented as 2 "CPUs".  Under the covers, the kernel does know that it's not 2 physical CPUs and will act accordingly.  You should be able to run 64-bit Ubuntu on that machine without any problems.  I have a dual core atom server that runs 64-bit Ubuntu and it runs great.  The high CPU usage you are seeing is, unfortunately, being caused by the actual monitoring of the CPU usage.  You can use top as suggested above or, if you want a lightweight constant monitor of CPU usage, you can right click on the panel at the top and add a CPU monitor to it.

---

