---
title: "Do I need a graphics driver??Counter-strike 1.6 via wine very slow and bad graphics."
date: 2009-09-06
forum: General Help
---

### Post by rock it on 2009-09-06
Hi, I've installed counter-strike 1.6 and have tried playing it. When It started up it said something about safe graphics or something. It started up but when playing it the graphics were really rubbish and it was running really slow. It ran fine on xp is it needing drivers or is it needing settings edited???

help will be appreciated greatly.

here is my spec and other info:

1.8ghz CPU
256mb RAM
30gb HDD
nVidia Geforce 420 32m Graphics Card

Xubuntu Jaunty Jackalope 9.04
Wine version 1.1.29

screen res: 1024x786

---

### Post by Vince N on 2009-09-06
Did you install the proprietary Nvidia Drivers using the "Hardware Drivers" under System -> Administration?  Without those drivers you may not be getting 3D acceleration which the game might want.

---

### Post by rock it on 2009-09-06
I dont think so I'll try that the next time I have the chance, I'm on a windows computer at the moment. Thanks for your help will keep you up to date.

---

### Post by carlosgs91 on 2009-09-06
.

---

### Post by Vince N on 2009-09-06
> **carlosgs91 said:**
> the problem is that you're emulating a game with Wine and the emulation is not perfect. My advise to you is to make a partition for Windows and install your games there.

**W**ine **I**s **N**ot an **E**mulator

It is an API layer that allows windows based games to run natively in Linux, however no "emulation" takes place.

If the proper drivers are installed and the game is already running fine under WINE then there is no reason it shouldn't work unless the game makes use of the drivers in some unorthodox way that the WINE API layer doesn't support.

I personally would recommend installing the drivers first if you haven't.  Even if the game itself still doesn't work you will find the overall system will run better with the NVidia drivers in most cases.  You'll also be able to access things like 3D Compositing with Compiz and several other features the 2D Open Source drivers do not allow for easily.

If it works for you game, GREAT one less thing tying you to windows.

((EDIT: For grins I checked Wine HQ.  counter-strike 1.6 currently has a "Platinum" rating which means for the most part it should run fine under Wine.))

---

### Post by carlosgs91 on 2009-09-06
.

---

### Post by rock it on 2009-09-06
cant find administration under the system menu, if your using ubuntu it might be different from my xubuntu. would be great if you could help with this, thanks. Thanks for all the help so far.

---

### Post by rock it on 2009-09-07
Ok, so I have installed the driver, but now the screen looks ridiculous and everything is huge and I went to display and the highest res I can get is something like 780x 360 or sumthing like that, Any help???

fixed it but everytime i reboot or boot up the graphic settings return to default????

---

### Post by gradinaruvasile on 2009-09-11
> **rock it said:**
> Hi, I've installed counter-strike 1.6 and have tried playing it. When It started up it said something about safe graphics or something. It started up but when playing it the graphics were really rubbish and it was running really slow. It ran fine on xp is it needing drivers or is it needing settings edited???

help will be appreciated greatly.

here is my spec and other info:

1.8ghz CPU
256mb RAM
30gb HDD
nVidia Geforce 420 32m Graphics Card

Xubuntu Jaunty Jackalope 9.04
Wine version 1.1.29

screen res: 1024x786

Dude install [COLOR="Red"]wine version 1.1.27[/COLOR] and CS will run fine. 

Version 1.1.28 and 29 of wine has a regression bug (i think) that messes up half-life based games, at least CS and DoD (both hl1 and 2 based)

---

### Post by rock it on 2009-09-11
ok cool, ill check tht out thx. i did get the graphics driver but its still pretty slow :(.

---

### Post by mr.suchy on 2009-09-20
Hi,

I don't want write a new topic so I write here. A few days ago I install Wine 1.0.1 from add/remove. Then I install Steam, everything go fine but in game I don't have stable FPS. From 14 to 60 FPS. On XP I have stable 60FPS all the time. In NVIDIA X Server setting I set "High performances" in OPEL GL. What else can I do to run CS faster and better ?:confused: Thanks for help and advance

---

### Post by gradinaruvasile on 2009-09-20
> **mr.suchy said:**
> Hi,

I don't want write a new topic so I write here. A few days ago I install Wine 1.0.1 from add/remove. Then I install Steam, everything go fine but in game I don't have stable FPS. From 14 to 60 FPS. On XP I have stable 60FPS all the time. In NVIDIA X Server setting I set "High performances" in OPEL GL. What else can I do to run CS faster and better ?:confused: Thanks for help and advance

Try what i suggested in [_[COLOR="Red"]post #9[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=7933770&postcount=9")

---

### Post by mr.suchy on 2009-09-21
Ok @gradinaruvasile I check it :P

---

