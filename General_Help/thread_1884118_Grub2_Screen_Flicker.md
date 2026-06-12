---
title: "Grub2 Screen Flicker"
date: 2011-11-20
forum: General Help
---

### Post by brohan76 on 2011-11-20
Hello everyone, thank you for taking the time to look at my questions.  I am running a laptop with dual boot (win & 11.10) In the Grub menu screen, the screen will flicker constantly. Not horribly bad but 1 - 1 flickers a second.  When it flickers it is as if the screen goes to half size horizontally and back to normal. (see double text width wise).  This happens while it was stock, and also when I have added an image. This was also the case in stock resolution, and when I change the resolution of the Grub screen to the acceptable 1400x1050 (image was 640x480 and 1400x1050 @ 900Kb).  Any ideas as to how to remedy this. The screen flickers when I use the arrow keys to select a different OS option, as well as when I touch nothing. Not a huge deal, as I can see everything necessary, and of course I do not sit on the Grub screen for too long.

FWIW I have a Dell Inspiron 6400 with ATI 1400 video card.

Thank you again.

---

### Post by esdi on 2011-12-11
Hello, 

I have a similar issue with grub2 (Oneiric) but with a different video card.
Unfortunately I do not have a solution but here is what I could find.

With grub debug mode active in grub.cfg, I have determined that grub is running fast until it reaches the command
```
terminal_output gfxterm
```and activates the desired resolution.  After the terminal resolution changes, it becomes sluggish and every debug entry takes for ever do display.

With the debug lines removed from grub.cfg, I have tried different supported resolutions as listed with the vbeinfo command.

The resolutions are applied correctly but in any resolution, there are these issues:
-The graphical menu flickers constantly
-Any key pressed (arrows, c for command line, e for edit) takes at least 2 seconds before grub responds.

Before I tried to configure grub to use my custom graphical theme, I had tested it on a virtual machine using Oneiric under kvm.  Everything worked out great so I suspect that it has something to do with how Grub handles my nVidia 8400 GS display adapter.

---

