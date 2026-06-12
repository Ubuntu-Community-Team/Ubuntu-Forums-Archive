---
title: "random shutdown"
date: 2009-12-27
forum: General Help
---

### Post by mick222 on 2009-12-27
Lately my computer has been randomly shutting-down i suspect a problem wit either the hard drive or memory. My cpu shows a temp of 56 oC and motherboard of round about 30 i think this is about normal.How do i check the memory and the hard drive I have SMART enabled but this shows no problems . athelon 3400xp ubuntu 9.1 512mb memory and 2 hard drives one 40gig 1 80gig.

---

### Post by Gizenshya on 2009-12-27
stick in a LiveCD and boot from it.  Then scroll to the memtest.  Let it do its thing for a while, and it will tell you if there are any errors.  Post what it says after it completes at least one full cycle (you might need a pencil and paper...)

When it randomly restarts, what exactly happens?  Is it like "normal... normal... normal... black.  startup text."?  Or does it display anything on the screen before the failure?

If you have windows, does it do it there as well?

---

### Post by mick222 on 2009-12-27
Tried running memtester from terminal it showed everything ok.
I dont have windows . It's wierd the screen shuts down my fans keep running but the computer refuses to turn off even when i hold in the power button or press restart.

---

### Post by Gizenshya on 2009-12-27
hats off to you for going windowless ;)

how do you restart it?  unplug it?  If so, do you wait at least 30 seconds before plugging it back up?

How often does this problem happen?

Have you noticed any patterns with the problem?  For instance, if you are doing memory-intensive things, or any particular action, or if it usually is at least X amount of time before it happens, or it never lasts X amount of time without crashing?

---

### Post by mick222 on 2009-12-27
Have to unplug and leave for a few minutes happens randomly i only really use the computer for the internet and watching videos can be ok for hours or crash after a few minutes.

---

### Post by Gizenshya on 2009-12-27
At the moment, I think the two highest possibilities are the RAM or the graphics card.

Do you have onboard video with your computer?  If so, you can try using that, and removing your card.  Then just wait and see what happens.

But the RAM is most probably it I think.  Do you have any known good RAM that is compatible with your computer that you can swap into it for a while?

How many sticks of RAM is in the computer?  Could you remove one stick and run it long enough to see if it's stable, then swap with another?

---

### Post by mick222 on 2009-12-27
will try swapping ram with another computer let you know what happens

---

### Post by drdanielfc on 2009-12-27
A friend of mine had a similar problem. Turned out the system was overheating....there was a sticker on the fan. Try checking your system temperature ([http://www.bradtrupp.com/ubuntu-cpu-temperature.html](http://www.bradtrupp.com/ubuntu-cpu-temperature.html)). Not sure what good temperatures would be but I'm sure overheating would be fairly obvious temperature-wise

---

### Post by mick222 on 2009-12-28
> A friend of mine had a similar problem. Turned out the system was overheating....there was a sticker on the fan. Try checking your system temperature ([http://www.bradtrupp.com/ubuntu-cpu-temperature.html](http://www.bradtrupp.com/ubuntu-cpu-temperature.html)). Not sure what good temperatures would be but I'm sure overheating would be fairly obvious temperature-wise
Already tried that i get a m\board temp of round 30oc and 50oc for my cpu isthat about right.I think it's my memory tried to run memtest from startup only completed about 77% also tried another stick of memory from an old computer but think that is faulty too.

---

### Post by drdanielfc on 2009-12-28
If this was the case than doing something very memory intensive would cause the system to crash (the system was trying to write to a bad RAM sector, etc). I have no idea how you would test this so just kinda putting my 2 cents in...

---

### Post by mick222 on 2010-01-04
I have went through everything an noticed that when using flash or watching videos my cpu temp goes up to 71 oC Must have unseated cpu when i was messing about with computer will reseat it and hope that fixes it.Otherwise it's a new computer.

---

### Post by mick222 on 2010-01-07
Solved my psu was the problem the fan had stopped working thanks everybody

---

