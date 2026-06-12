---
title: "Weird error, unable to login"
date: 2011-03-19
forum: General Help
---

### Post by Vostrocity on 2011-03-19
I have a Ubuntu 10.10 system that I haven't been using in a while. Upon turning it on, it boots to a stripped down login screen (not the usual nice one) with a warning about power configuration. When I try to login it flashes a terminal and then reverts back to the login screen. I recorded a quick video if it helps: [http://www.youtube.com/watch?v=h3UHm4jOw5Y](http://www.youtube.com/watch?v=h3UHm4jOw5Y)

I'm not sure why it's doing this so I need some someone to diagnose what's wrong and teach me how to fix it. Thanks!

---

### Post by andrewthomas on 2011-03-20
From the login screen you should
 
<CTL>+<ALT>+<F1> to get a terminal
 
log in and
 
```
 
sudo apt-get update & sudo apt-get upgrade

```
then 
```
 
sudo --configure gnome-power-manager

```
then <CTL>+<ALT>+<F7> or <CTL>+<ALT>+<F8> to get back to gdm and log in to see if your problem is resolved.

---

### Post by Vostrocity on 2011-03-22
Thanks!

---

