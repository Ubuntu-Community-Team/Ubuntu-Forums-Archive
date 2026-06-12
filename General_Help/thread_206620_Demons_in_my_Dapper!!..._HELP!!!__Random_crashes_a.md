---
title: "Demons in my Dapper!!... HELP!!!  Random crashes and weird stuff"
date: 2006-06-30
forum: General Help
---

### Post by Dr. Feelgood on 2006-06-30
Ever since I upgraded to Dapper some really weird crap has started to happen.  The most annoying is that my programs crash randomly for no reason.  I could just be sitting there and not clicking anything and they just go down.  In fact I'm retyping this post because my god damned browser closed on me the first time around.  So far Firefox, Frostwire, and Diablo 2 (under wine) have done this to me.  The only other program that I use frequently that hasn't randomly crashed (knock on wood) is Evolution.  But that's only the beginning...

For some reason, when I start my computer up, the little icons on the top and bottom bars are getting randomly moved around!  My trash icon ends up on the other side of the desktop switcher, my volume control ends up in the middle of the bar,  all kinds of weird stuff, and usually not the same place,  and for no apparant reason.  I mean.... I can see how crashes might happen....but random icon rearragement????

And finally, my sound issues, there is already a thread for this but I might as well mention it since it might be related.  Sound works whenver it damn well pleases in some programs.  Specifically Diablo 2 and FCE Ultra.  It's like a crap shoot.  System sounds and totem always work fine though.  Here's the thread if you want to take a stab at it [http://www.ubuntuforums.org/showthread.php?t=206204](http://www.ubuntuforums.org/showthread.php?t=206204)

I guess that's it for now.  Sorry for the long post but this is driving me nuts!!!

---

### Post by Dr. Feelgood on 2006-07-08
anyone??

---

### Post by PriceChild on 2006-07-08
Maybe an EXTREMELY long shot... but when i ran windows, i once had a dodgy mouse cable which made the cursor head randomly all around the screen and click every so often.

Maybe this is happenning to you? Might as well try a different mouse if no-one else has a saner opinion.

---

### Post by Dr. Feelgood on 2006-07-08
I use my laptop trackpad.

---

### Post by jlacroix on 2006-07-09
I *just* recovered from this problem. To try to fix it, I reinstalled Kubuntu, but it didn't fix anything. Then, I ran a memtest86 (at the Grub boot menu at the very beginning) and found out one of my sticks of RAM was bad. I replaced it, and I am good to go now. You should do a memtest.

---

### Post by Dr. Feelgood on 2006-07-10
I did the memtest and it did find some errors... but after I let it run for 24 hours it still wasn't sone running tests!!  How long did it take you?  I just ran the default tests.  But now here's my question:  Nothing ever crashed randomly on Breezy....why start in Dapper if my memory had a problem all along?  Does the OS use the memory that much differently?  Also I'm having trouble actually interpreting the results of the scan.  Any help with what everything means?

---

### Post by Christmas on 2006-07-10
After I reboot or log out and log in I have the same problem problem with icons, but only on the desktop. I don't know what can be the cause though. Maybe it's better to do a clean install, as most of the people around here recommend installing a fresh copy instead of upgrading.

---

### Post by jlacroix on 2006-07-11
I don't think the tests actually ever "finish". If you find errors that's all you need to know. You should remove all of your RAM, add it back stick by stick, running memtest each time, to find out which one is bad.

---

### Post by ZagiFlyer on 2006-07-11
FWIW Whenever I encounter seriously weird stuff that defies logic or troubleshooting, it almost always comes down to power (a failing power supply, or "dirty" power) or memory.

If I were in your shoes, I would do as suggested previously in the thread and rigorously check the RAM. It sounds odd, but it's concievable (although I would be awefully surprised if this were indeed the case) that caching algorythm changes in the kernel could make the problem occur in Dapper when it didn't in Breezy. That is, Breezy never tried to write "important" data to the bad memory. I'm serious -- I've had this happen to me. If you have spare memory, or another system _with known good_ memory you can scavenge temperarily, you could try swapping memory out.

If that didn't show anything, I'd start looking at power. I had a computer several years ago that had a power supply that was slowly failing. That, coupled with AC that was not the sine it was supposed te be, caused very bizarre issues.

Of course again, maybe it's just demons. Or Gremlins. If it turns out to be Gremlins, remember that they don't like water or bright lights :-D .

---

### Post by Dr. Feelgood on 2006-07-12
Thanks guys.  I have a laptop so do you think it may be a problem with the battery/AC power?  I always run with the AC power connected (original supply that came with laptop) since the battery only holds a few minutes of charge.  I'll see what I can check out.  I'll see about the memeory issue first though since the memtest did put out an error.  I'll find which one is defective and give you and update on my progress.

---

### Post by Dr. Feelgood on 2006-09-09
Well, after months of trying to figure out what the hell went wrong I decided to backup my computer and try a fresh install of Dapper (I had upgraded the first time from Breezy).  Problem solved.  It was the damn upgrade.  For some reason it caused a bunch of problems which the fresh install did not.  If anyone else is having this weird stuff happen try this first before buying any new parts.

---

