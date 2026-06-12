---
title: "Ubuntu keeps freezing"
date: 2010-03-15
forum: General Help
---

### Post by iguanaboy on 2010-03-15
Hello

I have been using the latest Ubuntu without problem for the last 3 months, but since today it has been freezing repeatedly for no clear reason. It generally freezes 5-20 minutes after I reboot. I have not installed anything recently, so I don't think that is the problem. Is this a known problem?

Thanks!

---

### Post by Grenage on 2010-03-15
I'd recommend running memtest (I think that's a boot option these days).  Have you installed anything new?

---

### Post by iguanaboy on 2010-03-15
I ran memtest but it froze at 69% (20 minutes). Ubuntu hasn't recently held on for longer than that so I gave up the memtest plan but... I will retry then.
And no, I haven't installed anything.
Anyway, thanks!

---

### Post by Grenage on 2010-03-15
Hi again,

If it's freezing on memtest then I would be suspecting either:

1) Memory (if you have more than one stick, you can remove one to rule it out).
2) Power Supply.
3) Overheating (unlikely).

---

### Post by wojox on 2010-03-15
When it freezes can you still use the mouse and keyboard? May want to check your log files. Might be X related.

---

### Post by purpleturtle on 2010-03-15
If memtest is hanging, then forget further trying anything in Ubuntu until you have memtest running for 24 hours with no errors.

In a nutshell - if memtest is failing, you've got hardware problems.

As previously suggested, try taking out your memory sticks, and reinsert 1, then try memtest again. If that works for say an hour, try putting the other one in, and test again.   The removal and reinsertion can help if there are connection issues on the contacts.  (Do all the removal insertion the the PC switched off).

If that doesn't help look at updating the firmware of your motherboard.

Good luck :-)

---

### Post by llawwehttam on 2010-03-15
It is definately to do with hardware. 
 
Here are the steps to take:
 
1. Clean the computer to make sure its not overheating. Dust in fans and heatsinks causes this.
 
2. Try different ram. It could be a ram issue.
 
2. If none of those help then your PSU could be dying. It is unlikely as they usually just blow up but if unsure contact your supplier.

---

### Post by cdenley on 2010-03-15
First thing I would check is make sure all the fans are spinning. Based on my experience, if the system freezes like that after running for a while, a failed fan is causing the CPU or power supply to overheat.

---

### Post by iguanaboy on 2010-03-15
first of all, thanks to everyone that answered
I finally completed a memtest; it said there was no problem.
Also, I should have said but I am using a laptop, not a PC.

Anyway, sounds like a hardware problem... I'll try to keep the laptop from overheating then. Since it's 18 months old, I can't send it back, unfortunately.

Ah, last question: I can't suspend/hibernate my laptop ( well I can but it won't wake up), might that be related?

---

