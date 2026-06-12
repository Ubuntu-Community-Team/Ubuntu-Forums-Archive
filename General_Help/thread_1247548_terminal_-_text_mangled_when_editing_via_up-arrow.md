---
title: "terminal - text mangled when editing via up-arrow"
date: 2009-08-23
forum: General Help
---

### Post by pickarooney on 2009-08-23
I've had this problem for as long as I can remember but have never tried to fix it until now. It's a little difficult to explain, but I'll try...

I often type/paste long commands into a terminal window (xfce4-terminal currently, but this happened also with KDE terminal and the GNOME one) with bash. Afterwards, to repeat the command for another file or to correct a typo, I use up-arrow to display the command and then use the left/right arrows to navigate to the letter(s) I need to change.

This is where the bad stuff happens. The text suddenly moves about and I'm left with bits of commands broken up by other characters or completely missing. Moreover, there is often a big difference between what I see on the screen before I hit Enter and what is returned in the error message alerting me to the bad syntax. 

In the first screenshot I copied a file to a new location. In the second one I changed the name of the target file and changed **cp** to **ls**. When I hit Enter, the **ls** is actually **cls**.

---

### Post by Brandon Williams on 2009-08-23
This is typically related to changes in screen geometry that somehow got missed by the shell. When it occurs, you can correct the bad behavior with this:
```
kill -WINCH $$
```
This sends the window change signal to the shell so that it will adjust how it displays text.

---

### Post by pickarooney on 2009-08-23
Thanks. I'll give it a shot, but this happ[ens regardless of whether or not I resize the terminal window.

---

