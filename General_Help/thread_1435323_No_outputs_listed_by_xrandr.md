---
title: "No outputs listed by xrandr"
date: 2010-03-21
forum: General Help
---

### Post by ignisuti on 2010-03-21
I'm trying to use [this thread]("http://ubuntuforums.org/showthread.php?t=1112186") to set my laptop's resolution to 640x480. To do this, I need to use the addmode command which expects me to list an OUTPUT. What OUTPUT do I list? The "xrandr -q" command doesn't list any outputs.

Here is the result of me typing "xrandr -q":
```

Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  

```

---

### Post by Sin@Sin-Sacrifice on 2010-03-21
That is the output... and according to it the min is 800x600.

---

### Post by geirha on 2010-03-21
Seems the output is called "default" in your case.

---

### Post by ignisuti on 2010-03-21
> **Sin@Sin-Sacrifice said:**
> That is the output... and according to it the min is 800x600.

I'm new to this, but I thought I could force it to whatever I wanted. My goal is to use a really old laptop as a portable DVD player for my kids. The movies play too slowly at the higher resolutions, but I think they'll play just fine at 640x480.

---

### Post by ignisuti on 2010-03-21
> **geirha said:**
> Seems the output is called "default" in your case.

Okay, default seemed to work for letting me add the mode. However, nothing changes when I try to use the new mode. Any thoughts?

---

### Post by Johnny B on 2010-03-21
what video drivers are you using?
i wrote a script to change my screen resolution and single/dual monitor mode, i tried using xrandr but it didn't work. im using the nvidia drivers installed by envy-ng with nvidia-settings. i got the solution when i found [Disper]("http://willem.engen.nl/projects/disper/")

---

