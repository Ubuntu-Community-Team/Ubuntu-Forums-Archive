---
title: "Login without x11"
date: 2009-10-07
forum: General Help
---

### Post by rubenator on 2009-10-07
Hey..  This is my very first post in the u untu forums!!  It took me a while to figure out how to actually start a new thread...

Anyway I am pretty much new to the amazing world of Linux and I've been reading a lot... 

But I'm still trying to figure out how to start a session without the GUI...  Command line only? 
I tried init 3..  But apparently it didn't work..  Somebody pls help.

---

### Post by tgeer43 on 2009-10-07
If you are already in a graphical desktop environment then you can go to System->Administration->Services and uncheck the Graphical Login Manager (GDM).

tgeer

---

### Post by JeSTeR7 on 2009-10-07
Ctrl+Alt+F1 should bring you to a terminal where you can login.

---

### Post by rubenator on 2009-10-07
Kk thnx a lot...

---

### Post by stefanadelbert on 2009-10-07
Doesn't grub give the option of booting directly into a terminal? At bootup, hit Esc and check grub's bootup options.

---

