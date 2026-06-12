---
title: "Nvidia-Settings - need to change size and position of screen"
date: 2010-04-20
forum: General Help
---

### Post by Erik765 on 2010-04-20
Hello,
I finally installed a new video driver (195.36.15) and can successfully change my Overscan Compensation now, but it's still altogether too low. If I could simply change the vertical position, I could get it just right (and maybe the horizontal size a litle).

This image should illustrate what I'm talking about. The white area is what's being used, the black area is, well, black area. If I adjust the overscan any bigger, it goes too low too and fills up the screen fine but hangs off the bottom a little.

I didn't see anything at all in nvidia-settings or in system settings to change this, and since (*)ubuntu doesn't use xorg.conf like it used to, I'm not really sure where to go here.

I've also tried every resolution setting in nvidia-settings, and have messed around with stretched, centered, and aspect ration scaled on each. They all pretty much produce the same effect (too low).

Any ideas?

I obviously want to be able to use the size of my monitor I paid for :confused:

[IMG]http://www.eriksplace.com/shared/screen.jpg[/IMG]

---

### Post by P4man on 2010-04-20
This thread may help:
[http://ubuntuforums.org/showthread.php?t=1003099&page=4](http://ubuntuforums.org/showthread.php?t=1003099&page=4)

Especially post 35 on how to make a custom EDID, but you may need to read the entire thread in order to follow. 

Note than xorg.conf by default is blank these days, but you can create a xorg file and put settings there. Its just optional these days, it hasnt been abandoned.

---

