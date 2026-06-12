---
title: "Nvidia driver activated but not in use, help!!"
date: 2011-08-03
forum: General Help
---

### Post by mussussu on 2011-08-03
Hi, I am new to linux, I installed the latest ubuntu version, 11 something, and went to system settings, additional drivers, it shows two drivers: Nvidia accelerated graphics driver (version 173) and Nvidia accelerated graphics driver (version current) [recommended], I pressed the recommended one and click activate, it prompted me to restart the computer, I did, and I notice that the graphics were really nice, but when I go back to the same place, it says that the driver is activated but not in use, if I choose the other driver, and activated, I restart the computer, and it will say the same thing, that the driver is activated but not in use, the only reason I want this to work is because I think that this is the reason I cannot get the special effects tab in preferences. please somebody tell me if there is anything I can do to fix it. 

THANKS

---

### Post by flipper T on 2011-08-03
this is a well known issue

it is a false message and can be ignored

the driver is activated, so ignore

ps try pressing the windows key and start typing "nvidia" in the search box...your nvidia x server settings gui should appear

---

### Post by coffeecat on 2011-08-03
> **mussussu said:**
> I think that this is the reason I cannot get the special effects tab in preferences.

The special effects tab has been removed in 11.04 - that's why you can't get it!

If you are able to log into the Unity desktop then you are getting effects. Unity is an effect in that it is a compiz plugin. If you want to play with special effects like wobbly windows, install the package compizconfig-settings-manager. But take care with ccsm - some effects are not compatible with Unity. If ccsm says it wants to disable something to enable something you've chosen, stop and search the forum before proceeding. 

Yes, I agree with flipper T - the activated but not in use message is a known bug.

---

### Post by wildmanne39 on 2011-08-03
Hi, if you do want to change effects and possible set up the cube with compiz here is a guide with pictures for every step.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

