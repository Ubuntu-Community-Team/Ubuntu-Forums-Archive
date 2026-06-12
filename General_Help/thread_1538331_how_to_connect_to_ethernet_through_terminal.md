---
title: "how to connect to ethernet through terminal?"
date: 2010-07-24
forum: General Help
---

### Post by owners4life5 on 2010-07-24
hello

how can i connect to the internet through an ethernet cable in the terminal... i.m having trouble booting and i need to connect to the internet and download some packages

any help is greatly appreciated

---

### Post by yetiman64 on 2010-07-25
> **owners4life5 said:**
> hello

how can i connect to the internet through an ethernet cable in the terminal... i.m having trouble booting and i need to connect to the internet and download some packages

any help is greatly appreciated

If you can access the grub menu boot a recovery mode (if it doesn't show normally, hold down SHIFT during boot). 

One of the options there is "netroot" (caution: it is a "root" terminal), this will drop you to a root terminal with networking support set up.

You should be able to download and install packages from there, once complete you can type "reboot" at the prompt or "exit" and then choose "continue normal boot".

Edit: being a root terminal drop all references to sudo in commands you use there, not needed.

---

### Post by owners4life5 on 2010-07-25
thanks for the quick reply... i actually figured it out myself... so i.ll mark it as solved (=

---

