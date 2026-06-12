---
title: "Gnome takes me back to the login screen."
date: 2006-06-02
forum: General Help
---

### Post by astrobit on 2006-06-02
When i try to log into gnome (my default manager) the desktop starts to load
and then suddenly it takes me back to the login screen. ](*,) 

I've been using KDE... and no problems there...

BUT, i discovered that if as soon as gnome starts loading the desktop i click
on the main menu and start moving around, then it doesnt takes me back
to the login screen.... 

whats wrong?? anybody has an idea?

---

### Post by givré on 2006-06-02
Try to log in in a fail safe session, and in the treminal it will give you, just type gnome-session to know what's happens

EDIT: run the failsafe terminal session and not the failsafe gnome session

---

### Post by astrobit on 2006-06-03
Well, in case somebody ever gets the same issue...

here is how i solved it.

It seems there was some issue related with the gnome configuration,
so i deleted my old configuration files in order to let dapper create a new
gnome default configuration file. so all your gnome look preferences will be lost.

just open a terminal and type:

rm -rf ~/.gconf* ~/.gnome*

Have fun! :) 

Long live Ubuntu!

---

