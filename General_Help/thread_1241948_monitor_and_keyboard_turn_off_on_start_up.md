---
title: "monitor and keyboard turn off on start up"
date: 2009-08-16
forum: General Help
---

### Post by rahrahmah on 2009-08-16
I have the newest version of Ubuntu, 9.04, and sometimes (but not everytime) it won't boot properly. It'll start, it'll do all the little checks, and it'll get to the part where it says ubuntu and has the little loading bar... then the monitor and keyboard suddenly turn off. The computer stays on, I can't push the power button to turn it off, I have to turn it off from the power bar. This never happened before, it's not a hardware issue. It might do this two or three times in a row, then it'll be fine again. It's done this before, but it didn't for awhile so I ignored it. It's done it again now, and I'm concerned. Obviously, it's not good to have to shut everything off suddenly from the power bar. Is this a known bug? Can I fix it?

Also, while we're here, my computer runs slower than damn molasses. Way slower than it ever did on windows. I was told ubuntu ran FASTER and was so great you could put it on old machines and make them run like new. Is there possibly something I have to do to calibrate it?

---

### Post by rahrahmah on 2009-08-16
bump

---

### Post by rahrahmah on 2009-08-16
bump

---

### Post by wojox on 2009-08-16
Don't know. Sounds like a hardware issue. What kind off machine are you running?

---

### Post by rahrahmah on 2009-08-16
Pentium 4, 2.93 Ghz. The newest ubuntu. The computer itself is called "emachines". It's only a few years old, and I never had this problem until I installed Ubuntu. There was an old thread on here, I saw, that had a similar problem, but no resolution.

---

### Post by rahrahmah on 2009-08-19
The same thing happened this morning. I KNOW this is NOT a hardware problem. I tried pressing buttons (like to degauss), and the monitor informed me it was in power-save mode and that I had to move the mouse or press a keyboard button to wake it up. But those things didn't work. It wasn't getting signals from the computer. I had to turn it off at the power bar and try again. It worked on only the second try this time, but it powered down briefly and hung for a few moments, before turning back on as ubuntu started up. This is an Ubuntu problem. I think that, for whatever reason, it doesn't start up on start up every time. Investigating this problem on (very old, and unresolved) threads indicated that ubuntu might do something to the video signal (or something, I didn't really understand) that confuses the monitor (can you confuse a monitor?) which makes sense, because a couple of times it's had to auto-adjust itself on start-up as well, which I've never seen till I got ubuntu. 

Also, when firefox is open my CPU usage is through the roof, which is probably something to do with how slow it is. Is there someway I can make firefox use LESS than 80% of my CPU? It's like using dial-up.

---

### Post by MaxIBoy on 2009-08-19
This could potentially be an overheating problem. Overheating does tend to cause irregular problems like this, and Pentium 4s are notorious for running hot. It can also explain the performance issues you're having, if the system underclocks the processor to stop it from frying. 

When was the last time you opened the case and vacuumed all the dust out? You're supposed to do this every six months or so. Otherwise the dust builds up. It A) hampers overall airflow, B) collects on the heatsinks, acting as an insulator and preventing it from dumping heat, and C) clogs up the fans.

Also, is the PC in a well-ventilated area?


EDIT: it's also entirely possible that only certain operating systems will be effected by overheating. Different OSs have different fan control software installed which behaves differently. I believe in Ubuntu, the fan control software only turns on later in the booting process.

---

### Post by rahrahmah on 2009-08-19
I never actually have taken the dust out. Could that really be the answer? Goodness, I hope so, because that's easy to do! It doesn't involve me talking to kernals or roots or anything. Thanks so much, I'm going to try right now.

---

### Post by rahrahmah on 2009-08-19
The inside of my computer was not as dusty as I thought it would be, considering I hadn't dusted it in it's three year life, but was supposed to do it bi-annually. The fan itself was filthy, though, and the grate beneath it was more than likely at least partially clogged. I don't know if this solved the problem I came here to ask about, since it was a sporadic problem, but you've at least saved me a lot of trouble later on, so thank you VERY much! I notice already that the fan is WAY quieter than it used to be.

I had no idea you should be dusting in there. I was under the impression that the less opening up and handling done, the better. I knew that a computer could over-heat but I thought that was something only techies who pushed their machines too far had to worry about. I remember when I was in high school no one had ever told me that you shouldn't put magnets on a computer. I just had no idea. So I put a bunch of decorative ABC magnets on the tower case, you know, for some personality. Oops. It took a while, but by the time anyone figured out what was going on, the thing was done for. I just hope that I haven't done too much damage already.

---

### Post by MaxIBoy on 2009-08-19
Most people never dust their computers, and they last for five years at most. If you dust your computer regularly, it will last ten years or more!

---

