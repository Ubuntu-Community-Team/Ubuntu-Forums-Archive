---
title: "nvidia-settings vanished after update..."
date: 2010-03-28
forum: General Help
---

### Post by kieran_uk on 2010-03-28
For some reason the nvidia-settings configuration utility entry vanished from the menu after an update, the problem happened again after a recovery via a clonezilla hdd image also after an update, has anyone got any idea's as to recover the entry and how to stop this issue arising in the future?

Regards, Kieran.

---

### Post by pbrane on 2010-03-28
How did you install the nvidia drivers? envyng, repos, dl from nvidia, etc. I take it nvidia-settings is still available from the command line?

I haven't had this issue myself, but more info might help to solve it.

---

### Post by kieran_uk on 2010-03-29
Cheers for the reply.

I installed the drivers through the 'Hardware Drivers' Applet (the applet seems to be broken too saying no drivers installed with a blank window), tried reinstalling via Synaptic Package Manager to no avail.

nVidia-settings still available via the command line/terminal.

Regards, K.

---

### Post by kieran_uk on 2010-03-30
Would resetting the BIOS to the defaults help matters (corrupt CMOS??)?

I'll try starting afresh using a clean clonezilla hdd image to see if that help matters too...

Regards Kieran.

---

### Post by kieran_uk on 2010-04-01
Finally solved, turned pc via the mains for the night the following morning tweaked the BIOS (back to defaults etc etc) and then clean install of 9.10 inc. updates etc - must of been a gfx card/mobo glitch that started the mess! :/

Happy now! :)

---

