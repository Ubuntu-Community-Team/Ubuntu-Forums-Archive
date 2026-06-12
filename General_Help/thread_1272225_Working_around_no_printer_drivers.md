---
title: "Working around no printer drivers"
date: 2009-09-21
forum: General Help
---

### Post by levells on 2009-09-21
I've spent a few hours on google trying to find drivers or .ppd files for my Lexmark X7675 and Brother MFC-240C printers with no success.
Is there some way I can still print from them without booting back to Windows?  I really don't want to use a Virtual Machine for numerous reasons, but I think that might be the only option available in Ubuntu.  I would appreciate suggestions on other ways this could be done.
This issue is the one of very few reasons I'm still dual-booting Windows.

---

### Post by bogdan.veringioiu on 2009-09-22
Hi.

Did you try with generic Postscript driver?
Bogdan

---

### Post by Bucky Ball on 2009-09-22
[https://help.ubuntu.com/community/Printers#Supported%20Printers](https://help.ubuntu.com/community/Printers#Supported%20Printers)

---

### Post by ianmillington on 2009-09-22
searching [www.openprinting.org](www.openprinting.org) suggests that people have got the Brother printer working.

[http://www.openprinting.org/show_printer.cgi?recnum=Brother-MFC-240C](http://www.openprinting.org/show_printer.cgi?recnum=Brother-MFC-240C)

The driver appears to be here

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-240C](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-240C)

Good luck!

---

### Post by plucky on 2009-09-22
Try **Synaptic Package Manager** and search for MFC-240C yields ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
```

Install both and then "add new printer" with printer powered on.

Don't know about the lexmark

Good Luck

---

### Post by P4man on 2009-09-22
> **plucky said:**
> Try **Synaptic Package Manager** and search for MFC-240C yields ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
```

Install both and then "add new printer" with printer powered on.

Don't know about the lexmark

Good Luck

Just for the record: to find those drivers in synaptic, you have to enable the multiverse repository in software sources.

As for the lexmark: probably not possible. Lexmark support for linux is nonexistant, and precious few, if any, lexmark printers work (with linux). If you intend to stick with ubuntu, id say put it on ebay and look for a printer from a vendor that does support linux. HP is good.

---

### Post by bogdan.veringioiu on 2009-09-22
I have a Lexmark T430 model, networked, working with generic Postscript driver.
Cheers.

---

### Post by levells on 2009-09-22
Thanks guys, I finally got the Brother.

---

### Post by i.r.id10t on 2009-09-22
Since Macs use CUPS as well for printing, you may be able to grab the appropriate PPD file for OS X and be able to manually install it.

---

