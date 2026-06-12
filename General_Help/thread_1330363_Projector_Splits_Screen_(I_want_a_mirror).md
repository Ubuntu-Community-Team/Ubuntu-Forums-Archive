---
title: "Projector Splits Screen (I want a mirror)"
date: 2009-11-18
forum: General Help
---

### Post by MiddleRiver on 2009-11-18
I am using a Lenovo Thinkpad tablet PC x61 with Ubuntu 9.10.  When I connect my projector my screen automatically splits and the "theme" changes.  Example: My firefox headers turn blue, icons change, and I cannot switch between screens using the workspace.  I want to mirror my screen with the projector so what I see is what they see.  Any help would be appreciated.

---

### Post by scouser73 on 2009-11-18
What make is your graphics card?

---

### Post by realzippy on 2009-11-18
...he should have an Intel GMA X3100 chip.Native resolution is 1024x768.
Cannot foresee his beamer's resolution,..if it would be the same,and vga,he could try (terminal):

**xrandr --output LVDS --mode 1024x768 --output VGA --mode 1024x768 --same-as LVDS**

---

