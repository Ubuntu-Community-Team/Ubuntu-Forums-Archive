---
title: "up-arrow key does a print-screen"
date: 2009-10-07
forum: General Help
---

### Post by drbobb on 2009-10-07
Well this started after some recent upgrade of gnome packages, and I must have missed it for a while because I was using KDE for some time. Now I tried to go back to Gnome, and the keyboard breakage is making it impossible.

In fact I have checked with xev that the up-arrow key does not generate the keysym PrintScreen, in fact it doesn't seem to generate keypress/release events at all, but instead emits some odd sequence of events I'n not able to interpret. But the net effect is to summon the screenshot applet. No such thing happens under KDE, where the correct sequence of key events is generated.

---

### Post by drbobb on 2009-10-08
I tried playing around with low-level tools (specifically, xkbcomp), and dumped the keymap active in a KDE session to read it into the xserver when logged into Gnome. This did not fix the issue. (I didn't really expect it to, but since I'm utterly confused about how keyboard handling in X actually works I decided to try anyway).

---

