---
title: "Installing D-Link DE620 Paralell Pocket Adaptor"
date: 2006-06-24
forum: General Help
---

### Post by jatos on 2006-06-24
I have an old D-Link Paralell BNC Pocket Adaptor. I need to get it working in Breezy, and I don't know how to do it. Any help would be appreciate.
Jamie

---

### Post by stephencameron on 2006-08-17
I also have a de620 parallel port to RJ45 and also I am new to the build - I loaded Ubuntu this morning on an old Toshiba laptop. I have recently got clues: using a bootloader to switch on the de620 device driver should be a start. I will report on my progress tonight.

Did you find any answers?

Steve

---

### Post by stephencameron on 2006-08-17
The first reference - I have is: 

[http://www.oreilly.com/catalog/debian/chapter/book/appd_06.html](http://www.oreilly.com/catalog/debian/chapter/book/appd_06.html)

This should give you a start by using:

insmod de620

this should work - but you may need to put the irq and port specs in as well. Read the page. Also it would be good that it was built into the boot so you will need to add a line to:

 /etc/conf.modules

I hope this helps. I will try this myself tonight - and tell you how it went. I have every hope that I will sort this out. I am only loading Ubuntu server.

Steve

---

