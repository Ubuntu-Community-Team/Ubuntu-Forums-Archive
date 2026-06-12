---
title: "can I remove gdm and keep gnome"
date: 2009-10-31
forum: General Help
---

### Post by dvdljns on 2009-10-31
I hate gdm and love gnome. Is there a way to remove gdm. gdm seems to be tied to ubuntu-desktop and so is gnome. Everyone talks about how easy it is to customize linux how do I get rid of this junk login program.

---

### Post by Anonymousable on 2009-10-31
gdm is part of gnome. They're interdependent. In other words, NO.

---

### Post by albandy on 2009-10-31
what version of ubuntu are you using?

---

### Post by dvdljns on 2009-11-01
> **albandy said:**
> what version of ubuntu are you using?

8.04

---

### Post by The Cog on 2009-11-01
So how do you intend to log in if GDM isn't running?

If you are happy to log into a TTY console and then use the command startx, then sudo chmod -x /etc/init.d/gdm will prevent GDM from starting when the system boots.

If instead you mean you want a user to auto-login then this is an option in System->Administration->Login Screen.

---

### Post by dvdljns on 2009-11-02
> **The Cog said:**
> So how do you intend to log in if GDM isn't running?


Login is about the only thing I do not need x for. 

> 
If you are happy to log into a TTY console and then use the command startx, then sudo chmod -x /etc/init.d/gdm will prevent GDM from starting when the system boots.


Somehow as buggy as gdm is That seems like a simple solution for a big problem. I will try it and get back to you. I never understood why they built a x program to handle login. seems like sideways thinking to me. I am happy with TTY loggin. I do not even mind if I have type startx every time need xwindows.

> 
If instead you mean you want a user to auto-login then this is an option in System->Administration->Login Screen.

I don't even let my windows login auto.

---

