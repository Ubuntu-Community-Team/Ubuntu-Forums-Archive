---
title: "Natty: Windows Not Opening Completely"
date: 2011-05-03
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-05-03
Hello,

I am having the following problem, and it has been persisent over several distros.

Often, when presented with a nautilus window, and asked to drill-down to select a file, the window will not completely open, leaving the *'Open'* and *'Cancel'* buttons invisible below the lower gnome-panel.  I will then have to click the maximize button, to get the window to fill the screen and make the *'Open'* and *'Cancel'* buttons visible.   This also seems to happen with some of my apps...:confused:  

For instance, I never have this problem with Firefox, but I always seem to have it with Ubuntu-Tweak, and some other apps.  This 'appears' to be happening randomly, although it could be related to *'inode-meta-data'* about the window state not getting updated.

This is about as far as I can extrapolate.


Can anyone shed some light on this?




Thanks, Hannibal

---

### Post by naikaustubh on 2011-05-06
I have had exactly same issue and this has been happening ever since I installed Compiz Configuration Settings Manager package to enable desktop effects. 
Now the problem persists even after removing the package, though as you said Firefox works fine.

---

### Post by naikaustubh on 2011-05-07
I switched back to GNOME and now everything looks normal. I would suggest that to you too, if you are not a big fan of the left-panel!

---

### Post by coljohnhannibalsmith on 2011-05-11
I tried the following in CCSM (Compiz Config Settings Manager) and this seems to have solved the problem, although I'm not exactly sure why:

CCSM > Window Management:

Window Rules (checked)

Place Windows (checked)

Extra WM Actions (checked)



Hannibal

---

