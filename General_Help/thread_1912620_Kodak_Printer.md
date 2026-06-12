---
title: "Kodak Printer"
date: 2012-01-21
forum: General Help
---

### Post by UltimateCat on 2012-01-21
Sorry if this post  belongs in Installation but I wasn't sure.

I have read through the Community Documentation and my printer ( Kodak ESP 7) wasn't listed in the supported printers.

I would hate to have to purchase a new printer.

Is there another way to get Ubuntu to recognize my printer?:(

Help is always appreciated....Thanks in advance

---

### Post by satanselbow on 2012-01-21
If you are on 11.10 then the c2esp kodak printer driver is in the software center or can be installed in a terminal with 

```
sudo apt-get install c2esp
```

Earlier versions will need the driver from here: [http://sourceforge.net/projects/cupsdriverkodak/files/](http://sourceforge.net/projects/cupsdriverkodak/files/) and install the appropriate deb.

*** Manual download may the the better option as the repo version is now quite old (ie v18 current = v23) - gonna upgrade mine now : ***

To install the downloaded deb just right click and choose "install with Gdebi" ;)

This driver does not currently support scanning - although it looks like it is under active dev at the mo ;)

Works well over wireless on my ESP 5250 - which is the same series/driver.

---

### Post by paulnewall on 2012-01-21
The main difference between version 18 and 23 is just the support for the newer printers like C110 and the Hero series.
So with ESP 7 or ESP 5250 there's not much advantage in upgrading

---

### Post by t0p on 2012-01-21
I own a HP Deskjet D2660 printer, which won't work with Ubuntu even though it's supposed to (grrr...).  My solution is to run XP in VirtualBox.  When I do so, the printer thinks it's dealing with a computer running XP, and everything is (so far) hunky-dory.

---

### Post by satanselbow on 2012-01-21
> **paulnewall said:**
> The main difference between version 18 and 23 is just the support for the newer printers like C110 and the Hero series.
So with ESP 7 or ESP 5250 there's not much advantage in upgrading

Cheers Paul,

I'm not known for reading update log :popcorn: :popcorn: Thanks for the good work as ever ;)

---

### Post by satanselbow on 2012-01-21
> **t0p said:**
> I own a HP Deskjet D2660 printer, which won't work with Ubuntu even though it's supposed to (grrr...).  My solution is to run XP in VirtualBox.  When I do so, the printer thinks it's dealing with a computer running XP, and everything is (so far) hunky-dory.

I still rdp into a local XP machine for scanning - couldn't get that to play nice in vbox :(

---

### Post by UltimateCat on 2012-01-22
You 2 are funny!

I'll go to the sourceforge.net and see what happens.
Hope it works

I'll mark this solved when I get my printer working today-

Thank You:D

---

