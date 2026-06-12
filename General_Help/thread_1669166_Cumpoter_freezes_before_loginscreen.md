---
title: "Cumpoter freezes before loginscreen"
date: 2011-01-17
forum: General Help
---

### Post by JCM_Pico on 2011-01-17
Hi there,
I've experiencing some random freeze of the system, just before the loginscreen.
When I turn on the computer, after the grub menu, computer freeze, it stays there, black with a little white line in the top left of the screen, that doesn't blink.
Any idea?

---

### Post by sandy8925 on 2011-01-17
could be that the os is busy loading.....does your hard disk light shine at this time (well normally it would shine anyway)

---

### Post by JCM_Pico on 2011-01-17
> **sandy8925 said:**
> could be that the os is busy loading.....does your hard disk light shine at this time (well normally it would shine anyway)

Usually when the system is loading the little white line blinks. In this case. it stops blinking and becomes static. The disk light continues blinking normally but the system never loads.

---

### Post by Mark Phelps on 2011-01-18
If this is running Ubuntu 10.10, you may be suffering from the same vague unreliability problem that plagues some of us -- sometimes it boots, sometimes it doesn't.

What tends to work most of the time is to do the following:
1) Hold down the shift key to get a GRUB menu
2) When that appears, select the top-most Recovery Mode option
3) When that finally stops scrolling, select the option to repair broken packages
4) At some point, you'll get a prompt.  Then, enter "startx"

That should get you to a working desktop.  IF it does, shutdown normally.

On the next boot, you should be OK (for a while -- until it does it again).

---

### Post by JCM_Pico on 2011-01-19
I'm under 10.04 :( 
And it stopped doing it for the last 2 days.. I find this situation very weird....

---

