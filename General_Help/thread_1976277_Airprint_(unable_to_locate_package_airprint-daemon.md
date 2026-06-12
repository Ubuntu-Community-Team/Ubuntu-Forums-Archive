---
title: "Airprint (unable to locate package airprint-daemon)"
date: 2012-05-08
forum: General Help
---

### Post by bigshoes on 2012-05-08
Hi, i'm still fairly new with using ubuntu, but i'm plenty capable with figuring things out, but i could use some help here. 

I am using virtual box to run ubuntu 12.04 on my windows 7 machine. I am trying to set up a airprint server so i can print from my ipad. 
I followed the instructions that were given by the following page:
[http://www.ranstam.se/?tag=air-print](http://www.ranstam.se/?tag=air-print)

When i follow the steps everything works well, but when i use "sudo apt-get install airprint-daemon" it acts like it is installing (goes through a percent complete) but in the end it replies "E: Unable to locate package airprint-daemon" 
I'm pretty sure that this is what is stopping me from picking up the printer through airprint. 

Thanks for the help.

(correction: it does a reading package list "percent done", and never finds it. obviously the install would never have been capable of happening.)

---

### Post by bigshoes on 2012-05-08
I'm thinking that i should be able to use one of these files on [http://ppa.launchpad.net/hughescih/ppa/ubuntu/pool/main/a/airprint-daemon/](http://ppa.launchpad.net/hughescih/ppa/ubuntu/pool/main/a/airprint-daemon/)

I'm just not sure yet on which one to use.

---

### Post by tombo9999 on 2012-05-20
I found a solution, maybe... ;)
1) Just remove ppa from Ubuntu Software Center.
2) Go to [http://ppa.launchpad.net/hughescih/ppa/ubuntu/pool/main/a/airprint-daemon/](http://ppa.launchpad.net/hughescih/ppa/ubuntu/pool/main/a/airprint-daemon/) and dowload airprint-daemon_1.0-1-1_all.deb
3) find the file and double-click, choose "Install"
4) open Printers and, in the "top bar", choose Server Settings
5) follow instruction and image at: 
[http://www.azsoftwaredownload.com/linux/apple-airprint-support-ubuntu](http://www.azsoftwaredownload.com/linux/apple-airprint-support-ubuntu)

It works on Ubuntu 12.04.

Hope it helps.

---

