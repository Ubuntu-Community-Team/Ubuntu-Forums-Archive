---
title: "Switch from XTERM to Gnome/GUI?"
date: 2009-11-14
forum: General Help
---

### Post by Cam! on 2009-11-14
I did a very dumb thing, and now I'm stuck in XTERM mode (where only the terminal shows up).

I switched the environment (via the login screen) from Gnome/GUI to XTERM. Now, whenever I start Ubuntu, it automatically logs me in, and goes to the terminal. Is there a way I can go back to the login screen, or somehow switch to the Gnome environment via a Terminal command? I tried some of the keyboard shortcuts, but they didn't work.

**OR,** is there a way I can solve this by doing something in Recovery Mode?

---

### Post by QLee on 2009-11-14
What happens when you enter the command exit in the terminal?

---

### Post by Cam! on 2009-11-14
Oh! Thanks! I'm a retard, LOL. I was messing around with XSTART. I guess I made a mountain out of a molehill. Thanks a lot!:D

---

### Post by QLee on 2009-11-14
[QUOTE=Cam!]Oh! Thanks! I'm a retard, LOL. I was messing around with XSTART. I guess I made a mountain out of a molehill. Thanks a lot!:D[/QUOTE]

Aw, you just don't yet have vast experience, none of us knew things until we learned. Give yourself credit for knowing how to ask, good luck!

---

### Post by ammarii on 2010-07-09
hi  I have the same problem 

when i type exit just doing log uot but when i log in stell the same  

also i tried startx & sudo dpkg-reconfigure gdm but i'm stell in xterm mode :(

---

### Post by Darkness Des on 2010-07-09
Use the same toggle switch to change your environment back.

---

### Post by ammarii on 2010-07-09
it doesn't work any other ideas?

---

### Post by nothingspecial on 2010-07-09
```
sudo service gdm start
```

---

### Post by jkid on 2010-12-26
when u type exit and it takes u to the login screen, look at the bottom where it shuld be a little box where u could switch between xterm and gnome

---

