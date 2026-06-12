---
title: "Bottom 1/4 of screen (mostly) not displaying"
date: 2010-11-28
forum: General Help
---

### Post by mikmalot on 2010-11-28
Ubuntu was refusing to open any of my folders, so I restarted it. When it booted up, the bottom 1/4th of the screen was mostly missing. It still shows my bottom panel, as well as my dock, but neither my background nor my web browser show up. What did I do? And more importantly, how do I fix it?

---

### Post by akand074 on 2010-11-28
That is the weirdest thing. Never heard of such a thing happening before. I would go to System > Administration > NVidia XServer Settings (or ATI Catalyst) depending on your graphics card and check the display settings.. Or turning off then turning back on your proprietary drivers and restarting. Assuming you already have them installed. (Install them by going to System > Administration > Additional Drivers). 

Otherwise I have no clue, a peculiar problem.

---

### Post by mikmalot on 2010-11-28
When I go to NVIDIA X Server settings, I get an error message reading "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server".

And I have no drivers installed in "Additional Drivers".

---

### Post by mikmalot on 2010-11-29
Okay, so I ended up just doing a fresh install, and that solved the problem. Any ideas what I can do to avoid this happening again? Should I try and figure out how to install and use the NVIDIA X driver?

---

### Post by akand074 on 2010-11-29
You can go to System > Administration > Additional Drivers (though usually after a fresh install it automatically comes up in the notification area). You can install proprietary drivers. They are necessary for 3D and 2D Acceleration. If you install that you NVidia X Server settings should install correctly with it. I'm glad its fixed up now, the good thing about Ubuntu is the fact that doing a clean install is very easy and quick.

---

