---
title: "Canon imageCLASS mf4450 printer failed installation"
date: 2012-06-05
forum: General Help
---

### Post by AurelioZen on 2012-06-05
I just bought a Canon imageCLASS MF 4450 printer and I'm having difficulty installing it in 64 bit12.04. The printer is currently connected to the USB port.

I've downloaded cndrvcups-common_2.40-3_amd64 and cndrvcups-ufr2-us_2.40-3_amd64 off of the canon US website for my model printer. 

I converted the .rpm files to .deb with alien, and then installed using Gdebi. 

When I add a printer, my computer recognizes the printer and the right drivers appear in CUPS, but after install, I get nothing out the printer.  When I try to print with the printer, I get an error message that says "Stopped- printer configuration error."

Anyone have any recommendations?

---

### Post by fdrake on 2012-12-08
go to the canno website and install the 32-bit debian package. even if you have a 64 bi t os it will still work.
[http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/black_white_laser_multifunction/imageclass_mf4450#DriversAndSoftware](http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/black_white_laser_multifunction/imageclass_mf4450#DriversAndSoftware)

---

### Post by pdc on 2012-12-08
there are various threads around this issue;

if you have a fresh install......... have you thought of just installing a 32bit Ubuntu...............

if you want to stick with the 64 bit, 

see post #99 here

[http://ubuntuforums.org/showthread.php?t=1427330&highlight=canon&page=10](http://ubuntuforums.org/showthread.php?t=1427330&highlight=canon&page=10)

........it involves creating symbolic links (ideally before installing the drivers but creating them now should help..)

...... that should get you going.......

posts # 7 and 8 here

[http://ubuntuforums.org/showthread.php?p=12385174#post12385174](http://ubuntuforums.org/showthread.php?p=12385174#post12385174)

also mention this need for links: 

if you subscribe to a thread: top right, thread tools......you can keep in touch more easily....let us know how things go

---

