---
title: "Ubuntu freezes completely randomly, no response whatsoever..."
date: 2011-07-11
forum: General Help
---

### Post by gwu777 on 2011-07-11
Hi there,

Very annoying problem, just build a new PC, new 500GB HDD and:

[FONT=Arial][SIZE=1]AMD Processeur Phenom II X4 955 Black Edition 3.2 GHz - 125W
[/SIZE][/FONT][FONT=Arial][SIZE=1]GSkill RipJawsX 4Go DDR3 C9 1600Mhz
[/SIZE][/FONT][FONT=Arial][SIZE=1]Carte mère socket AM3 - Chipset AMD 880G & SB710[/SIZE][/FONT]

Installed ubuntu 11.04, and now extremely randomely, it freezes completely, cannot get to a console, ie CTRL+ALT+F1, ALT+F2, the mouse do not even move. I have to turn it off and restart.

It may not happen for a whole day as it can happen 2 or three times in a row. From what I have gathered, it only happens when I use the PC as I can't remember coming to the PC and finding it frozen.

From searching the forum, some people seems to have problem because of the 4 cores of the phenom, but it was very vague.

How can I know better what is happening and how to fix it. I have so little time, I really would love to avoid re-isntalling the whole thing again, as it is properly setup at last.

Any ideas are VERY welcome...

---

### Post by doas777 on 2011-07-11
well, to start with, if your system is locked, try this to get a graceful shutdown
hold Alt + printscrn/sysreq and **slowly** type
```
reisub
```your towers io light may come on with s or u. wait until it is dark again before submitting the next keypress.
if this method does not work, then your system is locked all the way down to the kernel. 


as for Kernel freezes and locks, the problem is almost always the drivers or the kernel's interface to essential hardware. 
next time it locks up, make note of the PC time.
then reboot, and check your Log File Viewer, and look at
dmesg.0, as well as the messages, syslog, and kernel log for the time of the freeze.
that should give you some idea of what is causing the problem. 

what video card driver do you have installed?

I've done some looking, and I'm not seeing evidence of widespread endemic issues with the quad core phenoms. when they were brandnew, there were some issues using all cores, but I haven;t seen much reference to lockups.
this is not to say that you are not having a hardware problem, or a software configuration issue for your specific hardware configuration, but simply that there is no common well known fix.

---

### Post by dabl on 2011-07-11
You can open a terminal window and run ```
top
```

When the "freeze" happens, look at the terminal and see which process is hogging the CPU.  That tells you where to start troubleshooting the problem.

---

### Post by wildmanne39 on 2011-07-11
Hi, here is a link for freezing issues if you still have the problem after the other suggestions.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by gwu777 on 2011-07-25
> You can open a terminal window and run

No I can't and this is the problem. Following some of the advices above, here are my findings:



reisub do not do anything however slow I do it
I have change the graphic driver ATI catalyst to the generic one and I believe there is an ever so slightly improvement. It sill freezes, however, now  it sometimes closes X and I am in terminal, however, I cannot input anything as it is frozen there again, I haven't noted what it says so far, but definitly something crashes, I will let you know the next time it happens.

---

### Post by gwu777 on 2011-08-06
I have tried all the above, I cannot access anything. I have re installed the whole system, even without any additional proprietary driver such as the graphical one, the freeze keeps happening, just time I get to the console rather than a frozen screen. The console is completely frozen, the messages are always different. Is there any log I could look at or show you?

It still happens completely randomly, I cannot find a pattern.

Here is my config with integrated graphics:
Asus M4A88T - Chipset AMD 880G/SB710
GPU ATI Radeon™ HD 4250 integrated
AMD Phenom II X4 955 Black Edition 3.2 GHz
GSkill RipJawsX 4Go DDR3 C9 1600Mhz - Dual channel 2 x 2Go

Hope this helps as I really need help...

I am going to try and use fedora on my multiboot, to see if this problem appears also...

---

### Post by CatKiller on 2011-08-06
It's possible that it's a kernel/driver problem, but it sounds much more like a hardware problem to me. Some kind of short-circuit, bad RAM or noisy power could all cause the symptoms you describe. Damaged motherboard, too, I suppose, in either a memory-addressing or voltage-regulating section.

---

### Post by gwu777 on 2011-08-06
> **CatKiller said:**
> It's possible that it's a kernel/driver problem, but it sounds much more like a hardware problem to me. Some kind of short-circuit, bad RAM or noisy power could all cause the symptoms you describe. Damaged motherboard, too, I suppose, in either a memory-addressing or voltage-regulating section.

This is my great fear. Everything is new, done it since the beginning... Voltage setting could it be bios setting? How could I found out? I am not going to buy an other PC!

---

