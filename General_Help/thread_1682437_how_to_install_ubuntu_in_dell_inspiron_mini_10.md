---
title: "how to install ubuntu in dell inspiron mini 10"
date: 2011-02-05
forum: General Help
---

### Post by cjprofile on 2011-02-05
hey guys..help.well i want to install ubuntu in my dell..ive already installed one in my desktop can i use that installer to my dell mini inspiron 10?? i have a usb hard drive..or better to use usb stick? well what about blackbuntu?? seems awesome can i install that in my dell??? i dont wanna make mistake again .. help..

---

### Post by RedSingularity on 2011-02-06
Well you need to create a bootable usb drive.  This will allow you to boot your netbook from the usb stick and install the system.  To create the usb stick use unetbootin.  Its in the repositories.  On your desktop run:

sudo apt-get install unetbootin

to install it.  Then just run it to create your bootable stick.  Once you create the stick, plug it into your netbook and have the netbook boot from it.

---

### Post by cjprofile on 2011-02-06
thanks man it works..to be able to install it i unplug the internet wire of my desktop and i connct it to my netbook.. and now my problem is.. my netbook cant detect to the internet seems like wireless thingy is not working... how to fix that?? i tried to follow some of google steps. but didnt work

---

### Post by RedSingularity on 2011-02-06
Can you plug it into a wired connection temporarily?

---

### Post by cjprofile on 2011-02-06
> **RedSingularity said:**
> Can you plug it into a wired connection temporarily?
ya .. but how about my desktop , i need the wire for my desktop

---

### Post by RedSingularity on 2011-02-07
Thats fine.....just plug the wire into the netbook temporarily and use it to install the most recent updates.  After updating see if your wireless connection works.

---

