---
title: "how to get the close button on google chrome to the left side"
date: 2009-12-08
forum: General Help
---

### Post by anilcr on 2009-12-08
well any ideas on this guys?

---

### Post by Shideneyu on 2009-12-09
Hello, i have the same question ? :D
Any answer please?
And by the way, what's the solution to make the bar transparent? 
Thanks :)

---

### Post by ethanmadden on 2010-04-04
I assume you mean putting the Close, Maximize, and Minimize buttons on the left side (mac-style) in which case the only thing that I can suggest is going to tools, options, personal stuff, and then click the "use system titlebar and borders" option.

Unfortunately, this method puts the buttons ABOVE the tabs, which for me sort of defeats the purpose of using chrome. :/

I hope someone finds a better solution. Maybe a way to install the Mac version or something?

---

### Post by nerieru on 2010-05-02
> **ethanmadden said:**
> I assume you mean putting the Close, Maximize, and Minimize buttons on the left side (mac-style) in which case the only thing that I can suggest is going to tools, options, personal stuff, and then click the "use system titlebar and borders" option.

Unfortunately, this method puts the buttons ABOVE the tabs, which for me sort of defeats the purpose of using chrome. :/

I hope someone finds a better solution. Maybe a way to install the Mac version or something?

Well at least this way it's way better, nonetheless there should be a way to get chrome to behave like it should. (following the standards I mean).

At least this way chrome looks much better than with it's default theme :).

Also chrome is about more than just the tabs being above..

I'm gonna file a bug report to the chromium project anyway, so they know about this issue in ubuntu 10.04

---

### Post by logangorence on 2011-01-02
Try messing with the theme options.

---

### Post by Mindswap1 on 2011-01-02
Hey guys! I discovered that if you install Chrome from the website  itself it will be the newest version, and have the close button on the  left side by default. The one in the software center is not up to date.  So install from the website at the following link. 


> [http://www.google.com/chrome](http://www.google.com/chrome)

---

### Post by HermanAB on 2011-01-02
AFAIK those buttons are made by the window manager, not Chrome.  So you need to configure gdm to put them where you want them.

---

### Post by houseworkshy on 2011-01-03
The easy no fuss way to put the buttons back on the pre-10.04 side is to simply change themes via System>System preferences>appearance.  Clear looks is a nice one.

---

### Post by rvchari on 2011-01-03
if you wish mac like buttons always on top left, then one time work is this.
go to terminal > gconf-editor
apps > metacity > general
right side you should find button_layout.
right clik on the key and edit the key to this close,minimize,maximize:menu and then set that as mandatory. all your progs will have button on left irrespective of the these you ve installed.

alternatively a more easier way is to change through ailurus if you have it. if u dont then sudo apt-get install ailurus and that s a cool program to edit many things !!!!

ur button lay out can have gnome / mac or custom button layout.

hope i could solve your doubts

---

