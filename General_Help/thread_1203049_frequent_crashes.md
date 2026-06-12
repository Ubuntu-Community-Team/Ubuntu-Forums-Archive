---
title: "frequent crashes"
date: 2009-07-02
forum: General Help
---

### Post by arch_angle07 on 2009-07-02
After dual booting, but mainly using windows 99% of the time for quite awhile, I finally decided to switch completely to ubuntu after my windows partition essentially committed suicide.

I am running 9.04 64bit, and it frequently crashes, it shows the ubuntu shutting down screen then restarts.

I get the crashes every time I try to render an animation in blender, but also while playing games, and one time while web browsing.

I love ubuntu outside of this issue but I have no idea whats causing it, My computer has more than enough in it to handle the games and rendering, and I know it's not a heating issue, anybody have any ideas?

---

### Post by ~sHyLoCk~ on 2009-07-02
I think there's something seriously wrong with your hard disk. Do a full format and check for bad blocks.

---

### Post by arch_angle07 on 2009-07-02
To clarify, it was my own fault that I had to remove windows, not the computers

I've never had any problems with the harddrive before and so far theres no reason to suspect it, let alone reformat

---

### Post by internalkernel on 2009-07-02
Check your logs... perhaps there's something in there - 

>Administration->Log File Viewer

and look specifically in syslog, dmesg and kern.log 

Each line in there is time stamped so the next time you have a freeze, and have to reboot - try to pay attention to the time and see if you can locate some error or something in the logs to narrow this down.

I have a couple systems that have had issues with Ubuntu, both stem from proprietary video drivers... ATI and Nvidia... although, Nvidia seems to be the lesser of the two evils.

---

### Post by arch_angle07 on 2009-07-02
well I made it crash by rendering an animation and checked my syslog and got this

Jul  2 22:20:01 marcus-desktop /USR/SBIN/CRON[5418]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  2 22:24:07 marcus-desktop kernel: [ 3615.449259] ACPI: Critical trip point
Jul  2 22:24:07 marcus-desktop kernel: [ 3615.449268] Critical temperature reached (71 C), shutting down.


however typing acpi -V into terminal shows my temps at 43 degrees and my bios shows the same. Now I'm completely clueless.

---

### Post by internalkernel on 2009-07-02
Well, at least it's a start... I would start by turning off the acpi temperature events, not sure exactly where to do this though. I've never come across an issue such as this. That would at least keep your system from crashing or halting. 

There may also be another way to raise the critical temp trip point, obviously this is a less than ideal solution. 

Check into the support of your motherboard as well, perhaps there is a Bios update that it could use... maybe it's not communicating with the kernel properly.

---

### Post by arch_angle07 on 2009-07-02
Well I changed the max temp in my bios from 70 to 80 degrees, then when it booted up I check my temps, then opened multiple rendering animations, the temps instantly jumped from 40 to 65 degrees as soon as the rendering started, then slowly crept to 75 and stayed there, no crash.

however this temperature can't be correct just by feeling the case where the cpu is, but it does look to be at least a temporary solution. I really don't want to completely shut off the temperature shutdown just in case it does overheat.

---

### Post by scrooge_74 on 2009-07-02
Check your fans, the specially the one a top the processor, could be dirty or could by dieyng. Or the heat sink could be loose.

Try taking the cover off and put a fan pointing to the inside

---

### Post by Hobgoblin on 2009-07-02
> **arch_angle07 said:**
> 

however this temperature can't be correct just by feeling the case where the cpu is,

The temp will be that of the actual CPU, which is nowhere near the side of the case.

I suggest opening up the case and clearing out the heat sinks which you will find within.  Using a can of compressed air.

---

### Post by scrooge_74 on 2009-07-02
I don't recommend feeling the CPU either, it will give a pretty bad burn at those temps

---

### Post by arch_angle07 on 2009-07-02
I built the computer, and made sure to buy a good heatsink, It's got 7 fans and I can see inside the case, theres no dust and the fans are all fine. It's got a 1000 watt psu so it has more than enough power to run them all.

The problem isn't it over heating, theres no way that the temps could go up 35 degrees in 10 seconds, then drop back down instantly.

I'm checking for updated mobo drivers, however I specifically chose this one because it was said to work great with linux.

"I don't recommend feeling the CPU either, it will give a pretty bad burn at those temps"

exactly if it were really at just 25 degrees shy of boiling temp, you would be able to feel it through the side of the case that the cpu's on. instead it is completely cool

---

### Post by scrooge_74 on 2009-07-02
Proly problem is with lm-sensors or some other acpi package

---

### Post by RJARRRPCGP on 2009-07-02
75 C is not normal unless your running mprime. ;)

---

### Post by Coder68 on 2009-07-02
Make sure the heatsink is properly seated.  Never use to much heatsink compound when putting a fan down for the first time.  That can cuase a CPU heat issues! Make sure the fan and heatsink are totaly clean. IIt could also be a BIOS issue, so  update your BIOS to the latest. 

If none of this helps:

You could have a bad temp  sensor that is saying the CPU is overheating and shuts down for protection.
Get a laser tempature Thermomitor and see what the heatsink is really at.

As for your temp settings in the BIOS, set your max temp before shutdown to just below the hightest temp that is safe for your CPU. You can get this data of of Intel or AMD's website.  Going to high could (will) damage your CPU. Remember that if your PC shuts down, the CPU will actually get hotter for a minute or two!!  (No Fan) so make sure the safe temp is low enough to not get to close, but not to low.  

If you never had this issue under Windows... did you ever push Windows like you are Linux? 3D tools each CPU cycles for lunch. ;)

For a temp fix, open your case and blow a house fan into the case on high.  That should help.

Good luck,

C68

---

### Post by arch_angle07 on 2009-07-02
> **Coder68 said:**
> Make sure the heatsink is properly seated.  Never use to much heatsink compound when putting a fan down for the first time.  That can cuase a CPU heat issues! Make sure the fan and heatsink are totaly clean. IIt could also be a BIOS issue, so  update your BIOS to the latest. 

...set your max temp before shutdown to just below the hightest temp that is safe for your CPU...

If you never had this issue under Windows... did you ever push Windows like you are Linux? 3D tools each CPU cycles for lunch. ;)

For a temp fix, open your case and blow a house fan into the case on high.  That should help.

Good luck,

C68


Once again, this is NOT a heating issue, yes I have run mprime and it windows equivilent back when I used it (both lasted over 24 hours), if it was a bios issue it would affect windows as well.

If you read I have already raised the max temp and it stopped the crashes, however I don't like the fact that my computer can get that hot without shutting down.

For some reason when there is a heavy load on the cpu the temp spikes instantly up, then goes instantly back down, since the temperature couldn't go so high so fast, then return to normal so fast, that spike can't be the actual temperature, I'm trying to find out why it is reporting a spike in temperatures when it obviously isn't happening. (if it had heating probs it wouldn't be able to do mprime and the bios wouldn't report normal temps.)

---

