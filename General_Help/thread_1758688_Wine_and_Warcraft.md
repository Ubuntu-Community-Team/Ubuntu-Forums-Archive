---
title: "Wine and Warcraft"
date: 2011-05-14
forum: General Help
---

### Post by dontsaysticky on 2011-05-14
I have tried multiple distros and drivers in attempts to run World of Warcraft in Ubuntu.  I am currently using 10.04. I am able to run Warcraft (kindo of) after a fresh install, update and installing Wine (except the display is crap with lots of stuff just appearing black) I am able to log in, authenticate, chose characer and everything until after I install the driver for my ATI graphics card, WoW will not run at all. It starts to act like its going to run, but then it just disappers from the bottom bar and no error message is given. I have read many, MANY threads related to these kinds of issues, but I fear I need more personalized guidance. Thank you in advance for your patience.

HP pavilion a1677c media center
4g ram

(let me know what info i need to provide and where to find it, please)

---

### Post by cwwilson721 on 2011-05-19
A few things first:
[LIST]
[*]What ATi card do you have? Older models are not supported by ATi/AMD anymore. If one of those, you have to use the open-source drivers, and they are a bugger to work in wine/WoW
[*]There is a HOWTO in the wine forum for how to install WoW (Search "howto+wow" in the wine forum)
[*]Run in 'opengl' mode. Really. IF you want it to work.
[*]Install/use wine version 1.2 for now (1.3.20 has a mouse bug)
[*]Run WoW in wine in XP mode (Makes many things, especially sound, work better)
[*]DO NOT INSTALL IE OR VENT IN YOUR WOW/WINE INSTALL!!! (IE will 'bork' the "news feed", and Vent is too much of a pain. Install Mangler, a Linux Vent Client, instead)
[/LIST]

Go to the wine forum here at ubuntuforums.org. They have MANY posts about WoW

---

