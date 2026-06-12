---
title: "Bug in Terminal Profile Settings?"
date: 2010-05-04
forum: General Help
---

### Post by DellNote on 2010-05-04
Hello,

I'm running a new, updated installation of Lucid on an x86_64 box.  I think there's a bug in the Terminal app:

Go to Accessories/Terminal.  When it's open:

Go to Edit/Profiles.../Default.  
Click on Edit
Check the settings for the default profile.  I changed the font size and color scheme.  I have the color scheme set to "Black on white".  

When I change Background to "solid color", I get a transparent background.  When I set Background to "Transparent background" I get the solid color.

Is it just me or can someone confirm this behavior?

TIA

---

### Post by dcstar on 2010-05-05
> **DellNote said:**
> Hello,

I'm running a new, updated installation of Lucid on an x86_64 box.  I think there's a bug in the Terminal app:
.......

Is it just me or can someone confirm this behavior?


Mine works as it should now, but I do recall when I first installed 10.04 beta it did behave strangely in a manner that you have described - I put it down to it using old gconf settings from my /home partition that I used in my 9.04 system.

---

### Post by TheAlien on 2010-05-07
I've got the same problem with my freshly installed 10.04. The terminal has been transparent ever since install and after I activated the official Nvidia display drivers with visual effects set to extra.

It looked kind of cool to begin with, but when i noticed that it was a bug, it wasn't that cool anymore. :P

A temporary fix is to tick the background image option, and not choosing any image, just tick the option. Then the background will get a solid color.

---