### Post by CatKiller on 2011-08-06
Check your standoffs for the motherboard. That would be my first guess. Then run memtest overnight. Then try your cables. Running barebones with minimal components is a standard trouble-shooting step.

---

### Post by gwu777 on 2011-08-06
> **CatKiller said:**
> Check your standoffs for the motherboard. That would be my first guess. Then run memtest overnight. Then try your cables. Running barebones with minimal components is a standard trouble-shooting step.

Will have to search for standoff for the motherboard, however some new information:

Here are the result for memtest with various combinations or ram and slots, I initially did two passes of the whole test, but only found error on test 5, so I have done the rest of the testing on test 5 only:

RAM1 SLOT1 = NO ERRORS TEST 5
RAM2 SLOT1 = NO ERRORS TEST 5
RAM1 SLOT2 = NO ERRORS TEST 5
RAM2 SLOT2 = ERRORS TEST 5

RAM1 SLOT1 & RAM2 SLOT2 = ERRORS TEST 5
RAM2 SLOT1 & RAM1 SLOT2 = NO ERRORS TEST 5

RAM1 SLOT3 & RAM2 SLOT4 = NO ERRORS TEST 5

It seems I only get error when RAM2 is in SLOT2, does this make any sense. There are both same RAM, from the same package (ie 2x2Gb)

Tonight, I will run a whole nighter memetest on RAM2 SLOT1 & RAM1 SLOT2, and I will test the PC with this combination.

Any insights as always appreciated...

---

### Post by CatKiller on 2011-08-06
Ding ding ding, we have a winner! :)

The manual will have a recommended memory configuration. The last build I did recommended slot 1 & slot 3, which I wouldn't have expected. I agree that further testing with those sticks the other way round is worth doing, since that seems to work even though the same sticks give errors as you had them before. Weird, but it will save you having to send them back for replacements. Might be worth doing anyway, for peace of mind, depending on how convenient it is. One error is too many, obviously.

The standoffs are the screws that go between the motherboard and the case. They act as earthing points. If you miss one, that part isn't earthed, which can cause a build-up of charge. If you put one in the wrong place, it can lead to a short-circuit. Both of those are easy to do on a new build. Doesn't seem like it's the case here, now, though. The other fun one is that you sometimes get metal slivers from the screw holes, especially on cheap cases, that are almost impossible to spot but again cause short-circuits.

---

### Post by gwu777 on 2011-08-06
> **CatKiller said:**
> Ding ding ding, we have a winner! :)

The manual will have a recommended memory configuration. The last build I did recommended slot 1 & slot 3, which I wouldn't have expected. I agree that further testing with those sticks the other way round is worth doing, since that seems to work even though the same sticks give errors as you had them before. Weird, but it will save you having to send them back for replacements. Might be worth doing anyway, for peace of mind, depending on how convenient it is. One error is too many, obviously.

The standoffs are the screws that go between the motherboard and the case. They act as earthing points. If you miss one, that part isn't earthed, which can cause a build-up of charge. If you put one in the wrong place, it can lead to a short-circuit. Both of those are easy to do on a new build. Doesn't seem like it's the case here, now, though. The other fun one is that you sometimes get metal slivers from the screw holes, especially on cheap cases, that are almost impossible to spot but again cause short-circuits.

Thank you ever so much for this piece of information, I now know a new word and I probably will have to change this old casing I built the new PC in!

Coming back to the memory, I will have a look in the manuel and do so more testing. Will let you know the result of the nightly memtest.

Thank you for the time and good advice, will keep you posted.

---

### Post by CatKiller on 2011-08-06
The case will probably be fine. Old cheap cases have generally already lost all the bits of metal they're going to. They still require a blood sacrifice, though :)

Again, the motherboard manual will probably tell you which ones you need to put a screw through. Older cases tended to need brass shims to go between the case and the motherboard at the appropriate points, which is why they're called standoffs, but newer cases are dimpled at the appropriate points.

---

### Post by gwu777 on 2011-08-07
Here are the lastest development:

Redone the following test and found errors, so SLOT2 probably has a problem...

RAM2 SLOT1 & RAM1 SLOT2 = ERRORS TEST 5

5 hours on SLOT3 & SLOT4 = NO ERRORS

Had a look at the manual, here is what it says cf attachment:

Channel A DIMM_A1 and DIMM_A2
Channel B DIMM_B1 and DIMM_B2

However DIMM_A2 and DIMM_B2 are the first 2 and are black and DIMM_A1 and DIMM_B1 are the last 2 and are blue. I always though you should respect the color for dual channel RAM, but it seems that in that case I have to respect DIMM_A1 and DIMM_A2 to have the same channel?

Which DIMM do I put my RAM into?

Furthermore it says : Install the DDR3 1600 or higher frequency DIMMs on the blue slots for better overclocking performance.

