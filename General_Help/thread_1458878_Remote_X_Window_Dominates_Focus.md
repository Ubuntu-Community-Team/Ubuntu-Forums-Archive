---
title: "Remote X Window Dominates Focus"
date: 2010-04-20
forum: General Help
---

### Post by FlakJacket on 2010-04-20
I'm trying to run a software package through SSH from a Silicon Graphics machine.  The program loads fine and has worked in the past.  But with a fresh install of Ubuntu (Kubuntu 10.04 beta 2) all of a sudden the menu system in the window doesn't work.  

These are not native menus, but rather it appears that an X window named Bubble is created.  Upon the click event the cursor style changes and cannot leave the menu button.  

The only option I've found is to hit the power button on my computer which initiates a logout timer.  Once the timer runs out, it appears that the program resumes and the menu starts to open and close. Then the system logs out.

 So I feel like it is a problem of window focus, since no keyboard shortcuts function prior to logout, which can only be initiated from the physical power button, ie. ctrl+c; alt+tab do not switch focus.

Any ideas?

Thanks in advance.
Flak

---

