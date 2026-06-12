---
title: "Super Hybrid Engine"
date: 2010-12-05
forum: General Help
---

### Post by Jerry786 on 2010-12-05
Does the hybrid engine work with ubuntu? if so how do i get it to work?

---

### Post by Jerry786 on 2010-12-06
Anyone know?

---

### Post by milosz.galazka on 2010-12-06
Don't bother with fancy names :) and use CPU frequency applet in Gnome. It is the same thing. Then you can choose conservative/performance mode or even stick to one freq.

---

### Post by Jerry786 on 2010-12-06
> **milosz.galazka said:**
> Don't bother with fancy names :) and use CPU frequency applet in Gnome. It is the same thing. Then you can choose conservative/performance mode or even stick to one freq.

Super Hybrid Engine is what it is and im simply calling a spade a spade,, Nothing fancy about it :)

How do i use the frequency applet?

---

### Post by milosz.galazka on 2010-12-07
Just right click on the panel and choose add applet (or something like that).

---

### Post by Jerry786 on 2010-12-07
> **milosz.galazka said:**
> Just right click on the panel and choose add applet (or something like that).

I cannot right click on the panel, nor the taskbar :( 
I can right click in browser etc. Any ideas why this is happening?

---

### Post by philinux on 2010-12-07
> **Jerry786 said:**
> I cannot right click on the panel, nor the taskbar :( 
I can right click in browser etc. Any ideas why this is happening?

It could be related to the the theme you're using. Try reverting to the default theme and try right click on panel.

---

### Post by Jerry786 on 2010-12-07
> **philinux said:**
> It could be related to the the theme you're using. Try reverting to the default theme and try right click on panel.

I cant see a default theme under the settings,  Its set to ambiance [Which i think is the default theme?]

Still no right click Need to hide the taskbar as soon as, its taking way too much screen space

---

### Post by milosz.galazka on 2010-12-08
"Right click in an empty space on your panel and select Add to Panel from the menu that appears. A small window pops open, which displays the panel applets that are installed. Find the one that you want to install in the list, click Add, and then click Close."

Read more: [http://www.brighthub.com/computing/linux/articles/16690.aspx#ixzz17Wmvb1LL](http://www.brighthub.com/computing/linux/articles/16690.aspx#ixzz17Wmvb1LL)

---

### Post by Jerry786 on 2010-12-08
> **milosz.galazka said:**
> "Right click in an empty space on your panel and select Add to Panel from the menu that appears. A small window pops open, which displays the panel applets that are installed. Find the one that you want to install in the list, click Add, and then click Close."

Read more: [http://www.brighthub.com/computing/linux/articles/16690.aspx#ixzz17Wmvb1LL](http://www.brighthub.com/computing/linux/articles/16690.aspx#ixzz17Wmvb1LL)

You dont get it.. i have tried right clicking on the panel, taskbar, and on workspace, but no box appears

---

### Post by milosz.galazka on 2010-12-08
Then maybe [http://ubuntuforums.org/showthread.php?t=802039](http://ubuntuforums.org/showthread.php?t=802039) or [http://askubuntu.com/questions/13140/gnome-panel-and-menu-bar-cant-be-clicked](http://askubuntu.com/questions/13140/gnome-panel-and-menu-bar-cant-be-clicked) will help.

---

### Post by Jerry786 on 2010-12-09
> **milosz.galazka said:**
> Then maybe [http://ubuntuforums.org/showthread.php?t=802039](http://ubuntuforums.org/showthread.php?t=802039) or [http://askubuntu.com/questions/13140/gnome-panel-and-menu-bar-cant-be-clicked](http://askubuntu.com/questions/13140/gnome-panel-and-menu-bar-cant-be-clicked) will help.

Really dont want to be inputting codes. Im sure there must be a safer way

---

### Post by m_duck on 2010-12-09
I think the 'Super Hybrid Engine' does in fact differ from frequency scaling. I'm pretty sure it allows the motherboard of the Eee to undervolt the CPU, saving power. Anyway, there used to be a program called ***eee-control*** which allowed changing the setting of the SHE between *default*, *performance* and *powersave* using a system tray icon. It can also be done by echoing different values straight into /sys, which is outlined on the [Gentoo wiki](http://en.gentoo-wiki.com/wiki/Asus_Eee_PC_901#Super_Hybrid_Engine).

Frequency scaling can then be applied on top of the SHE settings.

---

