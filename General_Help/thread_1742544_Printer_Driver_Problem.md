---
title: "Printer Driver Problem"
date: 2011-04-29
forum: General Help
---

### Post by paranoidandroid42 on 2011-04-29
Recently installed Ubuntu. Absolutely love it, everything just makes sense! Had a lot of fun setting up a nifty Cairo Dock UI, and my Network Drive. But my printer is posing some problems.

The model is Canon Pixma iP1700, though I think drivers for a 1500 or 2200 have worked for others.

I've found and tried a few different techniques but I always get an error in "libcupsys2"

Error Print:
 pstocanonbj : Depends: libcupsys2 (>= 1.2.3)
               Depends: cupsys but it is not installable


Now I got this error when following these directions:
[http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/](http://choxblog.wordpress.com/2007/06/09/printer-pixma-ip1700-has-been-running-now/)

But I get the same thing no matter which method I use. My cups library is up to date, reinstalled, and as far as I can tell in pristine condition. 
I'm thinking an updated transition package would do it... or perhaps someone could tell me which links need to be made? Or maybe It's something else?

---

### Post by paranoidandroid42 on 2011-04-29
Tried this:

sudo ln -s libcupsys2 /usr/share/doc/libcups2

Didn't work.

---

### Post by paranoidandroid42 on 2011-04-29
[http://all-about-ubuntu.blogspot.com/2008/12/canon-ip1880-ip1700-ip1980-printer.html](http://all-about-ubuntu.blogspot.com/2008/12/canon-ip1880-ip1700-ip1980-printer.html)

This driver works. I can find the printer from the Printer app, but it still won't print.

Ok so this one again has a libcupsys2 dependency as well as some other broken dependencies.

EDIT
Well I think possibly the problem is that these are compiled for i386 and I have i686?
I'm at a total loss here, please help!

---

### Post by lupas on 2011-04-29
I have a similar problem. Whenever i upgrade from one version to another my printer Canon Ip1800 do not work. Can someone illuminate me to how to solve this problem. 
This is the only thing that hold me to switch forever to Ubuntu from WInd.

---

### Post by paranoidandroid42 on 2011-04-30
Well don't switch yet! Someone will help us...

*bump*

---

### Post by lupas on 2011-04-30
> **paranoidandroid42 said:**
> Well don't switch yet! Someone will help us...

*bump*


I really hope so

---

### Post by paranoidandroid42 on 2011-04-30
Well I'm not an expert but I think updating to the 11.04 distro might be worth a shot. Just after I got 10.10 installed too! =(

---

### Post by lupas on 2011-05-01
Right now i am on 11.04 and it is the best one. There are so many changes. You should try this version. Everything is working well but of course the printer do not print anything. I have to boot into Windows to print a file .

---

### Post by paranoidandroid42 on 2011-05-01
Yeah I have a 100gb hard drive but no Sata Cable for it. So the cables in the mail and as soon as that works I'll just use Windows for the printing... So it goes

Downloading 11.04 soon, I don't want it to interfere with the transfer of my music onto the new hard drive. 100gb transfer, taking forever =D

I'll just learn what I can and come up with my own fix I suppose!

---

