---
title: "Need to restart X to have the keyboard to work properly"
date: 2011-02-19
forum: General Help
---

### Post by diggan on 2011-02-19
I've recently installed Ubuntu 10.10 and everything worked like a dream the first 10 days. Now I have to restart X to get my keyboard to work like it should.

When I start the computer everything is fine until the login prompt where my password contains certain letters that don't work. To fix this I must use ctrl + alt + F1 and then start htop/top to find PID of X and kill it. This fixes the problem temporary but after next reboot I need to the same again...

Someone who got a fix for this?

---

### Post by diggan on 2011-02-19
Shameless bump

---

### Post by jerrrys on 2011-02-19
have you tried to edit x and save ?

is this the command you used ?

sudo dpkg-reconfigure -phigh xserver-xorg

---

