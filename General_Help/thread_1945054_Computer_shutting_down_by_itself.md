---
title: "Computer shutting down by itself"
date: 2012-03-22
forum: General Help
---

### Post by sumguy on 2012-03-22
My computer is running for a (seemingly) random amount of time, then shutting off by itself. I recently had the case open to recover a hard drive, so I checked inside. All the fan seem to be running, so I have no reason to think it would be overheating. Any ideas?

It's weird because sometimes it will only stay on a few minutes, but last night I upgraded to ubuntu 10.10 and it ran all night.

---

### Post by Frogs Hair on 2012-03-22
I would check the cpu temp because shutdowns like you are describing are often a result of overheating. ```
sudo apt-get install lm-sensors
``` Next run ```
sensors
```

---

### Post by deserthowler on 2012-03-22
If this is the computer suddenly quitting and not doing a normal shutdown, it might be a bad memory stick.  I salvage parts and rebuild "junkers" and have run into this problem a few times.  I"ve worked my way up to a P4  :D

Earl

---

### Post by 2F4U on 2012-03-22
Is the machine doing a regular shutdown or is it crashing? If it is doing a shutdown, I would suspect a problem with heat. Else it could be a bad hardware component such as RAM. Anyways, you should look into the log files and see if you can find some hints on what the problem is. It also doesn't hurt to run memtest from a liveCD. If you do that, run several iterations and not just one. Some RAM problems are only discovered on the second or third iteration.

---

### Post by deserthowler on 2012-03-23
As a quick memory test, I switch the memory sticks around.  This is not an infallible test, but it is quick.

Earl

---

