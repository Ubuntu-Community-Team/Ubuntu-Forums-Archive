---
title: "Botched attempt to upgrade Gutenprint?"
date: 2012-01-01
forum: General Help
---

### Post by W. James MacLean on 2012-01-01
Hi,

I tried to upgrade my 10.04 LTS machine from Gutenprint 5.2.5 (stock installation) to 5.2.7 (built from source), but the printer I'm trying to support (Epson Stylus Pro 3880) isn't working.

I downloaded Gutenprint 5.2.7 and compile/installed from source. As best I can tell everything went without errors. I am also able to get it to detect and install the printer, but when I try to print a test page, it says its working, but after a long period of inactivity I get the message that the job has failed.

/usr/lib/cups/backend/lpd failed

I'm not sure where to start looking to debug this.

---

### Post by dspisak on 2012-05-11
Hello.

Did you solve your problem?  I would like to buy a 3880, but there appear to be no Linux drivers.  I sent an e-mail to Avasys who used to develop Linux drivers for Epson.  They have not yet responded.  They turned-over their stuff to Epson earlier this year.  There seems to be no other information on the 'net.

FWIW, Linux drivers for the R3000 are available on the Epson website.  They work quite well.

I called Epson tech. support about 3880 drivers the other day.  They responded that there will be no Linux drivers for the 3880.

I considered using the 3800 Linux driver, but I understand it is not compatible with the 3880.  Have you tried the 3800 driver (pips-3.0-1.src.rpm)?

Dan

---

