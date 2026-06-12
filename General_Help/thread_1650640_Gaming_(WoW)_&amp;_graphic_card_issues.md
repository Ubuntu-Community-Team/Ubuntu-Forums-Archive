---
title: "Gaming (WoW) &amp; graphic card issues"
date: 2010-12-22
forum: General Help
---

### Post by SebK on 2010-12-22
Ok so basically, I installed Ubuntu, updated everything, installed the graphic card drivers...etc. I'm even using the "Extra" appearence settings to make everything look nice/3D/smooth. 

After installing Wine, I was able to open the Wow.exe file to play World of Warcraft. Everything went fine, but after selecting my character, the screen froze and I was stuch on the loading page. Couldn't play the game.

I searched on the internet to find solutions - I managed to find a WowWiki article that said it was necessary for me, since I had an ATI (Radeon 5850) graphic card, to change the xorg.conf file and add a few lines. 

I did, but it didn't change anything. I even re-installed the graphic drivers, and now I have two ATI Catalyst Contrlo Center" icons under System>Preference.

What must I do to be able to play WoW? (and, if possible, get rid of the extra ATI icon thing)

I'm using Ubuntu 10.10, fully updated, installed with Wubi, 64bit.

Also, my current xorg.conf file has these lines:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

---

### Post by 4Orbs on 2010-12-22
I think you are supposed to have two control center icons, one opens the center as "normal user" and the other opens the center as "root".

In order for me to play WoW, I had to add an extra bit of code to the end of the game launch command: -opengl
The original launch command was:
```
env WINEPREFIX="/home/4Orbs/.wine" wine C:\\Program\ Files\\Warcraft\ III\ Reign\ of\ Chaos\ \&\ The\ Frozen\ Throne\\Warcraft\ III.exe
```
And now the launcher command is:
```
env WINEPREFIX="/home/4Orbs/.wine" wine C:\\Program\ Files\\Warcraft\ III\ Reign\ of\ Chaos\ \&\ The\ Frozen\ Throne\\Warcraft\ III.exe -opengl
```

The game now runs flawlessly with my ati hd5770 card and proprietary driver.

EDIT: I missed the part where you were using a wubi install. Don't know if my post will be of any help.

---

### Post by SebK on 2010-12-22
> **4Orbs said:**
> I think you are supposed to have two control center icons, one opens the center as "normal user" and the other opens the center as "root".
Ah yes but I have 4 :/ 

> **4Orbs said:**
> In order for me to play WoW, I had to add an extra bit of code to the end of the game launch command: -opengl
The original launch command was:
```
env WINEPREFIX="/home/4Orbs/.wine" wine C:\\Program\ Files\\Warcraft\ III\ Reign\ of\ Chaos\ \&\ The\ Frozen\ Throne\\Warcraft\ III.exe
```
And now the launcher command is:
```
env WINEPREFIX="/home/4Orbs/.wine" wine C:\\Program\ Files\\Warcraft\ III\ Reign\ of\ Chaos\ \&\ The\ Frozen\ Throne\\Warcraft\ III.exe -opengl
```

The game now runs flawlessly with my ati hd5770 card and proprietary driver.

EDIT: I missed the part where you were using a wubi install. Don't know if my post will be of any help.

Yeah I wasn't really able to do that. What I usually to do play the game is browse through my hard drive and directly open Wow.exe. For some reason, maybe because my Windows is 64bit, Wine doesn't show the Program Files (x86) folder, only the useless Program Files one.

EDIT2: Ok so after posting the first post, I restarted my laptop and Ubuntu wouldn't open afterwards. I logged in with failsafe/graphic thing, and then uninstalled the ATI drivers  in System>Admi>Hardware Drivers. So now instead of 4, I only have 2 ATI icons. Problem is when I open Catalyst now, it says Failed to execute child process...etc. So I try reinstalling/activating the drivers with Hardware Drivers, it won't work. I need to uninstall the first ATI package I installed - how?

EDIT3: well I managed to uninstall/remove/fix a lot of random things. The 3D effects and everything else is back, but now there are NO catalyst icons at all. The drivers are installed though.

---

