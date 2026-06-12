---
title: "Connecting to network printer (SMB name)"
date: 2011-05-11
forum: General Help
---

### Post by AlpCen on 2011-05-11
I'm trying to connect to a network printer via SMB. On Windows XP, the printer address is (something like) 1.2.3.4:name. However, when I try to add the printer to CUPS I get:

"Bad device-uri "smb://1.2.3.4:name""

It doesn't work with "smb://1.2.3.4/name" or just with "smb://1.2.3.4" either.

Where am I supposed to enter the printer name?

---

### Post by AlpCen on 2011-05-11
Anyone? :confused:

---

### Post by Don Barzini on 2011-05-11
Try this tutorial.....

[http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html](http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html)

---

### Post by AlpCen on 2011-05-12
Thanks for the link! Worked by using "lpd://1.2.3.4/name" instead of "smb://".

---

