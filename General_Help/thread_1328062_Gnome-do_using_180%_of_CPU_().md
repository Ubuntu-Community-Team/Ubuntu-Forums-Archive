---
title: "Gnome-do using 180% of CPU (?)"
date: 2009-11-16
forum: General Help
---

### Post by Cod on 2009-11-16
Hi,
I recently upgraded from Jaunty to karmic.  The upgrade process was smooth and sweet.  However, according to System Monitor Gnome-do is now taking 180% of my CPU and my computer has become stuttery.  I'm not sure what is going on.  There is a lot of hard drive access too.

Anyone got any ideas what is happening?

Cheers

---

### Post by wilee-nilee on 2009-11-16
Open system monitor system-administration-system monitor right click on any gnome do running then click on kill this will shut it off then try opening it again and see if it still causing this high usage. I have had it do this as well in Karmic.

There is also htop install from the terminal sudo apt-get install sudo apt-get install htop 
This is also in synaptic you can shut down stuck programs with either, like Firefox for example. If gnome do doesn't startup after killing it just do a restart, gnome do seems a little buggy in Karmic for me so I hardly ever use it.

---

### Post by giancaldo on 2009-12-12
in gnome-do preferences try disabling all the plugins. that seems to have worked for me.

---

