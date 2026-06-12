---
title: "HP nx6325 - black screen on returning to gnome session from other terminals"
date: 2010-01-09
forum: General Help
---

### Post by CallumFR on 2010-01-09
Hi there.  I wasn't sure if this was the right bit of the forum to post this in :)

I've used linux on and off for a few years now, mainly dual booting along with XP.  Recently though XP caused a lot of trouble, I was getting BSODs every few mins and I decided it was the time to use Ubuntu as my primary OS.

In XP, when I put my laptop onto the docking station I have, the screen sometimes went black.  Computer became completely unresponsive, I had no choice but to hold the power button.  Back when I was using Ubuntu 9.04, I don't recall ever having this problem, however, with 9.10 I've been having this problem quite frequently.  The only work around I have found is locking my session before I put the laptop down, and then once I've put it in the docking station, pressing the little switch beneath the screen several times.  This work around is temperamental at best.  Another way that seems to sometimes work is to change to another terminal using ctrl + alt + f1, f2 etc.

This brings me onto my next issue.  If I was to switch to a new terminal right now, and then try and return to this one using ctrl + alt + f7, I would end up with this same black screen and system which doesn't respond.

The only setting I have modified on my system recently is adding "rmmod snd-hda-intel" to /etc/init.d/halt to fix an issue with unclean shutdowns. The above issues were still present before I made this change, but now it seems there's a higher chance of them happening.

I'm not really sure if you need any specs from my computer, or outputs from commands to try and see what's going wrong, but if you can help me I'd be happy to try and get you the required information.

Thanks :)

---

