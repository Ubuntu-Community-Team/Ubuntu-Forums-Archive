---
title: "Booting Stops at &quot;Checking NVRAM&quot;"
date: 2009-10-01
forum: General Help
---

### Post by Jantaro6 on 2009-10-01
Here's the situation: My laptop randomly crashed while running Ubuntu (I have both Ubuntu and Vista installed). When I restarted it the booting process stopped when it said "Checking NVRAM".

My brother and I have searched this problem on the internet, but despite the large amount of documentation on the problem, nothing has worked so far. We've tried changing the boot settings, holding down or tapping keys (namely ctrl, insert, and F11), to no avail.

Please help! :confused:

Also, I've heard mention about doing something with a cmos jumper cable, but I don't want to dig around in my nice laptop and void the warranty.

---

### Post by Woody1987 on 2009-10-01
This as far as im aware is not an operating system fault. This is a hardware problem, possible bios problem. You could try updating the bios if an update is available otherwise you may have to get it repaired.

---

### Post by Ziphilt on 2009-10-01
(I am the brother he is talking about)

At this point, as we've flashed the bios just to make sure it was not damaged for some reason, I agree that it's most likely hardware. Unfortunately, this is a laptop, where things are cramped and the warranty will break if we open it up. I have read on other forums that it could be a faulty IDE connector that the bios is complaining at. Does anyone at least know a way we could narrow down the problem, for example by disabling certain things? Oh yes, this is AMIBIOS version 0213 on an ASUS G50Vt, if that is relevant in any way.

---

### Post by Woody1987 on 2009-10-01
All i can suggest is that if its still under warranty that you take advantage of it and send it off for repair.

---

### Post by pawhtiobo on 2009-10-01
Hi :)
 
Usually the RAM slot is very accessible, but if the laptop is under warranty i would do it by the book...make use of the warranty :)
 
Do you see the grub menu? if so...did use memtest to check the integrity of the RAM?
 
see ya...

---

### Post by Ziphilt on 2009-10-01
It looks like the warranty ran out a while ago. I suppose we can show it to a computer technician at a Best Buy or Radio Shack and see what they figure it to be, or we could mess around with it ourselves if there is enough information on how and this messing about will be relatively safe.

---

### Post by Giblet5 on 2009-10-01
I'll put odds on it being the CMOS/clock battery.

If you're REAL lucky, it's under warranty.

If you're just lucky, it's one of those button-style lithium batteries (CR2032 is what you see in desktops). Those are usually in a clip/holder.

If you're having a bad day, it's soldered to the motherboard. JameCo or DigiKey will have a replacement.

---

### Post by Ziphilt on 2009-10-01
We can not get to GRUB; this is a BIOS message complaining about something. If we could satisfy the BIOS, we could at least use GRUB to try memtest86. You mentioned the RAM? Do you suggest we try removing it and see if the problem goes away?

---

### Post by cgb on 2009-10-01
If you have 2 RAM sticks in the laptop I would try pulling one out and checking to see if it made any difference.  Then try again by putting it back in and pulling the other out.  If there is only 1 RAM stick then unless you have a spare stick around its a little hard to test.  Dont suppose there is any irregular flashing lights on the laptop that are indicating the problem?  Most newer laptops and Desktops have lights that will flash in patters to indicate Hardware Failures and what possible cause.

---

### Post by Ziphilt on 2009-10-01
Surprisingly, after the top RAM stick was removed, the bios got past the NVRAM thing and Linux boots properly. Does this mean that the top one was faulty? If so, I'm glad that we only need to purchase a small common item rather than replace some big part or have the laptop useless. Thanks for the help, everyone!

---

### Post by cgb on 2009-10-01
Good to hear!  Yes, it sounds like the RAM stick is bad and you should be able to just buy a new one and replace.  The only exception is if the 2nd slot itself is bad but this rarely is the case.

---

### Post by Ziphilt on 2009-10-01
We should be able to test that by shuffling the sticks around, right?

---

### Post by cgb on 2009-10-01
Yes, this would be one way of testing.  Although some motherboards require atleast 1 stick to be in the primary slot but most dont require this.  So worth a shot to try it in the other slot and see what happens.

---

### Post by Ziphilt on 2009-10-06
Magically, the sticks now work in a configuration flipped from their original orientation. Why this works is beyond me, but at least it does work. Thanks again everyone!

---

### Post by pawhtiobo on 2009-10-06
> **Ziphilt said:**
> Does this mean that the top one was faulty?
 
Hi :)
 
I would remove the working stick, and put the "non-working" and do the memtest just to be sure :)
 
see ya...

---

### Post by smc18 on 2009-10-06
> **Ziphilt said:**
> Magically, the sticks now work in a configuration flipped from their original orientation. Why this works is beyond me, but at least it does work. Thanks again everyone!

Reseating components like memory or a video card (on a desktop) is often the fix for problems.  (yay! no money spent)

Due to movement and other mysterious causes, components find a way to come loose; reseating them just resecures their physical connection.

Essentialy, you only reseated your memory modules by moving them to the other slot. If you were to put the RAM modules back into their previous slots they most likely will work.

NOTE: Be careful not to mishandle the RAM sticks. You can damage them by static shock.

Just to be sure, you should run some memory diagnostic test.

---

