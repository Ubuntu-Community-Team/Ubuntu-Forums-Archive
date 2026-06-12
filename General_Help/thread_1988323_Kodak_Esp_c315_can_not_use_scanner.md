---
title: "Kodak Esp c315 can not use scanner"
date: 2012-05-27
forum: General Help
---

### Post by a26776500 on 2012-05-27
I've got a problem, I can't use the scanner with my Ubuntu 10.04 but I can use the printer. My printer is KODAK ESP C315 all in one printer (printer+scanner). How can I use the scanner with my Ubuntu?

---

### Post by a26776500 on 2012-05-27
Plases help me to solve the problem!

---

### Post by cuberts on 2012-05-27
[http://www.linuxquestions.org/questions/linux-newbie-8/configure-scanner-in-ubuntu-740564/]("http://www.linuxquestions.org/questions/linux-newbie-8/configure-scanner-in-ubuntu-740564/")

I would recommend you install Image Scanning software Xsane, because the default scanning software was a bit glitchy for me, like it created scans that were 4MB.

---

### Post by paulnewall on 2012-07-01
It is now possible to install a sane backend for scanning with the kodak printers from the git repository of sane.
There are some instructions here
[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

---

### Post by sizex on 2013-02-15
thanks for the sane link. I did the biz without seeing any error messages, but the ubuntu 12.10 system doesn't see the scanner. I don't have a usb cable since I bought the kodak for wireless use, so I cannot check if I could scan using a wired connection. I can use the printer capability of the kodak from the system in wireless mode though. rereading the information on the sane link I could interpret sane as supporting only scanners connected by cable. do you know if that's the case? thanks.

---

### Post by paulnewall on 2013-02-15
There are some troubleshooting ideas in the readme file here
[http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/](http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/)

---

