---
title: "Doom 3 Vsync and anti-aliasing not working."
date: 2009-08-16
forum: General Help
---

### Post by nbtrap on 2009-08-16
I can only get the AA to work if I force it on from the NVidia control panel, but the Vsync doesn't seem to be working either. Lots of screen tearing. Is there any way to force Vsync?

---

### Post by nbtrap on 2009-08-16
I also noticed that I can run the game with maxed AA and anisotropic filtering in windowed mode at a solid 40+ FPS, but when I switch to fullscreen mode, its not even playable. What could be causing this?

---

### Post by bodyharvester on 2009-08-16
computer specs would help

- joe

---

### Post by nbtrap on 2009-08-16
I'm running kubuntu 9.04 on a quad core Gateway 4GB. My GPU is an 8800GT, and I'm running the NVidia 185 drivers. Anything else?

---

### Post by bodyharvester on 2009-08-18
whats your monitors refresh rate?

check the section on Vsync here - [http://www.tweakguides.com/Doom3_6.html](http://www.tweakguides.com/Doom3_6.html)

on anti aliasing it says:
For most people however I recommend setting Antialiasing to Off since it is a major performance drain, and Doom 3 is a game which really doesn't require antialiasing at any resolution - the jaggedness of lines is barely noticeable.

------

 In my experience, setting vsync to "always on" in the ATI and NVIDIA drivers doesn't help. The game's default setting overrides the drivers, no matter what.  To turn on vsync, use the Advanced Options menu.  Alternately, you can hit **ctrl-alt-~** to bring down a game console.  At the console, type "r_swapinterval 1".  Then hit **~** to close the console.  You should be all set, and the tearing should be gone.  You can thank me later. 



got that advice from - [http://techreport.com/discussions.x/7133](http://techreport.com/discussions.x/7133)


hope these sites help, let us know if they do


p.s. cool specs

---

### Post by nbtrap on 2009-08-27
Thanks for the help but this didn't work. That command is no different from turning on Vsync from the options menu--that's exactly what it does.

---

### Post by nbtrap on 2009-09-01
Bump. Anyone have any ideas? I can only get vsync to work now if I force it on from the nvidia control panel.

---

