---
title: "I keep getting errors"
date: 2011-03-21
forum: General Help
---

### Post by Spyderkid on 2011-03-21
On my freshly installed 64bit ubuntu i keep getting this error:
Unable to lock the administration directory (/var/lib/dpkg/)
whats going on?

---

### Post by vivek.pandey on 2011-03-21
you getting this error when you are installing something from terminal and asked to enter your password as you typed sudo ....
or you tried to install something from synaptic.. right..? if its so the reason is you have two programs running simultaneously which require your password eg a sudo  in terminal and then you attempt synaptic or vice versa ...just quit one of the programs..

---

### Post by Krytarik on 2011-03-21
I guess what *vivek.pandey* wants to say, is that you can't run more than one package manager at the same time, e.g. apt-get, Synaptic, whatever else.

Greetings.

---

### Post by Spyderkid on 2011-03-22
I realised it only happens when im trying to install updates and downloads programs from the software centre, never mind then....

---

