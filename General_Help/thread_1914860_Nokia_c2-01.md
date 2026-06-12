---
title: "Nokia c2-01"
date: 2012-01-25
forum: General Help
---

### Post by bryncoles on 2012-01-25
Greetings fellows!

I recently got a new Nokia c2-01 phone.  My previous Nokia 6300 could simply mount as a drive when I plugged it in.  However, this c2-01 doesn't seem to want to play that way.  

When I type ```
lsusb
```The Nokia is visible.  It just wont mount for browsing.  Note that I have tried Gammu and Wammu to no effect.  I'm not trying to connect to the internet through the phone (that works fine) -- I just want to browse the phones file system.  

Any and all suggestions welcome!

Cheers guys.

---

### Post by raja.genupula on 2012-01-25
Hi man , when you connect your phone to System with USB , it will ask you to choose the mode , at that give as mass storage . 

To use that mobile for internet , make sure that you got right access point .What sim you're using there ?

---

### Post by bryncoles on 2012-01-25
S'up raja.genupula.  

We can ignore the mobile internet -- that works fine if I select 'Nokia pc suite' when I plug in the phone (though that doesn't mount the drive).  The other options are 'printing and media', which doesn't allow me to browse the file system, and 'data mode' which asks me to insert a memory card.  On the previous phone I had (the 6300), selecting 'data mode' allowed me to browse the phones internal storage.  

I'm using a cable to plug it in cause this laptop doesn't have bluetooth!

Oh -- and the sim is t-mobile (for all that's worth).

*** edit***

the output of ```
lsusb
```is```
Bus 006 Device 004: ID 0421:054d Nokia Mobile Phones
```The '054d' part changes between '054b' and '054c' depending on whether I'm in 'pc suit', 'printing and media' or 'data' modes

---

### Post by raja.genupula on 2012-01-25
when you select that mode then it shows you a window with 3 options .do nothing & one option is with your image manager and one option with open folder .you choose open folder option that will allows to look for the internal storage .

So are you getting any window like that? ?

---

### Post by raja.genupula on 2012-01-25
ok i got this 

[http://sourceforge.net/projects/nokuntu/](http://sourceforge.net/projects/nokuntu/)

A ubuntu managed nokia PC Suite . 

I hope that will help you .

---

### Post by bryncoles on 2012-02-02
*Red faced*

It turns out if I plug my phone it, select storage and media and fire up 'Gigalo', that browses my phone fine!  

Mistake I made was expecting to use Thunar!

Thanks for all your help though dude!

---

### Post by Harix on 2012-09-20
Want to connect my Nokia C1-01 by usb cable to transfer pictures to laptop and installed Gigolo.. (not Gigalo).
When I open Gigolo, the phone is not in the list of devices, only my harddrive shows up.
Anyone an idea how to mount the phone?
Thanks!

---

