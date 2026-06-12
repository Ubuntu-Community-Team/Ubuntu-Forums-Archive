---
title: "CUPS finds HP-3015 but will not print"
date: 2010-07-15
forum: General Help
---

### Post by walterbyrd on 2010-07-15
I am using Ubuntu 10.04. When I try to print a test page, nothing happens. 

CUPS found the printer right away, but it will not actually print.

I found a thread about this on linuxquestions.org, but that thread did not help.

[http://www.linuxquestions.org/questions/ubuntu-63/hp-laserjet-doesnt-work-with-ubuntu-10-04-a-818615/](http://www.linuxquestions.org/questions/ubuntu-63/hp-laserjet-doesnt-work-with-ubuntu-10-04-a-818615/)

There is also a thread about this on crunchbanglinux.org, but that did not help either. 

Refer: [http://crunchbanglinux.org/forums/to...inting-broken/](http://crunchbanglinux.org/forums/to...inting-broken/)


This is my log:


> 
/var/log/cups# tail error_log
E [15/Jul/2010:11:33:11 -0600] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory


If I remove .hplip, and try to print, I get:

> 
Description:	Hewlett-Packard hp LaserJet 3015
Location:	ash
Driver:	HP LaserJet 3015 Postscript (recommended) (grayscale)
Connection:	hp:/usb/hp_LaserJet_3015?serial=00MXBM207372
Defaults:	job-sheets=none, none media=na_letter_8.5x11in 


There is plenty of paper in the printer, and the printer works just fine with windows.

---

### Post by manuelnw on 2010-10-17
Hi,

In another forum, I found this:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

I deleted the printers and faxes I had in System->Administration->Printing and installed hplip. Now it works. Just follow the installation instructions. I think it's important to delete the printers first, cause at first I installed it without doing it and didn't work properly.

Good luck

---

### Post by walterbyrd on 2012-05-02
I have to reinstall the printer everytime I try to print something. I have the printer installed about a dozen times, so far.

I think the Lubuntu upgrades break the printer.

I wonder if this is just a problem with Lubuntu, or is it a problem with CUPS? 

The last version of Ubuntu I used was 10.4, I did not have constant printer problems with that.

---

