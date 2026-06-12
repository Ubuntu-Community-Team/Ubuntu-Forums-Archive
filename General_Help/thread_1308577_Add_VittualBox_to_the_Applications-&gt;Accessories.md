---
title: "Add VittualBox to the Applications-&gt;Accessories panel"
date: 2009-10-31
forum: General Help
---

### Post by edpatterson on 2009-10-31
I thought this would be easy, and maybe it is but I have not been able to do it. 

I would like to be able to start VirtualBox from the panel instead of from a terminal.

Thanks for any help and or pointers to docs.

Ed

---

### Post by happyhamster on 2009-10-31
In case you're using the closed-source version: it stores itself under Applications-->System Tools instead of Applications-->Accessories (as the open-source edition does).

---

### Post by wildweathel on 2009-10-31
Right click one of the menus -> Edit Menus.  Navigate to System Tools, drag VirtualBox to Accessories.

---

### Post by jake1017 on 2009-10-31
1. Right click the panel and select "Custom Application Launcher".
2. Type in the required information.

---

### Post by dj-toonz on 2009-10-31
it all depends on which version you are using , if your using the sun virtual box non-free version over the ose version, you can either right mouse on the panel & add to panel , Application launcher, forward, then system tools, click on virtualbox, then forward & it's in the panel, or an easier way, Applications on the top bar, System tools, & drag with your left mouse virtualbox to the panel, " if it's the OSE (open source Edition) version of virtualbox, it's the same thing but that will be in Accessory's instead of system tools  for both of the ways you can do it

---

### Post by edpatterson on 2009-11-01
> **happyhamster said:**
> In case you're using the closed-source version: it stores itself under Applications-->System Tools instead of Applications-->Accessories (as the open-source edition does).

I am using the closed source version and that is where the docs say it is created, it is not there. The app install successfully and works like a charm. I just want to it to the menu. I really do not care which sub panel it is in.

I am having zero luck using the right mouse button. All I have been able to do is add existing apps to the 'quick launch' area.

---

### Post by happyhamster on 2009-11-01
> **edpatterson said:**
> I am having zero luck using the right mouse button. All I have been able to do is add existing apps to the 'quick launch' area.
I'm not sure what you mean by "quick launch" area. What should work is: right click the main menu and choose "Edit Menus" (or, in a terminal, type: alacarte). In the left pane, select System Tools, and choose New Item to create a new entry.

If that doesn't work, then perhaps there's some permission screw-up? Running alacarte from a terminal might give some feedback in that case.

---

### Post by edpatterson on 2009-11-01
> **happyhamster said:**
> I'm not sure what you mean by "quick launch" area. 
The area directly under the Ubunut icon. Where you can 'one click' icons to launch apps.

[QOUTE]What should work is: right click the main menu and choose "Edit Menus" (or, in a terminal, type: alacarte). In the left pane, select System Tools, and choose New Item to create a new entry.[/QUOTE]
That got me closer. I see the Sun VirtualBox entry and it is checked but not visible. I tried to move it up in the off chance there were too many items. Still no go 

> If that doesn't work, then perhaps there's some permission screw-up? Running alacarte from a terminal might give some feedback in that case.
It is still listed there, Just not visible. Perhaps a Halloween goblin is messing with me :-)

Thanks for the help.
Ed

---

### Post by happyhamster on 2009-11-01
- Weird :) Does it help to reset the panel (don't use sudo on this one):

killall gnome-panel

- Another thing you could try is moving or renaming the files "applications.menu" and "settings.menu" in the .config/menus/ folder in your home folder (press ctrl-h to be able to see hidden files in nautilus). Those files will be rebuild automatically. Afterwards, issue:

killall gnome-panel

- and try editing the menus again:

alacarte


Good luck.

---

### Post by edpatterson on 2009-11-01
> **happyhamster said:**
> 
killall gnome-panel

- and try editing the menus again:

alacarte


Still did not show. I checked the properties all it had was VirtualBox. I changed it to /usr/bin/VirtualBox and it now shows up.

Thanks for all the help!

Ed

---

