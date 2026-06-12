---
title: "Kmobiletools"
date: 2006-04-06
forum: General Help
---

### Post by GreveFelix on 2006-04-06
Hello.
I am trying to install kmobiletools. But I cant find it in my installed Sources. I tried to add  

#ubuntu.czessi.net 
deb [http://archive.czessi.net/](http://archive.czessi.net/) breezy stable stable-updates testing testing-updates

to my sources.list but there was an error: NO PUBLIC KEY ! Does somebody know an an other adress where I could find kmobiletools or why there was this error? 


Or should I install WINE and run the original Motorola Software, for my Motorola Razr V3I??

---

### Post by nekr0z on 2006-05-01
[QUOTE=GreveFelix]
#ubuntu.czessi.net 
deb [http://archive.czessi.net/](http://archive.czessi.net/) breezy stable stable-updates testing testing-updates

to my sources.list but there was an error: NO PUBLIC KEY ! Does somebody know an an other adress where I could find kmobiletools or why there was this error? [/QUOTE]
This error is easy to solve:

wget [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg)
sudo apt-key add kczessi.gpg
rm kczessy.gpg

By the way, the correct line for sources.list is:
deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) breezy main restricted universe multiverse

---

### Post by GreveFelix on 2006-05-01
Thanks, that solved the problem.

---

### Post by taurusx5 on 2008-02-26
I have a Razr V3i and I want to use Kmobiletools to access my phonebook. I installed it on my Ubuntu 7.10 but it doesn't recognize my Razr. What do I do to make Kmobiltools recognize my Razr V3i? Thanks !

---

### Post by Shampyon on 2008-03-01
I've got a V3i as well. In kmobiletools under *Settings >> Main Settings*, the device is automatically set as /dev/mobile. To get mine working I just had to change it to /dev/ttyACM0. Hopefully that'll work for you too. Good luck :)

---

