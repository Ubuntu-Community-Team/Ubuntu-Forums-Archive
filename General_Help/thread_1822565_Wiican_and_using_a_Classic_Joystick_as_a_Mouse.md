---
title: "Wiican and using a Classic Joystick as a Mouse"
date: 2011-08-10
forum: General Help
---

### Post by Guin on 2011-08-10
Hi,

I've had a GlovePIE setup on windows for a while now, and I'm hoping to create something similar on ubuntu with Wiican.

In GlovePIE, it's possible to script it so that the Classic controller's joystick controls the mouse. It's also possible to fine tune the sensitivity, etc.

I've been fiddling with Wiican for the past half hour or so, and I've had only limited success. I can control the cursor with the joystick to some extent using:

Classic.RStick.X	= ABS_X
Classic.RStick.Y	= ABS_Y

but the Y axis is inverted, the sensitivity is blocky, and when I stop previding input it resets the position to the middle of the screen.
I've tried "REL_X/Y" but that's even worse. It just moves the cursor further and further towards the bottom of the screen.

Is there any documentation or a tutorial on how to do this somewhere? All I can find is a list of key definitions, which is useful, but doesn't really provide any information on how to solve this problem.

Furthermore, I'm not really familiar with the system Wiican uses to map wii controls to button presses, etc. Is it scriptable like GlovePIE? The format seems to imply it might be, but I don't really know where to look for information on how to use it.

Thanks.

---

