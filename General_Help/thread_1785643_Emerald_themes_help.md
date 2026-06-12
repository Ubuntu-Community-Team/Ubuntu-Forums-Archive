---
title: "Emerald themes help"
date: 2011-06-18
forum: General Help
---

### Post by hijiz on 2011-06-18
I know Emerald dosnt work in 11.04 but i found this article that gives a PPA that allows Emerald to work. the article is [http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html](http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html)
I instaled a few thmes but i cant use them. i duble click one of themand nothing hapens and i have used compiz fusion icon to set my window manager to compiz, and my window decorator to emerald. i am using ubuntu classic.

---

### Post by Frogs Hair on 2011-06-18
Try this in the terminal after you have selected the theme.
```
emerald --replace
```

---

### Post by dougalkerr on 2011-06-18
Go to the Ubuntu tweak utility and make sure Metacity is not still active as either the composting manager nor the window manager. I have found this before too and after making sure all the Metacity things were switched off Compiz and Emerald work just fine. You may need to reboot (but shouldn't have to).
Good luck.

---

### Post by hijiz on 2011-06-18
so 
> emerald --replaceFixed my issue but the theme i use now has the conrtols of close minimize, etc on the right.
how can i put them on the left?

---

### Post by hijiz on 2011-06-18
Also is there a way to change te title location.

---

### Post by lidex on 2011-06-18
You can change decoration options with emerald theme manager. Look in preferences menu. 'Theme Settings' main tab, 'Edit Themes' sub-tab, 'Titlebar' sub-tab allows you to place wherever you like.

---

