---
title: "black screen on startup"
date: 2010-11-30
forum: General Help
---

### Post by sevenfactorial on 2010-11-30
Hello,

Recently my laptop running Ubuntu 10.10 has had an abrupt power shutoff (actually several times -- my battery has some problems).

Now when Ubuntu boots, I get the startup screen, but after a few seconds, the screen goes black.  I can still boot from the live CD and in fact I am using my computer from the CD to write this post.

A few more details:  When I press the power button while my computer is in this "blank" state, I get hard drive activity.  Also, if I press "power", and then "enter", the machine actually shuts down.  

Any help is greatly appreciated.

H.

---

### Post by BlueSpecial on 2010-11-30
I'm new to Linux and I had the same problem.

I solved it by doing this:

- At boot press "e" repeatedly until you get to the GRUB edit screen.
- Once you are there add the following commands after "quiet splash": acpi=off noapic nolapic
- Ctrl-X to restart

See if it works! It worked for me.

Regards.

---

### Post by sevenfactorial on 2010-11-30
Thank you!

  For now it seems like it has mysteriously corrected itself!  I booted and got the blank screen three or so times in a row, but after booting from the live CD I now get only normal bootups.


H.

---

### Post by fally777 on 2010-11-30
That fixed the black screen for me too but disabled my wireless.

Any suggestion?

---

