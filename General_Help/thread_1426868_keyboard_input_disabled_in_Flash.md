---
title: "keyboard input disabled in Flash"
date: 2010-03-10
forum: General Help
---

### Post by Jioruji Derako on 2010-03-10
Apologies if this is in the wrong section, or if it's been posted recently.

The issue I've been having is with Flash on websites; most notably, Livestream's Flash-based browser viewer, and Adult Swim's flash-based games. Clicking works perfectly fine, but the keyboard input is entirely disabled for the Flash area. Text boxes, or game controls, won't respond at all, even when everything else is still working.
The only way to input any text into Flash-based text boxes is to write it somewhere else (Firefox's URL or Search bar, or in GEDIT), then copy+paste into the tect box (again, Ctrl+V won't work, only right-clicking and pasting will go through).

I've tried multiple versions of the Adobe Flash player, including the installer directly from Adobe's site, the adobe-flashplugin package in Synaptic, the flashplugin-installer package, and I believe I tried GNASH as well (although I'm not sure if that did anything).

I'm quite sure this worked a couple of months ago, so I'm pretty sure the fault here is with either a Flash or Firefox update. I haven't had a chance to attempt to downgrade either one yet, however, nor have I been able to test another browser.

I've seen a few other issues of this sort pop up here before, but they've all either gotten no solutions, or they're a year or two old, or they're running into 64-bit-specific issues. Hopefully this is posted in the correct location, and fingers crossed someone has an answer (or better yet, a solution).

Geo - a.k.a. Jioruji Derako

---

### Post by Toru Ranryu on 2010-03-22
Are you by any chance using SCIM or some other type of input method for non-standard languages? I had the same problem that you describe, and I solved it by starting firefox from the terminal with command

env GTK_IM_MODULE=gtk-im-context-simple firefox

which wil run firefox without SCIM. Don't ask me for details, I got the idea from a workaround for a well-known bug in Inkscape which wil crash the program when used together with SCIM.

---

### Post by Desty Nova on 2010-04-09
Thanks man, I had the same problem and disabling scim fixed it. Starting firefox from the terminal however didn't help (I could still trigger scim input on and off). Exiting scim manually on the other hand, did the trick.

---

