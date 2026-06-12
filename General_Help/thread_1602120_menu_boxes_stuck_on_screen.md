---
title: "menu boxes stuck on screen"
date: 2010-10-21
forum: General Help
---

### Post by deepdivered on 2010-10-21
i have looked all over and seen nothing like this. when i open the ubuntu menu some times the boxes freeze to my screen. how do i fix this?

i attached a screen shot to show whats happening

---

### Post by Blacklemon67 on 2010-10-23
I have the same problem too! I would guess it's a problem with metacity. I ended it's process one time and the stuck stuff went away, but along with it the window decoration :C

I have no idea what's going on, the only way to fix it is to log out and log in again.

Someone help us please D:

---

### Post by Blacklemon67 on 2010-10-24
I've switched to compiz from system -> preferences -> appearance -> visual effects -> normal. With compiz instead of metacity this no longer happens.

---

### Post by Ziga on 2010-11-18
I have same problem, only my visual effects are all grayed out..

---

### Post by war59312 on 2010-12-08
Having this problem too.

New with Ubuntu 10.10. Did NOT have this problem with 10.04.

---

### Post by war59312 on 2011-03-28
Bump.

Really annoying!

Any thoughts anyone? Fixed in 11.04 by chance?

This is on a server with ati es1000 graphics, which looks like there is no real working driver for still today. :(

> ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc ES1000 (rev 02)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

---

### Post by rowanparker on 2011-03-30
Did nobody find a fix other than 'using compiz' (which isn't an option till they sort full screen flash)?

---

### Post by natomasboy on 2011-04-22
I have this problem too.  I noticed it in Ubuntu 10.10.

I have a Dell optiplex 760 with a MSI R4350 (ATI 4350) video card running dual monitors.  I too have to login/logout to get rid of this annoying problem.

any help would be appreciated!

right-click context menus are stuck like ghost images that won't go away.

---

### Post by natomasboy on 2011-04-22
Problem also in Windows 7 but turning off/on the monitor doesn't help:

[http://www.techsupportforum.com/forums/f10/solved-menu-selection-gets-stuck-on-screen-256096.html](http://www.techsupportforum.com/forums/f10/solved-menu-selection-gets-stuck-on-screen-256096.html)

---

### Post by natomasboy on 2011-04-22
Hmm... changing Visual Effects to 'Normal' appears to have made the images go away.  The screen flickers for a few moments and when the question 'Do you want to keep this configuration' appears the ghost images are gone.

---

### Post by 14quartz on 2011-07-11
Compiz is only the solution...once installed the menu is not stucking again.....:)

---

### Post by clonedone on 2013-04-05
I use LXDE and don't want Compiz.. I prefer the speed.. I just want to know why sometimes I get a rectangle stuck on the screen.. the mouse moves over it, but anything else is "behind" it, and therefore non-visible. (See a piece of an email below, stuck on the screen.. )

[IMG]http://i.imgur.com/bydVK3l.png[/IMG]

Bloody weird..  Also, I have 100+ tabs open, I don't want to log-out! Gah. (system hasn't started paging yet, so I don't think its run out of memory)

---

### Post by clonedone on 2013-04-05
Seems related: My desktop icons had disappeared too.. 

Logged out and back in, worked fine. I tried switching to a VTY, but it did nothing but blank out the boxes to grey..

---

### Post by oldos2er on 2013-04-05
Old thread closed, please start a new thread.

---

