---
title: "CPU fan loud and system shutting down?"
date: 2010-09-22
forum: General Help
---

### Post by hoje04 on 2010-09-22
I recently had an OS system crash..WIndows XP. Purchased a new hard drive and installed Ubuntu 10.04. Everything installed as expected, however my CPU fan seems to be louder than usual. I did clean the fan and heat sink, but still running very loudly or fast I guess you could say. Also sometimes the PC shuts down when I try to open FireFox. Any ideas on what could be happening. This is an older machine using an Intel Celeron processor. Not sure of the speed, but I could look at the bios if that is needed. Any help would be appreciated. Thanks.

---

### Post by no2498 on 2010-09-23
open a terminal type in htop
it tells you how to install it
now type htop
this should tell you what is running to make it hot

---

### Post by cascade9 on 2010-09-23
Did you remove the heatsink/fan when you cleaned it? 

If you did, its possible that you put to much, or to little, thermal grease on the heatsink. Its also possible that your thermal grease has gone 'bad' (dry) and if it has, it can act like a blanket.

---

### Post by DeMus on 2010-09-23
> **cascade9 said:**
> Did you remove the heatsink/fan when you cleaned it? 

If you did, its possible that you put to much, or to little, thermal grease on the heatsink. Its also possible that your thermal grease has gone 'bad' (dry) and if it has, it can act like a blanket.

You could have been right with your idea, however the heatproblems started before the poster cleaned the heatsink. In other words the original grease was between processor and heatsink.
Just open a terminal : Applications -> Accessories -> Terminal.
In there type top.
The processes which use the processor most are displayed there, the nr. 1 on top. See which it is and tell us here.

---

### Post by hoje04 on 2010-09-23
Thanks I will try that when I get home and let you know..I really appreciate all the help...

---

### Post by QIII on 2010-09-23
> **DeMus said:**
> In other words the original grease was between processor and heatsink.

True, but the point still stands:  the thermal compound dries out and  breaks down over time, making it ineffective.  The original compound may have been dry.  If, after removing the  heat sink, the old compound is not removed, too much compound is applied  or not enough is applied, heat transfer from the CPU to the sink would  be compromised.  Overheating could result under even moderate loads.

top and htop may not really be what he needs.  This sounds to me like  the machine is shutting off because of high temperature, which would be a  result of CPU usage when heat transfer is compromised.  In a properly  maintained machine, high CPU usage does not necessarily precipitate  overheating.

If it is possible to monitor CPU temperature via the OS, then that should be considered as part of the resolution.

I that is not possible, the machine should be restarted, the BIOS entered, and the temperature examined there.

In either case, one would then have to consult the documentation for the CPU and the motherboard to see if the value is within operational parameters.

---

### Post by no2498 on 2010-09-23
have had the same thing in/on 804 and 1004 2 computers
its a bug in fire fox
try using epiphany web browser and fire fox go back and forth 
it gets fixed in a few days

---

### Post by hoje04 on 2010-09-23
I did not pull the heat sink...so I think my next step is to try that. I simply blew the dust out...wasn't too bad though.  I did notice on the system monitor that my pulseaudio for some reason had a priority of -11 so I changed that to 0...don't know if that would be a problem or not. When I typed top firefox was at the top with 19.6%, htop returns two to three usr/lib/firefox-3 each of them at 19%. Does this help? Thanks again for all the help...you guys are great!

---

### Post by hoje04 on 2010-09-23
I did check the temp also...38 C and the fan rpm was at 4300....could my motherboard by "dying".....just a thought

---

### Post by QIII on 2010-09-23
> **no2498 said:**
> its a bug in fire fox

Not unless it is a bug specific to some piece of hardware, combination of hardware or interaction with another running application.  If it were a general bug, it would be happening nearly universally.

It is not happening to me.

---

### Post by cascade9 on 2010-09-23
> **QIII said:**
> True, but the point still stands:  the thermal compound dries out and  breaks down over time, making it ineffective.  The original compound may have been dry.  If, after removing the  heat sink, the old compound is not removed, too much compound is applied  or not enough is applied, heat transfer from the CPU to the sink would  be compromised.  Overheating could result under even moderate loads.

top and htop may not really be what he needs.  This sounds to me like  the machine is shutting off because of high temperature, which would be a  result of CPU usage when heat transfer is compromised.  In a properly  maintained machine, high CPU usage does not necessarily precipitate  overheating.


Bingo, exactly what I meant. :) 

I though it was a temprature shutdown, but it could be other things. 

I've had one machine that just started randomly shutting down, etc.. I cleaned it out, updated the BIOS, changed power supplies, ran it with minimal hardware installed (1 hdd, no CD/DVD, 1 stick of RAM, everything I could turn off in BIOS turned off) In the end, it was the RAM. Changed the RAM sticks and everything ran great.

*edit- a neat, 'dirty' trick for find out if it is overheating is to get a nice big desk fan, rip the side of the case, point the fan into the case from a few centimetres away, power it up then boot the computer. If it runs well with the fan blowng in, and crashes without the fan, its heat related.

---

### Post by hoje04 on 2010-09-23
Could it be the motherboard....I have already thought of the fan trick (we have had to do that at work) but havent tried it yet...I ran it for over an hour and it did not shut off...and then my wife tries it, after I shut it down for over 30 min and it did it again...don't know...I will pull the fan and heat sink and give you updates afterwards, in the meantime, please keep your suggestions coming...thanks.

---

### Post by hoje04 on 2010-09-24
I reread my opening post and thought it may lead to some confusion. I stated that the system was shutting down...that isn't really the case. I guess I should say the OS is shutting down. My screen says some things but the last one states that it is checking the battery state? So the machine doesn't do this until it is under some strain as far as task the one thing I keep changing and it seems to keep running is the NICE value of the pulseaudio. When I turn the machine on, it is set at -11 and I change it to 0. Machine doesn't seem to shut off then, however the fan speed still seems louder than it ever has and this just started with the new system, do not remember it being this way, before the original system (sorry...Windows) crashed. Just though I would clarify my first statement because I thought it could be a bit misleading. Thanks and have a great day.

---

