---
title: "Diablo 2 installation help?"
date: 2010-08-03
forum: General Help
---

### Post by capitalfear on 2010-08-03
is there anyone out there who can provide a step by step installation of Diablo 2 with every detail? im running ubuntu 10.04 its the only real windows game im trying to run on here and my grandma HATES letting me on her computer so yea i just want to know if i can use wine or crossover or something. thanks

---

### Post by LowSky on 2010-08-03
it installs perfectly using WINE

---

### Post by 3Miro on 2010-08-03
I have done this several times, it installs under WINE without any need for special setup and also plays well. I only had to disable compiz to get good graphics because I was using my laptop with a weak integrated video card.

---

### Post by capitalfear on 2010-08-03
really? hmmm maybe i need a different video card. i got into the game itself and then the blizzard in the beginning showed up. and then it just went off

---

### Post by Vaphell on 2010-08-03
run it from terminal, something like 
```
wine ~/.wine/drive_c/Program\ Files/Diablo\ II/Diablo\ II.exe
```
(or whatever path the exe file is located)

and see if there is something interesting in the output after crash. what is your video card?

---

### Post by Zorgoth on 2010-08-04
Possibly direct rendering is disabled - this will occur if you used compiz functionality to run the parent process.

To see if it is enabled, type "glxinfo | grep direct" in a terminal

If it is disabled, try:

unset LIBGL_ALWAYS_INDIRECT
glxinfo | grep direct
- if that works right
wine "blah blah blah Diablo2.exe"

Or perhaps your card/drivers just don't support it.  Try typing "glxinfo | grep -i opengl" (with direct rendering ON).  If the version of OpenGL it says you have is lower than 2.0, wine gaming will be nearly impossible.  You may be able to fix this by getting new drivers, or else you may need a new card (if you are using a desktop).

---

### Post by mastablasta on 2010-08-24
as i know diablo also offers software acceleration.

---

