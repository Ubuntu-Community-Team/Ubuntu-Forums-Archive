---
title: "Problems turning off compiz in jaunty"
date: 2009-09-12
forum: General Help
---

### Post by KyleRaynor on 2009-09-12
I know 9.10 is soon to be released. But this is annoying, and I just now have noticed it happening.
I have had the default "Extra" special effects turned on for some time. But now that I'm trying to switch to Ubuntu for good, and not have to go back to Gates for games, I have to use wine, and it doesn't play nicely with compiz(or vice versa).

Whenever I try to turn off the "Visual Effects" through the appearance window, it befuddles my screen(see attached pic). [EDIT: I'm running gnome-do with the docky theme, and that was causing this problem, but I like Do and have found a way to keep it]

I have searched, but can't find anything like this happening. Any ideas?[EDIT: Still searching, still can't find anything similar]

---

### Post by KyleRaynor on 2009-09-14
[UPDATE::SOLVED]
Thanks for nothing guys, I fixed it myself.
I figured out that it's Gnome-Do using the docky theme. It requires a compositing wm.
For anyone else that has this problem, since NO ONE seems willing to help with it. You can easily create a 'Custom Application Launcher' with a command of 'compiz --replace' or 'metacity --replace' respectively. and tell gnome-do to autohide, and as long as it's hidden it won't screw up your desktop when using metacity. That way you can play wine/gl games and still have a neato desktop with special effects.

again, for all those that saw my post and decided not to help, or not to even look, THANKS FOR NOTHING.

---

### Post by drs305 on 2009-09-14
Install fusion-icon. You can put it on a panel. One click and you are in compiz. Right click, and you can select an option to return to another window manager.

It doesn't solve your overall problem but at least makes switching easier.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

