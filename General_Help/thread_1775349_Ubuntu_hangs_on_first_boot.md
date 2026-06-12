---
title: "Ubuntu hangs on first boot"
date: 2011-06-04
forum: General Help
---

### Post by paradox. on 2011-06-04
Okay... I built my computer and having trouble booting Ubuntu, here are my system specifications.


System Specifications: 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

CPU: AMD Athlon II X4 3.0GHz Quad-Core
GPU: ATI Radeon HD 5750 1GB 128-bit GDDR5
Motherboard: ASUS M4A88TD-V EVO/USB3	
Memory: 4G G.SKILL Ripjaws DDR3 1600 
PSU: Cooler Master GX Series 750w
HDD: 500GB Samsung 7200 RPM

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Problem:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Okay. So I have Ubuntu on a DVD and have tried both my DVD drives, AND an external DVD drive and have no luck. I have tried different versions of Ubuntu and get the same problem.

So I boot it fine and it gets the the Ubuntu splash screen and I select "Install Ubuntu" it loads for a few seconds then goes to a black screen with a blinking cursor in the top left corner. It sits here forever. I tested on my friends computer with very similar processor and it blinks for about 3 seconds then an Ubuntu splash screen appears with dots under it and it loads and works fine, so I am 100% positive the DVD is fine and should work for my processor also. I have been searching the web for weeks and haven't found a solution for this problem. I am a Linux noob but have used it in the past and like it a lot.

I do have Windows 7 currently installed. And I made a 100 GB partiton via Windows 7 using Easeus Partition Manager

If it matters, I did test Ubuntu on my computer by installing it from VirtualBox and it worked fine...but i'd rather do a dualboot because I don't like running an OS in another OS and its performance isn't so great when emulating an Operating System...

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ANY help is appriciate.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Thanks,
   Paradox.

---

### Post by paradox. on 2011-06-04
Bump...i know its only been 15 minutes but I have been working on this for weeks and its very frustrating :(

---

### Post by jim_deadlock on 2011-06-04
When you say you get the blinking cursor "forever", how long exactly? I've had that screen for 20+ mins on previous installs, then it carries on nicely, I think it's just checking hardware and stuff at that stage.

---

### Post by paradox. on 2011-06-04
by forever, i've waited like...10 minutes but, my friends computer has very low specs and only took about 3 seconds that why I figured its not doing anything. but after about 5 minutes the disc completely stops spinning, so im pretty sure it hangs :(

---

### Post by Joe- on 2011-06-04
Have you tried just running UBUNTU rather than installing it? And then if that works install from the shortcut on the desktop?

---

### Post by paradox. on 2011-06-04
same problem running Ubuntu and installing it. Always gets the blinking _ and hangs :( i have no clue what can be causing this...

---

### Post by jim_deadlock on 2011-06-04
5 minutes is nowhere near long enough. It will appear to stop working and go silent but it is actually still doing stuff. Just because your friend's computer took 3 sec at this stage doesn't mean anything. Leave it and go and do something else for at least 20-30 mins and you may be pleasantly surprised when you get back.

---

### Post by jim_deadlock on 2011-06-04
I just remembered the reason why I got that flashing cursor for so long before, it was when I built a new computer and I had the drives plugged into the 6Gb connectors on the motherboard, I switched them over to the 3Gb ones and it fixed the problem. Anyway, the point is that this flashing cursor screen is when it's checking your hardware before it even starts loading Ubuntu.

---

### Post by paradox. on 2011-06-04
:o i think i may have it plugged in the 6gb...which cable exactly are you talking about?

---

### Post by jim_deadlock on 2011-06-04
The data cable that goes from the drive to the motherboard connector, my motherboard has one grey, one dark blue (both 6Gb) and two light-blue (3Gb), I don't know if it was my CD drive or HDD (or both) causing the problem, but I switched them both over to the 3Gb light blue ones and since then I've had fast bootups.

---

### Post by paradox. on 2011-06-04
my motherboard case shows 2 ports and has a 3gb/s port and 6gb/s port. but when i open it i cant find a 3gb/s port... would it be something i would be something i could possibly adjust in my BIOS?

---

### Post by paradox. on 2011-06-04
are u talking about the main 24 pin connector? which would be my sata cable

---

### Post by paradox. on 2011-06-04
okay well I have 4 slots for ram sticks and when i built my computer i put them next to each other so i tried leaving a space between them and it seems to be booting now. thanks!

---

### Post by Bobrm2 on 2011-06-05
I think I need just to wipe the HDD, there's nothing on it and start again. Can I move the CMOSjumpers, yes, but will I hard the computer? And if I use CMOS jumpers is that a solution? There has been some chatter about a MS-dos program and wipes a hard drive completely

---

