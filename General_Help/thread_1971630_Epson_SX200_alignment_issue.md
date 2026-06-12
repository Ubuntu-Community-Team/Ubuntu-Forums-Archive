---
title: "Epson SX200: alignment issue"
date: 2012-05-02
forum: General Help
---

### Post by MrKappa on 2012-05-02
Since some couple of weeks I see a misalignment of colors issue printing with the Epson SX200 from my Ubuntu 64 bit OS (see the attachment).
It's very strange that I have no issue printing from the same pc from WinXP partition or from a direct copy.

I did some reset operations due to compatibility issue with cartridges and I suppose this problem has started with these its. 
I remember I ran the alignment utility from WinXp but nothing from Ubuntu.
I see the same problem from a second Ubuntu partition I have created for testing purposes.

Please, do you have any suggestion? It can be a driver issue? How can I recover it? Previously it was working fine... Thanks :confused:

---

### Post by MrKappa on 2012-05-03
Additional info: if copy without pc the result is good. It's only with Ubuntu that I have this problem. 
Is it alignment a printer parameter (stored in the printer)? 
Any suggestion?

---

### Post by swiftoid on 2012-05-06
I have the same problem. Does anyone know how to rectify this?

---

### Post by MrKappa on 2012-05-07
It seems we are not the only ones. There was a similar discussion:
[http://ubuntuforums.org/showthread.php?p=11774745](http://ubuntuforums.org/showthread.php?p=11774745)

Thanks to Cristian C. from Ubuntu.it forum.

---

### Post by MrKappa on 2012-05-07
The original solution using DX4800 was not working. I have luckily tried the one working with SX200:
Epson Stylus DX4850 - CUPS+Gutenprint v5.2.8-pre1

Anyway it's a problem started with Ubuntu 12.04 update.

Hope the developers will found how to fix it. Old versions of Ubuntu are ok.

---

### Post by swiftoid on 2012-06-23
If anyone is still stuck with this, just download the official linux epson driver and install it. Did the trick for me.

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Delete the printer from cups, then add it again. You should see two drivers listed for the sx200, select the ESC/P-R Driver (not the gutenprint one) and all should be fine.

---

### Post by degrootis on 2013-04-29
installing the deb package from that link on the epson website, solved my color alignment issues. thanks!

---

