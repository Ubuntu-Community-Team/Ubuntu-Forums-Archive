---
title: "Firefox fullscreen problem"
date: 2011-05-31
forum: General Help
---

### Post by SamDesign on 2011-05-31
Hi everyone,

I am working on a gym class display screen which was built by others. It is operated under Ubuntu. Everytime I click on Firefox, the page goes to fullscreen, but the problem is that the gym class display is not zoomed to full screen (which is what we need). there are black blank parts on both the right and the bottom of the screen.

There is no shortcut key working under firefox either, which means I can't zoom the screen or even enter url for any websites.

I checked the gym class website on my computer, everything looks perfect. I think there must be some setting wrong on the operating machine. I am new to this, so any suggestions would be appreciated.

Can someone please let me know how to fix this wrong screen size problem?

Thank you.
Sam :)

---

### Post by jerrrys on 2011-05-31
heres a place to start

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=adjust+screen+resolution&as_qdr=all&sa=Google+Search&lang=en#851](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=adjust+screen+resolution&as_qdr=all&sa=Google+Search&lang=en#851)

---

### Post by prshah on 2011-05-31
> **SamDesign said:**
> 
I am working on a gym class display screen which was built by others. 

Can someone please let me know how to fix this wrong screen size problem?


It may have a wrong virtual screen size setting. If it was installed before, and then upgraded, then this is likely. If it is a fresh installation, I don't think this will be the problem.

To check, please post back the contents of the /etc/X11/Xorg.conf file (if it exists). Case is important.

Some more information about the hardware(eg, graphics card, screen type) will be helpful.

---

### Post by SamDesign on 2011-05-31
Thanks everyone, this has been fixed. Just in case anyone else had same problem, this is how to fix it. It is Firefox add on - Rkiosk which stopped the firefox to quit from the full screen mode. To turn it off, just do alt+f2, and run firefox in safe mode - firefox -sfe-mode, run. After zoom the screen to the right size, we put the add on back again. All working now. Thanks for your replies.

---

