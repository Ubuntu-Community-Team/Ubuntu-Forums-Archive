---
title: "Blurry Graphics on Low Resolutions"
date: 2010-11-01
forum: General Help
---

### Post by ImTheBatman on 2010-11-01
Hi,  I have recently installed Ubuntu 10.10 on my computer. The default display driver supplied with it only allowed the screen's default resolution (1280x1024), so I downloaded and installed nVidia's latest driver (260). When I change the resolution to anything lower than the default, the graphics (and most notably letters) everywhere appear slightly blurry, becoming more and more blurry as I lower the resolution. The blur is not terrible, I can still use it but it becomes annoying to watch after a while. I am using a GT240 graphics card, and this problem does not exist on Windows using the same resolution and same driver version.  I would be glad if someone can suggest a solution to this problem. Thanks.

---

### Post by ImTheBatman on 2010-11-01
Anyone has an idea how to solve it?

---

### Post by blueridgedog on 2010-11-01
Experiment with lcd subpixel hinting...Preferences -> Appearance -> Fonts then advanced or custom...I can't recall for certain.  Also adjust the DPI.

---

### Post by ImTheBatman on 2010-11-01
> **blueridgedog said:**
> Experiment with lcd subpixel hinting...Preferences -> Appearance -> Fonts then advanced or custom...I can't recall for certain.  Also adjust the DPI.

Hmm... I changed the Rendering and Hinting settings, it seems to affect the fonts in some way but I can't really tell if it fixes the problem entirely. Also, inside programs (like firefox for example) the fonts are still blurred.  EDIT: the DPI settings only seem to affect the size of the fonts, which is okay as it is.

---

### Post by blueridgedog on 2010-11-01
As an alternative (one that is common), set your resolution to the default for your LCD of 1280x1024 (to get clear text), then use the DPI setting to change the size of the items to suit you.

---

