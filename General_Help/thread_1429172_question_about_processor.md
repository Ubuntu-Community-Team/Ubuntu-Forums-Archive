---
title: "question about processor"
date: 2010-03-13
forum: General Help
---

### Post by tubunu on 2010-03-13
Hello,
I would like to ask about my processor. System Monitor shows two of them and I wonder what it means? (please see the attached screenshot for details)

Processor 0 and 
Processor 1

Does it mean I have not one but two processors? Does Ubuntu make use of both of them and does it mean my performance should be better than on a PC with one processor? Thank you for any insight.

---

### Post by Pjotr123 on 2010-03-13
Apparently your processor has more than one core. In that case, this is normal.

---

### Post by srs5694 on 2010-03-13
Most mid-range and better computers sold in the last couple of years are dual-core (or better), meaning they have circuitry for two (or more) CPUs on one physical device. Yes, Ubuntu should take advantage of both cores, although the details depend on the program(s) you run. If you run just one CPU-intensive program (a game, raytracing tool, scientific simulation, etc.) and that program is written in what's called a "single-threaded" manner, then one of your cores will go almost completely unused. If you run two CPU-intensive programs, or one program that's written in a "multi-threaded" manner, then both your cores will be used. Note that most Linux programs don't use the CPU except when they need to. You can have a spreadsheet, Web browser, e-mail client, and shell program all open at once and the CPU load can still be near 0 if none of those programs is actually doing anything at the moment. The amount of CPU time required to read an e-mail, load a Web page, etc., is quite small. (Flash animations and some other features can chew up CPU time, though.)

There are utilities that will show your CPU use, including evidence of use of multiple CPUs or CPU cores. For instance, in Xfce (the desktop environment I use), I've got a widget called CPU Graph that sits in one of my panels. It shows a brief history of CPU use in graph form along with two instantaneous bars, one for each CPU. I can tell at a glance if something's hogging both my CPUs cores, just one core, or whatnot. I'm pretty sure that similar widgets are available in KDE and GNOME, but I don't know offhand what they're called.

---

### Post by tubunu on 2010-03-14
Thank you both for your replies. :)
I have a DAW program that I run in Wine and it experiences some underruns. I was wondering if I could change the priority so that most of the CPU power goes to that program. I think I found this option under System Monitor/Processes, by right clicking that program and adjusting the slider under "change priority". Not too sure if that actually makes any difference.

---

### Post by srs5694 on 2010-03-14
Yes, you can change a program's priority. It sounds like you've found a GUI tool for the job. The text-mode tool is called renice. Type "man renice" at a shell prompt to learn more about it. You can also launch a program from a shell with altered priority by using "nice," as in "nice cruncher" to run the fictitious cruncher program at reduced priority. Note that the priority codes can be confusing -- negative priority values refer to *increased* priority, while positive values refer to *reduced* priority. Ordinary users can only reduce the priority of their own processes; they can't increase the priority of any processes or adjust the priority of other users' processes.

There are also kernel options that can adjust how snappy your system feels when it's under load, but adjusting those is pretty advanced. Some of them require you to recompile your kernel. I don't recall offhand how the default Ubuntu kernel is configured in this respect, but I'd imagine it's configured with good options for most desktop users.

---

### Post by Slim Odds on 2010-03-14
> **tubunu said:**
> Thank you both for your replies. :)
I have a DAW program that I run in Wine and it experiences some underruns. I was wondering if I could change the priority so that most of the CPU power goes to that program. I think I found this option under System Monitor/Processes, by right clicking that program and adjusting the slider under "change priority". Not too sure if that actually makes any difference.

Running a non-native DAW program is likely to be problematic. Even native DAW programs typically want a real-time linux kernel (which is not part of the default Ubuntu install). Running with a non-real-time kernel and WINE is likely to have issues. 

You might want to find a linux application that is equivalent to the one you are currently using. Also, look into releases like Ubuntu Studio.

---

### Post by tubunu on 2010-03-16
Thanks!

---

