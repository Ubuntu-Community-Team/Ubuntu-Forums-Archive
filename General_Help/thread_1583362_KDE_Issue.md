---
title: "KDE Issue"
date: 2010-09-27
forum: General Help
---

### Post by javarunner on 2010-09-27
I just changed my ide to KDE. Now when I boot the box I cannot get a desktop from which I can return to my previous desktop.
How can I return to my original standard Ubuntu desktop?

---

### Post by q1_dab on 2010-09-27
> **javarunner said:**
> I just changed my ide to KDE. Now when I boot the box I cannot get a desktop from which I can return to my previous desktop.
How can I return to my original standard Ubuntu desktop?

A desktop from which you can return to your previous desktop? I can't work out what you mean by that, If you can get to TTY then edit .xinitrc accordingly to start gnome-session or whatever it is for gnome, instead of having it start KDE.

---

### Post by Finalfantasykid on 2010-09-27
If you simply want to use Gnome again, then you can log out, and then there is a drop down when you can select which session you want to use.

If you want to remove kubuntu as if it never existed, then you can check this out...

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by javarunner on 2010-09-27
The issue is this: When it boots into KDE all I get is a Black Screen and no means of changing options to get Gnome.  There is a menu popup that appears just before the 'black' screen but it seems to have no purpose.  So I cannot edit any file to enable Gnome one more.

---

### Post by q1_dab on 2010-09-27
> **javarunner said:**
> The issue is this: When it boots into KDE all I get is a Black Screen and no means of changing options to get Gnome.  There is a menu popup that appears just before the 'black' screen but it seems to have no purpose.  So I cannot edit any file to enable Gnome one more.

Can you access TTY?

---

### Post by javarunner on 2010-09-28
No I can access nothing.  The monitor is black and does not show any icons, menus etc.  So, I cannot get to anything, unless someone knows of a keyboard trick that'll do it.
Thanks.

---

### Post by Finalfantasykid on 2010-09-28
CTRL + ALT + F1

This should open up a TTY.  If you understand terminal commands you should be able to figure out where to go from here.  You probably need to start gdm manually for some reason.

Or if you can't even get a TTY going, then there is definitly something bad going on.  If that is the case, you could try booting into recovery mode.

---

