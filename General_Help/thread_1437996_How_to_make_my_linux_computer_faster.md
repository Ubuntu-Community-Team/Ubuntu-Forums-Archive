---
title: "How to make my linux computer faster?"
date: 2010-03-24
forum: General Help
---

### Post by hockey97 on 2010-03-24
Hi, after installing ubuntu 9.10. It's now been a month or so from a fresh reinstall.

Currently for some reason at times my computer slows down where typing starts to lag.

Is there any software that would speed up the linux os. Like for windows there is softwares that would check the registery for errors and shortcut errors etc and fix them.

I use free software like that for windows and works well. I just would like to know if I can get something like that for linux. I know linux dosen't use a regsiter but just saying software that checks the linux system for any errors that could cause the computer to slow down.

---

### Post by lavinog on 2010-03-24
> **hockey97 said:**
> 
Currently for some reason at times my computer slows down where typing starts to lag.

This could be a driver issue...I am wondering if it is a video driver.

Can you post some info about your system?
lshw
lspci
lsusb
df
dmesg

also attach your /var/log/Xorg.0.log

---

### Post by Serpher on 2010-03-24
Linux doesn't slow down overtime like Windows. Somethings happed to cause this.

---

### Post by lavinog on 2010-03-24
Also sometimes something could be running in the background that is using more resources than it should.
try using htop in a terminal.

---

