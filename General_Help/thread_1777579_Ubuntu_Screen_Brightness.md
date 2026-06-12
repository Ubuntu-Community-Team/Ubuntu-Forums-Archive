---
title: "Ubuntu Screen Brightness"
date: 2011-06-07
forum: General Help
---

### Post by hugom on 2011-06-07
I booted with windows 7 for the first time in a while and realised that it is so much brighter and makes ubuntu look so dull. 

I've gone into power management and the screen brightness bar was all the way up?

Is there any to make it more bright or something?

Does anyone else think this or is it just me?

I'm using gnome desktop on 10.10.

cheers, hugom.

---

### Post by pqwoerituytrueiwoq on 2011-06-07
only thing i can guess if you don't have the right graphics driver installed
although i thought brightness was hardware controlled honestly

---

### Post by hugom on 2011-06-08
Yeah didn't really think I could do anything about it.

But it was worth a try.

Thanks a lot though.

---

### Post by devonte on 2011-06-08
try the following:


sudo setpci -s 00:02.0 F4.B=FF

---

### Post by jwcalla on 2011-06-08
Some graphics drivers settings programs can control the display brightness, e.g., nvidia-settings.

---

### Post by hugom on 2011-06-08
> **devonte said:**
> try the following:


sudo setpci -s 00:02.0 F4.B=FF

Thanks.

Tried it but nothing happened.

---

### Post by pqwoerituytrueiwoq on 2011-06-09
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update
sudo apt-get upgrade
```
it will update several display packages (worth a try)
you may need to restart gdm to see changes after installing
close all apps [FONT="Courier New"]sudo service gdm restart[/FONT]

---

