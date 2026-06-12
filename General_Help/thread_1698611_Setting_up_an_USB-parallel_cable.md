---
title: "Setting up an USB-parallel cable"
date: 2011-03-02
forum: General Help
---

### Post by kondocarpo on 2011-03-02
Hello, readers!

I'd like to connect a parallel port printer to my new desktop and have got a Connectland C36 cable that shows up as:

Bus 003 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port

I've tried the URI /dev/usb/lp0 but I don't mange to set the printer working. May I need any driver?...

---

### Post by drdos2006 on 2011-03-02
You need a parallel printer cable from your parallel port to your parallel printer. Turn your printer on.

Go to your desktop toolbar, click on System -> Administration -> Printing.

Select Add -> LPT #1 and allow Ubuntu to find the drivers for your printer.

regards

---

### Post by kondocarpo on 2011-03-03
Thanks for the answer, but I cannot choose LPT #1. Only serial ports appear.

---

### Post by drdos2006 on 2011-03-03
In that case you may need something like this, or do you already have one ?

[http://www.jaycar.com.au/productView.asp?ID=XC4847&keywords=parallel&form=KEYWORD](http://www.jaycar.com.au/productView.asp?ID=XC4847&keywords=parallel&form=KEYWORD)

regards

---

### Post by kondocarpo on 2011-03-04
The cable I'm trying to use is this one:

[http://www.connectland.eu/products/fiche/id/33/name/cable-adaptateur-usb-imprimante-c36/culture/en](http://www.connectland.eu/products/fiche/id/33/name/cable-adaptateur-usb-imprimante-c36/culture/en)

---

### Post by drdos2006 on 2011-03-04
That cable should be OK.

Ubuntu should be able to find your printer when you Add a Printer.
Are you able to post a screenshot of what you get when you add a printer at the "Select Device" screen ?

regards

---

### Post by kondocarpo on 2011-03-05
That's what I get: two serial ports, "other", and network printers. Selecting "other" leads to an input dialog for "URI", where I type "parallel:/dev/usb/lp0", with no printing success.

---

### Post by drdos2006 on 2011-03-05
When you type

sudo lshw | grep usb

can you see usb at all ?

If so then your printer is not being seen by Ubuntu.
It may be the cable is not connected to the printer, or your printer is not switched on, or Ubuntu does not recognize the chipset in the printer.

regards

[edit]
Try  using CUPS to connect to the printer.
From your browser, type
[http://localhost:631/admin](http://localhost:631/admin)
and see if you can add from there.

[/edit]

---

### Post by kondocarpo on 2011-03-06
Yes, I find several USB controllers but no printer. I couldn't either set up the printer through CUPS. Thanks for your help anyway!

---

