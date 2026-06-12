---
title: "User Login Issue(No GUI)"
date: 2011-10-19
forum: General Help
---

### Post by DEdesign57 on 2011-10-19
I am having some problems when logging in under my admin account in Ubuntu 11.10. When I log in, a only the background wallpaper loads up. No Unity launch bar, no power/shutdown button, or any other GUI/buttons for that matter. I still have access to the terminal but I dont know how to use it. Note that I started having this issued after installing something called compiz the day before, also note that when I log in under guest, Ubuntu works! Does anyone know what could be the problem and how to fix this. I am new to Linux.

---

### Post by RaganN on 2011-10-19
I have this same problem on one of my computers.  What worked for me was to login using Unity 2D instead of Ubuntu (when you enter your password, there will be a gear symbol next to your name, click that for a list of desktops and choose 2D.)  It seemed my issue was caused by there not being a driver for my graphics card, and so opengl/3d were simply not working.

---

### Post by DEdesign57 on 2011-10-19
No driver huh, Ill give this a try, but dost that mean im going to have to use unity 2D for now on? And I have a gaming graphics card so I know I should be able to handle unity no problem.

---

### Post by obuntu91 on 2011-10-19
I also have the same problem after I installed compiz but I can't login at all. When I try to login in to my account it logs off. If I try to login to my account and then use the Guest account the Guest account becomes unusable, no GUI.

---

### Post by obuntu91 on 2011-10-20
I installed gnome from the guest account and the problem it's fixed

---

### Post by DEdesign57 on 2011-10-20
how did you install Gnome? And does that mean you have no more unity.

---

### Post by RaganN on 2011-10-21
If the problem only occured after changing compiz settings, you can restore the default unity settings by running the command:

unity --reset

You can get to the command line either by opening a terminal (ctrl-alt-T) or by pressing Ctrl-Alt-F2 and entering your username and password. 

That will reset all of the changes you have made to Unity, and might let you log back in.

---

