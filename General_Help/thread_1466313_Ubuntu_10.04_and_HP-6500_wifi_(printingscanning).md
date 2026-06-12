---
title: "Ubuntu 10.04 and HP-6500 wifi (printing/scanning)"
date: 2010-04-30
forum: General Help
---

### Post by mihai.ile on 2010-04-30
Hello.

I would like to mention that the printer HP-6500 wireless version works out of the box, 100% compatible with Ubuntu 10.04LTS. I tested double sided printing (the printer has support for it), and scanning a document (using the new scanning software in Ubuntu 10.04 that came installed). All this over the wifi network. All you have to do is to add the network printer, let Ubuntu install the drivers and that's it. (Even if you only want to scan, you have to add the printer before being able to print).

Ok, hope it will help someone when trying to decide whether or not to buy this exact printer.

---

### Post by moparcrazy on 2010-10-18
Maybe I should have done another tread but I am not able to get my 6500 wifi to work.  Under my printer settings there is no way to add a printer.  The add printer button is greyed out.  When I try to connect to the locahost network and select my printer it says that I am not able to.  There was an error with the CUPS server.  I am have checked to make sure that I am up to date with all the software.  I am running Ubuntu 10.04 and have the hp 6500 709n printer.  I am running Ubuntu on a dell inspiron 6000 laptop.  I can print on my XP desktop with no problem.  I can also print from my Moto droid phone so it is something with the Ubuntu setup. Please help.  Thank you.  In advanced.

---

### Post by GavinOB on 2010-11-19
Try installing the official HPLIP printer drivers (hplip-gui).

You should then see an icon for it under System > Preferences > HPLIP Toolbox.

It automatically located my wifi printer when I opened the Toolbox.

---

