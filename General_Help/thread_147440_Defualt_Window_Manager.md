---
title: "Defualt Window Manager"
date: 2006-03-20
forum: General Help
---

### Post by benofsky on 2006-03-20
hi,
I've just installed ubunu linux on an old win2k machine it was all good then I installed Kubuntu-desktop (kde)! And changed it to defualt I can't log in from xdmcp any more and I can't access the login scren prefences menu, (bye the way the defualt window manager was changed to kde and that's my problem)! Is there a way that I can change the defualt window manager from the command line because I can ssh into it and change it and I don't paticulary want to carry a monitor keyboard and mouse down to my basement! Any help would be apreciated
Ben!

---

### Post by oakz on 2006-03-20
what you are talking about is the display manager, not a window manager. To change back from kdm (the KDE display manager) to gdm (the GNOME one)...change the contents of /etc/X11/default-display-manager to be "/usr/sbin/gdm" and reboot

to manually stop kdm and start gdm, do the following:
$ sudo /etc/init.d/kdm stop
$ sudo /etc/init.d/gdm start

---

### Post by benofsky on 2006-03-20
I've never used linux before, thanks alot!
Ben

---

