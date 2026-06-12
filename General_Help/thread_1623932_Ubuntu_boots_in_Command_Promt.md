---
title: "Ubuntu boots in Command Promt"
date: 2010-11-17
forum: General Help
---

### Post by GGfpc on 2010-11-17
HEllo sexy peole!

I just installed Ubuntu 10.4.1 through wubi and I cant boot in the GUI

I used startx and the screen goes black

I also used sudo dpkg-reconfigure -phigh xserver-xorg and it cant find xserver.xorg (used the - phigh one too)

What can I do to solve this?

---

### Post by CTBuckweed on 2010-11-17
> **GGfpc said:**
> HEllo sexy peole!

I just installed Ubuntu 10.4.1 through wubi and I cant boot in the GUI

I used startx and the screen goes black

I also used sudo dpkg-reconfigure -phigh xserver-xorg and it cant find xserver.xorg (used the - phigh one too)

What can I do to solve this?


This has happened to me a couple of times also with 10.04. I've just recently learned that <Ctl><Alt> and a function key (F1-F6), maybe even more go through TTY login screens. <Ctl><Alt><F7> is the Gnome GUI. See if that gets you to the GUI...

---

### Post by shashanksingh on 2010-11-17
sudo apt-get install xserver-xorg

check if it is installed first

also check for gnome-common

---

