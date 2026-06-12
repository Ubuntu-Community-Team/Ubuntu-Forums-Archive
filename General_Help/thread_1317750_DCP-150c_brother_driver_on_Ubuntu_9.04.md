---
title: "DCP-150c brother driver on Ubuntu 9.04"
date: 2009-11-07
forum: General Help
---

### Post by vzhen on 2009-11-07
[SOLVED]
Didn't know have to install cupswarrper.

Thx all

I followed this solutions from Brother website i passed all the steps but my printer still not working.

[http://solutions.brother.com/linux/en_us/instruction_prn3.html](http://solutions.brother.com/linux/en_us/instruction_prn3.html)

Laptop : Dell 1501
OS : Linux ubuntu 9.04
Printer : Brother DCP-150c
Install method: debian package

At the last step #/etc/init.d/lpr restart   
I don't get lpr in my init.d but there is something call lpd so i #/etc/init.d/lpd restart. Result is nothing display, nothing error. I restart my printer and my laptop but i still can't get to print.

Here is my PrintScreen
[URL="http://img20.imageshack.us/i/screenshotlyf.png/"][IMG]http://img20.imageshack.us/img20/8748/screenshotlyf.png[/IMG]
[/URL]

---

### Post by Frantic_Earthling on 2009-11-07
Have you tried to install your printer by running:

[http://localhost:631/](http://localhost:631/)

in your browser, and by clicking on "Adding Printers and Classes"?

---

### Post by plucky on 2009-11-07
Use **Synaptic Package Manager** and search for **dcp-150c** and install the "brother-cups-wrapper-extra" and brother-lpr-drivers-extra" debs.

Then,connect printer and power on and  open **System > Administration > Printing** and add a new printer and select the correct driver for the printer,which should now be in the list.


Good Luck

---

