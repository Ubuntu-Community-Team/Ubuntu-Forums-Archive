---
title: "I cannot connect to X server"
date: 2009-12-18
forum: General Help
---

### Post by wanderer26 on 2009-12-18
Hello fellows,
I am new to Linux but till yesterday I had well working Kubuntu 9.10 on VMWare. I was trying to enable 3D effects and something went very wrong.

I don't know how I did it but X server wanted to reboot and then it didn't want to start again. My Kubuntu starts in console mode. I tried to reinstall the X server but when I write "startx" it says:
Fatal server error: no screens found

If I try any graphical application it says:
Cannot connect to X server

My video card is ATI Mobility Radeon HD 4330 Series
I may have installed wrong drivers...

Please, help.

---

### Post by wanderer26 on 2009-12-18
Please, anyone, any ideas?

---

### Post by deadalus.globalnode on 2009-12-18
Explain what you mean when you say you tried to reinstall X.

---

### Post by wanderer26 on 2009-12-18
I tried this command in the console:

sudo apt-get install --reinstall xserver-xorg

It worked well. I also tried this:

sudo dpkg-reconfigure xserver-xorg

---

