---
title: "Performance issue with open source radeon driver with X1650"
date: 2010-05-28
forum: General Help
---

### Post by Tlem on 2010-05-28
As the title says I have a performance issue using the open source radeon driver.  I normally would just attribute this to the driver still not ready, but it was working fine on the Mandriva install I just wiped out.  I replaced madriva in order to have Qimo sessions for my daughter to use.  When I try to run glxgears the gears basically don't move.  Any help would be appreciated.

---

### Post by clhsharky on 2010-05-29
Tlem

How about some info, what release?

```
glxinfo | grep OpenGL
```

My info
```
glxinfo | grep OpenGL
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on RV530
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20

```
Kernel 2.6.34
I have a ATI1650 on Ubuntu 10.04 and have no problems with graphics. OSS drivers work very well with this card.

glxgears
```
8480 frames in 5.0 seconds = 1695.802 FPS
8481 frames in 5.0 seconds = 1696.162 FPS
8486 frames in 5.0 seconds = 1697.026 FPS
8500 frames in 5.0 seconds = 1699.820 FPS
8583 frames in 5.0 seconds = 1716.459 FPS
8507 frames in 5.0 seconds = 1701.382 FPS

```

```
GtkPerf 0.40 - Starting testing: Sat May 29 00:32:59 2010

GtkEntry - time:  0.03
GtkComboBox - time:  1.56
GtkComboBoxEntry - time:  0.90
GtkSpinButton - time:  0.26
GtkProgressBar - time:  0.44
GtkToggleButton - time:  0.37
GtkCheckButton - time:  0.12
GtkRadioButton - time:  0.18
GtkTextView - Add text - time:  0.67
GtkTextView - Scroll - time:  0.30
GtkDrawingArea - Lines - time:  1.00
GtkDrawingArea - Circles - time:  1.27
GtkDrawingArea - Text - time:  0.99
GtkDrawingArea - Pixbufs - time:  0.16
 --- 
Total time:  8.26
```

Gtk is faster with UMS but KMS is now getting all the love.


Sharky

---

### Post by Tlem on 2010-05-29
I am using 10.04.  I installed using the Qimo 2.0 cd, but as far as I know that is just Xubuntu 10.04 with qimo-session installed.  

glxinfo | grep OpenGL 

OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RV530 71C7) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string: 1.5 Mesa 7.7.1
OpenGL extensions:

glxgears

115 frames in 6.1 seconds
126 frames in 6.1 seconds
115 frames in 6.1 seconds
116 frames in 6.1 seconds

---

### Post by Tlem on 2010-05-29
It is fixed.  I noticed that clhsharky's info was showing gallium.  I added the xorg-edgers/radeon PPA to my sources, updated, and now everything is working.  Thanks for the help.

---

### Post by woz on 2010-06-13
> **Tlem said:**
> It is fixed.  I noticed that clhsharky's info was showing gallium.  I added the xorg-edgers/radeon PPA to my sources, updated, and now everything is working.  Thanks for the help.

Hi all,

I think this will fix the problem that I am having however, I am not sure how to do the above. Can someone post a step by step of how to do this?

Thank you.

woz

---

