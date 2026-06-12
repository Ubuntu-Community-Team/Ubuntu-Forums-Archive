---
title: "WINE and Windows Games"
date: 2009-12-11
forum: General Help
---

### Post by ikislav on 2009-12-11
Hello...

Ubuntu 9.10 is installed on my system for two months now and it works wonderful. But there is one thing that I miss from Windows and that thing are games made for Windows. There are a few games that I really would like to play (Fallout 1 and 2, Heroes of Might and Magic 3, 4 and 5, Diablo 1 and 2). Can anyone tell me about their experiences with running games through WINE? Like compatibility, performances, etc...

---

### Post by MelDJ on 2009-12-11
try looking them up here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by vanv101 on 2009-12-11
IMO you're better off getting Cedega if you want game support.  WINE is made more for business type apps.  Your next best option is to install virtualbox by SUN and run a virtualized install of windows.  Other wise just dual boot.  I've heard of people downloading WinXP to run iTunes, etc.  For virtualization and playing games you would need some good hardware to keep it from being slow.

---

### Post by MelDJ on 2009-12-11
> **vanv101 said:**
> Your next best option is to install virtualbox by SUN and run a virtualized install of windows.

i disagree.
virtualbox is not a best bet for games as it only supports directx 8.

---

### Post by soulsource on 2009-12-11
From the list you gave, I only run Heroes 4. There's a nasty incompatibility with wine. You need to start the game in windowed mode or it crashes. I made a small script that imports a registry file setting it to windowed everytime before the game starts. As soon as the game is running, you can (and should) set it back to fullscreen. The whole procedure is explained in the wine appdb entry for the game.

---

### Post by vanv101 on 2009-12-11
I agree with your point.  I was just trying to point him towards a something he can use for free.  I've used VMware and Parallels for OSX before, but with linux i try to stay with the free stuff.

---

### Post by soulsource on 2009-12-11
I don't get it why people still recommend cedega. It's just an old wine version from 2002 with very minor changes and a few wrapper scripts.

That's also a good example why free software should be published under (l)gpl or a similar licence. If you use some less restrictive licence (like the wine-people did prior to 2002) someone just takes your code, modifies it a little, charges people money for your work and you get nothing.

---

