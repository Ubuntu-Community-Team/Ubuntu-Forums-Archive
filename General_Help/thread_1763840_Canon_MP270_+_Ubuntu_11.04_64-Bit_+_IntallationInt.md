---
title: "Canon MP270 + Ubuntu 11.04 64-Bit + Intallation/Integration"
date: 2011-05-20
forum: General Help
---

### Post by _1MoreDay_ on 2011-05-20
Hello, 

Canon does not offer any 64bit driver version for this Printer/Scanner, so I need to get the 32-Bit working.

I've downloaded 2 drivers for the Printer and Scanner
[http://www.canon.de/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP270.aspx?type=download&page=1](http://www.canon.de/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/MP270.aspx?type=download&page=1)

I followed the install instructions provided inside the Canon Guide, but I get the message that my Architecture does not match (that's right, because I'm trying to get the 32-Bit running on my 64-Bit)

```
Execution command = sudo dpkg -iG ./packages/cnijfilter-common_3.20-1_i386.deb
dpkg: error processing ./packages/cnijfilter-common_3.20-1_i386.deb (--install):
 package architecture (i386) **does not match system (amd64**)
Errors were encountered while processing:
 ./packages/cnijfilter-common_3.20-1_i386.deb
root@ubuntu:/home/trance/cnijfilter-mp270series-3.20-1-i386-deb# 
```
**[COLOR=Blue]How to force the system using the 32-Bit version? [/COLOR]**

---

### Post by linuxinstalledfromhdd on 2011-05-20
It would be better to install a 32-bit version of Ubuntu and then install that kind of printer. 

I had the same problem with a cannon a while back, to save you some time.

---

### Post by _1MoreDay_ on 2011-05-20
> **linuxinstalledfromhdd said:**
> It would be better to install a 32-bit version of Ubuntu and then install that kind of printer. 

I had the same problem with a cannon a while back, to save you some time.

Thats right, or I just could order a new Printer with a Linux friendly Service like- HP, Brother, etc, etc :D

But, I think it is doable to make it work here

---

### Post by linuxinstalledfromhdd on 2011-05-20
It may or may not be doable. It would be better to go with whatever works, so that's why I am suggesting that you try installing a 32bit version of Ubuntu so that your 32-bit drivers will work with it.  Of course, their may be a workaround, but do you really want to spend the time doing that for every driver you need to install in the future as well? That's up to you the end user.

---

### Post by _1MoreDay_ on 2011-05-20
> **linuxinstalledfromhdd said:**
> It may or may not be doable. It would be better to go with whatever works, so that's why I am suggesting that you try installing a 32bit version of Ubuntu so that your 32-bit drivers will work with it.  Of course, their may be a workaround, but do you really want to spend the time doing that for every driver you need to install in the future as well? That's up to you the end user.


In fact, it is a "huge waste" of time if you delete a whole system just because you cannot fix one new upcoming problem with one single device. :D

But there is a fix, i just can't remember how to :P

---

### Post by linuxinstalledfromhdd on 2011-05-20
No it doesn't that long in fact.  I have a file server here and I do a LAN network installation for any computer on our network in less than 10 minutes. Everytime.  10 minutes to switch to 32bit.. Or hours each time you want to play around with a 64-bit system and "force" 32-bit drive to function properly.  They may never too.

---

### Post by _1MoreDay_ on 2011-05-21
> **linuxinstalledfromhdd said:**
> No it doesn't that long in fact.  I have a file server here and I do a LAN network installation for any computer on our network in less than 10 minutes. Everytime.  10 minutes to switch to 32bit.. Or hours each time you want to play around with a 64-bit system and "force" 32-bit drive to function properly.  They may never too.

Yes thats right, I can do this too, but then I am stuck with a fresh installation, without personal tunings and extras, so it takes hours to reinstall a whole new system with all applications and  to fine tune this. Without a restore  from backup procedure, or course. Almost everybody puts days of work into it, to  make their system work like it should - may weeks or even months. Every  system grows week by week. And the more it grows the more your theory falls back.

Thanks for the little side-communication, now please back on the topic?

---

### Post by linuxinstalledfromhdd on 2011-05-21
Not all 32-bit drivers are going to install on 64-bit Ubuntu. 64-bit Ubuntu isn't even recommended yet for prime time.  Goodluck with forcing it to work though.

---

### Post by _1MoreDay_ on 2011-05-21
> **linuxinstalledfromhdd said:**
> Not all 32-bit drivers are going to install on 64-bit Ubuntu. 64-bit Ubuntu isn't even recommended yet for prime time.  Goodluck with forcing it to work though.

Thank you, let's see what happens.

---

### Post by BicyclerBoy on 2011-05-21
The Canon 32 bit drivers work fine on *buntu 64 10.04 10.10.
(so does 64 bit *buntu since 8.04 at least..)
 
Can just edit the canon install scripts to add "force-architecture" into one line with dpkg command...

Edit the both installer scripts (printer & scanner).

Have used this MP270/272 printer-scanner with 64 bit *buntu for couple years...

Canon also provide the source code..so you can compile 64 bit drivers..this works as well.
The driver install/compile documentation is very good. (IMO)

---

### Post by _1MoreDay_ on 2011-05-21
I've tried 
```
root@ubuntu:/home/trance# sudo dpkg -i --force-architecture '/home/trance/cnijfilter-mp270series-3.20-1-i386-deb' 
 
```Normally, it should run the printer registration, but it didnt


It opens the Package and shows the folder, plus the info in the Terminal 
[COLOR=Blue]
==================================================

Canon Inkjet Printer Driver Ver.3.20-1 for Linux
Copyright CANON INC. 2001-2009
All Rights Reserved.

==================================================
Execution command = sudo dpkg -iG /home/trance/cnijfilter-mp270series-3.20-1-i386-deb/packages/cnijfilter-common_3.20-1_i386.deb
[sudo] password for trance: [/COLOR]


When I enter the password, the terminal exectutes the command and closes, but nothing happens then. 

What's wrong here?





.

---

### Post by linuxinstalledfromhdd on 2011-05-21
BUMP  (64 bit system needs 32-bit drivers installed)

---

### Post by _1MoreDay_ on 2011-05-21
> **linuxinstalledfromhdd said:**
> BUMP  (64 bit system needs 32-bit drivers installed)

I have installed this already

```
sudo apt-get install ia32-libs
```[COLOR=Blue][/COLOR]

---

### Post by linuxinstalledfromhdd on 2011-05-21
Theoretically that might have helped, still it is a forcing a driver to work in 64-bit system. Someone would still need to write up a whole new way of installing for you.

---

### Post by _1MoreDay_ on 2011-05-21
> **linuxinstalledfromhdd said:**
> Theoretically that might have helped, still it is a forcing a driver to work in 64-bit system. Someone would still need to write up a whole new way of installing for you.

That's simply wrong. Not a whole new way. 98% has been tested and published. The informations need to be updated as everything improves. Thats it :) Getting 32-bit applications running inside a 64-bit environment is as normal as getting very old 32-bit applications running in brand new 64-bit systems :) But there are people complaining, and there are those trying to fix.

.

---

### Post by _1MoreDay_ on 2011-05-21
Canon MP270 + Ubuntu 11.04 64-Bit + Intallation/Integration

Its working - going to update the first posting in the Thread - then its SOLVED

---

### Post by BicyclerBoy on 2011-05-21
Good for you...

The canon.au site has the driver package with an install script..
[http://support-au.canon.com.au/contents/AU/EN/0100236202.html](http://support-au.canon.com.au/contents/AU/EN/0100236202.html)

This script can be edited (~ line 1359) to add --force-architecture command option..
Then it is easy to re-use later if necessary..

This script deals with the CUPS printer reg stuff..
The build/installation readme file, in the source package is very informative..

---

### Post by _1MoreDay_ on 2011-05-22
> **BicyclerBoy said:**
> Good for you...

The canon.au site has the driver package with an install script..
[http://support-au.canon.com.au/contents/AU/EN/0100236202.html](http://support-au.canon.com.au/contents/AU/EN/0100236202.html)

This script can be edited (~ line 1359) to add --force-architecture command option..
Then it is easy to re-use later if necessary..

This script deals with the CUPS printer reg stuff..
The build/installation readme file, in the source package is very informative..

Thank you BB for the Link and info!

Going to test this script aswell tomorrow. The Canon support team is always willing to help. With this said, a message to the Canon Support team helps and they do not let the support fall back.

---

### Post by kkjaergaard on 2011-07-31
> **_1MoreDay_ said:**
> ...I've downloaded 2 drivers

I use Ubuntu 11.04 64 bit, and my system was able to configure and print the test page without installing Canon's drivers.

---

