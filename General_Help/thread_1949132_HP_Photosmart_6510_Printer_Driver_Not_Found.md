---
title: "HP Photosmart 6510 Printer Driver Not Found"
date: 2012-03-29
forum: General Help
---

### Post by sousedpoet on 2012-03-29
Hello all,

I just got a new Dell XPS 15 and I am dual booting Ubuntu and Win7.  The installation and everything went great on WIN7.  The only problem I am having now is that I can not install my printer on Ubuntu.

I am using a HP Photosmart 6510.  I tried adding the printer through the Control Panel, it found the printer on the network, but when I tried to connect the two, it searched for a driver and none was found.  I have used the HPLIP and Cups, which according to the website, [supports my printer version]("http://hplipopensource.com/hplip-web/models/photosmart/photosmart_6510_series.html"), however when I use the drop-down menu to find the appropriate driver, mine is not listed.  It is almost as if the entire 6000 series of HP printers are left out of the list.  I have also connected the printer via USB, but still no luck.

Any advice?

Thanks in advance.

---

### Post by Mark Phelps on 2012-03-29
OK, I have an 8510 which is probably a similar process ...

First, in Win7, you install it ONLY by using the CD that came with it.  You don't use Control Panel in Win7 to install the printer.

Second, at least in the case of my printer, you can't have it connected to BOTH the network and a USB cable, you have to pick one or the other.

Third, to install in Linux, use CUPS.  You do that by opening a browser and entering "localhost:631".  Then, when that opens, use the option to add a printer.  When you choose network printer, you should see your printer listed and only have to select it.

---

### Post by sousedpoet on 2012-03-29
> **Mark Phelps said:**
> OK, I have an 8510 which is probably a similar process ...

First, in Win7, you install it ONLY by using the CD that came with it.  You don't use Control Panel in Win7 to install the printer.

Second, at least in the case of my printer, you can't have it connected to BOTH the network and a USB cable, you have to pick one or the other.

Third, to install in Linux, use CUPS.  You do that by opening a browser and entering "localhost:631".  Then, when that opens, use the option to add a printer.  When you choose network printer, you should see your printer listed and only have to select it.

Everything set up fine win Win7.

I tried using CUPS and went through that whole process but it still could not add the printer.  It is almost like it skips my series.
[IMG]http://i.imgur.com/f6xfQ.png[/IMG]

---

### Post by Azdour on 2012-03-30
Hi,

When I install any HP printer I open the terminal and use:

```
hp-setup
```

Hopefully this will set-up and download the correct driver for your printer.

---

