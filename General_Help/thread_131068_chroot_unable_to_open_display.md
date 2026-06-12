---
title: "chroot unable to open display"
date: 2006-02-15
forum: General Help
---

### Post by madubuntuer on 2006-02-15
sc@ubuntu:~$ dchroot -d xclock
(breezy) xclock
dchroot: chdir: No such file or directory
Xlib: connection to "localhost:0.0" refused by server
Xlib: No protocol specified

Error: Can't open display: :0.0
dchroot: Child exited non-zero.
dchroot: Operation failed.

why? I have installed the xbase libraries. but it still wont work. sc is a normal user. Basically what am trying to link my chroot to my 64bit xserver so that i can run anjuta along with sdl and other 32bit apps.

---

