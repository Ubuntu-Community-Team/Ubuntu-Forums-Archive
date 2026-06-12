---
title: "MySQL download for 64 Bit - it's just a dream"
date: 2012-04-07
forum: General Help
---

### Post by MyTorAndMe on 2012-04-07
Hi, guys.

I got two laptops here, one with Ubuntu 11.04 32 Bit and one with 10.04 LTS 64 Bit. Don't ask how, but I crashed the port of my network card on the 10.04 laptop, so I guess there will never any package be sent through this. :) So far I have downloaded everything that I need to my 11.04 machine, which worked quite a lot.

SInce the driver support is better on my 10.04 and I configured everything there already, I primaly use it as a sandbox environment for a website. Apache, Perl, internal interface etc, etc ... everything was running fine, I just missed the MySQL server, and since I don't want to re-write lots of code when the site goes productive with additional database support, I wanted to download the 64 Bit packages for 10.04. Unfortunaly, when I try to apt-get download the MySQL packages, I will only get the stuff for 11.04 32 Bit, and I don't know how to give apt-get the order to search for 10.04 packages only. There are lots of descriptions how to install 32 Bit packages on 64 Bit Linux, but not a single line about how to force apt-get to download THIS VERY PACKAGE for THIS VERY PROCESSOR.

Would be nice if you'd ditch me in the right direction - also it'd be good to know that I am using Ubuntu for about only a year, I am getting the idea, but am not a pro whatsoever.

---

### Post by iponeverything on 2012-04-07
There should be other options for getting network access.

usb wireles device for one..

---

### Post by MyTorAndMe on 2012-04-07
A considerable option, if I just had one. But neither W-LAN card nor USB device is available/in my possession. :(

---

### Post by wallaroo on 2012-04-07
You could just go to [http://packages.ubuntu.com/lucid/database/](http://packages.ubuntu.com/lucid/database/) and download the packages you need.

---

### Post by MyTorAndMe on 2012-04-07
First rule in the internet - if it's somehow accessable, you also can do it manually. That's what I needed - thanks, my friend. I guess the rest will work for dpkg.

---

