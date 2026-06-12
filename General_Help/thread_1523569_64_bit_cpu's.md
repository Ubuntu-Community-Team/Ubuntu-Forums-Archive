---
title: "64 bit cpu's"
date: 2010-07-03
forum: General Help
---

### Post by Timothy Benton on 2010-07-03
i'm wondering how 64 bit cpu's handle 32 bit operating systems and processes. are they designed for 64 bit? or is the 64 bit just an extension, or extra ability? i already know that 64 bit operating systems (windows and linux) have to use emulators to run 32 bit apps. i am aware they work pretty well, but it isnt native. do 32 bit os'es like windows xp x64 or ubuntu amd64 run natively on 64 bit processors or do they have to go through some kind of hardware emulation on the cpu?

basically i'd like to know how 64 bit processors handle running 32 bit operating systems.

---

### Post by QIII on 2010-07-03
Both AMD and many of Intel's 64 bit processors (as well as many other of the lesser players) can run in "long mode"  and "legacy mode" -- 64 and 32 bit respectively.  I think there is some  compatibility issue with the Intel Itanium processors with regard to how  they fit into the 64 bit community, so I don't know if it is true for them.
 
 If "started" in 64 bit mode  (i.e.: a 64 bit operating system), both 64 bit and 32 bit applications  can run simultaneously (see caveats at the end of this paragraph).  If "started" in 32 bit mode (i.e.: a 32 bit  operating system), only 32 bit applications can be run.   Caveats:  Many purely 32 bit applications simply will not run in a 64 bit OS;   some 32 bit applications that do work will work better with a "wrapper" when a  64 bit OS is running.

Countering the caveats:  Almost everyone is has ported or is currently porting (madly) everything to a 64 bit platform.
  
  So it is not necessarily true that there needs to be any "emulation" to  run a 32 bit OS on a machine with 64 bit architecture.  That's the fairly easy part.  The CPU starts either in long or legacy mode.

The difference between 2^32 and 2^64 is pretty large, but what is also important in a 64 bit machine are the modern instruction sets available.  A 32 bit OS would not be able to take advantage of much of that.

But, with all of that, the really important consideration is this:  The machine architecture is 64 bit and the industry has pretty much switched to 64 bit operating systems.  Sticking to a 32 bit OS right now would be about as pain free as staying with 16 bit was when 32 bit became the standard.  Getting left behind can leave a hollow feeling in the pit of your stomach.

So, the question is academic.

---

### Post by Astronaut356 on 2010-07-03
Don't know how 64 bit CPU's handle 32 bit operating systems. FWIW, I installed the 64 bit 10.04 and **everything[B]has worked flawlessly. **[/B]I have had no compatibility issues with any application using a 64 bit OS. Also, my experience with 64 bit Windows 7 is the same.

---

### Post by dcstar on 2010-07-03
> **Timothy Benton said:**
> 
.........
basically i'd like to know how 64 bit **processors** handle running 32 bit operating systems.

Natively, all Intel based 64-bit CPUs support 32-bit instruction sets.

If you want to know how 64-bit **Operating Systems** handle 32-bit code, then that is another issue.

---

### Post by Timothy Benton on 2010-07-04
> **dcstar said:**
> Natively, all Intel based 64-bit CPUs support 32-bit instruction sets.

This is exactly what I wanted to know. I thought maybe 32-bit code had to go through a wrapper of some sort to run on a 64-bit processor. Thanks!

---

