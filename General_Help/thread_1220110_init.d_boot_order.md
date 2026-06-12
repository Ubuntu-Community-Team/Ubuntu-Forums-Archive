---
title: "init.d boot order"
date: 2009-07-22
forum: General Help
---

### Post by namelessone on 2009-07-22
I have several custom init.d scripts that I need to be executed in a certain order (i.e ScriptA cannot start until apache has started).

How do I do this?

btw, I am running ubuntu server edition, so I don't have a gui.

---

### Post by KeyserSoze93 on 2009-07-22
Check out /etc/rc3.d, the files are all symlinks to init.d scripts prefixed with a number to specify the order. rc3 is runlevel 3, which is what a GUI-less system will be running.

---

### Post by namelessone on 2009-07-22
Yes, but is there any program that reorders the scripts so I don't have to do it myself? It's kinda messy to have to renumber them all by hand.

---

### Post by namelessone on 2009-07-27
I read about this command called insserv -- is this the command that i'm looking for?

---

