---
title: "Problems with Toshiba 2820c"
date: 2010-01-12
forum: General Help
---

### Post by klonschaf on 2010-01-12
Hey guys,

I just came up with Linux/Xubuntu so I hope you I hope you'll excuse my "noobishness".

I've Xubuntu 9.04 running on a laptop along with cups 1.3.9. 
I'd like to print on a toshiba 2820c which is connected to the local network. 
I tried to install it via localhost:631 what seemed to be working quite well since the toshiba is
automatically detected and the driver (according to the printers manuel it's the same as for 
the 4520c) is already included. So I finish the installation and whenever I try to print something
I am told that the job is sent and done but the printer doesn't even realise, that there was 
somebody trying to print something, at least there is nothing in the logs. 
I also tried to use the ppd-file from the toshiba-support but it failed again.

Can anybody please help me with CUPS or is there a different way to install the printer?
Thanks,
klonschaf

---

### Post by audiomick on 2010-01-12
Can you print a test page?

---

### Post by klonschaf on 2010-01-12
No, not even that. I get the message that the testpage is sent and done but nothing happens.

---

### Post by djchandler on 2010-01-12
Try changing the driver to CUPS+Gutenprint. The recommended first choice doesn't always work. 

You may want to try using the printer's host name in the device URL, i.e., socket://PRINTERHOSTNAME:631

If your printer uses HP PDL (not PostScript), you may need to use port 9100.

---

### Post by klonschaf on 2010-01-13
Okay, I gave it another try and it still doesn't work. I tried the cups+gutenprint driver (plus some others) and also replaced the ip in /etc/cups/printers.conf with the hostname. 
So far nothing new but one thing seems to be rather strange:
Using Linux I am not able to ping the printer with its hostname "printer", I am redirected to an external IP starting with 62.XXX.XXX.XXX but on a windows-computer it works perfectly.  Can anybody please explain this to me?

---

### Post by UAA on 2010-07-25
UPDATE:
now it's working with 4520c drivers and printing in colour too

OLD:
I've it working as this
TOSHIBA e-STUDIO850Series

but I realized that I can not print in colour. I'm searching for better drivers

and this location in the printer settings
socket://xxx.xxx.xxx.xxx:9100

but the CDs it came with has "4520cSeries" on it. I'll try it later God willing.

---

