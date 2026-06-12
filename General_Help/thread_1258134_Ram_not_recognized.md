---
title: "Ram not recognized"
date: 2009-09-04
forum: General Help
---

### Post by gollybegully on 2009-09-04
I had two half a gig sticks of ddr400
Just bought a one gig stick

At startup, it's only recognizing 1.5gb total.

When I run:

> my@my-desktop:~$ sudo lshw | sed -n '/*-memory/,/*-pci/p' | head -n -1
[sudo] password for my: 
     *-memory:0           
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 166 MHz (6.0 ns)
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:1
             description: DIMM 166 MHz (6.0 ns)
             physical id: 1
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:2
             description: DIMM 166 MHz (6.0 ns)
             physical id: 2
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 166MHz (6.0ns)
        *-bank:3
             description: DIMM 166 MHz (6.0 ns) [empty]
             physical id: 3
             slot: A3
             width: 64 bits
             clock: 166MHz (6.0ns)


I get this...it seems to recognize it but only here.  Even when I boot windows it only shows 1.5.

Any ideas? Thanks,

---

### Post by gollybegully on 2009-09-04
bump, should i have put this in another section? hmm...

---

### Post by bodhi.zazen on 2009-09-04
If your RAM is recognized in Ubuntu , but not Windows, I suggest you try a Windows forum.

---

### Post by Whiffle on 2009-09-04
If windows nor linux is recognizing it, I think you may have to tweak some BIOS settings.  What does your bios report for your RAM?

---

### Post by cmost on 2009-09-04
It's also possible that your computer doesn't fully recognize RAM sticks greater than 512 MB.  While 2.0 GB are recognized, perhaps only 1.5 GB total are available.  In that case, you can see if there is a BIOS upgrade that may fix the issue, or, you're out of luck.

Side note to bodhi.zazen...let's not be standoffish to folks because they happen to ask a question related to Windows.

---

### Post by NoaHall on 2009-09-04
Accutally, I think his problem is in both Ubuntu AND Windows - but he can see it through running "sudo lshw | sed -n '/*-memory/,/*-pci/p' | head -n -1", but he can't see it anywhere else . Do as the others have said, and check your bios.

I would not recommend flashing(updating) it unless you know what to do - it can cause major damage

---

### Post by gollybegully on 2009-09-04
> **NoaHall said:**
> Accutally, I think his problem is in both Ubuntu AND Windows - but he can see it through running "sudo lshw | sed -n '/*-memory/,/*-pci/p' | head -n -1", but he can't see it anywhere else . Do as the others have said, and check your bios.

I would not recommend flashing(updating) it unless you know what to do - it can cause major damage

that is correct. neither are recognizing more than 1.5gb

how can i check my BIOS?

---

### Post by NoaHall on 2009-09-04
It depends on your motherboard - when your computer starts up, there will be something on the bottom of the screen which says something like "Press DEL to enter the BIOS settings"

---

### Post by falconindy on 2009-09-04
Hmm, do DIMMs follow any similar rules to SIMMs when mixing different sized modules? Might also want to make sure you're not trying to run as a dual-channel setup.

---

### Post by darkstaar on 2009-09-04
Do you have integrated graphics? If so, some of the RAM will be allocated for the graphics system. This won't be counted as system RAM.

---

