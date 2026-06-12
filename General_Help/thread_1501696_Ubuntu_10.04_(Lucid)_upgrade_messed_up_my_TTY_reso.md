---
title: "Ubuntu 10.04 (Lucid) upgrade messed up my TTY resolution"
date: 2010-06-04
forum: General Help
---

### Post by respinosa1978 on 2010-06-04
Hello everyone.
I seem to have a problem with the recent update from Karmic to Lucid. Despite the ocassional glitches, whenever I click CTRL-ALT-F1 to access the TTY console, the screen is completely garbled, only some lines and colors show up in the top of the screen, the rest of the screen is completely black. If I do CTRL-ALT-F7 I can successfully go back to GDM, but I have not been able to correct this issue with TTYs. I assume it is an issue with grub and the resolution, since I tried changing it and sometimes it shows a split image of the splash itself, with lots of garbled lines and super inferior color quality (640x480x8) and whenever I tried to set the resolution higher, it hasn't worked at all. I have a Dell m6300 with dual core @ 2.8GHz, nVidia Quadro Graphics. Anyone has faced this same issue? I would certainly appreciate any help on how to solve the matter, since it has became a real nuisance. Thanks all.

---

### Post by dcstar on 2010-06-05
> **respinosa1978 said:**
> Hello everyone.
I seem to have a problem with the recent update from Karmic to Lucid. Despite the ocassional glitches, whenever I click CTRL-ALT-F1 to access the TTY console, the screen is completely garbled, only some lines and colors show up in the top of the screen, the rest of the screen is completely black. If I do CTRL-ALT-F7 I can successfully go back to GDM, but I have not been able to correct this issue with TTYs. I assume it is an issue with grub and the resolution, since I tried changing it and sometimes it shows a split image of the splash itself, with lots of garbled lines and super inferior color quality (640x480x8) and whenever I tried to set the resolution higher, it hasn't worked at all. I have a Dell m6300 with dual core @ 2.8GHz, nVidia Quadro Graphics. Anyone has faced this same issue? I would certainly appreciate any help on how to solve the matter, since it has became a real nuisance. Thanks all.

There are already threads on console resolution and the various Grub2 configuration changes you can make to try and fix them.

I solved my problems by installing the new **burg** bootloader as it actually sets these modes correctly (because Grub2 doesn't).

---

### Post by respinosa1978 on 2010-06-27
Well I;ve tried every thread available in this forum and still no luck
What I need is what to put after VGA= in menu.lst
Something that actually works and helps would be appreciated.
Thanks.

> **dcstar said:**
> There are already threads on console resolution and the various Grub2 configuration changes you can make to try and fix them.

I solved my problems by installing the new **burg** bootloader as it actually sets these modes correctly (because Grub2 doesn't).

---

