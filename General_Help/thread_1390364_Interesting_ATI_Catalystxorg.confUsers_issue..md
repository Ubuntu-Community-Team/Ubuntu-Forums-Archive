---
title: "Interesting ATI Catalyst/xorg.conf/Users issue."
date: 2010-01-25
forum: General Help
---

### Post by boballen55 on 2010-01-25
This takes a bit of explaining.

So, I have 64-bit Karmic (actually Mint 8 but should be the same for this issue) using Gnome with an HD 4650 Readon card with the newest (9.12) driver/catalyst installed from the ATI website.  I've set up two different kinds of monitors pretty much entirely through using the Catalyst Control Center and surprisingly I can get every thing to run nearly as beautifully as I dreamed possible.  I have them set in "Multi-display desktop" mode, so the desktop is basically one big continuous item and windows can be dragged from one to the next.  Compiz even works (haven't tried the craziest effects) as well as AWN (I even have AWN on one screen and a gnome panel on the other, sadly I can't get awn on both but I think I'll live).

The problem is when I restart/logout-login under my name the screen goes to a cloned mode and messes up one of my screens resolution heights.  Catalyst claims it is not in the cloned mode even though it is... This is easily fixed by opening Catalyst, reseting the resolution on my one screen and clicking apply.  And poof, it fixes the resolution as expected and also it goes back to the Multi-display mode!  And then it just works like a charm until I restart or whatnot.

But if I log in under my wife's name the display comes up as I expect right away!  No messing with anything...

What I've tried: So the only differences I could think of between my wife's user account and mine are what starts up automatically (thinking maybe the Screenlets deamon or AWN could possibly do something at login to mess something up).  So I matched mine to hers and that accomplished nothing... Our accounts both have all the same privileges, we're both admins so the only other difference I can think of is that mine is the original account, but I don't know if that could even mean anything.

I've also tried to see if it changes anything in the xorg.conf file only logging in under my name but it doesn't seem like it...

So does anyone have any ideas on why my name loads incorrectly but my wifes doesn't and what I can do about it?  Or how to begin and under what program should I be attempting to file a bug? Or at the very least where to else to ask these questions?  Thanks!

---

### Post by boballen55 on 2010-01-26
No ideas?

---

