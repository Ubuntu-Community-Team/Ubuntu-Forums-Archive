---
title: "Unity dash and launcher disappeared"
date: 2011-07-18
forum: General Help
---

### Post by amitst on 2011-07-18
I am using Ubuntu 11.04. My Unity start button and launcher disappeared after I installed compiz-settings-manager and unchecked all boxes to disable compiz. So now whenever I reboot and login, I only see the plain desktop background (no laucher bar to the left, no top bar). Any tips for getting the original (default Ubuntu settings) back and then to disable effects?

Some background:
I started facing issues while launching a game in full screen mode. So I wanted to switch off the desktop effects (I remember that in earlier versions of Ubuntu I could turn off desktop effects and the game would run properly).

---

### Post by kptsuresh on 2011-07-18
Go to System > Administration > Login Screen...

unlock it and check which login screen was selected ...and select "ubuntu" if any other selected..

---

### Post by srisharan on 2011-07-18
you might have disabled the unity plugin in ccsm.Log into ubuntu classic mode and  enable unity plugin in ccsm .With out that you cant have unity

---

### Post by amitst on 2011-07-18
Is there any terminal command to open this window? I am not seeing any menus...

---

### Post by amitst on 2011-07-18
> **srisharan said:**
> you might have disabled the unity plugin in ccsm.Log into unity classic mode and  enable unity plugin in ccsm .With out that you can have unity

How to login to the classic mode? At login screen I see only a menu to shutdown/reboot etc and another dialog with check boxes mostly related to accessibility options (like high contrast etc...).

---

### Post by srisharan on 2011-07-18
when you select your user at the bottom it says ubuntu.Change that to ubuntu classic and you can login to classic gnome desktop

---

### Post by amitst on 2011-07-18
I enabled the unity plugin in ccsm through unity classic mode. However after logging back to regular unity I still don see the launcher/dash.

---

### Post by srisharan on 2011-07-18
There are 2 plugins for unity.Did you enable the one called ubuntu unity plugin or unity handles one??

---

### Post by garvinrick4 on 2011-07-18
> **amitst said:**
> I enabled the unity plugin in ccsm through unity classic mode. However after logging back to regular unity I still don see the launcher/dash.
try:
```
gconftool-2 --recursive-unset /apps/compiz
``````
unity --reset
```> I am using Ubuntu 11.04. My Unity start button and launcher disappeared  after I installed compiz-settings-manager and unchecked all boxes to  disable compiz. So now whenever I reboot and login, I only see the plain  desktop background (no laucher bar to the left, no top bar). Any tips  for getting the original (default Ubuntu settings) back and then to  disable effects?
Gnome with Unity interface runs on Compiz. Disable it, disable your interface.

---

### Post by amitst on 2011-07-18
Thanks all. The above two commands solved the issue. Setting both unity handles and plug-in didn't solve it.

After running the commands through terminal the resolution was temporary (the terminal stated showing the unity debug output). When I pressed Ctrl-C in the terminal, Unity crashed again and all tool bars disappeared. However, after restart everything came back up fine.

---

### Post by jwilson1484 on 2011-10-23
I had the same exact problem. I couldnt see any icons or the dash not even the clock on the toolbar above. So I tried the two above commands and restarted all it did was reset font size to default. So I just ran a search through Computer/file system for CCSM and opened up Config manager that way and ran unity and resolved the conflicts. Reset everything back to normal and it all came back.

---

### Post by pite on 2011-11-08
Had the same issue too, but the above solutions weren't enough.
What did it for me was setting the GConf backend in the compizconfig settings manager -> settings. It got somehow switched to flat-file.

---

### Post by sairam2000 on 2011-11-16
i had the same issue. no top panel and no unity launcher. Keeping in mind about some other issues, i opted for erase and new installation. Installation and my own selection of softwares ran for hours together. Finally when i came to compiz config manager installation, suddenly unity launcher and top panel disappeared. (same problem.) I saw this thread and checked the CCsm options and found that unity plugin option was not selected. i selected it and everything returned to normal. Oh!

CCSM should have a confirmation messsage when this kind of options are selected/deselected.

---

