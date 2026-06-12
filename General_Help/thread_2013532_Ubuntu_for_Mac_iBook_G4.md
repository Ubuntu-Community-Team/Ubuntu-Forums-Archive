---
title: "Ubuntu for Mac iBook G4"
date: 2012-07-01
forum: General Help
---

### Post by rttch on 2012-07-01
I have an old iBook G4 and would like to pass it down to my daughter to play games and watch videos on Youtube.  Is there a Linux system that can play Flash on this machine?

Specs:
Machine Model:  iBook G4
CPU Type:  PowerPC G4 (1.2)
Number of CPUs: 1
CPU Speed:  1.2 GHz
L2 Cache:  512 KB
Memory:  768 MB
Bus Speed:  133 MHz
Boot ROM Version: 4.8.7f1

I'm not experienced at all with anything Linux, but have seen recommendations that Ubuntu, Debian, Yellow Dog and Mint PPC would be my workable options.

A direct download link (not sure if I have to get a certain version due to the iBook's age) would be greatly! appreciated as well as input about being able to use Flash.

Thanks (and sorry if I'm on the wrong website or forum to post my request).

---

### Post by lrcaballero on 2012-07-01
Have you tried booting of an Ubuntu 12.04 Live CD and take it for a spin on your iBook G4? Maybe you don't have to do nothing out of the ordinary!

---

### Post by rttch on 2012-07-01
No, I haven't tried anything yet.  I'm that much of a noob with Linux stuff that I wanted to ask before I do anything.  I'll get discouraged if it doesn't work and there is so much information with this specific model (I did google it first), that I'm not sure what my best approach would be with the stats of the iBook.

You think the Ubuntu 12.04 should work?

---

### Post by lrcaballero on 2012-07-01
Read this article:

[http://linuxclub.blogspot.com/2011/10/ubuntu-on-powerpc-ibook-g4.html](http://linuxclub.blogspot.com/2011/10/ubuntu-on-powerpc-ibook-g4.html)

hope this will clarify any doubts...Now, remember that when you run from a Live CD it doesn't touch your HDD there for you can play with it, make changes, install software, etc...without harming your system. have fun!

---

### Post by rttch on 2012-07-01
Absolutely wonderful and just what I need.  Thanks kindly and I will try this tomorrow and post an update :)

---

### Post by rttch on 2012-07-01
It downloaded and installed perfectly, but now I'm having a problem with access to my wireless internet.

I can't seem to install the broadcom b43 wireless driver and get the following message:

> please have a look at the logfile for details /var/log/jockey.log

I'm re-installing right now and am going to try and get the right driver on a usb drive to see if that will work.  I'm looking at [http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43") to see what I need to do.

---

### Post by SJPowell on 2012-07-31
I had the same issue.  Open up terminal and type in the following command:

sudo apt-get install firmware-b43-installer

It will ask for your root password and then install the drivers.  Works good, I'm using mine right now.

---

