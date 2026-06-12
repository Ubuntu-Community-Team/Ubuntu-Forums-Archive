---
title: "Firefox running really slowly"
date: 2011-02-25
forum: General Help
---

### Post by PDA1 on 2011-02-25
Firefox is running really slowly for me.  It seems it's accessing the hard drive constantly (as seen through System Monitor).

I'm running 10.04

If I start Thunderbird and Firefox invariably the disk drive light just keeps flashing for minutes and the Firefox screen gets "grayed out" and everything just slows way down.  Often I just throw the power switch to shut the computer off.

Any ideas how to fix this?

---

### Post by dino99 on 2011-02-25
check your driver activation: system admin additional driver

if you have not much ram or poor graphic card, then dont use "special effects" (compiz)

If you have installed firefox addon, check that the issue is not made by one (deactivate one by one to find it)

sudo dpkg-reconfigure firefox

The system manager can tell you which process is using too much ram or power or both (can use htop too)

---

### Post by PDA1 on 2011-02-25
There is no System----Administration----additional driver


Also, I think the problem isn't with FF.....I clicked on Thunderbird and the computer went through it's "take 10 mintues" to do nothing routine.

Also, I got the message;

The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet"

Then it has the Delete of not delete option....

Confused.

---

