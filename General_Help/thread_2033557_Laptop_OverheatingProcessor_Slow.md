---
title: "Laptop Overheating/Processor Slow"
date: 2012-07-26
forum: General Help
---

### Post by Dylan1473 on 2012-07-26
I'm not certain whether this is an issue with Ubuntu or with my computer, but I'm hoping someone can help me with it.

I have a few separate but, I suspect, related problems.

The most important two: my computer seems to be heating up faster than normal and the processor is running at one third speed. 

Regarding the processor: I initially thought the processor slowed down  because the computer was just running too hot, and I still think they're  related. However, even when my laptop is running at pretty normal  temperatures (50 or 60 odd degrees celsius, and I am checking it  constantly) the processor slows down from 2400 to 800 megahertz (as  indicated by lscpu).

Regarding the temperature: it overheated a LOT last night - it was  running at 70 odd degrees for fairly light activity (web browsing and  such) and 80 odd degrees at times. I thought it may have gone over 90 at  some point (I initially thought so because the processor slowed down)  but now I'm not sure since the processor seems happy to slow down at 50.  I'm checking constantly and getting paranoid every time it goes over 60  (should it be doing that for typical web browsing? I'm not sure).  Sitting at 57 degrees celsius as of this post. I have a usb cooling pad  underneath it right now though. However, this morning before I started  using that it was still in the 50s and 60s.

I'm also encountering some general performance issues (things are moving  a bit slower, umplayer apparently won't play any videos, system monitor  won't close or takes so long to close I'm inclined to just end the  process) most of which can probably be attributed to the dramatically  slowed processor speed.

Some relevant info about my system:

I'm running an Acer Aspire 5252-V662 laptop. My processor is an AMD V160  with one core and (usually) 2.4ghz of speed. I've had the laptop for a  year and I'm not certain how many months, but I think less than a year  and a half. It's been extremely heavily used in that time, though.

I'm running Ubuntu 12.04 built up from a minimal install and primarily  using the Enlightenment window manager/desktop environment. However,  using XFCE doesn't seem to affect this issue. I got Ubuntu 12.04 a few  days after it was officially released and this problem only started  (that I noticed) yesterday.

The output of lscpu is
```

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 6
Stepping:              3
CPU MHz:               800.000
BogoMIPS:              4787.57
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
NUMA node0 CPU(s):     0

```and acpi -V is 
```
Battery 0: Full, 100%
Battery 0: design capacity 4400 mAh, last full capacity 2936 mAh = 66%
Adapter 0: on-line
Thermal 0: ok, 57.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 200.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 90.0 degrees C
Cooling 0: LCD 0 of 9
Cooling 1: Processor 0 of 10

```if that's at all helpful.

Hope this is the right place to put this. Any assistance would be appreciated.

---

### Post by 2F4U on 2012-07-26
What graphics card is in the machine and what graphics driver are you using?
With respect to CPU frequency, this may be normal since modern Linux distributions do scale down CPU frequency when it is not needed. If it is, however, always low and doesn't scale up it may indeed be due to a heating issue.
Did you check that the fans are not blocked by something? Maybe there is dust inside the case that makes air flow less efficient. Are the fans working normally?

---

### Post by Dylan1473 on 2012-07-26
The graphics card is an ATI Mobility Radeon HD 4250. I've had problems with it in Linux before but mostly pertaining to glitches in games or low graphics quality, which isn't really surprising since it's a low end card and I'm told radeon cards are very poorly supported in linux.

I wondered if maybe the processor slow down was normal at first, but it still appeared to be running at 800 even when things begin to slow down. I'd been reluctant up to this point due to last night's overheating, but having just now tested it by starting up a virtual Windows machine it did indeed increase to normal speed for a moment as the virtual machine was booting up. I guess I panicked about that due to the earlier issues and since this was the first time I'd actually checked the speed, thanks. Wonder how much of that was just my imagination? Umplayer still doesn't work, but "not playing videos only in that one program" would be kind of a weird symptom of processor issues.

The fans are certainly pushing out air at least. I don't know how to tell if they're operating normally beyond that. I haven't yet opened the case to check for dust - I'm not entirely sure how with this laptop. I suspect it involves removing more of the bottom than I'm strictly comfortable with.

Running the virtual machine does seem to have increased the temperature, but only by a few degrees so far. Maybe last night was just a freak occurrence. I'll post again with new info in a couple hours, see if my laptop keeps overheating.

Thank you, the response is appreciated.

EDIT: I forgot to mention, I'm using the proprietary radeon drivers since I use my computer for gaming sometimes.

---

### Post by linux_tech on 2012-07-26
If the laptop is a few years old and heating up, best thing to do is try cleaning it first.  A can of compressed air or air compressor. Turn off laptop and disconnect electric.  Locate the heatsink vent usually on the side of laptop.  Usually there is a vent under on bottom of laptop nearby the side vent.   Spray compressed air first up through bottom vent so some dust can exhaust through the side, then spray in through the side. The dust collects between the heatsink and fan forming a mat that prevents air from exhausting and traps the heat in.  If you want to go one better than this then usually taking off the keyboard exposes the fan and heatsink. The heatsink will also usually detach if you loosen the captive screws holding it down.  But if you take off the heatsink then you will need to clean heatsink and processor, then reapply a very thin even coat of thermal paste. Usually just cleaning out the dust is sufficient though.

---

### Post by Dylan1473 on 2012-07-26
No more overheating problems today, so I'm going to go ahead and mark this as solved. I've run into a ton of other weird issues now, but I don't think they're related to this and it looks like my window manager recently went through some major upgrades so I figure I'll just have to wait while they work out some bugs.

Linux_tech, I'll keep your advice in mind - it seems possible this could happen again and maybe get worse, so I may need to clean it out. 

I'm getting a new nicer laptop in about a month, fortunately (though my little brother gets this one so I probably should leave it in decent condition).

---

### Post by Ralph L on 2012-07-27
It might be useful to display the clock frequency being used.  This can be done by Alt right-clicking a panel, selecting Add to Panel, and adding CPU Frequency Scaling Monitor.  It has settings accessible by right click its icon on the panel.

---

