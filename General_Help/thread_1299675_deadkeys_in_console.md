---
title: "deadkeys in console"
date: 2009-10-24
forum: General Help
---

### Post by zes on 2009-10-24
hi again, i have a strange issue with karmic

last time i used ubuntu was 15 days ago, all worked fine

Ubuntu 9.10, xfce4, without gdm, login from console.

ok, on the loading system screen and after last update, appears the new b&W logo, loading scripts it hangs after init-bottom and stops there.

i modifiy kernel line adding rw init=/bin/bash

boots ok, after init-bottom it makes fsck and ok, but appears root@(none),reboot into distro installed (Archlinux), check hostname y saw is wrong, i edited it with my real hostname. Reboot again now only with 3 at the end of the kernel line.

 appears login prompt with correct hostname. Before loggin, all keys of my keyboard works fine, after loggin like user or root, i can´t type neither "a" "e" (that limits me a lot, note that "A" and "E" works), logged like user i check the bash history and run startx.

In graphic mode "a" y "e" works fine in all apps, not in terminal and virtual consoles, i can´t type them, i can´t paste them into terminal.BUT MY USER AND ROOT PASSWORDS GETS "a" AND "e" AND BOTH OF THEM ARE RECOGNIZED (ONLY WHEN I TYPE THE PASSWDORD, but i can´t see it because is not shawn on screen.

Keyboard works fine, that is not the problem, i´m sure of that

keymap looks correctly configured, es_ES....UTF-8

I went again to Archlinux, keyboard works fine in text mode and graphic mode.

From Archlinux i opened a terminal and make  chroot to ubuntu partition, neither "a" "e" works. it seems too strange...

someone to give me a hand, knowing the limitations of the keys...
 
Perhaps from Arch i could edit the ubuntu´s bash or terminal history  to get commands to run on, but wich commands?

thx

---

### Post by jmalone767 on 2009-11-02
I have a similar issue...

my "Z" key does not work in any application... unless capitaliZed 

this is very annoying because several of my passwords contain a Z

the keyboard is not the problem and the keyboard settings all seem to be correct...

any suggestions?

---

