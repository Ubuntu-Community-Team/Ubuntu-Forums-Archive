---
title: "Issues with drawing of Emacs scrollbar and gnome-terminal"
date: 2010-08-21
forum: General Help
---

### Post by dzhu on 2010-08-21
I recently upgraded my system from 9.04 to 9.10 to 10.04, and the following two issues have appeared:
[LIST]
[*] In Emacs, if I run the command redraw-display, the scrollbars on all windows fail to be drawn (there are just white boxes instead). Doing anything that changes a scrollbar restores it (scrolling the window, mousing over).
[*] Minimizing a window when the one behind it is a gnome-terminal causes remnants of the minimize animation to remain in the terminal; the space below the last full line of text doesn't get cleared properly. This is visible in the bottom of the attached image.
[/LIST]

These are minor issues, I guess, but they're kind of annoying. Anyone know how to fix them? (I figure they might be related, hence the combined post.)

The computer is a Compaq CQ60-420US; Linux version is 2.6.32-24.

My graphics card:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
```
I'm not entirely sure how to determine the status of my drivers, but the version of xserver-xorg-video-intel on the system is 2:2.9.1-3ubuntu5.

---

