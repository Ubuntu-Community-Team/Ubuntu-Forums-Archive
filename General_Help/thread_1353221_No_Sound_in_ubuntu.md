---
title: "No Sound in ubuntu"
date: 2009-12-12
forum: General Help
---

### Post by fercomanche22 on 2009-12-12
Hi I installed ubuntu 9.10 and I had no problems with the sound, but suddenly I stop having sound in my computer not even with earphones. I have Windows also and I have sound there.

Im new in ubuntu so I really dont have a clue what to do to get the sound back.
Thanks

---

### Post by grpphoto on 2009-12-12
This happened to me once when Ubuntu was updated. From the "System" menu, select "Preferences." From that, select "Sound."

In the screen, make sure that the two "Mute" checkboxes are not checked. If they are not, increase the sound levels using the sliders. I set the basic sound level to 100% and the Alert sound level about 1/3 of the way up.

George

---

### Post by fercomanche22 on 2009-12-12
I've check that, and the volume is 100% and the mute option isn't checked.

---

### Post by miniyak on 2009-12-12
does anything seem suspicious in the hardware tab there?

---

### Post by fercomanche22 on 2009-12-12
Well Actually if i go to the hardware tab, I found nothing. It says Choose a device to configure, and below there are no devices.

---

### Post by MattPendley on 2009-12-12
I'm having this same exact problem!  No hardware and all.  I don't know if this has anything to do with it, but on your output tab, does it have a dummy output selected?  Mine does.

---

### Post by fercomanche22 on 2009-12-12
Exactly in the output I have the same thing. But I really dont have any idea of what we should do.

---

### Post by MattPendley on 2009-12-12
Alright, I have a question for you.  I want you to look in System > Administration > System Monitor and take a look at the System tab.  Where it says kernel, does it say 2.6.28, or 2.6.31?  I was reading on another thread where someone had this same problem and they still had 2.6.28 (the kernel used in Ubuntu 9.04) when they should have had 2.6.31 (what's used now in 9.10).  This could potentially cause some problems I guess.  It's what's wrong for me, but I haven't been able to test it out yet cuz I kinda screwed up my boot loader...  I'll see if I can get that fixed and tell if it works or not.

---

### Post by fercomanche22 on 2009-12-12
Well I've checked and my kernel is 2.6.31, then I guess its not the case :(

---

### Post by MattPendley on 2009-12-13
Hey, that really stinks.  I finally got my boot loader up and running smoothly again (turns out, that was actually the source of my problem and now my sound works...).  Take a look at this thread, and see if you can find anything there:

[http://ubuntuforums.org/showthread.php?t=1307491](http://ubuntuforums.org/showthread.php?t=1307491)

It's 9 pages, and apparently there are a lot of different ways to "fix" the problem, so take a look and see if any of them help you out.

---

### Post by miniyak on 2009-12-13
whats your hardware btw? is your sound card on the mobo or through pci? how old?

---

### Post by fercomanche22 on 2009-12-13
Thanks man this really helped.

> **MattPendley said:**
> Hey, that really stinks.  I finally got my boot loader up and running smoothly again (turns out, that was actually the source of my problem and now my sound works...).  Take a look at this thread, and see if you can find anything there:

[http://ubuntuforums.org/showthread.php?t=1307491](http://ubuntuforums.org/showthread.php?t=1307491)

It's 9 pages, and apparently there are a lot of different ways to "fix" the problem, so take a look and see if any of them help you out.

---

