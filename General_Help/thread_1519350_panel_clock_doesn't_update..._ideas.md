---
title: "panel clock doesn't update... ideas?"
date: 2010-06-28
forum: General Help
---

### Post by windfix on 2010-06-28
The clock applet "Clock 2.30.0" in my panel reads correctly on boot, and then never updates itself. When I go to its preferences, time setting is correct and continuously updating, but the display in my panel never changes.  I can use "killall-gnomepanel" from terminal, and this rests everything, making the time display correctly.  Furthermore, it updates itself afterward... but I'd like the dang thing to function correctly without resorting to that.

Anyone have an idea?

(running 10.04 64-bit)

---

### Post by dino99 on 2010-06-28
try into a console:

metacity --replace

ntpdate need to be installed (look into synaptic)

---

### Post by windfix on 2010-06-28
Thanks, Dino99.  I did a reinstall on ntpdate and ran "metacity --replace"; one of those seemed to do the trick.  The metacity command gave a few errors about blanks being assigned to workspaces 1 through 4 in keybindings, but happy with the results.

---

### Post by dino99 on 2010-06-28
im glad for you :p, you can find usefull errors logged into xsession-errors and /var/log/ (system admin logviewer) to keep a stable system on.

---

### Post by windfix on 2010-06-28
Dangit, rebooted this morning, and the problem is back.  My panel shows 8:27AM and it's an hour past that...  The applet itslef, when expanded, has the correct time - but in the panel, it's the time I booted up.  Grrrr.  Any more ideas?

---

### Post by windfix on 2010-06-28
logged into xsession-errors and /var/log/ (system admin logviewer) ??

Sorry, Dino99, I don't know what this means.  Tried xsession and xsession-errors from terminal, but nada.  Pokedn into /var/log but there's a lot there and I didn't know what I was looking for.

---

### Post by windfix on 2010-08-14
bump...

This problem left me alone for quite a while, but is now back again.

killall gnome-panel starts it working again, but until I do that the clock applet stays stuck on the time from bootup

---

### Post by windfix on 2010-10-13
I was hoping a Maverick upgrade would fix this.  It did not

---

