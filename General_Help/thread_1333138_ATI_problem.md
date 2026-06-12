---
title: "ATI problem"
date: 2009-11-21
forum: General Help
---

### Post by sadi2009 on 2009-11-21
Hey guys... I m using Kubuntu 9.10 for sometime... it is going well but one thing is bothering me... my graphics card is ATI Radeon 9200se... its performance in Kubuntu is very poor... the 3D games are slow and sluggish and my KDE environment seems to be slow also...

If you guys can tell me where I can find the driver of this graphics card ?!? or how to solve my problem I will be very glad...


Tc.:)

---

### Post by realzippy on 2009-11-21
Older ATI cards are not "well" supported since 9.04.
The best 3D performance for your card is to install Ubuntu 8.10
and the fglrx ATI driver.

---

### Post by 3rdalbum on 2009-11-21
> **realzippy said:**
> Older ATI cards are not "well" supported since 9.04.
The best 3D performance for your card is to install Ubuntu 8.10
and the fglrx ATI driver.

Note: It must be the older version of the fglrx ATI driver from [www.ati.com](www.ati.com). The new versions of the driver don't work with your card.

If you're using a desktop PC, you could get a different graphics card. If it has a PCI-E slot, then any modern card will do as long as you have a powerful-enough power supply. I recommend Nvidia cards. If your PC only has an AGP slot, then you are limited to the new ATI AGP cards made by PowerColor.

---

### Post by sadi2009 on 2009-11-21
> **3rdalbum said:**
> Note: It must be the older version of the fglrx ATI driver from [www.ati.com]("http://www.ati.com"). The new versions of the driver don't work with your card.

If you're using a desktop PC, you could get a different graphics card. If it has a PCI-E slot, then any modern card will do as long as you have a powerful-enough power supply. I recommend Nvidia cards. If your PC only has an AGP slot, then you are limited to the new ATI AGP cards made by PowerColor.


Can please tell me from where I can get the driver..? It seems the ATI website is providing drivers for only 64bit systems but my system is 32bit... Please guys need your help...

---

### Post by realzippy on 2009-11-21
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.28.8.run)

...should be your driver.
If no luck (or lazy),install *envy* and let it do it for you:

[B]sudo apt-get install envyng-core
[/B]
Find it in Menue/Systemtools or start it in text mode:

**sudo envyng -t**

---

### Post by Mark Phelps on 2009-11-21
> **sadi2009 said:**
> Can please tell me from where I can get the driver..? It seems the ATI website is providing drivers for only 64bit systems but my system is 32bit... Please guys need your help...

There are no ATI drivers that will work with your card and the Xorg versions in Ubuntu 9.04 or newer. The newer drivers won't work with your card; the older drives with not work with the new Xorg versions.

Your only choices are to downgrade the Xorg to an older version or go back to Ubuntu 8.10 -- which has the older Xorg version.

---

### Post by realzippy on 2009-11-21
> **Mark Phelps said:**
> There are no ATI drivers that will work with your card and the Xorg versions in Ubuntu 9.04 or newer. The newer drivers won't work with your card; the older drives with not work with the new Xorg versions.

Your only choices are to downgrade the Xorg to an older version or go back to Ubuntu 8.10 -- which has the older Xorg version.


that he should already know.See thread.

---

### Post by sadi2009 on 2009-11-21
> **realzippy said:**
> [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.28.8.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8.28.8.run)

...should be your driver.
If no luck (or lazy),install *envy* and let it do it for you:

[B]sudo apt-get install envyng-core
[/B]
Find it in Menue/Systemtools or start it in text mode:

**sudo envyng -t**


I m in deep trouble now... I have installed the above driver using EnvyNG... after installing my Kubuntu starts at Console, and if I try to start the X server it doenst start... So I removed the driver using envy and rebooted my pc... now the problem is KDM starts but my Screen resolution and refresh rate is not like before (it was 1600*900 @ 60Hz before) and now it is 1024*768...

There is no option is the display menu for 1600*900 so I cant go beyond 1024*768...:(:(:(

---

### Post by jeb800e on 2009-11-21
..removed..

---

### Post by jeb800e on 2009-11-21
(Please read the second paragraph first. This will base your decision.)

Go to ATI.com and put in your "Component Category", "Operating System", "Product Line", and "Product Model information" under the "Download Drivers" section. Pretty much self-explanatory from there. Make sure you are downloading the RIGHT driver for the RIGHT card. 

Once your driver is installed, look for the program in your computer somewhere (probably within Applications < Other < ) and click on the icon. Go through the settings and make sure the refresh rate is set to a rate acceptable or safe for your monitor to run at. A rate too high or too low may permanent cause damage to your monitor. You can also search up online somewhere what the default refresh rate is for your graphics card and driver before you download and install the driver in the first place, just to make sure!

---

### Post by realzippy on 2009-11-22
> **jeb800e said:**
> Go to ATI.com and put in your "Component Category", "Operating System", "Product Line", and "Product Model information" under the "Download Drivers" section. Pretty much self-explanitory from there.

[COLOR="SeaGreen"]Please read thread before posting ;-)[/COLOR]

---

### Post by realzippy on 2009-11-22
> **realzippy said:**
> Older ATI cards are not "well" supported since 9.04.
The best 3D performance for your card is to install Ubuntu 8.10
and the fglrx ATI driver.


so did you install ubuntu [COLOR="Lime"]8.10[/COLOR] ??
If running [COLOR="Red"]9.10[/COLOR] of course this will not work...

---

### Post by 3rdalbum on 2009-11-22
For Christs' sake people, please read the thread carefully before posting. Now the poster has worse troubles than he/she started with.

---

### Post by jeb800e on 2009-11-22
Okay. I removed one of my posts to make it easier for you, and added on to my other post. Good luck! :)

---

