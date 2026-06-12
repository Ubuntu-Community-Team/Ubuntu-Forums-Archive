---
title: "help me to install g++ on ubuntu 9.10"
date: 2011-02-12
forum: General Help
---

### Post by satishkumbhar on 2011-02-12
$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g
sbpcoe@sbpcoe-desktop:~$

---

### Post by lisati on 2011-02-12
> **satishkumbhar said:**
> $ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package g
sbpcoe@sbpcoe-desktop:~$

It almost reads as if you accidentally left a space after the g on the apt-get line.

---

### Post by Vaphell on 2011-02-12
sudo apt-get install build-essential
to get g++ and more programming related stuff

---

