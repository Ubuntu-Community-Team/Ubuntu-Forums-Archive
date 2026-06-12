---
title: "Printing from bonjour printer on mac"
date: 2009-08-13
forum: General Help
---

### Post by brucedes on 2009-08-13
Hi,

I have my printers plugged into a mac mini which I use as my printer server. If I want to print from os x or windows, I just use bonjour with no problems.

Thing is, I don't know how to do this in ubuntu 9.04, I saw a guide to printing from an airport base station, but don't know if that'll help me here.

Any help is appreciated on getting this to work :)

---

### Post by 3rdalbum on 2009-08-13
The Mac OS uses CUPS as its printing system, just like Ubuntu. And CUPS provides the functionality that Apple users call "Bonjour".

On your Ubuntu system, go to System > Administration > Printing. Go to the Server menu and go to New > Printer.

Now, this should probably find your printer straight away. It always has for me (admittedly, I run an Ubuntu-only network). If it doesn't, then you will be given a new window with "Network Printer" in the left pane with an arrow on the left side. Click the arrow and click Find Network Printer. Now you can type in the IP address of your Mac Mini and click Find, and this should do the trick.

---

