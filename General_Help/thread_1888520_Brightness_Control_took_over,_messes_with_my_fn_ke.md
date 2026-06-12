---
title: "Brightness Control took over, messes with my fn keys, can't identify it"
date: 2011-11-29
forum: General Help
---

### Post by inmatarian on 2011-11-29
This morning when I turned on my Laptop, this app took over my backlight brightness keys:

[IMG]http://i.imgur.com/mT3aw.png[/IMG]

Up until last night, I had no OSD indicator of brightness. The previous control gave me very fine increments (by like 5% I'd guess). Now, this control only allows 20% increments.

The only recent changes to my system was a hardware upgrade yesterday (ram) and a new kernel install (linux-generic-pae as my install in 32-bit and I'm waiting for 12.04 before my next reinstall). However, these happened yesterday morning, and my system went through more than several reboots throughout the day and nothing changed.

My question is, what app is this meter? My suspicions say its lightdm. Also, how do I get back the old control (which I have no idea what the old one was), or how do I fix the increment/decrement amount? And if anyone knows, why did this change on it's own?

System: Thinkpad L512 laptop, Xubuntu 11.10 (fresh install last month, 32bit).

Edit: The problem persisted between power cycling my laptop. Then I cycled the numlock a few times, and the problem disappeared (I got back my original behavior, and the OSD isn't showing anymore).

I was tipped off by this bug report: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=627336](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=627336)

Very strange.

---

