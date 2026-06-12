---
title: "Mouse Issues"
date: 2011-03-31
forum: General Help
---

### Post by JamesBartlett on 2011-03-31
Hi Guys, I recently switched from Win7 to Ubuntu, and am continuing to use the same mouse (Toshiba *PA3706E*-1ET1) which I love, however, the mouse has one or two extra buttons, which do work (e.g. one does the same as ALT+Tab) but the mouse came with a software CD which allowed you to edit what the buttons did, which I did a long time ago. I still have the CD but IT is only Windows compatible. I have tried running the contained .exe file on Wine to no avail. anyone able to help? Thx! I am running Ubuntu 10.04

---

### Post by nickleboyblue on 2011-03-31
There is a program called btnx (or "Button Extension") for GNU/Linux that allows you to map extra mouse buttons to key combinations from the keyboard, thus allowing you to set up keyboard shortcuts in System->Preferences->Keyboard Shortcuts and then map those keystrokes to your mouse's extra buttons.  This makes it possible to do whatever you want to with your extra mouse buttons.


```
sudo apt-get install btnx btnx-config
```

Or you can just install both packages with Synaptic.

---

### Post by JamesBartlett on 2011-03-31
> **nickleboyblue said:**
> There is a program called btnx (or "Button Extension") for GNU/Linux that allows you to map extra mouse buttons to key combinations from the keyboard, thus allowing you to set up keyboard shortcuts in System->Preferences->Keyboard Shortcuts and then map those keystrokes to your mouse's extra buttons.  This makes it possible to do whatever you want to with your extra mouse buttons.


```
sudo apt-get install btnx btnx-config
```

Or you can just install both packages with Synaptic.
Synaptic?

---

