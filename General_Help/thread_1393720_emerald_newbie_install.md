---
title: "emerald newbie install"
date: 2010-01-29
forum: General Help
---

### Post by Da CalebMan on 2010-01-29
Hey guys, I just installed Emerald. I got the Mooomex-emerald theme and imported into EMERALD THEME MANAGER. But it didn't work, so I opened a terminal and typed, "emerald --replace" then the window frame changed. However if I close the terminal, all the window frames disappear. 

How do I set Emerald up so that it changes everything to what the theme should look like, and doesn't close when the terminal closes?

---

### Post by VastOne on 2010-01-29
> **Da CalebMan said:**
> Hey guys, I just installed Emerald. I got the Mooomex-emerald theme and imported into EMERALD THEME MANAGER. But it didn't work, so I opened a terminal and typed, "emerald --replace" then the window frame changed. However if I close the terminal, all the window frames disappear. 

How do I set Emerald up so that it changes everything to what the theme should look like, and doesn't close when the terminal closes?

In CompizConfig Settings Manager

Under Enable Window Decoration

In the Command window put this:

/usr/bin/emerald --replace

---

### Post by howefield on 2010-01-29
Use a run box.

Press the alt + F2 keys, then type the command into that.

You can also add emerald --replace into your startup programs.

---

### Post by Da CalebMan on 2010-01-29
Thanks! By the way, do I need to uninstall GTK GNOME appearance to for emerald to do the full theming? 

~THANKS!:popcorn:

---

### Post by howefield on 2010-01-29
Don't think so, if I understand what you are asking :)

What do you mean by full theming ?

Emerald only looks after the windows decoration. It doesn't do anything else.

---

### Post by JustAnotherVagueAnon on 2010-01-29
Btw, any time you want to run a command without it hanging, use the command "nohup" or append an ampersand (&) to the back of the command:

example: gedit file.txt &

---

### Post by Da CalebMan on 2010-01-29
Oh! No wonder. I thought Emerald was an entire theme manager! Darn.

Anyway ~THANKS!

---

