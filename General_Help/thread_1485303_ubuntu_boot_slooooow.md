---
title: "ubuntu boot slooooow"
date: 2010-05-16
forum: General Help
---

### Post by sydd1 on 2010-05-16
Hi 

I've just tried to install Ubuntu 10.04 64 bit cause i've heard that its really fast.
I installed from windows 7 with WUBI to try it out first.
Everything works fine, except on boot i get a screen which says something like
try hd(0,0) no wubildr.

And this screen stays there for like 2 minutes.
Is this normal? cause my windows 7 boots like 5 times faster.
Im using a core duo 7400 with 4GB of ram.

---

### Post by Oblivion_4 on 2010-05-16
I don't have an answer for you but I can say that ubuntu should be at least as fast as windows 7. Here's some proof [http://www.youtube.com/watch?v=vM7LnDqZGgQ](http://www.youtube.com/watch?v=vM7LnDqZGgQ)

Also running ubuntu as an application on top of windows will make it slower than running ubuntu natively from you're hard drive

---

### Post by emanuel.b on 2010-05-16
Is this only with the WUBI installation? Does it do the same thing when you boot from disc?

---

### Post by sydd1 on 2010-05-16
I've tried it from a live CD, and i had no problems

Edit:
heres the exact message:

Try hd(0,0) NTFS5: no wubildr
then a 2 min break.. and for a moment:
try hd(0,1)   or something
After that itll boot up fast

---

### Post by techunit on 2010-05-16
I had the same problem when I "wubi"ed it but I decided to do a full install next to Windows and The boot speed of ubuntu went from just around a minute and 30 seconds to around 20 seconds.

---

### Post by techunit on 2010-05-16
You are going to have performance problems with WUBI and there is no getting around that. The Boot time is the worst. It has to load windows boot loader and the the grub boot loader after that and it is a huge mess.

---

### Post by sydd1 on 2010-05-16
Thanks for the tip, is the a way to upgrade wubi to a full ubuntu installation? i dont care if my data/settings are lost.
Edit:
nvm, i found it:
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
Thanks for help

---

### Post by techunit on 2010-05-16
Um I would recommend that you do a full install the normal way and don't attempt to move your wubi into a full install I would just do a normal install after backing up your data from the wubi install.

---

