---
title: "Laptop will not boot after upgrade (Blank screen)"
date: 2011-07-06
forum: General Help
---

### Post by vidryn on 2011-07-06
Hi there,

I am very new to Ubuntu and recently upgraded 10.10 to 11.04. After restarting, my laptop will not boot-up (Can't even access the bios) it just stays blank, no flashing cursor.

I am not sure what to do I have tried using a Live CD but still hitting a brick wall. I read on a different forum that this is a hardware issue (This was for a HP laptop)

Anyone have an idea what I could do? 

MAKE: Acer
MODEL: TravelMate 240

---

### Post by drs305 on 2011-07-06
Try these three things. Based on what happens, we may be able to provide some solutions:

The first two possibilities are remote. Normally they would be accompanied by a message, but are very easy to check:

1. Press s. If it can't mount a partition, it's possible the system is waiting for you do press a key. S will skip attempting to mount the partition and allow the system to continue booting.

2. Press c. If the system is doing an fsck check, it can take a long time to complete with no feedback. Pressing 'c' interrupts the check and continues booting.

3. Try holding down the SHIFT key during boot. Does the Grub menu appear?

---

### Post by vidryn on 2011-07-06
Hi drs305,

Thanks for the swift reply, I did try all three but still nothing happens. I don't even get the option to change the boot option because it is just a blank screen from the moment i press the power button, I assumed the screen might be broken so pluged it to one of my external monitors but there's no luck.

Do you think it's worth me taking the drive out and viewing it on a different machine (as an external drive that is). 

Thanks again.

---

### Post by drs305 on 2011-07-06
It sounds like a hardware issue although I am generally skeptical of hardware problems occurring just after some sort of software change...

However, if you are seeing *nothing* on the screen after power is applied that would be my guess. Nothing you did should have affected the BIOS and you should at least see the normal BIOS messages/logos as you power up the machine. If it was a simple Grub 2 problem it would at minimum have left you at a 'grub' or 'grub rescue' prompt or given you an error message.

You could try booting a LiveCD to see if the video is working. And being at a LiveCD Desktop would be the place you'd want to end up to begin troubleshooting if it's not a hardware issue.

You might wait for some further recommendations before disassembling your machine in case someone has a better idea...  ;-)

---

### Post by vidryn on 2011-07-06
Result !!

Well more like me being a an id10t. I had done a ram upgrade just after updating and the module was not secured properly.

Thanks for the advice, could come in handy later or might have helped someone else already.

---

