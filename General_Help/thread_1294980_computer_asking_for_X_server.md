---
title: "computer asking for X server??????????????????"
date: 2009-10-18
forum: General Help
---

### Post by BLOODHOUND11245 on 2009-10-18
when I turn on my computer it say failed to load X server and redirects me to the terminal......... could some one help please.........

---

### Post by iMisspell on 2009-10-18
while at the terminal you can try:
```
startx
```
and see what happens.
Posting the version of ubuntu might also help people, help you.
Also if you have changed anything, specialy if it had to do with your video card.

_

---

### Post by BLOODHOUND11245 on 2009-10-19
well I have ubuntu 9.04. and when i put in the comand it said that i needed to reconfigure x server. and what i previously did was install kubuntu inside of ubuntu and also ubuntu studio.

---

### Post by OpenGuard on 2009-10-19
```
sudo dpkg-reconfigure xserver-xorg
```

Follow the instructions and you should be fine.

---

### Post by BLOODHOUND11245 on 2009-10-19
thanks it worked

---