Not  that I intend to overclock, but here it seems, you should follow the color rather than the channel... My memory was previously installed on the black DIMMs.

Does any of this explain why I have errors when the RAM is insidle slot2 or DIMM_B2

Sorry, I know I should understand all this by now, but as you guys seem to be good at this, I appreciate your help...

---

### Post by CatKiller on 2011-08-07
If your manual suggests that one blue and one black will work, it's worth doing that. My last build did and it surprised me just as it has surprised you. It definitely seems like you should be avoiding slot 2 since neither of your sticks have worked there so far when you've had them both in.

---

### Post by gwu777 on 2011-08-07
> **CatKiller said:**
> If your manual suggests that one blue and one black will work, it's worth doing that. My last build did and it surprised me just as it has surprised you. It definitely seems like you should be avoiding slot 2 since neither of your sticks have worked there so far when you've had them both in.

This is what I have been running lately, memtest is OK, should I see a difference when running in dual channel, any test I could do?

I really find all this weird, should I try to have my board changed?

---

### Post by CatKiller on 2011-08-07
I believe memtest shows a higher memory bandwidth when you're running in dual-channel mode.

If it turns out that slot 2 is definitely faulty, exchanging the motherboard is certainly an option.

---

### Post by gwu777 on 2011-08-07
> **CatKiller said:**
> I believe memtest shows a higher memory bandwidth when you're running in dual-channel mode.

If it turns out that slot 2 is definitely faulty, exchanging the motherboard is certainly an option.

I realise I am now probably starting to be a pain, but here are further result from memetest:

Channel A DIMM_A1 and DIMM_A2 (SLOT1 & 3) : Memory says 4489Mb/s
DIMM_A2 and DIMM_B2 (SLOT 3 & 4) : Memory says 4740Mb/s

Does this increase justify/show the dual channel on? I would have expected more... And if so, it is the color to be respected rather than the supposed channel. I really would like to understand better this issue.

---

### Post by CatKiller on 2011-08-07
I'd expect more, too. The maximum bandwidth for DDR3-1600 in dual-channel mode is 25.6 GB/s, according to Wikipedia. I'm not sure if you've said what clock rate you're running at, but even at 1066 you'd hope for higher than you're getting. There may be a BIOS setting or motherboard jumper to allow dual-channel mode, as well as memory configuration. There may also be information in the BIOS about the memory information received from SPD to let you know if there's a problem with the way the memory's been detected.

As for colours, I couldn't tell you. I just do what the manual says :)

---

### Post by sierpito on 2011-08-17
Do you use Skype?
I had exactly the same problem and I found this [link]("http://forum.skype.com/index.php?showtopic=817699") and this [link]("http://forum.skype.com/index.php?showtopic=815125") on Skype forum. Unfortunately, there is only description, but no solution for this (solution with Skype on VM sounds very sad).

---

### Post by buddyd16 on 2011-08-17
Are you using the 64 bit version of flash?

I was having this exact issue seemingly random lockups and no ability to do any of the keyboard commands to restart or get into a terminal. After messing around more I found that the lockups happened pretty much anytime an embedded flash video was loaded. I used the flash aid firefox plugin to completely remove flash and install the 32 bit version and now I have not experienced any lock ups.

---

### Post by gwu777 on 2011-09-13
After a few weeks avoiding slot 2, no more freezes, my motherboard does have a fault. I am now confuse on how to know if I am running dual channel mode, how can I know this? I do not believe memtest to be the way to know this... Ideas would be appreciated...

Here are the various reading from the memtest if it gives anyone insight:
L1 cache 64K   52696Mb/s
L2 cache 512K 17007Mb/s
L3 cache 6144K 9237Mb/s
Memory 3838M 4762Mb/s

Thank you for you continuous help

---

### Post by gwu777 on 2011-11-02
Marking this thread as solved as my mothreboard seems to be faulty. Change the ram's slot and now everything is fine. Thank you all for your help.

I now really would like to know if I am running dual channel or not. I shall open a new thread.

---

### Post by Jouke74 on 2011-11-02
> **gwu777 said:**
> Marking this thread as solved as my mothreboard seems to be faulty. Change the ram's slot and now everything is fine. Thank you all for your help.

I now really would like to know if I am running dual channel or not. I shall open a new thread.

- Memtest should be error free, or indeed random freezes will occur.

- If you want to use dual channel you should use one black and one bluse channel A1+B1, or both (A1+2, vs B1+B2).

- Check also if the Phenom can run on the desired memory frequency. The old Phenoms could not run on anything higher than 800mhz if all 4 dimms were used. This should be in the motherboard manual as well.

- Make sure the voltage and settings of RAM are correct.

---

