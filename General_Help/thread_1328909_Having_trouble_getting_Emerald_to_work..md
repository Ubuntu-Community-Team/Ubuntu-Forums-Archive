---
title: "Having trouble getting Emerald to work."
date: 2009-11-16
forum: General Help
---

### Post by GetOutOfBox on 2009-11-16
Hi, I'm sort of new to ubuntu (I've tried on and off before), I do understand essential concepts (sudo, apt-get,etc, know my way around), but I'm having trouble getting Emerald Theme Manager to work. I installed Compiz Fusion, and I appear to have properly installed Emerald, but the weird thing is, the new themes sort of worked at first (limited effect, only the window bar was changed instead of the whole theme), but after 1 reboot, it stopped working.

I'm almost definetly sure its just me missing some step in the install proccess, as my computers new, I did get the latest (proprietry) ati linux drivers, etc.

Here's some info:

Ubuntu 9.10 Karmic
Radeon 4850
latest compiz/emerald

Any help would be appreciated, and don't worry about having trouble explaining things, I pick up computer related stuff pretty fast, and I have played around with various linux distros, so I'm familiar with the essential concepts/commands.

---

### Post by RedSingularity on 2009-11-16
In a terminal try

emerald --replace & exit

see if your themes are applying then.

---

### Post by GetOutOfBox on 2009-11-16
> **RedSingularity said:**
> In a terminal try

emerald --replace & exit

see if your themes are applying then.

Ok, that seems to have worked! 2 more things:

1. Is there anyway to configure Ubuntu to execute that command automatically at startup?

2. Are emerald themes supposed to change the taskbar? Can emerald customise the taskbar, or is there another program that does that.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
System>Preferences>Startup Applications  You can add the command there. The task bar is customizable via right clicking it and choosing properties.

---

### Post by GetOutOfBox on 2009-11-17
I have one more question, how do I get the 3D-Cube desktop working. I installed and cinfigured compiz, but I can't figure out how to access the 3d cube. Is there a shortcut I need to know?

---

### Post by RedSingularity on 2009-11-17
Did you install the settings manager?

sudo apt-get install compizconfig-settings-manager

Then look in System>Prefs for the program.

---

### Post by GetOutOfBox on 2009-11-18
Oops, it turned out it was installed correctly, my keyboard wasn't though, the ctrl,alt keys weren't working. Reset to US standard, and it worked!

Just for anyone else having similar trouble finding out how to pull up the desktop cube, the shortcut is ctrl+alt+click and drag mouse

I'm just saying that because it took me forever to find that shortcut.

---

### Post by darco on 2009-11-18
The emerald --replace command should actually be placed in CCSM under Window Decoration. You will see a field named command, add it there. The other way works too....


darco

---

