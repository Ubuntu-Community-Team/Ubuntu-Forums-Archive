---
title: "keyboard shortcut to open trash"
date: 2010-01-22
forum: General Help
---

### Post by princeofnam on 2010-01-22
does anyone know how to do this? i'd open it up through alt+f2 and nautilus but i don't know its location or any other means.

---

### Post by n0dix on 2010-01-22
> **princeofnam said:**
> .... i don't know its location or any other means.

In Hardy Heron the location of Thrash folder is:
```
~/.local/share/Trash/
```

---

### Post by princeofnam on 2010-01-23
doesn't seem to work in karmic unfortunately.

---

### Post by n0dix on 2010-01-23
Do this and post the output:
```
sudo find / -type d -name *Trash*
```

---

### Post by princeofnam on 2010-01-23
the query just sorta hung for awhile in terminal

---

### Post by philinux on 2010-01-23
I'm running karmic and trash folder is here for sure.

/home/username/.local/share/Trash

or

~/.local/share/Trash

---

### Post by princeofnam on 2010-01-24
what is the "~/" supposed to mean in unix? it works the same with or without it

---

### Post by Joey B. on 2010-01-24
Have you tried going to System>Preferences>Keyboard Shortcuts?

---

### Post by s.fox on 2010-01-24
> **princeofnam said:**
> what is the "~/" supposed to mean in unix? it works the same with or without it

Hello,

The ~ is the home directory :D

-Silver Fox

---

### Post by chewearn on 2010-01-24
> **princeofnam said:**
> what is the "~/" supposed to mean in unix? it works the same with or without it

The tilde symbol (~) is shortcut for your home directory.

---

### Post by John Bean on 2010-01-24
> **princeofnam said:**
> what is the "~/" supposed to mean in unix? it works the same with or without it

It expands to your home directory. If you're already there it makes no difference, but if you're somewhere else it does.

---

### Post by houseworkshy on 2010-01-24
It isn't in Preferences>Keyboard shortcuts so perhaps there isn't one.  You could always set one there if you like.  
@princeofnam The ~ means home.  So if you have browsed around in the terminal typing cd ~ will bring you back quickly.  I see what you mean though cd ~ and cd ~/  seem to do the same thing.

---

### Post by dnairb on 2010-01-24
The trash icon should apear on the bottom panel of your desktop, on the right hand side.
You can have the icon on the desktop by opening gconf-editor:

alt+F2, type gconf-editor

Then open apps > nautilus and click on desktop

Then put a tick in the box next to trash_icon_visible

You can, I guess, set a custom keyboard shortcut to open the trash. The files you have deleted, or sent to trash, appear in ~/.local/share/Trash/files

---

### Post by John Bean on 2010-01-24
> **princeofnam said:**
> does anyone know how to do this? i'd open it up through alt+f2 and nautilus but i don't know its location or any other means.
```
nautilus trash:///
```

---

