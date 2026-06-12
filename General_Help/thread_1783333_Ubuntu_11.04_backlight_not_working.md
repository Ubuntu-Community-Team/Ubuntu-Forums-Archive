---
title: "Ubuntu 11.04 backlight not working"
date: 2011-06-15
forum: General Help
---

### Post by fuzzisninja on 2011-06-15
I updated  ubuntu from 10.10 to 11.04 and once i had restarted my laptop the  backlight doesnt work and i have checked everything that would say if  the backlight works and its says its on full (i have to shine a light on  the screen) i have an acer aspire 5332 and ubuntu is dual booted with  windows 7 if anyone can help i would be grateful 
 
Thanks

---

### Post by FormatSeize on 2011-06-15
I found this in another thread by someone having your problem:
> **l3vity said:**
> I have the exact same problem, it's some kind of error with the latest kernel from what I can tell.
You have 3 options from what it seems,
 
1. Use something like a flash on a camera to open up terminal and type
 
```
sudo setpci -s 00:02.0 F4.B-0
```2. When booting select a different kernel to use. If you instantly auto-boot into the latest, pressing SHIFT while grub loads will open the menu. I am currently using the oldest kernel, which works fine.
 
3. Use a cable to connect to an external monitor.
 
I'm a complete ubuntu noob (my first ever udgrade) but have found these various solutions around the internet.
 
EDIT: Have now found a way to include the setpci code into boot.
 
select another kernel to boot so you dont have to mess around with the camera then...
```
gksudo gedit /etc/rc.local
```
this will probably be blank except some comments and an EXIT 0 at the bottom. Between the comments and the exit line, add
```
setpci -s 00:02.0 F4.B-0
```
 
You should now boot, after grub the backlight will go out, but should turn back on before log in.
 
See if any of those help.

---

