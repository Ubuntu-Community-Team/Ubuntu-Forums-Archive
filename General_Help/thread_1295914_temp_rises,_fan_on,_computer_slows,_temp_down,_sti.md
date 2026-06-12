---
title: "temp rises, fan on, computer slows, temp down, still slow"
date: 2009-10-20
forum: General Help
---

### Post by aaronre on 2009-10-20
EDIT:
-----------------------------------------------------------------------------------------------
this problem is actually related to my dell laptop's hardware.  You should only read on if you have a dell laptop having the following problem: (usually) a few minutes after booting, the fan comes on full speed and the computer slows down tremendously, and stays that way until you shut down your computer.

The problem is an aging thermistor (temperature sensor) on the motherboard, and the problem is described well at:

[http://cdiefer.proboards.com/index.cgi?board=i8kfan&action=display&thread=484](http://cdiefer.proboards.com/index.cgi?board=i8kfan&action=display&thread=484)

If you are having this problem, hit fn+z ("function key" and "z" at the same time) and it should be (temporarily) fixed, until it heats up again (maybe 10 seconds, maybe a long time).

Thanks to P4man for helping me figure it out.
-----------------------------------------------------------------------------------------------

ORIGINAL POST:

Hello,

I am running Kubuntu (dell inspiron 8200, 1.6 GHz Pentium 4 Mobile, 512 MB RAM), and having a strange problem.

After booting and running for various amounts of time, the computer starts running excruciatingly slowly and the laptop's fan kicks up to full speed.  Once this happens, the fan remains on high and the computer runs reeeeaaaally slowly until after the computer is shut down.  Because the fan is on, the cpu temp drops to about 45 C (as reported by acpi), but as i said, the fan stays on high, and the computer runs very slowly.

 I have experimented a lot to try to find out when this happens.  It seems to be related to using processor-intensive applications. If I don't open any programs, and the temp stays low, and the problem seems to never arise.  But if I watch videos in dragon player or flash videos in firefox (or konqueror) or run various other programs, and the temp gets up to about 70 C, the problem starts.  The fan comes on high, and things start running very slowly, but this isn't fixed when load is decreased: even if i close all programs, and the cpu temp goes down, the fan stays high and everything keeps runnign extrememly slowly.

I have used "top" to monitor processes.  After the fan comes on, each process running seems to be using about 4 times as much processor time as usual.  For example, Xorg uses about 3%-5% cpu normally, but it risees to about 12%-20% constant usage after the fan pickup.  There is a similar pattern for firefox as well as for a process called hal-system-smbi.  

I have not seen any strange programs in top using a lot of processor.  It just looks like the normal processes use 4x more cpu.

I have been running this setup (Kubuntu J) for a long time (almost a year?), and this problem suddenly started a couple of days ago.

sorry if this got a little long, i just wanted to be very clear.

Any help is appreciated, thanks a lot people.

---

### Post by P4man on 2009-10-20
Is that a pentium 4 based machine ? IT sounds a lot like thermal throtteling is kicking in, but well, not kicking out so to speak.

I would check your fans and airducts for clogged dust (if you have an air compressor blow them clean). Though that still doesnt explain why it doesnt stop doing it after temps have dropped. Perhaps reset and/or update your bios?

---

### Post by aaronre on 2009-10-20
> **P4man said:**
> Is that a pentium 4 based machine ? IT sounds a lot like thermal throtteling is kicking in, but well, not kicking out so to speak.

It is a pentium 4 mobile (i just edited my post to reflect that).

It's not just throtteling, though; some other strange thing is going on too, because the machine runs very slowly, even when the load is reduced, and processes use up much more cpu % after this switch happens.

> **P4man said:**
> I would check your fans and airducts for clogged dust (if you have an air compressor blow them clean). Though that still doesnt explain why it doesnt stop doing it after temps have dropped. Perhaps reset and/or update your bios?

the ducts seem fine, and all of the air that's being blown out isn't even hot.  Running
```
acpi -t
```
shows that the temperature in fact goes down to about 45 C, so the fan is effective.

> **P4man said:**
> Perhaps reset and/or update your bios?
maybe i'll attempt to figure that out and try to do it--could you elaborate on how the BIOS could be a problem, and what kind of symptoms it would have?

Thanks a lot

---

### Post by P4man on 2009-10-20
> **aaronre said:**
> It is a pentium 4 mobile (i just edited my post to reflect that).

It's not just throtteling, though; some other strange thing is going on too, because the machine runs very slowly, even when the load is reduced, and processes use up much more cpu % after this switch happens.

With P4s thermal throttelling, its not the clock speed that is reduced, instead the cpu issues nop ("empty") instructions in the pipeline. Depending on the heat, it will not be executing anything useful anywhere between 15 and 75% of the time. I have no idea how this relates to system monitor though, but I can imagine it increases the perceived load as its working harder,.. doing nothing. But obviously your performance will plummet.

Anyway, normally this behaviour should stop once the cpu temp has dropped below a certain threshold, and that doesnt seem to happen on your machine (assuming it is indeed thermal throtteling to begin with). This throtteling is governed by the cpu and the motherboard bios, hence my suggestion of resetting the bios (perhaps it got corrupted?) or flashing a new one. You could also check the bios options if there is anything to turn this on or off or change the behavior, but Dells typically have extremely simplistic BIOS screens, so I am not too hopeful.

Anyway, Im not saying at all Im sure Im on the right track here, but its pretty much all I can think off. Although i guess it would not hurt to have a look in dmesg output if anything is being picked up there.

---

### Post by aaronre on 2009-10-20
> **P4man said:**
> With P4s thermal throttelling, its not the clock speed that is reduced, instead the cpu issues nop ("empty") instructions in the pipeline. Depending on the heat, it will not be executing anything useful anywhere between 15 and 75% of the time. I have no idea how this relates to system monitor though, but I can imagine it increases the perceived load as its working harder,.. doing nothing. But obviously your performance will plummet.

Anyway, normally this behaviour should stop once the cpu temp has dropped below a certain threshold, and that doesnt seem to happen on your machine (assuming it is indeed thermal throtteling to begin with). This throtteling is governed by the cpu and the motherboard bios, hence my suggestion of resetting the bios (perhaps it got corrupted?) or flashing a new one. 


I think you're on to something here, but I have a question.  It seems that fan speed can be affected by system files and processes within ubuntu, so how does the BIOS also have control over the fan?  Since the fan can be controlled from within ubuntu (i think), maybe i can set a lower temp to start the fan, and then the cpu will never reach the critical temperature.

I think you may be right, though, about what the problem is; I didn't make any changes that should have affected the system, so corrupted files would make sense as the cause of the problem.  I'll try to reset my BIOS somehow (not sure how, but i'll give it a try) when i get home today.  It would be great to have a normally-functioning computer again.

---

### Post by P4man on 2009-10-21
Solving the throtteling issue isnt the real solution anyway; the real solutions is fixing the cooling. Try cleaning the fans and airducts and cooler if you can.

As for how to reset the bios, check the manual. On some machines its trivial, on others its all but impossible to do without taking it apart entirely. Flashing the bios should also reset it though.

As for fan speed. On many machines the OS can take control, but using BIOS interfaces. The bios would be in charge primarily but may or may not expose an interface for the OS to take control. Have a look here

[http://ubuntu-linux-for-human-beings.blogspot.com/2009/02/how-to-control-fan-speed-lm-sensors-in.html](http://ubuntu-linux-for-human-beings.blogspot.com/2009/02/how-to-control-fan-speed-lm-sensors-in.html)

---

### Post by aaronre on 2009-10-22
P4man,

Originally, i thought that this was an ubuntu problem, but your suggestions got me thinking that it was a hardware problem.  I started searching a lot more specifically related to my laptop model, etc, and found out what the problem is! :

[http://cdiefer.proboards.com/index.cgi?board=i8kfan&action=display&thread=484](http://cdiefer.proboards.com/index.cgi?board=i8kfan&action=display&thread=484)

basically, the thermistor on the motherboard has gone south, and is now reports high temp too early.  This means that the "throtteling" kicks in (along with the fan at full speed), but the board is actually *designed* to not go back to normal when things cool off; it needs to be shut down (bad design in my opinion).

Anyway, thank you very much for getting me on the right track, you saved my computer's life.

Now i just have to figure out how to control the fan (if i can) to get it to turn on earlier, but that is definitely a topic for another thread (which probably already exists).  I am also going to clean out my ductage and heat sinks, and replace the thermal paste, so hopefully i'll be as good as new--might even upgrade with a bit more RAM!

Again, thanks a ton, all the best to you.

---

### Post by P4man on 2009-10-22
Ah, interesting.
Does Fn +z work in ubuntu as well?

As for controlling fan speed, check the link I posted above.

I would also check your dmesg output, see if the kernel picks up this thermal event. If it does, perhaps its possible you could override it in linux, but your idea to clean out fans and reapply thermal paste is probably the best thing to try first. Might well solve it.

good luck!

---

