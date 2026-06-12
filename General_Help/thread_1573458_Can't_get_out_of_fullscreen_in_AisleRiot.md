---
title: "Can't get out of fullscreen in AisleRiot"
date: 2010-09-12
forum: General Help
---

### Post by DavidS on 2010-09-12
I have found on two computers that in AisleRiot, if you remove the status bar and menu bar, and go to full screen, there is no way back.  Every time the program starts it is full screen, and even if you can get to the "Leave fullscreen" button, it still reverts to full screen almost immediately.

I have tried deleting all the aisleriot folders under .gconf/ but it still behaves in the same way.

How do I get AisleRiot back to sensible behaviour?

David

---

### Post by howefield on 2010-09-14
> **DavidS said:**
> I have found on two computers that in AisleRiot, if you remove the status bar and menu bar, and go to full screen, there is no way back.

Can't reproduce this issue, what version of Ubuntu/AisleRiot are you using ?

---

### Post by DavidS on 2010-09-14
> **howefield said:**
> Can't reproduce this issue, what version of Ubuntu/AisleRiot are you using ?

Ubuntu 9.04 with AisleRiot 2.26.1 on one machine, Ubuntu 9.10 with AisleRiot 2.28.0 on the other.  Both exhibit the same behaviour.

The problem is that the only way into or out of full screen mode seems to be by clicking either on a menu item or a button in the toolbar.  If those elements are not available, there seems to be no way to get out of full screen mode.

The only solution I have found is to use gconf-editor and remove the relevant tick in Apps-AisleRiot.

David

---

### Post by howefield on 2010-09-14
I'm using more recent versions of both, and with or without the menus/tool bar, F11 toggles between window and full screen just fine.

---

### Post by DavidS on 2010-09-14
> **howefield said:**
> I'm using more recent versions of both, and with or without the menus/tool bar, F11 toggles between window and full screen just fine.

That doesn't seem to work in the earlier versions, and updating wouldn't help: the reason I wanted to use fullscreen was because one of my computers is a hand-held PC with a 800x480 screen.  But it also has a small keyboard with function keys f1 to f10 only!

David

---

