---
title: "memory problems"
date: 2010-07-25
forum: General Help
---

### Post by complience on 2010-07-25
Im getting alot of problems with my new build.

I've tried both Karmic & lucid and got the same problems.

Applications across the board fail due to segmentation faults.

Everytime I reboot the system is in a different mood, sometimes the bluetooth isnt functioning, somtimes the motherboards sounddrivers arent detected, sometimes the Wifi card isnt seen...

I tried changing from the 32bit install to 64bith - things improved but only slightly.

I've run the standard memory checker and it comes back fine, but I am certain there is an issue with it - what other methods are available for confirming memory errors?

---

### Post by jobix on 2010-07-25
- How much RAM do you have?
- How old is your RAM?
- Did you try changing the RAM to see if the problem still persists?

---

### Post by complience on 2010-07-25
Two sticks of Two Gig

Brandnew - infact the first sticks I got for this build did show faults when I error checked them so i sent them back and replaced them.

I've tried taking out one of the sticks, and the problem remains.

It seems to be some sort of caching or image retardation because its only after you restart the box a couple of times that it seems to correct itself temporarily.

---

### Post by bakegoodz on 2010-07-25
Sometimes hardware problems very elusive. I have 15 years experience repairing computers, and access to high end diagnostic tools and I still don't have a solid diagnosis for a computer. Microsoft reporting the bluscreens from ram problem, but their ram test and memtest86 says everything is fine. It doesn't matter which linux live CD I put in, it will still randomly reboot. I put in a $900 hardware diagnostic card in, and it can't find a single problem. I think it is the motherboard, only one clue is a single capacitor that is crowning with gas pressure. Have had a few hardware problems like this before, lucky they are not common.

I'm thinking your problem is in the motherboard too.

---

### Post by complience on 2010-07-26
Great to have the support of your knowledge.. unfortunate luck for a new build.

I've been putting it off.. but I think your right
My ASUS M4A79T Deluxe 790FX board is duff

After taking out one of the sticks of ram the problems werent going away after rebooting, the bluetooth just wouldn't become enabled or/& the sound wouldn't work.

Frustrated... I tried the internal 'reset' button on the actual motherboard that i've never used before.

Think its designed for heavy overclockers to use when they are in the middle of clocking. Not actually sure what the button does over that of the standard external restart button.

But.. magicly after pressing it.. bluetooth and sound was working.. no application crashes..

werid.. my guess is it resets the CMOS (whatever CMOS is)
But makes me think its definitely a motherboard issue

---

### Post by complience on 2010-07-27
Okay as we can't seem to get to the bottom of this, im sending the board back to ASUS..

:( a sad sad day for Taiwanese manufacture

---

### Post by Wim Sturkenboom on 2010-07-27
> **complience said:**
> 

But.. magicly after pressing it.. bluetooth and sound was working.. no application crashes..

werid.. my guess is it resets the CMOS (whatever CMOS is)
But makes me think its definitely a motherboard issue
Probably a damaged track somewhere on/in the board or a bad solder joint

---

### Post by 3rdalbum on 2010-07-27
Take the RAM sticks out. If they have the word "Kingston" on them, then they are faulty and should be sent back for a full refund.

No but seriously, the memtest86+ should be run for hours (as in, overnight). You could also try running the memory speed benchmark in Phoronix Test Suite; if this crashes the computer then you've got bad RAM.

---

### Post by complience on 2010-07-27
Phoronix Test Suite?

is that some kind of LiveCD?

---

### Post by bakegoodz on 2010-07-27
Memory problems are usually not the RAM. I've only found a few bad sticks of RAM in many years of doing computer repair service. In my experience if it bad RAM it shows up pretty quick in memtest. 90% of time RAM errors are actually the motherboard, and it can sometimes take a couple hours of memtest to make those show up. This may make sense for an electrical engineer, but I'm perplexed that I seen many motherboards lose compatibility with RAM (especially low latency/High performance ram) or lose the ability to do dual channel. Capacitor aging maybe?

---

### Post by complience on 2010-07-28
Had a look at Phoronix Test Suite

Seemed fairly complicated to use at the command line & the GUI didn't seem to work when i try to start it.

Sending the Boardback to the supplier - will get a replacement.

---

### Post by complience on 2010-08-09
I changed the motherboard for a new one (ASUS M4A79T Deluxe 790FX)

Things have gotten worse :(

Now it doesnt even boot, no bios, no beeps nothing.
The fans start up, the lights turn on.. so the PSU is working.

If i remove all the sticks of RAM then I get the continual beep warning.

I'm at a total loss.. I think the CPU might be dead, or not compatible with the bois installed on this particular board.

im so pissed.

---

### Post by complience on 2010-08-09
G.SKill NQ Series 4GB (2x2GB) DDR3 PC3-12800 1600MHz CL9 Dual Channel memory Kit - F3-12800CL9D-4GBNQ

---

