---
title: "Civilization 4 Beyond the Sword in wine with Intel Graphics card"
date: 2009-12-09
forum: General Help
---

### Post by zorkerz on 2009-12-09
Again this is for **INTEL** graphics cards only. There are a few other threads on ubuntuformus for civ with other graphics cards. 

May card is an intel GMA965 x3100 running in a thinkpad x61. I am using wine 1.1.34 on ubuntu 9.10 x86_64.

Civ4 bts runs without crashing or graphical glitches it is, however, extremely slow.

I installed using xp first Civ4 then warlords, then beyond the sword and finally the BTS 3.19 patch witch allows the game to be played without a cd. 

**Tweaking**
In the winecfg graphics tab I set vertex shaders to none and unchecked allow pixel shader.

I installed winetricks  ```
wget http://www.kegel.com/wine/winetricks
```and used it to install msxml3 and d3dx9 ```
sh winetricks msxml3 d3dx9

```I have tested installing corefonts dotnet11 dotnet20 and vcrun2003 but they have not appeared to improve the performance. Also I manually added msxml3r.dll to ~/.wine/windows/system32 and added an override (native, builtin) for it in the libraries tab of winecfg. If there is a way to install msxml3r.dll with winetricks please let me know. I am not convinced adding msxml3r.dll has improved performance either. 

Once you try to start civ once a new file is created in your home directory. I have edited this to disable movies, tech splash and voice. ```
sudo nano '~/My Games/Beyond the Sword/CivilizationIV.ini'
```Find and make the lines look as follows.
&#8728; NoTechSplash = 1
&#8728; NoIntroMovie = 1
&#8728; EnableVoice = 0

My audio is very choppy I have not figured out how to solve this though it is of minor importance to me. 

I have not noticed any graphical glitches the game appears to run perfectly. The **real  problem** is that even with all graphics settings as low as possible the game runs extremely slow. On vista and xp the game runs fine with all settings on high.

If anyone has any suggestions or is able to make the game run better with an intel card I am all ears.

---

### Post by consolation on 2009-12-11
running xubuntu; what works is disabling compositing in the windows manager.  Your FPS will jump a hundred fold.

---

### Post by zorkerz on 2009-12-11
Im still searching online but as of yet I cannot figure out how to disable composting. Does anyone know how and what does composting do?

consolation: Is your advice going to be useful considering I am running Gnome not xfc and that I am not playing an FPS?

---

### Post by mcmittens on 2010-01-23
Hi zorkerz,
I'm having the exact same problems as you with civ4 on intel graphics.
After following what you did, I managed to get civ4 bts to run with no problems other than being rather slow.

Compositing is how the window manager produces effects like transparency, on xfce the window manager handles this itself, on Gnome most of the time it is done with Compiz.

To disable compiz, you should go to preferences->appearance and disable visual effects.
However, this hasn't managed to get civ4 to work quickly for me.

For reference, I'm running wine 1.1.36, ubuntu 9.10 x86, and my card is an Intel Mobile GMA 4500MHD (GM45).

---

