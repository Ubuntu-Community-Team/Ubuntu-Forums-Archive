---
title: "Messed system library"
date: 2011-01-08
forum: General Help
---

### Post by layers on 2011-01-08
To make a long story short, I ran this command

```
sudo ln -s -f /usr/lib/libXi.so.6.0.0 /usr/lib/libXi.so.6

```and now, the menus are not working properly. To be more specific, I cannot launch an application using the menus (Ubuntu 10.04). I think I've been here months ago, when running 10.10, and when I restarted my machine, I had to reinstall gnome. What should I do (besides not restarting)?

---

### Post by layers on 2011-01-08
OK, now thing go much worse: after typing the command
```
sudo /etc/init.d/gdm restart
```the screen flickered, and I am where I knew it's going to go - stuck in terminal with no GUI. 

I tried ```
apt-get remove gnome

apt-get remove gnome-panel

```and then 
```
apt-get install gnome
``` (which gives me Broken packages error)
and ```
apt-get install gnome-panel
```which tells me that it could not resolve  some web links ending in .deb

Help please!

PS: I did manage to rename libXi.so.6 back to libXi.so.6.0.0, but no change.

---

