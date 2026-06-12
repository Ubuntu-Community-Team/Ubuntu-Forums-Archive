---
title: "Display not recognized after install."
date: 2012-01-16
forum: General Help
---

### Post by rock4christ on 2012-01-16
I have a Colby 24 in tv hooked up to my laptop as a monitor replacement. It works fine in the Oneiric Live cd(using it to type this),but once installed, it never detects the Colby. Any idea what changed?

---

### Post by xc3RnbFO8P on 2012-01-16
Can show the output of:
> lspci | grep VGA

---

### Post by rock4christ on 2012-01-16
Got it working by messing with Nvidia settings. Only problem is now on boot I get:


none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 354
CRTC 354: trying mode 1920x1080@50Hz with output at 1366x768@50Hz (pass 0)
CRTC 354: trying mode 1920x1080@50Hz with output at 1366x768@50Hz (pass 1)

before everything works fine

---

