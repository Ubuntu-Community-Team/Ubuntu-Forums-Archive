---
title: "Dialup trouble"
date: 2006-03-10
forum: General Help
---

### Post by kaaawa on 2006-03-10
How does one connect to the internet using dialup?  Modem is a Lucent technologies Soft Modem AMR on Com3 in Windows.  It's an internal on my laptop.

---

### Post by OscarGortez on 2006-03-11
You have to find the chipset for the modem, then download the driver for that modem and install it in linux... I really wish i could give you links and more details... but basically when i went through it all i learned there's modems and win-modems... win-modems make the software do most of the work... unfortunaltely it's meant for windows software so it doesn't run so hot in linux... now if you're lucky you'll find a driver for linux fine... it might be free... or you might have to pay for a key to activate it... which is a bitch i know, in my case I could only run at 14.4 speeds and had to purchase a key to get the full speed....

I eventually just said screw it and connect to the internet through another coputer running windows... and i get my full speed for free :-) which would also help you with your problem if you can run a network like that... *shrugs*

---

### Post by Bentu on 2006-03-11
Winmodems work just as well for me in linux as they do in windows. I have other posts that give more details, basically you just need to install the correct driver and use wvdial to connect. Then you can download and install KPPP, if you want to use that. It's easy once you've done it, I have three machines using winmodems on dial-up. Check out my other posts.

Here is the modem that I have:
Agere Systems (formerly Lucent) LT Winmodem Lucent/Agere DSP Mars or Apollo chipset
I am using it right now with the 2.6 kernel, it's your basic, dreaded "winmodem," and it works fine. If you're having trouble it's because of your driver, the one below configures everything when installed, avoid suffering through all the convoluted instructions and buying more hardware. Just download, untar, run, enter your isp's settings and surf the web. If the one below doesn't work, this site has many more, just get similar that will do the configuration (if the one below doesn't work for you) and be done with it. Avoid those drivers that don't do the configuration, if at all possible, they're too much hassle.

Link to driver:
[http://linmodems.technion.ac.il/pa](http://linmodems.technion.ac.il/pa)
ck...-8.26b1.tar.gz

---

### Post by kaaawa on 2006-03-11
My modem seems to be fine.  I can activate it, but I don't know how to dial a connection.  It is for a normal IP provider so I should just need their number and login/password I think.

---

### Post by jerrykenny on 2006-03-11
sudo pppconfig


will launch a program to input your details

you can start your connection with

sudo pon

or turn it off with 

sudo poff

a nice touch is a launcher on your toolbar with the following command

gtksu pon

which will then ask you for your password before making the connection.

---

### Post by towsonu2003 on 2006-03-11
check out the second link in my signature. I use wvdial, which is toward the bottom of that page.

---

