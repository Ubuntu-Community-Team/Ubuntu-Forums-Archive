---
title: "XGL Login problems"
date: 2006-07-01
forum: General Help
---

### Post by Tylo on 2006-07-01
Here is my problem. When I go switch my session to the XGL session I created following the tutorial found [here at Method A]("https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28XGL%29#head-4ad54c8799ed5fa6843db565fe7e6020daaee145"), the splash screen just goes away, the cursor icon appears to be loading something (as if booting into the desktop), then my monitor power-flickers and I am back at the splash login screen, unsure of which session I am in (but guessing I am back in the GNOME session).

This is what my startxgl.sh looks like:
```
#!/bin/bash
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 gnome-session

```

Also it should be noted that my video card is an ATI Radeon 9600 AIW, and the display driver appears to be working (including 3d support). This is what my **fglrxinfo** says:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

Thank you community,
Tylo

---

