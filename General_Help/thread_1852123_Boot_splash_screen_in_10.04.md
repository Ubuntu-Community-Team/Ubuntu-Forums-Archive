---
title: "Boot splash screen in 10.04?"
date: 2011-09-29
forum: General Help
---

### Post by mac666 on 2011-09-29
Hey
After grub in ubuntu 10.04 i dont get any fancy boot screen.
It only shows "login to tty0" for a couple of sec befor it boots.
How ever i dont know the correct terms for what this is called,

Anybody who would like to give me a hint on how i get a fancy boot screen instead of shell-text?
Thanks

---

### Post by MG&amp;TL on 2011-09-29
Typically a mucked-up plymouth (boot screen) is indicative of hardware issues. What hardware/drivers are you running?

And don't worry about the 'tty' thing, that's just what goes on behind gdm(the login screen)

---

### Post by mac666 on 2011-09-30
yeah, i know the tty thing is nothing to worry about...
What do i need to run to get you the info about drives? :-)

---

### Post by MG&amp;TL on 2011-09-30
Well, consult your computer's manual or BIOS for the hardware, for the drivers:go to system > administration > hardware drivers. 

If you have a graphics card (that's not Intel), or a Broadcom internet adapter, you will need to install one. (It will tell you). If you have already done this, get a screenshot of the screen with the hardware drivers listed.

If you haven't done either, you have more of a problem. ;)

---

