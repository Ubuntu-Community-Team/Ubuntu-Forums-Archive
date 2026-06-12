---
title: "X server already running on display :0"
date: 2009-11-02
forum: General Help
---

### Post by lithmariel on 2009-11-02
I keep getting that error while logging in after I upgraded from 8.04 to 9.04 (and everyone I found with same errors were upgrading from 8.04 also, sigh, still nvidia problem to solve after this one)

It also asks if I want to go on a different display, I say yes, and all goes normally, except that it won't let me install nvidia drivers with that x server open. 

Tried searching for solutions but found nothing, so... Solutions?

---

### Post by hal10000 on 2009-11-02
Type STRG-ALT-F2, then login with your username and type
```
sudo killall kdm
```
(or killall gdm / killall xdm if you are using one of these display managers).

After you killed the diplay manager, start it again with
```
 sudo kdm
```

and see if you get a graphical login screen.

To get your nvidia driver installed use **jockey-kde**

---

### Post by lithmariel on 2009-11-02
What is the "STRG"? And I do that while I'm logging?

---

### Post by hal10000 on 2009-11-02
> What is the "STRG"? And I do that while I'm logging?

STRG, ALT and F2 are the keys you have to press together (at the same time), then you will get a black login screen where you can log in with your user name

[EDIT] sorry i have a german keyboard, the keys you have to press are CTRL-ALT-F2

---

### Post by lithmariel on 2009-11-02
"and see if you get a graphical login screen", but I already do, everything is fine, except for that error, and it won't let me install nvidia drivers because of it. 
Sorry I didn't describe it well yesterday, I was tired and sleepy, editted now.

And I do that before or after logging?

Edit: Fixed it now, removed GDM, installed it again, then rebooted and installed NVIDIA, rebooted again and both problems solved.

---

