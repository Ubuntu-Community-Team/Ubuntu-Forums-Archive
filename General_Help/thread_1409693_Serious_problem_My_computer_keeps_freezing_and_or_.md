---
title: "Serious problem: My computer keeps freezing and or randomly shutting off..."
date: 2010-02-17
forum: General Help
---

### Post by CharlesJWelsh on 2010-02-17
Randomly; my computer will freeze up. I can move the mouse but I cannot click on ANYTHING. This has happened at LEAST 20 times today. Occasionally my computer will totally just shut down. I need some kind of help because my computer has been almost completely rendered USELESS. I do not know what to do or even where to begin. Please give ANY input you may have. The sooner we solve this problem the better. I do college online... so this has a major impact on me and my work and progress as a student.
Regards;
CJ

---

### Post by mikewhatever on 2010-02-17
What kind of computer is it? Can you post some specs.
Random freezes can mean faulty hardware. Try running memtest, which is one of the options on the live cd menu.
Could be overheating too. Try clearing dust from the insides.

---

### Post by CharlesJWelsh on 2010-02-17
Would bad sectors on my HDD be the cause of it? I am replacing my HDD. AND while im at it... is there a way I can increase my fan speed on Ubuntu? I knew i could on windows... But that may help the issue if it is hardware related.

---

### Post by CharlesJWelsh on 2010-02-17
How would i get the specs?

---

### Post by mikewhatever on 2010-02-17
> **CharlesJWelsh said:**
> Would bad sectors on my HDD be the cause of it? I am replacing my HDD. AND while im at it... is there a way I can increase my fan speed on Ubuntu? I knew i could on windows... But that may help the issue if it is hardware related.

Yes, a failing hdd may be the cause, however fan speed will do nothing in this case or if you have faulty RAM.

---

### Post by CharlesJWelsh on 2010-02-17
How do I know if it is my RAM?

---

### Post by CharlesJWelsh on 2010-02-17
here is my RAM info...
description: System Memory
       physical id: 81
       slot: System board or motherboard
       size: 512MiB
       capacity: 1GiB
     *-bank:0
          description: SODIMM SDRAM Synchronous
          physical id: 0
          slot: DIMM 0
          size: 256MiB
          width: 64 bits
     *-bank:1
          description: SODIMM SDRAM Synchronous
          physical id: 1
          slot: DIMM 1
          size: 256MiB
          width: 64 bits

---

### Post by mikewhatever on 2010-02-17
Memtest.

I've mentioned it before, just be aware that it takes some time. Probably best to leave it working overnight.

---

### Post by CharlesJWelsh on 2010-02-17
okay and before i do this... what will it be doing? What is the purpose? (NO i am not questioning your motives i am simply trying to learn.)

Is that the Installation CD? As in i have to boot from that?

---

### Post by woodmaster on 2010-02-17
what is your graphics card? post output of lspci grep VGA.  I had to go to an older driver for my graphics card to eliminate this problem.  There are posts about reverting the xorg driver on here if you search.  As a temporary fix when it locks up, SSH by pressing alt+F2.  Login to the prompt with usual name and pass. and enter the command: sudo restart gdm.  Faster than rebooting to get back to working system

---

### Post by CharlesJWelsh on 2010-02-17
lol... im sorry but i do not have a clue as to what my cards are. ANY of them. I just know i have a 20GB HDD Hitachi or somethin. Im gettin it replaced because it has bad sectors... I dunno if thats bad but i know its not good. Maybe you can tell me how to find this information?

---

### Post by CharlesJWelsh on 2010-02-17
> **woodmaster said:**
> what is your graphics card? post output of lspci grep VGA.  I had to go to an older driver for my graphics card to eliminate this problem.  There are posts about reverting the xorg driver on here if you search.  As a temporary fix when it locks up, SSH by pressing alt+F2.  Login to the prompt with usual name and pass. and enter the command: sudo restart gdm.  Faster than rebooting to get back to working system

Is it faster than the Alt+A+U+B+PrtSc?

---

### Post by mikewhatever on 2010-02-17
> **CharlesJWelsh said:**
> okay and before i do this... what will it be doing? What is the purpose? (NO i am not questioning your motives i am simply trying to learn.)

Is that the Installation CD? As in i have to boot from that?

As I am no expert, you can read on memtest yourself. [http://www.memtest86.com/tech.html#philo](http://www.memtest86.com/tech.html#philo)
There is more then one way of running memtest, the one I suggested was from the Ubuntu installation cd. Yes, you need to boot from the cd, which may be handy with the faulty hdd, but, needless to say, you don't have to install anything.

---

### Post by CharlesJWelsh on 2010-02-17
Here are the results...

Pentium 4 (0.13) 2394 mhz
L1 cache:    8k 17348 MB/S
L2 cache: 256k 15152 MB/S
L3 cache: none
Memory: 495M    950 MB/S
Chipset: Intel i852 PM  /GM  /FSB:   99 mhz/ mobile platform
Settings: Ram 132 mhz (DDR264) / CAS: 2.5-3-3-6

Test Pass  FailingAddress--------        Good------          Bad--------           Err-Bits--------      Count
2----- 0---       000016fe19c 22.8-    00000000   00000100   00000100--   1
5-----      0---       000016fe198 22.8-    fffffeff-----        ffffffff------         00000100----   136
6-----      0---       000016fe19c 22.8-    00000080   00000180   00000100--   137





And thats it. :) Is that what you needed?

---

### Post by mikewhatever on 2010-02-18
Where does that come from?

---

### Post by CharlesJWelsh on 2010-02-18
The memtest :/

---

### Post by CharlesA on 2010-02-18
Where did you run memtest from? Best thing to do would be to download the iso and burn it to a cd. DDR264 doesn't look right.

---

### Post by CharlesJWelsh on 2010-02-18
From my live cd... I have the cd from cananocal or whatever its called. AND i have a downloaded one. This were the onscreen results.

---

### Post by starredsteria on 2011-01-05
I too am having the exact same issue. Haven't done the mem test yet, but I figured I would post that this person is not the only one. I have a Acer Aspire One netbook running Maverick 10.10 Ubuntu Netbook edition (but often boot in Desktop Edition due to the dual monitor issue). Ill try to do the mem test... and post... but if there is any other info such as what drivers I have installed, please post the terminal cmd and I will reply. - Thx

---

