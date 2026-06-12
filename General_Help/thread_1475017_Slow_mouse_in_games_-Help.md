---
title: "Slow mouse in games -Help"
date: 2010-05-06
forum: General Help
---

### Post by ZereoX on 2010-05-06
I just bought the Humble Indie Bundle and the moment Aquaria and Gish are open the mouse becomes really slow.

Running Fullscreen, 1440x900, Lucid Lynx (10.04) on a Dell Dimension C521.
(Window or Lower resolutions didn't change anything.)

The mouse settings seem to be like this when I'm playing:

---

### Post by ZereoX on 2010-05-06
Bump!
Sorry for Double-Post.

---

### Post by Dacke on 2010-05-10
I have the same problem in Aquaria. The in-game mouse is extremely slow both in fullscreen and windowed modes.

I am running Lucid 64 on a fairly over-powered computer.

---

### Post by NESFreak on 2010-05-17
Confirmed for aquaria. I believe it's a problem with the sdl library they're shipping. Both setting fbuffer="0" in line 17 in ~/.Aquaria/preferences/usersettings.xml or replacing their version of libsdl with my own appear to fix it for me. (however replacing libsdl introduced other issues and since I'm running 64bit and am not in the mood of setting up a 32bit build environment)

Btw could anyone explain to me exactly what fbuffer does? (apart from fixing the lag?)

Can't wait for them to open up the source and build a 64 bit version.

---

