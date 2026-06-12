---
title: "HP Printer Drivers."
date: 2006-03-20
forum: General Help
---

### Post by youngerpants on 2006-03-20
Hi All,

Firstly, I'd like to say how impressed I am with Ubuntu. I've been using Red Hat on servers for years, but I'm converted (apt is everything I ever hoped it would be).

Anyway, I've got Breezy Badger set up on a spare desktop and I have an HP psc 2410 all-in-one printer that I cant print to. Ubuntu picks up the device when I plug in the USB so I can access its SD card, but I cant set it up as a printer as the drivers aren't available.

I've done a bit of googling around and tried a few alternative drivers, but non of these have worked so far. Can anyone recommend a method of getting my printer printing?

Much appreciated.

---

### Post by cilynx on 2006-03-20
According to [http://hpinkjet.sourceforge.net/productsmf.php](http://hpinkjet.sourceforge.net/productsmf.php) your printer is supported by HPLIP, the official HP drivers. 
```

sudo apt-get install hplip

```
When you go to install the printer, make sure you choose the manufacturer to be HPLIP as opposed to normal HP.  The driver works beautifully.  I have a Photosmart 2575 and an Officejet 5610 running fully supported like a dream.  Check out hp-toolbox once you've got it up and running.

---

### Post by youngerpants on 2006-03-21
Thanks Cilynx, I'll give that a try!

Edit... works like a charm. TYVM

---

### Post by youngerpants on 2006-03-21
Back again, sorry...

Printing is working fine as a stand alone box, however, when I try to add the printer to an XP box (using CUPS), I can find the printer via a url ([http://192.168.0.51:631/printers/hp-psc-2400](http://192.168.0.51:631/printers/hp-psc-2400)) but I'm getting asked for a driver, which predictably doesnt exist.

My cups.conf is a copy of [http://gerona.gov.ph/davidjr/?p=57](http://gerona.gov.ph/davidjr/?p=57) if that helps at all.

Thanks again

---

### Post by braddcadd on 2006-08-03
Does anyone have a fix (work around) for this?  I am having the same trouble.

Thanks.

---

### Post by cilynx on 2006-11-20
This is CUPS trying to be nice in the Windows world.  CUPS is used to Linux printer drivers sucking.  Because of this fact, CUPS will take a back seat to you Windows machine's printer driver if it's available.  You can grab the Windows driver off of the CD that came with your printer or from the HP website.  Once you have the driver setup on you Windows box, CUPS will just send the data to the printer without processing it itself.  In theory, using this system, you can use Linux to host a completely unsupported printer so long as you have drivers on all of your clients.

The other option (and the one I generally go with as I have very few Windows machines and have well supported printers) is to just tell Windows that the network printer is an HP Laserjet 4 (no matter what it really is).  The LJ4 speaks simple postscript so using that driver, your Windows box will throw postscripts down the line.  Being that postscripts is a nice standard, CUPS will process it flawlessly, convert it to printer code with the Linux driver, and spool it off to the hardware.

---

