---
title: "Changing screen resolution during boot up?"
date: 2009-10-02
forum: General Help
---

### Post by tonybruce on 2009-10-02
So, I very cleverly changed the resolution on my desktop and now the it's all staticey lines across the screen.  There anyway to change the resolution during bootup or any other options?

---

### Post by XDevHald on 2009-10-02
Hey tonybruce,

Welcome to Ubuntu Forums. Are you running the latest development of Karmic 9.10 or a different version? As an option just for a quick fix, you can load into the login screen (if you can) and click on the bottom left or right where it shows "Options" and select a different session.

From there you will choose the X Session so you can place this command in terminal to edit your xorg.conf: **sudo gedit /etc/X11/xorg.conf** - The file will load, you will see a section that shows the below:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Virtual	1600	1200
		Depth	24

```

Notice: Virtual 1600x1200 - You will want to edit this to the display that you want it to be so. I.E 1280x960, or 1024x768 etc. Let us know if you have any other questions or this does not work.

---

