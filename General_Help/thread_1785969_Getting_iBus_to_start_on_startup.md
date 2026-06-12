---
title: "Getting iBus to start on startup"
date: 2011-06-19
forum: General Help
---

### Post by whatthefunk on 2011-06-19
Im trying to get iBus daemon to start on boot, but cant seem to do it.  In the Desktop Session Settings window iBus is not listed in the start up programs and there is no option to start in on boot in the iBus preferences window.  How do I tell my computer to start it up when I boot?

---

### Post by kerry_s on 2011-06-19
do you know the command?

if so, in terminal:
lxshortcut -o ~/.config/autostart/ibus.desktop

i'm sure you can figure it out from there.

---

### Post by whatthefunk on 2011-06-19
Got it!  Thanks.

On a side note, how could I get a bash script to run on startup?

---

### Post by kerry_s on 2011-06-19
Same way, just put /path/to/script for the command.

---

### Post by whatthefunk on 2011-06-19
> **kerry_s said:**
> Same way, just put /path/to/script for the command.

Excellent!  Thanks.

---

