---
title: "Setting resolution/refresh rate for bootscreen?"
date: 2006-05-28
forum: General Help
---

### Post by DDM on 2006-05-28
I recently bought a new LCD monitor, and during startup, up until X starts I get a d-sub error from the monitor's OSD, and part of the screen is cut off. This is only a minor annoyance, that is, until I have to use the CLI without X, and the command line is cut off so that I can't read what I'm typing. Is there a way to fix this? I don't really care what resolution it runs at so long as I can actually read what I'm typing.

TIA

---

### Post by glotz on 2006-05-28
I'm a linux newbie, so take my advice with a pinch of salt.

I think that the screen resos during the boot menu are controlled by the kernel switches in /boot/grub/menu.lst.

One switch was vga=normal and others were something like vga=791 and I think there was vga=ask but I don't know what that'll do... I don't know if messing with those parameters can be dangerous...

---

### Post by DDM on 2006-05-28
That's a little better, but still kinda funky. Is there a way to force a refresh rate?

---

### Post by Trullo on 2006-05-28
.

---

