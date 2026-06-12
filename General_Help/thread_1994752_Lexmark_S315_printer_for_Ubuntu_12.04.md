---
title: "Lexmark S315 printer for Ubuntu 12.04"
date: 2012-06-03
forum: General Help
---

### Post by Thirup on 2012-06-03
Hello everyone! Yesterday I bought myself a Lexmark S315 printer and I was assured that it is linux compatible, however I've had some problems about installing it. 

I tried installing the driver software from [http://support.lexmark.com/index?pag...serlocale=DE#1](http://support.lexmark.com/index?pag...serlocale=DE#1) but after installing lexmark-printer-utility-wJRE-1.0-1.amd64.deb I tried running it in Ubuntu software center, it refuses to install it proberly.

Have I picked a wrong file for the installation, or am I doing something else wrong? Hoping someone can help, and I'm willing to give more detailed information, if it's neccesary :)

---

### Post by Thirup on 2012-06-03
Bump!

I've managed to open the Lexmark Print driver queue wizard, where I'll have to say what the printer type is, but I can't see S315 among the suggestions - can I import it to the list somehow? And also, if I want the printer to be used over usb, where is the usb drectory? /dev/usb/lp0 ?

Hoping someone can help, just tell me if you need details - I need the printer tomorrow, so I really need help :)

---

### Post by khunphil on 2012-06-26
HI...

Late ... but have a look, /dev/usb/lp0 does not exist anymore in 12.04 .. CUPS take care of it ... usblp module is blacklisted .. and I cannot use my Zebra generix printer as before : cat A.txt > /dev/usb/lp0 ...

This is a huge problem for me, as server is printing sticker .. and cannot anymore.

For information...

Philip

---

