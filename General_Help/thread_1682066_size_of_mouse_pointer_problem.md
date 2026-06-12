---
title: "size of mouse pointer problem"
date: 2011-02-05
forum: General Help
---

### Post by jolian ramos on 2011-02-05
i have ubuntu 10.04

i want to change the size of mouse pointer i use right click on the desktop then change desktop background then choose Themes --> customize then i draw from small to large  and the pointer get large only in windows like firefox but when i get the pointer on desktop i get the same size the small size can you help me please ?

---

### Post by VCoolio on 2011-02-05
Try expermenting with the number in this line in ~/.gtkrc-2.0 (create if it doesn't exist yet, don't know how it interacts with gnome-settings-daemon, but give it a shot):
gtk-cursor-theme-size = 16
You'll need to log out and back in, or try reconnecting the mouse.

---

### Post by aeronutt on 2011-02-05
> **jolian ramos said:**
> i have ubuntu 10.04

i want to change the size of mouse pointer i use right click on the desktop then change desktop background then choose Themes --> customize then i draw from small to large  and the pointer get large only in windows like firefox but when i get the pointer on desktop i get the same size the small size can you help me please ?

Odd, I just tried this and get the same results. In most windows, the pointer changed. But on the desktop, it stays the same as prior to changing the setting.

---

### Post by jolian ramos on 2011-02-05
i don't understand anything at all i am very fresh in using ubuntu so please explain more if you don't mind thank you 

> **VCoolio said:**
> Try expermenting with the number in this line in ~/.gtkrc-2.0 (create if it doesn't exist yet, don't know how it interacts with gnome-settings-daemon, but give it a shot):
gtk-cursor-theme-size = 16
You'll need to log out and back in, or try reconnecting the mouse.

---

### Post by aeronutt on 2011-02-05
> **jolian ramos said:**
> i don't understand anything at all i am very fresh in using ubuntu so please explain more if you don't mind thank you

If I were you, as a rookie, I'd wait and see if someone else has a known and easier fix. Others must be having the same issue. I know on the previous version (9.10), changing the mouse via the gui as you tried, worked fine.

---

### Post by jolian ramos on 2011-02-15
any help please

---

### Post by yyyc186 on 2011-03-15
Bump!

I have this bug as well.

---

