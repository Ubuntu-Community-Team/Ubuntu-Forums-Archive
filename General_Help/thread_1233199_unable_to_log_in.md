---
title: "unable to log in"
date: 2009-08-06
forum: General Help
---

### Post by abelito8 on 2009-08-06
Hi everybody, 

With no warning (I restarted it 10 minutes ago) my computer is not logging me in...
I am using a kubuntu 9.04 with the three desktop environments installed and a partition (with windows that no longer works)

When I switch it on I can choose the system I want to use, this leads me to the login page (where I can choose the desktop environment and have to type my password)...

but when I type in my password it simply brings me back to the initial login page. I have tried to log in with KDE, Gnome and XFCE the result is the same...

I have tried to log in through the terminal and it works, which means the system is still working, however I am not experienced enough to work only through the terminal nor to enter a graphical interface through the terminal

Any idea of what shall I do?
Thank you in advance

---

### Post by quixote on 2009-08-08
Not sure what could be causing your problem, but let's see whether any of the desktop environments load.  I believe (not sure!) that the command is whichever one you want of:
startxfce4
startkde
/etc/init.d/gdm start

If you're not at a root prompt, then you'd need sudo first, eg "sudo startkde"

---

