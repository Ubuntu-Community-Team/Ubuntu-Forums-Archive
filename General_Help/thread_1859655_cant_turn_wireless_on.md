---
title: "cant turn wireless on"
date: 2011-10-14
forum: General Help
---

### Post by loolooyyyy on 2011-10-14
i installed gnome-shell on live ubuntu, it had a button: turn wireless off, i did! then forgot to turn it on, 
so wireless was off during installation,now not detected
i mean when i push wireless button on keyboard the indicator light(on keyboard)  stays off
tried ifconfig wlan0 up, says: cant blablabla because of RF-KILL
do i need to install ubuntu again?
dont have access to ifconfig and lchw and those stuff right now
can you suggest something that actually works?
now i'm on windows

---

### Post by TeoBigusGeekus on 2011-10-14
Can you post us the output of
```
rfkill list
```
?

---

### Post by Bucky Ball on 2011-10-14
Have you plugged in an ethernet cable? Does that get you online? If so, do an update then, if you are not offered one in the process, check System>Administration>Hardware Drivers and check if there's a driver there for you card.


Also follow what TeoBigusGeekus has requested. The result of:

```
sudo lshw -C network
```

... would also be good along with the release you are using. ;)

---

### Post by loolooyyyy on 2011-10-14
good thing i just mentioned i dont have access to those :D
and it's 11.10 ofcourse

---

### Post by Bucky Ball on 2011-10-14
11.10? Try something more stable and you will probably have more luck. If you have no access to a cable it may be problematic, depending on what wireless card you have, but as you haven't posted that we wouldn't know. ;)

---

### Post by loolooyyyy on 2011-10-15
a fresh install and now it works
and no i cant use 11.04 because of stability, i'm working on gnome-shell and i need 11.10
the card is a ralink ra3090, it's very bugy, i've explained here how to get it working on 11.04: koosha.cc
on 11.10 works flawlessly 

and thanks to you  TeoBigusGeekus and 'Bucky Ball' both ;)

---

