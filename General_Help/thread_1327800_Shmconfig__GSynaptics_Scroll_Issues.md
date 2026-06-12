---
title: "Shmconfig / GSynaptics Scroll Issues"
date: 2009-11-15
forum: General Help
---

### Post by sliPrix on 2009-11-15
I'm running 9.10, and having some problems getting the vertical/horizontal scrolls working with my Synaptics touchpad.  I've added the Shmconfig.fdi file with the recommended contents as posted [here]("https://help.ubuntu.com/community/SynapticsTouchpad").  I've tried removing the file, re-adding it, etc. with no luck at all.  When I try to start Gsynaptics or any other program that requires Shmconfig to be running I get an error message similar to the following:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

It appears to me that the Shmconfig.fdi file isn't being processed on boot  Any suggestions or troubleshooting ideas are greatly appreciated; thanks!

(If it helps, I'm running a Lenovo X300 Thinkpad).

---

### Post by mikewhatever on 2009-11-15
Doesn't Karmic have a nice GUI under Preferences->Mouse to manage these settings? The howto you followed is for older releases, and, evidently, doesn't work with the new one.

---

### Post by sliPrix on 2009-11-16
Karmic does have a mouse interface under preferences, however it doesn't have anything for the touchpad specifically.

---

### Post by mikewhatever on 2009-11-17
What about the third tab titled Touchpad?

---

