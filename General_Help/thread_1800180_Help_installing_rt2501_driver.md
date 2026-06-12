---
title: "Help installing rt2501 driver"
date: 2011-07-08
forum: General Help
---

### Post by killakam on 2011-07-08
I am trying to install drivers from this page
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/) 
but when I run the make command I Keep getting this error. 

make[1]: Entering directory `/usr/src/linux-headers-2.6.32-32-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-32-generic'
rt73.ko failed to build!
make: *** [module] Error 1



I am dual booting my laptop running both Ubuntu 10.04.2 LTS and Windows7. Inside my laptop is an internal wireless card. I bought a TP-LINK TL-321G usb wireless card. I remember using it several months ago. 
I get the same result using sudo su. The driver I am trying to get is rt73-k2wrlz-3.0.3

Any advice please?

---

### Post by gandaran on 2011-07-08
are you having problems connecting to wireless? I believe the rt2501 chip works out of the box on ubuntu no need to install drivers, what version of ubuntu do you have?

---

### Post by Bucky Ball on 2011-07-08
Welcome.

In top directory? Get to you *untarred* directory with the driver in it, then;

```
sudo su
make
make install
```Is that what you're doing and not 'sudo make', 'sudo make install'? You need to 'sudo su' then give the commands. What driver are you trying to install exactly? What wireless card do you have? Have you plugged in an ethernet cable and gotten updates? Checked 'System>Administration>Additional Drivers'? Which Ubuntu release? Please try to include as much info as possible. ;)

---

### Post by killakam on 2011-07-09
Updates OP

---

### Post by killakam on 2011-07-11
No one has ever seen this before?

---

### Post by Bucky Ball on 2011-07-12
You didn't answer any of my questions from post #3 so little hard to help ya ....

---

