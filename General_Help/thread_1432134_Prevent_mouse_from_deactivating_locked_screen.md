---
title: "Prevent mouse from deactivating locked screen"
date: 2010-03-17
forum: General Help
---

### Post by chewearn on 2010-03-17
I recently installed Karmic Koala (desktop edition) on an old PC.  Most of the time, the PC is expected to be running in locked screen (i.e. blank screensaver), unless I need to fiddle with something.

However, I keep hitting the mouse accidentally.

Therefore, I would like to prevent the mouse from deactivating the locked screen and presenting the unlocking dialog.  I.e. only direct keyboard press should invoke this action.

Any idea?

---

### Post by bobcollard on 2010-03-17
> **chewearn said:**
> I recently installed Karmic Koala (desktop edition) on an old PC.  Most of the time, the PC is expected to be running in locked screen (i.e. blank screensaver), unless I need to fiddle with something.

However, I keep hitting the mouse accidentally.

Therefore, I would like to prevent the mouse from deactivating the locked screen and presenting the unlocking dialog.  I.e. only direct keyboard press should invoke this action.

Any idea?
Unplug your mouse?  As long as it is part of the system it will be active.

---

### Post by rnerwein on 2010-03-17
hi
i haven't tried it but what do you think about a little script wich looks like
modprobe -r your_mousmodule
screensaver
insmod your_mousemodule

ciao   :-)

---

### Post by chewearn on 2010-03-17
> **bobcollard said:**
> Unplug your mouse?  As long as it is part of the system it will be active.

That sounds like a possible fix, but the mouse is PS/2, not exactly plug'n play (it an old PC with old peripherals ;)).  There is a slight risk of damaging the port if I unplug too many times while it's powered.

---

### Post by chewearn on 2010-03-17
> **rnerwein said:**
> hi
i haven't tried it but what do you think about a little script wich looks like
modprobe -r your_mousmodule
screensaver
insmod your_mousemodule

ciao   :-)

Thanks for the suggestion.

Thinking more about it, I happened to have a wireless mouse with a  manual on/off switch on the bottom.  Looks like a direct hardware change is the most straight forward fix.

---

