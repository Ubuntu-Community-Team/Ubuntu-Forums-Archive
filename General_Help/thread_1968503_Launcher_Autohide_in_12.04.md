---
title: "Launcher Autohide in 12.04"
date: 2012-04-29
forum: General Help
---

### Post by guyver_dio on 2012-04-29
Just installed 12.04 LTS. Upgrade from 11.10 didn't work for me (upgrades have never worked for me yet), so I decided to do a fresh install. While trying to set it up the way I had it in 11.10, I saw they added the autohide into the appearance section. I thought cool saves me from having to install something like myunity etc... Turned on the autohide and it hid, almost all the time when I hover on the left edge of the screen it won't show the launcher, I have to take a run up with my mouse to get it to show lol. I saw the sensitivity setting and put it on the highest it can go, still is very unresponsive when I go to reveal the launcher. 

I used to use this feature in a customization tool called smart auto-hide, I thought myunity had it but I just installed it and it doesn't seem to be there. Anyone know of the tool that had smart auto-hide?

---

### Post by VinDSL on 2012-04-29
> **guyver_dio said:**
>  Anyone know of the tool that had smart auto-hide?
REAL WINDOW DODGE UNITY LAUNCHER BAHAVIOUR FOR UBUNTU 12.04

LINKAGE:[http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html](http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html)

---

### Post by nothingspecial on 2012-04-29
*Thread moved to **General Help**.*

---

### Post by jfernyhough on 2012-04-29
It was a design decision. The launcher now has only two options: shown, or auto-hide. There's no dodge mode any more.

As to why you're having difficulty getting the launcher to show, I had to alter my settings in CompizConfig Settings Manager (CCSM) to get it working nicely to my preferences. (Screenshot attached).

---

### Post by guyver_dio on 2012-04-29
> **VinDSL said:**
> REAL WINDOW DODGE UNITY LAUNCHER BAHAVIOUR FOR UBUNTU 12.04

LINKAGE:[http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html](http://www.webupd8.org/2012/04/real-window-dodge-unity-launcher.html)

Thanks, it's a little bit laggy but it's closer to what I like anyway. 

thank jfernyhough for the ccsm method, seems like alot of parameters just for a simple autohide function though lol.

---

### Post by mc4man on 2012-04-29
Atm this requires building unity yourself, there likely will be ppa at some point with packages.

This will restore the prior dodge & dodge active options that were removed.
Tested here & works fine along with the additionally described 'click on icon to minimize'

[http://ubuntuforums.org/showthread.php?t=1967822](http://ubuntuforums.org/showthread.php?t=1967822)

Edit: ppa now up with packages

---

### Post by guestolo on 2012-04-29
I didn't like the autohide on Desktop at first, used to it now
But like [jfernyhough]("http://ubuntuforums.org/member.php?u=143103"), I changed setting in CCSM
The only setting I changed however was
"Launcher Reveal Pressure" 

Dropped it from default 20 to 7 seems to work a treat

---

### Post by wa1d0rf on 2012-08-22
I have the same issue sometimes, and I logout then login again and the auto-hide is restored to the way I have it set.

---

