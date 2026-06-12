---
title: "Quick question: How to make a script run when you (dis)connect a particular WIFI?"
date: 2010-09-18
forum: General Help
---

### Post by kikazaru on 2010-09-18
I want to automatically mount a remote filesystem whenever I connect to a certain wifi network. I normally have to type sshfs ... ... every time. 

I'd like to make it automatic (although I'll need to type the password in anyway I guess, but I do that with zenity or some such).

---

### Post by bodhi.zazen on 2010-09-18
What about adding an entry to fstab ?

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

If you do not want it to automatically mount, use the option noauto.

In terms of password, use a key with no password or use ssh agent (seahorse, ssh-add, etc).

---

### Post by kikazaru on 2010-09-21
Much obliged.

---

