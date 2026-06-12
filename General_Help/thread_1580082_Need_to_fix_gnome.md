---
title: "Need to fix gnome"
date: 2010-09-22
forum: General Help
---

### Post by arashiko28 on 2010-09-22
Whenever I log in, restart, etc... There are no panels shown, I have to alt+F2, open terminal and run killall gnome-panels in order to have panels shown again. Is there a way to fix this?

---

### Post by andrewthomas on 2010-09-22
```
rm -r ~/.gconf/apps/panel
```**copy and paste** the above code into the terminal in order to reset your gnome-panel configuration

---

### Post by arashiko28 on 2010-09-26
That only deleted the additional icons I had added to the panels, but still does not solves the problem. :(

---

### Post by rinatin on 2010-10-05
I am having the same trouble exactly.

Any fixes or advice?

Thanks!

---

### Post by Crazedpsyc on 2010-10-05
I too had the same problem in Karmic except it only happened every so ofter, so I just made a launcer icon on my desktop to do killall gnome-panel, but if it's happening all the time that would get very annoying. I know why killing it helps, (because gnome automatically restarts it whenever it is killed) but that's about it. I would appreciate some help here too

---

