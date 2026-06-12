---
title: "nvidia graphics driver creates blue wavy lines"
date: 2010-04-30
forum: General Help
---

### Post by rkrizan on 2010-04-30
I just did a fresh install of 10.04. My resolution was limited to 800x600, so I installed the recommended nvidia drivers and rebooted. Now I have the resolution I want, but I have blue wavy lines all over.

Is there a way to fix this?

I have attached a picture of my desktop and what its doing.

[IMG]http://www.youecho.com/nvidia-blue.png[/IMG]

---

### Post by physic.dude on 2010-04-30
Wow, thats neat,:-k
I think this might be from the "motion blur" effect in compiz being enabled.
Something like that happened to me but it was tinted red. 

Turn off Motion Blur in CompizConfig

---

### Post by rkrizan on 2010-04-30
Visual effects are disabled.

---

### Post by rkrizan on 2010-04-30
My xorg.conf:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


Any suggestions on where to start?

---

### Post by physic.dude on 2010-05-03
Did you try a different monitor?

---

