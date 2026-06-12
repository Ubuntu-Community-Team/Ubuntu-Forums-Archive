---
title: "No graphical login screen:("
date: 2010-03-03
forum: General Help
---

### Post by kartal on 2010-03-03
Hi
Recently my Ubuntu has started dropping to bash shell instead of starting the graphical login. It first asks me login name and bassword(in the shell) then gives me a command line. I can then type startx to start it. It seems to start alright but that is not how it is supposed to work.

Doed anyone know how I can get it back to default behaviour?

thanks

---

### Post by patchwork on 2010-03-03
Did you accidentally remove gdm?  Did you manually edit your boot lines in grub? 

Either of these could cause this, along with some other, less likely scenarios.

I guess the first thing to try is to attempt to re-install gdm.  If it is already installed apt will tell you:

sudo apt-get install gdm

---

### Post by kartal on 2010-03-04
Hi

I do not think I messed with any of those. But in case I will reinstaall gdm

---

