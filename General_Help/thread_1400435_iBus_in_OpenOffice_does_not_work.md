---
title: "iBus in OpenOffice does not work"
date: 2010-02-06
forum: General Help
---

### Post by Kleenux on 2010-02-06
I tried the various tricks (GTK variables...) but I cannot get iBus to get triggered when I'm in OpenOffice Writer.

I want to enter accents easily (like AltGr-'e to get é).

In Ubuntu 9.10, with iBus, it works everywhere but is never triggered on in OpenOffice.

Thanks for your help.

---

### Post by Kleenux on 2010-02-13
**[size="7"]· · · — — — · · ·[/size]**

---

### Post by Kleenux on 2010-02-13
Ok got it to work by **disabling** ibus.

Have 2 keyboard layouts. USA and "USA International with AltGr deadkeys".
Have 2 input methods in iBus, normal and Anthy (Japanese).

Everywhere the keyboard layout is with dead-keys (or normal USA using R-Win). And I can trigger Anthy thanks to the iBus keyboard shortcuts. All works fine...

...except in OpenOffice, where Anthy works, but there is no way to use the "USA with dead keys" layout.

IMO there is a bug,
- bug either in Keyboard layouts, where Apply system-wide may not work (removing USA normal, having only USA with AltGr dead keys)
- or bug in OpenOffice, not able to switch to alternate layouts
- or bug in iBus (don't think so)

---

