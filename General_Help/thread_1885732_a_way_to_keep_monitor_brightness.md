---
title: "a way to keep monitor brightness?"
date: 2011-11-23
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-11-23
ubuntu 11.10- unity, gnome. acer laptop 5734z. normal boot results in no backlight. my fix for it is to "acpi_os= " for boot, and /etc/rc.local -before exit 0:
"setpci -s 00:02.0 F4.B=00"

i have hotkeys set up for "sudo setpci -s 00:02.0 F4.B=00" to get backlight to return after going to suspend, but on quite a few programs (games mostly), running fullscreen causes the backlight to go off again. the hotkey doesnt return it from in game. 

is there a way to make it instead of a hotkey to turn it back on, someway to make it where it STAYS at "setpci -s 00:02.0 F4.B=00" and doesn't dim or go off?

---

