---
title: "Ubuntu hangs on start after i deleted all content of libgtk2.0-0.immodules"
date: 2011-08-10
forum: General Help
---

### Post by philippe.winter on 2011-08-10
Hi,

I wanted to customize the keyboard to use the cedilla but accidentally i deleted all content of 
/usr/lib/gtk-2.0/2.10.0/libgtk2.0-0.immodules

Please help me out, i havent found any file to download and replace this one.

---

### Post by CatKiller on 2011-08-10
The best I can think of is to boot from a live cd, install the relevant package in that environment, and then copy the replacements for the files you deleted to your hard drive.

---

### Post by philippe.winter on 2011-08-10
I used synaptic to reinstall the gtk package with no success :/ also tried it using the terminal

maybe you can send me the file and ill try to replace it

---

### Post by philippe.winter on 2011-08-10
SOLVED:

sudo dpkg-reconfigure -phigh -a

---

