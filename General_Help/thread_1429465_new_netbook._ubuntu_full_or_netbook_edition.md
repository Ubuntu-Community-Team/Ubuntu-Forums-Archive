---
title: "new netbook. ubuntu full or netbook edition?"
date: 2010-03-14
forum: General Help
---

### Post by marshall31415 on 2010-03-14
Hi,

I've just unwrapped my new netbook. Its got the new Atom N450 processor and the first thing I want to do is get XP home off of it. I'm just wondering if I should install 9.10 full or download the "netbook edition". Whats the difference? Will I see better performance with the netbook or full edition? (just asking because I'd like to avoid the ~650mb download if I can)

Thanks

---

### Post by Tikkyca on 2010-03-14
Netbook edition is better for netbooks.

---

### Post by iflema on 2010-03-14
Ubuntu netbook remix (UNR) would be the better choice.

There is almost no difference, apart from a few things to make it work better on a small screen i.e. different menu and window managment....

Go with the UNR.

---

### Post by mikewhatever on 2010-03-14
> **marshall31415 said:**
> Hi,

I've just unwrapped my new netbook. Its got the new Atom N450 processor and the first thing I want to do is get XP home off of it. I'm just wondering if I should install 9.10 full or download the "netbook edition". Whats the difference? Will I see better performance with the netbook or full edition? (just asking because I'd like to avoid the ~650mb download if I can)

Thanks

You can most certainly avoid downloading. Just install the regular edition, and then install the ubuntu-netbook-remix metapackage. That said, if the screen resolution is higher then 1024x600, you need not bother. UNR gets you no performance boost, just a bunch of graphical optimizations to compensate for a smaller screen.

---

### Post by snowpine on 2010-03-14
Hi Marshall, I'd recommend reading

1. [Ubuntu system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")
2. [Supported netbook models]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")
3. Use the Search feature (top right of your screen) to read the experiences of other users with the same model netbook. 

This will help prepare you for any bugs/tweaks/etc. for your netbook.

Ubuntu and Netbook Remix are the same operating system with very different user interfaces. I recommend trying both in "live" mode to see which you prefer, prior to installing. Performance will vary based on your hardware. Good luck! :)

---

### Post by M1ke on 2010-03-14
I'm running Ubuntu 9.10 full on a 9" netbook and the screen size hasn't given me any trouble. UNR's a great idea and I like the look of the interface, but you're by no means at a disadvantage using the standard desktop. If they're the same OS "under the hood" so to speak, I guess it just comes down to which look you prefer.

---

### Post by andersvinther on 2010-03-16
If you go with the alternate version of the installer for the full version you get the option to set up encryption on your disk.

Given that netbooks go just about everywhere I prioritize this...

It means I can store sensitive information on my netbook and not worry about losing it... well, at least not worry about anyone getting to my data that is :D

I don't think that option is available for the UNR version... but I think it should be...

Cheers,

Anders

---

### Post by flipper9 on 2010-03-16
I use the full Ubuntu version as I didn't like the netbook interface.  The only downside is that you need to make a few modifications to the desktop and applications to maximize the amount of vertical real-estate available...

1. Remove the bottom Gnome toolbar.
2. Activate Compiz
3. Install Ubuntu Tweak (search via google)
4. Open Ubuntu Tweak and goto the compiz section and set the bottom-right-hand corner to "show windows", and the bottom-left-hand corner to "show workspaces".  
5. Install the compizconfig settings manager
6. Goto the compizconfig settings manager, general section, and set the number of desktops to be 2x2 or 3x3.  This will give you a lot more space to work with.
7. Install the gnome toolbar "window-picker-applet" from the repos.
8. Remove the firefox and other icons in the gnome toolbar, and the ubuntu/gnome menu that shows the ubuntu icon/places/system menu.
9. Add the single-icon ubuntu/gnome "main menu".
10. Add the window-picker-applet.  This will move the titlebar of windows into the gnome top bar, giving you more vertical space.  Goto the compizconfig settings manager, goto the Window Decoration icon, and change "decoration windows" to "!state=maxvert".  This will hide the titlebar of maximized windows, so that they show in the window-picker.
11. In various applications, such as firefox, hide unnecessary toolbars.
12. I also set the DPI of my fonts to something smaller than 96 (found in the appearance settings of your system)

This is what I do on my netbook, and I have plenty of space to work with.  I still wish I had a bigger screen, but that's the sacrifice of having a netbook in such a small form factor.

---

### Post by wojox on 2010-03-16
UNR is Ubuntu full with more packages.

---

